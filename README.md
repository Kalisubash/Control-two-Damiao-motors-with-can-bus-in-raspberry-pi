# Control-two-Damiao-motors-with-can-bus-in-raspberry-pi
Python script to control two Damiao (DM) servo motors over CAN bus using the DM_CAN_Library. Includes motor initialization, velocity control, synchronized forward/reverse motion, and safe shutdown. Designed for Raspberry Pi or PC using a USB-CAN adapter with proper 120 Ω termination.


This repository contains a Python script to control two Damiao (DM) brushless servo motors (e.g., DM6006) using the DM_CAN_Library via a USB-to-CAN adapter.
The script initializes both motors, sets them into velocity control mode, and runs a synchronized test sequence:

Forward rotation
Stop
Reverse rotation
Safe shutdown
This example is ideal for robotics applications such as mobile robots, arms, mecanum wheels, industrial actuators, and research systems.

🛠️ Features

Control two DM motors simultaneously
CAN-based communication over USB
Velocity mode control (VEL)
Safe enable/disable operations

Works on:
Raspberry Pi 4
Linux PC
Windows (COM port change required)

🔌 Hardware Requirements
Component	Description
DM Motors	DM6006 or any supported Damiao motor
USB-CAN Adapter	CANable, Waveshare, MCP2515-USB, etc.
Power Supply	Appropriate voltage/current for your motor
Raspberry Pi / PC	Runs the Python script
CAN Bus Termination	120 Ω resistor required at each end
Wires	CANH, CANL, GND
🧩 Important Wiring
CAN Wiring
Motor CANH  → USB-CAN CANH  
Motor CANL  → USB-CAN CANL  
Motor GND   → USB-CAN GND  
USB-CAN     → Raspberry Pi / PC (USB)
Motor Power → External supply

⚠️ CAN Bus Termination

A proper CAN bus requires 120 Ω at both ends of the CAN network.
✔ If using one motor + USB-CAN, you still need:
1× 120 Ω on the motor side
1× 120 Ω inside the USB-CAN (some have built-in termination)
If your adapter does NOT have a termination resistor, you must add one like this:

CANH ----[120Ω]---- CANL


Without termination, you may see:
No communication
Random CAN errors
Motor not responding

📦 Software Requirements
Install Python packages
pip install pyserial

DM_CAN_Library

Ensure DM_CAN_Library.py is placed in the same folder as your script:

project/
│── DM_CAN_Library.py
│── dual_motor_test.py
│── README.md


Or install it globally if you have a packaged version.
