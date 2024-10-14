# Sensit.App.Log
This application logs data from devices that communicate via a serial port. Most polled or streaming devices are supported, so long as they communicate with ASCII text.

# Installation
Download (or clone) this repository.  Run setup.exe.
The app checks for updates whenever it is started.

# User Manual

## Requirements
A serial port is required.  That's all.  The device you're communicating with must either stream text-based data or support some sort of text-based command to which it issues a response.  [SCPI](https://en.wikipedia.org/wiki/Standard_Commands_for_Programmable_Instruments) instruments work well.  So do Arduinos if you program them to print a sensor reading periodically or after receiving a character or string.

## Filename
Click the browse button to select a file name/location.  When running, the app will create a CSV file with separate entries for each response of the serial device.  All entries are timestamped.

## Serial Port
Select the serial port, baud rate, parity, number of data bits, number of stop bits, and handshaking mode to match the device you wish to communicate with.  A refresh button (which looks like two blue arrows) will repopulate the available serial ports.

## Sample
Select whether the device you wish to communicate with streams data periodically or is polled with a command.  If the device is polled, you need to specify a command and interval.
* Command - Whatever is typed in this text box will be sent over the serial port, with the frequency selected by the _Sample Interval_ above.  The text may include "\n" for a newline character, "\r" for a carriage return, or "\t" for a tab.  The command is saved between sessions of the app.
* Interval - The sample interval sets how often the app will poll the serial device.  If using with the Automate app, set the interval to 500 milliseconds.  If both apps are set to 1000 milliseconds (the default rate that Automate records data), then rounding errors will cause some data to not have matching timestamps between Automate and Datalogger.  Setting the app to poll at 500 milliseconds ensures that there will always be a data point that matches each datum collected by the Automate app.

## Stop
Various settings for when to stop logging.  The app supports the following modes:
* Elapsed Time - stop after so many hours, minutes, seconds have passed.
* Date/Time - stop at a certain day and time.
* Number of Samples - stop after a certain number of samples have been received.
* Stop Button - keep logging until the "Stop" button is pressed.

## Response
Every time the app receives data from the serial device, whatever response it gets is printed in this text box.  This allows you to check that the device is working as expected and preview data.

## Start/Stop
Pretty self-explanatory.  Click _Start_ to begin logging data from the serial device, and _Stop_ to quit logging.  The _Stop_ button will work regardless of what stop mode is in use.

## Closing the App
Use the **File --> Close** menu item or the app's close button to close the serial port (if it is still open) and exit the application.
