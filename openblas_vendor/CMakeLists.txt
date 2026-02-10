cmake_minimum_required(VERSION 3.8)
project(openblas_vendor)


if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


include(FetchContent)
FetchContent_Declare(
  openblas_vendor
  URL  https://github.com/OpenMathLib/OpenBLAS/archive/refs/tags/v0.3.31.tar.gz
)

set(BUILD_TESTING OFF CACHE BOOL "BUILD_TESTING." FORCE)
set(BUILD_SHARED_LIBS ON CACHE BOOL "BUILD_SHARED_LIBS." FORCE)


FetchContent_MakeAvailable(openblas_vendor)
