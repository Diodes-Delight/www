---
title: "Removing 2230 M.2 Nut"
weight: 4
---

If you want to use a 42mm long device on the M.2 slot that has components on the bottom past the 2230 mark it is possible to unsolder the nut at the 2230 mark.

Before you attempt this please make sure the device you intend on using is actually a PCI-e device and is not reliant on S-ATA. We had customers before that wanted to do this because of an S-ATA SSD which is not compatible with Piunora. Those S-ATA SSDs are often double sided. 2240 NVME SSDs are usually not double sided.

Heat your iron to around 340°C / 640°F and insert the tip into the hole of the stand-off or wherever you have good and mechanically secure contact with the stand-off.

It will probably take some time but eventually you will see the solder around the stand-off start to melt, after that happens you can use tweezers or pliers to lift it off the board. It's best to keep the iron in contact while you lift it off but be careful to not burn yourself by slipping.

No force should be required.

![Placement of soldering iron and tweezers](/docs/piunora/unsolder-nut.jpg)

You can put the solder nut back with the same process, just feed in some solder onto the pad while you press it down to ensure there is enough wetting happening.

Alternatively you can replace it with a screw-in M.2 nut. Just make sure the head of the screw is flat (less than 1.5mm) to not make contact with the Compute Module.

