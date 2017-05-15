## Check cmake version, we need 2.8 or newer
cmake_minimum_required(VERSION 2.8)

## EEROS Robotic Framework
project(sandboxCMAKE)



message(STATUS "looking for package 'ROS'")
find_package(roscpp QUIET)
if (roscpp_FOUND)
	message( STATUS "-> ROS found")
#	message( STATUS "roscpp_DIR:  " ${roscpp_DIR})
else()
	message( STATUS "-> ROS NOT found")
endif()



set( TESTVAR true )


add_subdirectory(src)


aux_source_directory(. SRC_LIST)

list (APPEND src)


add_executable(${PROJECT_NAME} ${SRC_LIST})


message( STATUS "Built with toolchainfile: " ${CMAKE_TOOLCHAIN_FILE} )
