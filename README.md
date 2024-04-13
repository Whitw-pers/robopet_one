## Robopet One Package

This package contains code for simulating and running the robopet_one robot chameleon for the Mechatronics 2 class. This package was built for use with ROS2 Humble and [Gazebo Classic 11](https://classic.gazebosim.org/tutorials?tut=install_ubuntu). Use of the RPLidar requires the [rplidar_ros package](https://index.ros.org/p/rplidar_ros/) be cloned and built within the same workspace as the robopet_one package.

---Current sim run process---

enter and source workspace

`ros2 launch robopet_one launch_sim.launch.py world:=./src/robopet_one/worlds/cone_hell.world`

in new terminal

`ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/diff_cont/cmd_vel_unstamped`

in new terminal

`rviz2 -d src/robopet_one/config/main.rviz`

should open rviz and display the robot model, transforms, and laserscan

---Current robot run process---

rplidar:

motor demo:

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).