# Software

This is a bit of a general overview over all the software I use. It's not strictly limited to only Smart Home stuff since
it's hard to draw a clear line.

## Home Automation

### [Home Assistant](/SmartHome/software/home-assistant/)
[Home Assistant](/SmartHome/software/home-assistant/) is the core of my smart home setup. It's an open source home automation software written in Python that runs locally on a computer as small as a Raspberry Pi or as powerful as the user desires. At the time of me writing this it supports over 1500 integrations with various smart home devices & services. It is actively developed and has a regular release cycle of 3 weeks. Updates are frequent and of good quality.  
I'm running my [Home Assistant](/SmartHome/software/home-assistant/) instance on a Intel NUC in supervised mode. This means I provide my own OS of choice (Ubuntu) and Home Assistant runs a supervisor software on top that manages the docker containers used by itself and addons.

### [Node-RED](/SmartHome/software/node-red/)
[Node-RED](/SmartHome/software/node-red/) is a programming tool for wiring together hardware devices, APIs and online services. It provides a web-editor that makes it easy to wire together flows using a wide range of nodes. Changes can be deployed with a single-click. Node-RED was originally developed by IBM but has since been contributed to the open source JS Foundation project.
I run Node-RED as a addon in Home Assistant and I use it to create & run a ton of simple and complicated automations. Some of my favorite automations are: only starting the cleaning robot when I'm not home, reminding me that the washing machine has finished with a push notification & google home announcement, and operating various lights fully automatically.

### Visual Studio Code
Visual Studio Code is an awesome IDE in it's own right. However I also run it as a Home Assistant Addon in order to edit all those .yaml configuration files. What's especially cool is that it has a full integration with Home Assistant, so there's even autocompletion for all the device entities managed by Home Assistant.

## Documentation

### [MkDocs](https://www.mkdocs.org/)
This page is made with [MkDocs](https://www.mkdocs.org/). It's a static site generator that's geared towards building project documentation. The source files are written in Markdown and configured with a single .yaml configuration file. I host my smart home documentation on Github pages.

## SaaS
Software as a service.. or cloud stuff that I use :)

### [Exist](https://exist.io/?referred_by=aerobless)
Exist combines the data of various sources (Apple Health, RescueTime, Weather .. etc.) to help you understand what makes you more happy, productive, active etc. This data is already being collected by other entities.. so it's interesting to have it for yourself and draw your own conclusions. I've made some automations in home assistant to automatically log the time spent gaming or watching tv to Exist.io.

### [1Password](https://1password.com/)
The password manager of my choice. Apart from storing passwords it has a few features that I really like. It has a scanner that detects weak, vulnerable or duplicate passwords and allows you to easily change them. And it can store 2FA pins in addition to passwords. This is a lot better than with Google Authenticator where you'd need to reset all your 2FA pins every time you set up a new phone.
