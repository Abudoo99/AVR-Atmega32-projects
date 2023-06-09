# AVR Atmega32 Development Kit Projects
This repository contains projects performed using the AVR Atmega32 Development Kit 

![666px-DSC00544](https://user-images.githubusercontent.com/69448986/231144271-ad52810e-aac2-419c-9e65-77c923ca9533.jpg)

_Note: All these projects are executed in Ubuntu18.04_

Hardware Setup
---------------
1. Connect the jumper to power the board using USB power mode.
2. Connect the Programmer across the ISP connector.
3. Connect the mini-B USB cable to the other end of the programmer
4. Continue with flashing the devices.
5. Once the flashing process is over, disconnect the programmer and power the board with USB Cable.

Preparing Packages
--------------------
 	sudo apt update
 	sudo apt-get install gcc-avr 
 	sudo apt-get install avr-libc
 	sudo cp avrdude /usr/bin/
 	sudo cp avrdude.conf /etc/
	
Create symlink for the libread.so.7

	sudo ln -sf /lib/x86_64-linux-gnu/libread.so.7 /lib/x86_64-linux-gnu/libread.so.6

Commands to build and flash code
-----------------
If the code is present in blink.c, run the following commands :

	avr-gcc -mmcu=atmega32 -Wall -Os -o blink.elf blink.c 
	avr-objcopy -j .text -j .data -O ihex blink.elf blink.hex
	sudo avrdude -p m32 -c usbtiny -P usb -U flash:w:blink.hex -v

**********************************************************************************************

