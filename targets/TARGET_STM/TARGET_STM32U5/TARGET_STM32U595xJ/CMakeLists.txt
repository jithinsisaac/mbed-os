# Copyright (c) 2024 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

add_subdirectory(TARGET_STM32U595ZJT_Q EXCLUDE_FROM_ALL)

if(${MBED_TOOLCHAIN} STREQUAL "GCC_ARM")
    set(STARTUP_FILE TOOLCHAIN_GCC_ARM/startup_stm32u595xx.S)
    set(LINKER_FILE TOOLCHAIN_GCC_ARM/stm32u595xj.ld)
elseif(${MBED_TOOLCHAIN} STREQUAL "ARM")
    set(STARTUP_FILE TOOLCHAIN_ARM/startup_stm32u595xx.S)
    set(LINKER_FILE TOOLCHAIN_ARM/stm32u595xj.sct)
endif()

add_library(mbed-stm32u595xj INTERFACE)

target_sources(mbed-stm32u595xj
    INTERFACE
        PeripheralPins.c
)

target_include_directories(mbed-stm32u595xj
    INTERFACE
        .
)

target_sources(mbed-stm32u595xj
    INTERFACE
        ${STARTUP_FILE}
        system_clock.c
)

mbed_set_linker_script(mbed-stm32u595xj ${CMAKE_CURRENT_SOURCE_DIR}/${LINKER_FILE})

target_link_libraries(mbed-stm32u595xj INTERFACE mbed-stm32u595xj)
