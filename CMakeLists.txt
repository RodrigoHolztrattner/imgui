cmake_minimum_required(VERSION 3.1.1 FATAL_ERROR)

###########
# PROJECT #
###########

set(PROJECT_NAME "imgui")
project(${PROJECT_NAME} VERSION 1.0.0 DESCRIPTION "blob")

SET(CMAKE_CXX_FLAGS "/Zi /sdl /MP /Oi /Gy /permissive- /GR- /TP /EHsc")
SET(CMAKE_CXX_FLAGS_DEBUG "/ZI /sdl /MP /JMC /permissive- /GR- /TP /EHsc /MDd /Od")

add_library(${PROJECT_NAME} STATIC
    imgui.cpp
    imgui.h
    imgui_demo.cpp
    imgui_draw.cpp
    imgui_widgets.cpp
    imgui_internal.h
    imconfig.h
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h)

###########
# INSTALL #
###########

include(GNUInstallDirs)

install(TARGETS ${PROJECT_NAME}
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
  PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
  COMPONENT library)

set_target_properties(${PROJECT_NAME} PROPERTIES
  CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON)    
    
add_definitions(-DUNICODE 
    -D_UNICODE)