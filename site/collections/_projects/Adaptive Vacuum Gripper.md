---
date: 2021-03-18
title: Adaptive Vacuum Gripper
subtitle: Bio-Inspired Compliant Manipulation with Electrostatic Stiffness Control
image: '/images/gripper_cover.jpg'
category: research
featured: true

gallery:
  title: Robot Build Gallery
  images:
    - image: /images/main-components.jpg
      caption: Chassis assembly
    - image: /images/robot-mounting-check.jpg
      caption: Motor and gearbox
    - image: /images/fingers.jpg
      caption: Electronics mounted
    - image: /images/adaptive-gripper.jpg
      caption: Final testing
    - image: /images/tpu-material.jpg
      caption: Final testing
    - image: /images/gripper-holder-3dprint.jpg
      caption: Final testing
    - image: /images/laser_cutting.jpg
      caption: Final testing
    - image: /images/before-machining.jpg
      caption: Final testing
    - image: /images/3d-pringing-finger.jpg
      caption: Final testing
    - image: /images/3d-printing-links.jpg
      caption: Final testing
    - image: /images/dro-drilling.jpg
      caption: Final testing

---

## Overview

This project explores a **hybrid adaptive gripper** that combines **Fin Ray effect compliant fingers**, **vacuum suction**, and **electrostatic braking** to achieve **shape-adaptive grasping with controllable stiffness**.

The core idea was to overcome a common limitation of soft grippers:  
> *high adaptability but low load stability.*

By selectively **locking compliance using electrostatic brakes**, the gripper can switch between:
- **Soft, conformal grasping** for irregular objects  
- **Stiff, load-bearing holding** for pick-and-place and palletizing tasks  

This enables **multi-task manipulation using a single end-effector**, reducing tool changes and system complexity.

---

## Design Inspiration

The gripper design is inspired by two key research directions:

### 1. Fin Ray Effect (Festo Adaptive Gripper Fingers)
- Passive compliance using triangular rib structures
- Shape adaptation without complex sensing
- Widely used for fragile and irregular objects

### 2. Electrostatic Braking (DextrES)
- Thin, low-power electrostatic brakes
- Ability to **lock motion on demand**
- Originally developed for haptic feedback and stiffness modulation

**This project combines both concepts**, using electrostatic braking to actively control the stiffness of Fin Ray compliant fingers.

---

## Mechanical Architecture

![Exploded View](/images/gripper_exploded.jpg)

**Key components:**
- Fin Ray inspired flexible fingers using TPU Thermoplastic Polyurethane filament (3D printed)
- Central vacuum suction cups
- Electrostatic brake layers integrated along finger flex zones
- Modular base for industrial robot mounting (ABB test mount)

---

## Actuation & Electronics

![Control Electronics](/images/adaptive gripper pcb.jpg)

- **Controller:** ESP8266
- **Motor Driver:** DRV8825 (stepper control for vacuum and brake actuation)
- **Custom perf-board circuit** with JST connectors
- Separate power domains for:
  - Logic
  - Vacuum system
  - Electrostatic brake drive

The electrostatic brakes are energized only during **stiffness locking**, resulting in **low average power consumption**.

---

## Control Interface

![Mobile App](/images/gripper-mobile-app.png){: style="width:50%;" }

A **custom control interface** was developed using **MIT App Inventor**, enabling:
- Grasp mode selection (soft / stiff)
- Vacuum on/off control
- Manual release and reset
- Rapid experimentation during testing

---

## Grasping Strategy

### Soft Mode
- Fin Ray fingers deform freely
- Vacuum cups assist initial contact
- Ideal for fragile or irregular objects

### Lock Mode
- Electrostatic brakes engage
- Finger compliance is arrested
- Grasp becomes rigid and load-stable

![Components](/images/gripper_demo.png)

---

## Industrial Relevance

This hybrid approach enables **multi-function manipulation with a single gripper**:

**Example workflow:**
- Pick individual water bottles using compliant grasp
- Place bottles inside a carton
- Lift and palletize the filled carton
- No gripper change, no tool swap, no second robot

**Target applications:**
- Pick & place
- Palletizing
- Mixed object handling
- Logistics automation
- Human-safe collaborative robots

---

## Key Learnings

- Passive compliance reduces sensing requirements but limits load stability
- Electrostatic braking enables **mechanical intelligence**
- Stiffness modulation is more effective than force control alone
- Hybrid grippers can significantly reduce system complexity in real deployments

## Project Showcase

{% bookshop gallery-section
  title=page.gallery.title
  images=page.gallery.images
%}

---

## References & Background

- **Festo Adaptive Gripper (Fin Ray Effect)**
- **DextrES: Wearable Haptic Feedback via Electrostatic Braking**
- Fin Ray Effect Inspired Soft Robotic Grippers (Frontiers in Robotics & AI)

> *Additional design details, calculations, and experimental notes are available upon request.*

