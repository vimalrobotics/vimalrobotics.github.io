---
date: 2025-01-05
title: Laptop-Based Educational Robot Platform
subtitle: Open-Source Robotics Education
image: '/images/laptop_bot_cover_2.jpg'
category: research
featured: true
---

## Overview
An open-source robotics platform designed for education and experimentation.  
The system uses a laptop as the primary compute unit to lower hardware cost while allowing students to experiment with real robotics software stacks.

## Goals
- Accessibility
- Modularity
- Open-source learning

## Current Work
- Platform architecture
- Educational use-case design
- Documentation and tooling
- Electronics and PCB development
- Encoder-based odometry validation

## Hardware Design

### Robot Control Circuit
![Laptop Bot Circuit](/images/lap_bot_circuit.jpg)

**Description:**  
This circuit integration shows how all major components of the robot are interconnected, including:

- ESP32 controller for motor control and sensor interfacing
- SmartElex motor driver controlling two DC motors
- AS5600 magnetic encoders for wheel feedback
- MPU6500 IMU for orientation estimation
- OLED display for system feedback
- Battery voltage sensing circuit
- Emergency stop and power control wiring

The layout demonstrates power routing, signal connections, and peripheral integration required for a compact educational mobile robot.

---

### PCB Layout
![Laptop Bot PCB Layout](/images/lap_bot_pcb_layout.jpg)

**Description:**  
The custom PCB consolidates robot electronics into a compact and robust module, featuring:

- ESP32 mounting area for control and wireless connectivity
- Dual AS5600 encoder connectors
- Dedicated MPU6500 placement for stable IMU orientation sensing
- OLED display interface
- Motor driver signal interface
- Battery voltage measurement circuitry
- Emergency stop terminal connection
- Power switching and regulation sections

The board layout is optimized for compact integration inside the robot chassis while maintaining easy access for experimentation and maintenance.

---

## Future Direction
- Classroom deployment
- Curriculum integration
- Expanded robotics experiments and modules

## Encoder Odometry Test
A demonstration of encoder-based odometry testing is available here:

<iframe width="560" height="315" src="https://www.youtube.com/embed/OhLbHPKgwjI?si=LxA4Nd1QGYIgQvtS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>