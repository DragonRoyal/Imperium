# Imperium

Imperium is a self moving chessboard which controls pieces through a H-BOT gantry moving a electromagnet. Each piece has a magnet underneath and each square has a hall sensor to detect where a piece is.

The board works with by having a 2 different microcontrollers, one has a gcode handler firmware that takes in GCODE and converts it motor movement, and the other has the "logic" of the chessboard which reads the 64x hall sensors using 4x 16:1 multiplexers, stores piece positions and then sends a request to a chess api to know what move to play next, for moving the pieces in a staircase type gcode gets generated which gets sent to the other microcontroller via uart. 

**CAD**
![image](https://github.com/user-attachments/assets/50e8c8e2-8ba4-4c7f-9a4a-bf9df8d5cbbd)

**PCB**
<img width="687" height="693" alt="image" src="https://github.com/user-attachments/assets/7c01dde1-3aa7-4aa2-8ba8-0a09ad2e6410" />
<img width="1066" height="654" alt="image" src="https://github.com/user-attachments/assets/936f3372-4393-4579-ac14-d43b7329d3f4" />
 ![image](https://github.com/user-attachments/assets/55f2aaf5-2e43-40c6-b2fa-735ea2e7b1ca) ![image](https://github.com/user-attachments/assets/0641aafe-a7a1-4ce9-b599-06e4ffb9c0a8)


