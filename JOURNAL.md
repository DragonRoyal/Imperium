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

After researching different smaller implementations I landed on T-Bot. T-bot is'nt the most common design and you wont see it in designs such as 3D printers because its not necessarily precise or fast enough for a 3D printer but it should work fine for a chessboard. Next session im going to start designing a H-Bot implementation
**Time Spent: 4 hours**

## **5/26/2025 - 5/29/2025 Log 2 Designing my Gantry & BOM work**
  A T-Bot gantry is really a fork of the coreXY and thus the same principles apply, the belts controlling X and Y direction must be pararell. The design of a T-bot gantry is pretty self explanatory, it looks like a T. The gantry would have 2 linear guides, 2 Nema 17 motors, 8 pulleys and 1 belt. The assembly of this gantry would be more effecient and cheaper since we traded the extra guide and belt for 4 more pulleys. To pick which linear guides I wanted I looked at the specifications and differences between the different MGN## rails. A rail such as MGN12 would be a low profile rail which would handle less load compared to a HGR12. I picked 2 MGN12 Rails which were each 450mm. ![image](https://github.com/user-attachments/assets/10248ef9-6df5-41af-a390-a7b097f2a167). The holes on the rail are too far spaced apart to just be directly connected so I made a 3d printed adapter to connect the two rails.

  Now, the hard part is actually making the full gantry with the other parts ( belts, pulleys, motors etc ). I made a wood board frame for the components to be placed on top with holes spaced 25mm apart. The first thing I needed was pieces to connect the linear rails with the wooden board. I designed 3 pieces for the two ends of the rail and the center. ![image](https://github.com/user-attachments/assets/150af9a0-781e-4325-9755-6c5045ff5a60). My vision for the implementation of the T-Bot gantry would be this, the red pulleys are idler pulleys and the blue ones being controlled by the motor. My drawing skills arent the best but it gives a general idea of the layout of the gantry, **note** the belts in the actual design would be pararal or else the tension would not be distributed evenly. I decided on small GT2 pulleys and some slightly bigger ones for the ones attached to the motor. I designed a motor mount and pulley mounts in order to hold the moving and idler pulleys. By convention NEMA 17 motors have the same X-Y dimensions so designing a motor mount was easier than I thought. I also had to design a a additional pulley mount to be connected to the guide rails. The biggest thing with the designing of these componenets are the positioning of the pulleys, the belts **must** be parallel. ![belt offset](https://github.com/user-attachments/assets/d40e193f-ad65-4821-a7b3-fc9e2b4b0491) This is not my sketch but its good for illustrating that even the belt thickness should be taken in account in this case im using a standard 6mm timing belt. After designing all my compoenents and placing them into a assembly I started making a belt but I constantly ran into issues of my belts not being parallel; sometimes a a pulley would be 2 mm displaced from another pulley, or sometimes I didnt take into account belt thickness but after trial and error I ended up with a parallel design ![Screenshot 2025-05-28 183847](https://github.com/user-attachments/assets/7df11b3c-aea9-48c8-bc2d-4b395a06463b)... actually I failed to notice the belts were intersecting through the linear guides. But it was'nt a hard fix and I adjusted all my pulleys a few milimeters higher in order to stop the clipping. I still had a few minor issues in my model, most notably different mates that were not fully defined but after fixing all the errors (I hope) I ended up with a finished product. ![Screenshot 2025-05-29 145640](https://github.com/user-attachments/assets/a4e7998d-85b0-485b-a92c-524842b15279). I still have a little bit of work left to do on some of the models like the pulley mount but the main design is pretty much done. It took me a span of 2-3 days to design the gantry as I ran into lots of different types of issues I never encountered before but some helpful websites that helped me were 
[basic philoshpy ](https://corexy.com/) and some [common pitfalls when designing a gantry](https://drmrehorst.blogspot.com/2018/08/corexy-mechanism-layout-and-belt.html)
**Time spent: 9 Hours**



