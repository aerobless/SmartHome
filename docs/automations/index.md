
All of these automations are built in Node-RED. And they're automating devices configured in Home Assistant.

## Universal

### Vacuum the floor when I'm not home
At 10am a check is executed whether the apartment is occupied or not. If it's not occupied the Roomba is triggered to start vacuuming the floor. If the apartment is occupied a notification is sent to me via Telegram to inform me that the cleaning cycle was not started.

![Roomba Cleaning Node-RED](roomba-cleaning-automation.png)

## Lights

### Kitchen Overhead Light
If motion is detected at the sink, the kitchen overhead light is turned on. At the same time a timer is set for 3mins. If further motion is detected the timer is reset. If no more motion occurs and the timer runs out the light is turned off again.

![Kitchen Overhead Light Node-RED](kitchen-overhead-light-automation.png)

### Shelly Light Switches
To prevent the hue lights from being turned off fully I've added a Shelly controller behind each light switch. This detaches the switch from turn on/off the power
and instead sends a MQTT messages to Home Assistant that the button was pressed. So in order for some of the light switches to actually turn on/off lights there
needs to be a really simple automation connecting the action of pressing the switch with some lights that can be controlled.

![Light Switch Node-RED](light-switch-automation.png){: style="width:400px"}

Another advantage of this system is that I've got light switches to spare for other functions. Since for example in the living room I'm happy with turning on/off
all the lights at the same time. So of 4 switches I only need one to control the lights and can use the others e.g. to set a specific scene or turn on the radio.

### Bathroom Light
My bathroom light is dumb, so it's controlled via power on/off of the shelly switch. For that reason and because of some edge cases there's a bit more logic behind this automation..

![Bathroom Light Node-RED](bathroom-light-automation.png)

There's a few requirements behind this automation. The light turns on automatically with motion detection. But I don't want to be blinded a night, since it's a dumb light it can't do dimming, so the light should only turn on during certain times (06:20-22:00 during the week or 08:00-22:00 on a weekend). But if I'm up late it should still turn on automatically, so I've added the condition that if the kitchen light is already on, it's probably fine to turn on the bathroom light as well and not check the time condition.  
But then there was another problem. Since it's a dumb light tube it's a bit slow to turn on. This could result in user error. E.g. the motion detector triggers the light to turn on but the user thinks it didn't work or doesn't know about the motion detector and presses the button. Now the light turns off again and the user wonders why the button didn't work. So to fix this behavior I've added a locking logic that blocks further commands for 2 seconds if the light has been turned on via the button or motion detection.

## Devices

### Washing machine/dryer has finished
If the washing machine or dryer finishes their work a push notification is sent to my phone and Google Home announces that the washer or dryer has finished.
That washing/drying has finished is detected via the power consumption of the respective device with a MyStrom switch. The push notification is sent via the Home Assistant App on my phone. The Google Home announcement uses TTS (text to speech) and Chromecast functionality.

![Washing has finished Node-RED](washing-has-finished-automation.png)

Template sensor to detect if the washing machine is on/off:
```yaml
binary_sensor: 
  - platform: template
    sensors:
        washingmachine_state:
            friendly_name: "Washing Machine State"
            delay_off: # Only switches states after new state existed for x minutes
                minutes: 3
            icon_template: mdi:washing-machine
            value_template: "{{ states.switch.mystrom_washingmachine.attributes.current_power_w | default(0) |float > 10}}"
```

Push Notification
```json
{
    "title": "Washing Machine done 👕",
    "message": "Don't wait for your clothes to wrinkle!"
}
```

### Turn off the charging station
I've set up a charging station for various camera batteries, drone, battery pack etc. To prevent them from being charged constantly I've set up a myStrom switch that is turned off after 5h. So if I plan on going somewhere where I need a fully charged battery in one of these devices I can simply say "Okay Google turn on the charging station" and forget about it. It's quite simple but very convenient.

![Charging Station Node-RED](charging-station-automation.png){: style="width:500px"}

## TV & Entertainment

### TV App Launcher
This one is a bit of a monster. Basically what it allows is to have a Channel selector drop down in the frontend where you can choose the App that should
be launched/switch to on the TV. As an added benefit this also work with Google Home. So I can say stuff like:

+ "Okay Google switch to [**PlayStation**/Apple TV/Netflix/...]"

![TV App Launcher UI](tv-app-launcher.png){: style="width:500px"}

The REST APIs of the TV are shit.. they allow some things but not all - so this is automation is a mixture of REST calls and IR commands. You may be wondering why use the REST APIs at all? Since the TV menu is basically a list of apps, the REST API allows me to jump to a "safe" point in that list. For example I can launch YouTube over the REST Api. I know that I've placed YouTube as the first App, so now I can use IR commands to move 2 positions to the right and for example launch Spotify. If I didn't have the REST command there'd be no way for me to know which App is open at the moment and navigate the menu.

![TV App Launcher Node-RED](tv-app-launcher-automation.png)

In case you're wondering about the Apple TV Wallpaper path. It's a hacky way to force Apple TV to show the screensaver immediately. The screensaver shows flyovers of major cities all over the world and it's nice to have on as a bit of decoration/art.