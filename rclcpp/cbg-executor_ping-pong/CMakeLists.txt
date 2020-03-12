cmake_minimum_required(VERSION 3.5)
project(examples_rclcpp_minimal_multiexecutors)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

include_directories(include)

add_executable(minimal_multi-executors main.cpp src/PingSubNode.cpp src/PongSubNode.cpp)
ament_target_dependencies(minimal_multi-executors rclcpp std_msgs)

install(TARGETS minimal_multi-executors
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
