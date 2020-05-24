cmake_minimum_required(VERSION 3.16)
project(renderer)

set(CMAKE_CXX_STANDARD 11)

# config output
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH  ${PROJECT_SOURCE_DIR}/lib)

# config glfw
option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_TESTS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
add_subdirectory(third_party/glfw)
include_directories(third_party/glfw/include)
set(LIBS ${LIBS} glfw)

# config glad
set(GLAD_SRC third_party/glad/src/glad.c)
include_directories(third_party/glad/include)

# add compile source file
set(SOURCES main.cc ${GLAD_SRC})

add_executable(renderer ${SOURCES})
target_link_libraries(renderer ${LIBS})