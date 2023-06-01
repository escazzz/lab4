cmake_minimum_required(VERSION 3.2)

project(Hello_World)

add_library(formatter_lib STATIC ../formatter_lib/formatter.cpp)

target_include_directories(formatter_lib PUBLIC ../formatter_lib)

add_library(formatter_ex_lib STATIC ../formatter_ex_lib/formatter_ex.cpp)

target_include_directories(formatter_ex_lib PUBLIC ../formatter_ex_lib)

add_executable(hello_world hello_world.cpp)

target_link_libraries(formatter_ex_lib formatter_lib)

target_link_libraries(hello_world formatter_ex_lib)
