# ECE470 Final Project: ACE (Autonomous Collector Explorer)
ECE 470 - Introduction to Robotics Final Project  
Team Members: Raymundo Muro Barrios, Joaqin Malik, and Jakob Leiva  
Hello! Welcome to our README. This will include an in-depth and intuitive summary of our codebase.  


# ACE Rover Script
Script Name: Threaded child script: Robotnik_Chassis_Kinematics.text  
Description: The main drive script for the base of the rover that controls the sample search protocol, allows the rover to move towards a detected sample, and progresively aligns the rover with a sample before collection. 

The sysCall_threadmain function dictates the rover motion. It first initializes, then writes the four wheels to each of the motors. 
It then performs a check to see if blobs are detected. If blobs are detected, it begins adjusting its wheel speeds and points towards the detected sample. If no blobs were detected, it begins its pattern of "random motion" turning and moving to find a new sample. Currently, the searching protocol is simply turning in a wide arc to the right, but in future works, more advance algoriths, and even mapping abilities, could be added to ACE.

When a sample is detected, the rover will read in the information about distance and heading from the camera sensors. The Robotnik chassis is programmed to approach the sample, adjusting its wheel speed as needed to keep the sample heading as close to zero as possible, or in other words, directly ahead. In order to keep the movement of the chassis as smooth as possible, the heading correction is progressive, and depends on how far the sample is, enabling the rover to adjust to the changing terrain as it nears the sample. Additionally, the heading correction script allows for a small tolerance of a few degrees, allowing the chassis to move smoothly and straight, without having to adjust its heading constantly, causing jerky motion. 

-Sample Collection

As the ACE chassis approaches a sample, it will slow down and proceed to drive above the sample. ACE will stop once the sample is detected in the rear camera sensor. It will proceed to adjust its wheel speeds to align the sample with the UR3's optimal collection position. Once the sample is in the optimal location with respect to the reart camera sensor, the chassis stops and sample collection is conducted. 

The robotnik chassis is programmed to wait for 8 seconds for suction between the robotic arm and the sample to occur, and begins to locate the next sample as the current sample is dumped in a collection bucket by the UR3.

# UR3 Arm Movemeent and Suction
Script Name: Threaded child script-UR3
Description: The main UR3 script controls the arm motion and trajectory. In addition, it contains the procedure for placing objects--acquired via the end-effector--into the containers mounted on the side of the rover.

The main function contains the code for aquiring desired positions and actuating the robot arm in its tucked, ready, pick-up, and bin placement modes. the forward kinemtaics has been heavily used to find the positions for the different setting modes of the UR3 arm. Code has been written with the intent of using inverse kinematics to find more accurate joint angles for the UR3 to arm to increase collection capability. Further development of inverse kinematics still needs to be done before implentation.

The sucker connector also contains a script that actuates the suction gripper to extract target objects.


# Camera Sensors and Blob Detection Scheme
ACE is fitted with 2 camera sensors used for blob detection and navigation, as well as 2 cameras used simply to provide a view from ACE's perspective.

Front Script Name: Sensing_Blob_Detection_Setup_Front.text and Sensing_Blob_Detection_Analysis_Front.text

Rear Script Name: Sensing_Blob_Detection_Setup_Rear.text and Sensing_Blob_Detection_Analysis_Rear.text

Description: These scripts filters the image seen by the blob detector camera. They select only red objects above a certain size and outputs the distance, and heading towards the closest sample seen by the camera sensor.
The distance and heading information output by the front sensor is used to navigate to samples, while the heading and distance from the rear sensors is used to align and stop the Robotnik chassis in an ideal location for sample collection, where the UR3 arm can reach and pick up the sample.


Till next time.
TEAM ACEs
Autonomous Collection Explorers
