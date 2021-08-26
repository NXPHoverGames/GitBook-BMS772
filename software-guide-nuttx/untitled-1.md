---
description: This page shows the parameters of the BMS.
---

# Parameters of the BMS

This page will describe the variables of the BMS.   
There are 3 kind of parameters

1. The BMS variables
2. The BMS configuration parameters 
3. The hardware parameters 

The BMS variables give the variables of the BMS, like the voltages, currents and temperatures.   
The BMS configuration parameters are the parameters that could be used to configure the BMS, like the battery parameters, BMS parameters and more.  
The hardware parameters could be used to keep track of the parameters of the hardware parameters, like the maximum current that is limited by the MOSFETs power dissipation. 

{% hint style="info" %}
In the console \(CLI\) type "bms get all" to get all the parameters and its current value.
{% endhint %}

##  BMS variables list

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter</b>
      </th>
      <th style="text-align:left"><b>Unit</b>
      </th>
      <th style="text-align:left"><b>Datatype</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
      <th style="text-align:left"><b>Default</b>
      </th>
      <th style="text-align:left"><b>RO/RW</b>
      </th>
      <th style="text-align:left"><b>No</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>c-batt</b>
      </td>
      <td style="text-align:left">C</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The temperature of the external battery temperature sensor</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">0</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>v-out</b>
      </td>
      <td style="text-align:left">V</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The voltage of the BMS output</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">1</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>v-batt</b>
      </td>
      <td style="text-align:left">V</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The voltage of the battery pack</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">2</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>i-batt</b>
      </td>
      <td style="text-align:left">A</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The last recorded current of the battery</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">3</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>i-batt-avg</b>
      </td>
      <td style="text-align:left">A</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">
        <p>The average current since the last</p>
        <p>measurement (period t_meas (defaults))</p>
      </td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">4</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>i-batt-10s-avg</b>
      </td>
      <td style="text-align:left">A</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The 10s rollling average current, updated each 1s with T_meas 1000 (ms)</td>
      <td
      style="text-align:left">0</td>
        <td style="text-align:left">RO</td>
        <td style="text-align:left">5</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>s-out</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">bool</td>
      <td style="text-align:left">This is true if the output power is enabled</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">6</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>s-in-flight</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">bool</td>
      <td style="text-align:left">This is true if the system is in flight (with flight-mode-enable and i-flight-mode)</td>
      <td
      style="text-align:left">0</td>
        <td style="text-align:left">RO</td>
        <td style="text-align:left">7</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>p-avg</b>
      </td>
      <td style="text-align:left">W</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">
        <p>Average power consumption over the last</p>
        <p>10 seconds</p>
      </td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">8</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>e-used</b>
      </td>
      <td style="text-align:left">Wh</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">Power consumption since device boot</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">9</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>a-rem</b>
      </td>
      <td style="text-align:left">Ah</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">Remaining capacity in the battery</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RW</td>
      <td style="text-align:left">10</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>a-full</b>
      </td>
      <td style="text-align:left">Ah</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">Full charge capacity, predicted battery capacity when it is fully charged.
        Falls with aging</td>
      <td style="text-align:left">4.6</td>
      <td style="text-align:left">RW</td>
      <td style="text-align:left">11</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>t-full</b>
      </td>
      <td style="text-align:left">h</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">
        <p>Charging is expected to complete in this</p>
        <p>time; <del>zero if not charging</del>
        </p>
      </td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">12</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>s-flags</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">uint8_t</td>
      <td style="text-align:left">
        <p>This contains the status flags as</p>
        <p>described in BMS_status_flags_t</p>
      </td>
      <td style="text-align:left">255</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">13</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>s-health</b>
      </td>
      <td style="text-align:left">%</td>
      <td style="text-align:left">uint8_t</td>
      <td style="text-align:left">
        <p>Health of the battery in percentage, use</p>
        <p>STATE_OF_HEALTH_UNKNOWN = 127</p>
        <p>if cannot be estimated</p>
      </td>
      <td style="text-align:left">127</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">14</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>s-charge</b>
      </td>
      <td style="text-align:left">%</td>
      <td style="text-align:left">uint8_t</td>
      <td style="text-align:left">Percentage of the full charge 0, 100</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">15</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>batt-id</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">uint8_t</td>
      <td style="text-align:left">
        <p>Identifies the battery within this vehicle,</p>
        <p>0 - primary battery.</p>
      </td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RW</td>
      <td style="text-align:left">16</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>model-id</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">uint64_t</td>
      <td style="text-align:left">Model id, set to 0 if not applicable</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RW</td>
      <td style="text-align:left">17</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>model-name</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">char[32]</td>
      <td style="text-align:left">
        <p>Battery model name, model name is a</p>
        <p>human-readable string that normally</p>
        <p>should include the vendor name, model</p>
        <p>name and chemistry</p>
      </td>
      <td style="text-align:left">
        <p>&quot;BMS</p>
        <p>test&quot;</p>
      </td>
      <td style="text-align:left">RW</td>
      <td style="text-align:left">18</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>v-cell1</b>
      </td>
      <td style="text-align:left">V</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The voltage of cell 1</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">19</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>v-cell2</b>
      </td>
      <td style="text-align:left">V</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The voltage of cell 2</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">20</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>v-cell3</b>
      </td>
      <td style="text-align:left">V</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The voltage of cell 3</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">21</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>v-cell4</b>
      </td>
      <td style="text-align:left">V</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The voltage of cell 4</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">22</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>v-cell5</b>
      </td>
      <td style="text-align:left">V</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The voltage of cell 5</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">23</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>v-cell6</b>
      </td>
      <td style="text-align:left">V</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The voltage of cell 6</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">24</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>c-afe</b>
      </td>
      <td style="text-align:left">C</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The temperature of the analog front end</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">25</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>c-t</b>
      </td>
      <td style="text-align:left">C</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The temperature of the transistor</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">26</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>c-r</b>
      </td>
      <td style="text-align:left">C</td>
      <td style="text-align:left">float</td>
      <td style="text-align:left">The temperature of the sense resistor</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RO</td>
      <td style="text-align:left">27</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>n-charges</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">uint16_t</td>
      <td style="text-align:left">The number of charges done</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RW</td>
      <td style="text-align:left">28</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>n-charges-full</b>
      </td>
      <td style="text-align:left">-</td>
      <td style="text-align:left">uint16_t</td>
      <td style="text-align:left">The number of complete charges</td>
      <td style="text-align:left">0</td>
      <td style="text-align:left">RW</td>
      <td style="text-align:left">29</td>
    </tr>
  </tbody>
</table>

##   BMS configuration parameters list

| **Parameter** | **Unit** | **Datatype** | **Description** | **Default** | **RO/RW** | **No** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **n-cells** | - | uint8\_t | Number of cells used in the BMS board | 3 | RW | 30 |
| **t-meas** | ms | uint16\_t | Cycle of the battery to perform a complete battery measurement and SOC estimation can only be 10000 or a whole division of 10000 \(For example: 5000, 1000, 500\) | 1000 | RW | 31 |
| ~~**t-ftti**~~ | ~~ms~~ | ~~uint16\_t~~ | ~~Cycle of the battery to perform diagnostics \(Fault Tolerant Time Interval\)~~ | ~~1000~~ | ~~RW~~ | ~~32~~ |
| **t-cyclic** | s | uint8\_t | Wake up cyclic timing of the AFE \(after front end\) during sleep mode | 1 | RW | 33 |
| **i-sleep-oc** | mA | uint8\_t | Overcurrent threshold detection in sleep mode that will wake up the BMS and also the threshold to detect the battery is not in use | 30 | RW | 34 |
| **v-cell-ov** | V | float | Battery maximum allowed voltage for one cell. Exceeding this voltage, the BMS will go to fault mode | 4.2 | RW | 35 |
| **v-cell-uv** | V | float | Battery minimum allowed voltage for one cell. Going below this voltage, the BMS will go to fault mode \(followed by deepsleep after t-fault-timeout\) | 3 | RW | 36 |
| **v-cell-nominal** | V | float | Battery nominal voltage for one cell. will be used for energy calculation | 3.7 | RW | 37 |
| **c-cell-ot** | C | float | Over temperature threshold for the cells. Going over this threshold and the BMS will go to FAULT mode | 45 | RW | 38 |
| **c-cell-ot-charge** | C | float | Over temperature threshold for the cells during charging. Going over this threshold and the BMS will go to FAULT mode | 40 | RW | 39 |
| **c-cell-ut** | C | float | Under temperature threshold for the cells. Going under this threshold and the BMS will go to FAULT mode | \(-20\) | RW | 40 |
| **c-cell-ut-charge** | C | float | Under temperature threshold for the cells during charging. Going under this threshold during charging and the BMS will go to FAULT mode | 0 | RW | 41 |
| **a-factory** | Ah | float | Battery capacity stated by the factory | 4.6 | RW | 42 |
| **t-bms-timeout** | s | uint16\_t | Timeout for the BMS to go to SLEEP mode when the battery is not used. | 600 | RW | 43 |
| **t-fault-timeout** | s | uint16\_t | After this timeout, with an undervoltage fault the battery will go to DEEPSLEEP mode to preserve power. 0 sec is disabled. | 60 | RW | 44 |
| **t-sleep-timeout** | h | uint8\_t | When the BMS is in sleep mode for this period it will go to the self-discharge mode, 0 if disabled | 24 | RW | 45 |
| **t-charge-detect** | s | uint8\_t | During NORMAL mode, if the battery current is positive for more than this time, then the BMS will go to CHARGE mode | 1 | RW | 46 |
| **t-cb-delay** | s | uint8\_t | Time for the cell balancing function to start after entering the CHARGE mode | 120 | RW | 47 |
| **t-charge-relax** | s | uint16\_t | Relaxation time after the charge is complete before going to another charge round. | 300 | RW | 48 |
| **i-charge-full** | mA | uint16\_t | Current threshold to detect end of charge sequence | 50 | RW | 49 |
| **i-system** | mA | uint8\_t | Current of the BMS board itself, this is measured \(as well\) during charging, so this needs to be subtracted | 40 | RW | 50 |
| **i-charge-max** | A | float | Maximum current threshold to open the switch during charging | 9**.**2 | RW | 51 |
| **i-charge-nominal** | A | float | Nominal charge current \(informative only\) | 4.6 | RW | 52 |
| **i-out-max** | A | float | Maximum current threshold to open the switch during normal operation, if not overruled | 60 | RW | 53 |
| **i-peak-max** | A | float | Maximum peak current threshold to open the switch during normal operation, can't be overruled | 200 | RW | 54 |
| **i-out-nominal** | A | float | Nominal discharge current \(informative only\) | 60 | RW | 55 |
| **i-flight-mode** | A | float | Current threshold to not disable the power in flight mode | 5 | RW | 56 |
| **v-cell-margin** | mV | uint8\_t | Cell voltage charge margin to decide or not to go through another topping charge cycle | 50 | RW | 57 |
| **v-recharge-margin** | mV | uint16\_t | Cell voltage charge complete margin to decide or not to do a battery re-charge, to keep the cell voltages at max this much difference with the cell-ov | 200 | RW | 58 |
| **t-ocv-cyclic0** | s | int32\_t | OCV measurement cyclic timer start \(timer is increase by 50% at each cycle\) | 300 | RW | 59 |
| **t-ocv-cyclic1** | s | int32\_t | OCV measurement cyclic timer final value \(limit\) | 86400 | RW | 60 |
| **c-pcb-ut** | C | float | PCB Ambient temperature under temperature threshold | -20 | RW | 61 |
| **c-pcb-ot** | C | float | PCB Ambient temperature over temperature threshold | 45 | RW | 62 |
| **v-storage** | V | float | The voltage what is specified as storage voltage for a cell | 3.8 | RW | 63 |
| **ocv-slope** | mV/A.min | float | The slope of the OCV curve. This will be used to calculate the balance time | 5.3 | RW | 64 |
| **batt-eol** | % | uint8\_t | Percentage at which the battery is end-of-life and shouldn’t be used anymore Typically between 90%-50% | 80 | RW | 65 |
| **battery-type** | - | uint8\_t | The type of battery attached to it. 0 = LiPo, 1 = LiFePo4, 2 = LiFeYPo4. Could be extended. Will change OV, UV, v-storage, OCV/SoC table if changed runtime | 0 | RW | 66 |
| **sensor-enable** | - | bool | This variable is used to enable or disable the battery temperature sensor, 0 is disabled, 1 is enabled | 0 | RW | 67 |
| **self-discharge-enable** | - | bool | This variable is used to enable or disable the SELF\_DISCHARGE state, 0 is disabled, 1 is enabled | 1 | RW | 68 |
| **flight-mode-enable** | - | bool | This variable is used to enable or disable flight mode, is used together with i-flight-mode | 0 | RW | 69 |
| **emergency-button-enable** | - | bool | This variable is used to enable or disable the emergency button on PTE8 | 0 | RW | 70 |
| **smbus-enable** | - | bool | This variable is used to enable or disable the SMBus update | 0 | RW | 71 |
| **uavcan\_node\_static\_id\*** | - | uint8\_t | This is the node ID of the UAVCAN message | 255 | RW | 72 |
| **uavcan-es-sub-id\*** | - | uint16\_t | This is the subject ID of the energy source UAVCAN message \(1...100Hz\) | 4096 | RW | 73 |
| **uavcan-bs-sub-id\*** | - | uint16\_t | This is the subject ID of the battery status UAVCAN message \(1Hz\) | 4097 | RW | 74 |
| **uavcan-bp-sub-id\*** | - | uint16\_t | This is the subject ID of the battery parameters UAVCAN message \(0.2Hz\) | 4098 | RW | 75 |
| **uavcan-legacy-bi-sub-id\*** | - | uint16\_t | This is the subject ID of the battery info legacy UAVCAN message \(0.2 ~ 1Hz\) | 65535 | RW | 76 |
| **uavcan-fd-mode\*** | - | uint8\_t | If true CANFD is used, otherwise classic CAN is used | 0 | RW | 77 |
| **uavcan-bitrate\*** | bit/s | int32\_t | The bitrate of classical can or CAN FD arbitration bitrate | 1000000 | RW | 78 |
| **uavcan-fd-bitrate\*** | bit/s | int32\_t | The bitrate of CAN FD data bitrate | 4000000 | RW | 79 |

A ~~line~~ means this is not implemented yet.  
\*these parameters will only be implemented during startup of the BMS

##  BMS hardware parameters list

| **Parameter** | **Unit** | **Datatype** | **Description** | **Default** | **RO/RW** | **No** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **v-min** | V | uint8\_t | Minimum stack voltage for the BMS board to be fully functional | 6 | RW | 80 |
| **v-max** | V | uint8\_t | Maximum stack voltage allowed by the BMS board | 26 | RW | 81 |
| **i-range-max** | A | uint16\_t | Maximum current that can be measured by the BMS board | 300 | RW | 82 |
| **i-max** | A | uint8\_t | Maximum DC current allowed in the BMS board \(limited by power dissipation in the MOSFETs\) | 60 | RW | 83 |
| **i-short** | A | uint16\_t | short circuit current threshold \(typical: 550A, min: 500A, max: 600A\) | 500 | RW | 84 |
| **t-short** | us | uint8\_t | Blanking time for the short circuit detection | 20 | RW | 85 |
| **i-bal** | mA | uint8\_t | Cell balancing current under 4.2V with cell balancing resistors of 82 ohms | 50 | RW | 86 |
| **m-mass** | kg | float | The total mass of the \(smart\) battery | 0 | RW | 87 |



