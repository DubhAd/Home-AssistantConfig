# Intent scripts

Component: [intent script](https://home-assistant.io/components/intent_script/)

For use with [Dialogflow](https://home-assistant.io/components/dialogflow/), allowing (in theory) more natural voice control. In reality with [Google Assistant](https://home-assistant.io/components/google_assistant/) it's a pain, because you have to go _Hey Google, talk to Home Assistant_, then have your conversation with Dialogflow, then end that...

These are mostly taken directly from the examples, so there's nothing exciting.

## Locate

Says where people are - uses the custom sensor for each person, so that we get the zone, or the travel time to home

## Outside doors

In theory says what doors are open, doesn't work though

## Temperature

Reports the temperature from the living room sensor - Google Assistant can now do this directly

## Turn lights on/off

Supposed to turn the lights on and off, though it doesn't work

## Where are we

Uses the custom sensor again to report which zone we're all in, or how far we are from home
