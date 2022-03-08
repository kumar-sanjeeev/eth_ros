# Programming for Robotics- ROS- ETH 
This repository contain solutions of the ros related exercise provided in the course [programming for robotics-ros](https://rsl.ethz.ch/education-students/lectures/ros.html). Video, lecture and exercise content all are available in the [site](https://rsl.ethz.ch/education-students/lectures/ros.html)

# System Setup
Course requires the use of `ROS-Noetic and gazebo environment` for simulation
```shell
# used this command to install the catkin build in noetic if not available

$ sudo apt install python3-catkin-tools python3-osrf-pycommon
```

For solving the exercise ros package will be build with following dependencies. Use the following commands to install the required `dependencies`
```
$ sudo apt install -y ros-noetic-hector-gazebo-plugins \
                    ros-noetic-velodyne \
                    ros-noetic-velodyne-description \
                    ros-noetic-velodyne-gazebo-plugins \
                    ros-noetic-pointcloud-to-laserscan \
                    ros-noetic-twist-mux`
```

## Exercise 1:
### Task Description

- Command a desired velocity to the robot from the terminal
- Use teleop_twist_keyboard to control your robot using the keyboard.
- Write a launch file in which new world environment will be added

### Solution:
- `rostopic pub /cmd_vel geometry_msgs/Twist '[0.5,0,0]' '[0,0,0]`
```html
<?xml version="1.0" encoding="utf-8"?>

<launch>

  <!-- Path to the world file -->
  <arg name="world_file"                            default="/usr/share/gazebo-11/worlds/robocup14_spl_field.world"/>

  <!-- Load Gazebo world -->
  <include file="$(find smb_gazebo)/launch/smb_gazebo.launch">
    <arg name="world_file"        value="$(arg world_file)"/>
  
  <!-- Loading the teleop_twist_keyboard Node -->
  </include>
    <node name="control" pkg="teleop_twist_keyboard" type="teleop_twist_keyboard.py" output="screen"/>

</launch>
```
### Result:
With the use of keyboard, commands can be given to the mobile robot to move in the football ground.

![Screenshot from 2022-03-08 20-05-44](https://user-images.githubusercontent.com/62834697/157307593-a157b5ac-f08a-446e-9b89-1879c047e0ad.png)




