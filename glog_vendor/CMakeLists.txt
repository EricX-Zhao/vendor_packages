cmake_minimum_required(VERSION 3.8)
project(glog_vendor)


if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)


include(FetchContent)
FetchContent_Declare(
  glog_vendor
  URL  https://github.com/google/glog/archive/v0.3.5.zip
)

FetchContent_MakeAvailable(glog_vendor)
