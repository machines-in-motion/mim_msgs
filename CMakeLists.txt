cmake_minimum_required(VERSION 3.5)
project(mim_msgs)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++17
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# Generate all msg and srv files.
file(
  GLOB msg_files
  RELATIVE ${PROJECT_SOURCE_DIR}
  msg/*.msg)
file(
  GLOB srv_files
  RELATIVE ${PROJECT_SOURCE_DIR}
  srv/*.srv)
rosidl_generate_interfaces(${PROJECT_NAME}_msg_srv ${msg_files} ${srv_files})

# Export and install the package.
ament_package()
