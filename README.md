## Robopet One Package

This package contains code for simulating and running the robopet_one robot chameleon for the Mechatronics 2 class. This package was built for use with ROS2 Humble and [Gazebo Classic 11](https://classic.gazebosim.org/tutorials?tut=install_ubuntu). Use of the RPLidar requires the [rplidar_ros package](https://index.ros.org/p/rplidar_ros/) be cloned and built within the same workspace as the robopet_one package.

---Current sim run process---

enter and source workspace, launch sim

`ros2 launch robopet_one launch_sim.launch.py world:=./src/robopet_one/worlds/cone_hell.world`

in new terminal launch slam toolbox

`ros2 launch robopet_one online_async_launch.py params_file:=./src/robopet_one/config/mapper_params_online_async.yaml use_sim_time:=true`

in new terminal launch nav2

`ros2 launch robopet_one navigation_launch.py use_sim_time:=true`

in new terminal launch telop

`ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/cmd_vel_joy`

in new terminal start rviz

`rviz2 -d src/robopet_one/config/basic_nav.rviz`

should open rviz and display the robot model, transforms, and laserscan. Add a map, set topic to global costmap and change color scheme to costmap (personal preference). Drive the bot around to generate a map then use the 2D Goal Pose button to set objectives for the robot to navigate to.

---Current robot run process---

robot:

enter and source workspace on rpi

`ros2 launch robopet_one launch_robot.launch.py`

rplidar:

motor demo:

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).