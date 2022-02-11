---
description: RDDRONE-BMS772 for Mobile Robotics
---

# Introduction

The RDDRONE-BMS772 is a standalone BMS Reference Design suitable for mobile robotics such as drones and rovers, supporting 3-6 cell batteries.

Other uses include portable electronics and equipment needing better battery management

* eScooters, ebikes
* high end power tools
* portable medical devices (Pulse oximeter, portable pumps, electric portable refrigerator)
* backup battery system
* outdoor monitoring/measuring equipment

![RDDRONE-BMS772](.gitbook/assets/RDDRONE-BMS772\_iso.jpg)

It is an open hardware and software design and useful leverages components used in general purpose automotive and high-reliability industrial applications. The BCC device performs ADC conversion on the differential cell voltages and currents. It is capable of very accurate battery charge coulomb counting and battery temperature measurements.

The NXP [MC33772](https://www.nxp.com/products/power-management/battery-management/battery-cell-controllers/6-channel-li-ion-battery-cell-controller-ic:MC33772B) is a 6 cell BCC. If higher cell counts are required this could be redesigned to daisy chain multiple BCC chips or switch to a larger cell count BCC such as the [MC33771](https://www.nxp.com/products/power-management/battery-management/battery-cell-controllers:BATTERY-CELL-CONTROLLERS). These parts are all automotive grade Li-Ion battery cell controller IC designed for automotive and industrial applications such as HEV, EV, ESS, UPS systems

The BMS772 also features an [S32K146/144 automotive grade S32K Microcontroller](https://www.nxp.com/products/processors-and-microcontrollers/arm-microcontrollers/s32k-automotive-mcus/s32k1-microcontrollers-for-general-purpose:S32K). These are rugged M4 core processors part of a scalable family of AEC-Q100 qualified 32-bit Arm® Cortex®-M4F and Cortex-M0+ based MCUs

An [NTAG5 Boost NFC](https://www.nxp.com/products/rfid-nfc/nfc-hf/ntag/nfc-tags-for-electronics/ntag-5-boost-nfc-forum-compliant-ic-bridge-for-tiny-devices:NTAG5-BOOST) NFC Forum-compliant I2C bridge is also onboard and appears as an NFC contactless tag to the external world, and interfaces internally in a simple manner similar to an EEPROM for easy secure query of status or setting of parameters using an external NFC device such as a cell phone. In a practical sense this allows an end user to check multitudes of batteries that may be in storage just by hovering their cell phone over them.

An A1007 is an enhanced version of [A1006](https://www.nxp.com/products/security-and-authentication/authentication/secure-authenticator-ic-embedded-security-platform:A1006) secure authenticator IC which includes monotonic counters and secure flags. These can be used to prove the battery pack is genuine and has not been tampered with as well as securely count charge cycles, and permanently flag negative events such as over discharge. The Secure Authenticator IC is a secure tamper-resistant authentication IC, which offers a strong cryptographic solution intended to be used by device manufacturers to prove the authenticity of their genuine products

Finally, the BMS communicates with a host such as a Drone Flight Management Unit (FMU) through UAVCAN or I2C/SMBus.

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png)](http://creativecommons.org/licenses/by/4.0/)\
This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
