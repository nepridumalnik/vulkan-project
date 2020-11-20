cmake_minimum_required(VERSION 3.16)
project(vulkan_project)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/out)
set(CMAKE_CXX_STANDARD_REQUIRED on)
set(CMAKE_CXX_STANDARD 17)
include_directories(${CMAKE_SOURCE_DIR}/include)

# Compiling GLFW3 from sources
add_subdirectory(${CMAKE_SOURCE_DIR}/src/GLFW)

# Adding Vulkan dependencies if Vulkan was found else do nothing
find_package(Vulkan REQUIRED)
include_directories(${Vulkan_INCLUDE_DIRS})
link_directories(${Vulkan_LIBRARIES})
add_subdirectory(src)