cmake_minimum_required(VERSION 3.5)
project(exoskeletonS1)
set(CMAKE_CXX_STANDARD 17)

find_package(Concurrency REQUIRED)
if(Concurrency_FOUND)
    message(STATUS "Concurrency package found and successfully imported.")
else()
    message(FATAL_ERROR "Failed to find the Concurrency package.")
endif()


set(MESSAGE ON)
if(MESSAGE)
    message(STATUS "srcPROJECT_BINARY_DIR: ${PROJECT_BINARY_DIR}")
    message( STATUS "srcPROJECT_SOURCE_DIR: ${PROJECT_SOURCE_DIR}" )
    message( STATUS "srcCMAKE_BINARY_DIR: ${CMAKE_BINARY_DIR}" )
endif()

add_subdirectory(concurrency)


add_executable(main main.cpp)
set_property(TARGET main PROPERTY RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

target_link_libraries(main concurrency)




