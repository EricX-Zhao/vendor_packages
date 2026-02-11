cmake_minimum_required(VERSION 3.8)
project(mimick_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  mimick_vendor
  GIT_REPOSITORY https://github.com/ros2/Mimick.git
  GIT_TAG 1e138b0e13da99278453dc96af954890d9f48348
)

FetchContent_MakeAvailable(mimick_vendor)

