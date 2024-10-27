---
title: "Not a new Idea 📚"
date: 2023-08-11T08:21:00.000Z
draft: false
language: en
featured_image: ../assets/images/posts/not-a-new-idea.png
summary: ?
description: ?
author: Lukas Runge
tags: 
    - History
    - DMX
    - ACN
---

## 🏛️ On the History of Fixture Control Protocols

With the invention of phase cut dimmers in 1959, it became possible to control dimmers via a separate 0-10V control signal for the first time. This allowed the dimmers that produced the operating current for the lamps to be moved to a separate room. When Vari*Lite invented the first moving light (VL0) in 1981, it made sense to go one step further and generate the operating currents for the motors installed in the fixture in the fixture itself. A protocol was therefore needed that could control several attributes of a remote device. A protocol standardized by the USITT in 1986 and based on the established RS-485 was to provide a remedy for such an application: Digital Multiplex (DMX). It was the first digital protocol that allowed centralized control of distributed lighting technology, making it possible to control not only the attributes of a luminaire, e.g. light color, focus, zoom, etc., but also devices that were not luminaires (e.g. curtain systems). For a long time, DMX was a robust protocol that met the requirements of our industry. However, the ever-increasing functionality of modern fixtures eventually led to fewer and fewer fixtures being able to operate in one DMX universe. To avoid having to pull several DMX universes onto one truss, Art-Net was developed. The protocol eliminates the limit of one universe per cable run. But as it builds on UDP using broadcast all other means of operation stay the same. It has not adopted any other advantages of a modern network stack. ESTA soon realized that there was a need for a new control protocol that uses those new advantages and meets the growing expectations of end users. After three years of work on the standard Architecture for Control Networks (ACN) was finally released to the public in 2006 as ANSI Standard E1.17-2006.

It was designed with the following design goals in mind:
- **Interoperability across manufacturers:** Enable equipment from different manufacturers to communicate effectively.
- **Many sources, many sinks:** Support multiple sources and consumers of control data on the same network.
- **Single network, multiple uses:** Allow a network to support various independent applications (e.g., separate lighting and audio control).
- **Mainstream protocol compatibility:** Utilize standard network protocols without duplicating lower-layer functionalities.
- **Leverage off-the-shelf technology:** Design to use readily available networking hardware and software.
- **Support for manufacturer-specific extensions:** Allow custom extensions while maintaining a cohesive protocol structure.
- **Scalability:** Adapt to diverse applications, from small systems to large, complex installations.
- **Extensibility:** Facilitate future extensions and adaptability to evolving requirements.
- **Ease of configuration:** Support dynamic device discovery and plug-and-play capabilities.
- **Efficient and predictable bandwidth usage:** Optimize bandwidth use and ensure predictability in network requirements.
- **Sub-network flexibility:** Allow flexible use of sub-net addressing and routing to suit network design.
- **Fault tolerance:** Ensure resilience against failures and minimize user intervention for network recovery.

As you see, a lot of the ideas SHIFTY brings to the table aren't new ideas at all.

## But why didn't ACN take off then?

In January 2018 Wayne Howell wrote "ACN has received limited industry support and is complex to implement, particularly in low processing power products". This is most likely why it never got adopted at a scale in the event industry. The only remainder of ACN still present today is Streaming ACN (sACN). It's used as an alternative to Art-Net that utilized multicast instead of broadcast for more efficient bandwith usage. Other than that it brings nothing more to the table than Art-Net already did.

## Conclusion
38 years after DMX was invented every protocol since tries to be backwards compatible with the behemoth that is DMX. Sadly this is why we, the end users, still need to deal with all the overhead that it brings with it.

With SHIFTY we try to change that. We try to reinvent fixture control from the ground up. If you would also like to see this project succeed, you are welcome to take part in it's development. ...

Thank you!