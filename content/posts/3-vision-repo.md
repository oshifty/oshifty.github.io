---
title: "Making the DX enjoyable 🎉"
date: 2023-09-01T07:30:00.000Z
draft: false
language: en
featured_image: ../assets/images/posts/visualizer.png
summary: The vision repo offers a virtual playground to test design concepts early, using web technologies to simulate device communication.
description: The vision repo offers a virtual playground to test design concepts early, using web technologies to simulate device communication.
author: Lukas Runge
tags:
    - Prototype
    - Software
---

## 💡 Thinking Outside the Drawing Board

Instead of going back to the drawing board 🎨 and inventing a new protocol out of real-world context, we decided it's best to try out ideas early. This way, we spend less time on speccing non-feasible ideas 🚫💡. That's where the **vision repo** comes in! It's our virtual playground 🛝 for show technology, simulating both communication between different end devices (hosts) and internal device communication (between microprocessors and peripherals).

## 🧰 Our Tech Toolbox

To make "playing on the playground" fun and efficient 😄, we're using modern web technologies:

- **Node.js** 🏃‍♂️ — Runtime environment
- **SvelteKit** 💻 — Backend and frontend framework
- **TCP** 🌐 — Communication between hosts
- **WebSocket** 📡 — Communication with peripherals
- **three.js** 🎨 — Library for 3D graphics with WebGL

## 🚀 How the Vision Repo App Works

So, how does this all come together? Let's dive into an example! 🏊‍♂️

A peripheral object (e.g., a motor fader 🎚️) is instantiated by calling an endpoint of the website (e.g., `/motorfader`). The frontend (client) automatically establishes a WebSocket (WS) connection to the backend (server), connecting reactive elements of the page (like our motor fader) bidirectionally to the backend. In actual devices, such communication is usually handled via Serial Peripheral Interface (SPI) or Inter-Integrated Circuit (I2C).

Communication between hosts (multiple instances of the entire program) happens over the network using the Transmission Control Protocol (TCP). Since TCP is "reliable" 🔒, there's no need to check if the transmission was successful—it's like having a trustworthy messenger who always delivers! 📬

## Enusuring Robustness ✨
By creating this virtual environment, we're able to test and refine our ideas in a fun and interactive way, ensuring robustness before implementation. It's all about making the development process as smooth and enjoyable as possible! 🎈

If you are a technician or developer, we invite you to join us on this journey. We are looking for contributors to help us design, build and (probably most important) test SHIFTY. If you are interested, please reach out to us on [GitHub](https://github.com/oshifty) or via our [contact form](/contact).

Let's make lighting design a breeze together! 🌈