cmake_minimum_required(VERSION 3.10)
project(liblz4_vendor)

# ament_package(CONFIG_EXTRAS liblz4_vendor-extras.cmake)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  liblz4_vendor
  URL https://github.com/lz4/lz4/archive/refs/tags/v1.9.4.tar.gz
  SOURCE_SUBDIR build/cmake
)

set(BUILD_STATIC_LIBS OFF CACHE BOOL "BUILD_STATIC_LIBS." FORCE)
set(LZ4_BUILD_LEGACY_LZ4C OFF CACHE BOOL "LZ4_BUILD_LEGACY_LZ4C." FORCE)
set(LZ4_BUILD_CLI OFF CACHE BOOL "LZ4_BUILD_CLI." FORCE)
set(LZ4_BUNDLED_MODE OFF CACHE BOOL "LZ4_BUILD_CLI." FORCE)
set(CMAKE_BUILD_TYPE Release)

FetchContent_MakeAvailable(liblz4_vendor)
