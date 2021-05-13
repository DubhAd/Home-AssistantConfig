This is a list of the various pieces of hardware I use, have used, or plan to use with Home Assistant, along with my take on them (if I've used them).

## Buy again notes:

| Symbol | Means |
| :---: | --- |
| :heavy_check_mark: | Yes |
| :pause_button: | Waiting on the next generation of this - typically that means it's good, but not Zigbee 3.0 |
| :grey_question: | Maybe - it's not bad, but I may find something better |
| :thumbsdown: | Unlikely, it's not terrible, but it has issues |
| :small_red_triangle: | There's a newer version that's better |
| :no_entry: | Discontinued |
| :warning: | Won't buy again - maybe it's the worst option, maybe there's other issues |

# Zigbee

My goal is to migrate away from all my pre Zigbee 3.0 devices to Zigbee 3.0. Sure, I'm limited to 200 Zigbee 3.0 devices in the mesh, but I don't expect that I'll actually get close enough to that limit for it to matter. If that does look likely to happen then I can always run two meshes.

## Zigbee 3.0 

| What | Function | Buy again? | Notes |
| --- | --- | :---: | --- |
| [Zig-A-Zig-Ah!](https://www.tindie.com/products/electrolama/zzh-cc2652r-multiprotocol-rf-stick/) | Coordinator | :heavy_check_mark: | The Zigbee 3.0 coordinator. Currently on the 202101 firmware, and proving solid and stable. I bought a second as a spare which I may use as a router. |
| Sleash | None | :warning: | Works as a router, but be aware of the well documented communication problems with the seller. |
| [Tube CC2652 router](https://www.tubeszb.com/product/cc_router/4) | Router | :heavy_check_mark: | A friend ordered a couple of these and it turned out they only needed one, so they gave me the spare. It replaced a CC2530 with antenna, and so far, so good. The sign of a good router device is that you forget about it after all :P |
| [CR Smart Home TS0207](https://www.zigbee2mqtt.io/devices/TS0207.html) | Leak sensor | :heavy_check_mark: | Bought one to test it out, and it works exactly as described. Ordered a few more for around the house. |
| [Gledopto GL-C-008P](https://www.zigbee2mqtt.io/devices/GL-C-008P.html) | Hall light | :heavy_check_mark: | Replaced the older GL-C-008, transitions are smoother, but otherwise it behaves much like the old unit. I use this with a strip of 24V RGB-CCT tape for some lighting in the hall, which is otherwise quite dark. I may replace the tape with COB tape |
| [IKEA LED1733G7](https://www.zigbee2mqtt.io/devices/LED1733G7.html#ikea-led1733g7) | Light | :heavy_check_mark: | I bought a couple of these for background lighting in the living room. I have no complaints about them, they transition smoothly, have a good range of brightness, and are cheap. NB: I'm not 100% sure these are Zigbee 3.0. |
| [Ikea LED1739R5](https://www.zigbee2mqtt.io/devices/LED1537R6_LED1739R5.html#ikea-led1537r6%252Fled1739r5) | Light | :heavy_check_mark: | This was bought to replace the Osram, and it does this well. My comments for the other Ikea lights apply here too. |
| [Innr SP222](https://www.zigbee2mqtt.io/devices/SP_222.html) | Router | :grey_question: | Purely functions as a (Zigbee 3.0) router, it doesn't do power monitoring, but it is compact and has local control. I'm going to use some more of these to replace some of the Z-Wave sockets. |
| [Konke button](https://www.zigbee2mqtt.io/devices/2AJZ4KPKEY.html) | Remote | :thumbsdown: | These are neat, smaller than the Xiaomi button, but not as nice to use. The main downside is that it supports three channels, out of 26... |
| [Konke contact sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPDR.html) | Doors | :grey_question: | These are neat, slightly smaller than the Xiaomi sensors, but visually not as nice. The main downside is that it supports three channels, out of 26... |
| [Konke motion sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPBS.html) | Motion sensor | :grey_question: | These are neat, smaller than the Xiaomi sensors, and visually quite nice. The main downside is that it supports three channels, out of 26... |
| [Konke temperature sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPFT.html) | Temperature and humidity | :grey_question: | These are neat, smaller than the Xiaomi sensors, but visually not as nice. The main downside is that it supports three channels, out of 26... |
| [Lidl light strip](https://www.zigbee2mqtt.io/devices/HG06104A.html) | Office light | :grey_question: | Not a bad strip, doesn't go that dim, but it works pretty well and isn't expensive. |
| [TERNCY-DC01](https://www.zigbee2mqtt.io/devices/TERNCY-DC01.html) | Windows | :warning: | Others have no problems, but this won't pair with my ZZH | 
| [TERNCY-PP01](https://www.zigbee2mqtt.io/devices/TERNCY-PP01.html) | Room sensor | :warning: | Combined motion, light, temperature sensor, and a button. It's huge, and like the other Terncy kit, won't pair for me. |
| [TERNCY-SD01](https://www.zigbee2mqtt.io/devices/TERNCY-SD01.html) | Remote | :warning: | I wanted this to give me volume control in the office, but sadly [it won't pair](https://github.com/Koenkk/zigbee2mqtt/discussions/5682). |
| [Xiaomi Mijia light sensor](https://www.zigbee2mqtt.io/devices/GZCGQ01LM.html) | Light levels | :heavy_check_mark: | This is a very reponsive, well behaved light sensor. If you're looking for one, I'd recommend this one. | 
| [YSRSAI YSR-MINI-01_rgbcct](https://www.zigbee2mqtt.io/devices/YSR-MINI-01_rgbcct.html) | Bedroom light | | A compact controller with what looks like local control. Sadly it takes a slightly non-standard connector for the LED strips, so I'm waiting on something coming so I can use it. |

### No longer in use
| What | Function | Buy again? | Notes |
| --- | --- | :---: | --- |
| [Lidl power socket](https://www.zigbee2mqtt.io/devices/HG06337.html) | None | :warning: | Quite a good socket, a little bulky, but it does power monitoring. Sadly it constantly dropped off the mesh and reconnected, so I removed it. |

## Zigbee 1.2 and older

| What | Function | Buy again? | Notes |
| --- | --- | :---: | --- |
| [Gledopto GL-C-008 RGB+CCT](https://www.zigbee2mqtt.io/devices/GL-C-008-1ID.html) | Hall lighting | :small_red_triangle: |  I use this with a strip of 24V RGB-CCT tape for some lighting in the hall, which is otherwise quite dark. I plan on swapping this out for the Zigbee 3.0 version, and probably replacing the tape with COB tape |
| [Hue dimmer](https://www.zigbee2mqtt.io/devices/324131092621.html) | Remote | :grey_question: | Quite nice four button remote, the only downside is that it's not Zigbee 3.0 |
| [Xiaomi Aqara button](https://www.zigbee2mqtt.io/devices/WXKG12LM.html) | Remote | :pause_button: | I like these, they feel good and work well, but it's only Zigbee 1.2 |
| [Xiaomi Aqara door/window sensor](https://www.zigbee2mqtt.io/devices/MCCGQ11LM.html) | Doors and windows | :pause_button: | I have a stack of those, one for every exterior window, and a few on interior doors. They're cheap, compact, don't stand out visually, and just work. The T1 versions are the new Zigbee 3.0 versions, that are really hard to get. |
| [Xiaomi Aqara motion sensor](https://www.zigbee2mqtt.io/devices/RTCGQ11LM.html) | Motion | :pause_button: | These are ok, not great, but ok. There is an on board light sensor, but it only reports light levels when motion is detected | 
| [Xiaomi Aqara temperature sensor](https://www.zigbee2mqtt.io/devices/WSDCGQ11LM.html) | Temperature and humidity | :pause_button: | These are pretty good, they report regularly enough to be useful and are reliable. Hopefully we'll get a Zigbee 3.0 version soon. |

### No longer in use
| What | Function | Buy again? | Notes |
| --- | --- | :---: | --- |
| CC2531 | Coordinator | :warning: | It worked for a small mesh, mostly. It isn't a great choice though so I'm migrating to the Zig-A-Zig-Ah! |
| [Hive active plug](https://www.zigbee2mqtt.io/devices/1613V.html) | Controlling an uplighter | :thumbsdown: | Worked well, but  slightly bulky and also not Zigbee 3.0 |
| [Ikea router](https://www.zigbee2mqtt.io/devices/E1746.html) | None | :thumbsdown: | Purely functioned as a router for the original mesh, but I don't need it any more, and it only routes for a handful of devices |
| [Osram smart bulb](https://www.zigbee2mqtt.io/devices/AC08560-DIM.html) | None | :warning: | This was a pain to include, and worked fine for a while. Then one day it fell off the mesh and refused to either reconnect or reset. Then I found out that problems are normal with this brand... |
| [Salus SP600](https://www.zigbee2mqtt.io/devices/SP600.html) | Router | :thumbsdown: | A pretty good socket, with power monitoring, but it's only Zigbee 1.2 |

# Z-Wave

All my current Z-Wave hardware is Z-Wave Plus.

| What | Function | Buy again? | Thoughts |
| --- | --- | :---: | --- |
| [Razberry board](https://razberry.z-wave.me/) | Controller | :thumbsdown: | It does avoid having to use a USB socket, but my Z-Wave mesh can now only run from the Pi |
| Aeotec MultiSensor 6 | Office sensor | :heavy_check_mark: | Excellent all around multi-sensor with a bonus of being USB powered |
| Fibaro FGK10x | Garage door sensors | :no_entry: | Fairly unobtrusive door sensors, which have support for external sensors too. Their only downside is they're not made any more |
| Fibaro MultiSensor | Living room sensor | :grey_question: | Pretty good multi-sensor. Doesn't do humidity unlike the Aeotec, and can chew through batteries like there's no tomorrow though. I'm more likely to buy some Zigbee sensors than buy another one of these. |
| NodOn Octan | Bedroom lights | :no_entry: | Great little four button remote, which sadly is discontinued |
| NodOn Soft Remote | Bedroom lights | :no_entry: | A brightly coloured, kid proof four button remote, that's also discontinued |
| [Sensative strips](https://sensative.com/sensors/strips-zwave/guard/) | Exterior door sensors | :heavy_check_mark: | Awesome sensors that fit inside the door (or window) frame. You can't replace the battery, but they claim a 10 year lifespan, which is in line with my experiences so far. |
| TKB TZ69E | General sockets | :heavy_check_mark: | Smart switch with power monitoring. I use these for the garden lights, and a range of interior sockets. Slightly bulky, but rather good. |
| Z-Wave.me WALLC-S | Light switch | :no_entry: | Looks like a normal light switch, and is _Associated_ with the TKB socket for the garden lights, this allows us to turn the lights on and off manually when required. Discontinued. |

# Other

| What | Function | Buy again? | Thoughts |
| --- | --- | :---: | --- |
| Google Home | Various | :heavy_check_mark: | Smart displays, announcements, and voice control. Mostly these are used for casting a camera stream to, or for TTS. |
| HiWatch IPC-T140 | Camera | :small_red_triangle: | Exterior security camera. A few years old now, and newer generation kit is better, but it's still pretty good |
| [LaMetric](https://lametric.com/) | Notifications | :heavy_check_mark: | Simple scrolling ticker, awesome for many unobtrusive notifications |
| Sonos speakers | Music! | :heavy_check_mark: | Good enough quality for audio, more then loud enough. I'll likely buy some of the Symfonisk speakers instead of more Play One type devices though |
| Squeezebox Radio | Alarm clock | :no_entry: | Awesome, but discontinued |
| Yeelight strip | Behind the bedhead lighting | :grey_question: | WiFi connected smart RGB strips, not terrible, not awesome. I'm considering replacing these with something Zigbee connected, or maybe WLED. |
| 240V RGB LED strip | Garden lights | :grey_question: | Yes, a single strip along the garden perimeter. There's about 25 meters of light strip in use, and being 240V no need to inject power. Sadly being dumb there's no fine control. If I had to do it again, I'd use WLED. |

# Future plans

* Dimmer modules at most light switches, the exception will be the toilet (since there's a fan linked to it), the outside light (which is a self contained unit that can't be dimmed), and the number sign light (though that _probably_ could be handled with a 12V dimmer)
* Switch modules for the extractor fans
* Multisensors or multiple sensors (light/motion/humidity/temperature) in the bedrooms and bathrooms
* Multisensors or multiple sensors (light/motion/temperature) in all other rooms
* More door and window sensors, including on the garden gate - the garden gate one may have to be LoRa as I'm not seeing any weatherproof Zigbee options yet
* Some form of distance sensor (ultrasonic or laser) in the garage
* Digital LED strip for the front of the garage
* LED strips (either Zigbee or Digital) for accent lighting and pathway lighting

