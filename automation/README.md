# Automations, automations everywhere, and all the brains did hurt

Documentation: [automation](https://home-assistant.io/docs/automation/)

_Some of these were first written when I started with HA, and didn't know better. You'll find that I've used hyphens (-) in some file names and underscores (\_) to match Home Assistant in others. Mostly I'm not renaming files._

Most of these have been split into sub-folders, except for these

### bedtime.yaml

Sets the input boolean called `bedtime` when everybody's asleep.

### house_awake.yaml

Clears the input boolean called `bedtime` when somebody wakes up.

### printer_low.yaml

We have a laser printer, since we print so little that an inkjet is always clogging. This warns us when it starts to run low.

---

### all_away_media_off.yaml

This hasn't ever been enabled, but the idea is that if we've left home, and it's not in guest mode, this would turn off any media players left on

