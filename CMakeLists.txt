cmake_minimum_required(VERSION 3.16)

project(gudluck)

# Source files
set(SOURCE_FILES 
    src/main.cpp
)
add_executable(${PROJECT_NAME} ${SOURCE_FILES})

# opengl function pointers loaders
option (GLAD "USING GLAD" OFF)

# glad
if (GLAD)
    add_subdirectory(vendor/glad)
    target_link_libraries(${PROJECT_NAME} PRIVATE glad::glad)

# glew
else()
    find_package(GLEW REQUIRED)
    include_directories(${GLEW_INCLUDE_DIRS})
    target_link_libraries(${PROJECT_NAME} PRIVATE GLEW::GLEW)
endif()

# glfw
add_subdirectory(vendor/glfw)
include_directories("${GLFW_SOURCE_DIR}/deps")
target_link_libraries(${PROJECT_NAME} PRIVATE glfw)

# opengl
find_package(OpenGL REQUIRED)
include_directories( ${OPENGL_INCLUDE_DIRS} )
target_link_libraries(${PROJECT_NAME} PRIVATE OpenGL::GL)
