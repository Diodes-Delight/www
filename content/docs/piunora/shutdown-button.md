---
title: "Shutdown Button"
weight: 4
---

If you are using Piunora with our modified OS then it comes with the shutdown button enabled.

If you press the button on the back of the board next to the SDCard connector (labeled "26" for GPIO26) for 5 seconds it will shutdown the CM4 safely. Once the green LED stopped blinking it is safe to unplug.

This behavior is done via a systemd service that you can also install it yourself with [this script](https://raw.githubusercontent.com/Diodes-Delight/piunora-raspberrypi-os-image/main/scripts/files/install-pwr-off.sh).

If you wish to modify the seconds needed to press the button then change the `button.hold_time` variable in `/usr/local/lib/shutdown_button/shutdown_button.py`
You will need to edit the file as root so f.e. `sudo nano /usr/local/lib/shutdown_button/shutdown_button.py`

You can still use the button for other purposes while this script is active! As long as you don't press it longer than 5 seconds it will be usable as any other button.
