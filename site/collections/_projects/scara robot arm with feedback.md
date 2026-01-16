---
date: 2024-02-12
title: Vision-Guided SCARA Robot
subtitle: Closed-Loop Visual Servoing with AprilTags
image: '/images/scara_cover.jpg'
category: robotics
featured: true
---

## Overview

This project demonstrates a **vision-guided SCARA robotic arm** operating under
**closed-loop visual feedback**. A camera mounted in the workspace observes
AprilTags attached to the end-effector and target objects, enabling
real-time pose estimation and corrective control.

The system closes the loop between **perception and actuation**, allowing the
robot to compensate for mechanical inaccuracies, servo backlash, and
calibration drift.

---

## Mechanical Assembly

![SCARA Robot Assembly](/images/scararobot_assembly.jpg)

The SCARA arm consists of:
- Two rotational joints for planar motion
- A rigid vertical structure for stiffness
- Servo-driven actuation suitable for educational and research use

The mechanical design emphasizes repeatability while remaining lightweight and
easy to reconfigure during experimentation.

---

## Control & Software Architecture

![SCARA Robot Programming & Control](/images/scara_robot_programming.jpg)

The control stack was implemented using **ROS**, with the following pipeline:

- AprilTag-based pose estimation from camera input
- Transformation of detected poses into the robot base frame
- Inverse kinematics solver for joint angle computation
- Servo command generation with feedback-aware correction

The visual feedback loop continuously updates the robot’s pose estimate,
enabling **real-time correction during motion**.

---

## Technical Stack

- ROS (robot middleware)
- AprilTag detection for visual localization
- Camera-based pose estimation
- Inverse kinematics for SCARA configuration
- Servo-based actuation and joint control

---

## Key Contributions

- Implementation of a **vision-based closed-loop control system**
- Integration of perception directly into the motion control pipeline
- Calibration-aware corrections to compensate for mechanical and sensing errors
- Demonstration of visual servoing on a low-cost robotic platform

---

## Learning Outcomes

- Practical challenges of visual servoing in real systems
- Sensitivity of closed-loop control to camera calibration and latency
- Importance of coordinate frame alignment in vision-guided robotics
- Trade-offs between mechanical precision and software correction

> *This project strengthened my understanding of perception-driven control and
highlighted the role of vision as a feedback sensor in robotic manipulation.*
