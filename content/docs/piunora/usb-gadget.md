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

### macOS

macOS 10.12 (Sierra) and later should have all the drivers you need built in. Simply attatching Piunora via the USB-C port should get it installed.

#### Serial

To connect via serial with an application like `screen`, simply use the name of the tty device that macOS added when you plugged it in.

In this case, it was added with the name `tty.usbmodem1103`:

![macOS ls /dev/tty.*](/docs/piunora/macos-ls-dev.png)

So running the command `screen /dev/tty.usbmodem1103` gets you connected:

![macOS connected to Piunora via screen](/docs/piunora/macos-screen.png)

#### RNDIS

Recent versions of macOS should automatically have a RNDIS driver. However, you'll need to configure the adapter that the USB connection presents.

##### macOS 10.11 (El Capitan) and Earlier

macOS didn't include a RNDIS driver until 10.12. For earlier versions (10.6.8 and later), a third party driver is available called [HoRNDIS](https://joshuawise.com/horndis) (pronounced: _"horrendous"_). This is a software package designed to support Android tethering, but it will likely work for our purposes as well. **N.B.**: This is as of yet untested.

##### Network Configuration

After you've attached Piunora to your Mac and allowed it time to boot up, open the `Network` panel in system preferences.

You can get there by pressing `⌘+Space` and typing `Network`, making sure the system preferences network option is selected, then pressing return.

![macOS spotlight showing network](/docs/piunora/macos-spotlight-network.png)

If there is an entry in the list on the left named `RNDIS/Ethernet Gadget` with an amber orb to its left, you're ready to go.

_Screenshot Here_

If not, you'll need to add the adapter. Click the `+` in the lower left. In the dialog that appears, change the `Interface` to `RNDIS/Ethernet Gadget`, then click `Create`.

_Screenshot Here_

Once it adds, if the orb to it's left turns amber, you should be ready to connect via SSH as `pi@raspberrpi.local`. If not, first connect via serial and check what IP the Pi (run `ifconfig`, and look at `inet` under `usb0`) has given itself and connect to that instead.

##### Internet Connection Sharing

**N.B.**: This is untested, but based on the information from [here](https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/ethernet-gadget#if-you-are-using-a-mac-as-the-host-computer-2570560-24) and [here](https://gist.github.com/superdodd/06b91ba03899e47beb43078b27dc601e).

If you want to share your Mac's internet connection with your Piunora, you'll need to do a little more configuration. First, while connected (via serial or ssh) to your Piunora, you'll want to configure a static IP address for the Pi to use.

From the terminal, open the file named `/etc/dhcpcd.conf` in your editor of choice.

Add the following lines to the bottom of that file:

```
interface usb0
static ip_address=192.168.2.2/24
static routers=192.168.2.1
static domain_name_servers=192.168.2.1
```

Write and close that file.

Now, back on your Mac, navigate back to the Network preferences panel. Select your `RNDIS/Ethernet Gadget` adapter

Change the `Configure IPv4` drop-down to `Manually`. Assign it the IP address `192.168.2.1`, with the subnet mask `255.255.255.0` and router set to `192.168.2.1`.

_Screenshot Here_

Next, click `Advanced`, On the `DNS` tab, add one or more IP addresses for the DNS server(s) you want to use. You can likely use the IP of your home gateway, or you can use something like: `1.1.1.1`, `1.0.0.1` (provided by Cloudflare), `8.8.8.8`, `8.8.4.4` (provided by Google).

_Screenshot Here_

Save those changes, then navigate to the `Sharing` section of the `System Preferences` app. (Press the `<` and then click the `Sharing` icon.)

Tick the box next to `Internet Sharing`, choose the connection you want to share, and tick the box next to your `RNDIS/Ethernet Gadget` interface.

_Screenshot Here_

Reboot your Pi, and it should be able to access the internet via your Mac!

If it doesn't seem to be working, some suggest adding an additional configuration on the Pi. As root, edit `/etc/modprobe.d/g_ether.conf`, and add the line `options g_ether use_eem`. Reboot the Pi.