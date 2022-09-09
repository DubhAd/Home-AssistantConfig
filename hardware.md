This is a list of the various pieces of hardware I use, have used, or plan to use with Home Assistant, along with my take on them (if I've used them).

## Buy again notes:

| Symbol | Means |
| :---: | --- |
| :heavy_check_mark: | Yes |
| :pause_button: | Waiting on the next generation of this - typically that means it's good, but not Zigbee 3.0 |
| :grey_question: | Maybe - it's not bad, but I'm looking something better |
| :thumbsdown: | Unlikely, it's not terrible, but it has issues |
| :small_red_triangle: | There's a newer version that's better |
| :no_entry: | Discontinued |
| :warning: | Won't buy again - maybe it's the worst option, maybe there's other issues |

# Zigbee

My goal is to migrate away from all my pre Zigbee 3.0 devices to Zigbee 3.0. Sure, I'm limited to 200 Zigbee 3.0 devices in the mesh, but I don't expect that I'll actually get close enough to that limit for it to matter. If that does look likely to happen then I can always run two meshes.

## Zigbee 3.0 

| What | Function | Buy again? | Notes |
| --- | --- | :---: | --- |
| [Zig-A-Zig-Ah!](https://www.tindie.com/products/electrolama/zzh-cc2652r-multiprotocol-rf-stick/) | Coordinator | :heavy_check_mark: | The Zigbee 3.0 coordinator for my original mesh. Currently on the 202101 firmware, and proving solid and stable. I bought a second as a spare which I may use as a router. |
| Sonoff CC2652 | Coordinator | :no_entry: | Bought when it was released as it was cheap, it has an advantage that you can flash it without having to hold down buttons. Now running my new mesh. |
| [Tube CC2652 router](https://www.tubeszb.com/product/cc_router/4) | Router | :heavy_check_mark: | A friend ordered a couple of these and it turned out they only needed one, so they gave me the spare. It replaced a CC2530 with antenna, and so far, so good. The sign of a good router device is that you forget about it after all :P |
| [CR Smart Home TS0207](https://www.zigbee2mqtt.io/devices/TS0207_water_leak_detector.html) | Leak sensor | :thumbsdown: | Bought one to test it out, and it works exactly as described. Ordered a few more for around the house. The downside is battery life is ... shockingly bad. |
| [Gledopto GL-C-008P](https://www.zigbee2mqtt.io/devices/GL-C-008P.html) | Hall light | :heavy_check_mark: | Replaced the older GL-C-008, transitions are smoother, but otherwise it behaves much like the old unit. I use this with a strip of 24V RGB-CCT tape for some lighting in the hall, which is otherwise quite dark. I may replace the tape with COB tape |
| [IKEA LED1733G7](https://www.zigbee2mqtt.io/devices/LED1733G7.html#ikea-led1733g7) | Light | :heavy_check_mark: | I bought a couple of these for background lighting in the living room. I have no complaints about them, they transition smoothly, have a good range of brightness, and are cheap. NB: I'm not 100% sure these are Zigbee 3.0. |
| [Ikea LED1739R5](https://www.zigbee2mqtt.io/devices/LED1537R6_LED1739R5.html#ikea-led1537r6%252Fled1739r5) | Light | :heavy_check_mark: | This was bought to replace the Osram, and it does this well. My comments for the other Ikea lights apply here too. |
| [Innr SP222](https://www.zigbee2mqtt.io/devices/SP_222.html) | Router and socket | :heavy_check_mark: | Some purely function as a (Zigbee 3.0) router, it doesn't do power monitoring, but it is compact and has local control. I'm use some of these to replace old Z-Wave sockets, for things like our Christmas lighting. |
| [Konke contact sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPDR.html) | Doors | :thumbsdown: | These are neat, slightly smaller than the Xiaomi sensors, but visually not as nice. They also seem to eat batteries and fail without warning. |
| [Konke motion sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPBS.html) | Motion sensor | :thumbsdown: | These are neat, smaller than the Xiaomi sensors, and visually quite nice. They also seem to eat batteries and fail without warning. |
| [Konke temperature sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPFT.html) | Temperature and humidity | :thumbsdown: | These are neat, smaller than the Xiaomi sensors, but visually not as nice. |
| [Linkind motion sensor](https://www.zigbee2mqtt.io/devices/ZS1100400-IN-V1A02.html) | Motion | :heavy_check_mark: | Nice, responsive motion sensors. They do need to be on a wall or on the edge of a piece of furniture, but that's the only downside. |
| [Lidl light strip](https://www.zigbee2mqtt.io/devices/HG06104A.html) | Office light | :grey_question: | Not a bad strip, doesn't go that dim, but it works pretty well and isn't expensive. |
| [TERNCY-DC01](https://www.zigbee2mqtt.io/devices/TERNCY-DC01.html) | Windows | :heavy_check_mark: | It wouldn't pair with my ZZH, but paired fine with my Sonoff coordinator. Small, responsive, and Zigbee 3.0, what's not to like? A little more expensive than the Xiaomi sensors, but far easier to buy. | 
| [TERNCY-SD01](https://www.zigbee2mqtt.io/devices/TERNCY-SD01.html) | Remote | :heavy_check_mark: | In use as a [media controller in the office](https://github.com/DubhAd/Home-AssistantConfig/blob/live/automation/office/office_dial.yaml), controlling the volume and pause/play. There's a very slight (unavoidable) delay in the clicks, since it supports single, double, and triple clicks, but it's otherwise a great device. |
| [Xiaomi E1 remote](https://www.zigbee2mqtt.io/devices/WXKG16LM.html) | Remote | :heavy_check_mark: | Bought to replace a Z-Wave wall switch, and it's a great replacement. |
| [Xiaomi Mijia light sensor](https://www.zigbee2mqtt.io/devices/GZCGQ01LM.html) | Light levels | :heavy_check_mark: | This is a very reponsive, well behaved light sensor. If you're looking for one, I'd recommend this one. | 
| [Xiaomi MCCGQ14LM door sensor](https://www.zigbee2mqtt.io/devices/MCCGQ14LM.html) | Doors/Windows | :heavy_check_mark: | The Zigbee 3.0 version of their popular door/window sensor. It's working well for me so far. | 
| [Xiaomi P1 presence sensor](https://www.zigbee2mqtt.io/devices/RTCGQ14LM.html) | Motion sensor | | The Zigbee 3.0 version of their popular motion sensor. Others have complained about the range, but so far I'm happy. |

**Notes**
- There's a known bug with the version of the firmware used on the Ikea devices, which impacts other devices too, that causes them to stop routing traffic. I've not experienced this myself, but others have reported it.
- The Konke devices are fairly nice, the only problem is that they work on three out of the twenty-six channels. Oh, and they seem to chew batteries - not as bad as the Tuya devices, but a lot faster than Xiaomi.

### Not in use
| What | Buy again? | Notes |
| --- | :---: | --- |
| [Konke button](https://www.zigbee2mqtt.io/devices/2AJZ4KPKEY.html) | :thumbsdown: | These are neat, smaller than the Xiaomi button, but not as nice to use. |
| [Lidl power socket](https://www.zigbee2mqtt.io/devices/HG06337.html) | :warning: | Quite a good socket, a little bulky, but it does power monitoring. Sadly it constantly dropped off the mesh and reconnected, so I removed it. |
| Sleash | Router | Worked as a router, currently in the drawer. |
| [TERNCY-PP01](https://www.zigbee2mqtt.io/devices/TERNCY-PP01.html) | | Combined motion, light, temperature sensor, and a button. It's huge and I haven't yet tried it on the new coordinator |
| [YSRSAI YSR-MINI-01_rgbcct](https://www.zigbee2mqtt.io/devices/YSR-MINI-01_rgbcct.html) | | A compact controller with what looks like local control. Sadly it takes a slightly non-standard connector for the LED strips, so I'm waiting on something coming so I can use it. |

## Zigbee 1.2 and older

| What | Function | Buy again? | Notes |
| --- | --- | :---: | --- |
| [Develco Motion Sensor Mini](https://www.zigbee2mqtt.io/devices/MOSZB-140.html) | Multi-sensor | :grey_question: | Pretty good multi sensor. A touch large, but it does take AA batteries. |
| [Hue dimmer](https://www.zigbee2mqtt.io/devices/324131092621.html) | Remote | :grey_question: | Quite nice four button remote, the only downside is that it's not Zigbee 3.0 |
| [Xiaomi Aqara button](https://www.zigbee2mqtt.io/devices/WXKG12LM.html) | Remote | :pause_button: | I like these, they feel good and work well, but it's only Zigbee 1.2 |
| [Xiaomi Aqara cube](https://www.zigbee2mqtt.io/devices/MFKZQ01LM.html) | Remote | :pause_button: | Fun toys. One was used to pause and play music in my office, but replaced by the Terncy dial, the other controls lighting |
| [Xiaomi Aqara door/window sensor](https://www.zigbee2mqtt.io/devices/MCCGQ11LM.html) | Doors and windows | :pause_button: | I have a stack of those, one for every exterior window, and a few on interior doors. They're cheap, compact, don't stand out visually, and just work. The T1 versions are the new Zigbee 3.0 versions, that are really hard to get. |
| [Xiaomi Aqara motion sensor](https://www.zigbee2mqtt.io/devices/RTCGQ11LM.html) | Motion | :pause_button: | These are ok, not great, but ok. There is an on board light sensor, but it only reports light levels when motion is detected | 
| [Xiaomi Aqara temperature sensor](https://www.zigbee2mqtt.io/devices/WSDCGQ11LM.html) | Temperature and humidity | :pause_button: | These are pretty good, they report regularly enough to be useful and are reliable. Hopefully we'll get a Zigbee 3.0 version soon. |
| [Xiaomi Aqara vibration sensor](https://www.zigbee2mqtt.io/devices/DJT11LM.html) | Chest freezer | :pause_button: | Sits on the lid of my chest freezer, where it helps tell us if the lid is closed or not. |
| [Xiaomi Aqara water leak sensor](https://www.zigbee2mqtt.io/devices/SJCGQ11LM.html) | Leak Sensor | :pause_button: | These are pretty good, the only downside is they're not Zigbee 3.0. |
| [Xiaomi D1 remote](https://www.zigbee2mqtt.io/devices/WXKG06LM.html) | Remote | :small_red_triangle: | Bought initially to replace a Z-Wave switch, but if it's asleep then the first press simply wakes it and does nothing. |

**Notes**
- Aqara's E1, P1, and T1 ranges are Zigbee 3.0, but they're often hard to get a hold of outside of China.

### Not in use
| What | Buy again? | Notes |
| --- | :---: | --- |
| CC2531 | :warning: | It worked for a small mesh, mostly. It isn't a great choice though so I'm migrating to the Zig-A-Zig-Ah! |
| [Gledopto GL-C-008 RGB+CCT](https://www.zigbee2mqtt.io/devices/GL-C-008-1ID.html) | :small_red_triangle: |  I use this with a strip of 24V RGB-CCT tape for some lighting in the hall, which is otherwise quite dark. I plan on swapping this out for the Zigbee 3.0 version, and probably replacing the tape with COB tape |
| [Hive active plug](https://www.zigbee2mqtt.io/devices/1613V.html) | :thumbsdown: | Worked well, but  slightly bulky and also not Zigbee 3.0 |
| [Ikea router](https://www.zigbee2mqtt.io/devices/E1746.html) | :thumbsdown: | Purely functioned as a router for the original mesh, but I don't need it any more, and it only routes for a handful of devices |
| [Osram smart bulb](https://www.zigbee2mqtt.io/devices/AC08560-DIM.html) | :warning: | This was a pain to include, and worked fine for a while. Then one day it fell off the mesh and refused to either reconnect or reset. Then I found out that problems are normal with this brand... |
| [Salus SP600](https://www.zigbee2mqtt.io/devices/SP600.html) | :thumbsdown: | A pretty good socket, with power monitoring, but it's only Zigbee 1.2 |

# Z-Wave - not in use

| What | Thoughts |
| --- | --- |
| [Razberry board](https://razberry.z-wave.me/) | It does avoid having to use a USB socket, but my Z-Wave mesh could only run from the Pi |
| Aeotec MultiSensor 6 | Excellent all around multi-sensor with a bonus of being USB powered |
| Fibaro FGK10x | Fairly unobtrusive door sensors I used for the garage doors, which have support for external sensors too. They're not made any more, and have been replaced with Zigbee sensors that perform so much better. |
| Fibaro MultiSensor | Pretty good multi-sensor. Doesn't do humidity unlike the Aeotec, and can chew through batteries like there's no tomorrow though. I replaced it with some Zigbee sensors. |
| Foxx Smart Switch G5 | Basically a Gen5 Aeotec socket. Worked well and was cheaper than the TKB. |
| NodOn Octan | Great little four button remote, which sadly is discontinued. Replaced by a Xiaomi cube. |
| NodOn Soft Remote | A brightly coloured, kid proof four button remote, that's also discontinued. Replaced by voice control. |
| [Sensative strips](https://sensative.com/sensors/strips-zwave/guard/) | Awesome sensors that fit inside the door (or window) frame. You can't replace the battery, but they claim a 10 year lifespan, which is in line with my experiences so far. The fastest any died was in 8 years, on a door used dozens of times a day. |
| TKB TZ69E | Smart switch with power monitoring. I used these for the garden lights, and a range of interior sockets. Slightly bulky, but rather good. |
| Z-Wave.me WALLC-S | Looks like a normal light switch, and was _Associated_ with the TKB socket for the garden lights, this allowed us to turn the lights on and off manually when required. Discontinued. |

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

