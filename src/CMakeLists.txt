set(SRC
    main.cpp
)
add_executable(main ${SRC})
target_link_libraries(main ${Vulkan_LIBRARIES} glfw)
