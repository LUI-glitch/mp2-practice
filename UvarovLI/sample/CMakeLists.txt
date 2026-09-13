# Сборка примера на macOS/Linux через CMake.
# Проект Visual Studio в sln/Project1 остаётся рабочим для Windows.
cmake_minimum_required(VERSION 3.10)

set(PROJECT_NAME complex)
project(${PROJECT_NAME} CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(MP2_LIBRARY "${PROJECT_NAME}")
set(MP2_INCLUDE "${CMAKE_CURRENT_SOURCE_DIR}/include")

include_directories("${MP2_INCLUDE}")

add_subdirectory(src)
add_subdirectory(samples)

message(STATUS "")
message(STATUS "Конфигурация ${PROJECT_NAME}: ${CMAKE_BUILD_TYPE}")
message(STATUS "")
