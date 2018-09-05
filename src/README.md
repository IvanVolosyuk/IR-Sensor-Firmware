R2 IR Sensor 
==================
###(Based on the OrmerodSensorBoard)

The IR Sensor PCBA uses two IR emitter diodes and one phototransistor to sense the nozzle distance from the build plate.  The circuit is based off Dave Crocker's (dc42) Mini Differential IR board, along with his V1 firmware.  

This folder contains the firmware sources, including the compiled .hex file. The firmware is compiled in Atmel Studio (with the ATTiny library installed). The .pdp files are for doing static checking or formal verification of the firmware using Escher C++ Verifier.  

To program the ATTiny25 mcu, we are using a Tiny Programmer (or JTAGICE MKII) and avrdude to flash the .hex file to the MCU.  

```avrdude -c <programmertype> -p t25 -U flash:w:MiniLedSensor.hex```

To write the fuse value (low fuse):
```avrdude -c <programmertype> -p t25 -U lfuse:w:0xe2:m```

For the schematics for the R2 variant of Dave's board, email developer@robo3d.com.

###Robo does not sell these boards individually!

If you want to get your hands on the latest version of Dave's Mini IR sensor, please check out his blog and follow the links to the appropriate store: https://miscsolutions.wordpress.com/mini-height-sensor-board/

### Upload code
```
avrdude -c usbasp -p t25 -P usb -u -Uflash:w:firmware.hex:a -U lfuse:w:0xe2:m -U hfuse:w:0xdf:m -U efuse:w:0xff:m
```

or just run
```
platformio -t upload
```