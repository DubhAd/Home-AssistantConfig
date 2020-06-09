# Sensors

Components:
* [sensor](https://home-assistant.io/components/sensor/)
* [Dark Sky sensor](https://home-assistant.io/components/sensor.darksky/) 
* [file sensor](https://home-assistant.io/components/sensor.file/)
* [Google Travel Time](https://home-assistant.io/components/sensor.google_travel_time/)
* [Season](https://home-assistant.io/components/sensor.season/)
* [Sun](https://home-assistant.io/components/sun/)
* [template sensor](https://home-assistant.io/components/sensor.template/)
* [UK transport sensor](https://home-assistant.io/components/sensor.uk_transport/)
* [Waze travel time](https://www.home-assistant.io/components/sensor.waze_travel_time/)
* [XBox Live](https://home-assistant.io/components/sensor.xbox_live/)

Sooo many sensors.

## Battery

These are templates taken from work initially done by [skalavala](https://github.com/skalavala/smarthome) to turn the mobile battery level into a sensor, and dynamic icon.

## Dark Sky

The [Dark Sky sensor](https://home-assistant.io/components/sensor.darksky/) for local weather conditions - in theory anyway.

## Travel Time

Knowing how long it'll take people to get places is handy for various automations, so I use the Google and Waze travel time sensors. I've an automation that triggers the updates of these intelligently, rather than blindly updating every X minutes.

The names of the resulting sensor entities are personXs_time_to_home.

## Hass

Version number trackers, for a display in Overview that nobody ever looks at.

## Met Office

I prefer the [Met Office sensor](https://home-assistant.io/components/sensor.metoffice/) to the weather component, just for the granularity. Used alongside the Dark Sky weather, because that way they can both tell me something different from what's really going on outside.

## Office

Not really used any more, I was messing about and simply abandoned this. I should delete it at some point.

## People

This is to have a human friendly location for people. If they're in a zone then it takes on the name of the zone, otherwise it takes on the travel time to home. 

## Printer

I have a shell script that regularly does an SNMP poll of our laser printer (a Samsung M2835DW), and pulls out the state of the consumables. These extract the relevant values into sensors for other automations.

## Seasons

A season sensor, to feed into the seasons input select I use for managing various other automations (like the Christmas lights).

## SSL Certificate

Sensor for the SSL certificate expiry, it isn't needed but I haven't bothered to remove it.

## Sun

This extracts the sun's elevation from the attribute of the [sun component](https://home-assistant.io/components/sun/) into it's own sensor. This makes it easier to use in other automations, as I can just use a numeric state trigger or condition, rather than templates.

## System

Sensor for the last boot time. I've never used this.

## Template 

These are for the train status, but I lumped them all together in a single template block

## Trains

Automations to get the status of the trains (for the commute) and the status message. I generate these from shell scripts, and then pull them to HA here.

## UK Transport

Configuration for the [UK transport sensor](https://home-assistant.io/components/sensor.uk_transport/), for the commute

## XBox

The [XBox Live](https://home-assistant.io/components/sensor.xbox_live/) sensor.

## Z-Wave Battery

More template battery sensors, but for the Z-Wave devices this time.
