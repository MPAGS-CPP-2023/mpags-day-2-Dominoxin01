# - Set CMake requirements then declare project:
cmake_minimum_required(VERSION 3.2)

# - When Makefiles are generated, output all command lines by default
#   Do this to begin with so it's easy to see what compiler command/flags
#   are used. This can also be done by removing the 'set' command and 
#   running make as 'make VERBOSE=1'.
set(CMAKE_VERBOSE_MAKEFILE ON)


set (CMAKE_CXX_STANDARD_REQUIRED ON)
# - Set the C++ Standard directly
set(CMAKE_CXX_STANDARD 11)

# - Declare the build of mpags-cipher main program
add_executable(mpags-cipher 
    mpags-cipher.cpp
    MPAGSCipher/TransformChar.cpp
    )

target_include_directories(mpags-cipher
PRIVATE MPAGSCipher)

# - Use our standard set of flags
set(CMAKE_CXX_FLAGS "-Wall -Wextra -Werror -Wfatal-errors -Wshadow -pedantic")

target_compile_features(mpags-cipher
PRIVATE cxx_auto_type cxx_range_for cxx_uniform_initialization
)

