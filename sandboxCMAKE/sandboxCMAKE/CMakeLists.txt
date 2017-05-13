## Check cmake version, we need 2.8 or newer
cmake_minimum_required(VERSION 2.8)

## EEROS Robotic Framework
project(sandboxCMAKE)



message(STATUS "looking for package 'ROS'")
find_package(roscpp QUIET)
if (roscpp_FOUND)
	message( Status "-> ROS found")
endif()



aux_source_directory(. SRC_LIST)

list (APPEND src)


add_executable(${PROJECT_NAME} ${SRC_LIST})
