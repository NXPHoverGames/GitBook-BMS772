---
description: Updated as we gain insight into specific applications
---

# Errata and known areas for change or alignment

## Introduction

As we learn of specific needs for specific use cases they will be noted here:

### 5V BMS output supply?

PX4 BMS specification and working group discusses the need to provide 5V power to a drone before activating the actual battery power supply. The intent is to allow the host to identify the battery characteristics to avoid a catastrophic mismatch. This means that in concept there is a need to supply 5V through the CAN /SBUS connectors to allow a _host-side processor_ to power up and query the _smart battery \(BMS\)_  for compatibility with the drone. \(i.e. do not power up a 12S battery on a drone that only is designed for 3S or 4S\)

* This functionality can be tested with the current revision of the board given a few jumper wires to the CAN/SBUS connectors. As built the +5V power is NC
* The 5V supply from the SmartBattery/BMS likely only needs to provide limited current in order to power a small MCU on the host side and not the complete host-side FMU. The small MCU could do the BMS query and then choose to power up the battery if in compliance.
* It needs to be determined how does BMS sleep mode or deep sleep mode should work with this operation. 

### LED Status indicators

There may be a trend toward using 4 LEDS to show battery gauge status visually. The BMS772 includes one RGB led which is intended to flash sequences and colors to show battery status

* Extra LEDs could be added on the expansion header
* Alternative option: I2C bus can be also be used to add an local OLED display.

### Charging and Balancing

The BMS itself doesn't regulate charging current or voltage, and needs a simple CC/CV charger. It can however balance it's own cells and disconnect the load. This situation could be improved by making a charger that talks with the battery over CAN and helps properly manage current and voltage, or even additional circuitry on board to manage this. 

### Errata

* Rev C of RDDRONE-BMS772 inadvertently does not connect the 5V power from one CAN Connector to the next - Between J3 and J20. If needed a jumper wire can be added between J3-Pin 1  and J20Pin-1. This is corrected on Rev D of the board. 



