# Armada
Objective:
A robotic arm that can be controlled remotely through detected arm movements across my 15-10 meter room. 
Made from salvaged electronics and controlled through an IMU-tracking gestural wristband.

Status: In development

Refer to screenshot for a diagram example of model.

goals:
- Make setting up personal workspaces more efficient 
- Make interesting room decor
- be resourceful with current already owned hardware

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

Inventory:
- 2 DC motors 
    - coreless Motos
-  IR receiver photodiode.
    -captures invisible infrared light signals from a hand held remote beacon
- EV3 motherboard
    -signal conversion power routing.
    -input low-voltage digital-signals( code, sensor reading)
    -translated to massive, high current electrical power output 
    -managing highspeed data calculations
- infrared sensor to sense proximity.
- 1 DC brushed motor 
    - spins incredibly fast with little torque
- 1 feedback circuit motor
    - counts the rotations of the motor 
- Interface controlpad



https://wokwi.com/projects/399309284079035393