# Home Assistant Examples

This repo contains some home assistant dashboards and other stuff that I found interesting to share

## Dashboard for Tesla vehicles

1) Install the custom Tesla integration from HACS: https://github.com/alandtse/tesla. Follow the instructions in the repo github to learn how to get your Tesla refresh token.

2) Add new sensors to include charging voltage, current and power. Add the sensors below to your configuration.yaml file. Remember to replace "tesla_model_y" with the name of the car you assigned when installing the Tesla integration.

    ```yaml
    sensor:
        - platform: template
        sensors:
            tesla_model_y_charging_rate_power:
            friendly_name: Tesla Model Y charging power
            value_template: "{{ state_attr('sensor.tesla_model_y_charging_rate_sensor', 'charger_power') }}"
            device_class: power
            unit_of_measurement: kW
            tesla_model_y_charging_rate_current:
            friendly_name: Tesla Model Y charging current
            value_template: "{{ state_attr('sensor.tesla_model_y_charging_rate_sensor', 'charger_actual_current') }}"
            device_class: current
            unit_of_measurement: A
            tesla_model_y_charging_rate_voltage:
            friendly_name: Tesla Model Y charging voltage
            value_template: "{{ state_attr('sensor.tesla_model_y_charging_rate_sensor', 'charger_voltage') }}"
            device_class: voltage
            unit_of_measurement: V

    ```

3) Install these custom cards from HACS:
    - [custom:button-card](https://github.com/custom-cards/button-card)
    - [custom:bar-card](https://github.com/custom-cards/bar-card)
    - [custom:mini-graph-card](https://github.com/kalkih/mini-graph-card)
    - [custom:simple-thermostat](https://github.com/nervetattoo/simple-thermostat)

4) Upload an image of your car to the config/www folder

5) Add your dashboard in the RAW Editor, copying the contents of the file [tesla.yml](https://github.com/rrlevy/home-assistant-personal/blob/main/lovelace/tela.yaml) in the place you want, inside the "views" list of dashboards. Remember to replace on that dashboard:
    - The variable name "tesla_model_y" to the one you gave to your own car
    - The car image file name "tesla.png" to the one you uploaded to the config/www folder
    - My card names are in Portuguese. You can rename them to whatever you want