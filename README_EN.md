# BigTreeTech SKR1.4 Turbo + TCM2208 + Ender3

This repository is for those who purchased a BigTreeTech SKR 1.4 turbo with TMC 2208 and would like to configure it on a standard Ender 3, without BLTouch, without dual motors, and with the simple LCD display.

Here is the link to the video showing how I created this repository: LINK

The repository was divided into two distinct and independent procedures:

- 1: For those who just want to install the firmware without changing the settings, ideal for those who have the original Ender and only needed to replace the board.
- 2: For those who want to adjust the settings according to changes made to the printer.

### Here is the video on how the repository was created:

## Initial Hardware Adjustments

### 1 - The first step is to set the drivers to UART mode (so no physical adjustment on the driver is necessary) as shown in the image.

![image](https://github.com/user-attachments/assets/cbe6c088-17b8-407b-bc51-223cabd694ad)

If the SKR 1.4 turbo board is new, it will have four jumpers placed. You will need to remove them to match the image.

### 2 - Add the TMC2208 drivers to the board along with the heat sinks

Place the five drivers into the five available slots for them.

![image](https://github.com/user-attachments/assets/93a567db-fc7c-425e-896f-0386e138d58b)

The colors of the components help during installation, but be careful not to place the drivers incorrectly.

### 3 - Plug in the other components

The board has labels indicating where each component goes, but below is a description of where to plug in the components of the Ender 3.

**REMEMBER THAT SOME CONNECTIONS HAVE A "+" AND A "-", BE CAREFUL NOT TO CONNECT THEM BACKWARDS**

![image](https://github.com/user-attachments/assets/dd5a70ec-325a-40c2-b003-b981ef68fd21)

1. **DCIN:** 24V power input;
2. **HB:** bed heating;
3. **HE0:** nozzle heating (HE1 is for heating a second nozzle, if you have one);
4. **FAN:** fan that runs constantly (front of the hotend);
5. **CNC FAN:** fan for filament cooling (side of the hotend);
6. **XM:** X-axis stepper motor;
7. **YM:** Y-axis stepper motor;
8. **ZAM:** Z-axis stepper motor (ZBM is for a second synchronous motor, if you have one);
9. **EM0:** extruder motor (EM1 is for a second extruder);
10. **EXP1:** standard Ender 3 LCD display;
11. **TB:** bed temperature sensor;
12. **TH0:** nozzle temperature sensor;
13. **X Stop:** X-axis endstop sensor (likely a two-wire plug, connect according to the green box);
14. **Y Stop:** Y-axis endstop sensor (likely a two-wire plug, connect according to the green box);
15. **Z Stop:** Z-axis endstop sensor (likely a two-wire plug, connect according to the green box).

## PROCEDURE 1

If you only want to use the precompiled settings and upload the firmware to your Ender 3, simply download the "firmware.bin" file from the "firmware" folder, save it to the memory card that goes into the printer, turn off the printer, insert the card, and turn the printer back on. Upon restarting, the board will read the "firmware.bin" file and update the firmware.

Here is the direct link to the file: LINK

## PROCEDURE 2

If you want to make changes to the firmware before installing it, follow the steps below.

### 1 - Download the necessary tools

1. VScode: download and install Visual Studio Code (https://code.visualstudio.com/Download);
2. PlatformIO IDE: download the PlatformIO IDE extension for VScode for compiling:

   ![image](https://github.com/user-attachments/assets/fe10a189-faae-440c-a83e-5abcf3756ce1)

4. Auto Build Marlin: download the Auto Build Marlin extension for VScode:

   ![image](https://github.com/user-attachments/assets/666de9ba-0901-4790-934d-7875fb20f3a8)

### 2 - Download the repository

The repository folders can be obtained in two ways:

1. Cloning the repository with the command: 
```
git clone https://github.com/Hobbies-Prof-Bento/BigTreeTech_SKR1.4_Turbo_TCM2208_ender3.git
```
2. Clicking "code" and then "Download.zip" (you need to extract the folders from the .zip file).
   ![image](https://github.com/user-attachments/assets/61a8a87b-6484-40d9-8dca-fedeffe9ad2f)

### 3 - Access the repository with VScode

1. Open VScode;
2. Go to "file";
3. Select "open folder";

![image](https://github.com/user-attachments/assets/f0d4651c-0e71-438b-ba36-bb2b53f5486e)
   
4. Choose the repository folder;

![image](https://github.com/user-attachments/assets/34a8b618-ea2a-4c3b-8195-6dded08b444a)

5. Make the necessary changes.

In the **Configuration.h** file of Marlin, you can make several changes that affect the behavior and functionalities of the 3D printer:

1. Bed dimensions and limits: Adjust the bed size and axis movement limits.
2. Speeds and accelerations: Configure the speeds and accelerations of the axes.
3. Motor currents: Set the stepper motor current.
4. Steps per millimeter (steps/mm): Adjust the precision of the axis and extruder movements.
5. Temperature: Configure the temperature control of the hotend and bed.

You can also adjust advanced functions such as using bed leveling sensors (BLTouch), enabling PID control, configuring specific drivers (like TMC), among other features specific to your printer.

In the **Configuration_adv.h** file of Marlin, you can adjust more advanced settings that affect performance and specific functionalities of the printer. Some of the main changes include:

1. Driver settings (like TMC): Adjust currents, interpolation, and modes like StealthChop or SpreadCycle.
2. Advanced PID: More detailed PID parameter control.
3. Fan management: Configure fan behavior for board and motor cooling.
4. Homing and movements: Sensorless homing settings and multiple Z motors.
5. Automatic calibration and mesh leveling.

These options allow further customization of the printing experience and the performance of the printer.

## Compiling changes

After making the necessary changes, click on "Auto Build Marlin" and then select "Show ABM Panel".
![image](https://github.com/user-attachments/assets/2dfd7b6c-cdab-4837-94c6-1a3dffa1e7e7)

An interface with configuration information and "build" and "update" buttons will appear. Click "build".
![image](https://github.com/user-attachments/assets/c25e484c-b175-4fc6-91b5-8335c21b6e23)

A warning message will appear, but don't worry.

![image](https://github.com/user-attachments/assets/26c612f3-5c9b-4386-b61f-274f7f730e0a)

The "firmware.bin" file will appear in the directory "<folder_where_the_repository_is_saved>\\.pio\\build\\LPC1769".

## Updating firmware

Save the "firmware.bin" file to the memory card that goes into the printer, turn off the printer, insert the card, and turn the printer back on. Upon restarting, the board will read the "firmware.bin" file and update the firmware.
