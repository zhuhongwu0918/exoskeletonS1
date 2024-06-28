cmake_minimum_required(VERSION 3.5)
project(exoskeletonS1)
# We will be using c++17
set(CMAKE_CXX_STANDARD 17)

message(STATUS "PROJECT_BINARY_DIR: ${PROJECT_BINARY_DIR}")
add_subdirectory(src)

if(CMAKE_INSTALL_PREFIX STREQUAL "/usr" OR CMAKE_INSTALL_PREFIX STREQUAL "/usr/local")
  if(CMAKE_SIZEOF_VOID_P EQUAL 8)
    set(CMAKE_INSTALL_LIBDIR lib64)
  else()
    set(CMAKE_INSTALL_LIBDIR lib)
  endif()
endif()

set(MESSAGE ON)
if(MESSAGE)
    message(STATUS "PROJECT_BINARY_DIR: ${PROJECT_BINARY_DIR}")
    message( STATUS "PROJECT_SOURCE_DIR: ${PROJECT_SOURCE_DIR}" )
    message( STATUS "CMAKE_BINARY_DIR: ${CMAKE_BINARY_DIR}" )
    message( STATUS "CMAKE_INSTALL_LIBDIR: ${CMAKE_INSTALL_LIBDIR}" )
    message( STATUS "CMAKE_INSTALL_PREFIX: ${CMAKE_INSTALL_PREFIX}" )
    message( STATUS "CMAKE_SIZEOF_VOID_P: ${CMAKE_SIZEOF_VOID_P}" )
endif()


option(BUILD_TESTS "Build library tests" OFF)


if (BUILD_TESTS)
    message(STATUS "Building tests...")
    add_subdirectory(test)
endif()


add_subdirectory(third_party)
