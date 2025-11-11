# Flipper Zero JTAG/SWD/SPI breakout

A simple breakout board to connect a Flipper Zero to JTAG/SWD/SPI targets.

OSHW ID : TBD

## Table of Contents

- [Features](#features)
  - [Compatible Apps](#compatible-apps)
  - [Pin selection](#pin-selection)
- [Pinouts](#pinouts)
  - [Flipper Zero GPIO header](#flipper-zero-gpio-header)
  - [20 pin JTAG 2x10 0.1" header](#20-pin-jtag-2x10-01-header)
  - [10 pin JTAG/SWD 2x5 0.1" and 0.05" header](#10-pin-jtagswd-2x5-01-and-005-header)
  - [6 pin SWD 2x3 0.1" header](#6-pin-swd-2x3-01-header)
  - [6 pin SPI 2x3 0.1" header](#6-pin-spi-2x3-01-header)
  - [5 pin UART 1x5 0.1" header](#5-pin-uart-1x5-01-header)
- [Usage](#usage)
- [Building Instructions](#building-instructions)
- [Sources](#sources)
- [License & Acknowledgements](#license--acknowledgements)

## Features

Convert the Flipper Zero's GPIO port into standard headers for JTAG, SWD, SPI, and UART connections.

### Compatible Apps

The board should be compatible with any apps that use the Flipper Zero's GPIO port for JTAG/SWD/SPI communication, though the following where the main targets during development for the pin selection and configuration :

- [DAP Link](https://github.com/flipperdevices/flipperzero-good-faps/tree/dev/dap_link) (JTAG/SWD & UART)
- [SWD Probe](https://github.com/xMasterX/all-the-plugins/tree/dev/base_pack/swd_probe) (SWD)
- [SPI Mem Manager](https://github.com/flipperdevices/flipperzero-good-faps/tree/dev/spi_mem_manager) (SPI)
- [SPI-Terminal](https://github.com/janwiesemann/flipper-spi-terminal) (SPI)
- [UART Terminal](https://github.com/xMasterX/all-the-plugins/tree/dev/base_pack/uart_terminal) (UART)
- [ESP Flasher](https://github.com/0xchocolate/flipperzero-esp-flasher) (UART)

### Pin selection

Depending on the app's requirements, some signals can be connected to different GPIO pins of the Flipper Zero using solder jumpers (see assembly instructions/schematics) :

- The TCK signal can be connected to GPIO 2 or GPIO 10
- The TMS signal can be connected to GPIO 3 or GPIO 12
- The UART TX pin can be connected to GPIO 13 or GPIO 15
- The UART RX pin can be connected to GPIO 14 or GPIO 16
- The SPI CS pin can be connected to GPIO 4

Other pins can be configured with jumper shunts :

- The VTref signal can be connected to 3.3V, 5V, or left floating
- The PWRSel signal can be connected to 5V or GND depending on the target's pinout
- The nTRST signal on the 10 pin headers can be connected to nTRST or left floating (NC)
- The SPI CS signal on the 6 pin SPI header can be connected to GPIO 4 or GPIO 6

> Note : Not all signals are used bu the Flipper Zero apps, but the board can also be used to convert from a 20-pin ARM JTAG connector to 10 or 6 pin headers.

## Pinouts

### Flipper Zero GPIO header

| Pin | Signals               |
|-----|-----------------------|
| 1   | 5V                    |
| 2   | SPI-SDO, *JTAG-TCK*   |
| 3   | SPI-SDI, *JTAG-TMS*   |
| 4   | *SPI-CS*, JTAG-nRESET |
| 5   | SPI-SCK, JTAG-TDO     |
| 6   | *SPI-CS*, JTAG-TDI    |
| 7   | NC                    |
| 8   | GND                   |
| 9   | 3.3V                  |
| 10  | *JTAG-TCK*            |
| 11  | GND                   |
| 12  | *JTAG-TMS*            |
| 13  | *UART_TX*             |
| 14  | *UART-RX*             |
| 15  | *UART-TX*             |
| 16  | *UART-RX*             |
| 17  | NC                    |
| 18  | GND                   |

> Note : *Italic* pins are configurable with the solder jumpers

### 20 pin JTAG 2x10 0.1" header

| Signal    | Pin | Pin | Signal |
|-----------|-----|-----|--------|
| VTref     | 1   | 2   | NC     |
| nTRST     | 3   | 4   | GND    |
| TDI       | 5   | 6   | GND    |
| TMS       | 7   | 8   | GND    |
| TCK       | 9   | 10  | GND    |
| RTCK      | 11  | 12  | GND    |
| TDO       | 13  | 14  | GND    |
| nRESET    | 15  | 16  | GND    |
| NC        | 17  | 18  | GND    |
| 5V-Supply | 19  | 20  | GND    |

### 10 pin JTAG/SWD 2x5 0.1" and 0.05" header

| Signal     | Pin | Pin | Signal |
|------------|-----|-----|--------|
| VTref      | 1   | 2   | TMS    |
| GND        | 3   | 4   | TCK    |
| *PWRSel*   | 5   | 6   | TDO    |
| RTCK       | 7   | 8   | TDI    |
| *nTRST/NC* | 9   | 10  | nRESET |

### 6 pin SWD 2x3 0.1" header

| Signal | Pin | Pin | Signal |
|--------|-----|-----|--------|
| VTref  | 1   | 2   | TMS    |
| nRESET | 3   | 4   | TCK    |
| GND    | 5   | 6   | TDO    |

### 6 pin SPI 2x3 0.1" header

| Signal | Pin | Pin | Signal  |
|--------|-----|-----|---------|
| SDI    | 1   | 2   | VTref   |
| SCK    | 3   | 4   | SDO     |
| *CS*   | 5   | 6   | GND     |

The CS pin can be connected to GPIO 4 or GPIO 6 of the Flipper Zero, depending on the app's requirements.

### 5 pin UART 1x5 0.1" header

| Pin | Signal |
|-----|--------|
| 1   | 5V     |
| 2   | 3.3V   |
| 3   | TX     |
| 4   | RX     |
| 5   | GND    |

## Usage

> TODO : Add usage instructions for some Flipper Zero apps (e.G. DAP Link, SPI mem manager, etc.)

## Building Instructions

> TODO : Add assembly instructions and wiring diagrams from KiCAD sources (awaiting OSHWA certification).

## Sources

- [Flipper Zero Documentation](https://docs.flipperzero.one/)
- [Segger JTAG pinouts](https://www.segger.com/products/debug-probes/j-link/technology/interface-description/)
- [ARM JTAG/SWD pinouts](https://developer.arm.com/documentation/dui0499/d/ARM-DSTREAM-Target-Interface-Connections/)
- [AVR ISP pinouts](https://www.microchip.com/en-us/development-tool/atavrisp2)

## License & Acknowledgements

Made with ❤️, lots of ☕️, and lack of 🛌  
Published under CreativeCommons BY-SA 4.0

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)  
This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
