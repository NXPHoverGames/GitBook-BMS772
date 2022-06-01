---
description: This page will describe how to use the CLI
---

# Command Line Interface (CLI)

## The help command

To view the help of the commands of the bms, type "bms help" in the terminal (CLI).\
Than you will see this window:

```
nsh> bms help                                                                   
This is the bms cli (command line interface) help                               
These commands can be used with the bms:                                        
bms help                  --this command shows this help                        
bms help parameters       --this command shows the <parameter> list             
bms help show-meas        --this command shows the <show-meas> list             
bms get <parameter>       --this command gets a parameter value.                
                            parameter is the parameter you want                 
bms get all               --this command gets all the parameters                
                            including the values                                
bms set <parameter> <x>   --this command can be used to set a parameter         
                            WARNING this could lead to unsave operations!       
                            WARNING only use this command in a safe manner!     
                            parameter is the parameter you want to set          
                            x is the new value of the parameter you want to set 
                            to enter a decimal value use "." as seperator       
                            to enter a string with spaces use "input string"    
bms show <show-meas> <x>  --this command can be used to show the cyclic 
                            measurement results 
                            show-meas is the to measurement to enable or 
                            disable visibility
                            if x is 1 the measurement is shown, if 0 it will 
                            be disabled
bms reset                 --this command will reset the fault when in the 
                            fault state
bms sleep                 --with this command it will go to the sleep state     
                            from the normal or the self_discharge state         
                            NOTE: if current is drawn it will transition to 
                            the normal state
bms wake                  --this command will wake the BMS in the sleep state   
bms deepsleep             --with this command it will go to the deep sleep state
                            from the sleep state or the charge state            
bms save                  --this command will save the current settings 
                            (parameters) to flash
bms load                  --this command will load the saved settings
                            (parameters) from flash
bms default               --this command will load the default settings         
bms time                  --this command will output the time since boot        
reboot                    --this command will reboot the microcontroller        
                            this command should be used without the word bms 
                            in front of it
                                                                                
some parameters have a letter in front of the "-", this indicates the type of 
parameter
a - capacity                                                                    
c - temperature (celcius)                                                       
e - energy                                                                      
i - current                                                                     
m - mass                                                                        
n - number                                                                      
s - status                                                                      
t - time                                                                        
v - voltage 
```

## What parameters are there?

When you type "bms help parameters", you will get a list with all the parameters with its unit, if it is Read Only (RO) or Read Write (RW) and what the data type is it. These are useful parameter properties that help with filling in parameters correctly.

## How can I see the cyclic update of the parameters?

The "bms help show-meas" command shows you which parameters you can view in cyclically in the CLI when the measurement happens. These commands should be used with the "bms show". To show them all, use "bms show all 1". if you want the measurements to be outlined and updated at the top of your terminal, use "bms show top 1". Keep in mind that if this is active, it could be that typed in characters disappear in this update.&#x20;

{% hint style="warning" %}
The BMS uses VT100 escape sequences to update the terminal. In order to see this, make sure your terminal emulation program (like PuTTY or minicom) has VT100 mode enabled.
{% endhint %}

## How do I get parameter values?

To get a single parameter value, you could use the bms get command. If for example you would like to get the state of charge, type "bms get s-charge" in the terminal. It will provide you with the value and its unit. If you want to check a lot of parameters, use the "bms get all" command, this will give you the full list of parameters, with the value and its unit.  \
When you wish to load the parameters from flash, type "bms load".&#x20;

## How do I set parameter values?

To adjust parameter values, you need to use the bms set command. If for example you would like to set the number of cells to 4, you need to enter the following command: "bms set n-cells 4".  \
To make sure parameters are saved to flash, type "bms save". \
If you would like to set the default parameters, type "bms default".&#x20;

## What parameters can I use to change the state?

To get out of the FAULT state the BMS needs to reset the FAULT, type "bms reset".\
To get in the SLEEP state (if you are able to enter it), type "bms sleep". \
To wake-up from the sleep state, type "bms wake".\
To go to the DEEP\_SLEEP state, type "bms deepsleep", it could be that it first self-discharges. &#x20;

