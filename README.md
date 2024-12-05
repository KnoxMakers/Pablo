# README
Pablo is a handy-dandy drawing machine housed by Knox Makers. It uses the Processing language/editor to send to a pair of stepper motors the code needed to have the motors create a drawing on a vertical(ish) notepad. From the motors depend small cables that hold a pen-holder. The code instructs the motors how to move so that the pen will create a drawing based on an svg file provided to the app.

## Background
Historically, Pablo has run on a tiny old Windows laptop. This repo includes an install file to make installing the necessary files onto a linux machine (tested on Ubuntu). It also includes some images that can be fed to Pablo to be drawn. The purpose of creating this repo is to shut down that Windows laptop so that we have all open-source software running at Knox Makers.

Pablo consists of three things:

* The [Processing](https://processing.org) software, which sends instructions to two stepper motors that control the drawing.
* A library/sketchbook called [polargraphcontroller](https://github.com/euphy/polargraphcontroller) that Processing uses to take an svg file as input and to send instructions to the stepper motors via a serial port.
* The hardware bits and bobs that make up the drawing apparatus itself. 

There's an [Instructables article](https://www.instructables.com/Polargraph-Drawing-Machine/) detailing how to build the drawing machine and set up the software. Simplified instructions for how to set up the software and run Pablo follow. Instructions are based on this [guide](https://github.com/euphy/polargraph/wiki/Running-the-controller-from-source-code).

Note that an older version of Processing (2.2.1) is required for this to work.

## Installation
* Clone this github repository.
* In the cloned directory, run the command `sudo ./install.sh` in the terminal.

You must have sudo access, as the script makes some changes to groups and permissions that require elevated access.

This script will create a directory named "pablo" in your home directory. This includes the processing application file required to run Pablo. It also creates a directory named "sketchbook" in your home directory. This is the default location in which Processing stores its sketchbooks. Finally, it adds a desktop icon that runs Processing and loads the polargraphcontroller sketchbook that works as an interface for sending a drawing to the hardware.

The installer downloads some software (Processing 2.2.1 and Polar Graph Controller 1.1.17) from their external repos. The install should be pretty quick but depends on download speed for those software packages. The installer also puts a launcher on your desktop.

## Running Pablo
Once you've installed the software, look for the launcher on your desktop and click or double click to load the Processing IDE. Within this, press the "play" button (a right-arrow). This will launch a user interface with lots of ugly buttons in it and an area to display a drawing.

If you wish to draw Tesla, as we have typically done for demos of the Pablo machine, press the "Draw Tesla" button in the user interface (second column of buttons on the main screen once you've pressed the "play" button). This should automatically prepare the software to send the Tesla image to the drawing machine.

If you wish to load a different svg file, you'll need to manually do some steps that our customizations for the Tesla button do for you. They're as follows:

# Press the "Clear Queue" button.
# Press the "Set Home" button.
# Press the "Pen Lift" button.
# Press the "Load Vectors" button and select the svg file that you wish to have the robot draw.
# If desired, press the buttons to resize or move the image.
# Press the "Draw Vectors" button.
# Press the "Pen Lift" button.
# Press the "Return to Home" button.
# Click the red text near the top right that includes the word "QUEUE PAUSED" to start the drawing.

What's happening when you click these buttons is that you're adding a series of commands to a command list that the software then sends to the Arduino device to be executed in order. The "Draw Tesla" button just happens to cue up these commands automatically for you.

## License
Sources for the images in this repo are unknown, and they should not be considered to be open source. The install script is open source, let's say GPL 3.


