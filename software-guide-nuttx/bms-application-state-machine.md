---
description: >-
  This page will show the designed state machine and the description of the
  states from this state machine.
---

# BMS application state machine

## The main state machine

In Figure 2 the main state machine that will be implemented in the BMS application can be seen. This state diagram will be implemented in the BMS application. Below the state machine, in Main state machine explained, the explanation of the states can be found. These states are needed for the requirements and to make a structured way of programming possible.

![Figure 2: Battery main state machine](../.gitbook/assets/battery-state-machine%20%281%29.png)

## Main state machine explained

### **INIT state**

The INIT state is typically entered from the SLEEP state. In this state the microcontroller unit \(MCU\) will wake up and it will verify configurations, fault registers and functions. This is needed because it can enter the INIT state when the user resets from a fault in the FAULT state as well. When everything is OK, it will close the switches if not already closed and proceed to the next state depending on the current direction. The LED will be steady green in this state.

### **NORMAL state**

  
This is the state were the battery operates how it should be, it is being discharged by the drone. Meaning that the power switches are closed. The LED will be blinking green to indicate the state of charge. In this state the BMS performs the following tasks:

* Battery voltage, cell voltage and current is measured and calculated every measurement cycle.
* SoC and SoH are estimated every measurement cycle.
* The UAVCAN BMS battery status will be send over the UAVCAN bus every measurement cycle.
* The user can read the BMS status and parameters with NFC and the CLI. The user may change the state to SLEEP.
* A timer will monitor if the current is below the sleep current for more than the timeout period. If this happens, it will go to the SLEEP state.
* It will monitor if the current flows in the battery and if the current is more than the sleep current for more than the charge detect time, the state will change to the CHARGE state.
* If the current is less than the sleep current while the button is pressed for 5 seconds, it will transition to the SELF DISCHARGE state.

### **CHARGE state**

  
During this state the same functions as in the NORMAL state are implemented as well. The charging of the battery is done in different stages and is reflected in the charging state diagram in Figure 3. These are the states and their description:

* CHARGE START: in this state the charging will begin, and a timer will start. The LED will be blue to indicate charging. After a set time \(default two minutes\) the state will change to CHARGE WITH CB.
* CHARGE WITH CB: in this state the cell balancing \(CB\) function will be activated. This function does cell balancing based on the cell voltage and the difference of each cell voltage compared to the lowest cell voltage. When the voltage of one of the cells reaches the cell overvoltage level or the charging current is less than the charge complete current, the state will change to the RELAXATION state. The LED will stay blue and will blink if cell balancing is active. Balancing is finished if the cells that are balanced, are the same voltage as the lowest cell voltage.  
* RELAXATION: in this state the power switches are set open, disconnecting the battery from the charger. The battery will relax for the specified relax time \(default five minutes\). During this relaxing, the cells can still be balanced since this happens with a low balancing current. At the end of the relaxation period, the system will check whether the balancing is finished. If balancing is done and the highest cell voltage is lower than the cell overvoltage minus the voltage margin, it will return to the CHARGE WITH CB state to continue charge process. If the highest cell is within this margin, the charging is complete, and it will go to the CHARGE COMPLETE state. To make sure it won’t endlessly go through this cycle with the CHARGE WITH CB state \(this can happen if the end of charge current is met but the voltage requirement is not met\), after 5 times it will not check if the highest cell voltage is within this margin and will go to the CHARGE COMPLETE state as well.
* CHARGE COMPLETE: in this state, the charging is done and the LED will be steady green. The power switches will remain open and if the charger is disconnected it will go to the SLEEP state after the defined period of time.

If at any time the current flows from the battery to the output and this current is higher than the sleep current, the BMS transitions to the NORMAL mode. If a charger is disconnected, the state will transition to the SLEEP state. If the go to deep sleep command has been given there are two options: If one cell voltage is less than the storage voltage it will complete charging until each cell has reached the storage voltage, after this is done the BMS will transition to the SELF DISCHARGE state and this will transition to the DEEP SLEEP state. The other option is that no cell voltage is less than the storage voltage, than the BMS will transition to the SELF DISCHARGE state.

![Figure 3: Charging state diagram](../.gitbook/assets/charge-state-diagram%20%281%29.png)

### **SLEEP state**

  
The sleep state is typically entered when the current is very low for an amount of time. The power switches will be closed to make sure the battery could be used. If any threshold is met during a cyclic measurement or the button is pressed, it will wake the MCU and the BMS will transition to the INIT state to check status. If the button is pressed for five seconds, the state will change to the SELF DISCHARGE state, in order to go to the DEEP SLEEP state. In this state the LED will be off. In a later release, this state is used to preserve power.

### **OCV state**

This state is not implemented yet.

### **FAULT state**

  
The FAULT state is entered when a critical fault that requires the battery switches to be opened has been detected \(over-current, over-voltage, cell over-temperature\). But only in extreme cases, to prevent sudden power outage on devices like flying drones. To exit this  FAULT state the user can manually force the BMS to go to the INIT state via the reset fault command with the CLI or by activating the push button. The LED will blink red in this state.

### **SELF DISCHARGE state**

  
This state is used to discharge the cells to the cell storage voltage in order to improve its life duration, when storing the battery for long time. In this mode, the power switches are open, the MCU is on and the CB function is activated. When the storage voltage is reached for each cell or if cells have a lower voltage, it will transition to the DEEP SLEEP state. CAN communication is disabled. The LED will blink dark blue in this state. To exit this state and to go back to the INIT state, the button needs to be pressed. 

### **DEEP SLEEP state**

  
This state is used for transportation and storage. In this state; the power switches are open, disconnecting the battery, all protections are turned off, there are no cyclic measurements are done, the LED is off, and it will set everything to sleep or off to ensure the lowest power usage. Only the button can wake everything in this state. When the button is pressed it will transition to the INIT state. If configuration parameters have changed, it will save the parameters to flash to make sure they are loaded at startup.

