
A list of the hardware currently present in my smart home.

## Computers

### Intel NUC Baby Canyon NUC7i3BNH
The brains of my whole Smart Home setup. It's sporting a Intel i3-7100U CPU clocking 2.4 GHz, 2x 8GB DDR-4 Ram and an Intel 545 256GB SSD.
As for software it's running Ubuntu 18.04 LTS, Docker and most importantly Home Assistant.

![Intel NUC](intel-nuc.webp){: style="height:150px"}

### Raspberry PI Zero
Just a Raspberry Pi Zero running a headless raspbian image. I use it as a BLE to MQTT gateway for the Xiaomi Flower Care sensors in my loggia. When triggered it will poll all the Flower Care sensors and forward their values over MQTT.

## Sensors

### Xiaomi
I have a lot of Xiaomi sensors. They're all paired to the Dresden Elektronik ConBee ZigBee stick

| Name                     | Description                        | Sensors                                      | Communication |
|--------------------------|------------------------------------|----------------------------------------------|---------------|
| Aqara Shock Sensor       | Detects movement                   | Vibration, Temperature                       | ZigBee        |
| Aqara Temperature Sensor | Reports temperature, humidity etc. | Temperature, Humidity, Atmospheric Pressure  | ZigBee        |
| Xiaomi Flower Care       | Reports soil status.               | Water level, temperature, fertilizer         | BLE           |
| Aqara Door Sensor        | Detects door open/closed           | open/close                                   | ZigBee        |

### Philips Hue

#### Netatmo Weatherstation
One of the first devices I bought for my smart home. It consists of a indoor and outdoor weather station. Sadly the outdoor one has died after a few years.. but the indoor one is still going strong. Apart from the temperature it also reports the Carbon Dioxide levels which none of my other sensors do.

## Power Switches

### Shelly
Shelly's are tiny power switches that I've placed behind the actual light switches of my apartment. I mainly use them to detach the event of clicking a light-switch and turning the power of the light bulbs on/off. Since I use smart light blubs (Philips Hue), the light bulbs need to be powered on all the time, otherwise they can't be controlled via Home Assistant, Google Home etc. This is where the Shellys come in real handy. They conntect to Home Assistant via MQTT over WiFi and they can be configured in a way that pressing the actual light switch will simply send an MQTT event but not actually turn of the power of the light blubs. Home Assistant can then decide what to do with the button press event. In some cases I turn on/off the lights, but in other cases I've re-used the light switch to do other things. Such as change light scene or turn on the radio.

#### Shelly 1PM
This shelly switches on power line / button. It also measure the power consumed.

![Shelly 1PM](shelly_1pm.jpg){: style="height:150px"}

#### Shelly 1PM
This shelly switches two power lines / buttons. It also measures the power consumed. It could also be used to control electric blinds, but I don't use it for that.

![Shelly 2.5](shelly_25.jpg){: style="height:150px"}

### MyStrom Switch
I have a bunch of MyStrom smart switches connected to all sorts of devices. I use them to control the connected devices, but also for automations. For example I use two of them to measure the power consumption of the washer & dryer. That data is then used to send a notification when the washer or dryer has finished and it's time to take out the clothes.

![MyStrom Switch](myStrom-Switch.jpg){: style="height:200px"}

## Voice Assistants & Smart Display

### Google Home

- Google Home Mini 3x
- Google Home
- Google Nest Hub

## Lights

### Philips Hue
I use mostly Philips Hue lightbulbs.

- Philips Filament

#### Nanoleaf Aurora

## Wireless Network Hubs

### Infrared

#### Logitech Harmony Hub
Used to control TV, external speakers and air conditioner.

### ZigBee

#### Dresden Elektronik ConBee Stick
I use a Dreden Elektronik ConBee stick as ZigBee gateway for most of my ZigBee devices. I'd like to use it exclusively, however I've been having some trouble with the new Bluetooth-enabled Philips Hue blubs. So those few new gen Philips Hue blubs are connected to a normal Hue Hub. The ConBee stick is plugged directly into the Intel Nuc running Home Assistant.

#### Philips Hue Hub v2
I use this hub only to connect to newer Philips Hue blubs that don't yet work with the ConBee ZigBee stick. I'd prefer to not use this hub because it is only connected to Home Assistant via Polling, this makes it slower then the ZigBee stick. It also doesn't support the Xiaomi ZigBee sensors and those sensors benefit from having powered devices nearby. So I try to have all ZigBee devices in the mesh connected to the Dresden Elektronik ConBee Stick.

### WiFi & Ethernet

#### FRITZ!Box 5490
![FRITZ!Box 5490](fritzbox5490.jpg){: style="height:150px"}

#### D-Link DGS-105

#### Google Wifi
![Google Wifi](google_wifi.jpg){: style="height:150px"}

## TV & Entertainment

#### Samsung QE65Q7F

#### Sony PS4 Pro

#### Apple TV 4K 32GB

#### Nvidia Shield TV

## Locks

#### Nello One

## NFC

### NFC Tags

## Blinds

#### KNX Controller

#### KNX IP Bridge

## Other Smart Devices

#### Kibernetik Air Conditioner
A simple AC device. Communicates over IR.

![Kibernetik Air Conditioner](kibernetik-klimageraet-mk-light-001.xxl3.jpg){: style="height:150px"}

#### iRobot Roomba 980
Smart vacuum robot that communicates over WiFi. It's actually running Linux and you can connect to it via SSH. Pretty dope, no? :D

![iRobot Roomba 980 Topdown](roomba_980.webp){: style="height:150px"}

#### Oral-B Elektro Genius 10100S
Smart toothbrush that communicates over BLE.

![Oral-B Genius 10100S](oral_b_genius_10100S.jpg){: style="height:150px"}