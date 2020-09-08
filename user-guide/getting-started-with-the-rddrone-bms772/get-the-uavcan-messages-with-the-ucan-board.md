---
description: This page will describe how to get the UAVCAN BMS messages with the UCAN board
---

# Get the UAVCAN messages with the UCAN board

## First make sure the BMS is connected to the UCAN board

Connect the UAVCAN device \(like the RDDRONE-UCANS32K146\) to the BMS using JST GH 4 pin connectors with 1 on 1 wires. End the CAN bus with a 120Ω terminator resistor between CAN high and CAN low.

## Get the BMS draft using the UCAN board in linux:

1. Connect the UCAN board with a USB-TTL-3V3 cable to the laptop.
2. Install the can utils with the following terminal command: 
   * sudo apt install can-utils 
3. Install python 3.7 with the following terminal command:
   * sudo apt install python3.7 
4. Install pyuavcan with the following terminal command: 
   * python3.7 -m pip install pyuavcan
5. Start the deamon on UART &lt;-&gt; SLCAN to use SLCAN0 use the command \(for ttyUSB1\): 
   * sudo slcand -o -s8 -t sw -S 115200 /dev/ttyUSB1 

{% hint style="info" %}
Keep in mind that in this case the UART of the UCAN board needs to be connected to ttyUSB1. You can check which USB it is by disconnecting the USB-TTL-3V3 cable connected to the UCAN board, write “ls /dev” in the terminal, connect the USB cable and write “ls /dev” again. Only the USB of the UCAN board should be added in the list. If not check if the USB connection of your virtual machine is passed through.
{% endhint %}

1. Enable the interface \(up\)\(same as ifup can0 in nuttx\) write the following command: 
   * sudo ip link set up slcan0
2. Clone the cannode v1 tools:
   * git clone [https://github.com/PetervdPerk-NXP/cannode-v1-tools](https://github.com/PetervdPerk-NXP/cannode-v1-tools) 
3. Make sure the sub modules are in the git repository write the following command in the cannode-v1\_tools directory: 
   * git submodule update --init
4. Find this line in print\_bmsstatus\_topic.py: 
   * media = pyuavcan.transport.can.media.socketcan.SocketCANMedia\('can0', mtu=8\)                                              
5. Change it to the right can device, for example: 
   * media = pyuavcan.transport.can.media.socketcan.SocketCANMedia\('slcan0', mtu=8\)
6. Run the pyuavcan tool by typing the following in a terminal where the print\_bmsstatus\_topic.py file is located: 
   * python3.7 print\_bmsstatus\_topic

