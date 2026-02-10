cmake_minimum_required(VERSION 3.8)
project(libyaml_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  libyaml_vendor
  URL https://github.com/yaml/libyaml/archive/refs/tags/0.2.5.tar.gz
)

FetchContent_MakeAvailable(libyaml_vendor)

