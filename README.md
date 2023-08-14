# STM32F407VET6_DevBoard
A STM32F407VET6 Industrial Development Board from Alibaba


## Schematics
On some of the AliExpress/Alibaba seller pages, the product description of the board shows a very low resolution, unusable schematic.
After contacting all the sellers, only one of them was able to provide me with the schematics in PDF format.
This file is included in this repository.

## Power from JLINK interface

The development board comes with a USB to barrel jack power connector. When connected, this cable can provide power to the board. As an alternative, the micro-USB connector is also able to provide power when jumper J5 is placed.
While the JLINK ‘standard’ interface is defined as capable to provide power to connected devices, the power(voltage) line on this development board is left floating (not connected). When connecting ping 19 of the JTAG interface to jumper 5, a J-Link programmer can be used to power and program the development board without the need for additional (USB)power cables.
By default, the J-Link programmer does not provide any power to the board. To enable this feature, one can start a GDB server session with the -powertarget option.
For example:

```
C:\ST\STM32CubeIDE_1.13.1\STM32CubeIDE\plugins\com.st.stm32cube.ide.mcu.externaltools.jlink.win32_2.2.0.202305091550\tools\bin\JLinkGDBServerCL.exe -powertarget 10 -port 2331 -s -device STM32F407VE -endian little -speed 4000 -if swd -vd
```

Note that the argument of the -powertarget option is the time the GDB server session will wait for the voltage level to become stable.


## From Fake to Real

<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/e59d9ec1-b42c-4076-9878-3a10bcc6a687" width="200">
<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/a0976636-ae28-4b34-bd82-ff91e7c9f746" width="200">
<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/50c2cca8-b306-4849-a320-658596c5a122" width="200">
<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/15d9dc3b-917b-4e15-853a-f29a0c2649e4" width="200">
<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/d7e22228-bdcd-4e6d-b827-37b5bf2147e6" width="200">
