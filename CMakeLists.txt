cmake_minimum_required(VERSION 3.0 FATAL_ERROR)

project(downsampling_compare)

message("The compiler used is ${CMAKE_CXX_COMPILER} or ${CMAKE_C_COMPILER} or ${CMAKE_C_COMPILER_ID} or${CMAKE_CXX_COMPILER_ID}")
set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS} -O3")
# *********************************************
# ******** ATTENTION: do NOT use the **********
# ******** following check for c++11 **********
# ******** because it will result in **********
# ******** a segmentation fault at startup! ***
# *********************************************

# check c++11 / c++0x
#include(CheckCXXCompilerFlag)
#CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
#CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
#if(COMPILER_SUPPORTS_CXX11)
#    set(CMAKE_CXX_FLAGS "-std=c++11")
#elseif(COMPILER_SUPPORTS_CXX0X)
#    set(CMAKE_CXX_FLAGS "-std=c++0x")
#else()
#    message(FATAL_ERROR "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
#endif()

find_package(catkin REQUIRED COMPONENTS
             pcl_ros
	     pcl_conversions
             roscpp)
             #Eigen REQUIRED)


catkin_package(
    INCLUDE_DIRS include
    LIBRARIES ${PROJECT_NAME}
    CATKIN_DEPENDS roscpp pcl_ros
    DEPENDS eigen
)

include_directories(
    include
    ${catkin_INCLUDE_DIRS}
    #${EIGEN_INCLUDE_DIRS}
)

# add the visibilityContextNode
add_executable (downsampling_compare src/downsampling_compare.cpp)
#add_dependencies
target_link_libraries (downsampling_compare ${catkin_LIBRARIES})



