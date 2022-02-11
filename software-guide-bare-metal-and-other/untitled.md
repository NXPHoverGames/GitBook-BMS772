# Battery Cell Controller (BCC) drivers

The MC33772B Battery Cell Controller (BCC) comes with a SW package. This package contains embedded SDK SW driver for NXP’s Battery Cell Controller products and example projects for S32K144 MCU and S32 Design Studio for Arm Version 2018.R1. It exists in a Lite and a Full version:

* The Lite version is implemented and used in the NUTTX-PX4 software. It allows controlling the BCC and performing its main tasks, as: measuring Cell Terminal (CT) voltages, current, temperatures, analog inputs, etc.. It is available on [NXP.com](https://www.nxp.com/design/analog-expert-software-and-tools/sdk-analog-expert-drivers/embedded-sw-battery-cell-controller-software-driver-for-mc33771b-mc33772b:EMBEDDED-SW-BCC)
* The Full version complements the Lite version by adding diagnostics and safety to it. This package can be useful for users wanting to add a safety layer on their applications. It is available under NDA on [Docstore](https://www.docstore.nxp.com/products?path=/content/docstore/product-hierarchy/Automotive-Battery-Management/MC33771--MC33772--MC33664\&folderuuid=10722735-c3a3-47dd-a794-8eec20db8c66)

