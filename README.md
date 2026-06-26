# Armada
Objective:
A robotic arm that can be controlled remotely through detected arm movements across my 15-10 meter room. 
Made from salvaged electronics and controlled through an IMU-tracking gestural wristband.

Status: In development

Refer to screenshot for a diagram example of model.

goals:
- Make setting up personal workspaces mroe efficient 
- Make interesting room decor

Mechanics:
-A button is turned on the wrist band that kickstarts the mechanism for tracking arm movements.
-Arm movements are tracked through the IMU chip measuring velocties and movements encriptying them into bluetooth signals for the arm
-Arm's camera is used to detect the user into the range allowing the arm to work
-Arm's camera correct's the arm's movement to match the user. 
-Arm uses both wristbadn signals and camera detectiosn to correct itself and creat accurate outputs.
- 2 motors at the base of the arm to provide x, z & y rotation
- 1 motor on the elbow of the arm to improve range and precision
- 3 motors for the claw that help it grasp objects.
- A motherboard is installed into hte abse of the arm to recive singals from wristband and camera to send outputs in precise motor movements 