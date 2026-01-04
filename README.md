# Open Source Smart Doorbell System

<img width="1185" height="600" alt="image" src="https://github.com/user-attachments/assets/d1c4d246-bde4-43be-b9dc-80ca0bfbd995" />


An open-source **DIY smart doorbell and intercom system** built around open protocols and self-hosted services.
The system provides **one-way video**, **two-way audio**, and **Home Assistant integration**, without relying on proprietary cloud services.

This project is ideal for learning about embedded Linux, streaming media, MQTT, and smart home integration.

---

## System Overview

The system consists of three main parts:

1. **Doorbell (embedded device)**
2. **Intercom (embedded Linux touchscreen device)**
3. **Server (Home Assistant + Media + MQTT)**

All communication is done locally using **RTSP/RTP**, **MQTT**, and open-source software.

---

## Architecture

### Media Streaming

* A central **MediaMTX** server runs on a server.
* The **doorbell** continuously publishes:

  * A **video stream**
  * An **audio stream**
* Both streams are sent to MediaMTX.

Consumers of these streams:

* **Home Assistant** (for live view and automations)
* **Intercom** (for live video and audio playback)

### Two-Way Audio

* The **intercom** publishes an **audio stream** to MediaMTX.
* The **doorbell** subscribes to this audio stream.
* This enables:

  * **Two-way audio**
  * **One-way video (doorbell → intercom / Home Assistant)**

---

## Home Assistant Integration

Home Assistant runs on the same server and provides automation and UI features.

### MQTT (Mosquitto)

* A **Mosquitto MQTT broker** runs inside Home Assistant.
* The **doorbell** connects to MQTT and publishes events.
* The doorbell appears as a **device** in Home Assistant.

### Doorbell Events

When the doorbell button is pressed:

* An MQTT event is published
* Home Assistant can:

  * Trigger the intercom wake-up
  * Play a sound on the intercom
  * Send push notifications
  * Trigger automations (lights, recordings, etc.)

### Day / Night Mode

* Home Assistant publishes the **time-of-day state** (light or dark) via MQTT.
* The doorbell subscribes to this topic.

LED behavior:

* **Daytime**

  * LED is normally **off**
  * LED **blinks on press**
* **Nighttime**

  * LED is normally **on**
  * LED **blinks off on press**

---

## Doorbell Software

* Fully **custom-written code**
* Uses:

  * `libgpio` for button and LED control
  * `paho.mqtt.c` for MQTT communication
* Responsibilities:

  * Publish button press events
  * Stream video and audio to MediaMTX
  * Subscribe to intercom audio stream
  * React to day/night MQTT topics

---

## Intercom Software

* Runs on **embedded Linux**
* Uses:

  * `ffmpeg` for media streaming
  * `lvgl` for the graphical UI
  * `libgpio` for hardware control
  * `paho.mqtt.c` for MQTT
* Video output:

  * Video is written directly to the **Linux framebuffer**
* Audio:

  * Plays doorbell audio
  * Publishes microphone audio for two-way communication

### Touchscreen

* Touchscreen is implemented via a **custom device tree overlay**
* The overlay:

  * Configures the SPI touchscreen device
  * Loads the correct driver
* Touch events are read from:

  ```
  /dev/input/event0
  ```

---

## Features

* One-way video (doorbell → intercom / Home Assistant)
* Two-way audio communication
* Local media streaming via MediaMTX
* MQTT-based event system
* Home Assistant device & automations
* Day/night LED behavior
* Fully self-hosted and cloud-free
* Open-source and extensible

---

## Components

All parts can be purchased from common online marketplaces:

* [Camera](https://nl.aliexpress.com/item/1005009234829192.html?gatewayAdapt=glo2nld)
* [Sound interface](https://nl.aliexpress.com/item/1005006196572718.html?gatewayAdapt=glo2nld)
* [Audio amplifier](https://nl.aliexpress.com/item/1005005926858790.html?gatewayAdapt=glo2nld)
* [Loudspeaker](https://nl.aliexpress.com/item/32832795528.html?gatewayAdapt=glo2nld)
* [Microphone](https://nl.aliexpress.com/item/1005007483195353.html?gatewayAdapt=glo2nld)
* [HDMI display](https://nl.aliexpress.com/item/1005009442086364.html?gatewayAdapt=glo2nld)
* [Ethernet HAT](https://nl.aliexpress.com/item/1005004437789277.html?gatewayAdapt=glo2nld)
* [Single Board Computer](https://nl.aliexpress.com/item/32839074880.html?gatewayAdapt=glo2nld)

---

## Project Structure

```
/doorbell-system
│── docs/                  # Documentation and diagrams
│ └── home-assistant.md    # Home Assistant & MQTT setup
│── hardware/              # Schematics and wiring
│── software/
│ ├── doorbell/            # Doorbell source code
│ └── intercom/            # Intercom source code
│── configs/               # MediaMTX, MQTT, HA configs
│── README.md              # This file
```

---
