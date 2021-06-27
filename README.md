# SlamMap_Turtlebot
Creating and safe map with tutrlebot3 using Slam approach 
As you can see in the files uploaded, I created a TurtleBot3 world and then initiated SLAM to create an safe a map. The steps were as following:
- after installation of ros 1 and its independednt packages I went to install TurtleBot3 via Debian Packages with the following commands:

$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3

- And then set the default for turtuleBot3 model which in my case was the Burger model.

$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc 

- and now it's time for installation of the simulation packages which requires TurtuleBot3_msgs, with the following commands: 

$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make

- time to launch, there are three worlds to choose from and in my case it was tutrleBot3_World: 

$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

- Running a SLAM node next:

$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

- And that's about it! all done, just need to run a telportation node to control the robot movement : 

$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

- And save the map (map.pgm file added in the respotirary) 

$ rosrun map_server map_saver -f ~/map

***** ALL DONE *****

