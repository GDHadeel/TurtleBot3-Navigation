# TurtleBot3-Navigation

# Task 5: Launch TurtleBot navigation

## Description

This guide provides step by step instructions for setting up TurtleBot3 navigation using ROS Noetic. It covers installing necessary packages, setting up the environment, launching the simulation, creating a map using SLAM, and finally, launching the navigation.


## Prerequisites

* ROS Noetic installed on your system
* Ubuntu 20.04 (Focal Fossa)

### Step 1: Install TurtleBot3 Packages

  * First, update your package list and install the TurtleBot3 packages:
    ```bash
    sudo apt update
    sudo apt install ros-noetic-turtlebot3 ros-noetic-turtlebot3-simulations
    ```
    
  * Install dependencies:
    ```bash
    sudo apt install ros-noetic-navigation ros-noetic-slam-gmapping    
    ```

### Step 2: Set Up the Environment

  * Add the TurtleBot3 model to your .bashrc file:
    ```bash
    echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
    source ~/.bashrc
    ```
    
  * Source the ROS setup file:

    ```bash
    source /opt/ros/noetic/setup.bash  
    ```

### Step 3: Launch the TurtleBot3 Simulation

  * Launch the TurtleBot3 world in Gazebo:
    ```bash
    roslaunch turtlebot3_gazebo turtlebot3_world.launch
    ```
<p align="center">
  <img src="https://github.com/user-attachments/assets/9d99d603-dddb-4185-a3f9-4b447470c16f" alt="Robotic Arm Image 1" width="600" height="600">
</p>

![image](https://github.com/user-attachments/assets/9d99d603-dddb-4185-a3f9-4b447470c16f)

### Step 4: Create a Map Using SLAM

  * Launch the SLAM node with Gmapping:
    ```bash
    roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
    ```

  * Control the TurtleBot using the keyboard:
    ```bash
    roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
    ```
![image](https://github.com/user-attachments/assets/3401c612-3ea3-418e-b38f-1e6a1a8cbc9a)
![image](https://github.com/user-attachments/assets/7a19f1db-73ba-4e7d-8d0a-5c3154b10794)
![image](https://github.com/user-attachments/assets/64206435-f176-4fb9-85e6-e5679b09e58e)

  * After exploring the environment and building a map, save the map by running the following command in a new terminal:
    ```bash
    rosrun map_server map_saver -f ~/map
    ```

### Step 5: Launch Navigation

  * Finally, launch the TurtleBot3 navigation with the saved map:
    ```bash
    roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
    ```
![image](https://github.com/user-attachments/assets/bf0def84-7cd9-4232-a4a4-0ec8bb8a3584)
    
## Acknowledgments
http://wiki.ros.org/turtlebot3

https://www.youtube.com/watch?v=QP-cxh8qUJQ









    
