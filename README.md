# HA_radiator_pump
 Using Home Assistant to control a radiator pump state using the radiator thermostat heating state

Hardware: 
I have around 10 Tado radiator thermostats scattered throughout the house. I have a heat pump that can switch between DHW and the tank for the radiators. There is a pump to send the water to the radiators.

Control:
I want to turn on the pump that sends hot water to the radiators if any of the radiator thermostats is set to >10% heating, and to turn off the pump if all the radiator thermostats are set to <10% heating.

Approach:
Triggers:
I use a template to identify all the thermostats linked to the radiators to crate a list of Triggers. I anticipate adding several more so I want to automate the identification of the radiator thermostats.
Condition:
None
Actions:
I use an Action type Choose with a similar template to determine if any of the radiators require water, which then turns on a switch for the radiator pump. The default action is to turn off the switch for the radiator pump.

Templates:
I am most unsure about the template used to define the Triggers. When I copy the template into the Developer's Tools section, the result is
[
  "sensor.basement_heating",
  "sensor.dining_room_heating",
  "sensor.guest_room_heating",
  "sensor.kitchen_heating",
  "sensor.living_room_heating",
  "sensor.master_bedroom_heating",
  "sensor.office_heating"
]
However, the documentation indicates that a list of triggers should be defined as:
      entity_id:
        - sensor.temp_sensor_room
        - sensor.tado_temperature
Do I need to format the result of the template to follow the format above, including the 'entity_id:'?