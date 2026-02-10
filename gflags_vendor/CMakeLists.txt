cmake_minimum_required(VERSION 3.8)
project(gflags_vendor)


if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


include(FetchContent)
FetchContent_Declare(
  gflags_vendor
  URL https://github.com/gflags/gflags/archive/v2.2.1.zip
  # SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/ext/
)

set(BUILD_SHARED_LIBS ON CACHE BOOL "Build shared libraries" FORCE)
set(INSTALL_HEADERS ON CACHE BOOL "Request installation of headers and other development files." FORCE)
set(GFLAGS_NAMESPACE "google" CACHE STRING "gflags namespace" FORCE)

FetchContent_MakeAvailable(gflags_vendor)
