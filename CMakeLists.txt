cmake_minimum_required(VERSION 3.20)

project(
    ReliableFileTransfer
    VERSION 1.0
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_library(
    file_transfer_common
    INTERFACE
)

target_include_directories(
    file_transfer_common
    INTERFACE
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

add_executable(
    file_transfer_server
    src/server_main.cpp
)

target_link_libraries(
    file_transfer_common
    PRIVATE
        file_transfer_common
        pthread
)

add_executable(
    file_transfer_client
    src/client_main.cpp
)

target_link_libraries(
    file_transfer_common
    PRIVATE
        file_transfer_common
        pthread
)