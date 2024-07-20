cmake_minimum_required(VERSION 3.26)
project(StaticOpenGL)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_FIND_LIBRARY_SUFFIXES ".a")

#message("X11_LIB_SEARCH_PATH=${X11_LIB_SEARCH_PATH}")
add_subdirectory(${CMAKE_SOURCE_DIR}/glfw)
#message("X11_LIB_SEARCH_PATH=${X11_LIB_SEARCH_PATH}")

add_library(glad STATIC ${CMAKE_SOURCE_DIR}/glad/src/glad.c)
target_include_directories(glad PUBLIC ${CMAKE_SOURCE_DIR}/glad/include)

add_executable(test main.cpp)

target_link_libraries(test PRIVATE glfw glad ${GLFW_LIBRARIES} )
target_include_directories(test PRIVATE 
${CMAKE_SOURCE_DIR}/glfw/include
)

