---
date: 2023-03-15
title: Stormbreaker
subtitle: Assistive Autonomous Towing Robot (ROS)
image: '/images/project_1.jpg'
---

## Overview

**Stormbreaker** is an assistive autonomous robotic platform designed to tow a wheelchair
safely and reliably in real-world environments.  
The system was developed as my final year research project and resulted in an
**IEEE conference publication**.

The project focuses on bridging autonomous navigation research with practical,
human-centered deployment constraints such as safety, reliability, and user trust.

---

## Problem Statement

Individuals using wheelchairs often face challenges navigating long distances
in indoor and semi-structured environments. Existing assistive solutions either
require continuous human control or lack sufficient safety guarantees for
autonomous operation.

The goal of Stormbreaker was to design a robotic system capable of:
- Autonomous navigation alongside humans
- Safe towing of a wheelchair
- Real-world deployment using affordable hardware

---

## System Architecture

The robot is built around a **ROS-based modular software architecture**, enabling
clear separation between perception, planning, and control layers.

**Key Components**
- ROS navigation stack
- Differential drive mobile base
- Sensor fusion for localization
- Safety-aware motion control

The modular design allows the system to be extended or adapted for future
assistive robotics research.

---

## Navigation & Control

Stormbreaker uses ROS-based localization and path planning to operate autonomously
in indoor environments.

**Features**
- Map-based navigation
- Obstacle-aware path planning
- Velocity and acceleration constraints for user safety
- Fail-safe stopping behavior

Special attention was given to smooth motion profiles to ensure comfort and
stability while towing a wheelchair.

---

## Human-Centered Design & Safety

A core design principle of Stormbreaker was **human safety and comfort**.

Safety considerations included:
- Conservative speed limits
- Emergency stop handling
- Predictable motion behavior
- Robust recovery from localization loss

![Stormbreaker Navigation in RViz](/images/rviz.png)

These constraints shaped both the mechanical design and the control algorithms.

---

## Results & Validation

The system was validated through:
- Indoor navigation experiments
- Towing tests with a wheelchair load
- Repeated autonomous runs to evaluate reliability

Stormbreaker demonstrated consistent navigation performance and safe towing
behavior under real-world conditions.

![Stormbreaker](/images/strombreaker.jpg)

---

## Research Contribution

This work was published as an **IEEE conference paper**, contributing to the field
of assistive robotics by presenting a practical, deployable approach to autonomous
wheelchair towing using ROS-based systems.

---

## Key Learnings

- Real-world robotics requires balancing autonomy with safety
- Assistive systems demand conservative and predictable control
- ROS enables rapid development but requires careful system integration
- Human-centered constraints significantly influence algorithm design

---

## Future Work

Potential extensions include:
- Outdoor navigation capability
- Advanced human intention prediction
- Improved sensor fusion and redundancy
- Clinical user studies
