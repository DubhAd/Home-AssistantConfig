# Automations, automations everywhere, and all the brains did hurt

Documentation: [automation](https://home-assistant.io/docs/automation/)

## The garden

We've a mains voltage LED strip, controlled by a Z-Wave socket

### garden_lights_left_on.yaml

This uses `binary_sensor.garden_lights_left_on` to determine if the lights were left on in error. If they were and the door is shut, turn off the lights immediately. If they've been left on and the door is open, turn off the lights 10 minutes later.

If we want the lights left on, it's a simple click to disable.

### nighttime_garden_off.yaml

The precursor to the above automation. Disabled and I'll be culling it eventually.

### utility-door-sunset-on.yaml

When the utility (or patio) door opens after dusk, and the lights are off, turn the lights on using [`script.garden_door_after_sunset`](https://github.com/DubhAd/Home-AssistantConfig/tree/master/scripts#garden). 

### utility-door-sunset-off.yaml

Turn the garden lights off when the utility door closes. The script mentioned above turns this automation off for the number of seconds defined in `input_number.door_delay`, which defaults to 8. That means you can open the door to let the dog out and the lights stay on, but if you're going to the bin then those 8 seconds will have passed, and the lights will turn off when you close the door.

### utility-door-sunset-closed.yaml

This turns on the off automation one second after the door closes.
