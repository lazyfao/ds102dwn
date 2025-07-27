type: vertical-stack
title: Boiler Control
cards:
  - type: entities
    entities:
      # Replace entity_ids with yours if they differ
      - entity: switch.smartswitch01_relay
        name: Manual Control
        icon: mdi:water-boiler
        # This section overrides the default tap action
        tap_action:
          action: call-service
          service: esphome.smartswitch01_toggle_manual
      - entity: sensor.smartswitch01_boiler_smartswitch_wifi_signal
        name: Wi-Fi Signal
      - entity: sensor.smartswitch01_boiler_smartswitch_uptime
        name: Uptime
  - type: conditional
    conditions:
      - entity: sensor.smartswitch01_boiler_smartswitch_uptime # Fixed entity_id typo
        state_not: unavailable
    card:
      type: entities
      entities:
        - entity: input_text.smartswitch_schedule
          name: Autonomous Schedule
          icon: mdi:calendar-clock
