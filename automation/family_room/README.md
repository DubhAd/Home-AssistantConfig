# Automations, automations everywhere, and all the brains did hurt

Documentation: [automation](https://home-assistant.io/docs/automation/)

## Family room

I used to track this in the individual automations, but it was getting silly, so now room occupancy is recorded in an input boolean

### `family_room_occupied.yaml`

The room is considered occupied if:

* Some media device is playing or the TV is on
* We're home, or guest mode is enabled

### `family_room_not_occupied.yaml`

The room is considered not occupied if:

* All the media devices are off
