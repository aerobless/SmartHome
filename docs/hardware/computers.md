### Intel NUC Baby Canyon NUC7i3BNH
The brains of my whole Smart Home setup. It's sporting a Intel i3-7100U dual core CPU clocking 2.4 GHz, 2x 8GB DDR-4 Ram and a WD Blue 1TB M.2 SSD.
As for software it's running [Proxmox](/software/proxmox/), a virtualization platform. Inside of Proxmox I've deployed Home Assistant OS as a virtual appliance.

![Intel NUC](images/intel-nuc.jpg){: style="height:150px"}

### Raspberry PI Zero
Just a Raspberry Pi Zero running a headless Raspbian image. I use it as a BLE to MQTT gateway for the Xiaomi Flower Care sensors in my loggia. When triggered it will poll all the Flower Care sensors and forward their values over MQTT.