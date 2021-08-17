---
description: This page will have information about the UAVCAN communication
---

# UAVCAN

## How to use the \(UAV\)CAN interface

Connect the UAVCAN device \(like the RDDRONE-UCANS32K146\) to the BMS using 2x JST-GH 4 pin connectors with 1 on 1 wires. End the CAN bus with a 120Ω terminator resistor between CAN high and CAN low.

## Get the Battery status draft using the UCAN board in Linux:

1. Make sure you Connect the UCAN board with a USB-TTL-3V3 cable to the laptop.
2. Install the can utils with the following terminal command: 

   o    sudo apt install can-utils 

3. Install python 3.7 with the following terminal command:

   o    sudo apt install python3.7 

4. Install pyuavcan with the following terminal command: 

   o    python3.7 -m pip install pyuavcan

5. Start the deamon on UART &lt;-&gt; SLCAN to use SLCAN0 use the command \(for ttyUSB1\): o sudo slcand -o -s8 -t sw -S 115200 /dev/ttyUSB1 

Keep in mind that in this case the UART of the UCAN board needs to be connected to ttyUSB1. One can check which USB it is by disconnecting the USB-TTL-3V3 cable connected to the UCAN board, write “ls /dev” in the terminal, connect the USB cable and write “ls /dev” again. Only the USB of the UCAN board should be added in the list. If not check if the USB connection of the used virtual machine is passed through.

1. Enable the interface \(up\)\(same as ifup can0 in nuttx\) write the following command: o sudo ip link set up slcan0
2. Clone the cannode v1 tools:

   o    git clone [https://github.com/PetervdPerk-NXP/cannode-v1-tools](https://github.com/PetervdPerk-NXP/cannode-v1-tools) 

3. Make sure the sub modules are in the git repository write the following command in the cannode-v1\_tools directory: 

   o    git submodule update --init

4. Find this line in print\_battery\_service.py: 

   o    media = pyuavcan.transport.can.media.socketcan.SocketCANMedia\('vcan0', mtu=8\) 

5. Change it to the right can device, for example: 

   o    media = pyuavcan.transport.can.media.socketcan.SocketCANMedia\('slcan0', mtu=8\)

6. Run the pyuavcan tool by typing the following in a terminal where the print\_bmsstatus\_topic.py file is located: 

   o    python3.7 print\_battery\_service

7. Check if the subject IDs of the messages are correct
   1. Uavcan\_es\_sub\_id should be 4096.
   2. Uavcan\_bs\_sub\_id should be 4097.
   3. Uavcan\_bp\_sub\_id should be 4098.
8. Check if the node id of the BMS is not 225

   o    In the CLI of the BMS type “bms get uavcan-node-static-id”, if this is 255, it needs to be changed to another value \(like 12\). Do this with “bms set uavcan-node-static-id 12”

   o    After that save it and reboot the bms with “bms save” and “reboot”.

