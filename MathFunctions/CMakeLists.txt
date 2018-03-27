add_library(MathFunctions mysqrt.cpp)

# Install
install (TARGETS MathFunctions DESTINATION bin)
install (FILES MathFunctions.h DESTINATION include)
