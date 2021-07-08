# Indoor-navigation-system-for-mobile-robot-design-and-implementation
This project aims to simulate the way the robot discovers its' environment in Gazebo while constructing it as a map using SLAM. This is done using an online version of ROS (https://app.theconstructsim.com/#/Home) along with robots from Turtlebot (https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/).

## PC Setup
First you need to sign up in (https://app.theconstructsim.com/#/Home) and start a new project using ROS melodic, open web shell and follow these steps to install turtlebot packages.

### 1. Install TurtleBot3 Packages
```
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3
```
### 2. Set TurtleBot3 Model Name
choose the Trurtlebot you want to work with: 

In case of TurtleBot3 Burger
```
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
```
In case of TurtleBot3 Waffle Pi
```
echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
```


## Simulation
After choosing the Trurtlebot you need to run it in an environment using a simulation, and you can use:

### Gazebo Simulation
#### 1. Install Simulation Package
```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```
![image](https://user-images.githubusercontent.com/85634099/124955892-19b80e00-e020-11eb-980f-18f305b03135.png)

#### 2. Launch Simulation World
There are 3 simulation environments prepared for TurtleBot3, you can select any one of these environments to launch Gazebo:
##### 1 ) Empty World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```
![image](https://user-images.githubusercontent.com/85634099/124955956-2b011a80-e020-11eb-9ded-33a272fd3677.png)

##### 2 ) TurtleBot3 World
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
![image](https://user-images.githubusercontent.com/85634099/124956241-774c5a80-e020-11eb-94d7-465d9e73b0ec.png)

##### 3 ) TurtleBot3 House
```
$ export TURTLEBOT3_MODEL=waffle_pi
$ roslaunch turtlebot3_gazebo turtlebot3_house.launch
```
![image](https://user-images.githubusercontent.com/85634099/124956306-86330d00-e020-11eb-881c-7d1aab01f3ec.png)


### SLAM Simulation
#### 1. Launch Simulation World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
![image](https://user-images.githubusercontent.com/85634099/124957245-8b448c00-e021-11eb-80f1-d32c5bd45904.png)

#### 2. Run SLAM Node
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
![image](https://user-images.githubusercontent.com/85634099/124957337-a3b4a680-e021-11eb-8e3f-a18e243a0228.png)
![image](https://user-images.githubusercontent.com/85634099/124957488-cf379100-e021-11eb-86b8-e3c2acd101c9.png)

#### 3. Run Teleoperation Node
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
![image](https://user-images.githubusercontent.com/85634099/124957383-b202c280-e021-11eb-8217-47ebbfdf680c.png)

#### 4. Save Map
```
$ rosrun map_server map_saver -f ~/map
```
![image](https://user-images.githubusercontent.com/85634099/124957526-dc548000-e021-11eb-866e-d23d72b56aaf.png)
![image](https://user-images.githubusercontent.com/85634099/124957570-e70f1500-e021-11eb-9a59-cc4519ed6209.png)
