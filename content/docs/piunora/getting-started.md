---
title: "Getting started"
weight: 2
---

## Before we dive in, the most important bits to remember:

- The Compute Module 4/5 is in all relevant aspects identical to a Raspberry Pi 4/5 when it comes to software. What works on a Pi4/5 work on a CM4/5.
- Things like the camera connector work identical to a big Pi. If a camera does not work on Piunora but does work on a big Pi then it is likely a missing device tree overlay.
- These days the stock OS image has good defaults, checkout our config.txt for setting up SPI and other relevant ports **[reference config.txt](https://github.com/Diodes-Delight/piunora-raspberrypi-os-image/blob/main/scripts/files/config.txt)**.
- We strongly recommend using a model with WiFi. Because the CM4 only had a single USB port it gets tricky to get connected if you have to use a USB Ethernet or WiFi dongle.

**If you have any questions please don't hesitate to reach out to us on [Discord!](https://www.diodes-delight.com/community/)**

## Getting started

Download the latest Raspberry Pi OS image. Things work out of the box these days of Compute Modules.

Use the Raspberry Pi Imager to flash and download the OS image. You can download it here
 - [Download for Windows](https://downloads.raspberrypi.org/imager/imager_latest.exe)
 - [Download for Mac](https://downloads.raspberrypi.org/imager/imager_latest.dmg)
 - [Download for Ubuntu (.deb)](https://downloads.raspberrypi.org/imager/imager_latest_amd64.deb) or `sudo apt install rpi-imager` (possibly a bit outdated)

Before flashing the image we recommend checking out the **advanced settings tab** which can be opened with the key combination **Ctrl+Shift+X**. This will open a little window where you can **set your WiFi credentials** and **enable SSH + set a new password**.

If you have a CM4 model with **eMMC**, please check out the instructions below. Flashing works largely the same but you can not use an SD card at all on eMMC models, **the SDcard interface is not present on eMMC models.**

Here are some relevant [config.txt](https://www.raspberrypi.com/documentation/computers/config_txt.html) settings you may want to apply after flashing.

```
#Already there in latest OS versions but just to be sure, this enables USB.
dtoverlay=dwc2

#Setup SPI5 for using the MCP3008 ADC from Python.
dtoverlay=spi5-1cs,cs0_pin=24

#Enable UART on Pin 4 and 5
dtoverlay=uart3

#Enable default I2C1 for QWIIC/STEMMA QT
dtparam=i2c_arm=on

#Enable default SPI0
dtparam=spi=on

#Disable Bluetooth
dtoverlay=disable-bt
```

(In the past we offered a customized OS image as many things were not setup right for the Compute Module. This has changed and this image is **deprecated** but you can still [download it here](https://github.com/Diodes-Delight/piunora-raspberrypi-os-image/releases))


### For eMMC models only

If you are using an eMMC module you can checkout the official Raspberry Pi [docs for flashing CM4 modules with eMMC](https://www.raspberrypi.com/documentation/computers/compute-module.html#flash-compute-module-emmc).

Note that any instructions specific to setting USB boot on a CM4IO/CM5IO board in the official Raspberry Pi guide do not apply to Piunora, instead follow the sequence below to enter USB boot mode. Otherwise you can fully follow the Raspberry Pi guide.

The **USB switch** (near the USB-C connector) must be set in the **DEVICE** position.
The Device position is the one closer towards the small Qwiic connector. The default position is Host which is facing away from the Qwiic connector towards the USB cable (the Host setting switches the USB over to the USB-A port)

![usb switch set to device](/docs/piunora/pic/usb-switch-device.jpg)

Now run the `rpiboot` binary, it will start to search for attached CM devices.

![rpiboot running](/docs/piunora/pic/rpiboot.png)

Holding down the USB boot button while attaching the USB-C cable will enable USB boot. This button is connected to both GPIO25 and the nRPI_BOOT signal for USB boot. Physically it is located on the top left behind the HDMI connector.

![USB BOOT button](/docs/piunora/pic/usb-boot-25.jpg)

You do not need to keep holding it down after attaching the USB cable, it just needs to be pressed during power up.

After a few seconds you should see the USB device disconnect and come back as a Mass Storage Device.
The `rpiboot` utility will automatically close/exit.

USB hubs sometimes can give you issues when the `rpiboot` utility tries to send the boot code. If you experience the tool going in a loop forever trying to send something, try a USB port that is directly connected to your computer or a different USB hub.
It may look something like this. Spewing errors of failed control transfers.

![rpiboot error](/docs/piunora/pic/rpiboot-error-w-hub.png)

Thats it, you can check out the [FAQ](/docs/faq) for some common questions next.