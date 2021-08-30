# Board components

## Featured devices

The board features several NXP ICs:

* **MC33772**: 6-Channel Li-Ion battery cell controller IC designed for automotive and industrial applications such as HEV, EV, ESS, UPS systems. The MC33772 allows ADC conversions on the differential cell voltages and currents as well as coulomb counting and temperature measurements. It features embedded balancing transistors and diagnostics to simplify applications. The device supports standard SPI and transformer isolated daisy chain communication \(via MC33664\) to an MCU for processing and control



* **S32K144**: AEC-Q100 certified microcontroller for general purpose automotive applications. The S32K144 features an Arm® Cortex®- M4F core, 512 KB of Flash, CAN/CAN-FD controllers, security module complying with SHE specification and is offered in LQFP-48, LQFP-64, LQFP-100 and MAPBGA-100 packages supporting an ambient temperature range from -40°C up to 125°C



* **UJA1169**: Mini high-speed CAN System Basis Chip \(SBC\) containing an ISO 11898-2:201x \(upcoming merged ISO 11898-2/5/6\) compliant HS-CAN transceiver and an integrated 5V or 3.3V 250 mA scalable supply \(V1\) for a microcontroller and/ or other loads. It also features a watchdog and a Serial Peripheral Interface \(SPI\). The UJA1169 can be operated in very low-current Standby and Sleep modes with bus and local wake-up capability



* **A1007**: A1007 authentication IC is a secure solution built with many tamper resistant features and security countermeasures to deter common invasive and non-invasive attacks



* **NTAG5**: NXP’s NTAG 5 boost shrinks the NFC footprint while adding AES security, so designers can deliver ultra-compact devices for use in IoT, consumer, and industrial applications

### IC board location identifiers 

The main ICs featured are listed in the table below:

| Label | Description | Reference |
| :--- | :--- | :--- |
| U1 | Battery Cell Controller \(BCC\) | [MC33772BSP1AE](https://www.nxp.com/MC33772B) |
| U2 | Micro-Controller Unit \(MCU\) | [FS32K144HAT0MLFT](https://www.nxp.com/S32K) |
| U3 | System Basis Chip \(SBC\) | [UJA1169TK/F/3](https://www.nxp.com/products/power-management/system-basis-chips/mini-sbcs/mini-high-speed-can-system-basis-chip:UJA1169TK) |
| U4 | Authentication | A1007 |
| U5 | Near-Field Communication \(NFC\) | [NTA53321G10FHK](https://www.nxp.com/products/identification-security/rfid/nfc-hf/ntag/nfc-tags-for-electronics/ntag-5-boost-nfc-forum-compliant-ic-bridge-for-tiny-devices:NTAG5-BOOST?lang=en&lang_cd=en&) |

## Connectors

The following figure shows the location of the connectors on the board.

![](../../.gitbook/assets/image%20%2813%29.png)

![Connectors placements \(top and bottom\)](../../.gitbook/assets/image%20%2811%29.png)

All connectors implemented on RDDRONE-BMS772 are detailed in the table below:

| **Label** | Description | Manufacturer | Reference | Placed or DNP |
| :--- | :--- | :--- | :--- | :--- |
| JP1 | Cell terminal connector | JST MFG. CO | SxB-XH-A\(LF\)\(SN\) | DNP |
| J1 | External temperature sensor | JST MFG. CO | SM02B-GHS-TB\(LF\)\(SN\) | Populated |
| J2 | JTAG debugger | - | _E.g.: FTS-105-01-F-D from SAMTEC_ | Populated |
| J3 | CAN bus | JST MFG. CO | SM04B-GHS-TB\(LF\)\(SN\) | Populated |
| J4 | Battery power input | - | _E.g.: FIT0588 from DFRobot_ | DNP |
| J5 | Battery power output | - | _E.g.: FIT0588 from DFRobot_ | DNP |
| J6 | Reset jumper | FCI | 68000-202HLF | Populated with jumper mounted |
| J18 | SMBus \(I²C slave bus\) | JST MFG. CO | SM04B-GHS-TB\(LF\)\(SN\) | Populated |
| J19 | DCD-LZ debugger | JST MFG. CO | SM07B-GHS-TB\(LF\)\(SN\) | Populated |
| J20 | Additional CAN bus | JST MFG. CO | SM04B-GHS-TB\(LF\)\(SN\) | Populated |
| J21 | MCU expansion header | HARWIN INC. | M50-3530842 | DNP |
| J22 | Wake jumper | FCI | 68000-202HLF | DNP |
| J23 | I²C master bus | FCI | 68000-204HLF | Populated |

_**Note**: Hardware configuration of the board is done via 16 jumpers to solder \(SJxx\). See_ [_Cell terminal connection_](../getting-started-with-the-rddrone-bms772/configuring-the-hardware.md#cell-terminal-connection)_,_ [_Shunt resistor_](../getting-started-with-the-rddrone-bms772/configuring-the-hardware.md#shunt-resistor) _and_ [_External NFC antenna_](../getting-started-with-the-rddrone-bms772/configuring-the-hardware.md#external-nfc-antenna) _for more details._

## Communication with Flight Management Unit

The RDDRONE-BMS772 board can communicate with a host device such as a PX4 Flight Management Unit \(FMU\) using the SMBus bus \(can also be used as a simple I²C bus, connector J18\) or the UAVCAN bus \(can also be used as a simple CAN bus, connectors J3 and J20\).

_**Note**: For further information about UAVCAN, look for enablement in PX4.io software._

## Programming and debug

There are two ways to program and debug the RDDRONE-BMS772 board: 

* through the DCD-LZ connector \(J19\) 
* through the JTAG connector \(J2\)

_**Note**: The DCD-LZ combines a debug interface with a debug serial console. It is used on RDDRONE-FMUK66 \(HoverGames\). For more information see the_ [_HoverGames gitbook._](https://nxp.gitbook.io/hovergames/rddrone-fmuk66/connectors/debug-interface-dcd-lz/dcd-lz-breakout-board)\_\_

## LED

The RDDRONE-BMS772 implements a programmable RGB LED. Various color combination and blink patterns can be used to indicate the state of the battery and system.

## Button

The side button is a wake button, it connects the WAKE pin of the SBC to the ground when pressed. The J22 header placed in parallel of the side button can be used as an alternative if an extended or panel mount button is needed.

## Display

An external display could be used to display important \(battery\) information. This display can be connected to J23, the I²C master bus. This header could be supplied with 3.3V \(D34\) or 5V \(D35, default populated\). By switching the diode, 3.3V or 5V could be used.

## External and additional components

### External components

An optional external temperature sensor can be added onto the RDDRONE-BMS772 board using connector J1. An example of application for this external sensor can be to monitor the cells temperature inside the battery pack.

### Additional components

Some components are included in the design but are not mounted on the RDDRONEBMS772 original board. They are marked "DNP" on the schematics and the BOM. The following table is giving the list of additional components that can be implemented in the design as well as their use:

| Feature | Description | Label |
| :--- | :--- | :--- |
| Additional MOSFETs | If the application requires more power, two pairs of back to back MOSFETs can be added on the bottom side of the board. Corresponding part is PSMNR70-30YLH. See [Configuring the hardware](../getting-started-with-the-rddrone-bms772/configuring-the-hardware.md#power-mosfets-and-heatsinks) | Q3, Q4, Q7, Q8 |
| Heatsinks | In order to dissipate more power, four additional heat-sinks can be mounted: two on the top side and two on the bottom side of the board. Recommended part is FK 244 08 D2 PAK | HS1, HS2, HS3, HS4 |
| Optional termination resistor network on CAN bus | One 60.4 Ω resistor on each CAN line connected to a 4700 pF capacitor wired to the ground | R49, R50, C66 |
| Capacitors on cell measurements connections | A filter can be added to the cell voltage measurements connections, according to the number of cells in use | C6, C12, C18, C22, C26, C29, C34 |
| Capacitors on external temperature sensor | If the external temperature sensor is implemented, two capacitors can be added on the external temperature sensor low pass filter for more EMC demanding applications | C49, C54 |
| Capacitor on cell balancing connections | Capacitors can be added on the cell balancing circuit for EMC, according to the number of cell in use | C99, C100, C101, C102, C103, C104, C105, C106, C107 |
| External NFC antenna | Coil as an alternative option for the PCB NFC antenna for extended range operations | L2 |
| Resistor on gate driver RS pin | Resistor to link RS pin on gate driver to MCU | R99 |
| MCU expansion header | Additional MCU pins are wired to a 1x8 header slot. Potential to use additional battery level LEDs, emergency button, etc. | J21 |
| Wake jumper | Jumper for SBC wake-up. In parallel of the button | J22 |

## Test point definitions

The following figure shows the location of the test points on the board.

![Test points \(Top\)](../../.gitbook/assets/image%20%2817%29.png)

![Test points \(Bottom\)](../../.gitbook/assets/image%20%2826%29.png)

| Label | Signal name | Description |
| :--- | :--- | :--- |
| TP1 | OVERCURRENT | Overcurrent signal |
| TP2 | AUTH\_NFC\_SCL | Authentication and NFC I²C bus clock signal |
| TP3 | AUTH\_NFC\_SDA | Authentication and NFC I²C bus data signal |
| TP4 | VCC\_3V3\_SBC | SBC 3.3 V regulator output |
| TP5 | RST\_N | Reset signal \(active low\) |
| TP6 | CAN\_LO | CAN Low signal |
| TP7 | CAN\_HI | CAN High signal |
| TP8 | VCC\_3V3\_LDO1 | LDO 3.3 V regulator output |
| TP9 | SMBUS\_SCL | SMBus I²C bus clock signal |
| TP10 | SMBUS\_SDA | SMBus I²C bus data signal |
| TP11 | VBAT\_IN | Power input |
| TP12 | VBAT\_OUT | Power output |
| TP13 | GND | Ground reference of the device |
| TP14 | N/A | Power switches gate command |
| TP16 | BCC\_MISO | BCC SPI MISO line |
| TP17 | BCC\_CS | BCC SPI chip select |
| TP18 | BCC\_SCLK | BCC SPI clock signal  |
| TP19 | BCC\_MOSI | BCC SPI MOSI line |
| TP20 | SBC\_CS | SBC SPI chip select |
| TP21 | SBC\_MISO | SBC SPI MISO line |
| TP22 | SBC\_MOSI | SBC SPI MOSI line |
| TP23 | SBC\_SCLK | SBC SPI clock signal |
| TP24 | VCC\_HARVEST | The VOUT pin of the NTAG \(voltage harvest\) |
| TP25 | N/A | Connected to J18\[1\] of SMBus connector |



