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
  URL https://github.com/jbeder/yaml-cpp/archive/refs/tags/yaml-cpp-0.9.0.tar.gz
)

set(CMAKE_BUILD_TYPE Release)
set(YAML_BUILD_SHARED_LIBS ON CACHE BOOL "YAML_BUILD_SHARED_LIBS" FORCE)
set(YAML_CPP_INSTALL ON CACHE BOOL "YAML_CPP_INSTALL" FORCE)

FetchContent_MakeAvailable(yaml_cpp_vendor)
