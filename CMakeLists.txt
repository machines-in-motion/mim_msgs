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
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

# Generate all msg and srv files.
file(
  GLOB msg_files
  RELATIVE ${PROJECT_SOURCE_DIR}
  msg/*.msg)
file(
  GLOB srv_files
  RELATIVE ${PROJECT_SOURCE_DIR}
  srv/*.srv)

find_program(LSB_RELEASE_EXEC lsb_release)
execute_process(COMMAND ${LSB_RELEASE_EXEC} -rs
    OUTPUT_VARIABLE LSB_RELEASE_SHORT
    OUTPUT_STRIP_TRAILING_WHITESPACE
)

if (LSB_RELEASE_SHORT STREQUAL "18.04")
  rosidl_generate_interfaces(${PROJECT_NAME}_msg_srv ${msg_files} ${srv_files}
                            DEPENDENCIES std_msgs geometry_msgs)
else()
rosidl_generate_interfaces(${PROJECT_NAME}_msg_srv ${msg_files} ${srv_files}
                            DEPENDENCIES std_msgs geometry_msgs
                            LIBRARY_NAME ${PROJECT_NAME})
endif()

# Export and install the package.
ament_package()
