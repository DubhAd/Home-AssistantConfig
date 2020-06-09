# Binary sensors

Components:
* [bayesian binary sensor](https://home-assistant.io/components/binary_sensor.bayesian/)
* [binary sensor](https://home-assistant.io/components/binary_sensor/)
* [template binary sensor](https://home-assistant.io/components/binary_sensor.template/)
* [trend binary sensor](https://www.home-assistant.io/components/binary_sensor.trend/)
* [workday binary sensor](https://home-assistant.io/components/binary_sensor.workday/)

A summary of the sensors, and what they're for

## Garden

This is to allow me to use an input_select to control when the garden lights turn off automatically.

## Living room

A simple template sensor [as documented here](https://home-assistant.io/docs/z-wave/entities/#burglar-entity) to turn my non-binary reporting Z-Wave sensor into a binary sensor.

## MQTT

These report whether the [monitor](https://github.com/andrewjfreyer/monitor) instances are online or not.

## Trains

Using the [UK Transport](https://home-assistant.io/components/sensor.uk_transport/) sensor to say whether the trains for the commute are running on time. Not used in any automations right now.

## Trend

Some simple trend sensors to track:
* Whether the sun is rising or setting - this is used in the lighting automations
* If the light level is generally increasing or decreasing - again used in the lighting automations

## Workday

Standard [workday sensor](https://home-assistant.io/components/binary_sensor.workday/)
