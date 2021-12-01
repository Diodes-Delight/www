---
title: "Getting started"
weight: 2
---

## Before we dive in, the most important bits to remember:


- The Compute Module 4 is in all relevant aspects identical to a Raspberry Pi 4 when it comes to software. What works on a Pi4 work on a CM4.
- USB is disabled by default in the vanilla Raspberry Pi OS and needs to be enabled in `/boot/config.txt`. You don't need to do this with our modified OS image. Our reference `config.txt` can be found **[here](https://github.com/Diodes-Delight/piunora-raspberrypi-os-image/blob/main/scripts/files/config.txt)**

**NOTE: We are still working on documentation and it will be expanded a lot over the coming days and week, sorry for the delay here. If you have any questions please don't hesitate to reach out to us on [Discord!](https://www.diodes-delight.com/community/)**

## Getting started the quick way

We prepared a customized version of Raspberry Pi OS that has everything installed and configured for Piunora and electronics prototyping.

**[Download latest Piunora Raspberry Pi OS Desktop image](https://github.com/Diodes-Delight/piunora-raspberrypi-os-image/releases)**

**Default user: `pi`**

**Default password: `raspberry`**

It is based on the latest "Raspberry Pi OS (32 bit) with Desktop". It behaves just the same way and has the same "first boot" experience with all the dialogs to get you setup if you are new to the Pi.

We highly recommend using the **Raspberry Pi Imager to flash you image**. You can download it here
 - [Download for Windows](https://downloads.raspberrypi.org/imager/imager_latest.exe)
 - [Download for Mac](https://downloads.raspberrypi.org/imager/imager_latest.dmg)
 - [Download for Ubuntu (.deb)](https://downloads.raspberrypi.org/imager/imager_latest_amd64.deb) or `sudo apt install rpi-imager`

Before flashing the image we recommend checking out the **advanced settings tab** which can be opened with the key combination **Ctrl+Shift+X**. This will open a little window where you can **set your WiFi credentials** and **enable SSH**. We highly recommend setting at least these two things up so you can access you CM4 via SSH! We chose to not enable SSH by default for the same reason as Raspberry Pi, SSH enabled with a default password is dangerous.
You can also change the default password and other useful things.

![Pi Imager](/docs/piunora/pi-imager.png)

### For eMMC models

If you are using an eMMC module follow the Raspberry Pi docs **[here](https://www.raspberrypi.com/documentation/computers/compute-module.html#steps-to-flash-the-emmc)**. Holding down the USB boot button while attaching the USB cable will enable USB boot for this purpose. You do not need to keep holding it down after attaching the USB cable, it just needs to be pressed during power up.


### Using an existing Raspberry Pi SD Card or vanilla Raspberry Pi OS

You can of course boot any OS you like!
The only thing you probably wanna do at very least is copy our Piunora/CM4 specific `config.txt`. You can find the latest version **[here](https://github.com/Diodes-Delight/piunora-raspberrypi-os-image/blob/main/scripts/files/config.txt)**.

This is enables things like extra SPI ports needed for ADC, enables USB and other things necessary to interface with hardware.
You can just copy the Piunora section, you don't have to overwrite your whole config.txt if you don't want to. Just make sure you don't disable anything again by accident.

For a comprehensive overview of what we install for Piunora you can check out the repository for the automated image build process.

https://github.com/Diodes-Delight/piunora-raspberrypi-os-image/tree/main/scripts

It contains all the shell scripts for all the features we add. You can run them manually on your installation but no guarantee it will work fine, it is only tested against the latest version of Raspberry Pi OS (Debian based).
