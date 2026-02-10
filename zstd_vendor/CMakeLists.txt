cmake_minimum_required(VERSION 3.8)
project(zstd_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  zstd_vendor
  URL https://github.com/jbeder/yaml-cpp.git
  GIT_REPOSITORY  https://github.com/facebook/zstd.git
  GIT_TAG v1.5.5
)

set(CMAKE_BUILD_TYPE Release)
set(ZSTD_BUILD_STATIC OFF CACHE BOOL "ZSTD_BUILD_STATIC" FORCE)
set(ZSTD_BUILD_SHARED ON CACHE BOOL "ZSTD_BUILD_SHARED" FORCE)
set(ZSTD_BUILD_PROGRAMS ON CACHE BOOL "ZSTD_BUILD_PROGRAMS" FORCE)

FetchContent_MakeAvailable(zstd_vendor)

