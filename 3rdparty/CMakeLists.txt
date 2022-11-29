cmake_minimum_required(VERSION 3.16)

project(imgui VERSION 0.0 LANGUAGES CXX)

add_library(${PROJECT_NAME} STATIC)

target_sources(${PROJECT_NAME}
        PRIVATE
            imgui/imgui_demo.cpp
            imgui/imgui_draw.cpp
            imgui/imgui_tables.cpp
            imgui/imgui_widgets.cpp
            imgui/imgui.cpp
        PRIVATE
            imgui/backends/imgui_impl_opengl3.cpp
            imgui/backends/imgui_impl_sdl.cpp
        )

target_include_directories(${PROJECT_NAME}
        PUBLIC imgui
        PUBLIC imgui/backends
        )

target_compile_features(${PROJECT_NAME}
        PRIVATE
            cxx_std_17)


find_package(OpenGL REQUIRED)
find_package(SDL2 REQUIRED)

target_link_libraries(${PROJECT_NAME} PUBLIC ${OPENGL_LIBRARIES})
target_link_libraries(${PROJECT_NAME} PUBLIC SDL2::SDL2main SDL2::SDL2)