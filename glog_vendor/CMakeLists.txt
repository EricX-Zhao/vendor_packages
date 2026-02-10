cmake_minimum_required(VERSION 3.8)
project(glog_vendor)


if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


include(FetchContent)
FetchContent_Declare(
  glog_vendor
  URL  https://github.com/google/glog/archive/refs/tags/v0.7.1.tar.gz
)

set(BUILD_EXAMPLES OFF CACHE BOOL "BUILD_EXAMPLES" FORCE)
set(WITH_GTEST OFF CACHE BOOL "WITH_GTEST" FORCE)


FetchContent_MakeAvailable(glog_vendor)
