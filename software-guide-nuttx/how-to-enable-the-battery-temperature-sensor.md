---
description: This page will explain which temperature sensor you need and how to enable it.
---

# How to enable the battery temperature sensor

By default the temperature sensor is not enabled. To configure the temperature sensor to be used, this temperature sensor need to be connected to J1 using a 2-pin JST-GH connector. The maximum length of the cable that leads to the temperature sensor is 20cm. This temperature sensor needs to be a 10k NTC, like the NTCLE100E3103JB0 from Vishay. With the CLI type:

“bms set sensor-enable 1”.

this will enable the temperature sensor measurement to be done together with the rest of the measurements in the BMS software.

