# Table of Contents
   * [Home Assistant configuration](#home-assistant-configuration)
      * [Z-Wave](#z-wave)
      * [The key software](#the-key-software)
      * [The devices, services, and software I use (with HA)](#the-devices-services-and-software-i-use-with-ha)
      * [Floorplan](#floorplan)
         * [Z-Wave](#z-wave-1)
         * [Zigbee](#zigbee)
         * [Lighting](#lighting)
         * [Media](#media)
         * [Notifications:](#notifications)
         * [Presence detection:](#presence-detection)
         * [Core integrations and APIs](#core-integrations-and-apis)
         * [Other things](#other-things)
         * [Custom integrations](#custom-integrations)
            * [Standard integrations](#standard-integrations)
         * [Other software](#other-software)
      * [Notes](#notes)
   * [Future plans](#future-plans)
      * [Devices](#devices)
      * [Automation thoughts](#automation-thoughts)
   * [Useful links](#useful-links)
   * [Coffee](#coffee)
##TOC##

# Home Assistant configuration
This is my primary [Home Assistant](https://home-assistant.io/) Core configuration, This instance is running 0.117.6 (Python 3.8.6 built [with this guide](https://blog.ceard.tech/2017/12/upgrading-python-virtual-environment.html)) on a VM, using Proxmox on an old laptop (Intel Core i5-3230M), the VM has two cores and 2 GB of RAM allocated. I use a manual Python virtual environment install [following this guide](https://home-assistant.io/docs/installation/raspberry-pi/).

Each directory has a short readme explaining what's in there, and the purpose of each file or group of files.

## Z-Wave
My Z-Wave stack runs on a Raspberry Pi 3, using the old All in One installer (effectively a [manual install like this](https://blog.ceard.tech/2017/12/installing-home-assistant-in-virtual.html), on a 16 GB card, that I've [upgraded to Python 3.6](https://blog.ceard.tech/2017/12/upgrading-python-virtual-environment.html). I use a [Razberry](https://razberry.z-wave.me/) board for Z-Wave control. The configuration for that instance can be [found here](https://github.com/DubhAd/HomeAssistant-ZWave).

To limit the risk brought by SD card corruption (a known risk with Pi3) I store the Home Assistant database on a USB stick, and use a multi-port USB charger with sufficient power for all ports, but have left one unused. The power cables are short, and high quality, to minimise issues with voltage drop. Of course, I also take [many different backups](https://blog.ceard.tech/2017/10/backing-up-home-assistant.html) to reduce the risk of losing anything.

This is one of a number of Pi3s I've got, and they're all in a [Multi-Pi stackable case](https://www.modmypi.com/raspberry-pi/cases-183/multi-pi-stacker/multi-pi-stackable-raspberry-pi-case), to keep the footprint down. They share an HDMI cable to a nearby monitor, and an old USB keyboard I've got kicking around, because having a Pi fail to respond isn't that uncommon.

## The key software

* [Home Assistant](https://home-assistant.io/)
* [nginx](https://nginx.org/en/) to provide remote access, in conjunction with [Let's Encrypt](https://letsencrypt.org/)
* [Mosquitto](https://mosquitto.org/) for the MQTT broker
* MariaDB for the database

## The devices, services, and software I use (with HA)

* [Sandisk Extreme](https://www.sandisk.co.uk/home/memory-cards/microsd-cards/extreme-microsd) micro SD cards (for the Z-Wave Pi)

## Floorplan

I use [Floorplan](https://github.com/pkozul/ha-floorplan) for a high level overview
  * ![Screenshot of floorplan](https://i.imgur.com/8oe0uTQ.png)
  * Showing: 
    * No bins are due for collection otherwise they'd have a yellow outline (collected tomorrow) or red outline (collected today)
    * The living room and family room are occupied
    * The front door is open, motion has been detected in the downstairs hall, and two windows upstairs is open
    * The TV is on in the living room
    * The TV in the family room is on
    * All the mobiles are home, as is the tablet, and the car
    * The office is a bit warm (red temperature), and the humidity in the bathroom and master en-suite is a little high (amber)
    * Oh, and the printer isn't a little low on consumables.
  * The floorplan was created in [Inkscape](https://inkscape.org/), by importing the image of the house's floorplan from the purchase paperwork, then drawing over it. If you look [at it](www/custom_ui/floorplan/floorplan.svg) you'll see that I built it up in layers, one for the foundation (ground), one for the structure, and one for the sensors. I don't really use those currently, other than to ensure that the right things are on top (sensors).

### Z-Wave

Currently I use the original [zwave](https://home-assistant.io/docs/z-wave/) integration, on a remote system

  * Z-Wave.me [Razberry](https://razberry.z-wave.me/) Z-Wave board - it has the advantage of not using a USB port, but does require that the onboard Bluetooth is disabled
  * Aeotec [MultiSensor 6](https://aeotec.com/z-wave-sensor)
  * Fibaro [motion sensor](https://www.fibaro.com/en/products/motion-sensor/) in the living room
  * Fibaro FGK10x door sensors (previous generation, superseded by the [FGDW-002](http://manuals.fibaro.com/door-window-sensor-2/)) on the garage doors
  * Sensative [door/window strips](https://www.stripsbysensative.com/strips-guard/) on the external house doors
  * TKB [TKB TZ69E](http://www.tkbhome.com/?cn-p-d-271.html) - metering wall plugs
  * Foxx Project [Smart Switch](https://www.getfoxx.com/products) (which identifies itself as an Aeotec ZW075, aka Smart Switch Gen5). These are cheap, but there's no local switch control for the attached device. Mostly I'm using these as range extenders.
  * NodOn [Octan Remote](http://nodon.fr/en/z-wave/octan-remote_7-2) in the master bedroom to provide manual control of the Yeelight. It was originally used by the kitchen door, where the next item is now mounted.
  * NodOn [Soft Remote](https://nodon.fr/en/nodon/z-wave-soft-remote/) in the second bedroom, to also provide manual control of that room's Yeelight.
  * Z-Wave.me [WALLC-S](http://eng.z-wave.me/index.php?id=30) wall controller, to provide a wall switch for the garden lights

### Zigbee

I use [Zigbee2MQTT](https://www.zigbee2mqtt.io/) running on another system

  * A CC2531 coordinator bought [from here](https://zigbee2mqtt.discourse.group/t/ad-buy-ready2use-zigbee2mqtt-stick-flashed-antenna-mod-and-printed-case/22/)
  * A [Zig-A-Zig-Ah!](https://electrolama.com/projects/zig-a-zig-ah/) for a new Zigbee 3.0 mesh
  * Xiaomi Aqara [door/window sensor](https://xiaomi-mi.com/sockets-and-sensors/xiaomi-aqara-window-door-sensor/) - one on every external window (yes, that's a lot)
  * Xiaomi Aqara [motion and light sensor](https://xiaomi-mi.com/sockets-and-sensors/aqara-human-body-sensor/)
  * Xiaomi Aqara [temperature and humidity sensor](https://xiaomi-mi.com/sockets-and-sensors/aqara-temperature-and-humidity-sensor/) in the bathrooms
  * Gledopto [GL-C-008 RGB+CCT](https://www.aliexpress.com/item/32858603964.html) LED controller (along with some RGB-CCT LED tape and a 24V power supplly)
  * A Hive [active smart plug](https://smile.amazon.co.uk/gp/product/B01N7L53TB/)
  * A Salus [SP600 smart plug](https://smile.amazon.co.uk/gp/product/B0743CTGJ6/)

### Lighting

  * [Yeelight](https://home-assistant.io/integrations/yeelight/) integration and [led strips](https://www.yeelight.com/en_US/product/pitaya), one mounted behind the headboard in the master bedroom, and one along the wall side of the bed frame in the second bedroom. These provide good enough lighting to read by at night, and also to help wake us in the morning.
  * Outdoor mains [240V LED strip](https://www.lightingever.co.uk/220-240-v-ac-led-strip-multicolour-5050-50m.html) which we turn on and off with one of the wall plugs

### Media

  * [Sonos](https://www.sonos.com/) speakers and [integration](https://home-assistant.io/integrations/sonos/)
  * [Squeezebox Radio](http://support.logitech.com/en_us/product/squeezebox-radio-black) as a smart alarm clock, and [associated integration](https://home-assistant.io/integrations/squeezebox/)
  * [Cast](https://home-assistant.io/integrations/cast) devices - a bunch of [Google Home Minis](https://store.google.com/product/google_home_mini), a couple of [Google Home Hubs](https://store.google.com/product/google_home_hub), 
  and a [Lenovo Smart Display](https://www.lenovo.com/gb/en/consumer-tablet-and-smart-device/lenovo-smart-device/smart-core-device/Smart-Display-10/p/ZA3N0006GB)

### Notifications:

  * [Telegram](https://telegram.org) for my notifications, supported by Hangouts Chat using a command line notifier, and the [REST notifier](https://www.home-assistant.io/integrations/notify.rest/) for [Discord](https://discordapp.com/) (system status notifications)
  * [LaMetric](https://lametric.com/) for [notifications](https://home-assistant.io/integrations/lametric/) "in person", and it's a clock the rest of the time
  * [TTS](https://home-assistant.io/integrations/tts/) with the Google Home Mini's, Sonos, and Squeezeboxes

### Presence detection:

  * Back to using [Nmap](https://nmap.org/) for [device tracking](https://home-assistant.io/integrations/nmap_tracker/). While I did switch to [Fritz!Box](https://en.avm.de/) [device tracking](https://www.home-assistant.io/integrations/fritz/) when I upgraded my router, the router ran out of memory
  * [Monitor](https://github.com/andrewjfreyer/monitor) on another Pi3, and an Orange Pi Zero LTS with a CSR 4.0 USB dongle. This has completely replaced the use of the built in Bluetooth device tracker, and more than halved the startup time of HA.
    * This works with our mobile phones, tablets, and beacons
  * [GPS Logger](https://home-assistant.io/integrations/gpslogger/) for remote device tracking
    * I used to use [OwnTracks](http://owntracks.org/) for device tracking, using the [HTTP interface](https://home-assistant.io/integrations/owntracks_http/), but not only did it have an [annoying bug](https://github.com/owntracks/android/issues/508) that caused it to randomly disable reporting, but it had been abandoned by the developer. Version 2.0 of the app solved both of those, but I've seen no reason to go back.

You'll note I use three different device trackers, two for home (nmap, bluetooth) and one for away (GPSLogger). I explain more about [this here](https://blog.ceard.tech/2020/04/presence-detection-one-last-time.html) (you can see the journey I took to get there, [starting here](https://blog.ceard.tech/2018/01/home-assistant-and-basic-presence.html), with an update [here](https://blog.ceard.tech/2018/09/a-while-back-i-covered-how-i-was-doing.html), and [another update](https://blog.ceard.tech/2018/10/presence-detection-update-3.html), and then [a fourth update](https://blog.ceard.tech/2019/03/presence-detection-are-we-nearly-there.html)). Short version - I don't merge the trackers (that's going away anyway), but I do use groups again.  I've experimented with the [Bayesian](https://www.home-assistant.io/integrations/bayesian) sensor, but compared to what I can do with the automations, it's not flexible enough for me.

### Core integrations and APIs

  * [TransportAPI](https://developer.transportapi.com/) for information on the local train service with the [UK transport](https://home-assistant.io/integrations/uk_transport/) integration
  * [DarkSky](https://darksky.net/dev/) for weather data, alongside the [Met Office](https://www.metoffice.gov.uk/datapoint), along with the [associated](https://home-assistant.io/integrations/darksky/) sensor [integration](https://home-assistant.io/integrations/metoffice/)
  * [Plex](https://www.plex.tv/sign-in/) for watching media, on TV, tablets and mobiles. I don't currently use [the component](https://home-assistant.io/components/media_player.plex/)
  * [Here Travel Time](https://www.home-assistant.io/integrations/here_travel_time/) integration, replacing my previous use of the [Google Travel Time integration](https://home-assistant.io/integrations/google_travel_time/) (which uses the Google [Distance Matrix](https://developers.google.com/maps/documentation/distance-matrix/)) to provide estimated time to home

### Other things

  * [Getmail](http://pyropus.ca/software/getmail/) with [a script](local/bin/parse-email) that acts as the message delivery agent, to parse the recycling collection emails
    * I gave up on the the [IMAP email content](https://home-assistant.io/integrations/imap_email_content/) sensor since it doesn't keep state through restarts (which isn't unique to it, Home Assistant doesn't have a persistence mechanism other than for the `input_*` entities)
  * A HiWatch IPC-T140 dome camera, using the generic camera integration. I use [MotionEye](https://github.com/ccrisan/motioneye/) for motion detection and [Doods](https://www.home-assistant.io/integrations/doods/) (in another VM) for object detection.

### Custom integrations

Historically I didn't make much use of custom components/integrations, however that's changed. Here are the ones I use, and why:

* [HACS](https://hacs.netlify.com) for intalling, updating, and finding new custom integrations. All other custom integrations are installed using this.
* [Circadian lighting](https://github.com/claytonjn/hass-circadian_lighting/) since the built in [flux integration](https://www.home-assistant.io/integrations/flux) isn't as good.
* [Fritzbox tools](https://github.com/mammuth/ha-fritzbox-tools) to allow me to track the status of the Internet connection
* [Home Assistant Remote](https://github.com/lukas-hetzenecker/home-assistant-remote) for linking my Z-Wave and primary instances. This is more effective than my ugly MQTT hack.

#### Standard integrations

These are all the standard integrations I've enabled (ignoring all the ones that Home Assistant (Core) itself uses internally), when last I checked. Some of these can only be set up in the UI, so you won't find them mentioned in the YAML here.

* [`alarm_control_panel`](https://www.home-assistant.io/integrations/alarm_control_panel/)
* [`alert`](https://www.home-assistant.io/integrations/alert/)
* [`automation`](https://www.home-assistant.io/integrations/automation/)
* [`binary_sensor`](https://www.home-assistant.io/integrations/binary_sensor/)
* [`calendar`](https://www.home-assistant.io/integrations/calendar/)
* [`camera`](https://www.home-assistant.io/integrations/camera/)
* [`cast`](https://www.home-assistant.io/integrations/cast/)
* [`cloud`](https://www.home-assistant.io/integrations/cloud/)
* [`default_config`](https://www.home-assistant.io/integrations/default_config/)
* [`device_tracker`](https://www.home-assistant.io/integrations/device_tracker/)
* [`discovery`](https://www.home-assistant.io/integrations/discovery/)
* [`ffmpeg`](https://www.home-assistant.io/integrations/ffmpeg/)
* [`geo_location`](https://www.home-assistant.io/integrations/geo_location/)
* [`google`](https://www.home-assistant.io/integrations/google/)
* [`gpslogger`](https://www.home-assistant.io/integrations/gpslogger/)
* [`group`](https://www.home-assistant.io/integrations/group/)
* [`history`](https://www.home-assistant.io/integrations/history/)
* [`http`](https://www.home-assistant.io/integrations/http/)
* [`influxdb`](https://www.home-assistant.io/integrations/influxdb/)
* [`input_boolean`](https://www.home-assistant.io/integrations/input_boolean/)
* [`input_datetime`](https://www.home-assistant.io/integrations/input_datetime/)
* [`input_number`](https://www.home-assistant.io/integrations/input_number/)
* [`input_select`](https://www.home-assistant.io/integrations/input_select/)
* [`input_text`](https://www.home-assistant.io/integrations/input_text/)
* [`light`](https://www.home-assistant.io/integrations/light/)
* [`local_ip`](https://www.home-assistant.io/integrations/local_ip/)
* [`logger`](https://www.home-assistant.io/integrations/logger/)
* [`lovelace`](https://www.home-assistant.io/integrations/lovelace/)
* [`media_player`](https://www.home-assistant.io/integrations/media_player/)
* [`met`](https://www.home-assistant.io/integrations/met/)
* [`mqtt`](https://www.home-assistant.io/integrations/mqtt/)
* [`notify`](https://www.home-assistant.io/integrations/notify/)
* [`person`](https://www.home-assistant.io/integrations/person/)
* [`plex`](https://www.home-assistant.io/integrations/plex/)
* [`proximity`](https://www.home-assistant.io/integrations/proximity/)
* [`recorder`](https://www.home-assistant.io/integrations/recorder/)
* [`rest_command`](https://www.home-assistant.io/integrations/rest_command/)
* [`samsungtv`](https://www.home-assistant.io/integrations/samsungtv/)
* [`scene`](https://www.home-assistant.io/integrations/scene/)
* [`script`](https://www.home-assistant.io/integrations/script/)
* [`sensor`](https://www.home-assistant.io/integrations/sensor/)
* [`sonos`](https://www.home-assistant.io/integrations/sonos/)
* [`ssdp`](https://www.home-assistant.io/integrations/ssdp/)
* [`stream`](https://www.home-assistant.io/integrations/stream/)
* [`sun`](https://www.home-assistant.io/integrations/sun/)
* [`switch`](https://www.home-assistant.io/integrations/switch/)
* [`system_health`](https://www.home-assistant.io/integrations/system_health/)
* [`telegram_bot`](https://www.home-assistant.io/integrations/telegram_bot/)
* [`timer`](https://www.home-assistant.io/integrations/timer/)
* [`tts`](https://www.home-assistant.io/integrations/tts/)
* [`updater`](https://www.home-assistant.io/integrations/updater/)
* [`weather`](https://www.home-assistant.io/integrations/weather/)
* [`webhook`](https://www.home-assistant.io/integrations/webhook/)
* [`wwlln`](https://www.home-assistant.io/integrations/wwlln/)
* [`yeelight`](https://www.home-assistant.io/integrations/yeelight/)
* [`zeroconf`](https://www.home-assistant.io/integrations/zeroconf/)
* [`zone`](https://www.home-assistant.io/integrations/zone/)

### Other software

* [PiVPN](http://www.pivpn.io/) for remote access to my network
* [Pi Hole](https://pi-hole.net/) for blocking those pesky adverts
* [netdata](https://my-netdata.io/) so I can keep an eye on the performance
* [rpi-clone](https://github.com/billw2/rpi-clone) for bootable backups of the Pis
* [rclone](https://rclone.org/) for offsite backups
* [rsnapshot](https://rsnapshot.org/) runs on another system, and pulls backups 
* [MotionEye](https://github.com/ccrisan/motioneye/) for motion detection
* [nginx](https://nginx.org/en/) to provide remote access, in conjunction with [Let's Encrypt](https://letsencrypt.org/)

## Notes

* These are (automatically) modified versions of my actual configurations
* The goals with Home Assistant have been:
  1. Minimise human actions, and where that isn't possible streamline those human actions
  2. Provide voice control where the automations don't get it right (but try to fix that)
  3. Have a minimal UI to provide manual control (this is currently the Google Home app)

# Future plans

A large amount of this will require a rewire of the lighting circuits, so that all the light switches have a neutral wire.

## Devices

* Dimmer modules at most light switches, the exception will be the toilet (since there's a fan linked to it) and the outside light
* Switch modules for the extractor fans
* Multisensors (light/motion/humidity/temperature) in the bedrooms and bathrooms
* Multisensors (light/motion/temperature) in all other rooms
* Lots more door and window sensors, including on the garden gate
* Some form of distance sensor (ultrasonic or laser) in the garage
* Digital LED strip for the front of the garage
* Analogue LED strips (likely with a Z-Wave controller) for accent lighting and pathway lighting

## Automation thoughts

* Turn on extractor fans when the humidity is more than 5 points above the adjacent room, turning off once they drop to within 5 points
* During darkness, if a bathroom door is opened, turn the bathroom light on at a low level, turning up to medium when the door closes, turning it off when the person leaves
* Turn on the outside front light when the front door opens, the doorbell rings, or somebody is less than 5 minutes away, and coming home
* Other than bedrooms, when the room is in darkness and there's movement turn on the light at a very low level
* During daytime, if the lights are on for *too long* turn them off
* Seasonal use of the digital LED strip
* Flash the relevant section of the LED strip red if the garage door is opening or closing

# Useful links

* [Home Assistant documentation](https://home-assistant.io/docs/) and [integration list](https://home-assistant.io/integrations/)
* Problems with Z-Wave delays and inconsistencies? Try [this script](https://hastebin.com/igujenogud.coffeescript) in the dev-states section and you'll see if you've problem devices - shown by an RTT value of 1,000 or more, and retries significantly more than other devices
* [My blog](https://ceard.tech/) on home automation and other things

# Coffee

If I've helped you, and you really want to, you can [buy me a coffee](https://buymeacoff.ee/9MWvkxr8P), but don't feel obliged - I'm not doing this for free coffee ;)
