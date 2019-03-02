#cmake

cmake_minimum_required(VERSION 3.5)

project(imgui)

find_package(SDL2 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(gl3w REQUIRED)

set(imgui_SRC
  imgui.cpp
  imgui_demo.cpp
  imgui_draw.cpp
  imgui_widgets.cpp
  examples/imgui_impl_sdl.cpp
  examples/imgui_impl_opengl3.cpp
  )

add_library(${PROJECT_NAME} ${imgui_SRC})

target_include_directories(${PROJECT_NAME}
  PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    examples
  )
    
target_link_libraries(${PROJECT_NAME}
  INTERFACE
    SDL2
    gl3w
    ${OPENGL_gl_LIBRARY}
  )

target_compile_features(${PROJECT_NAME}
  PRIVATE
    cxx_std_11
  )
