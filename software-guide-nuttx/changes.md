---
description: Changes relative to the last release (3.4-9.1)
---

# Changes

The changes relative to the last release, release 3.4-9.1, can be found in the table below.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Item</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Power on self-test</td>
      <td style="text-align:left">More components are tested at startup (NTAG5, A1007), with better output
        on terminal.</td>
    </tr>
    <tr>
      <td style="text-align:left">NuttX version</td>
      <td style="text-align:left">Upgraded to NuttX version 10.0 (stable release).</td>
    </tr>
    <tr>
      <td style="text-align:left">Sense resistor test</td>
      <td style="text-align:left">Added a test that will detect if the sense resistor is connected to the
        measurement input.</td>
    </tr>
    <tr>
      <td style="text-align:left">Negative input for unsigned variables</td>
      <td style="text-align:left">The CLI will notify you and will not set the variable when a negative
        number is entered for an unsigned variable.</td>
    </tr>
    <tr>
      <td style="text-align:left">self-test state</td>
      <td style="text-align:left">The self-test is only done at startup, made it a separate state (not only
        init state anymore).</td>
    </tr>
    <tr>
      <td style="text-align:left">LED color</td>
      <td style="text-align:left">LED is now solid red in the self-test state.</td>
    </tr>
    <tr>
      <td style="text-align:left">SoC calibration</td>
      <td style="text-align:left">Added the OCV state to calibrate the state of charge when in sleep mode.
        Added the SoC calibration to the self-discharge state.</td>
    </tr>
    <tr>
      <td style="text-align:left">CLI set parameter</td>
      <td style="text-align:left">Fixed that using the CLI, variables can&#x2019;t be set with more than
        its variable type can hold.</td>
    </tr>
    <tr>
      <td style="text-align:left">uv fault to deepsleep</td>
      <td style="text-align:left">Added that when an undervoltage occurs, it will go to the deepsleep mode
        after some time to protect the battery.</td>
    </tr>
    <tr>
      <td style="text-align:left">Reboot</td>
      <td style="text-align:left">Added the reboot command to the CLI to reboot the microcontroller.</td>
    </tr>
    <tr>
      <td style="text-align:left">Flight-mode</td>
      <td style="text-align:left">Added the flight-mode-enable and i-flight-mode parameters. This can be
        used to not cut the power to the FMU and motors in flight.</td>
    </tr>
    <tr>
      <td style="text-align:left">a-factory</td>
      <td style="text-align:left">After setting the factory capacity, the BMS will recalculate and set the
        full charge capacity and end of charge current as well.</td>
    </tr>
    <tr>
      <td style="text-align:left">Floating point variables</td>
      <td style="text-align:left">The floating point variables are better limited now.</td>
    </tr>
    <tr>
      <td style="text-align:left">Charge to deepsleep</td>
      <td style="text-align:left">Added that if the button is hold for five seconds in the charge state,
        it will go to deepsleep.</td>
    </tr>
    <tr>
      <td style="text-align:left">NFC</td>
      <td style="text-align:left">Is hard-powered down with GPIO.</td>
    </tr>
    <tr>
      <td style="text-align:left">Discharge to storage</td>
      <td style="text-align:left">After a long time-out, the BMS will discharge to storage level and go
        to the deepsleep state.</td>
    </tr>
    <tr>
      <td style="text-align:left">CLI syntax</td>
      <td style="text-align:left">Some wrong syntaxes are now fixed in the CLI.</td>
    </tr>
    <tr>
      <td style="text-align:left">CLI help messages</td>
      <td style="text-align:left">Improved the help message if the wrong number of cells are attached/inserted.</td>
    </tr>
    <tr>
      <td style="text-align:left">Wrong messages</td>
      <td style="text-align:left">
        <p>The wrong BMS undertemperature detected message if the sensor is disabled
          has been fixed.
          <br />
        </p>
        <p>The first &#x201C;pin rising edge BCC_FAULT&#x201D; message has been deleted.
          <br
          />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Message limit</td>
      <td style="text-align:left">Limited the number of &#x201C;Rising edge BCC_FAULT&#x201D; and &#x201C;clearing
        CC overflow&#x201D; messages.</td>
    </tr>
    <tr>
      <td style="text-align:left">CLI color messages</td>
      <td style="text-align:left">Added functions for the green (good), yellow (warning) and red (error)
        messages.</td>
    </tr>
    <tr>
      <td style="text-align:left">BCC com errors</td>
      <td style="text-align:left">This will not be reset (wrongly), but it will be counted and with 255
        errors it will reset it correctly.</td>
    </tr>
    <tr>
      <td style="text-align:left">UAVCAN</td>
      <td style="text-align:left">New message of the draft of the UAVCAN V1 standard message is implemented.</td>
    </tr>
    <tr>
      <td style="text-align:left">Data struct</td>
      <td style="text-align:left">
        <p>Added the unit and type string to the data struct.
          <br />
        </p>
        <p>Added floating point accuracy to the floating point limitations.
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Parameters</td>
      <td style="text-align:left">
        <p>Added the t-sleep-timeout, i-charge-nominal, i-out-nominal, i-flight-mode,
          battery-type, flight-mode-enable and m-mass.
          <br />
        </p>
        <p>Changed the model-id to uint64_t, t-fault-timeout to use with uv to go
          to the deepsleep state, t-ocv-cyclic0 and t-ocv-cyclic1 are implemented,
          changed the uavcan-subject-id to 3 different parameters for each message:
          uavcan-ess-sub-id, uavcan-bs-sub-id and uavcan-bp-sub-id.
          <br />
        </p>
        <p>v-cell-margin is default 50mV instead of 30mV. ocv-slope is in mV/Amin
          instead of V/Amin.
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">State diagram</td>
      <td style="text-align:left">Added LED indication, Added SELF TEST state, added button hold to the
        charge to self-discharge state transition, Added SLEEP_TIMEOUT to the sleep
        to self-discharge state transition, FAULT_TIMEOUT used for transition to
        go to deepsleep with an undervoltage.</td>
    </tr>
    <tr>
      <td style="text-align:left">Charge state diagram</td>
      <td style="text-align:left">Added LED indication and added button hold to the charge to self-discharge
        state transition.</td>
    </tr>
    <tr>
      <td style="text-align:left">Cell balancing</td>
      <td style="text-align:left">The cell balancing is not only based on the cell voltage compared to the
        desired voltage, but it is based on the calculated estimated cell balance
        minutes as well.</td>
    </tr>
  </tbody>
</table>

