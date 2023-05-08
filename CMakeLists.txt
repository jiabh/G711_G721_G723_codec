cmake_minimum_required(VERSION 3.22)
project(G711_G721_G723_codec C)

set(SRC_COMMON g711.c g72x.c g721.c g723_24.c g723_40.c)

# targets
add_library(libG711_G721_G723_codec STATIC ${SRC_COMMON})

add_executable(G711_G721_G723_cod encode.c)
add_executable(G711_G721_G723_dec decode.c)

# include
include_directories(.)

# Config for static library
set_target_properties(
        libG711_G721_G723_codec
        PROPERTIES
        OUTPUT_NAME G711_G721_G723_codec
)

# link library to executable
target_link_libraries(G711_G721_G723_cod PRIVATE libG711_G721_G723_codec)

target_link_libraries(G711_G721_G723_dec PRIVATE libG711_G721_G723_codec)
