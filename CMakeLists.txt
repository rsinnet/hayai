cmake_minimum_required(VERSION 2.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

rosbuild_find_ros_package(drc_common)
list(APPEND CMAKE_MODULE_PATH ${drc_common_PACKAGE_PATH}/cmake)
include(BuildOptions)

rosbuild_init()

# Must be called AFTER rosbuild_init()
bake_in_version_info(${PROJECT_NAME})

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

# Append nasa_cmake the CMAKE_MODULE_PATH
rosbuild_find_ros_package(nasa_cmake)
list(APPEND CMAKE_MODULE_PATH ${nasa_cmake_PACKAGE_PATH})

# find log4cpp
find_package(Log4cpp REQUIRED)
include_directories(${Log4cpp_INCLUDE_DIR})
message(STATUS "Found Log4cpp:")
message(STATUS "  include: ${Log4cpp_INCLUDE_DIR}")

include_directories(${PROJECT_SOURCE_DIR}/include)

# Sub projects
add_subdirectory(src)
add_subdirectory(sample)
