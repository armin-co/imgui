# Dear ImGui CMakeLists.txt for use as Git submodule in other projects

set(
    dear_im_gui_srcs
    imgui.cpp
    imgui_draw.cpp
    imgui_widgets.cpp
)

set(
    dear_imgui_impl_srcs
    example/imgui_impl_sdl.cpp
    example/../imgui_impl_opengl3.cpp
)

include_directories(examples examples/libs/gl3w)

add_definitions(-DIMGUI_IMPL_OPENGL_LOADER_GL3W)

add_library(
    dear_im_gui
    ${dear_im_gui_srcs}
    ${dear_im_gui_impl_srcs}
    examples/libs/gl3w/GL/gl3w.c
)

find_package(SDL2 REQUIRED)
include_directories(${SDL2_INCLUDE_DIRS})

target_link_libraries(
    dear_im_gui
    ${SDL2_LIBRARIES}
)
