# Imperium
### An Autonomous, Sensor-Driven Chessboard with Electromagnetic Piece Control

**Author:** Aarav Singhania  
---

## Abstract

**Imperium** is a fully autonomous chessboard that detects and moves pieces using a precision electromagnetic gantry, per-square Hall-effect sensing, and CNC-style motion control. The system integrates custom mechanical design, multi-PCB electronics, and firmware-level motion planning to deliver seamless, repeatable gameplay without manual calibration.

---

## System Overview

```mermaid
flowchart LR
    Pieces[Chess Pieces — Magnets]
    Sensors[Hall Sensor Matrix — 64 Squares]
    Mux[16:1 Multiplexers]
    MCU[ESP32 Master Controller]
    Drivers[TMC2209 Motor Drivers]
    Motors[Stepper Motors — T-Bot Gantry]
    Magnet[Electromagnet]

    Pieces --> Sensors
    Sensors --> Mux
    Mux --> MCU
    MCU --> Drivers
    Drivers --> Motors
    MCU --> Magnet
```


## Project Media

### Completed System

<p align="center">
  <img src="images/imperium_overview.jpg" width="600">
</p>

<p align="center">
  <em>Figure 2: Fully assembled Imperium chessboard</em>
</p>

### Videos
- 🎥 demonstration video: *(link)*


---

## Hardware Architecture

### Mechanical Subsystem

![image](https://github.com/user-attachments/assets/50e8c8e2-8ba4-4c7f-9a4a-bf9df8d5cbbd)


<p align="center">
  <em>CAD Figure: T-Bot gantry layout and belt routing</em>
</p>

**Gantry Design**
- Type: **T-Bot (CoreXY derivative)**
- Motors: 2× NEMA 17
- Linear motion: 2× MGN12 rails (450 mm)
- Drive: GT2 belts & pulleys
- End effector: Electromagnet (custom mount)

**Design Rationale**
- Compact footprint compared to CoreXY  
- Sufficient precision for chess (no micron-level requirement)  
- Reduced part count and cost  

---

## Sensing Architecture

### Hall Sensor Matrix
```mermaid
flowchart LR
    Square1[Square 1]
    Square2[Square 2]
    SquareN[Square 64]
    Mux1[16:1 MUX]
    MCU[ESP32]

    Square1 --> Mux1
    Square2 --> Mux1
    SquareN --> Mux1
    Mux1 --> MCU
```

<p align="center">
  <em>Figure 5: 64-square Hall-effect sensor grid</em>
</p>

- Sensors: **KTH-1601 (46 Gs threshold)**
- 1 sensor per square (64 total)
- Mounted beneath ~3 mm acrylic

**Why Hall Sensors**
- Instantaneous response  
- No ghosting (unlike reed switches)  
- Reliable removal detection  

---

### PCB Sheet Layout
```mermaid
flowchart TB
    PCB1[Hall PCB Sheet 1\n16 Sensors]
    PCB2[Hall PCB Sheet 2\n16 Sensors]
    PCB3[Hall PCB Sheet 3\n16 Sensors]
    PCB4[Hall PCB Sheet 4\n16 Sensors]
    Master[Master PCB]

    PCB1 --> Master
    PCB2 --> Master
    PCB3 --> Master
    PCB4 --> Master
```
<p align="center">
  <img width="1549" height="443" alt="image" src="https://github.com/user-attachments/assets/f73844ed-6b2d-4f5b-b489-c5b84b5b5fde" />
  <img width="1129" height="613" alt="image" src="https://github.com/user-attachments/assets/2986e8ea-5849-4472-bf4a-f83741cb089a" />

</p>

<p align="center">
  <em>Figure 6: Hall sensor PCB sheet (100 mm × 400 mm)</em>
</p>

Each PCB sheet contains:
- 16 Hall sensors  
- 1× 16:1 multiplexer  
- Local decoupling capacitors  
- Ribbon cable interface  

Total sheets: **4**

---

## Control Electronics

### Master Control Board

<p align="center">
  <img width="687" height="693" alt="image" src="https://github.com/user-attachments/assets/7c01dde1-3aa7-4aa2-8ba8-0a09ad2e6410" />
  <img width="1066" height="654" alt="image" src="https://github.com/user-attachments/assets/936f3372-4393-4579-ac14-d43b7329d3f4" />
</p>

<p align="center">
  <em>Figure 7: Master PCB functional block diagram</em>
</p>

**Core Components**
- MCU: **ESP32**
- Motor drivers: **2× TMC2209 (UART)**
- Power:
  - 12 V rail (motors + electromagnet)
  - Buck converter → 3.3 V logic
- Electromagnet switching via transistor

All schematics and footprints were custom-designed in KiCad.

---

### UART Motor Control
Chess pieces are moved exclusively along square edges rather than diagonals. This design choice:

Prevents collisions with stationary pieces

Simplifies motion planning

Ensures consistent and predictable movement paths

The gantry executes all moves as a sequence of orthogonal segments.

UART enables:
- Sensorless homing  
- Stall detection  
- Current tuning  
- Advanced diagnostics  

---

### Control Flow

1. **Board State Detection**  
   Hall sensor matrix scans current piece positions.

2. **Move Translation**  
   Chess moves converted into constrained paths.

3. **G-Code Generation**  
   Custom G-code enforces non-diagonal movement.

4. **Execution**  
   G-code executed by **FluidNC** on ESP32.

---


## Bill of Materials (BOM)

<p align="center">
  <img width="1896" height="808" alt="image" src="https://github.com/user-attachments/assets/e014ec14-6406-42a5-a177-552a8acb103d" />

</p>

📎 **Full BOM:**  
https://docs.google.com/spreadsheets/d/1yp7t6AiXMwJCAfVlhCX7udocGjks9lOOFWkv4rPJByo/view

---

## Results

- Reliable autonomous gameplay  
- Accurate per-square detection  
- Consistent homing and positioning  
- No recalibration required between games  

---

## Future Work

- Chess engine integration  
- Companion UI / mobile app  
- Faster traversal paths  
- Noise reduction  
- Fully enclosed consumer-ready housing  

---

## References

- CoreXY reference — https://corexy.com  
- Gantry design pitfalls — https://drmrehorst.blogspot.com  


---



**PCB**






