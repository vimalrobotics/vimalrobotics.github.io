---
date: 2023-09-05
title: Remote Haptic Communication System
subtitle: Affective Computing & Bidirectional IoT Interaction
image: '/images/remote_haptic_communication_cover.jpg'
category: embedded-iot
featured: true
---

## Overview

This project explores a **remote haptic communication system** that enables two geographically separated users to share **physiological signals and emotional states** over the internet.

The system focuses on **affective computing**, combining real-time heart-rate transmission, haptic feedback, visual emotion cues, and sound feedback to create a sense of presence between remote users.

---

## System Architecture

The system is implemented using **two ESP32-based devices**:

### Sender Device
- Measures heart rate (BPM)
- Publishes heart rate data over **MQTT**
- Hosts a web interface for emotion selection
- Sends emotion state events (animation + sound)

### Receiver Device
- Subscribes to heart rate and emotion topics
- Reconstructs heartbeat rhythm using LED pulses
- Displays emotion-specific animations
- Plays corresponding sound or haptic feedback

![System Overview](/images/heart_system.png)

---

## Communication Flow

1. Heart rate is measured and converted to BPM
2. BPM data is transmitted via MQTT
3. Receiver reconstructs pulse timing from BPM
4. LED and haptic feedback synchronize with heartbeat
5. Emotion states trigger visual and audio responses

This separation ensures **low latency**, scalability, and platform independence.

---

## Embedded Networking & Provisioning

From a **product-design perspective**, the system includes a robust onboarding flow:

### Default Access Point Mode
- Device boots in **AP mode** if no Wi-Fi is configured
- Hosts a local configuration web page
- User enters:
  - Wi-Fi credentials
  - MQTT broker details
  - Authentication token

### Persistent Storage
- Credentials and tokens are stored in **EEPROM**
- Device automatically reconnects on reboot
- AP mode is re-enabled only if connection fails

This design allows **non-technical users** to set up the device without reflashing firmware.

---

## Hardware Design

![3D Printed Enclosure front](/images/Remote haptic communication 3d printed case front.jpeg)
![3D Printed Enclosure back](/images/Remote haptic communication 3d printed case back.jpeg)

- Custom **3D-printed enclosure**
- Separate compartments for:
  - Power
  - Sensor
  - Haptic actuator
  - Audio output

![Internal Electronics](/images/Remote haptic communication electronics.jpeg)

- ESP32 (sender & receiver)
- Heart rate sensor
- Haptic motor / LED driver
- Audio feedback module

---

## Interaction Design

### Physiological Channel
- Heartbeat reproduced using LED pulse timing
- Creates intuitive, non-verbal feedback

### Emotional Channel
- Predefined emotional states
- Each emotion mapped to:
  - Display animation
  - Sound or vibration pattern

The combination allows **implicit (heartbeat)** and **explicit (emotion selection)** communication.

---

## Product Perspective & Applications

This system was designed as a **platform**, not a one-off prototype.

**Potential applications:**
- Long-distance relationships
- Telepresence and emotional bonding
- Mental health support
- Assistive and wellness devices
- Human-centered IoT products

---

## Key Learnings

- Physiological data requires careful temporal reconstruction
- MQTT enables scalable, low-latency communication
- UX matters as much as hardware in IoT products
- AP-based provisioning greatly improves usability
- Emotional feedback benefits from multimodal interaction

---

[▶ Watch system demonstration video](https://your-video-link)


> *This project demonstrates the integration of embedded systems, networking, human–computer interaction, and product-oriented design in a real-world IoT context.*
