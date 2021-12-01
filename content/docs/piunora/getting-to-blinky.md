---
title: "Getting to Blinky with Blinka (Python)"
weight: 3
---

### This guide assumes that you have followed the Getting Started site and are using our modified Raspberry Pi OS.

Our OS image comes pre-installed with [Adafruit Blinka](https://learn.adafruit.com/circuitpython-on-raspberrypi-linux). A compatibility layer for [CircuitPython](https://circuitpython.org/) for Linux computers.
You can run almost any CircuitPython code directly on Piunora that way.

We have pre-installed all CircuitPython libraries available for Blinka as of the date where the OS image was released.
So you don't need to worry to install the right things, they are already there!

For code examples to talk to the Analog to Digital converter, buttons and RGB LED please see the `~/piunora-blinka-examples` directory.
They can be a starting point for your applications.

Unlike CircuitPython we are running full blown Python here, so you can use any other Python libraries that you normally use on a computer like numpy or tensorflow!
Or just integrate the hardware bits into your existing Python code. Blinka works just like any other Python library.

To learn more about Blinka check-out [Adafruits guide](https://learn.adafruit.com/circuitpython-on-raspberrypi-linux)

Also checkout the [CircuitPython documentation](https://circuitpython.readthedocs.io/en/latest/shared-bindings/index.html#modules) and the [list of available hardware drivers and libraries](https://github.com/adafruit/Adafruit_CircuitPython_Bundle/blob/main/circuitpython_library_list.md) that we pre-installed for you.

Anything with a PyPi link is available via Blinka and pre-installed if it was released before you installed our OS release.
If you wish to update all of the libraries checkout our [install script](https://github.com/Diodes-Delight/piunora-raspberrypi-os-image/blob/main/scripts/files/install_all_cpy_libraries.py) that we use in the creation of our OS image.

[Adafruit](https://www.adafruit.com/) creates and maintains CircuitPython. Please support them, if you are looking for hardware to use with your Piunora, like f.e. easy to use, solder free [Stemma QT addons](https://www.adafruit.com/category/620) that connect via the I2C [Qwiic/Stemma QT connector](https://www.adafruit.com/category/619) on your Piunora.