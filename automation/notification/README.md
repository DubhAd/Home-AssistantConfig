# Automations, automations everywhere, and all the brains did hurt

Documentation: [automation](https://home-assistant.io/docs/automation/)

## Notifications

These are notifications for things people should be aware of - mostly this is background stuff.

### bin_notification.yaml

Uses the bin sensors to send a notification to the LaMetric clock the day before the recycling is due to be collected. It is pushed every 5 minutes, at 30 seconds past the minute.

### weather_notification.yaml

Sends a notification about the forthcoming weather conditions to the LaMetric clock every 5 minutes.
