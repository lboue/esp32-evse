# Home Assistant sensors

## REST sensors

```yaml
rest:
    resource: "http://192.168.1.195/api/v1/state/"
    sensor:
      - name: "ESP32 EVSE consumption"
        value_template: "{{ value_json['consumption'] }}"
        device_class: energy
        unit_of_measurement: "Wh"

      - name: "ESP32 EVSE chargingCurrent"
        value_template: "{{ value_json['chargingCurrent'] }}"
        device_class: current
        unit_of_measurement: "A"
        # unique_id 
        
      - name: "ESP32 EVSE consumptionLimit"
        value_template: "{{ value_json['consumptionLimit'] / 1000 }}"
        device_class: energy
        unit_of_measurement: "kWh"
        
      - name: "ESP32 EVSE chargingTimeLimit"
        value_template: "{{ value_json['chargingTimeLimit'] / 60 }}"
        device_class: duration
        unit_of_measurement: "minutes"
        
      - name: "ESP32 EVSE underPowerLimit"
        value_template: "{{ value_json['underPowerLimit'] / 1000 }}"
        device_class: power
        unit_of_measurement: "kW"

binary_sensor:
  - platform: rest
    resource: "http://192.168.1.195/api/v1/state/"
    name: "ESP32 EVSE available"
    value_template: "{{ value_json['available'] }}"

  - platform: rest
    resource: "http://192.168.1.195/api/v1/state/"
    name: "ESP32 EVSE enabled"
    device_class: running
    value_template: "{{ value_json['enabled'] }}"

  - platform: rest
    resource: "http://192.168.1.195/api/v1/state/"
    name: "ESP32 EVSE limitReached"
    value_template: "{{ value_json['limitReached'] }}"
```    
