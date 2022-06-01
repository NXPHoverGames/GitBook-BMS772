---
description: This page will give more information about the display
---

# Display

The display shows all kinds of battery information presented on an optional local I2C LCD display (e.g. SSD1306 type). The display should be connected to J23.&#x20;

Keep in mind that only 3.3V is supported. The display needs to be powered during NuttX startup in order to initialize it. In the current example the 5V regulator is off during startup and initialization and thus the display will not work with 5V.&#x20;

{% hint style="info" %}
Display support is only added for 3.3V supply. To enable 3.3V on the display connector J23, make sure **D34** is **placed** and **D35** is **not placed**! \
\
If the diode D35 is placed, move the diode placed on D35 and place it on D34.
{% endhint %}

There is a framebuffer which makes sure the data is transferred to the display. Information like SoC, SoH, output status, BMS mode, battery voltage, average current, temperature and ID can be seen on the display.
