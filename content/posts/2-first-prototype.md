---
title: "First E2E Prototype 🎉"
date: 2024-10-02T21:00:00+02:00
draft: false
language: en
featured_image: ../assets/images/posts/prototype_repo_screenshot.png
summary: Today we are proud to announce the first working end-to-end prototype...
description: Today we are proud to announce the first working end-to-end prototype...
author: Hannes Rüger
tags:
    - Prototype
    - Desk
    - Fixture
    - Hardware
    - Software
---

Today we are proud to announce the first working end-to-end prototype. In just two days, we were able to build a fully functional prototype with just an ESP32 Dev Board to showcase how easy it is to implement SHIFTY. You can find everything on GitHub in the [oshifty/prototype](https://github.com/oshifty/prototype) repository.

## Idea

We wanted to test using an end to end prototype, so we needed to build a control desk and a fixture. For the fixture, we used an ESP32 C6 Dev Board, since it already has a built-in RGB led. That would be our fixture. Because that board does not have onboard ethernet, we decided to use wifi and were suprised how usable it was.

The Desk was build in software using a Node.js / TypeScript / SvelteKit stack. Using a shared protobuf file, we were able to implement the protocol with type safety on both ends easily.

## Connection & Data Flow

The Desk discovers SHIFTY compatible fixtures in the network using DNS Service Discovery (mDNS). Once found, it shows them in the UI with a _Connect_ button. Once clicked, it opens a TCP socket to the fixture and starts speaking the protobuf protocol. After a initial handshake, the desk requests

-   Information about the device (manufacturer, mode, version, ...)
-   The fixture definition (emitters, their attributes, value ranges, ...)
-   The current attribute values

Using this data, the Desk can now render a UI to control the fixture. It sends the new values to the fixture, which then updates its physical state.

## Next Steps

Although the initial e2e prototype is working, there are still a lot of things to do. We need to implement and test a lot of features, like for example instructions: In order to avoid having to send frequent updates for a value transition (e.g. a color fade), the desk can send a instruction to the fixture to perform the transition itself. This needs only one message and the values can all be computed locally on the fixture, instead of sending a lot of messages over the network.

## Contribution

There's still a lot of work to be done. Therefore, if you want to contribute, feel free to open an issue or a pull request on one of our repositories! We are happy to help you get started.
