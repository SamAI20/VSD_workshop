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


# OPENLANE FLOW

In this lab, we first proceed with invoking the OPENLANE interactive mode by invoking commands in the terminal as seen below:

![openlane](https://github.com/SamAI20/VSD_workshop/assets/165182988/d7a511f0-4ac9-4388-94d5-6c67b274b40b)

Now that openlane is up and running, we need to setup our preparations and design path. The path is Desktop/work/tools/openlane_working_directory/openlane/ and then type the commmands for synthesis i.e "run synthesis" after entering interactive mode. It takes around 5 min to completely finish the synthesis as seen below:

![synthesis](https://github.com/SamAI20/VSD_workshop/assets/165182988/fba6793c-dd78-4d1b-bbac-8669dc018a6f)

One of the main aim is to calculate flop ratio i.r the number of d flip flops in the designs. This is done by taking the no of D flip-flops and dividing it by the total cells.
The total number of D flip flops is 1613 

![no of d flip flops](https://github.com/SamAI20/VSD_workshop/assets/165182988/6098b74b-8720-4063-b995-657305675beb)


Similarly the total number of cells is 14876



![no of cells](https://github.com/SamAI20/VSD_workshop/assets/165182988/709f9251-a3ce-44d0-a71e-d50908c1ac87)


So now we can calculate the flop ratio which is  (1613)/(14876) = 0.1084 which is percentage is  10.84%. Therefore the flop ratio is 10.84%

Finally the synthesized netlist is obtained and verification of each wire mapping is done as seen below:

![synthesized netlist](https://github.com/SamAI20/VSD_workshop/assets/165182988/0c8a10ea-f947-4a87-8f63-5dbe738fed2b)





# Day 2: Good Floorplan VS Bad Floorplan and Introduction to Library Cells


In Day 2, basics of floorplan along with how to procced with a good plan and also how to avoid floorplan was taught. In the labs sessions, the floorplan can be executed using the run_floorplan command, however before we proceed with floorplan, we need to check the configuration of default switches as seen below:


![floor plan default switches](https://github.com/SamAI20/VSD_workshop/assets/165182988/bad6c002-ece0-4f88-b7bb-7bdf8c9d583a)


After looking at the default configurations of switches, it is now time to execute the command "run_floorplan" and begin floorplan.


![floorplan executed](https://github.com/SamAI20/VSD_workshop/assets/165182988/0d33514f-84d2-4a2e-8b12-81b960a9af33)


Now that floorplan is completed, we an now proceed with viewing the dimensions of the chip in order to calculate the area of the chip after floorplan. In the conversion, 1 micron is equal to 1000 database units. 


![results of floorplan and area executed](https://github.com/SamAI20/VSD_workshop/assets/165182988/5c3b6448-33f7-4417-9754-615e5ddc4a7a)

From the new values obtained, we can now calculate the area of the chip. 
But first we need to convert the dimensions from database units to microns. So the new dimensions in microns are: 660.685 microns and 671.405 microns respectively.
Now the area of the chip becomes: 660.685 x 671.405 microns which is 443,587.2124 microns.
Therefore the area of the chip after floorplan is 443,587.2124 microns.

After calculating the area of the chip, we can now see the GUI layout of the post Floorplan using Magic tool. The tool can be invoked using the command magic -T.
The subsequent layout is shown below:

![floorplan gui](https://github.com/SamAI20/VSD_workshop/assets/165182988/1dd8d1e5-0f57-47ed-942f-0651880d8fc2)

The above shows the GUI Layout of the chip after performing floorplan.
The next step in the design flow after floorplan is placement. Placement is done using the command run_placement. This procedure is shown below:



![placement done](https://github.com/SamAI20/VSD_workshop/assets/165182988/91bd38c1-8f16-49d9-90ed-5216599ae1f0)

Post placement we get a detailed layout where all the components are placed with respect to the technology library cells. This can be seen in detail from the below image:


![post placement cells](https://github.com/SamAI20/VSD_workshop/assets/165182988/be5a4997-6c20-43ab-bd4e-f5a9b6354b59)

This completes the floorplan and placement flow in the design flow.



# DAY 3 : Design Library Cell Using Magic Layout and Gitclone vsdstdcelldesign

In day 3 labs, the first task was given to make changes to the I/o settings using IO placer tool. IO Placer is an open source tool to place or change any input settings. In previous floorplan, all the components are placed symmetrically, however this can be changed using the set command in the IO placer as shown below:

![changing io mode setting](https://github.com/SamAI20/VSD_workshop/assets/165182988/cf6c979a-c4a9-4db6-9280-d265456f9bf5)

After these changes the IO placement, the run_floorplan command is given once again to change the arrangement of the pins which is seen below:

![unsymmetrically placed](https://github.com/SamAI20/VSD_workshop/assets/165182988/164cea27-cfd2-47ec-8500-87ebe47c81e4)


After this, we clone the the vsdstdcells from github to take the sky130inv_mag in order to see the inverter layout in magic tool. The repository is shown below:

![git-clone](https://github.com/SamAI20/VSD_workshop/assets/165182988/3589345d-2d77-4a88-87d1-3a604b2ef047)

After pasting the clone link via url, we see the following files in the terminal:

![after cloning](https://github.com/SamAI20/VSD_workshop/assets/165182988/7b727d54-f181-4951-85e9-fababcc1f23b)

Now we can see the layout of the inverter after pasting the sky130A.tech file from the magic folder to the new cloned folder i.e vsdstdcell. After invoking the magic tool, we obtain the layout of the inverter as shown below:

![Screenshot 2024-06-04 105231](https://github.com/SamAI20/VSD_workshop/assets/165182988/f32e9f27-354c-4ca9-8a56-f47e53838cf9)
 
 The above layout is now extracted from magic to a spice file as shown below :

 ![extracting](https://github.com/SamAI20/VSD_workshop/assets/165182988/7dd4fabe-6ad0-4a22-9e94-c17ccbf8f3f7)

 Now we have successfully obtained a spice file. The contents of the spice file are shown below:

![spice file created](https://github.com/SamAI20/VSD_workshop/assets/165182988/633adb6e-d511-4d9f-a9f0-436ebeead052)

 




















