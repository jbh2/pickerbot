# pickerbot - An automated fruit picking robot
This repository is for the pickerbot fruit picking robot simulation for ECE 470. The goal of this project is to simulate a robot that can move on its own, while picking fruits from a tree. Secondary goals include moving from one tree to the next, and sorting different types of fruits into bins. 

## Getting Started
The simulation files for V-REP/CoppeliaSim are saved with .ttt extension. To run, the files should be opened as File > Open Scene... with V-REP v3.6.0 or later. Scripts for individual components of the simulation has been included for reference; however, most use of the scripts will require specific setup of the scene within CoppeliaSim.

## Project Update 1:
### Files:
Proximity_sensor threaded child script
UR3 threaded child script
test.ttt (CoppeliaSim Scene)

We will demonstrate our robot stopping its movement after detecting an object. The robot will use a proximity sensor attached to its wrist, and will rotate its base until it detects the tree. Currently, we are using a while loop that iterates and moves the robot base in small increments. Using sim.persistentDataRead and sim.persistentDataWrite, we are able to pass on the proximity data from the sensor's threaded script into the UR3's script. Once the sensor value reads '1', the robot is instructed to stop moving, since the movement only occurs when the sensor value is '0' (when there is no tree present). We will try and make the movement of the robot smoother, because right now the robot has to stop after each iteration, which is not very efficient. We will also try and switch to a vision sensor, since it will be more versatile in the future. Currently, the proximity sensor was much easier to work with, which is why we used it. 


## Project Update 2:
### Files:
blobTo3dPosition_sensor
Target_Sphere
Test_UR3_IK.ttt (CoppeliaSim Scene)


## Built With
V-REP v3.6.0
CoppeliaSim v4.0.0.

## Team members
Jenny Chu
Joseph Hong
Mohamed Radwan





