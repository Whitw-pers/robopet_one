## Robopet One Package

This package contains code for simulating and running the robopet_one robot chameleon for the Mechatronics 2 class. This package was built for use with ROS2 Humble and [Gazebo Classic 11](https://classic.gazebosim.org/tutorials?tut=install_ubuntu). Use of the RPLidar requires the [rplidar_ros package](https://index.ros.org/p/rplidar_ros/) be cloned and built within the same workspace as the robopet_one package.

Current sim run process:

Current robot run process:

Note that each directory currently has at least one file in it to ensure that git tracks the files (and, consequently, that a fresh clone has direcctories present for CMake to find). These example files can be removed if required (and the directories can be removed if `CMakeLists.txt` is adjusted accordingly).