---
description: >-
  This page will explain some start-up messages, what to do when first using the
  BMS
---

# First start-up

## First start-up messages

When first starting the BMS with the latest software the command line interface could look like the code snipping at the end of the page.

You can see that the version number is: bms3.4-9.1. this comes after "BMS version: ".  
Than it will begin doing self-tests. 

* START means it will start testing that part or component
* PASS means that the test succeeded
* FAIL means the test did not succeed

Be sure to check the error messages as it could help finding out what is wrong, some errors explain why it went wrong and you could fix it.  
  
It could be that you will get these messages:

```text
CRC of saved data doesn't match!
Setting old values!
nothing/wrong saved!
```

These messages mean that the CRC of the saved data \(the parameters\) in flash doesn't match. This could happen when nothing is saved or when a new program is flashed in the microcontroller \(and thus cleared the flash\).  
  
Than it could be that you get the message "NVMS registers don't have the right value!". This means a register in the SBC needs to be written, but before this could take effect, it needs to restart the SBC, "Restarting!" is stated when it does this. Since the SBC supplies the microcontroller with its power, the microcontroller will restart as well. 

```text
NVMS registers don't have the right value!
SBC_CONF: 8 != 4
MTPNV_STATUS: RX0: 225, RX1: 1
overwritting NVMPS registers
START_UP_CTRL W: RX0: 230, RX1: 0
SBC conf ctrl W: RX0: 232, RX1: 8
Restarting!
CRC W: RX0: 234, RX1: 0
```

You will get a warning if the battery temperature sensor is not enabled, "WARNING: battery temperature sensor is disabled!". To enable the battery temperature sensor see [How to enable the battery temperature sensor](how-to-enable-the-battery-temperature-sensor.md). 

"BMS main loop!" means the BMS has entered the main loop and will continue according to the main state diagram. 

In the beginning you will always get the message "Rising edge BCC\_FAULT!". This doesn't mean this pin was high, but this is because it will always check the faults first. 

Each time the BMS enters a new mode, it will output this with "&lt;mode&gt; mode"

```text
BãEG
Starting BMS
             total       used       free    largest
Umem:        39600      12048      27552      27552
Starting can0
ifup can0...OK
BMS version: bms3.4-9.1
SELF-TEST START: FLASH
CRC of saved data doesn't match!
Setting old values!
nothing/wrong saved!
SELF-TEST PASS:  FLASH
SELF-TEST START: GPIO
SELF-TEST PASS:  GPIO
SELF-TEST START: SBC
NVMS registers don't have the right value!
SBC_CONF: 8 != 4
MTPNV_STATUS: RX0: 225, RX1: 1
overwritting NVMPS registers
START_UP_CTRL W: RX0: 230, RX1: 0
SBC conf ctrl W: RX0: 232, RX1: 8
Restarting!
CRC W: RX0: 234, RX1: 0
BãEG
Starting BMS
             total       used       free    largest
Umem:        39600      12048      27552      27552
Starting can0
ifup can0...OK
BMS version: bms3.4-9.1
SELF-TEST START: FLASH
CRC of saved data doesn't match!
Setting old values!
nothing/wrong saved!
SELF-TEST PASS:  FLASH
SELF-TEST START: GPIO
SELF-TEST PASS:  GPIO
SELF-TEST START: SBC
Setting SBC to normal mode!
SELF-TEST PASS:  SBC
SELF-TEST START: UAVCAN
SELF-TEST PASS:  UAVCAN
SELF-TEST START: LEDs
SELF-TEST PASS:  LEDs
SELF-TEST START: BCC
WARNING: battery temperature sensor is disabled!
If this needs to be enabled write: "bms set sensor-enable 1" in the terminal
SELF-TEST PASS:  BCC
SELF-TEST START: GATE
SELF-TEST PASS:  GATE
SELF-TEST START: NFC
SELF-TEST PASS:  NFC
SELF-TEST START: A1007
SELF-TEST PASS:  A1007
BMS main loop!
Rising edge BCC_FAULT!                                                          
init mode                                                                       
normal mode                                                                     
Started                                                                         
                                                                                
NuttShell (NSH) NuttX-8.2.0                                                     
nsh> 
```

## first time software configuration of the BMS

It is highly recommended that you check each parameters in [Parameters of the BMS](untitled-1.md) and make sure to configure each parameter. Use "bms get all" to get each parameter and it's value, so you could configure each one for your battery.   
  
Some parameters you would like to configure are:

* a-rem \(the remaining capacity\)
  *  the BMS does a guess on what the remaining charge is based on a OCV\(open cell voltage\)/SoC \(state of charge\) table from one specific battery, but every battery is different.
* a-full \(the full charge capacity of the battery\)
  *  while charging the BMS will calculate this based on a-rem\)
* model-name \(the name of the battery\)
* n-cells \(the amount of cells of the battery\)
* a-factory \(the factory capacity of the battery\)
* i-charge-full \(the end of charge current of the battery \(could be 10% from i-charge-max\)\)
* i-charge-max \(the maximum charge current\)
* sensor-enable \(to enable the battery temperature sensor\)

