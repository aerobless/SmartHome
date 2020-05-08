
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

## Power Switches

#### Shelly

#### MyStrom
I have a bunch of MyStrom smart switches connected to all sorts of devices. I use them to control the connected devices, but also for automations. For example I use two of them to measure the power consumption of the washer & dryer. That data is then used to send a notification when the washer or dryer has finished and it's time to take out the clothes.

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
Used to control TV and external speakers.

### ZigBee

#### Dresden Elektronik ConBee Stick
I use a Dreden Elektronik ConBee stick as ZigBee gateway for most of my ZigBee devices. I'd like to use it exclusively, however I've been having some trouble with the new Bluetooth-enabled Philips Hue blubs. So those few new gen Philips Hue blubs are connected to a normal Hue Hub. The ConBee stick is plugged directly into the Intel Nuc running Home Assistant.

#### Philips Hue Hub v2
I use this hub only to connect to newer Philips Hue blubs that don't yet work with the ConBee ZigBee stick. I'd prefer to not use this hub because it is only connected to Home Assistant via Polling, this makes it slower then the ZigBee stick. It also doesn't support the Xiaomi ZigBee sensors and those sensors benefit from having powered devices nearby. So I try to have all ZigBee devices in the mesh connected to the Dresden Elektronik ConBee Stick.

### WiFi & Ethernet

#### FRITZ!Box 5490
![FRITZ!Box 5490](fritzbox5490.jpg){: style="height:150px"}

#### D-Link DGS-105

## TV & Entertainment

#### Samsung QE65Q7F

#### Sony PS4 Pro

#### Apple TV 4K 32GB

#### Nvidia Shield TV

## Locks

#### Nello One

## NFC

### NFC Tags

## Other Smart Devices

#### iRobot Roomba 980
![iRobot Roomba 980 Topdown](roomba_980.webp){: style="height:150px"}

#### Oral-B Elektro Genius 10100S