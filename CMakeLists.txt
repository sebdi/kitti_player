cmake_minimum_required(VERSION 2.8.3)
project(kitti_player)

find_package(catkin REQUIRED COMPONENTS roscpp tf tf2 std_msgs dynamic_reconfigure pcl_ros geometry_msgs)
find_package(PCL 1.7 REQUIRED)

generate_dynamic_reconfigure_options(cfg/kitti_player.cfg)

catkin_package(CATKIN_DEPENDS dynamic_reconfigure)

include_directories(
		${}
  		${catkin_INCLUDE_DIRS} 
  		${PCL_INCLUDE_DIRS}
)

link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

add_executable(kitti_player src/Random.cpp src/randomUtil.cpp src/bulletUtil.cpp src/kitti_player.cpp)

target_link_libraries(kitti_player ${catkin_LIBRARIES} ${PCL_LIBRARIES})
