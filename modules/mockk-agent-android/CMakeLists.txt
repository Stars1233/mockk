cmake_minimum_required(VERSION 3.4.1)

set(slicer_sources
    external/slicer/bytecode_encoder.cc
    external/slicer/code_ir.cc
    external/slicer/common.cc
    external/slicer/control_flow_graph.cc
    external/slicer/debuginfo_encoder.cc
    external/slicer/dex_bytecode.cc
    external/slicer/dex_format.cc
    external/slicer/dex_ir_builder.cc
    external/slicer/dex_ir.cc
    external/slicer/dex_utf8.cc
    external/slicer/instrumentation.cc
    external/slicer/reader.cc
    external/slicer/tryblocks_encoder.cc
    external/slicer/writer.cc)

add_library(slicer
            STATIC
            ${slicer_sources})

include_directories(external/jdk external/slicer/export/)

target_link_libraries(slicer z)

add_library(mockkjvmtiagent
            SHARED
            src/main/jni/mockkjvmtiagent/proxy-agent.cc)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -frtti -Wall -Werror -Wno-unused-parameter -Wno-shift-count-overflow -Wno-error=non-virtual-dtor -Wno-sign-compare -Wno-switch -Wno-missing-braces")

target_link_libraries(mockkjvmtiagent slicer)

target_link_options(mockkjvmtiagent PRIVATE "-Wl,-z,max-page-size=16384")