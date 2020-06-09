# Automations, automations everywhere, and all the brains did hurt

Documentation: [automation](https://home-assistant.io/docs/automation/)

_Some of these were first written when I started with HA, and didn't know better. You'll find that I've used hyphens (-) in some file names and underscores (\_) to match Home Assistant in others. Mostly I'm not renaming files._

## The living room (or lounge)

The automations here got unwieldy as things grew. I decided to stop duplicating logic, and simplified things (of sorts)

### living_room_occupied.yaml

These automations are used to determine if the room is occupied. At the heart is the basic concept that if the media devices (TV, music player, etc) are active, then somebody's in the room. Except, of course, that the darn TV wakes up in the night for a couple of minutes to do a software update check.

Triggered by

* Any of the media devices being active for 5 minutes
* Any of the media devices becoming active
* There's motion

The conditions are:

* We're home, or guest mode is active
* The media devices are active *and* one of the following is true
  * There was motion in the last 3 minutes
  * The media devices have been active for 5 minutes

### living_room_not_occupied.yaml

Triggered by all the media devices have been off for three minutes.

### living_room_away.yaml

The living room turns to Away when it's no longer occupied, we're away, and guest mode is off.

### living_room_day_on.yaml

Day mode and on when the light starts getting dull, the room is occupied, and either we're home or guest mode is on.

### living_room_day_off.yaml

Day mode and off during the day when the room becomes brighter, and either we're home or guest mode is on.

### living_room_night_on.yaml

Night mode and on when the room gets dark, it's occupied, and either we're home or guest mode is on. 

### living_room_night_off.yaml

Triggered by the sun going below the horizon, or no longer being occupied

Requires:

* The room to not be occupied
* The sun to be below the horizon, or the room is set to _Night on_
* We're home, or guest mode is on

### living_room_lights_day_on.yaml

Turns a subset of the lights on when the room turns to _Day on_

### living_room_lights_night_on.yaml

Turns all the background lighting on when the room turns to _Night on_

### living_room_lights_off.yaml

Turns all the lights off when the room turns to _Night off_ or _Day off_

### lounge_dark_motion.yaml

If the room is dark, not occupied, and the lights are off, turn on the lights when there's motion. This also sets an input boolean (`input_boolean.livingroom_lights_auto`) to indicate we've turned them on automatically.

### table_light_on.yaml

Two minutes after the motion stops, if we turned the lights on automatically, turn them off.

### tv-on-sonos-off.yaml

When the TV turns on, if the Sonos is playing, pause it.

### sonos_on_tv_mute.yaml

If the TV is on when the Sonos starts playing, mute the TV.

### sonos_off_tv_unmute.yaml

Unmute the TV if it's on when we stop playing music on the Sonos.
