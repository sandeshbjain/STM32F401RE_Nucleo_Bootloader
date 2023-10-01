# STM32F401RE_Nucleo_Bootloader
The repo contains two folders - Application and Bootloader. 
The bootloader folder contains the bootloader firmware flash which runs from 0x08000000( or 0x000000000 - memory aliasing) and the application code runs from the location ox08040000 in the memory. The final binary files can be of both binaries can be flashed using ST link flash utility. 

In the application code the reset handler is set to start from address by modifying the linker script:STM32F401RETX_FLASH.ld  

FLASH    (rx)    : ORIGIN = 0x8040000,   LENGTH = 150K 
![image](https://github.com/sandeshbjain/STM32F401RE_Nucleo_Bootloader/assets/31760278/ab9c1936-adb3-4179-b512-a11c4113e9b6)

The microcontroller has 512 kB of flash, by starting the application code from 0x8040000, the bootloader get 256kB of memory space (out of which 150kB is usable as per the above image)

Similarly, the bootloader code which begins at 0x8000000 has 64kB of flash:
![image](https://github.com/sandeshbjain/STM32F401RE_Nucleo_Bootloader/assets/31760278/b9acf004-c7a7-474f-826d-c742dd03076a)

Seperate binaries for both Application and Bootloader code is then generated and flashed using STM32 ST-LINK Flash utility. 

- When the microcontroller exceuted bootloader code - LED in the nucleo board turns ON and remains in ON state. 
- Once the the microcontroller starts exceuting the Applicaiton code - the LED starts blinking every 100ms. 

Improvements:
1. Add over-the-air firmware update functionality - In progress
    
