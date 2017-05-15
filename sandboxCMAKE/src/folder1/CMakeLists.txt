
add_eeros_sources(sourceWithoutROS.cpp)

if(roscpp_FOUND)
	add_eeros_sources(sourceWithROS.cpp)
endif()
