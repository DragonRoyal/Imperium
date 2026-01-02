# Imperium
### An Autonomous, Sensor-Driven Chessboard with Electromagnetic Piece Control

**Author:** Aarav Singhania  

---

## Overview

**Imperium** is a fully autonomous chessboard capable of detecting and moving chess pieces without human intervention. The system combines a precision electromagnetic gantry, per-square Hall-effect sensing, and CNC-style motion control to deliver reliable, repeatable gameplay.

Unlike novelty self-moving chessboards, Imperium was engineered with a focus on **low cost**, **being easy to build and manafacture**, and **transparency**. The board operates autonomously once powered, requiring no calibration or manual correction from the user.

---

## Project Media

> 📸 **Photos, videos, and demonstrations of the completed system**

<!-- Replace placeholders below with your media -->

### Photos
- `images/imperium_overview.jpg`
- `images/gantry_mechanism.jpg`
- `images/hall_sensor_pcb.jpg`
- `images/master_board.jpg`

### Videos
- **Gantry Movement Test:** *(link here)*
- **Piece Detection Demo:** *(link here)*

> Tip: GitHub supports embedded images and YouTube/Vimeo links.

---

## Key Features

- **Autonomous Piece Movement**  
  Chess pieces are moved beneath the board using an electromagnet mounted on a precision gantry.

- **Per-Square Piece Detection**  
  Each of the 64 squares is monitored using Hall-effect sensors for accurate and immediate state detection.

- **Sensorless Homing**  
  True (0,0) positioning achieved using TMC2209 motor stall detection—no limit switches required.

- **Collision-Safe Motion Planning**  
  All movement is constrained to square edges, preventing diagonal collisions with stationary pieces.

- **Modular Hardware Architecture**  
  Multi-PCB design improves manufacturability, reduces cost, and simplifies debugging.

---

## System Architecture

### Mechanical System

- **Gantry Type:** T-Bot (CoreXY derivative)  
- **Motors:** 2× NEMA 17 stepper motors  
- **Linear Motion:** 2× MGN12 linear rails (450 mm)  
- **Drive System:** GT2 timing belts and pulleys  
- **End Effector:** Custom electromagnet mount (3D printed)

The T-Bot gantry was selected to balance **compact size**, **cost efficiency**, and **sufficient precision** for chess piece manipulation.

---

### Sensing System

- **Sensors:** KTH-1601 Hall-effect sensors (46 Gs threshold)  
- **Layout:**  
  - 64 sensors (1 per square)  
  - Distributed across 4 PCB sheets (100 mm × 400 mm)

- **Signal Management:**  
  - 16:1 multiplexers (one per PCB)  
  - Only 4 MCU pins required to scan the entire board

Hall sensors were chosen over reed switches due to faster response times, lack of ghosting, and improved reliability.

---

### Electronics

#### Master Control Board

- **Microcontroller:** ESP32  
- **Motor Drivers:** 2× TMC2209 (UART-controlled)  
- **Power System:**  
  - 12 V rail for motors and electromagnet  
  - Buck converter (12 V → 3.3 V) for logic and sensors  
- **Electromagnet Control:** Logic-level transistor

All symbols and footprints were custom-designed in KiCad. The system primarily uses SMD components to enable stencil and hot-plate reflow soldering.

---

## Motion Control & Software

Imperium uses a CNC-inspired control pipeline:

1. **Board State Detection**  
   Hall sensor matrix determines current piece positions.

2. **Move Translation**  
   Chess moves are translated into constrained motion paths.

3. **G-Code Generation**  
   Custom G-code is generated to enforce non-diagonal movement.

4. **Execution**  
   G-code is executed using **FluidNC**, which drives the stepper motors.

This architecture is inspired by modern 3D printer firmware (e.g., Klipper) but optimized for ESP32 compatibility and reduced overhead.

---

## Design Considerations

- **No Diagonal Traversal**  
  Prevents accidental collisions with other pieces.

- **Relaxed Mechanical Tolerances**  
  Chess movement does not require micron-level precision.

- **Magnetic Field Isolation**  
  Sensor sensitivity and spacing were selected to prevent cross-square interference.

---

## Bill of Materials (BOM)

A detailed BOM was created to track electronics, mechanical hardware, raw materials, and miscellaneous components while optimizing cost and supplier consolidation.

📎 **BOM Spreadsheet:**  
[View BOM on Google Sheets](https://docs.google.com/spreadsheets/d/1yp7t6AiXMwJCAfVlhCX7udocGjks9lOOFWkv4rPJByo/edit?usp=sharing)

---

## Results

- Reliable, repeatable piece movement  
- Accurate real-time board state detection  
- Stable sensorless homing  
- Fully autonomous gameplay without user intervention  

The completed system performs consistently without requiring recalibration between games.

---

## Future Improvements

- Chess engine integration (local or cloud-based)
- Companion UI or mobile app
- Reduced gantry noise
- Faster move execution
- Enclosed, consumer-ready housing

---

## References & Acknowledgements

- CoreXY reference: https://corexy.com  
- Gantry design considerations: https://drmrehorst.blogspot.com  
---
**CAD**
![image](https://github.com/user-attachments/assets/50e8c8e2-8ba4-4c7f-9a4a-bf9df8d5cbbd)

**PCB**
<img width="687" height="693" alt="image" src="https://github.com/user-attachments/assets/7c01dde1-3aa7-4aa2-8ba8-0a09ad2e6410" />
<img width="1066" height="654" alt="image" src="https://github.com/user-attachments/assets/936f3372-4393-4579-ac14-d43b7329d3f4" />
 ![image](https://github.com/user-attachments/assets/55f2aaf5-2e43-40c6-b2fa-735ea2e7b1ca) ![image](https://github.com/user-attachments/assets/0641aafe-a7a1-4ce9-b599-06e4ffb9c0a8)




