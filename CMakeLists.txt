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

# should we use our own math functions?
option (USE_MYMATH 
        "Use tutorial provided math implementation" ON) 

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_BINARY_DIR}")

if (USE_MYMATH)
  include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
  add_subdirectory (MathFunctions)
  set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif (USE_MYMATH)
 
# add the executable
add_executable (cross-compile main.cpp)
target_link_libraries (cross-compile ${EXTRA_LIBS})



