cmake_minimum_required(VERSION 2.8.3)

project(dvo_benchmark)

find_package(catkin REQUIRED COMPONENTS cmake_modules roscpp dvo_core dvo_ros dvo_slam)
find_package(Eigen3 REQUIRED)
#find_package(OpenCV REQUIRED)
#find_package(G2O REQUIRED)

add_definitions(-std=c++11)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES dvo_benchmark
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${EIGEN3_INCLUDE_DIRS}
)


add_executable(benchmark
     src/benchmark_slam.cpp
)

#add_executable(experiment
#     src/experiment.cpp
#)

target_link_libraries(benchmark
#  vtkCommon
  ${catkin_LIBRARIES}
)

# create output directory - just convenience for our users
#file(MAKE_DIRECTORY "${PROJECT_SOURCE_DIR}/output")
#file(MAKE_DIRECTORY "${PROJECT_SOURCE_DIR}/output/video")

install(DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
)
