# Scripts

Component: [script](https://home-assistant.io/components/script/)

## Alarm

These aren't used yet, there for use with the [manual alarm](https://home-assistant.io/components/alarm_control_panel.manual/), or not.

## Bedhead light

These came to life when somebody in Discord asked for help using a Z-Wave remote to control the brightness of a smart bulb, and that first iteration ended up [in the cookbook](https://home-assistant.io/cookbook/dim_and_brighten_lights/). This moved on from that though to also control the warmth of the light.

## Bedtime

Because at bedtime you don't want everything to turn off at once and leave you in the dark, half way up the stairs, with pets moving around underfoot... It basically does a staged turning off of the various lights, leaving enough time to get to bed before the lights go out.

## Garden

This is to allow us to open and close the door to let the dog out, and have the garden lights come on, and stay on. We only use the *after sunset* script, because I now use the sun elevation to trigger the automations that call the script.

Basically, when we open the door after dark, this:

* Turns off the "turn off the lights when the door closes" automation
* Turns on the garden lights
* Waits for a delay (in seconds) defined by an input number
* Turns the "turn off the lights when the door closes" automation back on

## Notifications

Some scripts for notifications

## People

* The actions for the home and away automations for each person is now a script
* Some people in this house are hard to wake. This is to ensure that they get up, by controlling lights and speakers

## Scan

Triggers scans by monitor
