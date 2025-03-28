# CMakeLists.txt
cmake_minimum_required(VERSION 3.20)
project(SplatConverter)

set(CMAKE_CXX_STANDARD 20)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/cc)
# Add source files
set(SOURCES
    cc/load-spz.cc
    cc/splat-c-types.cc
    cc/splat-types.cc
)

# Add source files
add_executable(splat_converter  main.cpp ${SOURCES})

# Link zlib for compression/decompression
find_package(ZLIB REQUIRED)
target_link_libraries(splat_converter  PRIVATE ZLIB::ZLIB)

# DLL for Unity
add_library(spz_converter SHARED spz_converter_api.cpp ${SOURCES})
target_link_libraries(spz_converter ZLIB::ZLIB)

# Define DLL export macro for Windows
target_compile_definitions(spz_converter PRIVATE SPZ_CONVERTER_EXPORTS)