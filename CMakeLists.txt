cmake_minimum_required(VERSION 2.8.3)
project(loam_continuous)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(CMAKE_BUILD_TYPE RelWithDebInfo)

find_package(catkin REQUIRED COMPONENTS
    roscpp
    std_msgs
    sensor_msgs
    pcl_ros
    cv_bridge
)

find_package(OpenCV REQUIRED)

catkin_package(
    INCLUDE_DIRS src
)

include_directories(
    include
    ${catkin_INCLUDE_DIRS}
)


add_executable(scanRegistration src/scanRegistration.cpp)
add_executable(laserOdometry src/laserOdometry.cpp)
add_executable(laserMapping src/laserMapping.cpp)
add_executable(transformMaintenance src/transformMaintenance.cpp)

add_dependencies(scanRegistration ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
add_dependencies(laserOdometry ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
add_dependencies(laserMapping ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
add_dependencies(transformMaintenance ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

target_link_libraries(scanRegistration ${catkin_LIBRARIES} ${OpenCV_LIBS})
target_link_libraries(laserOdometry ${catkin_LIBRARIES} ${OpenCV_LIBS})
target_link_libraries(laserMapping ${catkin_LIBRARIES} ${OpenCV_LIBS})
target_link_libraries(transformMaintenance ${catkin_LIBRARIES} ${OpenCV_LIBS})
