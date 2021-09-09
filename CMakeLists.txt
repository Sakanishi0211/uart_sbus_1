cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(uart_sbus C CXX ASM)
set(CMAKE_C_STNDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(uart_sbus
        uart_sbus.c
)

# Pull in our pico_stdlib which pulls in commonly used features
target_link_libraries(uart_sbus pico_stdlib hardware_uart)

# enable usb output, disable uart output
pico_enable_stdio_usb(uart_sbus 1)
pico_enable_stdio_uart(uart_sbus 0)

# create map/bin/hex file etc.
pico_add_extra_outputs(uart_sbus)
