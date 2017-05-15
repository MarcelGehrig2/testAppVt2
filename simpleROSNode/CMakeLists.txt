project(simpleROSNode)
cmake_minimum_required(VERSION 2.8)
aux_source_directory(. SRC_LIST)


## ROS stuff
message( STATUS "ROS_ROOT: " $ENV{ROS_ROOT} )
message(STATUS "looking for package 'ROS'")
find_package( roscpp QUIET )
if (roscpp_FOUND)
	message( STATUS "-> ROS found")
else()
	message( STATUS "-> ROS NOT found")
endif()
message( STATUS "roscpp_LIBRARIES: " ${roscpp_LIBRARIES})

message( STATUS "find_library:")
#find_library( ROSCPP_LIBRARY roscpp)


#include_directories( roscpp_INCLUDE_DIRS )
#link_directories( roscpp_LIBRARIES  )

message( STATUS "roslib_LIBRARIES:  " ${roslib_LIBRARIES} )
find_package( roslib REQUIRED )
message( STATUS "roslib_LIBRARIES:  " ${roslib_LIBRARIES} )
message( STATUS "roslib_INCLUDE_DIR:  " ${roslib_INCLUDE_DIR} )
message( STATUS "roslib_INCLUDE_DIR:  " ${roscpp_INCLUDE_DIR} )
#include_directories( "/opt/ros/kinetic/include/" )


find_package( catkin REQUIRED COMPONENTS nodelet)
message( STATUS "catkin_INCLUDE_DIR:  " ${catkin_INCLUDE_DIRS} )
include_directories( "${catkin_INCLUDE_DIRS}" )


#find_library( ROS_LIBRARY roslib)
#message( STATUS "ROS_LIBRARY: " ${roslib} )

find_package( rosconsole )



add_executable(${PROJECT_NAME} ${SRC_LIST})



#target_link_libraries(${PROJECT_NAME} roslib ${ROSCPP_LIBRARY} rosconsole)
target_link_libraries(${PROJECT_NAME} ${catkin_LIBRARIES} )
