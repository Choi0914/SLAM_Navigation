cmake_minimum_required(VERSION 2.8)
project(gmapping)

find_package(catkin REQUIRED nav_msgs nodelet openslam_gmapping roscpp tf rosbag_storage)

find_package(Boost REQUIRED)

include_directories(${Boost_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS})

include_directories(src)

catkin_package()

# add_executable(rosrun으로 실행시킬 실행파일 이름 설정, 파일 경로)
add_executable(slam_gmapping src/slam_gmapping.cpp src/main.cpp)
target_link_libraries(slam_gmapping ${Boost_LIBRARIES} ${catkin_LIBRARIES})
if(catkin_EXPORTED_TARGETS)
  add_dependencies(slam_gmapping ${catkin_EXPORTED_TARGETS})
endif()

install(TARGETS slam_gmapping
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
