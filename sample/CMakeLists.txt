cmake_minimum_required(VERSION 2.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

rosbuild_find_ros_package(drc_common)
list(APPEND CMAKE_MODULE_PATH ${drc_common_PACKAGE_PATH}/cmake)
include(BuildOptions)

# set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

include_directories(${PROJECT_SOURCE_DIR}/include)

add_executable(sample
  WomanBenchmark.cpp
  WomanBenchmarkWithFixture.cpp
)

target_link_libraries(sample
  hayai_main
)
