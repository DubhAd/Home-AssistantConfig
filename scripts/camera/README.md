# Scripts

Components:

* [script](https://home-assistant.io/integrations/script/)
* [Doods](https://www.home-assistant.io/integrations/doods/)
* [Discord](https://www.home-assistant.io/integrations/discord/)

I'm experimenting with Doods, to see if it can help me with motion detection at the front of the house.

I use [Motion](https://motion-project.github.io/) (bundled as part of [MotionEye](https://github.com/ccrisan/motioneye) for motion detection at the front of the house. This works well enough, but the layout means I get some false detections, usually due to lighting (security lights, headlights, etc), but sometimes also due to birds, cats, and other animals. I'm testing out Doods, with the full tensorflow models, to see if I can get reliable notifications about only the things I'm interested in (signs of human activity).

For four of the things I'm interested in are easy, I just have to see if they've been found and provide a summary:

```
        {%- if "person" in state_attr('image_processing.doods_front_camera','matches') %}
          {{ state_attr('image_processing.doods_front_camera','summary').person }} people ({%- for state in state_attr('image_processing.doods_front_camera','matches').person %}{{ state.score|round(0) }}% at {{state.box}}{%- if loop.last %}{% else %}, {% endif %}{% endfor %})
        {% endif %}
        {%- if "truck" in state_attr('image_processing.doods_front_camera','matches') %}
          {{ state_attr('image_processing.doods_front_camera','summary').truck }} truck(s) ({%- for state in state_attr('image_processing.doods_front_camera','matches').truck %}{{ state.score|round(0) }}%{%- if loop.last %}{% else %}, {% endif %}{% endfor %})
        {% endif %}
        {%- if "motorcycle" in state_attr('image_processing.doods_front_camera','matches') %}
          {{ state_attr('image_processing.doods_front_camera','summary').motorcycle }} motorcycle(s) ({%- for state in state_attr('image_processing.doods_front_camera','matches').motorcycle %}{{ state.score|round(0) }}%{%- if loop.last %}{% else %}, {% endif %}{% endfor%})
        {% endif %}
        {%- if "bicycle" in state_attr('image_processing.doods_front_camera','matches') %}
          {{ state_attr('image_processing.doods_front_camera','summary').bicycle }} bicycle(s) ({%- for state in state_attr('image_processing.doods_front_camera','matches').bicycle %}{{ state.score|round(0) }}%{%- if loop.last %}{% else %}, {% endif %}{% endfor %})
        {% endif %}
```

Cars are trickier, I don't need to be told about my parked cars, so I'm trying to "tune" those out. This is where macros come in handy (something that [ludeeus](https://github.com/ludeeus) and [skalavala](https://github.com/skalavala) introduced me to). 
```
        {%- if "car" in state_attr('image_processing.doods_front_camera','matches') %}
          # Define a macro that checks to see if a car has been found in either of the two spaces
          {%- macro isParkedCar(box) -%}
          {{- True if (
              ((0.724 < box[0] < 0.754) and (0.442 < box[1] < 0.553) and (0.820 < box[2] < 0.850) and (0.518 < box[3] < 0.680))
               or
              ((0.750 < box[0] < 0.756) and (0.548 < box[1] < 0.573) and (0.840 < box[2] < 0.854) and (0.665 < box[3] < 0.680))
            ) else X -}}
          {%- endmacro -%}
          # Define a macro, that uses the above macro, to count the number of parked cars found
          {%- macro getParkedCars() -%}
          {%- for state in state_attr('image_processing.doods_front_camera','matches').car -%}{{- "X" if isParkedCar(state.box) -}}{%- endfor -%}
          {%- endmacro -%}
          # Now work out how many of the cars are parked, vs other
          {%- set parkedCars = getParkedCars()|length -%}
          {%- set otherCars = state_attr('image_processing.doods_front_camera','summary').car - parkedCars -%}
          # Produce a nice message about the cars we found
          {% if otherCars > 0 and parkedCars > 0 %} {{otherCars}} cars and {{parkedCars}} parked{% elif parkedCars > 0 %} {{parkedCars}} parked cars{% else %} {{otherCars}} cars{% endif %}
          # Details about each car found
          ({%- for state in state_attr('image_processing.doods_front_camera','matches').car %}{% if isParkedCar(state.box) %}parked ({{ state.score|round(0) }}% confidence at {{state.box}}){% else %}moving ({{ state.score|round(0) }}% confidence at {{state.box}}){% endif %}{%- if loop.last %}{% else %}, {% endif %}{% endfor %})
        {% endif %}
```

I'm including the box in the location so that I can continue to tune the detections for the locations. Once I'm happy (if I'm ever happy) I'll eventually end up with Home Assistant not notifying me unless it detects something of interest.
