# pyPhotometry data

pyPhotometry generates binary data files with a  *.ppd* file extension. File names are given by the subject ID and the data and time the recording started, e.g. *m1-2018-08-30-103945.ppd*

## Importing data

If you are using Python for analysis you can import files using the `import_ppd` function in the [data_import](https://bitbucket.org/takam/pyphotometry/src/default/tools/data_import.py?at=default&fileviewer=file-view-default) module:

```python
from data_import import import_ppd

data = import_ppd('path\\to\\data_file.ppd', low_pass=20, high_pass=0.01)
```

The `import_ppd` function returns a dictionary with the following entries:

```python
'subject_ID'    # Subject ID
'date_time'     # Recording start date and time (ISO 8601 format string)
'mode'          # Acquisition mode
'sampling_rate' # Sampling rate (Hz)
'LED_current'   # Current for LEDs 1 and 2 (mA)
'version'       # Version number of pyPhotometry
'analog_1'      # Raw analog signal 1 (Volts)
'analog_2'      # Raw analog signal 2 (Volts)
'analog_1_filt' # Filtered analog signal 1 (Volts)
'analog_2_filt' # Filtered analog signal 2 (Volts)
'digital_1'     # Digital signal 1
'digital_2'     # Digital signal 2
'time'          # Time of each sample relative to start of recording (ms)
```

The `high_pass` and `low_pass` arguments provided to the `import_data` function determine the frequency in Hz of highpass and lowpass filtering applied to the filtered analog signals.  To disable highpass or lowpass filtering set the respective argument to `None`.   The filtering applies a 2nd order Butterworth filter in the forward and reverse directions to give a 4th order zero phase filter.

## Data format

pyPhotometry data files have the following structure:

| Start byte    | End byte      | Content     | Format                              |
|---------------|---------------|-------------|-------------------------------------|
| 1             | 2             | header size | 2 byte little endian integer        |
| 3             | 2+header size | header      | JSON object encoded as UTF-8 string |
| 3+header size | file end      | data        | see below                           |


The first two bytes of the file indicate the size of the header.  The header is a UTF-8 encoded string which represents a [JSON](https://www.json.org/) object with the following entries:

```python
'subject_ID'         # Subject ID
'date_time'          # Recording start date and time (ISO 8601 format string)
'mode'               # Acquisition mode
'sampling_rate'      # Sampling rate (Hz).
'version'            # Version number of pyPhotometry
'volts_per_division' # Volts per division of the analog signals.
'LED_current'        # Current for LEDs 1 and 2 (mA)
```

The remainder of the data file contains the analog and digital signals.  Each two bytes chunk of data encodes a 16 bit little endian unsigned integer. The most significant 15 bits of each integer encode one sample of an analog signal and the least significant bit encodes one sample of a digital signal.  Analog channel 1 and digital channel 1 are paired together, and analog channel 2 and digital channel 2 are paired together. Channels 1 and 2 alternate in successive 2 byte chunks.  To convert the analog signals to Volts, multiply them by the 'volts_per_division' value from the header information.

In Python, the steps to convert the data bytes into signals are:

```python
# Convert the data bytes into an array of 16 bit unsigned integers.
data = numpy.frombuffer(data_bytes, dtype=numpy.dtype('<u2')) 

# Analog signals are most significant 15 bits of each integer,
# extract them by bit shifting 1 to the right.
analog = data >> 1

# Digital signals are least significant bit of each integer,
# extract them by bitwise AND with integer 1.
digital = data & 1

# Channels 1 and 2 are alternating samples:
analog_1  =  analog[0::2] 
analog_2  =  analog[1::2]
digital_1 = digital[0::2]
digital_2 = digital[1::2]

# Convert the analog signals into Volts.
analog_1 = analog_1 * volts_per_division[0]
analog_2 = analog_2 * volts_per_division[1]
```