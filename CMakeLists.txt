cmake_minimum_required(VERSION 3.20)
project(imgui)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED)

set(FILES
	${PROJECT_SOURCE_DIR}/imgui.cpp
	${PROJECT_SOURCE_DIR}/imgui.h
	${PROJECT_SOURCE_DIR}/imstb_rectpack.h
	${PROJECT_SOURCE_DIR}/imstb_textedit.h
	${PROJECT_SOURCE_DIR}/imstb_truetype.h
  ${PROJECT_SOURCE_DIR}/imgui_demo.cpp
  ${PROJECT_SOURCE_DIR}/imgui_draw.cpp
  ${PROJECT_SOURCE_DIR}/imgui_internal.h
  ${PROJECT_SOURCE_DIR}/imgui_tables.cpp
  ${PROJECT_SOURCE_DIR}/imgui_widgets.cpp
 )

foreach(BACKEND glfw opengl3)
    set(FILES ${FILES} "${PROJECT_SOURCE_DIR}/backends/imgui_impl_${BACKEND}.h")
    set(FILES ${FILES} "${PROJECT_SOURCE_DIR}/backends/imgui_impl_${BACKEND}.cpp")
endforeach()

set(FILES ${FILES} "${PROJECT_SOURCE_DIR}/backends/imgui_impl_opengl3_loader.h")

add_library(imgui STATIC
	${FILES}
)

target_link_libraries(imgui glfw opengl32)

target_include_directories(imgui PUBLIC
    "./"
)
