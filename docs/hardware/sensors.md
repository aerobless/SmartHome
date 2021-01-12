### Xiaomi
I have a lot of Xiaomi sensors. They're all paired to the Dresden Elektronik ConBee ZigBee stick. Xiaomi products are best bought on AliExpress although swiss retailers such as Galaxus now have them as well for a steep markup. The ZigBee sensors use the nearest cable-powered device to access the mesh network, so that the least bit of energy is needed. In my experience the battery life of their coin-cells last around 1-2years even for frequently used devices such as door sensors. The battery life is however a bit reduced if the sensor is exposed to the cold. My outside temperature sensor typically only lasts a few months. It probably also needs more energy since the signal has to pass through thick walls/insulated windows.

The Xiaomi Flower Care sensors use BLE to report their values. Although Home Assistant provides a direct integration I cannot use it since my Home Assistant computer is too far away from where I've placed the sensors. So I'm using a Raspberry Pi Zero to collect the sensor values via BLE and then send them on the Home Assistant over MQTT.

| Name                     | Description                        | Sensors                                      | Communication |
|--------------------------|------------------------------------|----------------------------------------------|---------------|
| [Aqara Vibration Sensor](https://www.aqara.com/us/vibration_sensor.html)       | Detects movement                   | Vibration, Temperature                       | ZigBee        |
| [Aqara Temperature Sensor](https://www.aqara.com/us/temperature_humidity_sensor.html) | Reports temperature, humidity etc. | Temperature, Humidity, Atmospheric Pressure  | ZigBee        |
| [Xiaomi Flower Care](https://www.amazon.de/-/en/Xiaomi-Flower-Smart-Sensor-Monitor/dp/B074TY93JM)       | Reports soil status.               | Water level, temperature, fertilizer         | BLE           |
| [Aqara Door Sensor](https://www.aqara.com/us/door_and_window_sensor.html)        | Detects door open/closed           | open/close                                   | ZigBee        |

### Withings Sleep
It's main purpose is to record my sleep patterns and store them in Apple Health. However as an added benefit I can use it detect when the bed is occupied and e.g. automatically turn off lights.

![Withings Sleep](images/withings_sleep.png){: style="height:150px"}

### Netatmo Weatherstation
One of the first devices I bought for my smart home. It consists of a indoor and outdoor weather station. Sadly the outdoor one has died after a few years.. but the indoor one is still going strong. Apart from the temperature it also reports the Carbon Dioxide levels which none of my other sensors do.

![Netatmo Weatherstation](images/netatmo_weatherstation.jpg){: style="height:150px"}