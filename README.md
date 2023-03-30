# Table of Contents
   * [Home Assistant configuration](#home-assistant-configuration)
      * [The key software](#the-key-software)
      * [Floorplan](#floorplan)
      * [Devices](#devices)
      * [Zigbee](#zigbee)
      * [Lighting](#lighting)
      * [Media](#media)
      * [Notifications:](#notifications)
      * [Presence detection:](#presence-detection)
      * [Core integrations and APIs](#core-integrations-and-apis)
      * [Other things](#other-things)
      * [Custom integrations](#custom-integrations)
         * [Standard integrations](#standard-integrations)
      * [Other software and services](#other-software-and-services)
      * [Notes](#notes)
   * [(Far) Future plans](#far-future-plans)
      * [Automation thoughts](#automation-thoughts)
   * [Useful links](#useful-links)
   * [Coffee](#coffee)

# Home Assistant configuration

This is my live(-ish) [Home Assistant](https://home-assistant.io/) Core configuration, This instance is running 2023.3.4 
on a mini-PC (AMD Ryzen 5 5560U), with more RAM than I'm ever going to use. I use a Python 3.10.9 virtual environment 
built [with pyenv](https://github.com/pyenv/pyenv), [following this guide](https://home-assistant.io/docs/installation/raspberry-pi/).

Each directory has a short readme explaining what's in there, and the purpose of each file or group of files.

## The key software

* [Home Assistant](https://home-assistant.io/) (2023.3.4)
* [traefik](https://traefik.io/) (2.9.9) with [ZeroSSL](https://zerossl.com/) for remote access (replaced NGINX)
* [Zigbee2MQTT](https://www.zigbee2mqtt.io/) (1.30.1) for Zigbee
* [Mosquitto](https://mosquitto.org/) for the MQTT broker

## Floorplan

I use [Floorplan](https://github.com/ExperienceLovelace/ha-floorplan) for a high level overview
  * ![Screenshot of floorplan](https://i.imgur.com/gzwtfno.png)
  * Showing: 
    * The grey bin is due for collection tomorrow. If any were due today they'd have a red outline.
    * The family room and home office are occupied
    * The office window is open (red with yellow outline), all others are closed (green).
    * All outside doors are closed (green), as are many interior doors (brown). Open interior doors are green.
    * Motion has been detected in the office (yellow with a red outline), but nowhere else.
    * The family room TV is on (blue).
    * The car isn't in the garage (faded), but the freezer lid is closed (blue).
    * All the mobiles are home, and I'm working from home.
    * The temperature and humidity in all rooms are good (green).
    * Oh, and the printer's consumables are unknown (blue).
  * The floorplan was created in [Inkscape](https://inkscape.org/), by importing the image of the house's floorplan from the purchase paperwork, then drawing over it. If you look [at it](www/custom_ui/floorplan/floorplan.svg) you'll see that I built it up in layers, one for the foundation (ground), one for the structure, and one for the sensors. I don't really use those currently, other than to ensure that the right things are on top (sensors).

## Devices

You can find a list of my [current and previous hardware here](hardware.md).

## Zigbee

For Zigbee I use [Zigbee2MQTT](https://www.zigbee2mqtt.io/) (version 1.30.1) running on another system. I use this instead of ZHA because my experience with Z-Wave taught me the value of separation.

I used to use the original zwave integration on a remote system, using [Remote Home-Assistant](https://github.com/custom-components/remote_homeassistant). I've since stopped using Z-Wave, as [explained here](ZWAVE.md).

## Lighting

  * [Yeelight](https://home-assistant.io/integrations/yeelight/) integration and led strips. These provide good enough lighting to read by at night, and also to help wake us in the morning.
  * Zigbee bulbs and strips in various rooms.

## Media

  * [Sonos](https://www.sonos.com/) speakers and [integration](https://home-assistant.io/integrations/sonos/)
  * [Squeezebox Radio](http://support.logitech.com/en_us/product/squeezebox-radio-black) as a smart alarm clock, and [associated integration](https://home-assistant.io/integrations/squeezebox/)
  * [Cast](https://home-assistant.io/integrations/cast) devices - a bunch of [Google Home Minis](https://store.google.com/product/google_home_mini), a couple of [Google Home Hubs](https://store.google.com/product/google_home_hub), 
  and a [Lenovo Smart Display](https://www.lenovo.com/gb/en/consumer-tablet-and-smart-device/lenovo-smart-device/smart-core-device/Smart-Display-10/p/ZA3N0006GB)

## Notifications:

  * [Telegram](https://telegram.org) for my notifications
  * Supported by Google Chat using a command line notifier (so the messages come from a bot, and not a personal account)
  * For sysem status notifications I use the [REST notifier](https://www.home-assistant.io/integrations/notify.rest/) for [Discord](https://discordapp.com/), along with the [Discord notifier](https://www.home-assistant.io/integrations/discord/) itself
  * LaMetric for [notifications](https://home-assistant.io/integrations/lametric/) "in person", and it's a clock the rest of the time
  * [TTS](https://home-assistant.io/integrations/tts/) with the Google Home Mini's, Sonos, and Squeezeboxes, aided by [Sonos Cloud](https://github.com/jjlawren/sonos_cloud) to avoid interrupting music

## Presence detection:

  * Back to using [Nmap](https://nmap.org/) for [device tracking](https://home-assistant.io/integrations/nmap_tracker/). While I did switch to [Fritz!Box](https://en.avm.de/) [device tracking](https://www.home-assistant.io/integrations/fritz/) when I upgraded my router, the router ran out of memory
  * [Monitor](https://github.com/andrewjfreyer/monitor) on another Pi3, and an Orange Pi Zero LTS with a CSR 4.0 USB dongle. This has completely replaced the use of the built in Bluetooth device tracker, and more than halved the startup time of HA.
    * This works with our mobile phones, tablets, and beacons
  * The [HA Companion app](https://companion.home-assistant.io/) for remote tracking. I used to use [GPS Logger](https://home-assistant.io/integrations/gpslogger/), but the additional sensors in the official app are a winner
    * I used to use [OwnTracks](http://owntracks.org/) for device tracking, using the [HTTP interface](https://home-assistant.io/integrations/owntracks_http/), but not only did it have an [annoying bug](https://github.com/owntracks/android/issues/508) that caused it to randomly disable reporting, but it had been abandoned by the developer. Version 2.0 of the app solved both of those, but I've seen no reason to go back.

You'll note I use three different device trackers, two for home (nmap, bluetooth) and one for away (HA App). I explain more about [this here](https://blog.ceard.tech/2020/04/presence-detection-one-last-time.html) (you can see the journey I took to get there, [starting here](https://blog.ceard.tech/2018/01/home-assistant-and-basic-presence.html), with an update [here](https://blog.ceard.tech/2018/09/a-while-back-i-covered-how-i-was-doing.html), and [another update](https://blog.ceard.tech/2018/10/presence-detection-update-3.html), and then [a fourth update](https://blog.ceard.tech/2019/03/presence-detection-are-we-nearly-there.html)). Short version - I don't merge the trackers (that's going away anyway), but I do use groups again.  I've experimented with the [Bayesian](https://www.home-assistant.io/integrations/bayesian) sensor, but compared to what I can do with the automations, it's not flexible enough for me.

## Core integrations and APIs

  * [TransportAPI](https://developer.transportapi.com/) for information on the local train service with the [UK transport](https://home-assistant.io/integrations/uk_transport/) integration
  * [DarkSky](https://darksky.net/dev/) for weather data, alongside the [Met Office](https://www.metoffice.gov.uk/datapoint), along with the [associated](https://home-assistant.io/integrations/darksky/) sensor [integration](https://home-assistant.io/integrations/metoffice/)
  * [Plex](https://www.plex.tv/sign-in/) for watching media, on TV, tablets and mobiles. I don't currently use [the component](https://home-assistant.io/components/media_player.plex/) even if it's configured
  * [Here Travel Time](https://www.home-assistant.io/integrations/here_travel_time/) integration, replacing my previous use of the [Google Travel Time integration](https://home-assistant.io/integrations/google_travel_time/) (which uses the Google [Distance Matrix](https://developers.google.com/maps/documentation/distance-matrix/)) to provide estimated time to home

## Other things

  * [Getmail](http://pyropus.ca/software/getmail/) with [a script](local/bin/parse-email) that acts as the message delivery agent, to parse the recycling collection emails
    * I gave up on the the [IMAP email content](https://home-assistant.io/integrations/imap_email_content/) sensor since it doesn't keep state through restarts (which isn't unique to it, Home Assistant doesn't have a persistence mechanism other than for the `input_*` entities)
  * A HiWatch IPC-T140 dome camera, using the generic camera integration. I use [Frigate](https://frigate.video/) for motion and object detection, supported by a Coral stick. This runs on a different computer to the one that runs Home Assistant.

## Custom integrations

Historically I didn't make much use of custom components/integrations, however that's changed. Here are the ones I use, and why:

* [HACS](https://hacs.xyz) for intalling, updating, and finding new custom integrations. All other custom integrations are installed using this.
* [Adaptive lighting](https://github.com/basnijholt/adaptive-lighting) (replacing [Circadian lighting](https://github.com/claytonjn/hass-circadian_lighting/)) since the built in [flux integration](https://www.home-assistant.io/integrations/flux) isn't as good.
* [Alarmo](https://github.com/nielsfaber/alarmo) as an alternative to the built in manual alarm
* [Frigate](https://github.com/blakeblackshear/frigate-hass-integration) for integrating with Frigate
* [Here Weather](https://github.com/eifinger/hass-here-weather) as yet another weather integration, it has the advantage that it includes a (brief) text summary of the forecast
* [Sonos Cloud](https://github.com/jjlawren/sonos_cloud) to allow TTS (and media playing) without interrupting the music
* [The Watchman](https://github.com/dummylabs/thewatchman) for making sure I've caught all the missing entities
* [WebRTC](https://github.com/AlexxIT/WebRTC) to make viewing cameras less laggy

### Standard integrations

I moved these all [out here](integrations.md) because it's a long list, and not _that_ interesting.

## Other software and services

* [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome/) for blocking those pesky adverts
* [Authentik](https://goauthentik.io/) for authentication when remotely accessing services
* [Cloudflare Pages](https://pages.cloudflare.com/) to host my blog
* [Container Mon](https://github.com/RafhaanShah/Container-Mon) so I know when a container is unhealthy
* [Dozzle](https://dozzle.dev/) for each access to container logs
* [Diun](https://github.com/crazy-max/diun/) to get notifications when an update is available for a container
* [Frigate](https://frigate.video/) for motion detection
* [Heimdall](https://heimdall.site/) for a dashboard of all my apps
* [Jekyll](https://jekyllrb.com/) for my blog
* [netdata](https://my-netdata.io/) so I can keep an eye on the performance
* [Paperless NGX](https://github.com/paperless-ngx/paperless-ngx) for turning paper into searcheable digital documents
* [Photoprism](https://photoprism.app/) both to back up photos from the mobile phones, as well as make it easier to find photos
* [rpi-clone](https://github.com/billw2/rpi-clone) for bootable backups of the Pis
* [rclone](https://rclone.org/) for offsite backups
* [rsnapshot](https://rsnapshot.org/) runs on another system, and pulls backups 
* [traefik](https://traefik.io/) with [ZeroSSL](https://zerossl.com/) for remote access (will shortly replace nginx)
  * I did previously use [nginx](https://nginx.org/en/) to provide remote access, in conjunction with [Let's Encrypt](https://letsencrypt.org/)
* [Uptime Kuma](https://github.com/louislam/uptime-kuma) for some simple service status monitoring
* [Wireguard](https://www.wireguard.com/) for remote access to my network

## Notes

* These are (automatically) modified versions of my actual configurations
* The goals with Home Assistant have been:
  1. Minimise human actions, and where that isn't possible streamline those human actions
  2. Provide voice control where the automations don't get it right (but try to fix that)
  3. Have a minimal UI to provide manual control (this is currently the Google Home app)

# (Far) Future plans

A large amount of this will require a rewire of the lighting circuits, so that all the light switches have a neutral wire.

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
