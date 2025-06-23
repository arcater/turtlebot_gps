################################################################################
# Set minimum required version of cmake, project name and compile options
################################################################################
cmake_minimum_required(VERSION 3.5)
project(turtlebot_gps)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

if(MSVC)
  add_compile_definitions(_USE_MATH_DEFINES)
endif()

################################################################################
# Find ament packages and libraries for ament and system dependencies
################################################################################
find_package(ament_cmake REQUIRED)
find_package(ros_gz_sim REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(rclcpp REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(tf2 REQUIRED)

################################################################################
# Build
################################################################################
link_directories(
  ${GAZEBO_LIBRARY_DIRS}
)

include_directories(
  include
  ${GAZEBO_INCLUDE_DIRS}
)


# add_library(traffic_light_plugin SHARED src/traffic_light_plugin.cpp)
# target_link_libraries(traffic_light_plugin ${GAZEBO_LIBRARIES})

# add_library(traffic_bar_plugin SHARED src/traffic_bar_plugin.cpp)
# target_link_libraries(traffic_bar_plugin ${GAZEBO_LIBRARIES})

# add_library(obstacle1 SHARED src/obstacle1.cpp)
# target_link_libraries(obstacle1 ${GAZEBO_LIBRARIES})

# add_library(obstacle2 SHARED src/obstacle2.cpp)
# target_link_libraries(obstacle2 ${GAZEBO_LIBRARIES})

# add_library(obstacles SHARED src/obstacles.cpp)
# target_link_libraries(obstacles ${GAZEBO_LIBRARIES})

################################################################################
# Install
################################################################################

install(DIRECTORY launch models params urdf worlds
  DESTINATION share/${PROJECT_NAME}/
)


################################################################################
# Macro for ament package
################################################################################
ament_export_dependencies(
  gazebo_ros_pkgs
  geometry_msgs
  nav_msgs
  rclcpp
  sensor_msgs
  tf2
)
ament_package()
