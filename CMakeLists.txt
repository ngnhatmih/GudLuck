cmake_minimum_required(VERSION 3.16)

project(gudluck)

# Source files
set(SOURCE_FILES 
    src/main.cpp
)
add_executable(${PROJECT_NAME} ${SOURCE_FILES})

# glad
add_subdirectory(vendor/glad)
target_link_libraries(${PROJECT_NAME} PRIVATE glad::glad)

# glfw
add_subdirectory(vendor/glfw)
include_directories("${GLFW_SOURCE_DIR}/deps")
target_link_libraries(${PROJECT_NAME} PRIVATE glfw)

# opengl
find_package(OpenGL REQUIRED)
include_directories( ${OPENGL_INCLUDE_DIRS} )
target_link_libraries(${PROJECT_NAME} PRIVATE OpenGL::GL)
