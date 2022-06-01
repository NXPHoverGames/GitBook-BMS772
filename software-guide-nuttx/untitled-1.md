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
| **c-batt**         | C        | float        | The temperature of the external battery temperature sensor                                                                                                | 0                       | RO        | 0      |
| **v-out**          | V        | float        | The voltage of the BMS output                                                                                                                             | 0                       | RO        | 1      |
| **v-batt**         | V        | float        | The voltage of the battery pack                                                                                                                           | 0                       | RO        | 2      |
| **i-batt**         | A        | float        | The last recorded current of the battery                                                                                                                  | 0                       | RO        | 3      |
| **i-batt-avg**     | A        | float        | <p>The average current since the last</p><p>measurement (period t_meas (defaults))</p>                                                                    | 0                       | RO        | 4      |
| **i-batt-10s-avg** | A        | float        | The 10s rollling average current, updated each 1s with T\_meas 1000 (ms)                                                                                  | 0                       | RO        | 5      |
| **s-out**          | -        | bool         | This is true if the output power is enabled                                                                                                               | 0                       | RO        | 6      |
| **s-in-flight**    | -        | bool         | This is true if the system is in flight (with flight-mode-enable and i-flight-mode)                                                                       | 0                       | RO        | 7      |
| **p-avg**          | W        | float        | <p>Average power consumption over the last</p><p>10 seconds</p>                                                                                           | 0                       | RO        | 8      |
| **e-used**         | Wh       | float        | Power consumption since device boot                                                                                                                       | 0                       | RO        | 9      |
| **a-rem**          | Ah       | float        | Remaining capacity in the battery                                                                                                                         | 0                       | RW        | 10     |
| **a-full**         | Ah       | float        | Full charge capacity, predicted battery capacity when it is fully charged. Falls with aging                                                               | 4.6                     | RW        | 11     |
| **t-full**         | h        | float        | <p>Charging is expected to complete in this</p><p>time; <del>zero if not charging</del></p>                                                               | 0                       | RO        | 12     |
| **s-flags**        | -        | uint8\_t     | <p>This contains the status flags as</p><p>described in BMS_status_flags_t</p>                                                                            | 255                     | RO        | 13     |
| **s-health**       | %        | uint8\_t     | <p>Health of the battery in percentage, use</p><p>STATE_OF_HEALTH_UNKNOWN = 127</p><p>if cannot be estimated</p>                                          | 127                     | RO        | 14     |
| **s-charge**       | %        | uint8\_t     | Percentage of the full charge 0, 100                                                                                                                      | 0                       | RO        | 15     |
| **batt-id**        | -        | uint8\_t     | <p>Identifies the battery within this vehicle,</p><p> 0 - primary battery.</p>                                                                            | 0                       | RW        | 16     |
| **model-id**       | -        | uint64\_t    | Model id, set to 0 if not applicable                                                                                                                      | 0                       | RW        | 17     |
| **model-name**     | -        | char\[32]    | <p>Battery model name, model name is a</p><p>human-readable string that normally</p><p>should include the vendor name, model</p><p>name and chemistry</p> | <p>"BMS</p><p>test"</p> | RW        | 18     |
| **v-cell1**        | V        | float        | The voltage of cell 1                                                                                                                                     | 0                       | RO        | 19     |
| **v-cell2**        | V        | float        | The voltage of cell 2                                                                                                                                     | 0                       | RO        | 20     |
| **v-cell3**        | V        | float        | The voltage of cell 3                                                                                                                                     | 0                       | RO        | 21     |
| **v-cell4**        | V        | float        | The voltage of cell 4                                                                                                                                     | 0                       | RO        | 22     |
| **v-cell5**        | V        | float        | The voltage of cell 5                                                                                                                                     | 0                       | RO        | 23     |
| **v-cell6**        | V        | float        | The voltage of cell 6                                                                                                                                     | 0                       | RO        | 24     |
| **c-afe**          | C        | float        | The temperature of the analog front end                                                                                                                   | 0                       | RO        | 25     |
| **c-t**            | C        | float        | The temperature of the transistor                                                                                                                         | 0                       | RO        | 26     |
| **c-r**            | C        | float        | The temperature of the sense resistor                                                                                                                     | 0                       | RO        | 27     |
| **n-charges**      | -        | uint16\_t    | The number of charges done                                                                                                                                | 0                       | RW        | 28     |
| **n-charges-full** | -        | uint16\_t    | The number of complete charges                                                                                                                            | 0                       | RW        | 29     |

\
&#x20;BMS configuration parameters list
---------------------------------------

| **Parameter**                  | **Unit** | **Datatype**  | **Description**                                                                                                                                                 | **Default** | **RO/RW** | **No** |
| ------------------------------ | -------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | --------- | ------ |
| **n-cells**                    | -        | uint8\_t      | Number of cells used in the BMS board                                                                                                                           | 3           | RW        | 30     |
| **t-meas**                     | ms       | uint16\_t     | Cycle of the battery to perform a complete battery measurement and SOC estimation can only be 10000 or a whole division of 10000 (For example: 5000, 1000, 500) | 1000        | RW        | 31     |
| ~~**t-ftti**~~                 | ~~ms~~   | ~~uint16\_t~~ | ~~Cycle of the battery to perform diagnostics (Fault Tolerant Time Interval)~~                                                                                  | ~~1000~~    | ~~RW~~    | ~~32~~ |
| **t-cyclic**                   | s        | uint8\_t      | Wake up cyclic timing of the AFE (after front end) during sleep mode                                                                                            | 1           | RW        | 33     |
| **i-sleep-oc**                 | mA       | uint8\_t      | Overcurrent threshold detection in sleep mode that will wake up the BMS and also the threshold to detect the battery is not in use                              | 30          | RW        | 34     |
| **v-cell-ov**                  | V        | float         | Battery maximum allowed voltage for one cell. Exceeding this voltage, the BMS will go to fault mode                                                             | 4.2         | RW        | 35     |
| **v-cell-uv**                  | V        | float         | Battery minimum allowed voltage for one cell. Going below this voltage, the BMS will go to fault mode (followed by deepsleep after t-fault-timeout)             | 3           | RW        | 36     |
| **v-cell-nominal**             | V        | float         | Battery nominal voltage for one cell. will be used for energy calculation                                                                                       | 3.7         | RW        | 37     |
| **c-cell-ot**                  | C        | float         | Over temperature threshold for the cells. Going over this threshold and the BMS will go to FAULT mode                                                           | 45          | RW        | 38     |
| **c-cell-ot-charge**           | C        | float         | Over temperature threshold for the cells during charging. Going over this threshold and the BMS will go to FAULT mode                                           | 40          | RW        | 39     |
| **c-cell-ut**                  | C        | float         | Under temperature threshold for the cells. Going under this threshold and the BMS will go to FAULT mode                                                         | (-20)       | RW        | 40     |
| **c-cell-ut-charge**           | C        | float         | Under temperature threshold for the cells during charging. Going under this threshold during charging and the BMS will go to FAULT mode                         | 0           | RW        | 41     |
| **a-factory**                  | Ah       | float         | Battery capacity stated by the factory                                                                                                                          | 4.6         | RW        | 42     |
| **t-bms-timeout**              | s        | uint16\_t     | Timeout for the BMS to go to SLEEP mode when the battery is not used.                                                                                           | 600         | RW        | 43     |
| **t-fault-timeout**            | s        | uint16\_t     | After this timeout, with an undervoltage fault the battery will go to DEEPSLEEP mode to preserve power. 0 sec is disabled.                                      | 60          | RW        | 44     |
| **t-sleep-timeout**            | h        | uint8\_t      | When the BMS is in sleep mode for this period it will go to the self-discharge mode, 0 if disabled                                                              | 24          | RW        | 45     |
| **t-charge-detect**            | s        | uint8\_t      | During NORMAL mode, if the battery current is positive for more than this time, then the BMS will go to CHARGE mode                                             | 1           | RW        | 46     |
| **t-cb-delay**                 | s        | uint8\_t      | Time for the cell balancing function to start after entering the CHARGE mode                                                                                    | 120         | RW        | 47     |
| **t-charge-relax**             | s        | uint16\_t     | Relaxation time after the charge is complete before going to another charge round.                                                                              | 300         | RW        | 48     |
| **i-charge-full**              | mA       | uint16\_t     | Current threshold to detect end of charge sequence                                                                                                              | 50          | RW        | 49     |
| **i-system**                   | mA       | uint8\_t      | Current of the BMS board itself, this is measured (as well) during charging, so this needs to be subtracted                                                     | 40          | RW        | 50     |
| **i-charge-max**               | A        | float         | Maximum current threshold to open the switch during charging                                                                                                    | 9**.**2     | RW        | 51     |
| **i-charge-nominal**           | A        | float         | Nominal charge current (informative only)                                                                                                                       | 4.6         | RW        | 52     |
| **i-out-max**                  | A        | float         | Maximum current threshold to open the switch during normal operation, if not overruled                                                                          | 60          | RW        | 53     |
| **i-peak-max**                 | A        | float         | Maximum peak current threshold to open the switch during normal operation, can't be overruled                                                                   | 200         | RW        | 54     |
| **i-out-nominal**              | A        | float         | Nominal discharge current (informative only)                                                                                                                    | 60          | RW        | 55     |
| **i-flight-mode**              | A        | float         | Current threshold to not disable the power in flight mode                                                                                                       | 5           | RW        | 56     |
| **v-cell-margin**              | mV       | uint8\_t      | Cell voltage charge margin to decide or not to go through another topping charge cycle                                                                          | 50          | RW        | 57     |
| **v-recharge-margin**          | mV       | uint16\_t     | Cell voltage charge complete margin to decide or not to do a battery re-charge, to keep the cell voltages at max this much difference with the cell-ov          | 200         | RW        | 58     |
| **t-ocv-cyclic0**              | s        | int32\_t      | OCV measurement cyclic timer start (timer is increase by 50% at each cycle)                                                                                     | 300         | RW        | 59     |
| **t-ocv-cyclic1**              | s        | int32\_t      | OCV measurement cyclic timer final value (limit)                                                                                                                | 86400       | RW        | 60     |
| **c-pcb-ut**                   | C        | float         | PCB Ambient temperature under temperature threshold                                                                                                             | -20         | RW        | 61     |
| **c-pcb-ot**                   | C        | float         | PCB Ambient temperature over temperature threshold                                                                                                              | 45          | RW        | 62     |
| **v-storage**                  | V        | float         | The voltage what is specified as storage voltage for a cell                                                                                                     | 3.8         | RW        | 63     |
| **ocv-slope**                  | mV/A.min | float         | The slope of the OCV curve. This will be used to calculate the balance time                                                                                     | 5.3         | RW        | 64     |
| **batt-eol**                   | %        | uint8\_t      | Percentage at which the battery is end-of-life and shouldn’t be used anymore Typically between 90%-50%                                                          | 80          | RW        | 65     |
| **battery-type**               | -        | uint8\_t      | The type of battery attached to it. 0 = LiPo, 1 = LiFePo4, 2 = LiFeYPo4. Could be extended. Will change OV, UV, v-storage, OCV/SoC table if changed runtime     | 0           | RW        | 66     |
| **sensor-enable**              | -        | bool          | This variable is used to enable or disable the battery temperature sensor, 0 is disabled, 1 is enabled                                                          | 0           | RW        | 67     |
| **self-discharge-enable**      | -        | bool          | This variable is used to enable or disable the SELF\_DISCHARGE state, 0 is disabled, 1 is enabled                                                               | 1           | RW        | 68     |
| **flight-mode-enable**         | -        | bool          | This variable is used to enable or disable flight mode, is used together with i-flight-mode                                                                     | 0           | RW        | 69     |
| **emergency-button-enable**    | -        | bool          | This variable is used to enable or disable the emergency button on PTE8                                                                                         | 0           | RW        | 70     |
| **smbus-enable**               | -        | bool          | This variable is used to enable or disable the SMBus update                                                                                                     | 0           | RW        | 71     |
| **uavcan\_node\_static\_id\*** | -        | uint8\_t      | This is the node ID of the UAVCAN message                                                                                                                       | 255         | RW        | 72     |
| **uavcan-es-sub-id\***         | -        | uint16\_t     | This is the subject ID of the energy source UAVCAN message (1...100Hz)                                                                                          | 4096        | RW        | 73     |
| **uavcan-bs-sub-id\***         | -        | uint16\_t     | This is the subject ID of the battery status UAVCAN message (1Hz)                                                                                               | 4097        | RW        | 74     |
| **uavcan-bp-sub-id\***         | -        | uint16\_t     | This is the subject ID of the battery parameters UAVCAN message (0.2Hz)                                                                                         | 4098        | RW        | 75     |
| **uavcan-legacy-bi-sub-id\***  | -        | uint16\_t     | This is the subject ID of the battery info legacy UAVCAN message (0.2 \~ 1Hz)                                                                                   | 65535       | RW        | 76     |
| **uavcan-fd-mode\***           | -        | uint8\_t      | If true CANFD is used, otherwise classic CAN is used                                                                                                            | 0           | RW        | 77     |
| **uavcan-bitrate\***           | bit/s    | int32\_t      | The bitrate of classical can or CAN FD arbitration bitrate                                                                                                      | 1000000     | RW        | 78     |
| **uavcan-fd-bitrate\***        | bit/s    | int32\_t      | The bitrate of CAN FD data bitrate                                                                                                                              | 4000000     | RW        | 79     |

A ~~line~~ means this is not implemented yet.\
\*these parameters will only be implemented during startup of the BMS

\
BMS hardware parameters list
----------------------------

| **Parameter**   | **Unit** | **Datatype** | **Description**                                                                           | **Default** | **RO/RW** | **No** |
| --------------- | -------- | ------------ | ----------------------------------------------------------------------------------------- | ----------- | --------- | ------ |
| **v-min**       | V        | uint8\_t     | Minimum stack voltage for the BMS board to be fully functional                            | 6           | RW        | 80     |
| **v-max**       | V        | uint8\_t     | Maximum stack voltage allowed by the BMS board                                            | 26          | RW        | 81     |
| **i-range-max** | A        | uint16\_t    | Maximum current that can be measured by the BMS board                                     | 300         | RW        | 82     |
| **i-max**       | A        | uint8\_t     | Maximum DC current allowed in the BMS board (limited by power dissipation in the MOSFETs) | 60          | RW        | 83     |
| **i-short**     | A        | uint16\_t    | short circuit current threshold (typical: 550A, min: 500A, max: 600A)                     | 500         | RW        | 84     |
| **t-short**     | us       | uint8\_t     | Blanking time for the short circuit detection                                             | 20          | RW        | 85     |
| **i-bal**       | mA       | uint8\_t     | Cell balancing current under 4.2V with cell balancing resistors of 82 ohms                | 50          | RW        | 86     |
| **m-mass**      | kg       | float        | The total mass of the (smart) battery                                                     | 0           | RW        | 87     |

