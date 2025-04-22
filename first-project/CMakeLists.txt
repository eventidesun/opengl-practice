cmake_minimum_required(VERSION 3.10)
project(first_project)

set(CMAKE_CXX_STANDARD 20)

add_executable(first_project main.cpp)
target_include_directories(first_project PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/Libraries/include) # because we added glad

# glfw headers in Libraries/include
target_include_directories(first_project PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/Libraries/include)

# glad stuff
add_library(glad STATIC Libraries/src/glad.c)
target_include_directories(glad PUBLIC Libraries/include)

# link static glfw and macos frameworks
target_link_libraries(first_project
        PRIVATE
        glad
        ${CMAKE_CURRENT_SOURCE_DIR}/Libraries/lib/libglfw3.a
        "-framework OpenGL"
        "-framework Cocoa"
        "-framework IOKit"
        "-framework CoreVideo"
)
