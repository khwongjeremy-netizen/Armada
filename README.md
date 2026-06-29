# Armada

*  **Mechanical Reference Model:** Inspired by the 3D-printed [SmartBuilds.io MARK 1 Arm](https://smartbuilds.io/diy-robot-arm-arduino-hand-gestures/) design. 

A 6-axis Robotic arm that mimics arm movments from across a room( up to 15 meters away). It uses a wristband with a motion sensor and a small camera to track arm movements and copy gestures.

Status: In Development
(Proof of concept, Bill of materials for basic arm completed.)

Goals:
- Building an interactive assistant to optimize workspace efficiency
- Create a unique aesthetic that adds decor to room environment 

Theoretical Logic: 

1. Input: A user-worn wristband is intergrated with. an IMU sensor tracking linear velocities and spatial orientation data, transalting it to Bluetooth data
2. A camera built into the base verifies arm movements picked up through bluetooth checking it with video recording while also scanning the room to verify the user is within range 
3. Signals are converted into target PWM signals to series of servo motors to execute physical movement 

Model layout:

The arm achieves 6 degress of freedom by distribuitng physical loads across 7 motors:
* Base (1 Stepper Motor): A hgih torque NEMA 17 Motor sits in the abse pedestal to spin the entire arm left and rihgt.
* Shoulder(2 Servos): Two heavy-duty sevos work sisde-by-side to push and pull the heavy main arm forward and backward.
* Elbow (1 Servo): One Sevo controls the mid-joint to give the arm better reach and precision.
* Wrist (2 Servos): Two Servops let the wrist tilt up/down adn rotate side-to-side.
* Claw ( 1 Servo): One last servo operatesa the gripper fingers to clamp onto objects.

Testing and simulation:

* Testing model Mark 1 Arm through simulation on Wokwi[https://wokwi.com/projects/468107537102683137]
* Used Ai as a feedback and educational tool for project: [https://gemini.google.com/app/66d2c7d817efa6f5]
Refer to image for refrencing of inspired model.

Temporate Shopping list:

* Component/ QTY / USE

* Arduino Uno / 1 / The main brain that processes inputs and outputs
* HC-05 Bluetooth Module / 1 / Recieves bluetooth singals from wristband. 
* MG996R Servos / 6 / Powers the shoulder, elbow, wrist and gripper joints.
* PCA9685 Servo Driver / 1 / LEts the Arduino cleanly control all 6 servos at once.
* NEMA 17 Stepper Motor / 1 / High-torque motor for powering base
* A4988 Stepper Driver / 1 / Controls the stepper motor's accuracy
* 5V Battery pack (2200 mAh) / 1 / Provides high-voltage power to give the motorsfull torque. 
* Breadboard & Jumper Wires / 1/ Conncets all the components