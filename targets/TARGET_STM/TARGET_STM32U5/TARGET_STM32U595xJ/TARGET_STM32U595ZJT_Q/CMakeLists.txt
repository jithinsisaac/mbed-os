# Copyright (c) 2024 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

add_library(mbed-stm32u595zjt-q INTERFACE)

target_sources(mbed-stm32u595zjt-q
    INTERFACE
        PeripheralPins.c
)

target_include_directories(mbed-stm32u595zjt-q
    INTERFACE
        .
)

target_link_libraries(mbed-stm32u595zjt-q INTERFACE mbed-stm32u595xj)
