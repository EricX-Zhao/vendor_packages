cmake_minimum_required(VERSION 3.8)
project(pybind11_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  pybind11_vendor
  GIT_REPOSITORY  https://github.com/pybind/pybind11.git
  GIT_TAG v2.11.1
  GIT_SHALLOW TRUE
)

if (NOT pybind11_vendor_POPULATED)

  FetchContent_Populate(pybind11_vendor)

  set(CMAKE_BUILD_TYPE Release)
  set(PYBIND11_INSTALL ON CACHE BOOL "PYBIND11_INSTALL" FORCE)
  set(PYBIND11_TEST OFF CACHE BOOL "PYBIND11_TEST" FORCE)
  set(PYBIND11_NOPYTHON ON CACHE BOOL "PYBIND11_NOPYTHON" FORCE)
  add_subdirectory(${pybind11_vendor_SOURCE_DIR} ${pybind11_vendor_BINARY_DIR})
endif()
