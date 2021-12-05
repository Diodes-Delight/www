---
title: "USB Gadget"
weight: 3
---

The Piunora OS distribution comes with the USB gadget mode pre-configured.
When the USB Switch is in the `device` position and you have it connected via the USB-C connector to a computer or laptop you should see a Piunora "USB Stick" or so called Mass Storage Device pop up during boot up. There will also be a USB Serial device and a "USB RNDIS" device, the latter is essentially USB Ethernet.

Right now the USB Mass Storage is a bit useless, its mostly there for testing purposes. In the very near future though you will able to place code files onto that USB storage and it will automatically transfer your files to the Linux filesystem for you so you can easily work on code with your favorite editor on your host computer without SFTP.

You can connect to your Piunora easily via serial, just open the tty / COM device with a terminal app like `screen` on Linux or Mac OS and `putty` on Windows. Typical baudrate is `115200` but the Pi should auto-detect the baudrate.
If you are using a version of Windows before Windows 10 you might need to install generic Serial device drivers. We currently only support Windows 10 and up.

For the RNDIS Ethernet device you should not need to setup drivers for Linux.
You should usually be able to connect via ssh to `pi@raspberrpi.local`
If not, first connect via serial and check what IP the Pi has given itself and connect to that instead.

On MacOS there seem to issues with the RNDIS driver. This is being looked into to support in the future but for now you have to stick to Serial on MacOS.

On Windows you will need to install the Microsoft "USB RNDIS Adapter" driver.

To do this first open up the `Device Manager` by right clicking on the Start Menu button.

![Start Menu](/docs/piunora/start-menu-device-manager.png)

Then under `Networking Adapters` look for a device called RNDIS or USB RNDIS. It will probably have a yellow warning triangle.
Right click the device and choose `Update driver`

![Start Menu](/docs/piunora/device-manager-rndis.png)

Next choose to select a driver from your computer.

![Start Menu](/docs/piunora/select-local-driver.png)

Then choose to select a driver from a list of available drivers.

![Start Menu](/docs/piunora/pick-driver-from-list.png)

In that window scroll down in the list of Manufacturers and select `Microsoft` then scroll in the Model list until you find the `USB RNDIS Adapter`. Exactly this device, not other devices with RNDIS in their name.

Accept by clicking on `Next.

![Start Menu](/docs/piunora/usb-networking-adapter.png)

After the driver is installed you should get a new Ethernet device in your Networking Adapter list.
It might take a bit until Windows identified the Network. Once its done you should usually be able to connect via ssh to `pi@raspberrpi.local`
If not, first connect via serial and check what IP the Pi has given itself and connect to that instead.

![Start Menu](/docs/piunora/windows-network-intentifying.png)
