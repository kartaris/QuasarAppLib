#
# Copyright (C) 2018-2020 QuasarApp.
# Distributed under the lgplv3 software license, see the accompanying
# Everyone is permitted to copy and distribute verbatim copies
# of this license document, but changing it is not allowed.
#

if(DEFINED QUASARAPP_LIBRARY)
  return()
else()
  set(QUASARAPP_LIBRARY 1)
  add_definitions(-DQUASARAPP_LIBRARY)
endif()

project(QuasarApp)

if(TARGET ${PROJECT_NAME})
  message("The ${PROJECT_NAME} arledy included in main Project")
  return()
endif()

cmake_minimum_required(VERSION 3.1)
#include(CMake/crossplatform/crossplatform.cmake)


include(CMake/ProjectOut.cmake)
include(CMake/ccache.cmake)
include(CMake/Version.cmake)


set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 COMPONENTS Core REQUIRED)

file(GLOB SOURCE_CPP
    "*.cpp"
)

add_library(${PROJECT_NAME} ${SOURCE_CPP})
target_link_libraries(${PROJECT_NAME} PRIVATE Qt5::Core)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

setVersion(1 4 1)
