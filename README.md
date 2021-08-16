# m5stack-grbl-uiflow
Sample programs for testing the M5Stack GRBL Module 13.2 using uiFlow

#
These are very basic programs for the M5Stack GRBL module 13.2. To test these programs, you will need an M5Stack Fire (can also use Core, Grey, or Go) with GRBL module 13.2 attached and an M5Stack Faces kit with QWERTY keyboard attached. The Faces kit can be used to type GRBL commands and send them over ESP-Now to the Fire. The Fire will print the commands on the screen. I'm still experimenting with the GRBL module, so they are considered incomplete at this time (see issues below).

#
***Note: these programs have not been tested with stepmotors attached, so use at your own risk! If testing with stepmotors attached to the GRBL module, be sure to also attach a 9-24V power supply to the power jack of the module so you have enough power for the stepmotors. Max current is 1.5A per channel.***

#
Initial Setup:

Copy/paste the MAC address of the Fire to the GRBL_tx.m5f program and the MAC address of the Faces to the GRBL_rx.m5f program. This will set up the point-to-point ESP-Now network for sending GRBL commands from the Faces to the Fire. If you don't know the MAC address of your device, connect it to your computer's USB port and it should print the MAC on a serial terminal after running the program.
#
Basic functionality (based on uiFlow v1.8.2): 

Faces:
1. On the Faces kit, type a GRBL command and then press the Send button (A) or the OK button on the QWERTY keyboard. The Fire should receive the command, display it on the screen, and also display the GRBL return message (from the module) just below the GRBL command. Press the Clear button (B) to clear the command.

![Image of GRBL_tx](https://github.com/bstein2379/m5stack-grbl-uiflow/blob/main/GRBL_tx.png)

Fire:
1. GRBL commands sent from the Faces kit should display on the screen automatically.
2. Copy a GRBL file (ex: circle.nc) to a microSD card and insert it into the Fire. Press the Load button (A) on the Fire should display it on the screen. Press the Rub button (B) to execute the GRBL program.
2. Press the Reset button (C) to clear the screen.

![Image of GRBL_rx](https://github.com/bstein2379/m5stack-grbl-uiflow/blob/main/GRBL_rx.png)

#
Issues:
1. When running the GRBL_rx.m5f program, the M5Stack Fire with GRBL module 13.2 attached seems to reboot every ~3-5 minutes when just sitting idle. I'm unsure why this is happening and haven't had time to troubleshoot it yet.
1. There seems to be a limit in the transmit or receive buffer between the GRBL module and the M5Stack Fire. They communicate internally over I2C (default address 0x70) and I have seen some of the GRBL return messages being truncated (cut off) when printing the GRBL response to the screen. 
#
Other comments:
1. The GRBL module 13.2 is running a really old version of GRBL, which is version 0.7. There should be a away to flash the latest GRBL v1.1 firmware, but I have not tried it yet.  You can see the supported v0.7 GRBL commands here: https://github.com/grbl/grbl/wiki/Configuring-Grbl-v0.8
