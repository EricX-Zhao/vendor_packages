cmake_minimum_required(VERSION 3.8)
project(uncrustify_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

include(FetchContent)
FetchContent_Declare(
  uncrustify_vendor
  GIT_REPOSITORY https://github.com/uncrustify/uncrustify.git
  GIT_TAG uncrustify-0.78.1
  GIT_SHALLOW TRUE
)

set(NoGitVersionString ON CACHE BOOL "NoGitVersionString" FORCE)

FetchContent_MakeAvailable(uncrustify_vendor)

