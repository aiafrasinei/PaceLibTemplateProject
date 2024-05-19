cmake_minimum_required(VERSION 3.5)

project(template)


include_directories(source)

set(LIBS_PATH "${CMAKE_CURRENT_SOURCE_DIR}/libs")
set(PACE_INCLUDE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/libs/linux/PaceLib/include/PaceLib")

include_directories("${PACE_INCLUDE_PATH}")
include_directories("${PACE_INCLUDE_PATH}/utils")
include_directories("${PACE_INCLUDE_PATH}/utils/SDL2")
include_directories("${PACE_INCLUDE_PATH}/config")
include_directories("${PACE_INCLUDE_PATH}/core")
include_directories("${PACE_INCLUDE_PATH}/graphics")
include_directories("${PACE_INCLUDE_PATH}/graphics/points")
include_directories("${PACE_INCLUDE_PATH}/graphics/lines")
include_directories("${PACE_INCLUDE_PATH}/graphics/effects")
include_directories("${PACE_INCLUDE_PATH}/graphics/polygons")
include_directories("${PACE_INCLUDE_PATH}/graphics/polygons/quads")
include_directories("${PACE_INCLUDE_PATH}/graphics/conics")
include_directories("${PACE_INCLUDE_PATH}/graphics/gui")
include_directories("${PACE_INCLUDE_PATH}/resources")
include_directories("${PACE_INCLUDE_PATH}/scene")

set(CMAKE_CXX_FLAGS "-std=c++20")

include_directories("/opt/homebrew/include")
include_directories("/mingw64/include/")

link_directories("/opt/homebrew/lib/")
link_directories("/usr/local/lib64/")
link_directories("/mingw64/lib/")

if (MSYS OR MINGW)
        message("this is sparta")
        link_directories("${LIBS_PATH}/windows/PaceLib/")
else()
        link_directories("${LIBS_PATH}/linux/PaceLib/")
endif()

add_executable (template
        src/main.cpp)

target_link_libraries(template m dl libPaceLib.a SDL2 SDL2_image SDL2_ttf pthread)
