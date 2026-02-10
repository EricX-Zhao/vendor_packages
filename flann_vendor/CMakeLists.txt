cmake_minimum_required(VERSION 3.8)
project(flann_vendor)


if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  flann
  URL https://github.com/flann-lib/flann/archive/refs/tags/1.9.2.tar.gz
)

set(BUILD_PYTHON_BINDINGS OFF CACHE BOOL "BUILD_PYTHON_BINDINGS." FORCE)
set(BUILD_MATLAB_BINDINGS OFF CACHE BOOL "BUILD_MATLAB_BINDINGS." FORCE)
set(BUILD_EXAMPLES OFF CACHE BOOL "BUILD_EXAMPLES." FORCE)
set(BUILD_TESTS OFF CACHE BOOL "BUILD_TESTS." FORCE)
set(BUILD_DOC OFF CACHE BOOL "BUILD_DOC." FORCE)
set(LZ4_INCLUDE_DIRS $ENV{ROS_HOME}/include CACHE STRING "LZ4_INCLUDE_DIRS." FORCE)
set(CMAKE_BUILD_TYPE Release)

FetchContent_MakeAvailable(flann)
