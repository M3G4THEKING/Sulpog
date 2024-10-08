# Sulpog
Pokemon GO Plus emulator using ESP32 with display (fork).

This project is a DIY clone of the Pokémon Go Plus device, designed to interact with the Pokémon Go app. It uses an ESP32 board as its core, leveraging its Bluetooth capabilities to communicate with the mobile game. 

![Alt text](Sulpogs.jpg?raw=true "Sulpogs")

![Alt text](Sulpogs2.jpg?raw=true "Sulpogs (alt case)")

![Alt text](Diagram.png?raw=true "Diagram")

## Features
This fork adds some features:

* Fully working GUI
* Statistics on screen: caught, spins and flees
* Displays timer
* Displays battery capacity
* 60 seconds to connect
* Stays on while charging
* Setting: turn on/off display
* Setting: change GUI color
* Setting: toggle between multiple PGP secrets (hold 'display on/off' and press power button)

## Known issues
* ~~Battery will drain in sleep mode (unfortunately, you cannot turn the ESP32 off)~~
* ~~Buttons on the 3D printed case are very fragile~~

## Requirements
Below is a comprehensive list of the components needed to build your own Sulpog.

### Board
The heart of the project, providing Bluetooth connectivity, processing power, and GPIO pins for interfacing with other components.

[LilyGO TTGO T-Display with TFT Display](https://aliexpress.com/item/33048962331.html)

### Case
Although not an electronic component, a custom-designed 3D printed case can house the ESP32 and other components.

[Large case, 852540 by Stevesch](https://www.thingiverse.com/thing:4183337)

@rhuba8324 has developed an improved version of the case for the TTGO T-Display, addressing some known issues. This includes the following improvements:

* This case has been revised to better withstand the USB-C cable being pulled out and accommodates T-Displays with screens in slightly different positions.
* A slot for a switch button has been added to the case.
* The buttons have been reinforced to prevent them from breaking easily during use.

[Alternative case by @rhuba8324](https://www.printables.com/model/817468-ttgo-t-display-cases)

### Battery
A battery such as MakerFocus 4pcs 3.7V Lithium Rechargeable Battery JST1.25 Connector 2pin, 952540 3.7V 1000mAh Battery with Protection Board and Insulated Rubber Tape Compatible with ESP32 Development Board.

[MakerFocus 3.7V Lithium Rechargeable Battery](https://www.amazon.com/dp/B07CXNQ3ZR/ref=cm_sw_em_r_mt_dp_U_0XovEbVB7EPGM)

## Get started
Use [Suota-Go-Plus](https://github.com/Jesus805/Suota-Go-Plus) to extract the keys. Download and install the APK Suota Go+ 1.0 from there and follow the instructions at the bottom. If you get an error at step 10, pair the device manually, then it works.

Add the keys in [main/secrets.c](main/secrets.c).

Install [ESP-IDF](https://docs.espressif.com/projects/esp-idf/en/release-v4.3/esp32/get-started/index.html) and use version 4.3. Newer versions are not tested and might not work correctly.

I will not explain here how to build and flash, as it is documented in the guide above.

Run command to get a config file.
```
idf menuconfig
```

The TTGO T-Display should be selected by default. To change it, select 'TFT_display_configuration', then 'Select predefined display configuration' and choose the device you have. You can now build and flash the software.

Device specific configuration can be changed in [components/tft/tftspi.h](components/tft/tftspi.h).

## Commands
Build
```
idf build
```

Flash
```
idf -b 115200 -p <PORT> flash
```

Monitor
```
idf monitor -p <PORT>
```

## Links
Go Plus emulator\
https://github.com/yohanes/pgpemu

ESP32 TFT Display library\
https://github.com/loboris/ESP32_TFT_library

## License

MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
