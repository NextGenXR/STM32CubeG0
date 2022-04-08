/**
  @page DemoLoader   Demo STM32G081B-EVAL
 
  @verbatim
  ******************************************************************************
  * @file    readme.txt 
  * @author  MCD Application Team
  * @brief   Description of STM32G081B-EVAL Demo Loader
  ******************************************************************************
  * @attention
  *
  * Copyright (c) 2018 STMicroelectronics.
  * All rights reserved.
  *
  * This software is licensed under terms that can be found in the LICENSE file
  * in the root directory of this software component.
  * If no LICENSE file comes with this software, it is provided AS-IS.
  *
  ******************************************************************************
  @endverbatim

@par Demo Description

The provided demonstration "Loader" firmware based on STM32Cube helps you to discover STM32
Cortex-M devices that can be plugged on a STM32G081B-EVAL board. 

The role of the demonstration loader is to load the so called "legacy" binary or the UCPD binary
according to the daughter board connected to the extension connector of the mother board.

At the beginning of the main program the HAL_Init() function is called to reset 
all the peripherals, initialize the Flash interface and the systick.
Then the SystemClock_Config() function is used to configure the system clock
(SYSCLK) to run at 64 MHz.

@note Care must be taken when using HAL_Delay(), this function provides accurate
      delay (in milliseconds) based on variable incremented in SysTick ISR. 
      This implies that if HAL_Delay() is called from a peripheral ISR process, 
      then the SysTick interrupt must have higher priority (numerically lower)
      than the peripheral interrupt. Otherwise the caller ISR process will be blocked.
      To change the SysTick interrupt priority you have to use HAL_NVIC_SetPriority() function.
      
@note The application needs to ensure that the SysTick time base is always set to
      1 millisecond to have correct HAL operation.

@par Keywords

Demonstrations,

@par Hardware and Software environment

  - This demonstration runs on STM32G081B-EVAL mother board (MB1350 rev B)
    with Legacy daughter board (MB1351 rev A) or USBPD daughter board (MB1352 rev C).

  - A SDSC microSD card (capacity up to 4GB), must contain all the resources files
    available under the FW package Binary/SD_card folder.
    

@par How to use it ? 

In order to make the program work, you must do the following :
 - Open your preferred toolchain 
 - Rebuild all files and load your image into target memory
 - Run the example


 */
