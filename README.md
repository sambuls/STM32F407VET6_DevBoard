# STM32F407VET6_DevBoard
A STM32F407VET6 Industrial Development Board from Alibaba

<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/51135204-c445-4b2e-9b0e-9131603c9c60" width="200">



## Schematics
On some of the AliExpress/Alibaba seller pages, the product description of the board shows a very low resolution, unusable schematic.
After contacting all the sellers, only one of them was able to provide me with the schematics in PDF format.
This file is included in this repository.

## Power from JLINK interface

The development board comes with a USB to barrel jack power connector. When connected, this cable can provide power to the board. As an alternative, the micro-USB connector is also able to provide power when jumper J5 is placed.
While the JLINK ‘standard’ interface is defined as capable to provide power to connected devices, the power(voltage) line on this development board is left floating (not connected). When connecting ping 19 of the JTAG interface to jumper 5, a J-Link programmer can be used to power and program the development board without the need for additional (USB)power cables.

<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/979fc7d8-5c55-4197-83fb-cddc7ce6b8dc" width="200">

By default, the J-Link programmer does not provide any power to the board. To enable this feature, one can start a GDB server session with the -powertarget option.
For example:

```
C:\ST\STM32CubeIDE_1.13.1\STM32CubeIDE\plugins\com.st.stm32cube.ide.mcu.externaltools.jlink.win32_2.2.0.202305091550\tools\bin\JLinkGDBServerCL.exe -powertarget 10 -port 2331 -s -device STM32F407VE -endian little -speed 4000 -if swd -vd
```

Note that the argument of the -powertarget option is the time the GDB server session will wait for the voltage level to become stabel.
After this command, the JLink will remain the voltage level after a GDB server shutdown. Keeping the voltage level enables the CubeIDE debugger 
to create a new GDB server session. 


## From Fake to Real

The development board is advertised as 'Industrial Control STM32F407VET6 Development Board RS485 Dual CAN Ethernet Networking STM32' which suggestively indicates that the controller is of the type STM32F407VET6 from the respected company ST.
Unfortunately, first initial test with a Segger JLink debugger/programmer showed that the chip did not respond with official ST device ID’s.
After reading several AliExpress/Alibaba product reviews and additional sanity checks I concluded that this specific development board/chip is very likely to be a counterfeit product.
Since the chip does not respond with official ID’s, the tools of ST will abort any attempt to program this chip. To fix this issue, the counterfeit chip is replaced with an official STM32F407VET6 chip from ST.
After removing the counterfeit chip and soldering the genuine one, the ST tools worked as expected and a first ‘hello world’ (blinky) program was successfully downloaded and executed.

<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/e59d9ec1-b42c-4076-9878-3a10bcc6a687" width="200">
<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/a0976636-ae28-4b34-bd82-ff91e7c9f746" width="200">
<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/50c2cca8-b306-4849-a320-658596c5a122" width="200">
<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/15d9dc3b-917b-4e15-853a-f29a0c2649e4" width="200">
<img src="https://github.com/sambuls/STM32F407VET6_DevBoard/assets/10206545/d7e22228-bdcd-4e6d-b827-37b5bf2147e6" width="200">
