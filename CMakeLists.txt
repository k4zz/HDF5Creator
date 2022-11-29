cmake_minimum_required(VERSION 3.16)

project(HDF5Creator
        VERSION 0.0)

option(TESTS "" OFF)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

add_subdirectory(3rdparty)
add_subdirectory(src/example-module)
add_subdirectory(src/exe)



if (${TESTS})
    add_subdirectory(3rdparty/googletest)
    enable_testing()
    include(GoogleTest)
    add_subdirectory(tests)
endif ()
