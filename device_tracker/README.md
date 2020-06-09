# Presence detection

Components:
* [GPSlogger](https://home-assistant.io/components/device_tracker.gpslogger/)
* [MQTT](https://www.home-assistant.io/components/device_tracker.mqtt)
* [nmap](https://www.home-assistant.io/components/device_tracker.nmap_tracker/)

You can read about my approach [on my blog](https://blog.ceard.tech/)

## GPS Logger

For knowing (roughly) where people are. This is used for the proximity and travel time sensors, and other automations.

## MQTT

I use MQTT for two main purposes
* A dummy device tracker for the [person component](https://www.home-assistant.io/components/person/). This maps to the input boolean I use to indicate if somebody is home or not.
* Device trackers for the various entities created by [monitor](https://github.com/andrewjfreyer/monitor).

## nmap

Simple network scanning based detection. Modern smart phones will turn their WiFi off in sleep mode, so this can't be used by itself.
