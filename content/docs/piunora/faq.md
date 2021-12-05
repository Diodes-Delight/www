---
title: "Frequently-Asked Questions"
weight: 3
---

**Which SSDs will work with Piunora?**

We recommend the SN520 from Western Digital and SanDisk. (It's sold under both
brands.) M.2 is not universal. It comes in different so called "keys" that
specify the application. Every **NVME** 2242/2230 **B+M Key** SSD should work
just fine. (They have two notches and are compatible with both B- and M-Keys.)
**M.2 M-Key-only SSDs will not work** because Piunora uses the **M.2 B-Key**.
Piunora is not designed for NAS applications so there was no focus on large SSD storage.

**Are SATA-based SSDs supported?**

There is no SATA chipset on Piunora, so no S-ATA SSDs can be used. There are M.2 PCI-e to S-ATA boards out there though if you want to support S-ATA based storage but it will not be a compact solution by any means.

**Can I use the SD-card connector with CM4 modules that have eMMC?** 

Unfortunately, no. This is a hardware limitation of the CM4. There is a single
SDIO interface available and that interface is only available to be used on the
"Lite" modules. On modules with eMMC, this interface is used up by the eMMC
chip. (The connector pins that normally carry the SDIO interface are simply not
connected to anything.)

**So what M.2 sizes does Piunora support?**

Piunora supports 2230 and 2242 as well as 3042 and 3030. So called "thick"
modules also work. (There are no components under the M.2 area.) The *Piunora
M.2 B-Key 2280 Expander* allows you to use 2280 and 2260 devices, but they will
extend beyond Piunora itself, so keep that in mind if you want to retain the
form factor.

**What does 2242 or 2280 mean in regard to M.2?**

That's the size of the card. 2242 means 22x42 mm, and 2280 means 22x80 mm.


**Can I power Piunora from the pin headers?**

Yes! That is totally possible. I recommend that you use both available 5 V pins
when doing so. Also, if you do that, you should not use the USB Type-C input at
the same time. (You don't want to back power the host device.) You can still use
the USB Type-C for data if you cut the VBUS line from your USB Type-C cable (GND
should still be connected) or if you use a product like the [Power
BLough-R](https://www.th3dstudio.com/product/power-blough-r-pi-usb-power-blocker/).
with your computer.

**Can I boot from an NVME SSD?**

Yes! [This is now
possible](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bootmodes/nvme.md),
though it's still in beta and has a few issues like some users have trouble rebooting from within Linux.

**Why did you go with an M.2 B-Key instead of an M-Key?**

M-Key is intended specifically for SSDs. While many Piunora users will be
interested in SSDs, there are a lot of B-Key modules in the 2242 form factor.
Most 2230 and 2242 devices are designed for either B-Key or B+M Key.
The majority of M-Key devices are 2280 or larger. Furthermore, most 2242
SSDs come as B+M-Key, which means they're compatible with *both* form factors
and should work just fine with Piunora. So, using a B-Key supports more add-on
cards while still accommodating most NVME SSDs.

**I'm confused by the USB setup. How many USB ports does Piunora have? And can I
use them all at once?**

Unfortunately, the CM4 has only a single USB port, which can act *either* as a
USB host *or* as a USB device. They are mutually exclusive, which is why we
added a switch so you can toggle between host mode and device mode. When the
switch is set to host mode, a USB multiplexer is routing the USB bus to the USB
Type-A connector. When the switch is set to device mode, the USB bus is routed
to the USB Type-C connector.

**How does the M.2 port play into the whole USB thing? I thought it was PCI-e?**

Apart from PCI-e, M.2 can host a lot of different peripherals. That includes
USB, SATA, I²C, SPI, and many others. It's up to the host device to decide what
it wants to implement. (Only PCI-e is mandatory.)

When you bridge the solder jumpers for the USB lines to the M.2 ports, you are
bridging the USB data lines of the USB Type-A port to the M.2 port. You still
retain the ability to switch to device mode, but you have to be careful when
using the USB Type-A port. It's a trade off: you can not use the USB Type-A port
while using USB on the M.2 port.

This hack also creates a so called "stub" (a
piece of conductor that is not part of the signal pathway) which might cause
unwanted signal reflections, so please keep this in mind if you plan to use a
High-Speed USB device after bridging these pads. While there is no guarantee that
it will work flawlessly in all situations, it's usually not a problem in
practice (at least not over short distances).

**I see a SIM card footprint on the back, is it usable if I solder the connector?**

Yes! It was added for people willing to hack around with their Piunora.
The connector used is the [HOAUC HYC244-SIM07-140](https://lcsc.com/product-detail/SIM-Card-Connectors_HOAUC-HYC244-SIM07-140_C645502.html).
Other connectors might be compatible to this footprint.

You can then use the SIM card with WWAN (LTE, 5G etc.) modules. Though keep in mind that almost all LTE modules use USB rather than PCI-e so you will also have to bridge the M.2 USB solder jumper (you can't use USB on M.2 and the USB-A port at the same time, you bridged them physically)