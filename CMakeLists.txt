cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Pull in Raspberry Pi Pico SDK
include(pico_sdk_import.cmake)

if (PICO_SDK_VERSION_STRING VERSION_LESS "1.5.1")
  message(FATAL_ERROR "Raspberry Pi Pico SDK version 1.5.1 (or later) required. Your version is ${PICO_SDK_VERSION_STRING}")
endif()

project(usb2serial C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

add_executable(usb2serial usb2serial.c)

pico_set_program_name(usb2serial "usb2serial")
pico_set_program_version(usb2serial "0.1")

pico_enable_stdio_uart(usb2serial 1)
pico_enable_stdio_usb(usb2serial 0)

target_include_directories(usb2serial PUBLIC ${CMAKE_CURRENT_LIST_DIR})
target_link_libraries(usb2serial pico_stdlib tinyusb_host tinyusb_board)

pico_add_extra_outputs(usb2serial)
