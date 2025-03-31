---
title: "Analog to Digital Converter"
weight: 6
---

Piunora has an on-board analog to digital converter (ADC) so you can read analog voltages in f.e. Python (see the Getting to Blinky guide) and other programming languages.
It is connected via a dedicated SPI bus.

The ADC is a [MCP3008](https://ww1.microchip.com/downloads/aemDocuments/documents/MSLD/ProductDocuments/DataSheets/MCP3004-MCP3008-Data-Sheet-DS20001295.pdf) and is connected to the CM in the following way:

- SPI bus #5
- MOSI/DIN: GPIO14
- MISO/DOUT: GPIO13
- SCLK/CLK: GPIO15
- CS/SHDN: GPIO24


You can use the Blinka/Python example we provide (see Getting to Blinky guide) or use a different programming language. There are drivers for:
- [C/C++](https://gist.github.com/NSBum/7c395001af3235f6033641db5e34a882) (untested, you should probably talk to the Linux universal SPI driver instead)
- [JavaScript](https://github.com/fiskeben/mcp3008.js/)
- [Go](https://gobot.io/documentation/drivers/mcp3008/)
- [Rust](https://docs.rs/adc-mcp3008/0.1.1/adc_mcp3008/) (depends on [rpi_embedded](https://docs.rs/rpi_embedded/0.1.0/rpi_embedded/))

You can also use the built-in Linux IIO driver to use the ADC from within Kernel features.
https://github.com/torvalds/linux/blob/master/drivers/iio/adc/mcp320x.c

There are also many more options our there that are not covered here.