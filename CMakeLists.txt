cmake_minimum_required(VERSION 3.16)
project(vulkan_project)

set(CMAKE_CXX_STANDARD_REQUIRED on)
set(CMAKE_CXX_STANDARD 17)
include_directories(${CMAKE_SOURCE_DIR}/include)

# Compiling GLFW3 from sources
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory(${CMAKE_SOURCE_DIR}/src/GLFW)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/out)

# Adding Vulkan dependencies if Vulkan was found else do nothing
find_package(Vulkan REQUIRED)
if(Vulkan_FOUND)
    include_directories("$ENV{VULKAN_SDK}/include")
    link_directories("$ENV{VULKAN_SDK}/lib")
    add_subdirectory(src)
endif()