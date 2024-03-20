# PowerPiNano
The PowerPiNano is a development Board based on the RP2040 microcontroller, except it's highly customizable with pull-up/down resistor networks, "high" current capable GPIOs and flash memory up to 16MB.

## The very first revision (fully functional though with visual design errors, fixed for V1.1):
![PowerPiNano](https://github.com/stefarrn/PowerPiNano/assets/80580541/a2fce6cd-a498-4956-8dee-874aa5448d65)

## Pin Description:

#### General purpose IO pins (GPIO):
All pins marked with the Öetter "G" are general purpose IO-pins, with the number correspind to the GPIO pin number of the IC

#### Optional pull-up/down resistors:
G0 to G3 and G4 to G7 each have a footprint for pull-up/down resistor networks respectivley, which can be populated or left unpopulated by personal preference

#### "High" current output pins:
All Pins marked with an "O" are "high" current output only pins, which also have an LED attached for easy debugging without needing to probe the pins. They are directly connected to the collector of MMBT3904 NPN transistors. They therefore switch to GND when the corresponding GPIO number is toggled HIGH by the IC, switching the corresponding GPIO LOW or floating will result in the output Pin being pulled HIGH through the LED. The output pins are suitable for switching up to 40V at 200mA (recommended 30V at 100mA).

#### Analog input pins:
Pins A26 to A29 are the four inputs to the analog to digital converter (ADC) of the RP2040. The reference voltage of the RP2040 is directly ried to 3V3.

#### Power pins:
The pins marked 3V3 and GND are exactly what you'd expect. The board can be externally powered (only 3,3V!) through one of the 3V3 pins, as long as it is not simoutanously being powered through USB or the V_EXT pin.

#### V_EXT pin:
The V_EXT pin is directly connected to the input of the onboard 3,3V regulator and is intended for powering the board from an external powersource. CAUTION: V_EXT is directly connected to the 5V pin of the USB connector, NEVER power the board through V_EXT if any USB device is connected. if the board is powered through USB V_EXT can be used as a 5V output pin.

## Setup
When the Board is being flashed for the first time after assembly, the BOOT Button needs to be held down while plugging it in in order to put the RP2040 in boot mode. It should then show up as a USB storage device, and flashing any code onto it will also flash the bootloader, such that it will not need to be put into boot mode for future programming.

It is also highly recommended to check all voltage rails aswell as the USB datalines for shorts before plugging a freshly assembled Board in for the first time.

## Troubleshooting
If the Board does not show up as a USB storage device after plugging it in while holding down the boot button
1. unplug it and try again
2. make sure all voltage rails are present, including the 1,1V core voltage
3. check for solder bridges between the data pins of the USB connector
4. try plugging the board into a device running linux, windows sometimes refuses to detect the devices as USB storage

#### Sources used:
- The amazing documentation for the RP2040 microcontroller: https://datasheets.raspberrypi.com/rp2040/hardware-design-with-rp2040.pdf
- 3D-Model for the SMD Button: https://grabcad.com/library/tactile-switches-6mm-smt-1
- 3D-Model for the mini USB connector: https://grabcad.com/library/two-type-of-mini-usb-receptacle-type-b-5-pin-1
