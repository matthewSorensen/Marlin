# Marlin,

a [RepRap](http://reprap.org/wiki/Main_Page) firmware originally derived from 
[Sprinter](https://github.com/kliment/Sprinter) and [grbl](https://github.com/grbl/grbl)
by [Erik van der Zalm](https://github.com/ErikZalm). I ([MDS](http://www.sorens.in)) am
maintaining this fork in order to work on the following issues:

  * The proper configuration for my MendelMax 1.5/RAMPS 1.4 setup.
  * Better documentation. At the moment of forking, the existing documentation
    really only tracks major deviations from Sprinter and some configuration parameters.
    Furthermore, it is suffused with misspellings, grammatical error, and poor sentence structures...

  * Support for a small serial LCD display to monitor various device parameters. The current
    system is targeted to a large (20x4) parallel LCD, along with full autonomous printing.

  * A simpler configuration system with well-documented and sensible defaults. This is the 
    most complicated issue, but also potentially the most rewarding...

  * Merging in support for [Printrboard](http://github.com/lincomatic/Marlin.git) - this will
    have to wait until I have regular access to a Printrboard-based printer.
    
## Features

  * Interrupt based movement with real linear acceleration

  * High step-rate

  * Look ahead (Keep the speed high when possible. High cornering speed)

  * Interrupt based temperature protection

  * Preliminary support for Matthew Roberts advance algorithm 
    For more info see: http://reprap.org/pipermail/reprap-dev/2011-May/003323.html

  * Full endstop support

  * SD Card support, including folders (in pronterface), and autostart.

  * LCD support (ideally 20x4), including a menu for autonomous printing.

  * EEPROM storage of many device parameters.

  * Arc support

  * Temperature oversampling

  * Dynamic Temperature setpointing aka "AutoTemp"

  * Support for [QTMarlin](https://github.com/bkubicek/QTMarlin), a very beta GUI for PID-tuning and velocity-acceleration testing.

  * Endstop trigger reporting to the host software.

  * Updated sdcardlib

  * Heater power reporting - useful for PID monitoring.

  * PID tuning

  * [CoreXY kinematics](http://www.corexy.com/theory.html)

## Notes

  * Uses the Arduino 1.0 environment.

  * Gen6 and sanguinololu users must copy the Marlin/sanguino folder into their Arduino 
    [environment's](http://arduino.cc/en/Guide/Environment) hardware directory.

  * The default baud-rate is 250000. 

## Branching Strategy

  * As we're going with a rolling release strategy, master should always contains a functional
    firmware version. All changes should thus be made in topic branches that get merged only when
    they're ready for release.

  * matthew-mendelmax always contains the current firmware on my MendelMax, which should
    simply be master with a machine-specific configuration applied to it.

  * upstream, which acts as a staging branch for all major changes introduced by the [parent](https://github.com/ErikZalm/Marlin)
    repository.
