cmake_minimum_required(VERSION 3.8)
project(orocos_kdl_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  orocos_kdl_vendor
  GIT_REPOSITORY  https://github.com/orocos/orocos_kinematics_dynamics.git
  GIT_TAG ce4bcb65a050615b6d7f21bc60fbb2656515791b
)

if (NOT orocos_kdl_vendor_POPULATED)
  FetchContent_Populate(orocos_kdl_vendor)

  set(CMAKE_CXX_STANDARD 14)
  set(ENABLE_TESTS OFF CACHE BOOL "ENABLE_TESTS" FORCE)
  set(ENABLE_EXAMPLES OFF CACHE BOOL "ENABLE_EXAMPLES" FORCE)
  set(CMAKE_POLICY_VERSION_MINIMUM 3.5)
  add_subdirectory(${orocos_kdl_vendor_SOURCE_DIR}/orocos_kdl ${orocos_kdl_vendor_BINARY_DIR})
endif()
