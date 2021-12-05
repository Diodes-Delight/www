---
title: "USB Switch"
weight: 2
---

Piunora comes with a special feature when it comes to USB.
You can find a small slide switch next to the USB-C port. With this switch you can put Piunora either into USB **Host** mode, which means you want to connect things like a Keyboard or a USB Stick *to* Piunora via the **USB-A port**.
Or you can put it into the USB **Device** mode which will switch the USB over to the **USB-C port**.
In this mode you can use Piunora as a USB device and connect it to your computer.

**You can switch back and forth between Host and Device mode any time, no need to reboot!**

**Though this also means the USB-C and USB-A port are mutually exclusive! You can not use both at once because the CM4 only comes with a single native USB port.**

Our OS image comes with the so called USB Gadget mode enabled in the `multi_gadget` mode.
This enables USB Ethernet, USB Serial and USB Mass Storage all at once. You may notice a "USB Stick" called Piunora pop up when you power it directly via your computer.
For more details on that check out the USB Gadget Mode article.

In order to power it from your computer you should at least use a USB port capable of delivering **900mA** of current. Better even to use a USB-C PD capable port which can supply up to 3A! Many laptops and modern PC motherboards will offer such a port.

![USB Switch](/docs/piunora/usb-switch.jpg)