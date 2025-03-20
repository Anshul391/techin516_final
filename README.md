# techin516_final

## Overview
This package sets up a ROS2 Python package named `move_turtlebot` and integrates an external repository inside it.

## Prerequisites
Ensure you have ROS2 installed and sourced properly. You also need Git for cloning repositories.

## Installation Steps

### 1. Create the ROS2 Package
Run the following command to create a new ROS2 package with Python build type:
ros2 pkg create --build-type ament_python move_turtlebot

### 2. Clone repository in the package directory and extract content

### 3. Build environment
colcon build

### 5. SSH into turtlebot
ssh <username>@<ip_address>

### 4. Add these to turtlebot and your pc .bachrc file
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
echo "source ~/TECHIN516/turtlebot_ws/install/setup.bash" >> ~/.bashrc
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
export ROS_DOMAIN_ID=30
export ROS_DISCOVERY_SERVER=<ip_of_your_laptop>:11811

### 5. Run a dds server on your pc
fastdds discovery --server-id 0

### 6. launch on robot
ros2 launch turtlebot3_bringup robot.launch.py

### 7. Connect to kinova arm
ros2 launch kortex_bringup gen3_lite.launch.py \
robot_ip:=<ip.of.the.arm> \
launch_rviz:=false

### 8. Run RVIZ
ros2 launch kinova_gen3_lite_moveit_config robot.launch.py \
robot_ip:=<ip.of.the.arm>

### 9. Run your package
ros2 run <package_name> <node_name>
