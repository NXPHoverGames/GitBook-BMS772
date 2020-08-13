# Board features

The RDDRONE-BMS772 integrates the following functions and features: 

* LiPo Battery from 3s to 6s, with stack voltage ranging from 6V to 26V 
* ambient temperature range from -20°C to 60°C 
* measures battery stack and cell voltages with an accuracy of +/-5mV, battery charge or discharge current up to 200A peak and 90A\* DC with an accuracy of 1% for the complete chain and cell temperature with an accuracy of +/- 2°C \(including AFE, PCB and NTC inaccuracies\) 
* active cell balancing during charging 
* offers a deep sleep mode \(for transportation and storage\) with &lt;80μA leakage current, as well as an automatic sleep mode with &lt;200μA current consumption on the battery. 
* allows authentication of the battery 
* allows diagnostics to verify the safe operation of the battery 
* allows CAN, I²C and NFC communication 
* implements SWD and JTAG debugging interfaces, works with standard Segger J-Link and other debuggers 
* implements DCD-LZ combined debug and uart console interface for use with PX4 DroneCode and HoverGames platforms

_**Note**: The 90A DC maximum current is obtained only when all MOSFETs and heatsinks are mounted. See_ [_Power MOSFETs and heatsinks_](../getting-started-with-the-rddrone-bms772/configuring-the-hardware.md#power-mosfets-and-heatsinks).



