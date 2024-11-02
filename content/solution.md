---
title: "Solution"
date: 2021-12-18T11:10:36+08:00
draft: false
language: en
description: A Deep Dive into the technical details of SHIFTY.
featured_image: ../assets/images/featured/featured-img-placeholder.png
---

Now that you're familiar with the [motivation behind SHIFTY](/posts/1-kickoff), let's dive into the technical details. Be prepared — it might get a bit technical! 🛠️

## 🔗 Device Connection

SHIFTY fixtures are all interconnected via a network, allowing for a lot of flexibility:

### 🔍 Auto Discovery

Devices can be added to the network, and they will automatically appear in the control desk. No need to manually inform the control desk about new devices or fiddle with DMX addresses. It's plug-and-play magic! ✨

### 🏗️ Proven Topology

Traditional DMX systems work with a bus topology, meaning one device is connected to the next. This has a few advantages over common network star topologies, like requiring less cabling. However, if one cable fails, the whole chain is broken. Also, a single DMX cable can only carry one universe (512 channels).

A star topology, in comparison, isn't suited for structures like trusses where devices are connected in a line. Therefore, SHIFTY combines the best of both worlds by supporting both topologies. A technical standard implementing Ethernet over a bus is **10Base-T1S**.

**Redundancy**: As devices require two network ports anyway for the bus topology, it's possible to connect both to different switches for redundancy. This way, if one switch fails, the system can continue to operate seamlessly. Using *Rapid Spanning Tree Protocol* (RSTP) and building a ring can further increase reliability 🔁.

In addition, if fixture control isn't as time-critical, wireless operation via Wi-Fi is also imaginable, greatly simplifying the setup 📶.

### 📡 Reliable Transport

*ArtNet* and *sACN* use *UDP* as the transport protocol. This means packets are sent without any guarantee they arrive. Also, no connection is established, so the sender doesn't know if the receiver is still there. For SHIFTY, we wanted reliable transport with connection establishment and automatic retransmission of lost packets. Therefore, we use *TCP* as the transport protocol. This also allows for more efficient network use, as the sender can adapt the rate of packets to the receiver's capabilities 🚀.

### 🤖 Self-Describing Devices

After the initial connection, the device will tell the control desk what it's capable of. This includes, but isn't limited to:

- **Static Physical Attributes**: Dimensions, weight, max power consumption
- **Dynamic Physical Attributes**: Pan/Tilt range, zoom range, light output
- **Control Capabilities**: Firmware version, supported SHIFTY features

... and much more! 🎉

Self-describing devices completely eliminate the need for manual device definitions and libraries for operation. Fixtures will always behave exactly as they should and can be visualized perfectly in the control desk 🖥️.

## 🎛️ Device Control

Now that we've connected all devices, let's see what we can do with them:

### ⚙️ Auto Patching

Tired of manually assigning DMX addresses, keeping track of which device is in which universe, and ensuring there are no address conflicts? That can be a thing of the past 🚫. As every device is now connected via network and speaking the SHIFTY protocol, there's no need for DMX addresses. IP addresses are assigned automatically (APIPA) or via DHCP. Every device will automatically appear in the control desk and can be controlled without any manual intervention. Of course, if you want to assign a specific IP address or add a device when auto-discovery didn't work, you can still do that 🛠️.

### 📏 Physical Attributes

A control desk will always control a device using *Instructions* (see below) which alter physical values. Instead of mapping the light output intensity from 0% to 100%, the control desk knows the maximum light output of the device and can control it in absolute values (e.g., 500 lumens). This allows you to mix and match different devices from different manufacturers without worrying about different scaling factors, resulting in a better look 🎨. The same applies to all other attributes like pan/tilt, zoom, focus, color, etc.

Also, this allows for an exact (pre-)visualization of the show 🌟.

### 🏷️ Metatags

Devices can be tagged with metatags by the user. In fixed installations, this could be the function description of the device (e.g., "front"). Then, once an operator connects their control desk to the network, they can see all devices and their metatags, allowing for a quick and easy setup. See below for ideas using metatags like auto-grouping 🚀.

### 🌀 Transparent Driver

The firmware of a SHIFTY device is designed to be as simple as possible since it transparently provides the current values of the physical attributes via the SHIFTY protocol and executes the instructions sent by the control desk. No complex logic is implemented in the device itself, allowing for small and cost-effective devices 💡.

### 📝 Instructions

Instructions describe changes to the physical attributes of a device. They can be sent by the control desk to the device and are executed by the device. Instructions can be sent as a one-time command or as a continuous stream, allowing for smooth transitions between different states.

For example, a pan/tilt head can be instructed to move to a certain position in a certain time. The device will then calculate the necessary steps to reach the target position in the given time, allowing for smooth movement without any jerking 🎥. A color fade would also be a single instruction (e.g., "fade to red in 5 seconds"). This greatly reduces the amount of data sent over the network compared to sending target values for every step 📉.

### 📡 Single Source of Truth

Devices can publish their current state — like pan/tilt position, zoom level, etc. — to the network. Therefore, the control desk always knows the real state of the devices and can react accordingly. These values are also interesting to the operator, for example, fluid levels in a fog machine or the temperature of a lamp. This allows for more reliable operation and a better overview of the system 🔍.

### 🤝 Multi-Device Connections

Devices can be connected to multiple other devices. For example, a flame machine could be connected to a control desk as well as to an emergency stop button. If one connection fails, the device would automatically shut off. Additionally, multiple control desks within a single network can provide different sets of data to devices. For example, a media server could supply color data while a lighting desk controls intensity levels. This eliminates the need to merge the media server's data within the lighting desk, reducing latency to the fixture 🎛️.

### 💡 Future Ideas: Auto Positioning

With such a flexible base, more advanced features could be imagined. One possibility is the use of Bluetooth Low Energy (BLE) beacons to determine the position of a device in a room. This could be used to automatically position devices or group them. With an extra gyroscope, the orientation of a device could also be determined. This would allow for a completely new way of setting up a show — making manual positioning of devices in the desk obsolete. In addition, we'd get more accurate position data 🌐.

## 🎚️ Control Desk-Only Features

There are also some features that would only need to be implemented in the control desk. They aren't directly part of SHIFTY, but we wanted to mention them here:

### 🎯 Goal-Based Programming

Instead of programming a show by setting the values of the physical attributes of the devices at certain times, the operator could describe the goal of a device at a certain time. For example, "the light should be on the actor" or "the light should be in the middle of the stage." The control desk would then calculate the necessary steps to reach the goal for a much more intuitive programming experience 🧠.

### 🗣️ Natural Language Control

Instead of using a graphical user interface or command-line interface, the operator could use natural language to control the devices. For example, "move the light to the left" or "make the light red." This would allow for a more intuitive control of the devices and would be especially useful for inexperienced users 🗣️.

---

As you can see, with SHIFTY, we're not just rethinking lighting control — we're rebuilding it from the ground up. 💡🚀

And because this is - as you already might have guessed - a huge task, we need your help. 🙏 You don't need to be a technician or developer, it already helps if you just share this! 🌐

However, if you are a technician or developer, we invite you to join us on this journey. We are looking for contributors to help us design, build and (probably most important) test SHIFTY. If you are interested, please reach out to us on [GitHub](https://github.com/oshifty) or via our [contact form](/contact).

Let's make lighting design a breeze together! 🌈