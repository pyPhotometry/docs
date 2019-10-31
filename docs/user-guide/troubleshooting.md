# Troubleshooting

The page details how to fix common problems that can occur when using pyPhotometry.  If you encounter a problem that is not covered on this page, please contact the [google group](https://groups.google.com/forum/#!forum/pycontrol).

### Can't connect to acquisition board.

If the GUI status says 'Connection Failed' when you try to connect to the acquisition board, try resetting the board using the small button labled 'RST' on the Micropython microcontroller.

If the GUI status says 'Firmware Error' when you try and connect, copy the files *photometry_upy.py* and *hardware_config.py* from *pyPhotometry/uPY* to the root directory of the acquition board flash drive.  If you still get a firmware error, reset the filesystem by following the instructions [here](https://docs.micropython.org/en/latest/pyboard/tutorial/reset.html#factory-reset-the-filesystem), then re-copy the file *photometry_upy.py* to the board and try again.