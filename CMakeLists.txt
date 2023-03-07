cmake_minimum_required(VERSION 2.8)
project(video_transmit)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_COMPILER g++)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
include_directories(${PROJECT_SOURCE_DIR}/include)

set(FFMPEG_LIBS_DIR /usr/local/ffmpeg/lib/)
set(FFMPEG_HEADERS_DIR /usr/local/ffmpeg/include )
include_directories(${FFMPEG_HEADERS_DIR})
link_directories(${FFMPEG_LIBS_DIR})
set(FFMPEG_LIBS libavcodec.so libavformat.so libswscale.so libavdevice.so libavutil.so)

add_executable(rtmp_transmit src/decode_video.c)
# add_executable(get_camera src/get_camera.cpp)

target_link_libraries(rtmp_transmit ${FFMPEG_LIBS})
# target_link_libraries(get_camera ${FFMPEG_LIBS})

