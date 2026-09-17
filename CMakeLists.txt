cmake_minimum_required(VERSION 3.10)
project(MyCMakeProject)

# Все выходные файлы (exe, dll, lib) — в папку bin
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin)

# Библиотека
add_library(util_lib SHARED util/util.cpp)
target_include_directories(util_lib PUBLIC util)

# Явно указываем, что экспортируемые символы должны создавать импортную .lib
set_target_properties(util_lib PROPERTIES
    WINDOWS_EXPORT_ALL_SYMBOLS ON
)

# Исполняемый файл
add_executable(my_app main.cpp)
target_link_libraries(my_app PRIVATE util_lib)