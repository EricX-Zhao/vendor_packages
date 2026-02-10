cmake_minimum_required(VERSION 3.8)
project(geographiclib_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


include(FetchContent)
FetchContent_Declare(
  geographiclib_vendor
  URL https://github.com/geographiclib/geographiclib/archive/refs/tags/v2.5.tar.gz
)

set(CMAKE_BUILD_TYPE Release)

FetchContent_MakeAvailable(geographiclib_vendor)
