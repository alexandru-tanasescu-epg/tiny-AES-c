cmake_minimum_required(VERSION 3.12)

project(AES128CTREncryption CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add executable target for the AES-128 CTR mode benchmarking program
add_executable(${PROJECT_NAME} mainAES128CTR.cpp)

# Ensure release mode if no build type is provided
# If build type is set to "Profiling", set optimization level to O2 and 
# enable debug symbols in order for profiling tools to work properly

if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
elseif (${CMAKE_BUILD_TYPE} STREQUAL "Profiling")
    message(STATUS "   Configuring for Profiling build with O2 and debug symbols.")
    target_compile_options(${PROJECT_NAME} PRIVATE -O2 -g)
endif()

message(STATUS "Configuring for ${CMAKE_BUILD_TYPE} build!")

# Make the root directory available for the current project (for aes.hpp and aes.c)
target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/..)

# Set the current directory as the output directory for the executable
set(OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})
set_target_properties(${PROJECT_NAME} PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY                ${OUTPUT_DIRECTORY}
    RUNTIME_OUTPUT_DIRECTORY_DEBUG          ${OUTPUT_DIRECTORY}
    RUNTIME_OUTPUT_DIRECTORY_RELEASE        ${OUTPUT_DIRECTORY})
