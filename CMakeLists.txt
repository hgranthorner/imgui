cmake_minimum_required(VERSION 3.20)
project(imgui)

set(CMAKE_CXX_STANDARD 20)

set(srcs imgui.cpp imgui_draw.cpp imgui_widgets.cpp imgui_tables.cpp)
set(phdrs imgui.h)
set(hdrs imgui_internal.h imstb_rectpack.h imstb_textedit.h imstb_truetype.h)

add_library (imgui-sdl INTERFACE)
target_sources(imgui-sdl INTERFACE
        backends/imgui_impl_sdl2.h
        backends/imgui_impl_sdl2.cpp)

add_library(imgui ${srcs} ${phdrs} ${hdrs})

target_link_libraries(imgui-sdl INTERFACE imgui)
