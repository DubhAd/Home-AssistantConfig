# Automations, automations everywhere, and all the brains did hurt

There's some "not simple" home and away logic in here.

## Away 

Four triggers:
1. The phone is at least 400 meters away
2. The phone is at least 800 meters away
3. Any device goes to `not_home`
4. Home Assistant starts
```
trigger:
  - platform: numeric_state
    entity_id: proximity.person1_home
    above: 400
  - platform: numeric_state
    entity_id: proximity.person1_home
    above: 800
  - platform: state
    entity_id: 
      - device_tracker.3c_28_6d_da_eb_a1
      - device_tracker.person1_bt_mobile
      - device_tracker.person1_bt_front_mobile
    to: 'not_home'
  - platform: homeassistant
    event: start
```

The conditions are "simple":
1. At least two of the local trackers show away; and
2. Either
   1. A door recently opened/closed
   2. All trackers are away and proximity shows the phone is at least 400 meters away
   3. Proximity shows the phone is at least 800 meters away

```
condition:
  # As long as at least two trackers mark as away, they're away
  - condition: numeric_state
    entity_id: group.person_person1
    below: 2
    value_template: "{{ dict((states|selectattr('entity_id', 'in', state_attr('group.person_person1', 'entity_id'))|list)|groupby('state'))['home']|count }}"
  # Either an exit door recently opened/closed, or we're far far away
  - condition: or
    conditions:
    # An exit door recently opened or closed, or motion in the vestibule
    - condition: template
      value_template: >-
        {{ ((as_timestamp(now()) - as_timestamp(states.binary_sensor.pi3_front_door_sensor.last_updated)) | int < 300) 
          or 
           ((as_timestamp(now()) - as_timestamp(states.binary_sensor.pi3_garage_closed_car_sensor.last_updated)) | int < 300) 
        }}
    # All away, and not near
    - condition: and
      conditions:
      - condition: state
        entity_id: group.person_person1
        state: 'not_home'
      - condition: numeric_state
        entity_id: proximity.person1_home
        above: 400
    # Far far away (land)
    - condition: numeric_state
      entity_id: proximity.person1_home
      above: 800
```

All the actions are in a script
```
action:
  - service: script.person1_away
```

## Home


Arriving home is based on two triggers - a state trigger of any device arriving home, or HA starting
```
initial_state: 'on'
alias: 'person1 home'
trigger:
  - platform: state
    entity_id: 
      - device_tracker.3c_28_6d_da_eb_a1
      - device_tracker.person1_bt_mobile
      - device_tracker.person1_bt_front_mobile
    to: 'home'
  - platform: homeassistant
    event: start
```

A simple requirement, is at least one device is home. This means that returning home is a quick detection.
```
condition:
  - condition: numeric_state
    entity_id: group.person_person1
    above: 0
    value_template: "{{ dict((states|selectattr('entity_id', 'in', state_attr('group.person_person1', 'entity_id'))|list)|groupby('state'))['home']|count }}"
```

I do all the "arrived home" logic in a script.
```
action:
  - service: script.person1_home
```	
