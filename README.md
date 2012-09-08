# Marlin,

a [RepRap](http://reprap.org/wiki/Main_Page) firmware originally derived from 
[Sprinter](https://github.com/kliment/Sprinter) and [grbl](https://github.com/grbl/grbl)
by [Erik van der Zalm](https://github.com/ErikZalm).

Features
===================

*   Interrupt based movement with real linear acceleration
*   High step-rate
*   Look ahead (Keep the speed high when possible. High cornering speed)
*   Interrupt based temperature protection
*   preliminary support for Matthew Roberts advance algorithm 
    For more info see: http://reprap.org/pipermail/reprap-dev/2011-May/003323.html
*   Full endstop support
*   SD Card support, including folders (in pronterface), and autostart.
*   LCD support (ideally 20x4), including a menu for autonomous printing.
*   EEPROM storage of many device parameters.
*   Arc support
*   Temperature oversampling
*   Dynamic Temperature setpointing aka "AutoTemp"
*   Support for [QTMarlin](https://github.com/bkubicek/QTMarlin), a very beta GUI for PID-tuning and velocity-acceleration testing.
*   Endstop trigger reporting to the host software.
*   Updated sdcardlib
*   Heater power reporting. Useful for PID monitoring.
*   PID tuning
*   [CoreXY kinematics](http://www.corexy.com/theory.html)

The default baudrate is 250000. This baudrate has less jitter and hence errors than the usual 115200 baud, but is less supported by drivers and host-environments.


Non-standard M-Codes, different to an old version of sprinter:
==============================================================
Movement:

*   G2  - CW ARC
*   G3  - CCW ARC

General:

*   M17  - Enable/Power all stepper motors. Compatibility to ReplicatorG.
*   M18  - Disable all stepper motors; same as M84.Compatibility to ReplicatorG.
*   M30  - Print time since last M109 or SD card start to serial
*   M42  - Change pin status via gcode
*   M80  - Turn on Power Supply
*   M81  - Turn off Power Supply
*   M114 - Output current position to serial port 
*   M119 - Output Endstop status to serial port

Movement variables:

*   M202 - Set max acceleration in units/s^2 for travel moves (M202 X1000 Y1000) Unused in Marlin!!
*   M203 - Set maximum feedrate that your machine can sustain (M203 X200 Y200 Z300 E10000) in mm/sec
*   M204 - Set default acceleration: S normal moves T filament only moves (M204 S3000 T7000) im mm/sec^2  also sets minimum segment time in ms (B20000) to prevent buffer underruns and M20 minimum feedrate
*   M206 - set home offsets.  This sets the X,Y,Z coordinates of the endstops (and is added to the {X,Y,Z}_HOME_POS configuration options (and is also added to the coordinates, if any, provided to G82, as with earlier firmware)
*   M220 - set build speed mulitplying S:factor in percent ; aka "realtime tuneing in the gcode". So you can slow down if you have islands in one height-range, and speed up otherwise.
*   M221 - set the extrude multiplying S:factor in percent
*   M400 - Finish all buffered moves.

Temperature variables:
*   M301 - Set PID parameters P I and D
*   M302 - Allow cold extrudes
*   M303 - PID relay autotune S<temperature> sets the target temperature. (default target temperature = 150C)

Advance:

*   M200 - Set filament diameter for advance
*   M205 - advanced settings:  minimum travel speed S=while printing T=travel only,  B=minimum segment time X= maximum xy jerk, Z=maximum Z jerk

EEPROM:

*   M500 - stores paramters in EEPROM. This parameters are stored:  axis_steps_per_unit,  max_feedrate, max_acceleration  ,acceleration,retract_acceleration,
  minimumfeedrate,mintravelfeedrate,minsegmenttime,  jerk velocities, PID
*   M501 - reads parameters from EEPROM (if you need reset them after you changed them temporarily).  
*   M502 - reverts to the default "factory settings".  You still need to store them in EEPROM afterwards if you want to.
*   M503 - print the current settings (from memory not from eeprom)

MISC:

*   M240 - Trigger a camera to take a photograph
*   M999 - Restart after being stopped by error

Configuring and compilation:
============================

Install the arduino software IDE/toolset v22
   http://www.arduino.cc/en/Main/Software

For gen6 and sanguinololu the Sanguino directory in the Marlin dir needs to be copied to the arduino environment.
  copy Marlin\sanguino <arduino home>\hardware\Sanguino

Install Ultimaker's RepG 25 build
    http://software.ultimaker.com
For SD handling and as better substitute (apart from stl manipulation) download
the very nice Kliment's printrun/pronterface  https://github.com/kliment/Printrun

Copy the Ultimaker Marlin firmware
   https://github.com/ErikZalm/Marlin/tree/Marlin_v1
   (Use the download button)

Start the arduino IDE.
Select Tools -> Board -> Arduino Mega 2560    or your microcontroller
Select the correct serial port in Tools ->Serial Port
Open Marlin.pde


The configuration is now split in two files
Configuration.h for the normal settings
Configuration_adv.h for the advanced settings


Click the Verify/Compile button

Click the Upload button
If all goes well the firmware is uploading

Start Ultimaker's Custom RepG 25
Make sure Show Experimental Profiles is enabled in Preferences
Select Sprinter as the Driver

Press the Connect button.

KNOWN ISSUES: RepG will display:  Unknown: marlin x.y.z

Gen7T is not supported.

That's ok.  Enjoy Silky Smooth Printing.

# Contributors

Sprinters' lead developers are Kliment and caru.
Grbls lead developer is Simen Svale Skogsrud. Sonney Jeon (Chamnit) improved some parts of grbl
A fork by bkubicek for the Ultimaker was merged, and further development was aided by him.
Some features have been added by:
Lampmaker, Bradley Feldman, and others...
