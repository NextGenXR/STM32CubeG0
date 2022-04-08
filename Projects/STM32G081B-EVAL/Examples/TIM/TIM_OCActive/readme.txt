/**
  @page TIM_OCActive TIM_OCActive example
  
  @verbatim
  ******************************************************************************
  * @file    TIM/TIM_OCActive/readme.txt 
  * @author  MCD Application Team
  * @brief   This example shows how to configure the Timer to generate four 
  *          delayed signals.
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

@par Example Description 

Configuration of the TIM peripheral in Output Compare Active mode 
(when the counter matches the capture/compare register, the corresponding output 
pin is set to its active state).

  The TIM1 frequency is set to SystemCoreClock, and the objective is
  to get TIM1 counter clock at 10 kHz so the Prescaler is computed as following:
     - Prescaler = (TIM1CLK /TIM1 counter clock) - 1
   
  SystemCoreClock is set to 56 MHz for STM32G0xx Devices.

  The TIM1 CCR1 register value is equal to 10000:
  TIM1_CH1 delay = CCR1_Val/TIM1 counter clock  = 1s
  so the TIM1 Channel 1 generates a signal with a delay equal to 1s.

  The TIM1 CCR2 register value is equal to 5000:
  TIM1_CH2 delay = CCR2_Val/TIM1 counter clock = 500 ms
  so the TIM1 Channel 2 generates a signal with a delay equal to 500 ms.

  The TIM1 CCR3 register value is equal to 2500:
  TIM1_CH3 delay = CCR3_Val/TIM1 counter clock = 250 ms
  so the TIM1 Channel 3 generates a signal with a delay equal to 250 ms.

  The TIM1 CCR4 register value is equal to 1250:
  TIM1_CH4 delay = CCR4_Val/TIM1 counter clock = 125 ms
  so the TIM1 Channel 4 generates a signal with a delay equal to 125 ms.

  The delay correspond to the time difference between PD5 falling edge and
  TIM1_CHx signal rising edges.
  STM32 board LED can be used to monitor the example status:
  - LED1 turns ON if example is OK.
  - LED3 toggles slowly in case of error.

@note Delay values mentioned above are theoretical (obtained when the system clock frequency 
      is exactly 56 MHz). Since the generated system clock frequency may vary from one board to another observed
      delay might be slightly different.
	  
@note Care must be taken when using HAL_Delay(), this function provides accurate delay (in milliseconds)
      based on variable incremented in SysTick ISR. This implies that if HAL_Delay() is called from
      a peripheral ISR process, then the SysTick interrupt must have higher priority (numerically lower)
      than the peripheral interrupt. Otherwise the caller ISR process will be blocked.
      To change the SysTick interrupt priority you have to use HAL_NVIC_SetPriority() function.
      
@note This example needs to ensure that the SysTick time base is always set to 1 millisecond
      to have correct HAL operation.

@par Keywords

Timer, Output, Compare, Active, Signals, 

@par Directory contents

  - TIM/TIM_OCActive/Inc/stm32g0xx_hal_conf.h    HAL configuration file
  - TIM/TIM_OCActive/Inc/stm32g0xx_it.h          Interrupt handlers header file
  - TIM/TIM_OCActive/Inc/main.h                  Header for main.c module  
  - TIM/TIM_OCActive/Src/stm32g0xx_it.c          Interrupt handlers
  - TIM/TIM_OCActive/Src/main.c                  Main program
  - TIM/TIM_OCActive/Src/stm32g0xx_hal_msp.c     HAL MSP file
  - TIM/TIM_OCActive/Src/system_stm32g0xx.c      STM32G0xx system source file


@par Hardware and Software environment

  - This example runs on STM32G081RBTx devices.
    
  - This example has been tested with STM32G081B-EVAL 
    board and can be easily tailored to any other supported device 
    and development board.      

  - STM32G081B-EVAL Set-up
   Connect the following pins to an oscilloscope to monitor the different waveforms:
      - Use LED1 connected to PD5 (Reference) (pin 9 in CN9 connector)
      - PA8: (TIM1_CH1) (pin 1 in CN5 connector)
      - PA9: (TIM1_CH2) (pin 3 in CN5 connector)
      - PA10: (TIM1_CH3) (pin 4 in CN5 connector)
      - PC11: (TIM1_CH4) (pin 16 in CN9 connector)
   Please make sure that the Jumper JP7 is open (connected to PC11)
@par How to use it ? 

In order to make the program work, you must do the following :
 - Open your preferred toolchain
 - Rebuild all files and load your image into target memory
 - Run the example

You should see these waveforms on oscilloscope :

 CH1                                                            ________________
 _______________________________________________________________|
           <---------------------- 1sec------------------------->
           
 CH2                                   __________________________________________
 ______________________________________|
           <------------500ms--------->
 
 CH3                        _____________________________________________________
 ___________________________|
           <----250ms------->
 
 CH4                  ____________________________________________________________
 _____________________|
           <--125ms--->

 LED       ______________________________________________________________________
 __________|


 */
