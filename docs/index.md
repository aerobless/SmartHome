# Welcome

Hi there 👋 and welcome to my Smart Home documentation!

I've set up this page to document my own setup and also to share some of my findings, configuration hints and automations. Although there's a vast community of fellow Smart Home enthusiasts it can still be hard to get started. I'm trying to make this a bit easier with this site.

If you've got any input, have questions or otherwise get stuck feel free to leave a comment 😄 or hit me up on twitter [@eletiy](https://twitter.com/eletiy)

## Quickstart
+ [Screenshots of the UI](software/home-assistant/)
+ [Hardware](hardware/)
+ [Automations](automations/)

## Blog

### 28.02.2021 **Getting Started with Node-RED guide**
I had a bit of spare time so I wrote a [Getting Started with Node-RED](/automations/getting-started-with-node-red/) guide that teaches some of the basics on how to create automations in Node-RED. While creating this
guide I realized again just how few nodes you really need to do most things in Node-RED. I've really got a ton of automations in Node-RED but I probably only use about 10-20% of
all the nodes that come pre-installed.

### 21.01.2021 **Migrated my Home Assistant installation to Proxmox**
Until recently I've had Home Assistant installed in supervised mode. That's the one where I have full control over the OS but still use the HA Supervisor and docker containers.
It used to be easy to install and I didn't really have any issues. However since the HA Supervisor started to include various health checks it's been a bit annoying to keep it "healthy".
So I've decided to go the virtualization route and install Proxmox. This allows me to run the official Home Assistant OS image as a VM and still run other VMs with different applications on the same machine. [I've added a chapter about Proxmox under Software where you can find more information.](/software/proxmox)