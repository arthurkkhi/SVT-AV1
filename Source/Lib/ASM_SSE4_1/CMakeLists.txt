# 
# Copyright(c) 2019 Intel Corporation
# SPDX - License - Identifier: BSD - 2 - Clause - Patent
# 

# ASM_SSE4.1 Directory CMakeLists.txt

# Include Encoder Subdirectories
include_directories (${PROJECT_SOURCE_DIR}/Source/API/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/Codec/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/C_DEFAULT/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/ASM_SSE2/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/ASM_SSSE3/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/ASM_SSE4_1/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/ASM_AVX2/)

if(${CMAKE_SYSTEM_NAME} MATCHES "Windows")
    SET(CMAKE_C_FLAGS "/MP")    
endif(${CMAKE_SYSTEM_NAME} MATCHES "Windows")

if(CMAKE_C_COMPILER_ID STREQUAL "GNU")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -msse4.1")
endif()

if(CMAKE_C_COMPILER_ID STREQUAL "Intel")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fPIC -static-intel -w")
endif()


file(GLOB all_files
    "*.h"
    "*.asm"
    "*.c")

add_library(ASM_SSE4_1
    ${all_files}
)




