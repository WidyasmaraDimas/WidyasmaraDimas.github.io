---
layout: post
title: The Precision Pioneers: Bottle Transport Crane
description:  For my Introduction to Engineering Design course, my team, The Precision Pioneers, and I engineered a custom bottle transport device from concept to functional prototype. The objective was to automatically move three bottles over a one-inch square extrusion barrier. My team designed the mechanical components in SolidWorks, validated the structural integrity using FEA, and fabricated the parts using 3D-printing and laser cutting. Finally, an Arduino microcontroller was programmed to control the servos and motors, enabling the device's automated function.
skills: 
- SolidWorks
- Mechanical Assembly
- GD & T
- COTS Implementation
- Microcontroller & C Programming
- Automatic algorithm
- Structural Analysis
main-image: /CAD_Plain.png
---

---
# The Challenge
The objective for this project was to design and fabricate a device capable of automatically transporting three bottles from one place to another over a one-inch square cross section extrusion. A key constraint was that the bottles cannot be harmed and the task needed to be completed under 30 seconds without human intervention.


# Design & Analysis

### **Design Ideas:**
The key inspiration for our crane-like design was the gantry crane, usually found on shipyards. We found that the vertical and horizontal transportation of crates by the gantry crane inspiring and it became a big part of the final product. We mainly studied the mechanism by which the gantry crane moves containers.

{% include image-gallery.html images="/Gantry.jpg" height="400" %} 

### **CAD & Modeling:**
Our team designed the complete mechanical assembly in SolidWorks, with an emphasis on a high-strength crane structure. Geometric dimensioning and tolerancing was implemented for a sturdy fitment and the integration of COTS hardware. 
I was responsible in designing the claw mechanism, with the challenge of grabbing three bottles with one mechanism and one servo. The design idea that I implemented consists of two rack and pinion gear mechanism and three attached grippers two ensure consistency and simplicity. 

{% include image-gallery.html images="/Gripper.png" height="400" %} 

### **Analysis & Validation:**
A finite element analysis of the edge of the rails was conducted to ensure that the mechanism can carry a load of at least 1-kg. From the simulation, it was seen that the ABS material can withstand the given load with minimal deflection and stress.

{% include image-gallery.html images="/Sim.png" height="400" %} 


# Prototyping and Fabrication
FDM 3D-printing was used to fabricate the whole custom-designed grippers and rail guides, which allowed for complex geometries. The main crane chassis were laser-cut from balsa wood for strong and precise fabrication. This iterative design process allowed us to quickly test and validate design choices, such as the shape of the gripper and gear tolerances for lifting mechanism.


# Automation and Integration
To achieve fully autonomous functionality, an algorithm was created in C program by testing the prototype. An addition of a joystick allows manual operation of the mechanism while simultaneously providing a button to activate the automatic process of moving the bottles. The algorithm controlled the sequence of servos and DC motors to transport three bottles with 100% success rate.

---
