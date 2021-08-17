# Charging with the BMS

The BMS is not able to limit the current. It can only disconnect the battery from the output. For charging make sure a current limited power source is used and set the limitation to the right value.   
The BMS is not able to limit the voltage. For charging, the charge voltage should be limited as well.

{% hint style="info" %}
The standard balancing current is only 50mA for one cell.   
This means it could take some time before balancing is done if the battery pack very unbalanced. 
{% endhint %}

To get more information about the charging process see CHARGE state on the [BMS application state machine](bms-application-state-machine.md) page.

