---
layout: post
title: PID - Controlled Automatic Ball Balancer
description:  For the Introduction to Mechatronics course, I co-engineered an electromchanical system designed to automatically balance a steel ball on a tilting platform. The device uses a closed-loop feedback control system where a touchscreen detects the ball's location and a Raspberry Pi executes a PID control algorithm to adjust servo position to counteract disturbances in real-time.
skills: 
- SolidWorks
- Mechanical Assembly
- GD & T
- COTS Implementation
- Microcontroller & Python Programming
- Control System
main-image: /mainimg.jpg
---

---
# The Challenge
The primary objective was to design a mechanism that is capable of balancing a steel ball on a flat platform. The mechanism has to be able to disturbances to the system and keep it stable. This system requires a position feedback input and precise actuation output to balance the ball on a specific position. A secondary challenge was to implement a remote manipulation of the system via BLuetooth.


# Design
The design of the platform requires a joint that only has two degrees of freedom, the tilt on the vertical and horizontal axes. The solution that we implemented was the universal joint, that is commmonly found on machineries. This allowed the platform to tilt freely on both axes.<br>

{% include image-gallery.html images="ujoint.png" height="300" %} <br>

# Prototyping and Fabrication
The mechanical components were 3D printed. During the initial assembly, we identified tolerance issues that affected the mechanism's assembly. The CAD model was iterated with adjusted tolerances and the components were re-printed to ensure precise fit.<br>

{% include image-gallery.html images="fabrication.png" height="300" %} <br>

# Control System and Logic

---

