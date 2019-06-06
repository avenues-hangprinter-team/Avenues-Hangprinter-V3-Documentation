#Avenues Hangprinter Usage Manual

[test](#Printing)

<a name="Power"></a>
## Power

Before using the printer, make sure it is connected to power and that the voltage regulator is outputting 5V. That is the correct amount of voltage used to power the Raspberry Pi and the Smart Steppers. If the value shown is bigger, immediately shut down the system.

## Octopi

To send and receive commands from the printer, we are using a Raspberry Pi 3 B+ connected to the Arduino, and a wireless platform called Octopi. To login, access [octopi-2.local](http://octopi-2.local) and use the following keys:

Username: `user`  
Password: `Avenues1`
_\*for regular use_

Username: `admin`  
Password: `avenuesadmin`
_\*only when making configuration changes_

>

- _If the website is not loading, first make sure you are connected to the network `AVEWIFI_-1`. If it still refuses to load, try going to [octopi.local](octopi.local) or [octopi-3.local](octopi-3.local).\_

## G-code

3D printers use a specific set of commands to print and communicate, they are called G-code. After having an estabilished connection with Octopi, you will be able to look at the overall status of the Hangprinter, which includes things such as hotend temperature, fan speed etc.

If needed to calibrate or test any sort of movement, some G-code commands are essential to know. To send them to the printer, acces the `Terminal` tab.

The general structure of G-code is essentialy composed of three parts. The following is an example G-code command.

> G6 A60 B60 C60 D50 F1000

If executed, this command will make motor A, B and C move 60mm, and motor D move 50mm. All of them will do that in a _feed rate_ of 1000.

Simplifying the three main parts mentioned before, they can be seen as **_what_**, **_who_** and **_how_**.

- As you can probably tell, the **_what_** is represented by the `G` followed by a number. The numbers chosen represent different actions a printer can perform.

- The **_who_** can be in a diverse range of options. In this example, it was the motors `A`, `B`, `C` and `D`. Notice how each of them were followed by a number. In this case, that number represented the amount of movement in millimiters.

- Finally, the **_how_**. Depending on the `G`command chosen, it can mean a variety of different things. In the example shown, it meant the feedrate of the movement being executed, represented by the letter `F`.

---

To assist you in your first "conversations" with the Hangprinter, here are some of the most important G-code commands to know:

- `G0, G1` - _Moves the gantry_

  > G1 Z200 F1000
  > //moves the gantry 200mm along the Z axis at a feed rate of 1000

- `M104` - _Sets the extruder temperature_

  > M104 S200
  > //sets the temperature of the extruder to 200°C

- `G95` - _Sets the printer to torque mode, which is further explained in the "Calibration" section_

  > G95 A35 B35 C35 D35
  > //puts all axes into torque mode at a level of 35/255

- `G92` - _Sets an origin position to the printer_
- `M114` - _Receive the current position of the gantry. This is useful during the calibration process._

##What to print?
With any 3D printer, the first step to printing is either designing or downloading a 3D object that you would like to see in the real world.

If you don't really want to design your own prints, [Thingiverse](https://www.thingiverse.com/) is an excellent place to find the awesome things made by the 3D printing community.
But if you want to go and design your own creatiosn, we recommend two pieces of Software. For beginners, [tinkercad](https://www.tinkercad.com/), a simple to use intuitive online editor. For individuals with previous experience in CAD, Fusion 360 is an amazing option.

For a first print, a cube or a 3D Benchy are usually sufficient, as you will be able to see the issues with the printer easily.

After you've chosen what to print, there is still one more step to take: slicing. For that, programs as Cura and Slic3r are recommended.
Slicing serves to transform a 3D object into a series of G-code commands for a specific printer.

In the slicer settings, you should set a profile for the Hangprinter. The settings we used are:

- Layer Height:
- Nozzle thickness:
- Temperature:
- Speed:

<a name="Printing"></a>
## Printing

It is finally time to print. After having a G-code file correctly sliced for the printer, upload it to Octopi in the `Load File` tab.
Before starting your print, there are some necessary "pre-flight" checks:

- _Hot end temperature:_
  If you are printing PLA, the recommended is around 185°C to 205°C.
  >
- _Z height_:
  The correct distance from the nozzle to the print surface is essential for a good print. To test it, slide a piece of paper between them. There should be some drag, but not enough to create marks on the paper's surface.
  >
- _Levelling_:
  If the print surface is not correctly levelled, the chances of a bad print are certain. Always make sure everything is calibrated and aligned properly.
