# ROS1-ROS2-Bridge
### ROS1-ROS2 Bridge: This bridge allows for communication between ROS1 (e.g., ROS Noetic) and ROS2 (e.g., ROS Foxy). It facilitates the integration of systems and components that are still on ROS1 with those that have been upgraded to ROS2. This is particularly useful during the transition period from ROS1 to ROS2. The bridge translates messages and services between the two versions.

### 1- create workspace for ros noetic and ros2 foxy

### 2- Install Arduino_robot_arm package in ros noetic

### 3- Create ros1_bridge workspace and clone the package
```

mkdir -p ~/ros1_bridge_ws/src

cd ~/ros1_bridge_ws/src

```


### 4- Source ROS1 and ROS2 setup bash files
```

source ~/catkin_ws/devel/setup.bash

source ~/ros2_ws/install/setup.bash
```


![Screenshot 2024-07-10 193907](https://github.com/HAN6661/ROS1-ROS2-Bridge/assets/173714836/d3552d77-9d20-4b74-8d2d-544b0a329200)


### 5- Build the bridge package in its workspace
```

colcon build --packages-select ros1_bridge --cmake-force-configure --cmake-args
-DBUILD_TESTING=FALSE
```

### 6- test the bridge
```

source install/local_setup.bash

ros2 run ros1_bridge dynamic_bridge --print-pairs
```

### 7- launch the Arduino_robot_arm package
```
source /opt/ros/noetic/setup.bash

source ~/catkin_ws/devel/setup.bash

roslaunch robot_arm_pkg check_motors.launch

rostopic list

```

![Screenshot 2024-07-10 193925](https://github.com/HAN6661/ROS1-ROS2-Bridge/assets/173714836/019a8305-b9e9-4a1d-b5a7-0f13fcf7dbdb)

### 8- run the bridge
```
source install/setup.bash

ros2 run ros1_bridge dynamic_bridge
```
![Screenshot 2024-07-10 193944](https://github.com/HAN6661/ROS1-ROS2-Bridge/assets/173714836/98b1afc8-868c-4b73-bf9c-b433c8b74752)

### 9- echo /joint_states topic in ros2

```
source /opt/ros/foxy/setup.bash

ros2 topic echo /joint_states sensor_msgs/msg/JointState
```

![Screenshot 2024-07-10 193958](https://github.com/HAN6661/ROS1-ROS2-Bridge/assets/173714836/c3f51428-f833-4e77-ba49-138461c6b3b8)


## By following these steps, you can successfully bridge the communication gap between ROS1 and ROS2, allowing for an integrated system that leverages the strengths and functionalities of both versions.
