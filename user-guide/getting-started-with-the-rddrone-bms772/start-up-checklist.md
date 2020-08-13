# Start-up checklist

## First start-up

Before first start-up, make sure the board is configured properly:

{% hint style="danger" %}
The board MUST be configured, connectors and solder jumpers need to be soldered and installed to match your exact battery cell count
{% endhint %}

1. Solder your power in and power out connectors or wires on the J4 and J5 footprints
2. Solder the correct cell terminal connector at the JP1 location. Ensure it is correctly positioned and aligned
3. Configure the board for your application by soldering the corresponding SJxx connectors
4. Configure the board with additional and/or optional components as described in [Configuring the hardware](configuring-the-hardware.md) to fit the application requirements

## Powering the RDDRONE-BMS772 board on and off

Once the board is configured properly \(see [Configuring the hardware](configuring-the-hardware.md) for more details about configuration\), it is time to connect the board. 

To power on the RDDRONE-BMS772 board, \***first**\* connect the battery to the power input connector \(J4\) and **then** the cell terminal connector \(JP1\). This protects the boards form internal damage due to hot plugging.

Similarly, to disconnect the battery from the board, the cell terminal connector \(JP1\) should be disconnected first. Then the power input \(J4\) can be disconnected.



