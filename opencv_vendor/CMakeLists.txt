cmake_minimum_required(VERSION 3.8)
project(opencv_vendor)

set(opencv_MAJOR_VERSION 0)
set(opencv_MINOR_VERSION 0)
set(opencv_PATCH_VERSION 0)
set(opencv_VERSION
  ${opencv_MAJOR_VERSION}.${opencv_MINOR_VERSION}.${opencv_PATCH_VERSION})

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)
include(FetchContent)
FetchContent_Declare(
  opencv
  URL https://github.com/opencv/opencv/archive/refs/tags/4.12.0.tar.gz
)

set(WITH_ADE OFF)
set(WITH_GTK OFF)
set(WITH_ITT OFF)
set(WITH_IPP OFF)
set(WITH_VTK OFF)
set(BUILD_IPP_IW OFF)
set(BUILD_ITT OFF)
set(BUILD_JAVA OFF)
set(BUILD_JPEG ON)
set(BUILD_PACKAGE OFF)
set(BUILD_PERF_TESTS OFF)
set(BUILD_PNG ON)
set(BUILD_TESTS OFF)
set(BUILD_TIFF ON)
set(BUILD_WEBP ON)
set(BUILD_ZLIB ON)
set(BUILD_opencv_apps OFF)
set(CMAKE_CXX_STANDARD 14)
set(BUILD_ANDROID_PROJECTS OFF)
set(BUILD_ANDROID_EXAMPLES OFF)
set(BUILD_EXAMPLES OFF)
set(WITH_OPENCL ON)
set(BUILD_opencv_python3 OFF)
set(BUILD_opencv_python2 OFF)
set(ENABLE_NEON ON)
set(BUILD_SHARED_LIBS ON)
set(CMAKE_BUILD_TYPE Release)

FetchContent_MakeAvailable(opencv)
