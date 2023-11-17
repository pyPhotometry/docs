# Troubleshooting

The page details how to fix common problems that can occur when using pyPhotometry.  If you encounter a problem that is not covered on this page, please post on the [discussion board](https://github.com/orgs/pyPhotometry/discussions).

### Can't open GUI

To open the GUI you need to run the file *pyPhotometry_GUI.pyw* using Python.  One way to do this is to set the file association for *.py* files to Python 3 so that you can run the file by double clicking it.  Alternatively you can open a command prompt, change directory to the folder containing *pyControl_GUI.py* and run the file with the command `python pyControl_GUI.py`.

If the GUI does not open this is probably because you do not have the required [dependencies](../index.md#dependencies) installed, a file will be generate in the pyPhotometry root folder called *'ErrorLog.txt'* specifying which dependency is missing.

### Board does not show up in GUI.

If no pyboards that you connect to the computer show up in the GUI's board select dropdown menu, the problem may be caused by the computers operating system langauge being set to something other than English.  This changes the name that pyboards are given in the computers list of connected serial devices, which is used by the GUI to identify connected boards.  There are two possible ways to fix this problem:

- Use the Micropython USB drivers rather than the generic windows USB serial device drivers.  This should ensure that pyboards are listed by the computers operating system as *Pyboard* irrespective of the operating system language.  Information on how to install the Micropython USB drivers is provided below in section *How to install Micropython USB drivers*.

- Alternatively, change the computers operating system language to English.

### Can't connect to acquisition board.

If the GUI status says 'Connection Failed' when you try to connect to the acquisition board, try resetting the board using the small button labled 'RST' on the Micropython microcontroller.

If you still cannot connect to the board, try resetting the pyboard filesystem by following the instructions [here](https://docs.micropython.org/en/latest/pyboard/tutorial/reset.html#factory-reset-the-filesystem).

### GUI freezes during acquisition

When aquiring data from many boards in parallel you may need to reduce the frequency with which GUI plots are updated by increasing the `update_interval` variable in *config/GUI_config.py* to avoid overloading the CPU.

### How to install Micropython USB drivers

By default windows will use generic USB serial device drivers for connected pyboards.  Normally this works fine, but if you are having reliability problems, or the GUI is not recognising connected pyboards due the computers operating system langage being set to something other than English (see above), it is recommended to use the Micropython USB drivers.  

To check which drivers you are using, look in the windows device manager under *Ports (COM & LPT)*, if your pyboard shows up as a *USB Serial Device* then you are using the generic windows driver, if it shows up as a *Pyboard USB Comm port* you are using the micropython USB drivers. For information on installing the microputhon USB drivers see [micropython windows setup](http://micropython.org/resources/Micro-Python-Windows-setup.pdf) and the micropython [docs](http://docs.micropython.org/en/latest/pyboard/pyboard/tutorial/repl.html).  The micropython drivers are unsigned so to install them on Windows 10, follow the instructions [here](https://www.maketecheasier.com/install-unsigned-drivers-windows10/) under *Install Unsigned Drivers from Advanced Boot Menu*.  You should only need to do this the first time you install the drivers on a computer.
