cmake_minimum_required(VERSION 3.8)
project(eigen3_vendor)

set(eigen3_vendor_MAJOR_VERSION 0)
set(eigen3_vendor_MINOR_VERSION 0)
set(eigen3_vendor_PATCH_VERSION 0)
set(eigen3_vendor_VERSION
  ${eigen3_vendor_MAJOR_VERSION}.${eigen3_vendor_MINOR_VERSION}.${eigen3_vendor_PATCH_VERSION})

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  eigen3
  URL https://gitlab.com/libeigen/eigen/-/archive/3.4.0/eigen-3.4.0.tar.gz
  # SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/ext/
)

set(CMAKE_BUILD_TYPE Release)
set(BUILD_TESTING OFF)

FetchContent_MakeAvailable(eigen3)

