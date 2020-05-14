# ECE470Project: ACE
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

The main function contains the inverse kinemtaics for the UR3 arm. Future versions of the code will implement call functions to substitute the inverse kinematics code from the main code. In its place code for a trajectory path to the containers can be generated.

The sucker connector also contains a script that will actuate the suction gripper to extract target objects.


# Camera Views and Blob Detection
Our robot is simulated to have 2 camera feeds for operator review and one blob detector specific camera.

Script Name: blob_camera customization script
Description: This script filters the image seen by the blob detector camera. It selects only red objects, and feeds the modified image to blob_camera child script.
The filter screens for RBG values and proportion of image taken up by the blob detected. It outputs a live view as well.

Script Name: blob_camera child script
Description: This script initializes the blob detecting camera. It also opens the detected objects packet, and extracts the number of detected objects, and their positions relative to the sensor. 

The next step is to use this information to allow the robot to make decisons and navigate towards objects of interest.



Till next time.
TEAM ACEs
Autonomous Collection Explorers
