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
![saml1 (2)](https://github.com/laylaAm/ROS-2/assets/139586277/2461c7f6-fe17-4335-b0a2-455fda7e34fd)


![saml1 (1)](https://github.com/laylaAm/ROS-2/assets/139586277/78fa43b6-af70-4d56-a7dd-8439538b6a9d)


# Execute SLAM 
In this case, we use gmapping that is general slam package.

File> New Tap

```linux
$cd catkin_ws
$source devel/setup.bash
$export TURTLEBOT3_MODEL=waffle_pi
$roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```

![saml2](https://github.com/laylaAm/ROS-2/assets/139586277/a46890bc-157a-4b9d-ac2f-a20070062992)

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

![Salm3](https://github.com/laylaAm/ROS-2/assets/139586277/601b12a3-d775-4cf2-8fbe-dd8530c4ff58)
