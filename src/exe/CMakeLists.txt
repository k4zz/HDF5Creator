cmake_minimum_required(VERSION 3.16)

project(${CMAKE_PROJECT_NAME} LANGUAGES CXX)

# == BUILD ==

add_executable(${PROJECT_NAME}
        ${SOURCE_FILES})

target_sources(${PROJECT_NAME}
        PRIVATE
            src/main.cpp)

target_include_directories(${PROJECT_NAME}
        PRIVATE
            src)

target_compile_features(${PROJECT_NAME}
        PRIVATE
        cxx_std_17)

# find_package()

target_link_libraries(${PROJECT_NAME}
        PRIVATE
        HDF5Creator::Version
        HDF5Creator::ExampleModule
        imgui
        PUBLIC)

add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy $<TARGET_RUNTIME_DLLS:${PROJECT_NAME}> $<TARGET_FILE_DIR:${PROJECT_NAME}>
        COMMAND_EXPAND_LISTS)

# == INSTALL ==

include(GNUInstallDirs)

install(TARGETS ${PROJECT_NAME}
        RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
