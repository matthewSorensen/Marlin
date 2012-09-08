# Non-standard G-codes

## Movement

   * G2  - CW ARC
   * G3  - CCW ARC

## General

  * M17  - Enable/Power all stepper motors. Compatibility to ReplicatorG.
  * M18  - Disable all stepper motors; same as M84.Compatibility to ReplicatorG.
  * M30  - Print time since last M109 or SD card start to serial
  * M42  - Change pin status via gcode
  * M80  - Turn on Power Supply
  * M81  - Turn off Power Supply
  * M114 - Output current position to serial port 
  * M119 - Output Endstop status to serial port

## Movement variables


*(nb. that these descriptions are unchanged from the original Marlin - I don't fully understand their function/relevancy)*

  * M202 - Set max acceleration in units/s^2 for travel moves (M202 X1000 Y1000) - apparently unused.
  * M203 - Set maximum feedrate that your machine can sustain (M203 X200 Y200 Z300 E10000) in mm/sec
  * M204 - Set default acceleration: S normal moves T filament only moves (M204 S3000 T7000) im mm/sec^2  also sets minimum segment time in ms (B20000) to prevent buffer underruns and M20 minimum feedrate
  * M206 - set home offsets.  This sets the X,Y,Z coordinates of the endstops (and is added to the {X,Y,Z}_HOME_POS configuration options (and is also added to the coordinates, if any, provided to G82, as with earlier firmware)
  * M220 - set build speed multiplying S:factor in percent ; aka "real-time tuning in the gcode". So you can slow down if you have islands in one height-range, and speed up otherwise.
  * M221 - set the extrude multiplying S:factor in percent
  * M400 - Finish all buffered moves.

## Temperature variables

  * M301 - Set PID parameters P I and D
  * M302 - Allow cold extrudes
  * M303 - PID relay auto-tune S<temperature> sets the target temperature, which defaults to 150C.

## Advance

  * M200 - Set filament diameter for advance
  * M205 - advanced settings:  minimum travel speed S=while printing T=travel only,  B=minimum segment time X= maximum xy jerk, Z=maximum Z jerk

## EEPROM

All of the following commands refer to the following parameters: *axis_steps_per_unit*,  
*max_feedrate*, *max_acceleration*, *acceleration*, *retract_acceleration*, *minimumfeedrate*,
*mintravelfeedrate*, *minsegmenttime*, *jerk velocities*, and *PID*.

  * M500 - store parameters from RAM into EEPROM. The following parameters are stored
  * M501 - read parameters from EEPROM into RAM
  * M502 - read parameters from the chip's flash (ie. the original values from the configuration) into RAM.
  * M503 - print the current parameters from RAM.

## Miscellaneous

  * M240 - Trigger a camera
  * M999 - Restart after an error
