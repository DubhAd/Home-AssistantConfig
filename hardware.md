This is a list of the various pieces of hardware I use, or have used, with Home Assistant, along with my take on them.

## Buy again notes:

| Symbol | Means |
| ---: | --- |
| :heavy_check_mark: | Yes |
| :grey_question: | Maybe - it's not bad, but I may find something better |
| :construction: | Waiting on the next generation of this - typically that means it's good, but not Zigbee 3.0 |
| :x: | Unlikely, it's not terrible, but it has issues |
| :warning: | No, just no |

# Zigbee

| What | Function | Buy again? | Zigbee generation | Notes |
| --- | --- | :---: | :---: | --- |
| CC2531 | Coordinator | :x: | :one: | It worked for a small mesh, mostly. It isn't a great choice though so I'm replacing it |
| [Zig-A-Zig-Ah!](https://www.tindie.com/products/electrolama/zzh-cc2652r-multiprotocol-rf-stick/) | Coordinator | :heavy_check_mark: | :three: | The replacement coordinator. Currently on the 202101 firmware, and proving solid and stable. |
| Sleash | None | :warning: | :three: | I flashed this with router firmware, and it joined the mesh, then fell off. I'll revisit this in the future, but so far, I'm unimpressed |
| [Xiaomi Mijia light sensor](https://www.zigbee2mqtt.io/devices/GZCGQ01LM.html) | Light levels | :heavy_check_mark: | :three: | This is a very reponsive, well behaved light sensor. If you're looking for one, I'd recomend this one. | 
| [Innr SP222](https://www.zigbee2mqtt.io/devices/SP_222.html) | Router | :grey_question: | :three: | Purely functions as a (Zigbee 3.0) router, it doesn't do power monitoring, but it is compact and has local control |
| [Xiaomi Aqara door/window sensor](https://www.zigbee2mqtt.io/devices/MCCGQ11LM.html) | Doors and windows | :construction: | :one: | I have a stack of those, one for every exterior window, and a few on interior doors. They're cheap, compact, don't stand out visually, and just work. The T1 versions are the new Zigbee 3.0 versions, that are really hard to get. |
| [Xiaomi Aqara motion sensor](https://www.zigbee2mqtt.io/devices/RTCGQ11LM.html) | Motion | :construction: | :one: | These are ok, not great, but ok. There is an on board light sensor, but it only reports light levels when motion is detected | 
| [Xiaomi Aqara temperature sensor](https://www.zigbee2mqtt.io/devices/WSDCGQ11LM.html) | Temperature and humidity | :construction: | :one: | These are pretty good, they report regularly enough to be useful and are reliable. |
| [Xiaomi Aqara button](https://www.zigbee2mqtt.io/devices/WXKG12LM.html) | Remote | :construction: | :one: | I like these, they feel good and work well |
| [Hue dimmer](https://www.zigbee2mqtt.io/devices/324131092621.html) | Remote | :grey_question: | :one: | Quite nice four button remote, the only downside is that it's not Zigbee 3.0 |
| [Konke contact sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPDR.html) | Doors | :x: | :three: | These are neat, slightly smaller than the Xiaomi sensors, but visually not as nice. The main downside is that it supports three channels, out of 26... |
| [Konke motion sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPBS.html) | Motion sensor | :x: | :three: | These are neat, smaller than the Xiaomi sensors, and visually quite nice. The main downside is that it supports three channels, out of 26... |
| [Konke temperature sensor](https://www.zigbee2mqtt.io/devices/2AJZ4KPFT.html) | Temperature and humidity | :x: | :three: | These are neat, smaller than the Xiaomi sensors, but visually not as nice. The main downside is that it supports three channels, out of 26... |
| [Konke button](https://www.zigbee2mqtt.io/devices/2AJZ4KPKEY.html) | Remote | :x: | :three: | These are neat, smaller than the Xiaomi button, but not as nice to use. The main downside is that it supports three channels, out of 26... |
| [Lidl light strip](https://www.zigbee2mqtt.io/devices/HG06104A.html) | Light | :grey_question: | :three: | Not a bad strip, doesn't go that dim, but it works pretty well and isn't expensive. |
| [Hive active plug](https://www.zigbee2mqtt.io/devices/1613V.html) | Controlling an uplighter | :x: | :one: | This both extends my mesh, and also manages a dumb uplighter that I'll fit a smart bulb to at some point, again |
| [Salus SP600](https://www.zigbee2mqtt.io/devices/SP600.html) | Router | :x: | :one: | A pretty good socket, with power monitoring, but it's only Zigbee 1.2 |
| [Gledopto GL-C-008 RGB+CCT](https://www.zigbee2mqtt.io/devices/GL-C-008-1ID.html) | Hall lighting | :construction: | :one: |  I use this with a strip of 24V RGB-CCT tape for some lighting in the hall, which is otherwise quite dark. I plan on swapping this out for the Zigbee 3.0 version, and probably replacing the tape with COB tape |
| [Ikea router](https://www.zigbee2mqtt.io/devices/E1746.html) | Router | :x: | Unsure | Purely functions as a router for the original mesh, but I don't need it any more |
| [Lidl power socket](https://www.zigbee2mqtt.io/devices/HG06337.html) | None | :warning: | :three: | Quite a good socket, a little bulky, but it does power monitoring. Sadly it constantly drops off the mesh and reconnecting |
| [Osram smart bulb](https://www.zigbee2mqtt.io/devices/AC08560-DIM.html) | None | :warning: | :one: | This was a pain to include, and worked fine for a while. Then one day it fell off the mesh and refused to either reconnect or reset. Then I found out that problems are normal with this brand... |

# Z-Wave

| What | Function | Thoughts |
| --- | --- | --- |

# Other

| What | Function | Thoughts |
| --- | --- | --- |
