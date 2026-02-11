cmake_minimum_required(VERSION 3.8)
project(spdlog_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  spdlog_vendor
  URL https://github.com/gabime/spdlog/archive/refs/tags/v1.17.0.tar.gz
)

set(CMAKE_BUILD_TYPE Release)
set(SPDLOG_BUILD_TESTS OFF CACHE BOOL "SPDLOG_BUILD_TESTS" FORCE)
set(SPDLOG_BUILD_EXAMPLE OFF CACHE BOOL "SPDLOG_BUILD_EXAMPLE" FORCE)
set(SPDLOG_INSTALL ON CACHE BOOL "SPDLOG_INSTALL" FORCE)

FetchContent_MakeAvailable(spdlog_vendor)

