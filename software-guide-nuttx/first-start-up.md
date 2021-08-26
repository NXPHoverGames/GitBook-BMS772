---
description: >-
  This page will explain some start-up messages, what to do when first using the
  BMS
---

# First start-up

## First start-up messages

When first starting the BMS with the latest software the command line interface could look like the code snipping at the end of the page.

You can see that the version number is: bms4.0-10.1. this comes after "BMS version: ".  
Than it will begin doing self-tests. 

* START means it will start testing that part or component
* PASS means that the test succeeded
* FAIL means the test did not succeed

Be sure to check the error messages as it could help finding out what is wrong, some errors explain why it went wrong and how you could fix it.  
  
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

It could be that you get the message that the stackvoltage is too different from sum of cells, so there is a wrong n\_cells number. This means that the actual connected cells are different than the entered number of cells \(n-cells\). To fix this, check what the current n-cells value is with "bms get n-cells" and make sure it corresponds with the number of cells in the attached battery. To configure the correct number of cells type "bms set n-cells x" where x the number of cells of the battery, that can be 3-6. After that type "bms reset" or press the button to reset the fault. In version 3.4 there is something wrong, n\_cells should be n-cells. 

```text
bcc_monitoring ERROR: stackvoltage too different from sum of cells! stack:   19.160V cells:    9.601V
batManagement: ERROR: wrong n_cells!
Please set the correct cells! using "bms set n_cells x"
```

You will get a warning if the battery temperature sensor is not enabled, "WARNING: battery temperature sensor is disabled!". To enable the battery temperature sensor see [How to enable the battery temperature sensor](how-to-enable-the-battery-temperature-sensor.md). 

If you see the text that the BCC overvoltage set to &lt;number&gt;mV. That number should be slightly higher than the actual set cell-ov in the software. This is because the overvoltage threshold register of the BCC is an 8-bit register, compared to the floating point variable in the software this has a lot less resolution. The value in the BCC is set slightly higher to not falsely trigger on it, but have it as a backup trigger since the software will react on the overvoltage as well with the measured cell voltage.

```text
BCC overvoltage set to 4218mV
```

It could be that you see the following line: "NOTICE: Disabling 5V regulator \(CAN transceiver\) briefly!". This happens when the SBC needs to switch modes, because it can only be done in the standby mode where the 5V regulator is disabled.

```text
NOTICE: Disabling 5V regulator (CAN transceiver) briefly!
```

"BMS main loop!" means the BMS has entered the main loop and will continue according to the main state diagram. 

Each time the BMS enters a new mode, it will output this with "&lt;mode&gt; mode"

```text
nsh> B�EG                                                                       
Starting BMS                                                                    
             total       used       free    largest                             
Umem:        40528      11328      29200      29200                             
Starting can0                                                                   
ifup can0...OK                                                                  
BMS version: bms4.0-10.1                                                        
SELF_TEST mode                                                                  
SELF-TEST LEDs: START                                                           
SELF-TEST LEDs: PASS                                                            
CRC of saved data doesn't match!                                                
Setting old values!                                                             
nothing/wrong saved!                                                            
SELF-TEST GPIO: START                                                           
SELF-TEST SBC: START
NVMS registers don't have the right value!
SBC_CONF: 8 != 4
MTPNV_STATUS: RX0: 225, RX1: 1
overwritting NVMPS registers
START_UP_CTRL W: RX0: 230, RX1: 0
SBC conf ctrl W: RX0: 232, RX1: 8
Restarting!
CRC W: RX0: 234, RX1: 0
nsh> B�EG                                                                       
Starting BMS                                                                    
             total       used       free    largest                             
Umem:        40528      11328      29200      29200                             
Starting can0                                                                   
ifup can0...OK                                                                  
BMS version: bms4.0-10.1                                                        
SELF_TEST mode                                                                  
SELF-TEST LEDs: START                                                           
SELF-TEST LEDs: PASS                                                            
CRC of saved data doesn't match!                                                
Setting old values!                                                             
nothing/wrong saved!                                                            
SELF-TEST GPIO: START                                                           
SELF-TEST SBC: START                                                            
Setting SBC to normal mode!                                                     
SELF-TEST SBC: PASS                                                             
SELF-TEST BCC: START                                                            
WARNING: battery temperature sensor is disabled!                                
If this needs to be enabled write: "bms set sensor-enable 1" in the terminal    
BCC overvoltage set to 4218mV                                                   
SELF-TEST BCC: PASS                                                             
SELF-TEST GATE: START                                                           
SELF-TEST GATE: PASS                                                            
SELF-TEST CURRENT_SENSE: START                                                  
SELF-TEST CURRENT_SENSE: PASS                                                   
SELF-TEST NFC: START                                                            
SELF-TEST NFC: PASS                                                             
SELF-TEST A1007: START                                                          
SELF-TEST A1007: PASS                                                           
SELF-TEST GPIO: PASS                                                            
ALL SELF-TESTS PASSED!                                                          
BMS main loop!                                                                  
NOTICE: Disabling 5V regulator (CAN transceiver) briefly!                       
INIT mode                                                                       
NORMAL mode                                                                     
Started                                                                         
                                                                                
NuttShell (NSH) NuttX-10.1.0                                                    
nsh> 
```

## first time software configuration of the BMS

It is highly recommended that you check each parameters in [Parameters of the BMS](untitled-1.md) and make sure to configure each parameter. Use "bms get all" to get each parameter and it's value, so you could configure each one for your battery.   
  
Some parameters you would like to configure are:

* a-rem \(the remaining capacity\)
  *  the BMS does a guess on what the remaining charge is based on a OCV\(open cell voltage\)/SoC \(state of charge\) table from one specific battery, but every battery is different.
    * It is advisable to insert the correct OCV/SoC table for the battery.
* a-full \(the full charge capacity of the battery\)
  *  while charging, the BMS will calculate this based on a-rem\)
* model-name \(the name of the battery\)
* n-cells \(the amount of cells of the battery\)
* a-factory \(the factory capacity of the battery\)
* i-charge-full \(the end of charge current of the battery \(could be 10% from i-charge-max\)\)
* i-charge-max \(the maximum charge current\)
* sensor-enable \(to enable the battery temperature sensor\)

