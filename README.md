🚍 CAN-Based Intelligent Bus Accident Prevention and Automatic Braking System Using LPC2129
📌 Project Overview

The CAN-Based Intelligent Bus Accident Prevention and Automatic Braking System is an embedded system designed to improve passenger safety by preventing potential collisions through intelligent distance monitoring and automatic speed control.

The system uses the LPC2129 ARM7 microcontroller and Controller Area Network (CAN) communication to exchange real-time information between multiple Electronic Control Units (ECUs).

An ultrasonic sensor continuously monitors the distance between the bus and nearby obstacles, while an ADC-based speed monitoring unit measures the vehicle speed. Based on the received distance and speed information, the system automatically adjusts the motor speed or activates braking when an obstacle is detected within a critical range.

The system also displays the vehicle's safety status, obstacle distance, and speed on an LCD.

🎯 Objectives
To prevent bus accidents using real-time obstacle detection.
To implement automatic braking based on obstacle distance.
To monitor vehicle speed using an ADC interface.
To establish communication between multiple ECUs using CAN protocol.
To improve passenger safety through an intelligent vehicle control system.
To provide real-time status information through an LCD display.
⚙️ Hardware Requirements
S.No	Components	Description
1	LPC2129 Microcontroller	ARM7-based main controller
2	Ultrasonic Sensor	Measures distance between the bus and obstacles
3	MCP3204 ADC	Analog-to-digital conversion
4	CAN Transceiver	CAN bus communication interface
5	DC Motor	Represents the bus motor
6	LCD Display	Displays distance, speed, and system status
7	Motor Driver	Controls motor operation
8	Power Supply	Provides required operating voltage
9	Connecting Wires	Hardware interconnections
💻 Software Requirements
Embedded C
Keil µVision IDE
Flash Magic
ARM7 LPC2129 Development Board
CAN Communication Protocol
LPC2129 Device Library
🏗️ System Architecture

The project consists of three main Electronic Control Units (ECUs).

ECU 1 – Obstacle Detection Unit
Uses an ultrasonic sensor to measure the distance between the bus and an obstacle.
Calculates the distance based on the ultrasonic echo pulse duration.
Transmits the measured distance through CAN communication.
Uses CAN Identifier 0x100.
ECU 2 – Vehicle Control Unit
Receives obstacle distance and vehicle speed information through CAN.
Processes the received information.
Determines the appropriate vehicle operating condition.
Controls motor speed using PWM.
Displays distance, speed, and safety status on the LCD.
ECU 3 – Speed Monitoring Unit
Uses the MCP3204 ADC to acquire analog input.
Converts the analog signal into a digital speed value.
Transmits the speed information through CAN communication.
Uses CAN Identifier 0x200.
🔄 Working Principle

The system operates through continuous communication between the three ECUs.

The ultrasonic sensor measures the distance between the bus and the obstacle.
ECU 1 processes the sensor output and transmits the distance through the CAN bus.
ECU 3 reads the analog speed input using the MCP3204 ADC.
The speed information is transmitted to ECU 2 through CAN communication.
ECU 2 receives both distance and speed information.
Based on the obstacle distance, the controller determines the safety condition.
The PWM output is adjusted to control the motor speed.
The LCD displays the current distance, speed, and safety condition.
📊 Automatic Braking Logic

The system uses the following distance-based control conditions:

Obstacle Distance	System Status	Motor Speed
≥ 100 cm	SAFE	100% of received speed
60–99 cm	CAUTION	75% of received speed
30–59 cm	ALERT	55% of received speed
< 30 cm	BRAKE	0%

Note: These are the distance thresholds and control percentages implemented in the current source code.

📡 CAN Communication Details

The CAN protocol is used to exchange information between the ECUs.

ECU	CAN Identifier	Data Transmitted
ECU 1	0x100	Obstacle distance
ECU 3	0x200	Vehicle speed
ECU 2	Receives both IDs	Processes distance and speed

The CAN communication enables the different control units to share information efficiently.

📂 Project Structure
text
CAN-Based-Intelligent-Bus-Accident-Prevention/
│
├── ecu1.c
│   └── Ultrasonic sensor and obstacle distance measurement
│
├── ecu2.c
│   └── Main control unit, LCD display and PWM motor control
│
├── ecu3.c
│   └── ADC-based speed monitoring using MCP3204
│
├── can2_init.h
│   └── CAN communication initialization and functions
│
├── delay.h
│   └── Delay functions
│
└── all_lcd_header.h
    └── LCD initialization and display functions

🔧 Implementation Details
1. Ultrasonic Distance Measurement

ECU 1 generates a trigger pulse and measures the echo pulse duration using the LPC2129 timer.

The distance is calculated using:

c
distance = time / 58;


The measured distance is transmitted through CAN using identifier 0x100.

2. ADC-Based Speed Measurement

ECU 3 communicates with the MCP3204 ADC using SPI communication.

The ADC reads the analog input and converts it into a digital value representing the speed.

The speed information is transmitted through CAN using identifier 0x200.

3. PWM-Based Motor Control

ECU 2 uses the LPC2129 PWM peripheral to control motor speed.

The PWM duty cycle is adjusted according to the obstacle distance and received speed information.

4. LCD Display

The LCD displays:

Operating mode (SAFE, CAUTION, ALERT, BRAKE)
Obstacle distance
Motor speed
🚀 Expected Output

The system continuously monitors obstacle distance and vehicle speed.

Depending on the detected distance, the system automatically changes its operating condition:

SAFE: Vehicle operates at the received speed.
CAUTION: Motor speed is reduced to 75%.
ALERT: Motor speed is reduced to 55%.
BRAKE: Motor output is stopped.

The corresponding information is displayed on the LCD.

🔮 Future Enhancements
Integration of GPS for vehicle location tracking.
GSM-based emergency notification to predefined contacts.
Integration of IoT for remote vehicle monitoring.
Real-time accident detection and emergency alert generation.
Advanced obstacle detection using multiple sensors.
Implementation of adaptive braking based on vehicle speed and stopping distance.
Integration with vehicle dashboard monitoring systems.
⚠️ Safety Disclaimer

This project is an educational embedded-system prototype intended to demonstrate CAN-based communication, obstacle detection, and automatic motor control.

The implementation is not certified or validated for controlling real passenger vehicles. Practical automotive deployment requires safety-rated hardware, redundant sensing, fault detection, braking-system validation, and compliance with applicable automotive safety standards.

👨‍💻 Author

Balasakthikumar

GitHub Repository:

CAN-Based Intelligent Bus Accident Prevention and Automatic Braking System Using LPC2129

⭐ Support

If you find this project useful for learning embedded systems, ARM7 microcontrollers, CAN communication, and automotive safety applications, consider giving this repository a star!
