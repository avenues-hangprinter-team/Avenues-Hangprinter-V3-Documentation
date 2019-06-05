# Avenues-Hangprinter-V3-Documentation

## **1. Construction**
####Materials 
The first task to build the printer is to gather all of the needed materials and parts. Some of the parts have to be 3D printed while some have to be bought. 
- BOM
  - *This bill of materials lists all of the necessary materials needed outside of 3D printed parts. Adjust the lengths of cables, wires and anchors for your scale.*
- 3D printed parts 
  - You can find the STL files for the 3D printed parts in this link. It is recommended that these parts be sent out for professional 3D printers, since precision is of utmost importance.
####Mover Assembly
- Structure
  - The structure of the mover consists of four wood beams, 3D printed corner clamps and beam sliders, the extruder and a lot of zipties. The instructions for how to put everything together can be found in the assembly manual in the official Hangprinter website. 
- Attach lines
  - This part of the assembly process has proven to be very difficult if not done properly. While cutting the fishline, ensure that it does not get tangled in the process. To avoid that, wrap the line around something small and flat, like a piece of cardboard. 
- Extruder assembly
  - Use the mount that was 3D printed to fix the gantry to the mover. This can be done using high strength zip ties, which was proven to be effective. 
####Ceiling Mount Assembly
- 2D template
  - This template helps to attach the right parts in the right places. Make sure to print it in 100% scale. The PDF can be found in this link. Once the template is printed, tape it together and use it to drill holes in your wooden plate. 
- Linerollers
  - Before attaching the line rollers to the ceiling mount, you should insert PTFE tubing into the D-linerollers. After this is done, place the line rollers in their right place, with the help of the template, and screw them with self tapping wood screws. 
- Spools
  - The spools, spool gears, spool cores, spacers and 608 bearings will need to be assembled before being mounted. There is a detailed explanation on how to do it in the official assembly manual, that can be found in this link. Make sure that the bearings fit in the spool cores, don't force those too much because they can get stuck. 
- Attach motors
  - Use the template to ensure that the motor mounts are in the correct place. You can see how to attach the motors to the motor mounts in the official assembly, that can be found in this link. You might need to add washers under the mounts in order to have the spools spinning smoothly. If you are doing a build without mechaduinos, then you can go ahead and mount the motors now. Otherwise, read the mechaduino section and mount the motors after the mechanduinos are attached. 
- Anchors
  - The anchor's job is to redirect the line coming from the ceiling mount. First of all, we should prepare two anchor line rollers which are 3D printed (It is the easiest method to  get those pieces) Then, prepare a wood sheet which is in square shape. After that we attach a same-length-with-wood-sheet wood beam on a side of wood square sheet. Measure the length of side of the mover(triangle structure) and fixed the anchor line rollers on the wood beam. The length between two rollers should have the same length with the side of the mover.


Electronics
Arduino
Marlin (Cole + Noya)
Raspberry Pi
OctoPi (Marton)
Smart Steppers/Mechaduino
SmartStepper Sub tree (Cole)
Wiring and Circuitry
(NOYA)
Calibration
Instructions (Cole)
Get points
How to use
.stl to print (octo-pi)
Time estimations (g/s? mm/s?)


## **1. Construction**











## **2. Electronics**
- The version of the Hangprinter we used included Smart Steppers/Mechaduinos for each stepper motor. They make the overall stability of the printer superior than before, preventing issues such as layer shifting. There also exists an experimental use of the Smart Stepper's torque mode to auto-calibrate the printer, saving huge amounts of time and effort.
>
- The main board is an Arduino Mega 2560 powered by a Ramps 1.4 shield. For wireless connection with the board, we used a Raspberry Pi 3 B+ loaded with OctoPi.
<br> <br> *We recommend Misfitech's Nano Zero Stepper (NZS) software even for Mechaduino owners. The Mechaduino software includes some floating point rounding errors that can ruin the quality of the prints.*

**Necessary Changes to the Code:**
We were having i

___
Torbjørn's Smart Stepper software had a bug while booting. We were bombarded with "You need to Calibrate" in the Serial Monitor and were not able to give any commands.

***Our Solution:*** 

To solve it, we flashed NZS original software, ran the `calibration` and copied the calibration numbers that were shown in the serial motor.


Then we came back to Torbjørn's version, in the file `nonvolatile.cpp` We pasted the numbers in line 29, and added a comma after CAccAthe last one.
  
  ![Numbers](/CalNumbers.png)


After booting up, we ran `testcal` and made sure that the max error was at least less than 0.1. If yours is bigger, run `calibrate` again and `testcal` after.