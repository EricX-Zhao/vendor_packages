cmake_minimum_required(VERSION 3.8)
project(ceres_vendor)


if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


include(FetchContent)
FetchContent_Declare(
  ceres_vendor
  GIT_REPOSITORY https://github.com/EricX-Zhao/ceres-solver.git
  GIT_TAG        suitesparse  # 锁定 2.0.0 标签
)

# set(SUITESPARSE OFF CACHE BOOL "" FORCE)
set(BUILD_SHARED_LIBS ON CACHE BOOL "" FORCE)
set(BUILD_EXAMPLES OFF CACHE BOOL "BUILD_EXAMPLES" FORCE)
set(BUILD_TESTING OFF CACHE BOOL "BUILD_TESTING" FORCE)
set(BUILD_BENCHMARKS OFF CACHE BOOL "BUILD_BENCHMARKS" FORCE)
set(CMAKE_BUILD_TYPE Release)

FetchContent_MakeAvailable(ceres_vendor)
