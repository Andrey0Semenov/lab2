cmake_minimum_required(VERSION 3.10)
project(MyCMakeProject)

add_library(util_lib STATIC util/util.cpp)
target_include_directories(util_lib PUBLIC util)

add_executable(my_app main.cpp)
target_link_libraries(my_app PRIVATE util_lib)