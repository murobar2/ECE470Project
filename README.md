# ECE470Project
ECE 470 - Introduction to Robotics Final Project  
Team Members: Raymundo Muro Barrios, Joaqin Malik, and Jakob Leiva  
Hello! Welcome to our README. This will include an in-depth and intuitive summary of our codebase.  
For now, it's a work in progress!  
Make sure to come back next update for a more detailed experience where we will get a chance to wow you with our big brains and introductory knowledge of robotics.  


# Rover main script
Script Name: Threaded child script: Robotnik  
Description: The main drive script for the base of the rover that controls the "random drive" and the function for the rover to approach a sample when it has been identified.  

The main rover script has two functions currently: wait and sysCall_threadmain.  

The wait function is a simple function that creates a "wait" feature similar to that of python or most other scripting languages in Lua which doesn't currently have a native wait function.  

The sysCall_threadmain function dictates the rover motion. It first initializes, then writes the four wheels to each of the motors. 
Then it performs a check to see if the blobs are detected. If blobs were detected, it stops moving, then waits half a second before moving to approach the sample that was detected. If no blobs were detected, it begins its pattern of "random motion" turning and moving to find a new sample.  

# Camera Views and Blob Detection
Our robot is simulated to have 2 camera feeds for operator review and one blob detector specific camera.
Script Name: blob_camera customization script
Description: This script filters the image seen by the blob detector camera. It selects only red objects, and feeds the modified image to blob_camera child script.
The filter screens for RBG values and proportion of image taken up by the blob detected. It outputs a live view as well.

Script Nmae: blob_camera child script
Description: This script initializes the blob detecting camera. It also opens the detected objects packet, and extracts the number of detected objects, and their positions relative to the sensor. 

The next step is to use this information to allow the robot to make decisons and navigate towards objects of interest.



Till next time.
TEAM ACEs
Autonomous Collection Explorers
