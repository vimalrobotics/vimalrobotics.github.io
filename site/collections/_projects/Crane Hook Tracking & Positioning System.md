---
date: 2022-07-10
title: Crane Hook Tracking and Positioning System
subtitle: Autonomous Stabilization & Sensing
image: '/images/chtp_cover.jpg'
category: embedded-iot
featured: false
---

## Overview

The **Crane Hook Tracking and Positioning System** was developed as a **Techgium competition project** to improve operational safety and situational awareness in crane operations.  
The system enables **real-time tracking, positioning, and stabilization of a crane hook** using a combination of **wired and wireless ultrasonic sensing**, onboard processing, and a **telemetry-enabled controller unit**.

The project focused on **robust sensing under industrial constraints**, prioritizing reliability, redundancy, and operator usability over laboratory-grade precision.

---

## Problem Statement

Crane operators often lack direct visibility of the hook position when operating at height or over obstructed environments, increasing the risk of:
- Collision with structures
- Load instability
- Accidents due to blind spots

The objective was to design a **deployable sensing system** that can be mounted on the crane hook assembly to:
- Identify hook position and orientation in real time
- Transmit data wirelessly to the operator
- Provide collision awareness through a GUI

---

## System Architecture

The system is composed of three primary subsystems:

### 1. Sensor Layer (Hook-Mounted)

- **Wireless ultrasonic sensors** mounted on multiple sides of the hook
![Wired Ultrasonic Sensor](/images/chtp_wired_sensor.jpg)
- **Wired ultrasonic sensors** for redundancy and validation
- Weather-proof sensor enclosures with mechanical mounts
- Anti-locking curved gear mesh for stable orientation
![Wireless Ultrasonic Sensor](/images/chtp_wireless_sensor.jpg)

---

### 2. Main Controller Box (Telemetry Unit)

The **controller box acts as the core processing and communication unit**, integrating:

- **APM 2.8 Flight Controller**
- RF telemetry module
- GPS module
- Power management and battery monitoring
- Data logging and fail-safe mechanisms
![Components Inside Controller](/images/chtp_components.jpg)
The controller aggregates **both wired and wireless sensor data**, processes raw distance measurements, and transmits stabilized positional data to the ground station GUI.

![Controller Box](/images/chtp_controller_box.jpg)


---

### 3. Ground Station & GUI

- Real-time visualization of hook position and orientation
- Collision proximity alerts
- Operator-friendly interface designed for industrial use
- Comparison of simulation vs real-world data

![GUI Visualization](/images/chtp_testing.jpg)

---

## Implementation Details

### Sensor & Enclosure Mounting
- Sensors mounted on lower sheave plates
- Modular mount design adaptable to different crane types
- IP65/IP67-rated components for outdoor operation

![Prototype Assembly](/images/chtp_prototype.jpg)

### Data Flow
1. Ultrasonic sensors capture distance measurements
2. Data transmitted wirelessly to controller box
3. Controller filters noise and compensates latency
4. Processed data sent to ground station via telemetry
5. GUI displays real-time hook position and alerts

---

## Testing & Validation

### Indoor Testing
- Custom-built indoor test rig
- Validation of sensing accuracy and communication stability

![Indoor Test Setup](/images/chtp_card_board_box_test_setup.jpg)

### Industrial Testing
- Deployed on a **50-ton EOT crane**
- Validated under real industrial conditions
- Confirmed survivability in vibration and EMI-heavy environments

![Crane Hook Sensors Mounted](/images/chtp_crane_hook.jpg)
![Crane Hook ](/images/chtp_crane_hook2.jpg)
![Crane Hook ](/images/chtp_with_load_industrial.png)



---

## Technical Specifications

- **Ultrasonic Sensor Range:** 25 mm – 4500 mm  
- **Coverage Angle:** 70°  
- **Sensor Rating:** 5V, 30 mA  
- **Controller:** APM 2.8 Flight Controller with GPS  
- **Power:** 12V Li-Ion Battery (1800 mAh)  
- **Battery Life:** ~2–3 days continuous operation  
- **Data Transmission:** RF Telemetry  
- **Attachment:** Magnetic switch / fastened mount  
- **GUI Interface:** Application-based ground station  

---

## Challenges Addressed

- Communication latency in wireless transmission
- Sensor noise and environmental interference
- Blind spots due to sensor misalignment
- Real-time stabilization under dynamic crane motion

---

## Outcome

- Reached **final round of the Techgium competition**
- Successfully demonstrated real-time hook tracking
- Validated feasibility for industrial deployment
- Demonstrated reduction in operator blind spots

---

## Real-Time Testing
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZQRPcVxeY9U?si=MJIT7eil_cu0E8lZ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

---

## Key Learnings

- Industrial robotics demands **robustness over elegance**
- Redundancy is critical in safety-related systems
- Sensor fusion must tolerate packet loss and noise
- User-centric visualization is as important as sensing accuracy

---

## Future Scope (POC → MVP)

- Rigid industrial-grade enclosure redesign
- Motorized sensor angle adjustment
- Integration with existing crane dashboards
- Multi-crane monitoring capability
- Mobile application support

---

## References

- *Overhead Crane Positioning System*, Vol. 2, Issue 3, 2019  
- Wang et al., *Collision Avoidance Strategy for Auto Crane*, Sensors 2021  
- Du et al., *Attitude Estimation of Crane Hook*, ICICIP 2014  

---
