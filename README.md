# 4-Sensor Parking Assistance System with LCD Display Using PIC16F877A

## Project Description
This project is a microcontroller-based parking assistance system designed with the PIC16F877A and four ultrasonic distance sensors. The system measures distances to obstacles in four directions: front, rear, left, and right. These distances are displayed in real-time on a 16x2 character LCD screen. A passive buzzer provides audible feedback based on the proximity of the closest obstacle. This system is useful for assisting drivers or autonomous systems in avoiding collisions during parking or in tight spaces.

## Key Features
- **Four-Direction Distance Detection**: Measures distances in front, rear, left, and right.
- **Real-Time LCD Display**: Displays distance values on a 16x2 LCD screen.
- **Proximity-Based Audible Alerts**: Buzzer feedback varies with the nearest obstacle's distance.
- **Microcontroller-Based**: Built around the PIC16F877A and written in CCS C.
- **Modular and Expandable**: Code designed to be simple, modular, and easily extendable.
- **Versatile Applications**: Suitable for educational, automotive, or robotic use cases.

## Hardware Components
- PIC16F877A Microcontroller
- 4 Ultrasonic Sensors (e.g., HC-SR04 or analog-compatible)
- 16x2 LCD Display
- Passive Buzzer
- Resistors and Jumper Wires
- Power Supply (5V Regulated)
- Breadboard or Printed Circuit Board (PCB)

## Software Tools
- **MPLAB X IDE**
- **CCS C Compiler**
- **Proteus Design Suite** (optional, for simulation purposes)

## Code Overview
- **Ultrasonic Sensor Logic**:
  - Each sensor has defined trigger and echo pins.
  - The function `measure_distance(trig, echo)` sends a 10-microsecond trigger pulse and calculates the echo pulse width using Timer1.
  - Distance is computed in centimeters using the formula:
    ```plaintext
    distance = 2 * time / 58
    ```
- **Reading Sensors**:
  - Sensors are read sequentially to prevent ultrasonic interference.
  - The LCD displays:
    - **Line 1**: Front and rear distances.
    - **Line 2**: Left and right distances.
- **Proximity Alerts**:
  - The minimum distance among the four sensors is calculated.
  - The buzzer behavior is based on the closest obstacle:
    - If distance > 30 cm: No sound.
    - If 30 cm ≥ distance > 10 cm: Intermittent beeping (shorter intervals for closer objects).
    - If distance ≤ 10 cm: Continuous fast beeping.
  - A simple `map()` function dynamically calculates the beeping interval.

## Program Flow
1. Initialize sensors and LCD.
2. Measure distance from each sensor.
3. Display all four distances on the LCD.
4. Calculate the shortest distance.
5. Control the buzzer based on the shortest distance.
6. Repeat the above steps continuously.

## Distance Response Logic
- **Distance > 30 cm**: No buzzer sound.
- **30 cm ≥ Distance > 10 cm**: Intermittent beeping (interval decreases with proximity).
- **Distance ≤ 10 cm**: Fast and continuous beeping.

## Possible Improvements
- Replace buzzer delay logic with PWM for better tone control.
- Add LED bar indicators or RGB lights for visual feedback.
- Integrate direction-based audio messages or alerts.
- Add a Bluetooth module for mobile app integration.
- Include EEPROM logging or data export via a serial port.

---
This project serves as a practical and adaptable solution for parking assistance. Its modular design and the potential for enhancements make it a great platform for further development in automotive and robotic applications.
