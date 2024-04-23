## Robopet One Package

This package contains code for simulating and running the robopet_one robot chameleon for the Mechatronics 2 class. This package was built for use with ROS2 Humble and [Gazebo Classic 11](https://classic.gazebosim.org/tutorials?tut=install_ubuntu). Use of the RPLidar requires the [rplidar_ros package](https://index.ros.org/p/rplidar_ros/) be cloned and built within the same workspace as the robopet_one package.

---Current sim run process---

enter and source workspace, launch sim

`ros2 launch robopet_one launch_sim.launch.py world:=./src/robopet_one/worlds/cone_hell.world`

in new terminal source and launch slam toolbox

`ros2 launch robopet_one online_async_launch.py params_file:=./src/robopet_one/config/mapper_params_online_async.yaml use_sim_time:=true`

in new terminal source and launch nav2

`ros2 launch robopet_one navigation_launch.py use_sim_time:=true`

in new terminal launch telop

`ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/cmd_vel_joy`

in new terminal start rviz

`rviz2 -d src/robopet_one/config/basic_nav.rviz`

should open rviz and display the robot model, transforms, laserscan, and map. As long as you keep teleop_twist_keyboard your active window, you can drive the robot around with your keyboard. Use the 2D Goal Pose button in Rviz to tell the robot where to navigate to.

---Current robot run process---

enter and source workspace on rpi over ssh

`ros2 launch robopet_one launch_robot.launch.py`

sometimes this fails seemingly because RSP doesn't launch properly. If this happens just wait a few seconds and try to run again. It seems like it likes some time to warm up on occasion.

in new ssh terminal on rpi, source and launch rplidar

`sudo chmod 777 /dev/ttyUSB1`
`ros2 launch robopet_one rplidar.launch.py`

if this has issues use `sudo dmesg | grep ttyUSB` and `sudo dmesg --human --follow` to confirm the serial ports are configured properly.

on dev machine enter workspace and run teleop

`ros2 run teleop_twist_keyboard teleop_twist_keyboard`

in new terminal source and run slam_toolbox

`ros2 launch robopet_one online_async_launch.py params_file:=./src/robopet_one/config/mapper_params_online_async.yaml use_sim_time:=false`

in new terminal source and run nav2

`ros2 launch robopet_one navigation_launch.py use_sim_time:=false`

in new terminal start rviz

`rviz2 -d src/robopet_one/config/basic_nav.rviz`

should open rviz and display the robot model, transforms, laserscan, and map. As long as you keep teleop_twist_keyboard your active window, you can drive the robot around with your keyboard. Use the 2D Goal Pose button in Rviz to tell the robot where to navigate to.

safely shutdown the rpi before turning off the robot by running `sudo shutdown -h now` in an ssh terminal

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).