OVERVIEW
--------
![alt text](http://circuitcellar.com/wp-content/uploads/2016/10/FTDI-Img.png "riverdi-logo")

*riverdi-eve-lib* is an easy-to-use C library for the [*Riverdi Intelligent Display*](https://riverdi.com/product-category/intelligent-displays/bt817q/) driven by [*Bridgetek EVE graphics controllers*](http://brtchip.com/eve/):

- __EVE 1__ series: FT800 and FT801,
- __EVE 2__ series: FT810, FT811, FT812 and FT813,
- __EVE 3__ series: BT815 and BT816,
- __EVE 4__ series: BT817 and BT818

Library supports instructions in a similar format to the [*FT80x and FT81x Series Programmers Guides*](https://brtchip.com/wp-content/uploads/Support/Documentation/Programming_Guides/ICs/EVE/FT81X_Series_Programmer_Guide.pdf), [*BT81X Series Programming Guide*](https://brtchip.com/wp-content/uploads/2022/12/BRT_AN_033_BT81X-Series-Programming-Guide.pdf) and the [*EVE Screen Editor*](https://brtchip.com/ese-2/).

LIBRARY ARCHITECTURE
--------------------

#### API Layer

This layer is designed to allow the main application to use syntax close to that of the *FT80X/FT81X/BT81X Programmers Guide* and make it more user friendly. The functions provided in this layer handle co-processor operation and assist with creating and executing co-processor lists as well as keeping track of the offset within the FIFO for each command and sending parameters of commands such as text strings.

#### EVE Layer

This layer translates the calls from the API layer above into a series of SPI byte transfers formatted for the protocol used by the FT8XX/BT8XX. It includes a series of functions which send the register address as well as for reading and writing 8/16/32-bit values. It also has functions for checking the read and write pointers of the RAM_CMD FIFO and for checking the free space available, which are used by the layers above.

LIBRARY INTEGRATION
-------------------

To integrate *riverdi-eve-lib* with your own hardware (microcontroller, single board computer, ...), everything what you need to do is to provide an interface to the hardware (by adding platform.c and platform.h files), which takes the SPI transfers from the EVE layer and translates them into the low-level operations (SPI and GPIO operations for chip select and power down). Please check ready-to-use examples of *riverdi-eve-lib* library integration for such platforms like: [*RP2040*](https://github.com/riverdi/riverdi-eve-demo-rp2040), [*ESP32*](https://github.com/riverdi/riverdi-eve-demo-esp32) or [*Raspberry Pi*](https://github.com/riverdi/riverdi-eve-demo-rpi)

GETTING HELP
------------

Please contact Riverdi support - [*<contact@riverdi.com>*](contact@riverdi.com)

LICENSE
-------

See *LICENSE.txt* file for details.

