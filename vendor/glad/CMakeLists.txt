# CMake minimum 3.16
cmake_minimum_required(VERSION 3.16)

# glad project
project(glad)

# Add the glad (GL) library
add_library(glad STATIC src/glad.c)

# Add simple aliases for the glad (GL) library
add_library(glad::glad ALIAS glad)
add_library(glad::gl ALIAS glad)

# Add include directory for glad
target_include_directories(glad PUBLIC include)