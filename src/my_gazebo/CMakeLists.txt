cmake_minimum_required(VERSION 3.0.2)
project(my_gazebo)

add_compile_options(-std=c++11)
find_package(catkin REQUIRED COMPONENTS
roscpp
rospy
std_msgs
sensor_msgs
geometry_msgs
nav_msgs
tf
gazebo_ros
)

find_package(gazebo REQUIRED)
catkin_package(
CATKIN_DEPENDS roscpp std_msgs sensor_msgs geometry_msgs nav_msgs tf gazebo_ros
DEPENDS gazebo
)

link_directories(${GAZEBO_LIBRARY_DIRS})
include_directories(
${catkin_INCLUDE_DIRS}
${GAZEBO_INCLUDE_DIRS}
)
install(DIRECTORY launch models rviz worlds
DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
catkin_install_python(PROGRAMS
  src/r2d2_teleop_key.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)