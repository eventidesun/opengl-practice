cmake_minimum_required(VERSION 3.30)
project(HelloTriangle)

set(CMAKE_CXX_STANDARD 20)

add_executable(HelloTriangle main.cpp)
target_include_directories(HelloTriangle PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/Libraries/include)

# glfw headers in Libraries/include
target_include_directories(HelloTriangle PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/Libraries/include)

# glad stuff
add_library(glad STATIC Libraries/src/glad.c)
target_include_directories(glad PUBLIC Libraries/include)

# link static glfw and macos frameworks
target_link_libraries(HelloTriangle
        PRIVATE
        glad
        ${CMAKE_CURRENT_SOURCE_DIR}/Libraries/lib/libglfw3.a
        "-framework OpenGL"
        "-framework Cocoa"
        "-framework IOKit"
        "-framework CoreVideo"
)
