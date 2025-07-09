4-SENSOR PARKING ASSISTANCE SYSTEM WITH LCD DISPLAY USING PIC16F877A


PROJECT DESCRIPTION


This project is a microcontroller-based parking assistance system developed using the PIC16F877A and four ultrasonic distance sensors. The system measures the distance to nearby obstacles in four directions: front, rear, left, and right. The measured distances are displayed in real-time on a 16x2 character LCD screen. Additionally, a passive buzzer provides audible feedback based on the proximity of the nearest obstacle. This system is designed to assist drivers or autonomous systems in avoiding collisions during parking or navigation in tight spaces.


KEY FEATURES


-Distance detection in four directions (front, rear, left, right)

-Real-time display of distance values on LCD

-Proximity-based audible feedback using a buzzer

-Uses CCS C and PIC16F877A microcontroller

-Simple, modular, and easily expandable code structure

-Can be used for educational, automotive, or robotic applications


HARDWARE COMPONENTS


-PIC16F877A microcontroller

-4 ultrasonic sensors (e.g., HC-SR04 or analog-compatible)

-16x2 LCD display

-Passive buzzer

-Resistors and jumper wires

-Power supply (5V regulated)

-Breadboard or printed circuit board (PCB)


SOFTWARE TOOLS


-MPLAB X IDE

-CCS C Compiler

-Proteus Design Suite (optional, for simulation)


CODE OVERVIEW


The code defines the trigger and echo pins for each ultrasonic sensor. The function measure_distance(trig, echo) sends a 10-microsecond trigger pulse and uses Timer1 to measure the echo pulse width. This width is converted to distance in centimeters using the formula:

-distance = 2 * time / 58

-Each sensor is read one by one to prevent ultrasonic interference. The distances are displayed on the LCD in two lines:

-Line 1: front and rear distances

-Line 2: left and right distances

-The minimum of the four distances is calculated. Based on this value, the buzzer is controlled:

-If the object is closer than 30 cm, the buzzer beeps

-The beep interval is shorter when the obstacle is closer

-If the object is farther than 30 cm, the buzzer remains off

-The beep interval is dynamically calculated using a simple map() function.


PROGRAM FLOW


-Initialize all sensors and LCD

-Measure distance from each sensor

-Display all four distances on the LCD

-Find the shortest distance

-Activate the buzzer based on the shortest distance

-Repeat continuously


DISTANCE RESPONSE LOGIC


-Distance > 30 cm → No buzzer sound

-30 cm ≥ Distance > 10 cm → Intermittent beep (interval based on distance)

-Distance ≤ 10 cm → Fast and continuous beeping


POSSIBLE IMPROVEMENTS


-Replace the buzzer delay logic with PWM for better tone control

-Add LED bar indicators or RGB lights for visual distance feedback

-Integrate direction-based audio messages or alerts

-Add Bluetooth module for mobile app integration

-Include EEPROM logging or data export over serial port
