cmake_minimum_required(VERSION 3.8)
project(suitesparse_vendor)


if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

include(FetchContent)
FetchContent_Declare(
  suitesparse_vendor
  URL  https://github.com/DrTimothyAldenDavis/SuiteSparse/archive/refs/tags/v7.12.1.tar.gz
  SOURCE_SUBDIR SuiteSparse-7.12.1
)

FetchContent_GetProperties(suitesparse_vendor)
if (NOT suitesparse_vendor_POPULATED)
  FetchContent_Populate(suitesparse_vendor)
  set(BUILD_SHARED_LIBS ON CACHE BOOL "BUILD_SHARED_LIBS." FORCE)
  set(BUILD_STATIC_LIBS OFF CACHE BOOL "BUILD_STATIC_LIBS." FORCE)
  set(SUITESPARSE_ROOT_CMAKELISTS OFF CACHE BOOL "SUITESPARSE_ROOT_CMAKELISTS." FORCE)
  set(SUITESPARSE_ENABLE_PROJECTS "suitesparse_config;mongoose;amd;btf;camd;ccolamd;colamd;cholmod;cxsparse;ldl;klu;umfpack;paru;rbio;spqr" CACHE STRING "" FORCE)
  set(BUILD_TESTING OFF CACHE BOOL "BUILD_TESTING." FORCE)
  set(SUITESPARSE_DEMOS OFF CACHE BOOL "SUITESPARSE_DEMOS." FORCE)


  add_subdirectory(${suitesparse_vendor_SOURCE_DIR} ${suitesparse_vendor_BINARY_DIR})
endif()

# cmake .. \
#   -DCMAKE_TOOLCHAIN_FILE=/opt/cmake/rk3588.toolchain.cmake \
#   -DCMAKE_INSTALL_PREFIX=/workspace/output/RK3588/install \
#   -DSUITESPARSE_ENABLE_PROJECTS="suitesparse_config;mongoose;amd;btf;camd;ccolamd;colamd;cholmod;cxsparse;ldl;klu;umfpack;paru;rbio;spqr" \
#   -DBUILD_SHARED_LIBS=ON \
#   -DSUITESPARSE_DEMOS=OFF \
#   -DCMAKE_EXE_LINKER_FLAGS="-Wl,-rpath-link,/workspace/output/RK3588/install/lib" \
#   -DBUILD_TESTING=OFF \
#   -DBUILD_STATIC_LIBS=OFF
