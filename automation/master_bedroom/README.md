# Automations, automations everywhere, and all the brains did hurt

Documentation: [automation](https://home-assistant.io/docs/automation/)

_Some of these were first written when I started with HA, and didn't know better. You'll find that I've used hyphens (-) in some file names and underscores (\_) to match Home Assistant in others. Mostly I'm not renaming files._


## Master bedroom 

### Bedhead light

#### person2-up-bedhead-light-on.yaml

When the alarm goes off, turn on the bedhead light to help with the wake up. This is triggered by either the Squeezebox Radio playing, or the Home Mini playing music. 

#### person2-up-bedhead-light-off.yaml

Turns the bedhead light off 30 minutes after the alarm stops.

#### late_disable_fluxer.yaml

Turns off fluxer at 23:00

---

These automations control the brightness, depending on the time of day/night - details to follow

#### bedhead-light-bright-sunrise.yaml
#### bedhead-light-dim-2.yaml
#### bedhead-light-dim-late-2.yaml
#### bedhead-light-dim-late.yaml
#### bedhead-light-dim-midnight-2.yaml
#### bedhead-light-dim-midnight.yaml
#### bedhead-light-dim-sunset-2.yaml
#### bedhead-light-dim-sunset.yaml
#### bedhead-light-dim.yaml
#### bedhead-light-left-on.yaml
#### bedhead_light_on_morning.yaml
#### bedhead-light-on-night.yaml

---

These are triggered by the Z-Wave remote - details to follow

#### bedhead_turn_off.yaml
#### bedhead_turn_on_cool.yaml
#### bedhead_turn_on_max.yaml
#### bedhead_turn_on_min.yaml
#### bedhead_turn_on_red.yaml
#### bedhead_turn_on_warm.yaml
#### bedhead_turn_on.yaml
#### bedhead_turn_red.yaml
#### bedhead_turn_white_max.yaml
#### bedhead_turn_white.yaml
#### master_bedhead_bright_stop.yaml
#### master_bedhead_bright.yaml
#### master_bedhead_cool_stop.yaml
#### master_bedhead_cool.yaml
#### master_bedhead_dim_stop.yaml
#### master_bedhead_dim.yaml
#### master_bedhead_warm_stop.yaml
#### master_bedhead_warm.yaml
