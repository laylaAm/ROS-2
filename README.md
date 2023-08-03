# ROS-2
# Requirements

- Oracle VM VirtualBox Manager version 7.0

- Ubuntu-18.04.6-desktop-amd64.iso

- ROS melodic

# Install ROS on Remote PC

```linux
$sudo apt update
$sudo apt upgrade
$wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh
$chmod 755 ./install_ros_melodic.sh 
$bash ./install_ros_melodic.sh
```

# Install Dependent ROS Packages
```linux
$ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
```

# Install TurtleBot3 Packages

```linux
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3
```

# Set TurtleBot3 Model Name

``` linux
$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
```

# Execute Gazebo

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslunch turtlebot3_gazebo turtlebot3_world.lunch
```
![saml1 (1)](https://github.com/laylaAm/ROS-2/assets/139586277/a136f6cd-be85-408f-9780-fe01d7715d21)

![saml1 (2)](https://github.com/laylaAm/ROS-2/assets/139586277/706da746-9f98-45a9-acdc-e7cda94cba6c)

# Execute SLAM 
In this case, we use gmapping that is general slam package.

File> New Tap

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```

![saml2](https://github.com/laylaAm/ROS-2/assets/139586277/0b1d8361-c79c-4032-9b33-6fbfa503ec24)

# Execute keypad

File> New Tap

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

# Map output

File> New Tap

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$rosrun map_server map_saver -f ~/map
```
out and close terminal ( Execute keypad ) and ( Execute SLAM ).

# Activate Gazebo

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```
![Salm3](https://github.com/laylaAm/ROS-2/assets/139586277/b5100a8c-0229-49e8-aecd-a26d703f9111)
