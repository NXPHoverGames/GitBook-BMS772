---
description: Updated as we gain insight into specific applications
---

# Errata and known areas for change or alignment

## Introduction

As we learn of specific needs for specific use cases they will be noted here:

### 5V BMS output supply?

PX4 BMS specification and working group discusses the potential requirement to provide 5V power to a vehicle **before** activating the actual battery power supply main outputs. The intent is to allow something on the host to identify the battery characteristics in advance in order to avoid a catastrophic voltage mismatch.&#x20;

Conceptually there is a need to supply 5V through the CAN /SBUS connectors to allow a _host-side processor_ to power up and query the _smart battery (BMS)_  for compatibility with the drone. (i.e. do not power up a 12S battery on a drone that only is designed for 3S or 4S)

* This functionality can be tested with the current revision of the board given a few jumper wires to the CAN/SBUS connectors. As built the +5V power is NC
* The 5V supply from the SmartBattery/BMS likely only needs to provide limited current in order to power a small MCU on the host side and not the complete host-side FMU. The small MCU could do the BMS query and then choose to power up the battery if in compliance.
* It needs to be determined how does BMS sleep mode or deep sleep mode should work with this operation.&#x20;

There are other preventative configurations being discussed such as mechanically preventing incompatible battery packs being inserted, and also using host side configuration resistor to signal to the battery what power/voltage the host expects. These may be discussed on the PX4 working group for BMS.

### LED Battery Status indicators

The BMS772 evaluation design includes one RGB led which is intended to flash sequences and colors to show battery status. It has been noted however that some implementations may wish to use 4 LEDS for visual battery gauge status.&#x20;

* Extra LEDs can be accommodated by using the expansion header
* Alternative option: I2C bus can be also be used to add an local OLED display.

### Charging and Balancing

The BMS772 itself doesn't regulate charging current or voltage, and needs a simple CC/CV charger. It can however balance it's own cells and disconnect the load. This situation could be improved by making a charger that talks with the battery over CAN and helps properly manage current and voltage, or even additional circuitry on board to manage this.&#x20;

### Errata

* Rev C of RDDRONE-BMS772 inadvertently does not connect the 5V power from one CAN Connector to the next - Between J3 and J20. If needed a jumper wire can be added between J3-Pin 1  and J20Pin-1. This is corrected on Rev D of the board.&#x20;

