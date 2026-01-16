---
date: 2020-08-20
title: Face Detection Welcome System
subtitle: Embedded Vision & Human Interaction
image: '/images/face_detection_parts_2.jpg'
category: embedded-iot
featured: false
---

## Overview

The **Face Detection Welcome System** is an embedded vision–based interactive system designed to detect human presence, recognize faces, and respond with **audio greetings and guided interactions**.  
The system integrates **ESP32-CAM**, **Arduino**, motion sensing, and **text-to-speech synthesis** to create a human-centered entry experience.

---

## System Block Diagram

![Face Detection Block Diagram](/images/face_detection_block_diagram.jpg)

---

## Circuit Diagram

![Face Detection Circuit Diagram](/images/face_detection_circuit.jpg)

---

## System Explanation (Based on Block Diagram)

The system operates as a **multi-stage pipeline**, combining sensing, vision processing, control logic, and human interaction.

### 1. Human Presence Detection (PIR Sensor → Arduino)

- A **PIR sensor** continuously monitors motion near the entry point.
- When motion is detected, a digital signal is sent to the **Arduino**.
- This acts as a **power-efficient trigger**, ensuring the camera and vision pipeline activate only when required.

---

### 2. Control & Actuation Layer (Arduino → Motors)

- The **Arduino** serves as the primary control unit for:
  - Processing PIR sensor input
  - Driving **motors** (e.g., door mechanism, camera pan/tilt, or indicator movement)
- Upon valid detection, the Arduino can:
  - Activate motors
  - Notify the vision subsystem through **serial communication**

---

### 3. Vision Acquisition (ESP32-CAM)

- The **ESP32-CAM** captures live image frames once triggered.
- It streams visual data internally to the **face detection module**.
- The ESP32-CAM is optimized for:
  - Low-cost embedded vision
  - Real-time face detection under constrained resources

---

### 4. Face Detection Processing

- Captured frames are processed using **face detection algorithms**.
- When a face is detected:
  - A detection flag or event is generated
  - Relevant contextual information (e.g., presence confirmed) is forwarded

---

### 5. Text-to-Speech Generation

- Face detection output is passed to **Google Text-to-Speech**.
- The system dynamically generates:
  - Welcome messages
  - Calming or instructional voice prompts
- This enables **natural human interaction** without screens or physical input.

---

### 6. Audio Interaction (Voice Output)

- The synthesized speech is delivered through a **speaker or audio module**.
- Users receive immediate feedback upon entry, improving:
  - Accessibility
  - User comfort
  - Engagement

---

## Data Flow Summary

PIR Sensor
↓
Arduino ────→ Motors
↓
Serial Communication
↓
ESP32-CAM
↓
Face Detection
↓
Google Text-to-Speech
↓
Voice Output

---

## Core Technologies

- ESP32-CAM (Embedded Vision)
- Arduino (Control & Actuation)
- PIR Motion Sensor
- Face Detection Algorithms
- Google Text-to-Speech (Audio Interaction)

---

## Applications

- Office reception systems
- Educational institutions
- Smart public entry points
- Assistive and calming environments

---

## System Demonstration Video

<iframe
  width="100%"
  height="420"
  src="https://www.youtube.com/embed/kPMmHl-kV-g?si=8XKet-5bbjmyIYu6"
  title="System demonstration video"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>

---

## Key Learnings

- Designing vision systems under embedded constraints
- Power-efficient event-driven architectures
- Human-centered interaction without graphical interfaces
- Integration of sensing, vision, and audio feedback