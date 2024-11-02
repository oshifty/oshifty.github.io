---
title: "Solution"
date: 2021-12-18T11:10:36+08:00
draft: false
language: en
description: Technical details of SHIFTY
featured_image: ../assets/images/featured/featured-img-placeholder.png
---

TLDR, will be removed later:
- Device Connection
    - Auto Discovery
    - Proven Topology
    - Reliable Transport
    - Self Describing Devices

- Device Control
    - Auto Patching
    - Auto Positioning
    - Auto Grouping
    - Physical Attributes
    - Single Source of Truth
    - Metatags
    - Multi Device Connections
    - Instructions
    - Transparent Driver

- Other: Control Desk only features
    - Goal Based Programming
    - Natural Language Control




So, as you now know about the [motivation behind SHIFTY](/motivation), let's dive into the technical details of SHIFTY. Be prepared, it might get a bit technical.

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
- **Physical Attributes**: Dimensions, weight, max. power consumption
- **Physical Capabilities**: Pan/Tilt range, zoom range, light output
- **Control Capabilities**: Firmware version, supported SHIFTY features

... and much more 🎉

Self Describing Devices completely elimitate the need for a manual device definitions and libraries for operation. Fixtures will always behave exactly as they are supposed to and can be visualized perfectly in the control desk.
