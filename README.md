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

https://wokwi.com/projects/468093537466099713

https://wokwi.com/projects/399309284079035393

Shopping: 
6vx servo motor - MG966R Series 
Servo Driver PCA9685 
BAttery Pack(5V, 2200 mAh)
Arduino Uno
Arduino HC-05
Bread Board
Jumper Wires
NEMA 17 Servo Motor
A4988 Stepper Motor Driver 
LiPo 11.1V, 2200mAh,3s

https://wokwi.com/projects/468044397198469121


#include <Servo.h>

// 1. Create Servo Objects for the Arm Joints
Servo joints[6];
const int servoPins[6] = {3, 5, 6, 9, 10, 11}; // Digital PWM pins

// 2. Define Stepper Driver Pins (A4988)
const int stepPin = 4;
const int dirPin = 2;

void setup() {
  // Initialize Serial communication at 9600 baud rate
  Serial.begin(9600);
  
  // Attach all 6 servos to their physical data pins
  for(int i = 0; i < 6; i++) {
    joints[i].attach(servoPins[i]);
    joints[i].write(90); // Start every joint at a safe middle angle (90 degrees)
  }
  
  // Set Stepper driver pins as outputs
  pinMode(stepPin, OUTPUT);
  pinMode(dirPin, OUTPUT);
  
  Serial.println("=== 6-Axis Arm Simulation Online ===");
  Serial.println("Commands:");
  Serial.println("  1 to 6 : Sweep specific joint servo");
  Serial.println("  F / B  : Spin Stepper Base Forward / Backward");
}

void loop() {
  // Check if a command was typed into the Serial Monitor
  if (Serial.available() > 0) {
    char cmd = Serial.read();
    
    // --- Servo Joint Testing Logic ---
    if (cmd >= '1' && cmd <= '6') {
      int jointIndex = cmd - '1'; // Convert character '1'-'6' to index 0-5
      Serial.print("Testing Joint Servo #");
      Serial.println(jointIndex + 1);
      
      // Sweep the selected joint out and back to prove it moves cleanly
      joints[jointIndex].write(150);
      delay(300);
      joints[jointIndex].write(30);
      delay(300);
      joints[jointIndex].write(90); // Return to neutral
    }
    
    // --- Stepper Base Testing Logic ---
    else if (cmd == 'F' || cmd == 'f') {
      Serial.println("Spinning Stepper Base Forward...");
      digitalWrite(dirPin, HIGH); // Set direction
      for(int i = 0; i < 200; i++) { // Step 200 times
        digitalWrite(stepPin, HIGH);
        delayMicroseconds(2000);
        digitalWrite(stepPin, LOW);
        delayMicroseconds(2000);
      }
    }
    else if (cmd == 'B' || cmd == 'b') {
      Serial.println("Spinning Stepper Base Backward...");
      digitalWrite(dirPin, LOW); // Reverse direction
      for(int i = 0; i < 200; i++) {
        digitalWrite(stepPin, HIGH);
        delayMicroseconds(2000);
        digitalWrite(stepPin, LOW);
        delayMicroseconds(2000);
      }
    }
  }
}