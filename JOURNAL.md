---
title: "Imperium"
author: "Aarav Singhania"
description: "A self moving chessboard controlled by electro magnets"
---

## **5/24/2025 Log 1 Deciding a Gantry**
Some of the main things I want to keep in mind while deciding a gantry is the cost and the size of the gantry, who wants to play chess on a 5 feet x 5 feet chessboard? 
Before deciding a gantry I wanted to lay out what were the bare minimum requirements my gantry should be able to achieve. 
### *The gantry should:** ###
+ Have high precision ( chess pieces not colliding on each other )
+ Be robust, a chessboard is something that would have belts, motors, pulleys and etc moving all the time, it needs be able to not wear out too soon.
+ Strong enough to support the weight of the electromagnet mechanism
+ High repeatability (be able to return to the same position multiple times
---
**Note**: Precision and repeatability do not need to be on the level of something like a 3D printer for a project such as this. Tolerances can be higher for this gantry as compared to a gantry needed for a 3D printer.

With this information I researched multiple different types of gantries and I landed on the coreXY. A popular and common gantry used in all sorts of projects including 3D printers. Motor control is simple with 2 motors controlling the movement of the gantry, horizontal movement is achieved from both motors spinning in the same direction, vertical by two opposite direction and diagnal movement is done by spinning only one motor.

![CoreXy implementation](https://corexy.com/reference.png)

A corexy gantry is composed of at least 4 pulleys, 2 motors, 3 linear rods ( or guides ) with 2 belts. After picking some choosing some components I designed a implementation of the CoreXy mechanism. I settled on 2 Nema 17 motors and linear rods as my main componenets. I designed 3d printed mounts and pulleys to connect the parts but the implementation had a problem, the gantry was too big, with the COREXY's strengths of  precision and speed was the issue the space needed to accomodate such a large design, my current implementation was already over 600mm width.
![yZ1mRqmg0R](https://github.com/user-attachments/assets/7d137424-c771-49b1-9551-27206f75b042)

After researching different smaller implementations I landed on H-Bot. H-bot is'nt the most common design and you wont see it in designs such as 3D printers because its not necessarily precise or fast enough for a 3D printer but it should work fine for a chessboard. Next session im going to start designing a H-Bot implementation
**Time Spent: 4 hours**
