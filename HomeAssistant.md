# Home Assistant sensors

## REST sensors

```yaml
rest:
    resource: "http://192.168.1.195/api/v1/state/"
    sensor:
      - name: "ESP32 EVSE consumption"
        value_template: "{{ value_json['consumption'] }}"
        #device_class: current

      - name: "ESP32 EVSE chargingCurrent"
        value_template: "{{ value_json['chargingCurrent'] }}"
        #device_class: current
        
      - name: "ESP32 EVSE consumptionLimit"
        value_template: "{{ value_json['consumptionLimit'] }}"
        #device_class: current
        
      - name: "ESP32 EVSE chargingTimeLimit"
        value_template: "{{ value_json['chargingTimeLimit'] }}"
        #device_class: time
        
      - name: "ESP32 EVSE underPowerLimit"
        value_template: "{{ value_json['underPowerLimit'] }}"
        device_class: power
```    
