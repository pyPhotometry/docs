# Release Notes

---

## Maintenance team

* [Thomas Akam](https://bitbucket.org/takam/) thomas.akam@psy.ox.ac.uk

## Change log

Version 0.2.1 2019/05/10 -----------------------------------------------

- Fixed bug that caused GUI to crash if an invalid value was entered for 
  plot axis limits.

- Added calculation of digital input pulse times and sample numbers to 
  import_ppd function in data_import.py.

- Improved error handling so errors always provide an error message
  with a traceback indicating where the error occurred.

- Removed Pyperclip dependency.

- Moved hardware configuration to file hardware_config.py that is loaded 
  on the pyboard.  Allows boards with different configurations to be 
  run using the same GUI.

Version 0.2 - 2018/11/08 -----------------------------------------------

Version detailed in Scientific Reports Manuscript.

- Added functionality to save data as .csv files.

- Added function for importing *.ppd* files into Matlab.

Version 0.1 -  2018/10/02 ----------------------------------------------

Version detailed in Biorxiv manuscript.