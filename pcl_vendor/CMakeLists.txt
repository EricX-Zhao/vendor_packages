cmake_minimum_required(VERSION 3.8)
project(pcl_vendor)

set(tinyxml2_MAJOR_VERSION 0)
set(tinyxml2_MINOR_VERSION 0)
set(tinyxml2_PATCH_VERSION 0)
set(tinyxml2_VERSION
  ${tinyxml2_MAJOR_VERSION}.${tinyxml2_MINOR_VERSION}.${tinyxml2_PATCH_VERSION})

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  pcl
  URL https://github.com/PointCloudLibrary/pcl/archive/refs/tags/pcl-1.15.1.tar.gz
)

set(WITH_LIBUSB OFF CACHE BOOL "WITH_LIBUSB." FORCE)
set(WITH_CUDA OFF CACHE BOOL "WITH_CUDA." FORCE)
set(WITH_PCAP OFF CACHE BOOL "WITH_PCAP." FORCE)
set(WITH_OPENGL OFF CACHE BOOL "WITH_OPENGL." FORCE)
set(WITH_GLEW OFF CACHE BOOL "WITH_GLEW." FORCE)
set(WITH_VTK OFF CACHE BOOL "WITH_VTK." FORCE)

set(BUILD_apps OFF CACHE BOOL "BUild_apps." FORCE)
set(BUILD_global_tests OFF CACHE BOOL "BUild_global_tests." FORCE)
# set(BUILD_features OFF CACHE BOOL "BUILD_features." FORCE)
# set(BUILD_sample_consensus OFF CACHE BOOL "BUILD_sample_consensus." FORCE)
# set(BUILD_segmentation OFF CACHE BOOL "BUILD_segmentation." FORCE) 
set(CMAKE_BUILD_TYPE Release)

FetchContent_MakeAvailable(pcl)
