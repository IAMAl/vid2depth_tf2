cmake_minimum_required(VERSION 3.0 FATAL_ERROR)

project(icp_op)

find_package(PCL 1.8 REQUIRED)
find_package(Eigen3 REQUIRED)

include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

include_directories(/home/toodef/anaconda3/envs/vid2depth/lib/python3.6/site-packages/tensorflow/include)
link_directories(/home/toodef/anaconda3/envs/vid2depth/lib/python3.6/site-packages/tensorflow)

include_directories("${EIGEN3_INCLUDE_DIR}")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_GLIBCXX_USE_CXX11_ABI=0")

add_library(icp_op SHARED icp_op_kernel.cc)
target_link_libraries(icp_op ${PCL_LIBRARIES} tensorflow_framework)
