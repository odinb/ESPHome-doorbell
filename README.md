# ESPHome modified doorbell on ESP8266 HW.

For more information and hardware used, see here:<br /> https://www.zuidwijk.com/esphome-based-doorbell/

Alternative project: <br /> https://frenck.dev/diy-smart-doorbell-for-just-2-dollar/

This is run with Home-assistant: <br /> https://www.home-assistant.io/

And the following automation:

alias: Notify Doorbell
description: ""
trigger:
  - platform: state
    entity_id: binary_sensor.doorbell
    from: "off"
    to: "on"
condition: []
action:
  - service: notify.all_devices
    data:
      message: Ding dong! Someone is at the door!
      title: Doorbell pressed.
      data:
        push:
          sound:
            name: default
            critical: 1
            volume: 1
