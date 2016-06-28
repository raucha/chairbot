cmake_minimum_required(VERSION 2.8.3)
project(chairbot)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  roscpp
  tms_msg_db
  nav_msgs
  tf
)

###################################
## catkin specific configuration ##
###################################
catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES kobuki_virtual_control
  CATKIN_DEPENDS geometry_msgs roscpp tms_msg_db tms_msg_rc nav_msgs
  DEPENDS system_lib
  CATKIN_DEPENDS tf
)

###########
## Build ##
###########
include_directories(
  ${catkin_INCLUDE_DIRS}
)

## Declare a cpp executable
 add_executable(chairbot_node src/chairbot_node.cpp src/ClientSocket.cpp src/Socket.cpp)

 add_dependencies(chairbot_node DEPENDS tms_msg_rc_gencpp tms_msg_db_gencpp)

## Specify libraries to link a library or executable target against
 target_link_libraries(chairbot_node
   ${catkin_LIBRARIES}
 )
