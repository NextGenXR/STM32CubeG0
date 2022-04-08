/**
  @page USB-PD_Consumer_1port USBPD Consumer example
 
  @verbatim
  ******************************************************************************
  * @file    USB-PD/USB-PD_Consumer_1port/readme.txt
  * @author  MCD Application Team
  * @brief   Description of the consumer example.
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

@par Application Description

How to create a simple type C Consumer.

This application initialize the type C port 1 in sink mode with only one PDO at 5V.

Connect UCPD cube Monitor on the VCP associated to our board (only available if USB cable is connected)
The UCPD Cube Monitor will be used to trace all the messages exchange between the ports partner.  
  
@note Care must be taken when using HAL_Delay(), this function provides accurate
      delay (in milliseconds) based on variable incremented in HAL time base ISR.
      This implies that if HAL_Delay() is called from a peripheral ISR process, then
      the HAL time base interrupt must have higher priority (numerically lower) than
      the peripheral interrupt. Otherwise the caller ISR process will be blocked.
      To change the HAL time base interrupt priority you have to use HAL_NVIC_SetPriority()
      function.
 
@note The application needs to ensure that the HAL time base is always set to 1 millisecond
      to have correct HAL operation.

@note The FreeRTOS heap size configTOTAL_HEAP_SIZE defined in FreeRTOSConfig.h is set accordingly to the 
      OS resources memory requirements of the application with +10% margin and rounded to the upper Kbyte boundary.

For more details about FreeRTOS implementation on STM32Cube, please refer to UM1722 "Developing Applications 
on STM32Cube with RTOS".

@par Keywords

USB_PD_Lib, UCPD, Type C, USBPD, FreeRTOS

@par Directory contents
    - USB-PD/USB-PD_Consumer_1port/Src/main.c                       Main program file
    - USB-PD/USB-PD_Consumer_1port/Src/app_FreeRTOS.c               Code for freertos applications file 
    - USB-PD/USB-PD_Consumer_1port/Src/stm32g0xx_hal_msp.c          MSP Initialization file 
    - USB-PD/USB-PD_Consumer_1port/Src/stm32g0xx_it.c               Interrupt handlers file
    - USB-PD/USB-PD_Consumer_1port/Src/system_stm32g0xx.c           STM32G0xx system clock configuration file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd.c                      Ucpd init file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_dpm_core.c             device policy manager core file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_dpm_users.c            device policy manager users file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_pwr_if.c               power if management file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_pwr_user.c             power management file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_vdm_users.c            user vendor define message management file
    - USB-PD/USB-PD_Consumer_1port/Inc/FreeRTOSConfig.h             FreeRTOS Configuration file
    - USB-PD/USB-PD_Consumer_1port/Inc/main.h                       Main program header file
    - USB-PD/USB-PD_Consumer_1port/Inc/stm32_assert.h               assert program header file
    - USB-PD/USB-PD_Consumer_1port/Inc/stm32g0xx_hal_conf.h         HAL Library Configuration file
    - USB-PD/USB-PD_Consumer_1port/Inc/stm32g0xx_it.h               Interrupt handlers header file
    - USB-PD/USB-PD_Consumer_1port/Inc/main.h                       Main program header file
    - USB-PD/USB-PD_Consumer_1port/Inc/main.h                       Main program header file
    - USB-PD/USB-PD_Consumer_1port/Inc/tracer_emb_conf.h            setting file for UCPD tracer 
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd.h                      header of Ucpd init file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_devices_conf.h         UCPD device configuration file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_dpm_conf.h             UCPD stack configuration file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_dpm_core.h             device policy manager core header file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_dpm_users.h            device policy manager users header file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_pwr_if.h               power if management header file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_pdo_defs.h             pdo definition header file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_pwr_user.h             power management header file
    - USB-PD/USB-PD_Consumer_1port/Src/usbpd_vdm_users.h            vendor define message management header file


@par Hardware and Software environment

  - This application runs on STM32G081Bx devices.
    
  - This application has been tested with STM32G081B-EVAL board.
    

@par How to use it ?

In order to make the program work, you must do the following:
 - As UCPD Monitor is using a dedicated flash area for storing USPBD port capabilities, please make sure to erase full flash content before starting. (With STM32CubeProgrammer for example)
 - Open your preferred toolchain 
 - Rebuild all files and load your image into target memory
 - Run the example
 - Run CubeMx Monitor and open trace tools
 - Connect a type C source device on the Type-C connector 1
  

 */
