cmake_minimum_required(VERSION 3.14.5)
project(fisheye_calib)

add_definitions(-std=c++1y)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

find_package(OpenCV 4.1.0 REQUIRED)
find_package(Boost REQUIRED filesystem system)
find_package(Eigen3 REQUIRED)

include_directories(include)
include_directories("${EIGEN3_INCLUDE_DIR}")

include_directories(${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIBRARY_DIRS})

include_directories(${Boost_INCLUDE_DIRS})
link_directories(${Boost_LIBRARY_DIRS})

###########
## Build ##
###########

add_executable(fisheye_calib
    src/fisheye_calib.cpp
    src/fisheye.cpp
)
target_link_libraries(fisheye_calib
    ${Boost_LIBRARIES}
    ${OpenCV_LIBS}
)
