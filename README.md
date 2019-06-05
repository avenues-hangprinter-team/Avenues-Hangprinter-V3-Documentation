# Avenues-Hangprinter-V3-Documentation

## **1. Calibration**
words here
















## **2. Electronics**
- The version of the Hangprinter we used included Smart Steppers/Mechaduinos for each stepper motor. They make the overall stability of the printer superior than before, preventing issues such as layer shifting. There also exists an experimental use of the Smart Stepper's torque mode to auto-calibrate the printer, saving huge amounts of time and effort.
>
- The main board is an Arduino Mega 2560 powered by a Ramps 1.4 shield. For wireless connection with the board, we used a Raspberry Pi 3 B+ loaded with OctoPi.
<br>  *We recommend Misfitech's Nano Zero Stepper (NZS) software even for Mechaduino owners. The Mechaduino software includes some floating point rounding errors that can ruin the quality of the prints.*

___
Torbjørn's Smart Stepper software had a bug while booting. We were bombarded with "You need to Calibrate" in the Serial Monitor and were not able to give any commands.

***Our Solution:*** 

To solve it, we flashed NZS original software, ran the `calibration` and copied the calibration numbers that were shown in the serial motor.


Then we came back to Torbjørn's version, in the file `nonvolatile.cpp`. We pasted the numbers in line 29, and added a comma after the last one.
  
  ![Numbers](/CalNumbers.png)


After booting up, we ran `testcal` and made sure that the max error was at least less than 0.1. If yours is bigger, run `calibrate` again and `testcal` after.