---
title: "RGB LED"
weight: 6
---

Piunora comes with a **WS2812** (aka Neopixel) LED for you to use in your application.

The LED is connected to **GPIO12**. See our Blinka example located in the home folder to use the LED.

Or check the examples out [here in git](https://github.com/Diodes-Delight/piunora-raspberrypi-os-image/tree/main/scripts/files/piunora-blinka-examples).

Please be aware that this uses the PWM0 peripheral (also available on GPIO18), so if you use PWM audio this will be in conflict.

If you prefer C over Python you can also use [rpi_ws281x](https://github.com/jgarff/rpi_ws281x) directly which is the underlying library for the Python library.