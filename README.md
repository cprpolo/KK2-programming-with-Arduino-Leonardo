# KK2-programming-with-Arduino-Leonardo

This repository explains how to flash the kk2.0 1.5 with atmega m644pa.

Instructions: 
(similar to: http://blog.oscarliang.net/flash-kk20-16-firmware-upgrade-arduino/ or http://arduinodev.woofex.net/2013/02/11/how-to-flash-kk-2-0-using-an-arduino-uno/)

1. Download and unzip the kkflash tool for linux:
http://lazyzero.de/en/modellbau/kkmulticopterflashtool

2. Download and unzip the firmware for the KK2 board (.hex file)

3. Load the code of this repository: ISPArduino.ino into the Arduino Leonardo

4. Connect the Arduino to the KK2 board as follows:
Arduino Pin 10 -------- KK2 Board SS / Reset
Arduino Pin 11 -------- KK2 Board MOSI
Arduino Pin 12 -------- KK2 Board MISO
Arduino Pin 13 -------- KK2 Board SCK
(for some reason, it did not work with the ISP pins of the Arduino Leonardo).

5. In the Linux Terminal, browse to the location of the kkflash tool (/lib/avrdude/linux64/avrdude) and run:

avrdude -P /dev/ttyACM0 -b 19200 -c avrisp -p m644p -F -v -e -U flash:w:"/home/kk2.hex":i

where "home/kk2.hex" is the full path to the hex file to the new firmware (notice the inverted commas)

It should start writing if everything is fine.





