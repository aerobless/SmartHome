````yaml
esphome:
  name: aircon_furber_cool_mcu32s
  platform: ESP32
  board: nodemcu-32s

wifi:
  ssid: "WIFI_SSID"
  password: "WIFI_PASSWORD"

  # Enable fallback hotspot (captive portal) in case wifi connection fails
  ap:
    ssid: "FALLBACK_WIFI_SSID"
    password: "FALLBACK_WIFI_PASSWORD"

captive_portal:

# Enable logging
logger:

# Enable Home Assistant API
api:
  password: "API_PASSWORD"

ota:
  password: "OTA_PASSWORD"

switch:
  - platform: gpio
    pin: 18
    id: gpio_18
  - platform: template
    name: "AirCon Temperature Higher"
    icon: "mdi:thermometer-plus"
    turn_on_action:
    - switch.turn_on: gpio_18
    - delay: 500ms
    - switch.turn_off: gpio_18
    
  - platform: gpio
    pin: 5
    id: gpio_5
  - platform: template
    name: "AirCon Temperature Lower"
    icon: "mdi:thermometer-minus"
    turn_on_action:
    - switch.turn_on: gpio_5
    - delay: 500ms
    - switch.turn_off: gpio_5
    
  - platform: gpio
    pin: 17
    id: gpio_17
  - platform: template
    name: "AirCon Fan Speed"
    icon: "mdi:speedometer"
    id: aircon_speed
    turn_on_action:
    - switch.turn_on: gpio_17
    - delay: 500ms
    - switch.turn_off: gpio_17
    - delay: 200ms
    - script.execute: next_aircon_speed
    
  - platform: gpio
    pin: 16
    id: gpio_16
  - platform: template
    name: "AirCon Hvac Mode"
    icon: "mdi:hvac"
    turn_on_action:
    - switch.turn_on: gpio_16
    - delay: 500ms
    - switch.turn_off: gpio_16
    - delay: 200ms
    - script.execute: next_aircon_mode
    
  - platform: gpio
    pin: 4
    id: gpio_4
  - platform: template
    name: "AirCon Power On/Off"
    icon: "mdi:power-standby"
    id: aircon_power
    turn_on_action:
    - switch.template.publish:
        id: aircon_power
        state: true
    - switch.turn_on: gpio_4
    - delay: 500ms
    - switch.turn_off: gpio_4
    - delay: 300ms
    - lambda: 'id(aircon_fan_speed).publish_state("High");'
    - lambda: 'id(aircon_hvac_mode).publish_state("Cool");'
    turn_off_action:
    - switch.template.publish:
        id: aircon_power
        state: false
    - switch.turn_on: virtual_switch_speed_high
    - switch.turn_on: virtual_switch_mode_cool
    - delay: 500ms
    - switch.turn_on: gpio_4
    - delay: 500ms
    - switch.turn_off: gpio_4
    - delay: 500ms
    - lambda: 'id(aircon_fan_speed).publish_state("Off");'
    - lambda: 'id(aircon_hvac_mode).publish_state("Off");'
    
  - platform: template
    id: virtual_switch_speed_high
    turn_on_action:
    - lambda: |-
        if(id(aircon_fan_speed).state == "High"){
          // do nothing         
        } else if(id(aircon_fan_speed).state == "Medium"){
          delay(500);
          id(gpio_17).turn_on();
          delay(500);
          id(gpio_17).turn_off();
          delay(500);
          id(gpio_17).turn_on();
          delay(500);
          id(gpio_17).turn_off();
          delay(500);
        } else if(id(aircon_fan_speed).state == "Low"){
          delay(500);
          id(gpio_17).turn_on();
          delay(500);
          id(gpio_17).turn_off();
          delay(500);
        }
        id(aircon_fan_speed).publish_state("High");
        
  - platform: template
    id: virtual_switch_mode_cool
    turn_on_action:
    - lambda: |-
        if(id(aircon_hvac_mode).state == "Cool"){
          // do nothing         
        } else if(id(aircon_hvac_mode).state == "Dry"){
          delay(500);
          id(gpio_16).turn_on();
          delay(500);
          id(gpio_16).turn_off();
          delay(500);
          id(gpio_16).turn_on();
          delay(500);
          id(gpio_16).turn_off();
          delay(500);
        } else if(id(aircon_hvac_mode).state == "Fan"){
          delay(500);
          id(gpio_16).turn_on();
          delay(500);
          id(gpio_16).turn_off();
          delay(500);
        }
        id(aircon_hvac_mode).publish_state("Cool");
        
  - platform: template
    name: "AirCon Temperature Lowest"
    icon: "mdi:snowflake"
    turn_on_action:
    - lambda: |-
        for (int i = 0; i < 7; i++) {
          id(gpio_5).turn_on();
          delay(500);
          id(gpio_5).turn_off();
          delay(500);
        }

binary_sensor:
- platform: gpio
  pin:
    number: 27
    inverted: True
  id: aircon_mode_cold
  filters:
    - delayed_on: 100ms
    - delayed_off: 300ms
    
- platform: gpio
  pin:
    number: 26
    inverted: True
  id: aircon_mode_dry
  filters:
    - delayed_on: 100ms
    - delayed_off: 300ms
    
- platform: gpio
  pin:
    number: 33
    inverted: True
  id: aircon_speed_high
  filters:
    - delayed_on: 100ms
    - delayed_off: 300ms

- platform: template
  id: virtual_power_state
  
script:
  - id: next_aircon_speed
    then:
      - lambda: |-
          if(id(aircon_fan_speed).state == "High"){
            id(aircon_fan_speed).publish_state("Medium");            
          } else if(id(aircon_fan_speed).state == "Medium"){
            id(aircon_fan_speed).publish_state("Low");            
          } else if(id(aircon_fan_speed).state == "Low"){
            id(aircon_fan_speed).publish_state("High");            
          }
  - id: next_aircon_mode
    then:
      - lambda: |-
          if(id(aircon_hvac_mode).state == "Cool"){
            id(aircon_hvac_mode).publish_state("Dry");            
          } else if(id(aircon_hvac_mode).state == "Dry"){
            id(aircon_hvac_mode).publish_state("Fan");            
          } else if(id(aircon_hvac_mode).state == "Fan"){
            id(aircon_hvac_mode).publish_state("Cool");            
          }
    
text_sensor:
  - platform: template
    name: "AirCon Fan Speed"
    id: aircon_fan_speed
    icon: "mdi:speedometer"
    update_interval: 60s
    
  - platform: template
    name: "AirCon Mode"
    id: aircon_hvac_mode
    icon: "mdi:hvac"
    update_interval: 60s
````