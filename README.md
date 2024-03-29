# VSD_workshop

# Day 1: Sky130 Inception of open source EDA, OpenLANE and SKY130 PDK


![arduino board](https://github.com/SamAI20/VSD_workshop/assets/165182988/ed5a5bef-5ab3-4a5c-9d07-8c0a26153942)

Considering the example of this ARDUINO Leonardo, we notice that the core of this device lies in the chip(circled). The core drives the whole system for various functionality and operations. When we further try to magnify the chip, we obtain the following block diagram of the chip:


![board diagram](https://github.com/SamAI20/VSD_workshop/assets/165182988/d6ed9e59-9aef-4f46-b196-bada93f36724)

The above close up image of this chip (QFN-48). In the industry, the term "chip" is replaced by "package". Inside a package, the  main chip lies in the centre of the package. This main chip is connected to other pins and other components by using the wire-bonds (as seen below):


![open up of chip](https://github.com/SamAI20/VSD_workshop/assets/165182988/a030e76c-e5eb-40ba-8b1f-4bfb1deef68c)

To send and receive signals from inside and outside the package, "pads" are used. Inside the "CORE" area, logic circuits and digital logic components are placed. Consider the  example of the RISC-V soc, 

![RISC V sample chip](https://github.com/SamAI20/VSD_workshop/assets/165182988/4945cc36-be9e-4297-bef6-e3ad3294ad0a)

This package consists of various components :
SRAM, ADC,DAC,PLL, SPI.
These  are collectively the "Foundary IPs"
Foundary is nothing but the set of machines which the SOC/PD/VLSI engineers continously communicate with in order to realise the compenent. IP require some amount of intelligence to make some automated blocks. Design blocks are also macros that consist of pure digital logic.

# INTRODUCTION TO RISC-V


![Screenshot (1)](https://github.com/SamAI20/VSD_workshop/assets/165182988/0e22ac5c-1020-4046-a7af-5f5d3d8fb6f3)


The implementation of RISC-V architecture can be undestood in the following flow. First a C program is written for the functionality which is then passed on to the OS. The Operating System (OS) then converts the C code using a compiler. This then gives us the executable file which is then converted to binary. The OS mainly handles all the input/output operation, allocation of memory. The output of the OS is combination of various functions of C++ or JAVA. This is then sent to the compiler which then converts it to instructions to the respective hardware application or supported version ( which is an .exe file). This is then given to the assembler which then converts it to binary. The instruction set is nothing but the abstract interface or architecture of computer. The HDL ( Hardware Descriptive Language) comes in between the assembler and the hardware. The HDL used is synthesized and then the netlist is physically implemented on the hardware.

![Screenshot (4)](https://github.com/SamAI20/VSD_workshop/assets/165182988/87c4b597-fcf9-4991-b3bf-32cedb14e00f)




