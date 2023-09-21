# STM32F401RE_Nucleo_Bootloader
The repo contains two folders - Application and Bootloader. The bootloader folder contains the bootloader firmware flash which runs from 0x08000000( or 0x000000000 - memory aliasing) and the application code runs from the location ox08040000 in the memory. The final binary files can be of both binaries can be flashed using ST link flash utility. 
