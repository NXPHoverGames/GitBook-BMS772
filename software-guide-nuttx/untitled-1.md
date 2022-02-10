---
description: This page shows the parameters of the BMS.
---

# Parameters of the BMS

This page will describe the variables of the BMS. \
There are 3 kind of parameters

1. The BMS variables
2. The BMS configuration parameters&#x20;
3. The hardware parameters&#x20;

The BMS variables give the variables of the BMS, like the voltages, currents and temperatures. \
The BMS configuration parameters are the parameters that could be used to configure the BMS, like the battery parameters, BMS parameters and more.\
The hardware parameters could be used to keep track of the parameters of the hardware parameters, like the maximum current that is limited by the MOSFETs power dissipation.&#x20;

{% hint style="info" %}
In the console (CLI) type "bms get all" to get all the parameters and its current value.
{% endhint %}

## &#x20;BMS variables list

| **Parameter**      | **Unit** | **Datatype** | **Description**                                                                                                                                           | **Default**             | **RO/RW** | **No** |
| ------------------ | -------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | --------- | ------ |
| **c-batt**         | C        | float        | The temperature of the battery                                                                                                                            | 0                       | RO        | 0      |
| **v-out**          | V        | float        | The voltage of the BMS output                                                                                                                             | 0                       | RO        | 1      |
| **v-batt**         | V        | float        | The voltage of the battery pack                                                                                                                           | 0                       | RO        | 2      |
| **i-batt**         | A        | float        | The last recorded current of the battery                                                                                                                  | 0                       | RO        | 3      |
| **i-batt-avg**     | A        | Float        | <p>The average current since the last</p><p>measurement (period T_meas (defaults))</p>                                                                    | 0                       | RO        | 4      |
| **s-out**          | -        | bool         | This is true if the output power is enabled                                                                                                               | 0                       | RO        | 5      |
| **p-avg**          | W        | float        | <p>Average power consumption over the last</p><p>10 seconds</p>                                                                                           | 0                       | RO        | 6      |
| **e-used**         | Wh       | float        | Power consumption since device boot                                                                                                                       | 0                       | RO        | 7      |
| **a-rem**          | Ah       | float        | Remaining capacity in the battery                                                                                                                         | 2.6                     | RW        | 8      |
| **a-full**         | Ah       | float        | <p>Predicted battery capacity when it is fully</p><p>charged. falls with aging</p>                                                                        | 4.6                     | RW        | 9      |
| **t-full**         | h        | float        | <p>Charging is expected to complete in this</p><p>time; zero if not charging</p>                                                                          | 0                       | RO        | 10     |
| **s-flags**        | -        | uint8\_t     | <p>This contains the status flags as</p><p>described in BMS_status_flags_t</p>                                                                            | 255                     | RO        | 11     |
| **s-health**       | %        | uint8\_t     | <p>Health of the battery in percentage, use</p><p>STATE_OF_HEALTH_UNKNOWN = 127</p><p>if cannot be estimated</p>                                          | 127                     | RO        | 12     |
| **s-charge**       | %        | uint8\_t     | <p>Percentage of the full charge 0, 100.</p><p>This field is required.</p>                                                                                | 55                      | RO        | 13     |
| **batt-id**        | -        | uint8\_t     | <p>Identifies the battery within this vehicle,</p><p> 0 - primary battery.</p>                                                                            | 0                       | RW        | 14     |
| **model-id**       | -        | int32\_t     | Model id, set to 0 if not applicable                                                                                                                      | 0                       | RW        | 15     |
| **model-name**     | -        | Char\[32]    | <p>Battery model name, model name is a</p><p>human-readable string that normally</p><p>should include the vendor name, model</p><p>name and chemistry</p> | <p>"BMS</p><p>test"</p> | RW        | 16     |
| **v-cell1**        | V        | float        | The voltage of cell 1                                                                                                                                     | 0                       | RO        | 17     |
| **v-cell2**        | V        | float        | The voltage of cell 2                                                                                                                                     | 0                       | RO        | 18     |
| **v-cell3**        | V        | float        | The voltage of cell 3                                                                                                                                     | 0                       | RO        | 19     |
| **v-cell4**        | V        | float        | The voltage of cell 4                                                                                                                                     | 0                       | RO        | 20     |
| **v-cell5**        | V        | float        | The voltage of cell 5                                                                                                                                     | 0                       | RO        | 21     |
| **v-cell6**        | V        | float        | The voltage of cell 6                                                                                                                                     | 0                       | RO        | 22     |
| **c-afe**          | C        | float        | The temperature of the analog front end                                                                                                                   | 0                       | RO        | 23     |
| **c-fet**          | C        | float        | The temperature of the transistor                                                                                                                         | 0                       | RO        | 24     |
| **c-r**            | C        | float        | The temperature of the sense resistor                                                                                                                     | 0                       | RO        | 25     |
| **n-charges**      | -        | uint16\_t    | The number of charges done                                                                                                                                | 0                       | RW        | 26     |
| **n-charges-full** | -        | uint16\_t    | The number of complete charges                                                                                                                            | 0                       | RW        | 27     |

\
&#x20;BMS configuration parameters list
---------------------------------------

| **Parameter**                  | **Unit**    | **Datatype**  | **Description**                                                                                                                                                  | **Default** | **RO/RW** | **No** |
| ------------------------------ | ----------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | --------- | ------ |
| **n-cells**                    | -           | uint8\_t      | Number of cells used in the BMS board                                                                                                                            | 3           | RW        | 28     |
| **t-meas**                     | ms          | uint16\_t     | Cycle of the battery to perform a complete battery measurement and SOC estimation can only be 10000 or a whole division of 10000 (For example: 5000, 1000, 500). | 1000        | RW        | 29     |
| ~~**t-ftti**~~                 | ~~ms~~      | ~~uint16\_t~~ | ~~Cycle of the battery to perform diagnostics (Fault Tolerant Time Interval)~~                                                                                   | ~~1000~~    | ~~RW~~    | ~~30~~ |
| **t-cyclic**                   | s           | uint8\_t      | Wake up cyclic timing of the AFE (after front end) during sleep mode                                                                                             | 1           | RW        | 31     |
| **i-sleep-oc**                 | mA          | uint8\_t      | Overcurrent threshold detection in sleep mode that will wake up the BMS and also the threshold to detect the battery is not in use                               | 30          | RW        | 32     |
| **v-cell-ov**                  | V           | float         | Battery maximum allowed voltage for one cell. Exceeding this voltage, the BMS will go to fault mode.                                                             | 4.2         | RW        | 33     |
| **v-cell-uv**                  | V           | float         | Battery minimum allowed voltage for one cell. Going below this voltage, the BMS will go to deep\_sleep mode.                                                     | 3           | RW        | 34     |
| **c-cell-ot**                  | C           | float         | Over temperature threshold for the cells. Going over this threshold and the BMS will go to FAULT mode                                                            | 45          | RW        | 35     |
| **c-cell-ot-charge**           | C           | float         | Over temperature threshold for the cells during charging. Going over this threshold and the BMS will go to FAULT mode                                            | 40          | RW        | 36     |
| **c-cell-ut**                  | C           | float         | Under temperature threshold for the cells. Going under this threshold and the BMS will go to FAULT mode                                                          | (-20)       | RW        | 37     |
| **c-cell-ut-charge**           | C           | float         | Under temperature threshold for the cells during charging. Going under this threshold during charging and the BMS will go to FAULT mode                          | 0           | RW        | 38     |
| **a-factory**                  | Ah          | float         | Battery capacity stated by the factory                                                                                                                           | 4.6         | RW        | 39     |
| **t-bms-timeout**              | s           | uint16\_t     | Timeout for the BMS to go to SLEEP mode when the battery is not used.                                                                                            | 600         | RW        | 40     |
| ~~**t-fault-timeout**~~        | ~~s~~       | ~~uint8\_t~~  | ~~After this timeout, the battery will leave the FAULT mode and go to SLEEP mode. T~~                                                                            | ~~60~~      | ~~RW~~    | ~~41~~ |
| **t-charge-detect**            | s           | uint8\_t      | During NORMAL mode, if the battery voltage is positive for more than this time, then the BMS will go to CHARGE mode                                              | 1           | RW        | 42     |
| **t-cb-delay**                 | s           | uint8\_t      | Time for the cell balancing function to start after entering the CHARGE mode                                                                                     | 120         | RW        | 43     |
| **t-charge-relax**             | s           | uint16\_t     | Relaxation after the charge is complete before going to another charge round.                                                                                    | 300         | RW        | 44     |
| **i-charge-full**              | mA          | uint16\_t     | Current threshold to detect end of charge sequence                                                                                                               | 50          | RW        | 45     |
| **i-charge-max**               | A           | float         | Maximum current threshold to open the switch during charging                                                                                                     | 9**.**2     | RW        | 46     |
| **i-out-max**                  | A           | float         | Maximum current threshold to open the switch during normal operation, if not overruled                                                                           | 60          | RW        | 47     |
| **v-cell-margin**              | mV          | uint8\_t      | Cell voltage charge margin to decide or not to go through another topping charge cycle                                                                           | 30          | RW        | 48     |
| ~~**t-ocv-cyclic0**~~          | ~~s~~       | ~~int32\_t~~  | ~~OCV measurement cyclic timer start (timer is increase by 50% at each cycle)~~                                                                                  | ~~300~~     | ~~RW~~    | ~~49~~ |
| ~~**t-ocv-cyclic1**~~          | ~~s~~       | ~~int32\_t~~  | ~~OCV measurement cyclic timer final (timer is increase by 50% at each cycle)~~                                                                                  | ~~86400~~   | ~~RW~~    | ~~50~~ |
| **c-pcb-ut**                   | C           | float         | Minimal ambient temperature (measured on the PCB)                                                                                                                | -20         | RW        | 51     |
| **c-pcb-ot**                   | C           | float         | Maximal ambient temperature (measured on the PCB)                                                                                                                | 45          | RW        | 52     |
| **v-storage**                  | V           | float         | The voltage what is specified as storage voltage for a cell                                                                                                      | 3.8         | RW        | 53     |
| ~~**ocv-slope**~~              | ~~V/A.min~~ | ~~float~~     | ~~The slope of the OCV curve~~                                                                                                                                   | ~~0~~       | ~~RW~~    | ~~54~~ |
| **batt-eol**                   | %           | uint8\_t      | Percentage at which the battery is end-of-life and shouldn’t be used anymore Typically between 90%-50%                                                           | 80          | RW        | 55     |
| **sensor-enable**              | -           | bool          | This variable is used to enable or disable the battery temperature sensor, 0 is disabled, 1 is enabled                                                           | 0           | RW        | 56     |
| **self-discharge-enable**      | -           | bool          | this variable is used to enable or disable the SELF\_DISCHARGE state, 0 is disabled, 1 is enabled                                                                | 1           | RW        | 57     |
| **uavcan\_node\_static\_id\*** | -           | uint8\_t      | This is the node ID of the UAVCAN message                                                                                                                        | 255         | RW        | 58     |
| **uavcan-subject-id\***        | -           | uint16\_t     | This is the subject ID of the UAVCAN message                                                                                                                     | 4096        | RW        | 59     |
| **uavcan-fd-mode\***           | -           | uint8\_t      | If true CANFD is used, otherwise classic CAN is used                                                                                                             | 0           | RW        | 60     |
| **uavcan-bitrate\***           | bit/s       | int32\_t      | the bitrate of classical can or CAN FD arbitration bitrate                                                                                                       | 1000000     | RW        | 61     |
| **uavcan-fd-bitrate\***        | bit/s       | int32\_t      | the bitrate of CAN FD data bitrate                                                                                                                               | 4000000     | RW        | 62     |

A ~~line~~ means this is not implemented yet.\
\*these parameters will only be implemented during startup of the BMS

\
BMS hardware parameters list
----------------------------

| **Parameter** | **Unit** | **Datatype** | **Description**                                                                           | **Default** | **RO/RW** | **No** |
| ------------- | -------- | ------------ | ----------------------------------------------------------------------------------------- | ----------- | --------- | ------ |
| **v-min**     | V        | uint8\_t     | Minimum stack voltage for the BMS board to be fully functional                            | 6           | RW        | 63     |
| **v-max**     | V        | uint8\_t     | Maximum stack voltage allowed by the BMS board                                            | 26          | RW        | 64     |
| **i-peak**    | A        | uint16\_t    | Maximum peak current that can be measured by the BMS board                                | 200         | RW        | 65     |
| **i-max**     | A        | uint8\_t     | Maximum DC current allowed in the BMS board (limited by power dissipation in the MOSFETs) | 60          | RW        | 66     |
| **i-short**   | A        | uint16\_t    | short circuit current threshold (typical: 550A, min: 500A, max: 600A)                     | 500         | RW        | 67     |
| **t-short**   | us       | uint8\_t     | Blanking time for the short circuit detection                                             | 20          | RW        | 68     |
| **i-bal**     | mA       | uint8\_t     | Cell balancing current under 4.2V with cell balancing resistors of 82 ohms                | 50          | RW        | 69     |

