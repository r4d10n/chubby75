Colorlight 5A-75B V7.0 Hardware
===============================


Components
----------

* Lattice ECP5 `LFE5U-25F-6BG256C` ([product page](https://www.latticesemi.com/Products/FPGAandCPLD/ECP5))
* Winbond `25Q32JVSIQ`, 32 Mbits SPI flash ([datasheet](datasheets/w25q32jv_spi_revc_08302016.pdf))
* 2x Broadcom `B50612D` Gigabit Ethernet PHYs ([datasheet](datasheets/B50610-DS07-RDS.pdf))
* 2x ESMT `M12L16161A-5T` 1M x 16bit 200MHz SDRAMs (organized as 1M x 32bit) ([datasheet](datasheets/M12L16161A.pdf))  
  or  
  2x WinBond `W9816G6JH-6` 1M x 16bit 166MHz SDRAMs (organized as 1M x 32bit)
  ([datasheet](datasheets/w9816g6jh_a02-1489757.pdf))
* 12x `74HC245T` Octal Bidirectional Transceiver (used for level translation to 5V)


PCB overview
------------

![PCB front](images/cl-5a-75b-v70-front.jpg)
![PCB back](images/cl-5a-75b-v70-back.jpg)


Definitions
-----------


Power
-----


JTAG
----

JTAG is available on a 4-pin header next to the FPGA (U33). VCC/GND are available on a 2-pin header nearby.

| Pin | Function |
|-----|----------|
| J27 | TCK      |
| J31 | TMS      |
| J32 | TDI      |
| J30 | TDO      |
|     |          |
| J33 | *3.3V*   |
| J34 | *GND*    |


SPI Flash
---------


Connections
===========

Clock
-----

A 25MHz clock is available at FPGA pin P6, and is also connected to both PHYs.

SDRAM, U29
----------

| U29 Pin | FPGA Pin |
|---------|----------|
| DQ0     | B13      |
| DQ1     | C11      |
| DQ2     | C10      |
| DQ3     | A11      |
| DQ4     | C9       |
| DQ5     | E8       |
| DQ6     | B6       |
| DQ7     | B9       |
| DQ8     | A6       |
| DQ9     | B5       |
| DQ10    | A5       |
| DQ11    | B4       |
| DQ12    | B3       |
| DQ13    | C3       |
| DQ14    | A2       |
| DQ15    | B2       |
| A0      | A9       |
| A1      | E10      |
| A2      | B12      |
| A3      | D13      |
| A4      | C12      |
| A5      | D11      |
| A6      | D10      |
| A7      | E9       |
| A8      | D9       |
| A9      | B7       |
| A10/AP  | C8       |
| BA      | A7       |
| LDQM    | *GND*    |
| UDQM    | *GND*    |
| CLK     | C6       |
| CKE     | *3.3V*   |
| ~CS     | *GND*    |
| ~RAS    | D7       |
| ~CAS    | E7       |
| ~WE     | C7       |

SDRAM, U32
----------

| U32 Pin | FPGA Pin |
|---------|----------|
| DQ0     | E2       |
| DQ1     | D3       |
| DQ2     | A4       |
| DQ3     | E4       |
| DQ4     | D4       |
| DQ5     | C4       |
| DQ6     | E5       |
| DQ7     | D5       |
| DQ8     | E6       |
| DQ9     | D6       |
| DQ10    | D8       |
| DQ11    | A8       |
| DQ12    | B8       |
| DQ13    | B10      |
| DQ14    | B11      |
| DQ15    | E11      |
| A0      | A9       |
| A1      | E10      |
| A2      | B12      |
| A3      | D13      |
| A4      | C12      |
| A5      | D11      |
| A6      | D10      |
| A7      | E9       |
| A8      | D9       |
| A9      | B7       |
| A10/AP  | C8       |
| BA      | A7       |
| LDQM    | *GND*    |
| UDQM    | *GND*    |
| CLK     | C6       |
| CKE     | *3.3V*   |
| ~CS     | *GND*    |
| ~RAS    | D7       |
| ~CAS    | E7       |
| ~WE     | C7       |

PHY0, U3
----------

| U3 Pin  | FPGA Pin |
|---------|----------|
| GTXCLK  | M2       |
| TXD[0]  | L1       |
| TXD[1]  | L3       |
| TXD[2]  | P2       |
| TXD[3]  | L4       |
| TX\_EN  | M3       |
| RXC     | M1       |
| RXD[0]  | N1       |
| RXD[1]  | M5       |
| RXD[2]  | N5       |
| RXD[3]  | M6       |
| RXD\_DV | N6       |
| MDC     | P3       |
| MDIO    | T2       |
| ~RESET  | P5       |

PHY1, U7
----------

| U7 Pin  | FPGA Pin |
|---------|----------|
| GTXCLK  | M12      |
| TXD[0]  | T14      |
| TXD[1]  | R12      |
| TXD[2]  | R13      |
| TXD[3]  | R14      |
| TX\_EN  | R15      |
| RXC     | M16      |
| RXD[0]  | P13      |
| RXD[1]  | N13      |
| RXD[2]  | P14      |
| RXD[3]  | M15      |
| RXD\_DV | L15      |
| MDC     | P3       |
| MDIO    | T2       |
| ~RESET  | P5       |

Buffers
-------


LED, Button
-----------

There is a general purpose, FPGA controlled LED (DATA_LED-) at P11, active low (FPGA pin should be set to open drain).

Additionally, there is a button (J28, KEY+). When M13 is an input, pressing the button will read low, otherwise it will read high.

Connector J1
--------------

| J1 Pin| HUB75 pin | FPGA Pin | Buffer                         | Notes                         |
|-------|-----------|----------|--------------------------------|-------------------------------|
| 1     | R0        |  F3      |                                | Bank 7 - PL5D / -             |
| 2     | G0        |  F1      |                                | Bank 7 - __PL14A__ / -        |
| 3     | B0        |  G3      |                                | Bank 7 - __PL14C__ / VREF1_7  |
| 4     | *GND*     |  *GND*   |                                | -                             |
| 5     | R1        |  G2      |                                | Bank 7 - __PL14B__ / -        |
| 6     | G1        |  H3      |                                | Bank 7 - __PL14D__ / -        |
| 7     | B1        |  H5      |                                | Bank 7 - PL17A / -            |
| 8     | E         |  F15     |                                | Bank 2 - PR11C / -            |
| 9     | A         |  L2      |                                | Bank 6 - PL26B / PCLKC6_1     |
| 10    | B         |  K1      |                                | Bank 7 - __PL23C__ / PCLKT7_0 |
| 11    | C         |  J5      |                                | Bank 7 - PL17D / -            |
| 12    | D         |  K2      |                                | Bank 7 - __PL23D__ / PCLKC7_0 |
| 13    | CLK       |  B16     |                                | Bank 2 - PR2A / -             |
| 14    | STB       |  J14     |                                | Bank 2 - PR20C / GR_PCLK2_0   |
| 15    | OE        |  F12     |                                | Bank 2 - PR8D / -             |
| 16    | *GND*     |  *GND*   |                                | -                             |


Connector J2
--------------

| J2 Pin| HUB75 pin | FPGA Pin | Buffer                         | Notes                         |
|-------|-----------|----------|--------------------------------|-------------------------------|
| 1     | R0        |  J4      |                                | Bank 7 - __PL17C__ / -        |
| 2     | G0        |  K3      |                                | Bank 7 - PL20D / -            |
| 3     | B0        |  G1      |                                | Bank 7 - PL20A / GR_PCLK7_1   |
| 4     | *GND*     |  *GND*   |                                | -                             |
| 5     | R1        |  K4      |                                | Bank 6 - PL29A / GR_PCLK6_0   |
| 6     | G1        |  C2      |                                | Bank 7 - PL5B / -             |
| 7     | B1        |  E3      |                                | Bank 7 - PL5C / -             |
| 8     | E         |  F15     |                                | Bank 2 - PR11C / -            |
| 9     | A         |  L2      |                                | Bank 6 - PL26B / PCLKC6_1     |
| 10    | B         |  K1      |                                | Bank 7 - __PL23C__ / PCLKT7_0 |
| 11    | C         |  J5      |                                | Bank 7 - __PL17D__ / -        |
| 12    | D         |  K2      |                                | Bank 7 - __PL23D__ / PCLKC7_0 |
| 13    | CLK       |  B16     |                                | Bank 2 - PR2A / -             |
| 14    | STB       |  J14     |                                | Bank 2 - PR20C / GR_PCLK2_0   |
| 15    | OE        |  F12     |                                | Bank 2 - PR8D / -             |
| 16    | *GND*     |  *GND*   |                                | -                             |


Connector J3
--------------

| J3 Pin| HUB75 pin | FPGA Pin | Buffer                         | Notes                         |
|-------|-----------|----------|--------------------------------|-------------------------------|
| 1     | R0        |  H4      |                                | Bank 7 - PL17B / -            |
| 2     | G0        |  K5      |                                | Bank 6 - PL29B / -            |
| 3     | B0        |  P1      |                                | Bank 6 - __PL35A__ / -        |
| 4     | *GND*     |  *GND*   |                                | -                             |
| 5     | R1        |  R1      |                                | Bank 6 - __PL35B__ / VREF1_6  |
| 6     | G1        |  L5      |                                | Bank 6 - PL29D / -            |
| 7     | B1        |  F2      |                                | Bank 7 - PL11C / -            |
| 8     | E         |  F15     |                                | Bank 2 - PR11C / -            |
| 9     | A         |  L2      |                                | Bank 6 - PL26B / PCLKC6_1     |
| 10    | B         |  K1      |                                | Bank 7 - __PL23C__ / PCLKT7_0 |
| 11    | C         |  J5      |                                | Bank 7 - PL17D / -            |
| 12    | D         |  K2      |                                | Bank 7 - __PL23D__ / PCLKC7_0 |
| 13    | CLK       |  B16     |                                | Bank 2 - PR2A / -             |
| 14    | STB       |  J14     |                                | Bank 2 - PR20C / GR_PCLK2_0   |
| 15    | OE        |  F12     |                                | Bank 2 - PR8D / -             |
| 16    | *GND*     |  *GND*   |                                | -                             |


Connector J4
--------------

| J4 Pin| HUB75 pin | FPGA Pin | Buffer                         | Notes                         |
|-------|-----------|----------|--------------------------------|-------------------------------|
| 1     | R0        |  P4      |                                | Bank 6 - PL41A / -            |
| 2     | G0        |  R2      |                                | Bank 6 - PL38C / -            |
| 3     | B0        |  M8      |                                | Bank 8 - PB15B / DOUT/CSON    |
| 4     | *GND*     |  *GND*   |                                | -                             |
| 5     | R1        |  ?       |                                | ?                             |
| 6     | G1        |  T6      |                                | Bank 8 - __PB4A__ / D7/IO7    |
| 7     | B1        |  R6      |                                | Bank 8 - __PB4B__ / D6/IO6    |
| 8     | E         |  F15     |                                | Bank 2 - PR11C / -            |
| 9     | A         |  L2      |                                | Bank 6 - PL26B / PCLKC6_1     |
| 10    | B         |  K1      |                                | Bank 7 - __PL23C__ / PCLKT7_0 |
| 11    | C         |  J5      |                                | Bank 7 - PL17D / -            |
| 12    | D         |  K2      |                                | Bank 7 - __PL23D__ / PCLKC7_0 |
| 13    | CLK       |  B16     |                                | Bank 2 - PR2A / -             |
| 14    | STB       |  J14     |                                | Bank 2 - PR20C / GR_PCLK2_0   |
| 15    | OE        |  F12     |                                | Bank 2 - PR8D / -             |
| 16    | *GND*     |  *GND*   |                                | -                             |


Connector J5
--------------

| J5 Pin| HUB75 pin | FPGA Pin | Buffer                         | Notes                         |
|-------|-----------|----------|--------------------------------|-------------------------------|
| 1     | R0        | M11      |                                | Bank 3 - __PR47A__ / -        |
| 2     | G0        | N11      |                                | Bank 3 - __PR47B__ / -        |
| 3     | B0        | P12      |                                | Bank 3 - PR47D / LRC_GPLL0C_IN|
| 4     | *GND*     | *GND*    |                                | -                             |
| 5     | R1        | K15      |                                | Bank 2 - PR23D / PCLKC2_0     |
| 6     | G1        | N12      |                                | Bank 3 - PR44D / -            |
| 7     | B1        | L16      |                                | Bank 3 - __PR26A__ / PCLKT3_1 |
| 8     | E         | F15      |                                | Bank 2 - PR11C / -            |
| 9     | A         | L2       |                                | Bank 6 - __PL26B__ / PCLKC6_1 |
| 10    | B         | K1       |                                | Bank 7 - __PL23C__ / PCLKT7_0 |
| 11    | C         | J5       |                                | Bank 7 - PL17D / -            |
| 12    | D         | K2       |                                | Bank 7 - __PL23D__ / PCLKC7_0 |
| 13    | CLK       | B16      |                                | Bank 2 - PR2A / -             |
| 14    | STB       | J14      |                                | Bank 2 - PR20C / GR_PCLK2_0   |
| 15    | OE        | F12      |                                | Bank 2 - PR8D / -             |
| 16    | *GND*     | *GND*    |                                | -                             |


Connector J6
--------------

| J6 Pin| HUB75 pin | FPGA Pin | Buffer                         | Notes                         |
|-------|-----------|----------|--------------------------------|-------------------------------|
| 1     | R0        | K16      |                                | Bank 2 - PR23C / PCLKT2_0     |
| 2     | G0        | J15      |                                | Bank 2 - __PR23B__ / PCLKC2_1 |
| 3     | B0        | J16      |                                | Bank 2 - __PR23A__ / PCLKT2_1 |
| 4     | *GND*     | *GND*    |                                | -                             |
| 5     | R1        | J12      |                                | Bank 2 - PR17D / -            |
| 6     | G1        | H15      |                                | Bank 2 - __PR20B__ / -        |
| 7     | B1        | G16      |                                | Bank 2 - __PR20A__ /GR_PCLK2_1| 
| 8     | E         | F15      |                                | Bank 2 - PR11C / -            |
| 9     | A         | L2       |                                | Bank 6 - PL26B / PCLKC6_1     |
| 10    | B         | K1       |                                | Bank 7 - __PL23C__ / PCLKT7_0 |
| 11    | C         | J5       |                                | Bank 7 - PL17D / -            |
| 12    | D         | K2       |                                | Bank 7 - __PL23D__ / PCLKC7_0 |
| 13    | CLK       | B16      |                                | Bank 2 - PR2A / -             |
| 14    | STB       | J14      |                                | Bank 2 - PR20C / GR_PCLK2_0   |
| 15    | OE        | F12      |                                | Bank 2 - PR8D / -             |
| 16    | *GND*     | *GND*    |                                | -                             |


Connector J7
--------------

| J7 Pin| HUB75 pin | FPGA Pin | Buffer                         | Notes                         |
|-------|-----------|----------|--------------------------------|-------------------------------|
| 1     | R0        | H13      |                                | Bank 2 - __PR17B__ / -        |
| 2     | G0        | J13      |                                | Bank 2 - PR17C / -            |
| 3     | B0        | H12      |                                | Bank 2 - __PR17A__ / -        |
| 4     | *GND*     | *GND*    |                                | -                             |
| 5     | R1        | G14      |                                | Bank 2 - __PR14C__ / VREF1_2  |
| 6     | G1        | H14      |                                | Bank 2 - __PR14D__ / -        |
| 7     | B1        | G15      |                                | Bank 2 - PR14B / -            |
| 8     | E         | F15      |                                | Bank 2 - PR11C / -            |
| 9     | A         | L2       |                                | Bank 6 - PL26B / PCLKC6_1     |
| 10    | B         | K1       |                                | Bank 7 - __PL23C__ / PCLKT7_0 |
| 11    | C         | J5       |                                | Bank 7 - PL17D / -            |
| 12    | D         | K2       |                                | Bank 7 - __PL23D__ / PCLKC7_0 |
| 13    | CLK       | B16      |                                | Bank 2 - PR2A / -             |
| 14    | STB       | J14      |                                | Bank 2 - PR20C / GR_PCLK2_0   |
| 15    | OE        | F12      |                                | Bank 2 - PR8D / -             |
| 16    | *GND*     | *GND*    |                                | -                             |


Connector J8
--------------

| J8 Pin| HUB75 pin | FPGA Pin | Buffer                         | Notes                         | 
|-------|-----------|----------|--------------------------------|-------------------------------|
| 1     | R0        | A15      |                                | Bank 1 - __PT67B__ / -        |
| 2     | G0        | F16      |                                | Bank 2 - PR14A / -            |
| 3     | B0        | A14      |                                | Bank 1 - __PT65B__ / -        |
| 4     | *GND*     | *GND*    |                                | -                             |
| 5     | R1        | E13      |                                | Bank 1 - PT62B / -            |
| 6     | G1        | B14      |                                | Bank 1 - __PT67A__ / -        |
| 7     | B1        | A13      |                                | Bank 1 - __PT65A__ / -        |
| 8     | E         | F15      |                                | Bank 2 - PR11C / -            |
| 9     | A         | L2       |                                | Bank 6 - PL26B / PCLKC6_1     |
| 10    | B         | K1       |                                | Bank 7 - __PL23C__ / PCLKT7_0 |
| 11    | C         | J5       |                                | Bank 7 - PL17D / -            |
| 12    | D         | K2       |                                | Bank 7 - __PL23D__ / PCLKC7_0 |
| 13    | CLK       | B16      |                                | Bank 2 - PR2A / -             |
| 14    | STB       | J14      |                                | Bank 2 - PR20C / GR_PCLK2_0   |
| 15    | OE        | F12      |                                | Bank 2 - PR8D / -             |
| 16    | *GND*     | *GND*    |                                | -                             |

