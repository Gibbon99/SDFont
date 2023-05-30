cmake_minimum_required(VERSION 3.25)
project(SDFont-Gen)
include(FetchContent)
set(CMAKE_CXX_STANDARD 17)
#
# Set source files here
file(GLOB_RECURSE source_files           CONFIGURE_DEPENDS  "./src_lib/*.cpp")

set(SOURCES
        ${source_files}
        src_bin/sdfont_generator.cpp
        )

#
# Set options for different builds here
if (CMAKE_BUILD_TYPE MATCHES Debug)
    add_definitions(-DMY_DEBUG=1)              # Preprocessor for compiler
endif ()

if (CMAKE_BUILD_TYPE MATCHES Release)
endif ()

include_directories("/usr/include/freetype2")
include_directories(SYSTEM ${CMAKE_CURRENT_SOURCE_DIR}/include)
include_directories(SYSTEM ${CMAKE_CURRENT_SOURCE_DIR}/)

#
# Link with these libraries
link_libraries(GL GLEW glfw png freetype)

#
# Place the output binaries here
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)

add_executable(${PROJECT_NAME} ${SOURCES})
