include(FetchContent)

FetchContent_Declare(
  Stm32Cube
  GIT_REPOSITORY https://github.com/STMicroelectronics/STM32CubeF4.git
  GIT_TAG v1.25.0
  )

FetchContent_GetProperties(Stm32Cube)
if(NOT Stm32Cube_POPULATED)
  FetchContent_Populate(Stm32Cube)

endif()

set(CMSIS_PATH "${stm32cube_SOURCE_DIR}/Drivers/CMSIS")
add_library(cmsis_core INTERFACE)
target_include_directories(cmsis_core INTERFACE ${CMSIS_PATH}/Core/Include)
add_library(cmsis_rtos2 INTERFACE)
target_include_directories(cmsis_rtos2 INTERFACE  ${CMSIS_PATH}/Core/Include)

add_library(smt32f4 INTERFACE)
target_include_directories(smt32f4 INTERFACE ${CMSIS_PATH}/Device/ST/Core/Include)
