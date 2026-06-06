cmake_minimum_required(VERSION 3.12)

project(AES128CTREncryption)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(${PROJECT_NAME} mainAES128CTR.cpp)

# Make the root directory available for the current project (for aes.hpp and aes.c)
target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/..)

# Set the current directory as the output directory for the executable
set(OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})
set_target_properties(${PROJECT_NAME} PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY                ${OUTPUT_DIRECTORY}
    RUNTIME_OUTPUT_DIRECTORY_DEBUG          ${OUTPUT_DIRECTORY}
    RUNTIME_OUTPUT_DIRECTORY_RELEASE        ${OUTPUT_DIRECTORY})
