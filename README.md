# stopy_people_detection(October 2018)

----
## General Info

Author: Ragesh Ramachandran

This package contains the basic framework to run a robot in the Gazebo Simulator with ROS. The map and rosbag was provided by Ingeniarius Ltd, Portugal.

rosbag files: https://mega.nz/#F!h2JH0KbL!vcG7FXrRs_8_k-P984z1UQ

----
## Assumption

You should have ROS Kinetic and Gazebo 7 installed on Ubuntu 16.04.
Install the following dependencies:

```
sudo apt install ros-kinetic-move-base ros-kinetic-nav-core ros-kinetic-amcl ros-kinetic-map-server
```

Clone this packages into your workspace (assuming it is at */home/your_user/catkin_ws*):

```
cd ~/catkin_ws/src
git clone https://github.com/EnigmaRagesh/stopy_people_detection.git
```
Install the following dependencies:

```
sudo apt install ros-kinetic-move-base ros-kinetic-nav-core ros-kinetic-amcl ros-kinetic-map-server
```
Then compile it
```
cd ~/catkin_ws
catkin_make
```


----
## Usage

To start up the Gazebo environment with the CTCV and 1 Robot do:

```
roslaunch ctcv_gazebo ctcv.launch
```

And in a separate terminal, start the localization and navigation software of the robot:

```
roslaunch ctcv_gazebo robot.launch
```
----
## Development

Perform several active detections in parallel: leg detection with laser, people detection with normal images, people detection with depth images (and/or eventually point cloud images to extract the 3d position of the people, if you cannot do it directly from the depth image information), and then possibly have a fusing node to make sure that you trim false positives and reliably detect a person with the information from all these different sources, and the lighting conditions, as you propose.

- In a first stage, it would be nice if you can reliably detect that people in the environment.

- In a second stage, it would be nice if you can extract the 3D position of these people in the map.

- In a third stage, it would be nice if you can use the information from the two (or more) robots and the persons' position to distinguish if they  are looking at the same person or discriminate if these are different people.

- Finally, gathering all the information, it would be nice to have a list of all the unique people detected in the environment and their positions.

