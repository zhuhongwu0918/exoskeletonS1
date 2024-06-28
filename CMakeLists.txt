cmake_minimum_required(VERSION 3.5)
project(exoskeletonS1)
# We will be using c++17
set(CMAKE_CXX_STANDARD 17)

message(STATUS "PROJECT_BINARY_DIR: ${PROJECT_BINARY_DIR}")
add_subdirectory(src)

set(MESSAGE ON)
if(MESSAGE)
    message(STATUS "PROJECT_BINARY_DIR: ${PROJECT_BINARY_DIR}")
    message( STATUS "PROJECT_SOURCE_DIR: ${PROJECT_SOURCE_DIR}" )
    message( STATUS "CMAKE_BINARY_DIR: ${CMAKE_BINARY_DIR}" )
endif()


option(BUILD_TESTS "Build library tests" OFF)


if (BUILD_TESTS)
    message(STATUS "Building tests...")
    add_subdirectory(test)
endif()


add_subdirectory(third_party)
