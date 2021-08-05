# le_chiff_ble
## What is this? 
This is a drop-in replacement PCB for [tominabox1's](https://github.com/tominabox1) Le Chiffre keyboard, one of my all time favourite boards. I redesigned the existing PCB from top up and added bluetooth. 
Please be so kind and check out the [original repo](https://github.com/tominabox1/Le-Chiffre-Keyboard) and leave a star. This is where you can also find case files for this PCB. 
Some of the footprints are not taken from the standard kicad libraries, huge thanks to [foostan](https://github.com/foostan) for making the awesome "kbd" library and to [ai03](https://ai03.com/) for their super nice footprint libraries, the minew symbol and footprints are by [oreore](https://github.com/ogatatsu).

All graphics on my PCB are handdrawn. 
## State of the project
### implemented
- charging circuit is working
- MCU connects via bluetooth and USB
- all features have been tested and are working, including OLED and Encoder
### open tasks
- PCB will get a polish soon, I'll remove unnecessary silkscreen
- bootloader and zmk firmware need to be added to the repo, I'll do that when I transformed the zmk firmware from my zmk fork to building online which will be easier for the enduser. If you're impatient, find the zmk firmware on [my zmk fork](https://github.com/MangoIV/zmk)
- the widgets in zmk for the OLED are still very basic, I'd like to do something to make them look better, this will be added after I finished and uploaded the firmware 
## How can I obtain one
- Gerbers are supplied, be free to order them with the PCB manufacturer you want
### you will need parts: 
1. **Resistors, footprint is 0805:**
  - 1x 2M
  - 1x 1M
  - 1x 806k
  - 1x 100k
  - 2x 5.1k
  - 1x 1.8k 
  - 3x 1k
  - 2x 100
  - 1x 2.1
2. **Capacitors, footprint is 0805**
  - 4x 10uF
  - 2x 1uF
  - 2x 0.1uF
  - 1x 1nF
3. **Diodes**
  - 35x SOD123 for the switches and encoder
  - 1x Schottky, SOD323, should be low voltage drop
  - either 2x in switch LEDs or 2x 0805 SMD LEDs for the charging indicator
4. 1x PMOS, A03401A
5. 1x battery management chip, TP4056, footprint is SOP-8-PP
6. 1x LDO, XC6206PxxMR
7. 1x usblc6, footprint is sot-23-6
8. 1x 500mA Fuse, footprint is 1206/ 3216Metric
9. 1x battery protection IC DW01A, footprint is sot-23-6
10. 1x two nmos with gates connects FS8205, footprint is sot-23-6
11. 1x Minew MS88SF2, be careful to choose the version with nrF52840, there's also another version with the same name which won't work
12. 1x USB type c port, 12 pin
13. 1x MSK-12C02 smd toggle switch
14. 1x SW SPST TL3342 push switch for reset
15. 34-35 MX/alps/choc switches depending on whether you use the encoder or not
16. Battery connector with 1.25mm pitch, choose whichever you're fine with
17. optional: 1x Encoder, 1x 128x32 OLED
## How do I build one? 
- solder all components
- flash bootloader (I liked [this one](https://github.com/adafruit/Adafruit_nRF52_Bootloader) a lot, it's fairly easy to modify to your needs, my fork will be supplied soon)
- plug into PC and test whether everything is working, flash Firmware 
- plug in battery, plug in PC again to unlock DW01A (this needs to be done everytime you physically disconnect the PCB from the battery)
- be careful to adjust resistor value of the tp4056 when you take different battery sizes, I chose 1Ah which works fine with the specified resistor values
- verify charging and bluetooth works 
- continue building as if this was a "normal" chiffre
