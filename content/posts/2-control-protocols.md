---
title: "Not a New Idea 📚"
date: 2023-08-11T08:21:00.000Z
draft: false
language: en
featured_image: ../assets/images/posts/not-a-new-idea.jpg
summary: "Exploring the evolution of fixture control protocols and why it's time for a fresh approach with SHIFTY."
description: "A journey through the history of lighting control — from the invention of phase-cut dimmers to DMX and ACN — and how SHIFTY aims to revolutionize fixture control."
author: Lukas Runge
tags: 
  - History
  - DMX
  - ACN
---

## 🏛️ A Trip Through Fixture Control History

The story of lighting control is a fascinating one. Back in **1959**, the invention of **phase-cut dimmers** made it possible to control dimmers via a separate **0-10V control signal** for the first time. This innovation allowed dimmers, which produced the operating current for lamps, to be moved to a separate room 🏠.

When **Vari-Lite** introduced the first moving light (**VL0**) in **1981**, it was a game-changer 🎮. It made sense to take things a step further by generating the operating currents for the motors within the fixture itself. This advancement created a need for a protocol capable of controlling multiple attributes of a remote device.

To meet this need, the **USITT** standardized **Digital Multiplex (DMX)** in **1986**, based on the established **RS-485** protocol. DMX was the first digital protocol that allowed centralized control of distributed lighting technology 🌐. It enabled control over not just the attributes of a luminaire—like color, focus, and zoom—but also devices that weren't luminaires, such as curtain systems 🎭.

For a long time, DMX was robust and met industry requirements. However, as modern fixtures became more advanced, fewer fixtures could operate within a single DMX universe 🌌.

## 🚧 The Limitations of DMX and the Rise of Art-Net

To avoid the hassle of running multiple DMX universes onto one truss, the Ethernet-based **Art-Net** was developed. This protocol eliminated the one-universe-per-cable limitation by building on **UDP** using broadcast 🚀. However, it didn't adopt other advantages of modern network stacks. Essentially, it was a patch rather than a solution.

Recognizing the need for a more advanced protocol, **ESTA** worked on developing a new control protocol that leveraged modern networking advantages and met growing user expectations.

## 🧩 Enter ACN: A Noble Attempt

After three years of development, the **Architecture for Control Networks (ACN)** was released in **2006** as **ANSI Standard E1.17-2006** 📜. ACN was designed with ambitious goals:

- **Interoperability Across Manufacturers** 🤝: Enable equipment from different manufacturers to communicate effectively.
- **Many Sources, Many Sinks** 🔄: Support multiple sources and consumers of control data on the same network.
- **Single Network, Multiple Uses** 🎚️🎛️: Allow a network to support various independent applications.
- **Mainstream Protocol Compatibility** 🌐: Utilize standard network protocols without duplicating functionalities.
- **Leverage Off-the-Shelf Technology** 🛠️: Use readily available networking hardware and software.
- **Support for Manufacturer-Specific Extensions** 🔧: Allow custom extensions while maintaining cohesion.
- **Scalability** 📈: Adapt to diverse applications, from small setups to large installations.
- **Extensibility** ➕: Facilitate future extensions and adaptability.
- **Ease of Configuration** 🔌: Support dynamic device discovery and plug-and-play capabilities.
- **Efficient Bandwidth Usage** 📊: Optimize bandwidth use and ensure predictability.
- **Sub-Network Flexibility** 🗺️: Allow flexible use of sub-net addressing and routing.
- **Fault Tolerance** 🛡️: Ensure resilience against failures and minimize recovery efforts.

As you can see, many ideas that **SHIFTY** brings to the table aren't new at all 🔄.

## 🤔 So, Why Didn't ACN Take Off?

In **January 2018**, Wayne Howell wrote, "*ACN has received limited industry support and is complex to implement, particularly in low processing power products.*" This complexity likely hindered its widespread adoption 😕.

The only remnant of ACN still present today is **Streaming ACN (sACN)**. It's used as an alternative to Art-Net, utilizing multicast instead of broadcast for more efficient bandwidth usage 📶. Other than that, it doesn't offer more than what Art-Net already did.

## 📜 Conclusion: Learning from the Past

Thirty-eight years after DMX was invented, every subsequent protocol has tried to remain backward-compatible with this industry behemoth 🦕. Sadly, this means we're still dealing with the overhead and limitations it brings 😩.

With **SHIFTY**, we're aiming to change that 🛠️. We're reinventing fixture control from the ground up. If you'd like to see this project succeed, you're welcome to participate in its development 🙌.

We are looking for contributors to help us design, build and (probably most important) test SHIFTY. If you are interested, please reach out to us on [GitHub](https://github.com/oshifty) or via our [contact form](/contact).

Let's make lighting design a breeze together! 🌈
