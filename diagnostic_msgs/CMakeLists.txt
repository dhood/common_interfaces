cmake_minimum_required(VERSION 2.8.3)

project(diagnostic_msgs)

if(NOT WIN32)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -Wextra")
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)

set(msg_files
  "msg/DiagnosticArray.msg"
  "msg/DiagnosticStatus.msg"
  "msg/KeyValue.msg"
)
set(srv_files
  "srv/SelfTest.srv"
)
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES std_msgs
)

ament_package()
