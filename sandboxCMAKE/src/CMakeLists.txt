
macro(add_eeros_sources)
    file(RELATIVE_PATH _relPath "${PROJECT_SOURCE_DIR}/src" "${CMAKE_CURRENT_SOURCE_DIR}")
    foreach(_src ${ARGN})
        if(_relPath)
            list(APPEND EEROS_SRCS "${_relPath}/${_src}")
        else()
            list(APPEND EEROS_SRCS "${_src}")
        endif()
    endforeach()
    if(_relPath)
        # propagate EEROS_SRCS to parent directory
        set(EEROS_SRCS ${EEROS_SRCS} PARENT_SCOPE)
    endif()
endmacro()

#include_directories(${EEROS_SOURCE_DIR}/includes ${EEROS_BINARY_DIR})

add_subdirectory(folder1)
add_subdirectory(folder2)

#link_directories(${EEROS_BINARY_DIR}/src/core)

#add_library(eeros SHARED ${EEROS_SRCS})

#target_link_libraries(eeros ${EXTERNAL_LIBS})

#set_target_properties(eeros PROPERTIES
#			VERSION ${EEROS_VERSION}
#			SOVERSION ${EEROS_VERSION_SO})


#INSTALL(TARGETS eeros LIBRARY DESTINATION lib)
