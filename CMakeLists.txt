cmake_minimum_required(VERSION 3.17 )

project(QTBreakpadplugin VERSION 1.0 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)

find_package(unofficial-breakpad CONFIG REQUIRED )
find_package(Qt5 REQUIRED COMPONENTS Core )

add_library(${PROJECT_NAME} qt_breakpad.cpp qt_breakpad.h)

target_link_libraries(${PROJECT_NAME}
    PRIVATE Qt5::Core
    PRIVATE unofficial::breakpad::libbreakpad
    PRIVATE unofficial::breakpad::libbreakpad_client)

target_include_directories(${PROJECT_NAME}
    PUBLIC ${VCPKG_INCLUDE_PATH})
