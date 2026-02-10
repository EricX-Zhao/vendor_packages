cmake_minimum_required(VERSION 3.8)
project(suitesparse_vendor)


if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)
# include(ExternalProject)

# ExternalProject_Add(suitesparse_external
#   URL https://github.com/DrTimothyAldenDavis/SuiteSparse/archive/refs/tags/v7.12.1.tar.gz
  
#   # 强制传递所有交叉编译参数
#   CMAKE_ARGS
#     -DCMAKE_TOOLCHAIN_FILE=${CMAKE_TOOLCHAIN_FILE}
#     -DCMAKE_INSTALL_PREFIX=${SS_INSTALL_DIR}
#     -DBUILD_SHARED_LIBS=ON
#     -DBUILD_STATIC_LIBS=OFF
#     -DSUITESPARSE_DEMOS=OFF
#     -DBUILD_TESTING=OFF
#     -DBLAS_LIBRARIES=${CMAKE_INSTALL_PREFIX}/lib/libopenblas.so
#     -DSUITESPARSE_ENABLE_PROJECTS=suitesparse_config;mongoose;amd;btf;camd;ccolamd;colamd;cholmod;cxsparse;ldl;klu;umfpack;paru;rbio;spqr
#     # 注入 rpath-link 解决链接期间找不到 libopenblas.so.0 的问题
#     -DCMAKE_EXE_LINKER_FLAGS=-Wl,-rpath-link,${CMAKE_INSTALL_PREFIX}/lib

#   # BUILD_COMMAND make -j4 # RK3588 建议限流
#   INSTALL_COMMAND make install
# )

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


# FetchContent_MakeAvailable(suitesparse_vendor)

# 3. 欺骗 colcon：创建一个伪装的 install 目标
# 因为 ExternalProject 在构建时运行，colcon 在配置时看不到 target
# install(DIRECTORY DESTINATION include) 


# cmake .. \
#   -DCMAKE_TOOLCHAIN_FILE=/opt/cmake/rk3588.toolchain.cmake \
#   -DCMAKE_INSTALL_PREFIX=/workspace/output/RK3588/install \
#   -DSUITESPARSE_ENABLE_PROJECTS="suitesparse_config;mongoose;amd;btf;camd;ccolamd;colamd;cholmod;cxsparse;ldl;klu;umfpack;paru;rbio;spqr" \
#   -DBUILD_SHARED_LIBS=ON \
#   -DSUITESPARSE_DEMOS=OFF \
#   -DCMAKE_EXE_LINKER_FLAGS="-Wl,-rpath-link,/workspace/output/RK3588/install/lib" \
#   -DBUILD_TESTING=OFF \
#   -DBUILD_STATIC_LIBS=OFF