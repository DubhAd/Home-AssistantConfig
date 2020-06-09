# Input booleans

Component: [input boolean](https://home-assistant.io/components/input_boolean/)

Some of these are used to enable and disable automations, some are used to track whether something is in a particular state (and then trigger automations).

## Adults

A simple toggle for when the adults are away, since we'll want different things to happen then.

## Alarm

Now I'm using the manual alarm control panel, I don't need this any more.

## All 

A simple toggle for when we're all away. This is mostly for things like lighting control, for now. It will be replaced by `input_boolean.home_occupied`

## Bedtime

If it's bedtime then it's time to turn off lights. If it's no longer bedtime, and it's still dark, it's time to turn some on.

## Guest mode

When we've got guests around certain behaviours need to be different, this is a manual toggle to control that.

## Holiday mode

If we're all away then some automations we'll simply not want running (and others that we wouldn't want running when we're home we would). This is to control those.

## Lighting

Just in case we ever want to disable the lighting automations, this will control that.

## Rooms

* There's a toggle to indicate that the living room lights were turned on automatically
* Each room has one to indicate whether it's occupied 

## Notifications

To track whether it's a work/school/whatever day for people and nag them about key things.

Also controls whether to notify about the train status.

## People

Various people related booleans

### Awake

These are the indicators of whether people are (probably) asleep or awake, or in bed. These feed in to various automations.

### Home

Simple binary home/away indicators for people, plus one for the house as a whole.

### Travelling

These are used to indicate whether people are on an extended trip. These feed in to the Holiday mode, and will eventually feed in to things like chosing which notifiers get used, and other things.

