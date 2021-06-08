cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(myplay)

find_package(SDL2 REQUIRED)

# FFmpeg source
set(FFMPEG_SOURCE ~/ffmpeg-4.3.1)

# FFmpeg build
set(FFMPEG_BUILD ~/ffmpeg-4.3.1/build)

set(CMAKE_CXX_FLAGS   "-fpermissive -w -g")

aux_source_directory(. DIR_SRCS)

add_executable(myplay ${DIR_SRCS})

target_include_directories(myplay PRIVATE
                          ${SDL2_INCLUDE_DIRS}
                          ${FFMPEG_SOURCE}
                          ${FFMPEG_BUILD}
                          )

target_link_libraries(myplay
                     -lavcodec
                     -lavdevice
                     -lavfilter
                     -lavformat
                     -lavutil
                     -lswresample
                     -lswscale
                     -lm
                     -lSDL2
                     )

set_property(TARGET myplay PROPERTY CXX_STANDARD 14)
