
## Overview

This is a port of the Smoothieware bootloader to the fabbster cnc4nf-mb rev. 1.1 board.

Smoothie is a free, opensource, high performance G-code interpreter and CNC controller written in object-oriented C++ for the LPC17xx micro-controller ( ARM Cortex M3 architecture ).

Documentation can be found here: http://smoothieware.org/

## Quick Start

These are the quick steps to get the bootloader installed on your cnc4nf-mb rev. 1.1 board:

### Flashing the Bootloader

##### Recommended method
Use a JTAG debugger (for example the SEGGER JLink or any other JTAG adapter) to flash the bootloader binary to your cnc4nf-mb board at address 0x00000. There is a standard 20 pin JTAG connector on the board (the connector is approx. in the middle of the board, you cannot miss it).

The original firmware will be deleted if you flash the bootloader. In order to be able to restore the original fabbster firmware you should save the flash locations 0x00000 to 0x80000 (512k) to a file before flashing the Smoothie bootloader.

The bootloader binary can be found in the FirmwareBin directory.

##### Alternative method
Alternatively you can use the LPC1768 ISP via UART0. You need to remove R91 and possibly C50 as well as lift pin 6 of U9 (output of OpAmp) and possibly remove C47. Connect the RxD0 and TxD0 processor pins to your USB/serial adapter. Short circuit the pins marked with ISP/S3 and power on the board. The processor should enter ISP mode. Use FlashMagic or lpc21isp to flash the bootloader. Re-solder the removed components after you are done flashing the bootloader.

**Note:** The ISP method is complicated and should be used by experienced users only. You need to know what you are doing.
  
### Flashing the Smoothie Firmware

The ported Smoothieware that runs on the fabbster board can be found here:  
https://github.com/acurana/Smoothieware/tree/port/fabbster-board-rev-1.1

After installing the bootloader the firmware can be placed on the SD card as outlined here:  
http://smoothieware.org/flashing-smoothie-firmware

Do not forget to put the fabbster config file on the SD-card as well. It can be found in the ConfigSamples/fabbsterG directory of the Smoothieware fabbster-board-rev-1.1 branch.