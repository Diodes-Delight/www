---
title: "USB Gadget"
weight: 2
---

## Overview

The Piunora OS distribution comes with the USB gadget mode pre-configured.
When the USB Switch is in the `device` position and you have it connected via the USB-C connector to a computer or laptop you should see a Piunora "USB Stick" or so called Mass Storage Device pop up during boot up. There will also be a USB Serial device and a "USB RNDIS" device, the latter is essentially USB Ethernet.

Right now the USB Mass Storage is a bit useless, its mostly there for testing purposes. In the very near future though you will able to place code files onto that USB storage and it will automatically transfer your files to the Linux filesystem for you so you can easily work on code with your favorite editor on your host computer without SFTP.

You can connect to your Piunora easily via serial, just open the tty / COM device with a terminal app like `screen` on Linux or Mac OS or `putty` on Windows. Typical baudrate is `115200` but the Pi should auto-detect the baudrate.
If you are using a version of Windows before Windows 10 you might need to install generic Serial device drivers. We currently only support Windows 10 and up.

For the RNDIS Ethernet device you should not need to setup drivers for Linux or Mac.
You should usually be able to connect via ssh to `pi@raspberrpi.local`
If not, first connect via serial and check what IP the Pi has given itself and connect to that instead.

## Platform Specific

### Windows

#### Serial

Windows 10 and later has drivers for the USB Serial device built-in. It should assign Piunora a COM port automatically.

You can find the name of the port by opening the `Device Manager` by right clicking on the Start Menu button.

![Windows device manager in the start menu](/docs/piunora/start-menu-device-manager.png)

Then, expand the `Ports (COM & LPT)` section and look for an entry that starts with `USB Serial Device`. The name in parenthesis is the port name you will use to connect to.

![Device Manager Ports](/docs/piunora/device-manager-ports.png)

#### RNDIS

On Windows you will need to install the Microsoft "USB RNDIS Adapter" driver.

To do this first open up the `Device Manager` by right clicking on the Start Menu button.

![Windows device manager in the start menu](/docs/piunora/start-menu-device-manager.png)

Then under `Networking Adapters` look for a device called RNDIS or USB RNDIS. It will probably have a yellow warning triangle.
Right click the device and choose `Update driver`

![Windows device manager showing the RNDIS device](/docs/piunora/device-manager-rndis.png)

Next choose to select a driver from your computer.

![Windows selecting a local driver](/docs/piunora/select-local-driver.png)

Then choose to select a driver from a list of available drivers.

![Windows picking a driver from a list](/docs/piunora/pick-driver-from-list.png)

In that window scroll down in the list of Manufacturers and select `Microsoft` then scroll in the Model list until you find the `USB RNDIS Adapter`. Exactly this device, not other devices with RNDIS in their name.

Accept by clicking on `Next.

![Windows USB Networking Adapter](/docs/piunora/usb-networking-adapter.png)

After the driver is installed you should get a new Ethernet device in your Networking Adapter list.
It might take a bit until Windows identified the Network. Once its done you should usually be able to connect via ssh to `pi@raspberrpi.local` (or whatever hostname you gave it when you flashed your OS image.)
If not, first connect via serial and check what IP the Pi (run `ifconfig`, and look at `inet` under `usb0`) has given itself and connect to that instead.

![Windows Network showing Identifying](/docs/piunora/windows-network-intentifying.png)
