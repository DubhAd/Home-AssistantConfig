# Automations, automations everywhere, and all the brains did hurt

Documentation: [automation](https://home-assistant.io/docs/automation/)

_Some of these were first written when I started with HA, and didn't know better. You'll find that I've used hyphens (-) in some file names and underscores (\_) to match Home Assistant in others. Mostly I'm not renaming files._

## Office

I work from home at times, and have the pleasure of having set aside the smallest bedroom to function as my home office.

### office_occupied.yaml

If the work laptop comes online, then the office is assumed to be occupied. This is pretty reliable, since I only connect it to the wired network, and there's nowhere else to hook it up.

### office_not_occupied.yaml

When the work laptop goes offline for 2 minutes, then the office is no longer occupied.

### play_classical_music_in_the_office.yaml

So nice being able to listen to music while working. This plays music when the office becomes occupied.

### pause_music_in_the_office.yaml

While it's great listening to music while you work, not so great when on a phone call. When my work calendar shows I'm busy, and music is currently playing, pause the music.

### resume_music_in_the_office.yaml

When the meeting ends, if I didn't already start playing the music manually, start it playing again.

### stop_classical_music_in_the_office.yaml

Finally, at the end of the day when the office is no longer occupied, turn off the music.
