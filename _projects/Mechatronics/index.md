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
The mechanical components were 3D printed. During the initial assembly, we identified tolerance issues that affected the mechanism's assembly. The CAD model was iterated with adjusted tolerances and the components were re-printed to ensure precise fit. Heated inserts were used as a method of fastening the components to ensure a strong connection. <br>

{% include image-gallery.html images="fabrication.png" height="300" %} <br>

# Control System and Logic
The brain of the project was a _Raspberry Pi Pico H_ programmed in MicroPython. A PID controller was implemented to manage the system's stability. It utilizes a feedback loop where the touchscreen provided the coordinates of the ball (x,y). Then, the PID controller function calculates the output required to correct the position of the ball. Lastly, the output values are sent to the servos to tilt the plate.<br>

Below is the control logic used for the PID controller. The PID controller function utilizes a function that takes multiple input values and return the system response of the PID. The input values are the setpoint (center point coordinate of the screen), the ball position, the three PID multiplier, the error of the previous iteration, the summation value, and the time recorded when the previous iteration was completed. The output value on the code is the output response itself, the integral summation, and time recorded at the end of the function. The error, integral, and the time recorded will be inputted into the next function iteration for a successful PID system.<br>

```python
def pid_controller(setpoint, measured_value, Kp, Ki, Kd, last_error, integral, last_time):
    current_time = time.ticks_ms()
    dt = time.ticks_diff(current_time, last_time) / 1000 # time difference in seconds

    if dt == 0:
        return 0, last_error, integral, current_time

    error = setpoint - measured_value
    integral += error * dt
    derivative = (error - last_error) / dt

    output = (Kp * error) + (Ki * integral) + (Kd * derivative)
    return output, error, integral, current_time
```
<br>

# Advanced Features and Integration
Once the primary function of balancing the ball was stable, we expanded the system's functions. A *Bluetooth* module was added to allow a mobile phone to change the ball's center point remotely. *Joystick control* was added that modifies the target coordinates in the code, allowing the user to move the ball around the plate while the system maintains stability. <br>

# Outcome
The final prototype succesfully balanced the ball when disturbed and responded accurately to Bluetooth and joystick commands. The project was a comprehensive exercise of mechatronics integration, where program, electronics, and hardware are of equal importance. I learned the importance of tight mechanical tolerances for control systems - loose joints introduce a "play" that makes PID tuning difficult. Additionally, choosing a universal joint over other joints proved to be a significant advantage in simplifying the mechanical linkage.<br>

# Demo
 <p style="text-align:center;">{% include youtube-video.html id="vRDW4piRGKY" autoplay = "false" %}  </p><br>
 <p style="text-align:center;">{% include youtube-video.html id="vpUHNOjhh5c" autoplay = "false" %}  </p><br>
---

