# turtlebot_gps for ROS 2 Humble
This is a modified version of the [turtlebot3_gazebo](https://github.com/ROBOTIS-GIT/turtlebot3_simulations/tree/humble/turtlebot3_gazebo) folder from turtlebot3_simulations. This repository contains a turtlebot3 waffle pi model with an added GPS sensor and an empty world with spherical coordinates.
# Setup
This repo does not replace [turtlebot3_simulations](https://github.com/ROBOTIS-GIT/turtlebot3_simulations/tree/humble) and must be installed alongside it. `git clone` this repo within the src folder of a ROS 2 workspace and use `colcon build`.
# Launch
   ``` bash
   ros2 launch turtlebot_gps gps_world.launch.py
   ```
