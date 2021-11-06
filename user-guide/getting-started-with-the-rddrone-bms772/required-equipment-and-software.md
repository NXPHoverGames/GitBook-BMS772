# Required equipment and software

To use this BMS772  kit, you will need:&#x20;

### Additional items needed

* LiPo battery pack&#x20;
  * 3S to 6S with cell balancing connector - Voltage range of 6V to 26V
* Suitable charger for the type of battery
* Soldering iron to configure the board
* External Thermistor temperature sensor with cable and JST-GH 2-pin connector (optional)
* Debugger:&#x20;
  * Segger J-Link Mini debugger
  * PEMicro universal multilink&#x20;
  * or other suitable JTAG/SWD debugger&#x20;

{% hint style="success" %}
_**Note**:  The HoverGames Drone Kit (KIT-HGDRONEK66) and/or  FMU Kit (RDDRONE-FMUK66) both include a **DCD-LZ adapter** and **Segger J-Link Mini EDU **and an **FTDI USBUART-3v3 **cable**. **_

_By using the DCD-LZ interface and **USBUART **cable you will also gain access to the command line interface (CLI) of the board._
{% endhint %}

### Software tools and sources

* S32 Design Studio for ARM-based MCUs (recommended)
* Alternatively : PX4 or NuttX build environment depending on what code source is used.&#x20;
* PX4/NuttX board target example code (optional, see Software guide)

_**Note**: The RDDRONE-BMS772 board allows to open the charge circuit when the battery is overcharging , to perform cell balancing and to monitor all cell voltages. Therefore the charger does not need to have a cell terminal connector._

