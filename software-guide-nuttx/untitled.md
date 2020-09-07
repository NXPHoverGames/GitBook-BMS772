---
description: This page will describe the software block diagram of the nuttx example
---

# Software block diagram

## Software block diagram

Figure 1 is the BMS application consisting of several modular parts. Functions from these parts can be called from the BMS application. These parts are tasks that will run semi-parallel \(since it is still a single core processor\). NuttX scheduler will take care of this aspect for us. 

The CLI \(command line interface\) module is called by running the BMS application from the nuttshell interface with arguments. An explanation of each of the blocks can be found below in the module description section. The CLI module is needed for easy debugging and user interface, while the NFC, Display, UAVCAN, Bat management and LED state modules are needed for the overall functional requirements.

![Figure 1: Software block diagram](../.gitbook/assets/0%20%281%29.png)

## Module description

### **BMS application**

The BMS application creates the main task wich implements a battery state machine. It calls the functions from the different modules to implement the overall BMS application. This application is called during startup. The application can be called from the nuttshell with various arguments to use it as a CLI.

### **CLI**

The command line interface \(CLI\) module takes care of communication with the user through nuttshell, it can be used during debugging of the smart battery application or a specific battery under test. The communication is mapped to use a universal asynchronous receiver-transmitter \(UART\) also known as the root console. 

The application command may be followed by optional arguments such as  sleep, deepsleep, wake, reset, help, show, set or get. With the set or get command the user can read and write every value, including the configuration parameter list. These values can be read/written by calling the BMS application followed by a set or get command followed by the name of the variable. In the case of a set command this would instead followed by the new value of the variable.

### **Authentication - A1007**

The authentication module will take care of the authentication using the A1007 chip. The A1007 is capable of secure asymmetric key exchange and storage as well as secure monotonic counters and flags for use in such things as counting charge or discharge cycles or permanently flagging under-voltage or over-temperature conditions.  
This module is not implemented yet. Only verification via I2C is implemented.

### **NFC - NTAG5**

The NFC module manages NFC communication. It needs to read all the values and should be able to write the configuration parameter list. It should be able to read the values with a refresh rate of once a second. NFC will allow the user to insert commands like wake, reset, sleep, deepsleep, etc. The updater task will be used to update the data. The NTAG5 chip is capable of operating using energy harvested from the NFC field of a reading device. It can operate in a similar manner to a double ported EEPROM, and NFC records can include standardized messages for HTTP records. In this way the NFC tag could be updated regularly with status information. That information could be added to a URL, and a smartphone would be capable of reading the URL with data attached, and rendering a human readable webpage with minimal coding effort. This method removes the need for any custom software on the reading device.  
This module is not implemented yet. Only verification via I2C is implemented.

### **Display**

The display module manages information presented on an optional local I2C LCD display.   
This module is not implemented at this time.

### **UAVCAN**

The UAVCAN module manages UAVCAN communication. UAVCAN V1 protocol is used to relay battery and power usage to the FMU \(or host processor\). It sends the battery status list on a cyclic time interval. It sends configuration data if requested.  This module also manages the SBC \(systems basis chip - CAN PHY and voltage regulator\) on board.

### **Bat management**

The Bat management \(battery management\) part is the most important part, it will oversee the whole battery management. It will be used to monitor the battery, the PCB \(temperatures\) and calculate voltages, temperatures, current, SoC, SoH, average power and more, it will ensure the BCC chip reacts if thresholds are exceeded. Function of this part can be used to drive the gate driver, which allows it to disconnect the battery from the output power connector on the BMS. Because this is such a large part of the system, the Bat management part can create some tasks. These tasks can all access the BCC, the timers and the GPIO. 

#### These are the sub-tasks:

* **meas task** -  this task will oversee the measurements and if triggered do the calculations. 
* **otherCalc task** - this task will make sure that once every measurement cycle, the meas task will do the calculations.
* **sdchar task** - this task will oversee the self-discharging.

### **LED state**

The LED state module can be used to set the RGB LED. It can set a RGB color on or off, and blink the LEDs at given intervals. If a LED needs to blink a blinker task will be created to ensure it blinks. This module is used to inform the user visually of various states and status.

#### Table 1: LED states

This module implements the LED states given below

<table>
  <thead>
    <tr>
      <th style="text-align:left">State</th>
      <th style="text-align:left">LED state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Deep sleep</td>
      <td style="text-align:left">Off (after 1 sec white)</td>
    </tr>
    <tr>
      <td style="text-align:left">Sleep</td>
      <td style="text-align:left">Off</td>
    </tr>
    <tr>
      <td style="text-align:left">Wake-up</td>
      <td style="text-align:left">Green</td>
    </tr>
    <tr>
      <td style="text-align:left">Normal</td>
      <td style="text-align:left">
        <p>Green blinking (with state indication)</p>
        <p>1 blink 0-40%</p>
        <p>2 blinks 40-60%</p>
        <p>3 blinks 60-80%</p>
        <p>4 blinks 80-100%</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Fault</td>
      <td style="text-align:left">Red blinking</td>
    </tr>
    <tr>
      <td style="text-align:left">Charging</td>
      <td style="text-align:left">Dark blue</td>
    </tr>
    <tr>
      <td style="text-align:left">Charging done</td>
      <td style="text-align:left">Light blue</td>
    </tr>
    <tr>
      <td style="text-align:left">Balancing/self-discharge</td>
      <td style="text-align:left">Dark blue blinking</td>
    </tr>
    <tr>
      <td style="text-align:left">NFC communication</td>
      <td style="text-align:left">Yellow blinking</td>
    </tr>
    <tr>
      <td style="text-align:left">Charger connected at startup</td>
      <td style="text-align:left">Red-blue blinking</td>
    </tr>
  </tbody>
</table>

### **Data**

Since different parts need to use the same data, a data library is used to take care of this. This library will make sure it is protected against concurrent usage by multiple tasks.

