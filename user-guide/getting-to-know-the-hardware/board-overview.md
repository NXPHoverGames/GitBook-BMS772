# Board overview

The RDDRONE-BMS772 is a standalone BMS Reference Design suitable for mobile robotics such as drones and rovers, supporting 3-6 cell batteries. Other portable electronics and equipment, such as scooters, power tools, portable medical devices could also benefit from referencing this design. If higher cell counts are required this could be redesigned to daisy chain multiple BCC chips or switch to a larger cell count BCC.&#x20;

The device performs ADC conversion on the differential cell voltages and currents. It is capable of very accurate battery charge coulomb counting and battery temperature measurements. Additionally, it communicates with a Flight Management Unit (FMU) through UAVCAN and/or an SMBus.

![RDDRONE-BMS772](../../.gitbook/assets/RDDRONE-BMS772\_iso.jpg)
