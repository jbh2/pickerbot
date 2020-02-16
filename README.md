# pickerbot
ECE 470 Project 

Team members: Jenny Chu, Joseph Hong, Mohamed Radwan


This repository is for the pickerbot fruit picking robot simulation for ECE 470. This project will be using V-REP version 3.6.0 & Coppelia 4.0.0. The goal of this project is to simulate a robot that can move on its own, while picking fruits from a tree. Secondary goals include moving from one tree to the next, and sorting different types of fruits into bins. 

For the Project Update 1, we will demonstrate our robot stopping its movement after detecting an object.. The robot will use a proximity sensor attached to its wrist, and will rotate its base until it detects the tree. Currently, we are using a while loop that iterates and moves the robot base in small increments. Using sim.persistentDataRead and sim.persistentDataWrite, we are able to pass on the proximity data from the sensor's threaded script into the UR3's script. Once the sensor value reads '1', the robot is instructed to stop moving, since the movement only occurs when the sensor value is '0' (when there is no tree present). We will try and make the movement of the robot smoother, because right now the robot has to stop after each iteration, which is not very efficient. We will also try and switch to a vision sensor, since it will be more versatile in the future. Currently, the proximity sensor was much easier to work with, which is why we used it. 


