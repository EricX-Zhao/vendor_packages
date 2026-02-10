cmake_minimum_required(VERSION 3.8)
project(yaml_cpp_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  yaml_cpp_vendor
  URL https://github.com/jbeder/yaml-cpp.git
)

set(CMAKE_BUILD_TYPE Release)
set(BUILD_TESTING OFF)

FetchContent_MakeAvailable(yaml_cpp_vendor)

