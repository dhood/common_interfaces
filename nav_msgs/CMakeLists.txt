cmake_minimum_required(VERSION 2.8.3)

project(nav_msgs)

if(NOT WIN32)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -Wextra")
endif()

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)

set(msg_files
  "msg/GridCells.msg"
  "msg/MapMetaData.msg"
  "msg/OccupancyGrid.msg"
  "msg/Odometry.msg"
  "msg/Path.msg"
)
set(srv_files
  "srv/GetMap.srv"
  "srv/GetPlan.srv"
)
# TODO(wjwwood): port the action GetMap from ROS 1, once actions are supported.
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES builtin_interfaces geometry_msgs std_msgs
)

ament_package()
