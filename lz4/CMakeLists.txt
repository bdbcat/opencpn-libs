cmake_minimum_required(VERSION 3.1.0)

if (TARGET ocpn::lz4)
    return ()
endif ()

set(SRC src/lz4.c  src/lz4.h  src/lz4hc.c  src/lz4hc.h)

add_library(LZ4 STATIC ${SRC})
add_library(ocpn::lz4 ALIAS LZ4)
if (CMAKE_CXX_COMPILER_ID MATCHES "Clang|GNU")
  set_property(TARGET LZ4 PROPERTY COMPILE_FLAGS "-fvisibility=hidden")
endif ()
set_property(TARGET LZ4 PROPERTY POSITION_INDEPENDENT_CODE ON)
target_include_directories(LZ4 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
