---
title: "Using Qwiic/Stemma QT (I2C)"
weight: 4
---

Piunora comes equipped with a Stemma QT / Qwiic connector which is a standard originally coined by Sparkfun to easily connect I2C devices with a standardized cable and connector.
Adafruit sells compatible products under the brand Stemma QT.

![Qwiic Connector](/docs/piunora/qwiic_piunora.jpg)

The connector on Piunora is connected to I2C-1 which is also the default I2C port in Blinka.
So you can access the I2C port in blinka with the `board.SDA` and `board.SCL` (given you have `import board`).

Almost if not all Blinka/CircuitPython code examples for Qwiic or Stemma QT devices should just work as is.

Here an example for interfacing with the [Adafruit VCNL4040](https://www.adafruit.com/product/4161) proximity and lux sensor and letting it do virtual key presses.
You may need to install the python [keyboard library](https://pypi.org/project/keyboard/) with `pip install keyboard`

```
import math
import time
import board
import busio
import adafruit_vcnl4040
import neopixel
import simpleio
import keyboard

pixels = neopixel.NeoPixel(board.D12, 1, brightness=0.2)
i2c = busio.I2C(board.SCL, board.SDA)
sensor = adafruit_vcnl4040.VCNL4040(i2c)

while True:
	print("Proximity:", sensor.proximity)
	pixels.fill((0, math.floor(simpleio.map_range(sensor.proximity,3,200,0,255)), 0))

	if sensor.proximity > 6:
		keyboard.press('space')
		pass
	else:
		keyboard.release('space')
```
