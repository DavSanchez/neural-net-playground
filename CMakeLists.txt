# Minimum version of CMake required to build this project
cmake_minimum_required(VERSION 3.0)

# so build/compile_commands.json will be generated
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
# set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17")

# Name of the project
project(Project)

# Include Conan dependencies
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)

# This will setup conan environment. Without this, including our dependencies
# would fail
conan_basic_setup()

# Compile main.cpp
add_executable(project src/main.cpp src/NeuralNetwork.cpp)

# Link the dependencies with our binary
target_link_libraries(project ${CONAN_LIBS})

