# pickerbot - An automated fruit picking robot
This repository is for the pickerbot fruit picking robot simulation for ECE 470 Spring 2020.

The goal is to simulate a robot that can move on its own, while picking fruits from a tree. Secondary goals include moving from one tree to the next, and sorting different types of fruits into bins. 

## Getting Started
The simulation files for V-REP/CoppeliaSim are saved with .ttt extension. To run, the files should be opened as File > Open Scene... with V-REP v3.6.0 or later. Scripts for individual components of the simulation have been included for reference; however, most use of the scripts will require specific setup of the scene within CoppeliaSim.

## Project Update 1:
### Files:
Proximity_sensor threaded child script

UR3 threaded child script

test.ttt (CoppeliaSim Scene)

### Summary:
We will demonstrate our robot stopping its movement after detecting an object. The robot will use a proximity sensor attached to its wrist, and will rotate its base until it detects the tree. Currently, we are using a while loop that iterates and moves the robot base in small increments. Using sim.persistentDataRead and sim.persistentDataWrite, we are able to pass on the proximity data from the sensor's threaded script into the UR3's script. Once the sensor value reads '1', the robot is instructed to stop moving, since the movement only occurs when the sensor value is '0' (when there is no tree present). We will try and make the movement of the robot smoother, because right now the robot has to stop after each iteration, which is not very efficient. We will also try and switch to a vision sensor, since it will be more versatile in the future. Currently, the proximity sensor was much easier to work with, which is why we used it. 

[Project Update 1 Demonstration](https://youtu.be/38Osir12bx4 "Have a nice Day!")

## Project Update 2:
### Files:
blobTo3dPosition_sensor

Target_Sphere

Test_UR3_IK.ttt (CoppeliaSim Scene)

### Summary:
For this second update, a 3D blob detector is used to locate the detectable object (green). The coordinates of the object are sent to the target of the inverse kinematics (IK) tip-target pair. The target is moved to the detected object and by inverse kinematics, the robotic arm is moved so the tip is also positioned at the detected object.


To setup the kinematic chain, set each joint of the UR3 to 'inverse kinematics mode'. Group the visible and triangulated model of each link. The UR3 does not contain any script. Create a dummy, 'tip', and attach to the end effector of the UR3. Add a second dummy, 'target', and link to the tip dummy as an IK tip-dummy pair. Using the Kinematics Module, make an IK group using the tip dummy and set the base as the UR3 base. Constraints should be set to x, y ,z and alpha-beta. This sets up the IK solution to match the x, y, z position and the z-axis of the tip dummy to the target dummy. Set the calculation method to the damped resolution method (DLS). The model becomes unstable when the target moves out of range of the tip if the calculation method is set to pseudo inverse although this method is faster. All other default settings can be kept.

Add a 3d blob detector to view the space in front of the UR3. Create a static sphere to represent the 'apple' and setup the 3d blob detector to only detect this 'apple'. Since dummy models can not be dynamically moved, a second sphere, 'target_sphere', is created to be the parent of the target dummy. Using sim.persistentDataWrite within the 3d blob detector script, the location of the detected apple is sent to target_sphere and read using sim.persistentDataRead. sim.setObjectPosition is then used to move the target_sphere and attached dummy target to the apple. By IK, the UR3 is positioned so the tip matches the location of the dummy target which is now located at the apple.

[Project Update 2 Demonstration](https://youtu.be/ZUpGvyd_rsQ ":D")

## Built With
V-REP v3.6.0

CoppeliaSim v4.0.0.

## Team members
Jenny Chu

Joseph Hong

Mohamed Radwan
