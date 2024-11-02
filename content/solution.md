---
title: "Solution"
date: 2021-12-18T11:10:36+08:00
draft: false
language: en
description: Technical details of SHIFTY
featured_image: ../assets/images/featured/featured-img-placeholder.png
---

So, as you now know about the [motivation behind SHIFTY](/posts/1-kickoff), let's dive into the technical details of SHIFTY. Be prepared, it might get a bit technical.

## Device Connection
SHIFTY fixtures are all interconnected via network. This allows for a lot of flexibility:

### Auto Discovery
Devices can be added to the network and they will be automatically appear in the control desk. No need to manually tell the control desk about the new device or fiddle with DMX addresses.

### Proven Topology
Traditional dmx systems work with a bus topology, meaning one device is connected to the next. This has a few advantages over common network star-topologies like requiring less cabling. However, if one cable or device fails, the whole chain is broken. Also, a single dmx cable can only carry one universe (512 channels). A star topology, in comparison, would not be suited for structures like trusses where devices are connected in a line. Therefore, SHIFTY combines the best of both worlds by supporting both topologies. A technical standard implementing Ethernet over a bus is 10Base-T1S.
In addition, if fixture control is not time critical, wireless operation via WiFi is also imaginable, greatly simplifying the setup.
**Redundancy**: As devices require two network ports anyway for the bus topology, it is possible to connect both to different switches for redundancy. This way, if one switch fails, the system can continue to operate. Using *Rapid Spanning Tree Protocol* (RSTP) and building a ring can further increase reliability.

### Reliable Transport
*ArtNet* and *sACN* use *UDP* as transport protocol. This means that packets are sent without any guarantee that they arrive. Also, no connection is established, so the sender does not know if the receiver is still there. For SHIFTY, we wanted to have a reliable transport with connection establishment and automatic retransmission of lost packets. Therefore, we use *TCP* as transport protocol. This also allows for a more efficient use of the network, as the sender can adapt the rate of packets to the receiver's capabilities.

### Self Describing Devices
After the initial connection, the device will tell the control desk what it is capable of. This includes, but is not limited to:
- **Static Physical Attributes**: Dimensions, weight, max. power consumption
- **Dynamic Physical Attributes**: Pan/Tilt range, zoom range, light output
- **Control Capabilities**: Firmware version, supported SHIFTY features

... and much more 🎉

Self Describing Devices completely elimitate the need for a manual device definitions and libraries for operation. Fixtures will always behave exactly as they are supposed to and can be visualized perfectly in the control desk.

## Device Control
Now that we have connected all devices, let's see what we can do with them:

### Auto Patching
Tired of manually assigning DMX addresses, keeping track of which device is in which universe and making sure there are no address conflicts? That can be a thing of the past. As every device is now connected via network and speaking the SHIFTY protocol, there don't need to be any DMX addresses. There's no need for any addresses, other than IP addresses which are assigned automatically or via DHCP. Every device will automatically appear in the control desk and can be controlled without any manual intervention. Of course, if you want to assign a specific IP address or add a device when auto-discovery did not work, you can still do that.

### Physical Attributes
A control desk will always control a device using *Instructions* (see below) which alter physical values. Instead of mapping the light output intensity for example from 0% to 100%, the control desk knows the maximum light output of the device and can control it in absolute values (for example 500 lumens). This allows to mix and match different devices from different manufacturers without having to worry about different scaling factors resulting in a better look. The same applies to all other attributes like pan/tilt, zoom, focus, etc.
Also, this allows for an exact (pre-)visualization of the show.

### Metatags
Devices can be tagged with metatags by the user. In fixed installations, this could be the function description of the device (e.g. "front"). Then, once an operator connects his control desk to the network, he can see all devices and their metatags allowing for a quick and easy setup. See below for ideas using Metatags like auto grouping.

### Transparent Driver
The firmware of a SHIFTY device is designed to be as simple as possible, since it transparently provides the current values of the physical attributes via the SHIFTY protocol and executes the instructions sent by the control desk. No complex logic should be implemented in the device itself, allowing for small and cheap devices.

### Instructions
Instructions describe changes to the physical attributes of a device. They can be sent by the control desk to the device and are executed by the device. Instructions can be sent as a one-time command or as a continuous stream. This allows for smooth transitions between different states of a device. For example, a pan/tilt head can be instructed to move to a certain position in a certain time. The device will then calculate the necessary steps to reach the target position in the given time. This allows for a smooth movement without any jerking. A color fade for example would also be a single instruction (e.g. "fade to red in 5 seconds"). This greatly reduces the amount of data sent over the network in comparison to sending the target values for every step.

### Single Source of Truth
Devices can publish their current state like pan/tilt position, zoom level, etc. to the network. Therefore, the control desk always knows the real state of the devices and can react accordingly. Those values are also interesing to the operator, for example if they are fluid levels in a fog machine or the temperature of a lamp. This allows for a more reliable operation and a better overview of the system.

### Multi Device Connections
Devices can be connected to multiple other devices. For example, a flame machine could be connected to a control desk as well as to an emergency stop button. If one connection fails, the device would automatically shut off. Also, multiple control desks in a single session could be imagined.

### Future Ideas: Auto Positioning
With such a flexible base, more advanced features could be imagined. One possibility could be the use of Bluetooth Low Energy (BLE) beacons to determine the position of a device in a room. This could be used to automatically position devices in a room or to automatically group devices. With an extra gyroscope, the orientation of a device could also be determined. This would allow for a completely new way of setting up a show - by making the whole manual positioning of devices in the desk obsolete. In addition we would get more accurate position data.

## Control Desk only features
There are also some features that would only need to be implemented in the control desk. They are not directly part of SHIFTY, but we wanted to mention them here:

### Goal Based Programming
Instead of programming a show by setting the values of the physical attributes of the devices at a certain time, the operator could describe the goal of a device at a certain time. For example, "the light should be on the actor" or "the light should be in the middle of the stage". The control desk would then calculate the necessary steps to reach the goal for a much more intuitive programming experience.

### Natural Language Control
Instead of using a graphical user interface or command line interface, the operator could use natural language to control the devices. For example, "move the light to the left" or "make the light red". This would allow for a more intuitive control of the devices and would be especially useful for unexperienced users.
