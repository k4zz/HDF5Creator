cmake_minimum_required(VERSION 3.16)

project(Version LANGUAGES CXX)

# == BUILD ==

add_library(${PROJECT_NAME} INTERFACE)

add_library(${CMAKE_PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

configure_file(cmake/version.cmake.in ${CMAKE_CURRENT_BINARY_DIR}/include/HDF5Creator/Version.h)

target_include_directories(${PROJECT_NAME}
        INTERFACE
            ${CMAKE_CURRENT_BINARY_DIR}/include)
