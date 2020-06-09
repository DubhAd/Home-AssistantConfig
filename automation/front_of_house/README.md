# Automations, automations everywhere, and all the brains did hurt

Documentation: [automation](https://home-assistant.io/docs/automation/)

## The front of the house

We've got a light by the house number, to illuminate it and make the house easier to find.

### number-sign-off.yaml

Turns the number sign off light at:

* Sunrise
* Midnight (in the theory that we're unlikely to have any visitors after midnight)

### number-sign-on-evening.yaml

Turns the number sign light on at sunset.

### number-sign-on-morning.yaml

Turns the number sign light on at 06:00, as long as that's before sunrise

### person2-up-early.yaml

If they get up before sunrise, turn on the number sign. Probably if this happens a taxi is coming.

### Doors

These automations call scripts to tell monitor to scan for arriving or departing Bluetooth devices.
