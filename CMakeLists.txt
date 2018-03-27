cmake_minimum_required (VERSION 3.8)

project (cross-compile)

set (CROSS_VERSION_MAJOR 1)
set (CROSS_VERSION_MINOR 0)

# configure a header file to pass some of the CMake settings
# to the source code
configure_file (
  "${PROJECT_SOURCE_DIR}/CrossConfig.h.in"
  "${PROJECT_BINARY_DIR}/CrossConfig.h"
  )

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_BINARY_DIR}")

add_executable(cross-compile main.cpp)

