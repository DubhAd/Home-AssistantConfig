# Z-Wave

**My Z-Wave stack is no longer in use**

My Z-Wave stack used to run on a Raspberry Pi 3, using the old All in One installer (effectively a [manual install like this](https://blog.ceard.tech/2017/12/installing-home-assistant-in-virtual.html), on a 16 GB card, that I'd [upgraded to Python 3.6](https://blog.ceard.tech/2017/12/upgrading-python-virtual-environment.html). I used a [Razberry](https://razberry.z-wave.me/) board for Z-Wave control. The configuration for that instance, before it was turned off, can be [found here](https://github.com/DubhAd/HomeAssistant-ZWave).

To limit the risk brought by SD card corruption (a known risk with Pi3) I stored the Home Assistant database on a USB stick, and use a multi-port USB charger with sufficient power for all ports, but left one unused. The power cables were short, and high quality, to minimise issues with voltage drop. Of course, I also took [many different backups](https://blog.ceard.tech/2017/10/backing-up-home-assistant.html) to reduce the risk of losing anything.

This was one of a number of Pi3s I've got, and they're all in a [Multi-Pi stackable case](https://www.okdo.com/p/multi-pi-stackable-raspberry-pi-case/), to keep the footprint down. They share an HDMI cable to a nearby monitor, and an old USB keyboard I've got kicking around, because having a Pi fail to respond isn't that uncommon.

I stopped using this in September 2022, having expanded my Zigbee mesh. I may well return to Z-Wave in the future, those Sensative Guard strips are still the best design of door/window sensor I've found, but for now... Z-Wave no more.
