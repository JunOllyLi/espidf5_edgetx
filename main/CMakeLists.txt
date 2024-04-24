idf_component_register(SRCS "espidf5_edgetx_main.cpp"
                    INCLUDE_DIRS ""
                    REQUIRES lvgl lvgl_esp32_drivers
                )

set(DISABLE_COMPANION YES)
set(GVARS YES)
set(LUA YES)
set(DEBUG YES)
set(CMAKE_BUILD_TYPE Debug)

add_definitions(-DPCB_MUFFIN)

option(EdgeTX_SUPERBUILD "Cross-compile EdgeTX for each toolchain" OFF)

set(USE_OLED_FEATHERWING OFF)
add_subdirectory(edgetx)

target_compile_options(tx_firmware PRIVATE -Wno-ignored-qualifiers -Wno-deprecated-enum-enum-conversion -Wno-error=dangling-pointer= -Wno-error=format -Wno-format -Wno-missing-field-initializers)

