# Physical-Design-of-Approximate-Multiplier
An OpenROAD project

## Introduction to OpenROAD project
OpenROAD is an open-source EDA Tool capable of running complete RTL to GDSII implementation. It uses all open-source tools which are available for various steps in physical design flow, such as synthesis, placement, CTS, routing and STA. It is capable of running large-scale designs and supports various PDK's including gf12 and intel16. 

## Installing OpenROAD tools

The detailed guide for installing OpenROAD-flow-scripts can be found [here](https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts/blob/master/docs/user/BuildLocally.md) . 

It is advised to have UBUNTU 22.04 OS, or virtual machine of the same.

## Using the automated flow to run user-specific design

The steps to run the user-project are as follows :

1. In the OpenROAD-flow-scripts, run following command 'source ./env.sh'
2. Navigate to 'flow' folder inside the OpenROAD-flow-scripts.
3. Create a new folder for source files, named after your design in '/designs/src' .
4. Copy all the verilog files to the '/designs/src/design_nickname' .
5. Create a new folder again in '/designs/platform_name' , named after your design.
6. Create the 'confik.mk' and 'constraint.sdc' in the above created folder.
7. Edit the required variables, like top module name, clock name and platform. 
8. Navigate back to flow folder.
9. Edit the Makefile, and add the DESIGN_CONFIG for new design, save and close.
10. Run
    '
    make
    '
11. After command executes, run
    '
    make gui_final
    '
    which will open the GUI.

## Example project - Approximate Multiplier.

1. Follow first two steps from above section. 
2. Create the folder named 'apxmul, in /designs/src/ .
3. Copy the above file, new_mul.v into the folder.
4. Create the folder named 'apxmul', in /designs/asap7/ .
5. Copy the files, 'config.mk' and 'constraint.sdc' into the above created folder.
6. Navigate back to flow directory, and add the following command
   '
   make DESIGN_CONFIG=./designs/asap7/apxmul/config.mk
   '
7. Finally run
   '
   make DESIGN_CONFIG=./designs/asap7/apxmul/config.mk gui_final
   '

## Common Variables used
The list of commonly used flow variables are as follow:
1. DESIGN_NAME - Name of the top module of project
2. DESIGN_NICKNAME - Name of the directories where files are located
3. PLATFORM - PDK, either ASAP7 or sky130hd
4. CORE_UTILIZATION - Minimum core utilization out of 100

## Output of the flow
The output of the run will look like this

<img width="960" alt="Screenshot 2024-01-11 192307" src="https://github.com/xchinmaydh/Physical-Design-of-Approximate-Multiplier/assets/153248450/a4bad3bd-ad68-4ac0-b40e-4bbdeedb4eb0">



