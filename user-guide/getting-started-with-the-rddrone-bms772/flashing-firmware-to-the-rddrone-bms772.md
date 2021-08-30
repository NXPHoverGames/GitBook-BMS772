---
description: This page will provide all the information needed to flash the BMS
---

# Flashing firmware to the RDDRONE-BMS772

## Downloading J-link

[Download J-Link Software and Documentation Pack](https://www.segger.com/downloads/jlink#J-LinkSoftwareAndDocumentationPack)

J-Link Commander is used to flash binaries onto the RDDRONE-BMS772 board. The latest \(stable\) release of the J-Link Software and Documentation Pack is available at the SEGGER website for different operating systems.

## Connecting the programmer to the BMS

The software can only be written to the board using a debugger. The HoverGames drone kit includes a J-Link EDU Mini debugger. To use it, you need to install the J-Link Software Pack. 

The debugger can be plugged into the BMS using a small adapter board. This small PCB comes with a 3D printed case that can easily be put together. The J-Link debugger can be connected using an **SWD cable**. The connectors have to be oriented such that the **wires directly go to the side of the board**, as shown in the picture below.

While you do not need it right now, the adapter board also has a 6-pin connector for a **USB-TTL-3V3 cable**, which you can use to access the system console \(CLI\) of the BMS. The 3D printed case has a small **notch** on one side of the connector. The USB-TTL-3V3 cable needs to be plugged in such that the **black \(ground\) wire is on the same side as this notch** in the case. Make sure the cables are plugged in as shown in the picture below. Connect the 7-pin JST GH to the programming header of the BMS, J19. 

![The debug adapter board](../../.gitbook/assets/image%20%286%29.png)

![BMS programming header](../../.gitbook/assets/image%20%2816%29.png)

## Flashing the firmware

A guide for flashing firmware to this board is outlined in one of our consolidated GitBooks for flashing a multitude of NXP hardware. The link to this GitBook is below.

## [https://nxp.gitbook.io/nxpmobilerobotics/flashing-guide/flashing-hovergames-boards](https://nxp.gitbook.io/nxpmobilerobotics/flashing-guide/flashing-hovergames-boards)

## Next steps

Once you're done flashing your board, you may continue to the Accessories and tools for development tutorial.

