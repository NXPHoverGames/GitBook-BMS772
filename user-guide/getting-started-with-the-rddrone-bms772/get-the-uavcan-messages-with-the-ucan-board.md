---
description: This page will describe how to get the UAVCAN BMS messages with the UCAN board
---

# Get the UAVCAN messages with the UCAN board

## First make sure the BMS is connected to the UCAN board

Connect the UAVCAN device \(like the RDDRONE-UCANS32K146\) to the BMS using JST GH 4 pin connectors with 1 on 1 wires. End the CAN bus with a 120Ω terminator resistor between CAN high and CAN low.

## Get the BMS draft using the UCAN board in linux:

Connect the UCAN board with a USB-TTL-3V3 cable to the laptop.

Install the can utils with the following terminal command: 

sudo apt install can-utils 

Install python 3.7 with the following terminal command: 

sudo apt install python3.7 

Install pyuavcan with the following terminal command: 

python3.7 -m pip install pyuavcan

To start the deamon on UART &lt;-&gt; SLCAN to use SLCAN0 use the command \(for ttyUSB1\): 

sudo slcand -o -s8 -t sw -S 115200 /dev/ttyUSB1 

keep in mind that in this case the UART of the UCAN board needs to be connected to ttyUSB1, you can check which USB it is by disconnecting the USB-TTL-3V3 cable connected to the UCAN board, write “ls /dev” in the terminal, connect the USB cable and write “ls /dev” again. Only the USB of the UCAN board should be added in the list. If not check if the USB connection of your virtual machine is passed through.

To enable the interface \(up\)\(same as ifup can0 in nuttx\) write the following command: 

sudo ip link set up slcan0

clone the cannode v1 tools: 

git clone [https://github.com/PetervdPerk-NXP/cannode-v1-tools](https://github.com/PetervdPerk-NXP/cannode-v1-tools) 

Make sure the sub modules are in the git repository write the following command in the cannode-v1\_tools directory: 

git submodule update --init

In print\_bmsstatus\_topic.py, change the line:

media = pyuavcan.transport.can.media.socketcan.SocketCANMedia\('can0', mtu=8\)

To the right can device, for example: media = pyuavcan.transport.can.media.socketcan.SocketCANMedia\('slcan0', mtu=8\)

To run the pyuavcan tool type the following in the terminal where the print\_bmsstatus\_topic.py file is stored: 

python3.7 print\_bmsstatus\_topic

