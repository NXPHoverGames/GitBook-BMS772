---
description: Updated as we gain insight into specific applications
---

# Known areas for change or alignment

As we learn of specific needs for specific use cases they will be noted here:

*   PX4 BMS specification and working group discusses the need to provide 5V power to a drone before activating the actual battery power supply. The intent is to allow the host to identify the battery characteristics to avoid a catastrophic mismatch. Conceptually there is a need to supply 5V through the CAN /SBUS connectors to allow a host-side processor to power up and query the battery for compatibility with the drone. i.e. do not power up a 12S battery on a drone that only is designed for 3S or 4S

    * This functionality can be tested with the current revision of the board given a few jumper wires to the CAN/SBUS connectors. As built the +5V power is NC
    * Not clear if the battery can be asleep then woken up with a button press to supply power.&#x20;
    * The 5V supply MAY only need to power a small MCU on the host side and not the complete host-side FMU. The small MCU could do the BMS query and then choose to power up the battery if in compliance.


*   May be a trend toward 4 LEDS to show battery gauge status visually. We have one RGB led which we intend to flash a sequence and color to show battery status

    * Extra LEDs could be added on the expansion header


* The BMS itself doesn't regulate charging current or voltage, and needs a simple CC/CV charger. It can however balance it's own cells and disconnect the load. This situation could be improved by making a charger that talks with the battery over CAN and helps properly manage current and voltage, or even additional circuitry on board to manage this.&#x20;

