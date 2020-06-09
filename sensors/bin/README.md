# Bin Sensors

Components:
* [file sensor](https://home-assistant.io/components/sensor.file/)
* [template sensor](https://home-assistant.io/components/sensor.template/)


In theory the recycling and rubbish collections happen on a nice predictable schedule, and mostly they do. Except it's not always every other week, some are once a month, some are weekly, and sometimes they move the day. 
Our local council sends out emails about the upcoming collection. Which is great, but parsing those in Home Assistant is a pain. As a result I'm using [Getmail](http://pyropus.ca/software/getmail/), to pass incoming emails for the relevant sender through a [local script](../local/bin/parse-email). That script then spits out information in JSON format to the relevant files (one per collection type).

This mass of sensors then pulls out the dates for each collection type, and then has sensors that change between _future_, _tomorrow_, _today_, and _past_ as appropriate. These values are then used in automations, and Floorplan.

