# Board features

The RDDRONE-BMS772 integrates the following functions and features:&#x20;

* LiPo Battery from 3s to 6s, with stack voltage ranging from 6V to 26V&#x20;
* ambient temperature range from -20°C to 60°C&#x20;
* measures battery stack and cell voltages with an accuracy of +/-5mV, battery charge or discharge current up to 200A peak and 90A\* DC with an accuracy of 1% for the complete chain and cell temperature with an accuracy of +/- 2°C (including AFE, PCB and NTC inaccuracies)&#x20;
* active cell balancing during charging&#x20;
* offers a deep sleep mode (for transportation and storage) with <80μA leakage current, as well as an automatic sleep mode with <200μA current consumption on the battery.&#x20;
* allows authentication of the battery&#x20;
* allows diagnostics to verify the safe operation of the battery&#x20;
* allows CAN, I²C and NFC communication&#x20;
* implements SWD and JTAG debugging interfaces, works with standard Segger J-Link and other debuggers&#x20;
* implements DCD-LZ combined debug and uart console interface for use with PX4 DroneCode and HoverGames platforms

_**Note**: The 90A DC maximum current is obtained only when all MOSFETs and heatsinks are mounted. See_ [_Power MOSFETs and heatsinks_](../getting-started-with-the-rddrone-bms772/configuring-the-hardware.md#power-mosfets-and-heatsinks).

