cmake_minimum_required(VERSION 3.0.0)
project(ImGui VERSION 0.1.0)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(SOURCES
    imgui.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp
    imgui_demo.cpp
    backends/imgui_impl_opengl3.cpp
    backends/imgui_impl_glfw.cpp
)
set(HEADERS
    imconfig.h
    imgui.h
    imgui_internal.h
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h
    backends/imgui_impl_opengl3.h
    backends/imgui_impl_glfw.h
    backends/imgui_impl_opengl3_loader.h
)

add_library(${PROJECT_NAME} STATIC ${HEADERS} ${SOURCES} ${HEADERS_B} ${SOURCES_B})

target_include_directories(${PROJECT_NAME}
    PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}" "${CMAKE_CURRENT_SOURCE_DIR}/backends"
)
message("${CMAKE_CURRENT_SOURCE_DIR}")

target_link_directories(${PROJECT_NAME} PRIVATE vendor/GLFW/src)
target_link_libraries(${PROJECT_NAME} PRIVATE glfw)