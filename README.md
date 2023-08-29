
# VLSI Physical Design for ASICs
The objective of VLSI physical design for ASICsis to transform a digital circuit's logical representation into a physical layout that meets various performance, power, area, and manufacturability requirements.
+ [Installation of Virtual Machine and RISC-V GCC compiler](url)

## Installation of Virtual Machine and RISC-V GCC compiler

**Requirements:**
+ OS: Ubuntu 20 
+ Memory: 200 GB
+ RAM: 6 GB

- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) ← Click on the link to head to the downloads page. Download and install the windows hosts version.
    - Open the VirtualBox application and click on “New”
    - Give a name to the VM and choose the folder where your VM files will reside.
    - For iso file you need to install the iso image from these sites.
        - For Ubuntu: http://ubuntu-releases.mirror.net.in/ubuntu/releases/jammy/ubuntu-22.04.3-desktop-amd64.iso (for Intel and AMD users)
        - Please refer to the ubuntu website for MacOS (M1, M2) users.
    - Download any one of the two iso file and include it in the iso option.
    - For type, choose “Linux” and for version either choose “Ubuntu 22.04 (64-bit)”.
    - Rest is set to default. Please DM either one of us if you’re facing issues at this point.
    - Click on “Next” and for base memory set it to “2048MB” if you have less than 8gb, if you have more, set it to “4096MB”.
    - For the Processors, leave it in “1” unless you have 4+ cores. If you have more than 4 cores, you can set it to “2”.
    - Click on “Next” and in the “Create a virtual hard disk now” and set it to 50GB or 100GB. Please make sure you have enough space for this, but this space that you allocate is dynamic so don’t worry, it will only take up upto 100GB when required.
    - Click on “Next” and “Finish”.
    - If you’re having issues connecting to the network inside the VM, click on the “Devices” option on the menu bar above on the VirtualBox application. In that menu, choose “Network” and enable “Connect Network Adapter”. If it still does not work after enabling, please restart the VM and see if that works.
    
    ---
    
    - For the riscv-gcc compiler, head over to this link https://www.embecosm.com/resources/tool-chain-downloads/ and install the tar.gz file based on your Linux version. **************Make sure you do this on the Virtual Machine!**************
        - For Ubuntu VMs
          -v22.04

# ***Commands to download RISC-V toolchain on your ubuntu***

***Install Git and Vim with automatic "yes" response to prompts***

`sudo apt-get install git vim -y`

***Install various development tools and libraries***

`sudo apt-get install autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev git libexpat1-dev gtkwave -y`

***Navigate to the home directory***

`cd`

***Store the current directory path***

`pwd=$PWD`

***Create a directory for the RISC-V toolchain***

`mkdir riscv_toolchain`

***Enter the RISC-V toolchain directory***

`cd riscv_toolchain`

***Download and extract the RISC-V GCC toolchain***

`wget "https://static.dev.sifive.com/dev-tools/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14.tar.gz"
tar -xvzf riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14.tar.gz `

***Add the RISC-V toolchain's bin directory to the PATH***

`export PATH=$pwd/riscv_toolchain/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14/bin:$PATH`

***Install device-tree-compiler***

`sudo apt-get install device-tree-compiler -y`

***Clone the RISC-V ISA simulator repository***

`git clone https://github.com/riscv/riscv-isa-sim.git`

***Enter the RISC-V ISA simulator directory***

`cd riscv-isa-sim/`

***Create a build directory***

`mkdir build`

***Enter the build directory***

`cd build`

***Configure the RISC-V ISA simulator build***

`../configure --prefix=$pwd/riscv_toolchain/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14`

***Build the RISC-V ISA simulator***

`make`

***Install the RISC-V ISA simulator***

`sudo make install`

***Navigate back to the RISC-V toolchain directory***

`cd $pwd/riscv_toolchain`

***Clone the RISC-V proxy kernel repository***

`git clone https://github.com/riscv/riscv-pk.git`

***Enter the RISC-V proxy kernel directory***

`cd riscv-pk/`

***Create a build directory***

`mkdir build`

***Enter the build directory***

`cd build`

***Configure the RISC-V proxy kernel build***

`../configure --prefix=$pwd/riscv_toolchain/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14 --host=riscv64-unknown-elf
`
***Build the RISC-V proxy kernel***

`make`
***
Install the RISC-V proxy kernel***

`sudo make install`

***Add the RISC-V proxy kernel's bin directory to the PATH***

`export PATH=$pwd/riscv_toolchain/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14/riscv64-unknown-elf/bin:$PATH`

***Navigate back to the RISC-V toolchain directory***

`cd $pwd/riscv_toolchain`

***Clone the Icarus Verilog repository***

`git clone https://github.com/steveicarus/iverilog.git`

***Enter the Icarus Verilog directory***

`cd iverilog/`

***Check out the v10-branch of Icarus Verilog***

`git checkout --track -b v10-branch origin/v10-branch`

***Update the repository***

`git pull`

***Make autoconf.sh executable***

`chmod 777 autoconf.sh`

***Run autoconf.sh***

`./autoconf.sh`

***Configure Icarus Verilog***

`./configure`

***Build Icarus Verilog***

`make`

***Install Icarus Verilog***

`sudo make install  `

**Update Your Path:**

**After installing, you'll want to add the toolchain binaries to your PATH:**

`echo 'export PATH=$PATH:/opt/riscv/bin' >> ~/.bashrc
source ~/.bashrc`

# updated tools installation for day 3 and day 4
`git clone https://github.com/YosysHQ/yosys.git `

`cd yosys`

`sudo apt install make`

`sudo apt-get update`

`sudo apt-get install build-essential clang bison flex  libreadline-dev gawk tcl-dev libffi-dev git  graphviz xdot pkg-config python3 libboost-system-dev libboost-python-dev libboost-filesystem-dev zlib1g-dev`

*Comment the export path in bashrc for the code given below to work*

`make config-gcc`

`make -j 4`

`sudo make install`

`sudo apt install gtkwave`



# TABLE OF CONTENTS
## DAY 1 
**Introduction to RISCV ISA and GNU Compiler Toolchain**
+ Introduction to Basic Keywords
+ Labwork for RISCV Toolchain
+ Integer Number Representation  
## DAY 2 
**Introduction to ABI and Basic Verification Flow**
+ Application Binary Interface
+ Labwork using ABI Function Calls
# Introduction
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/a9f04dfd-9ff4-48b4-b6f2-47f8845763ad)
**Basic Definition**
+ An Instruction Set Architecture (ISA) is part of the abstract model of a computer that defines how the CPU is controlled by the software. The ISA acts as an interface between the hardware and the software, specifying both what the processor is capable of doing as well as how it gets done.
+ RISC-V is an open-source instruction set architecture used to develop custom processors for a variety of applications, from embedded designs to supercomputers.
# From Apps to Hardware
1. **Applications:** Applications, also known as software applications or simply apps, are programs or software designed to perform specific tasks or functions for end-users. Examples include word processors, web browsers, and games.
2. **System Software:** System software refers to a collection of programs and utilities that manage and control a computer system's hardware and provide services to other software applications. It includes the operating system, device drivers, and system utilities.
3. **Compiler:** A compiler is a software tool that translates high-level programming code (source code) written by humans into machine code or intermediate code that can be executed directly by a computer's hardware or by a virtual machine.
4. **Assembler:** An assembler is a program or tool that translates assembly language code, a low-level human-readable representation of machine code instructions, into machine code that can be executed by a computer's CPU.
5. **RTL (Register-Transfer Level):** RTL, or Register-Transfer Level, is a level of hardware description language used to model the behavior of digital circuits at a low level of abstraction. It specifies how data moves between registers and how logic operations are performed.
6. **Hardware:** Hardware refers to the physical components of a computer system, including the CPU, memory, storage devices, input/output devices, and other electronic and mechanical components. It is the tangible, physical part of a computer system.
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/1af652e7-16ef-47b9-a749-515db468e778)
# Detail description of course content
1. **Pseudo Instructions** The pseudo instructions are provided by the assembler tools, which convert them into one or more real instructions. The most commonly used pseudo instruction is the LDR. This allows a 32-bit immediate data item to be loaded into a register.
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/b1658f3c-375e-4b42-b489-82b5d3a0df30)

2. **Base Integer Instructions:** The term "base integer instructions" refers to the fundamental set of instructions that form the foundation for performing basic arithmetic, logical, and data movement operations.
3. **Multiply Extension Intructions:** The RISC-V architecture includes a set of multiply and multiply-accumulate (MAC) extension instructions that enhance the instruction set to perform efficient multiplication and multiplication-accumulate operations.
4. **Single and Double Precision Floating Point Extension:** The RISC-V architecture includes floating-point extensions that provide support for both single-precision (32-bit) and double-precision (64-bit) floating-point arithmetic operations. These extensions are often referred to as the "F" and "D" extensions, respectively. Floating-point arithmetic is essential for handling real numbers with fractional parts and for performing accurate calculations involving decimal values.
5. **Application Binary Interface:** ABI stands for "Application Binary Interface." It is a set of rules and conventions that govern how software components interact with each other at the binary level. The ABI defines various aspects of program execution, including how function calls are made, how parameters are passed and returned, how memory is allocated and managed, and more.
6. **Memory Allocation and Stack Pointer** 
- Memory allocation refers to the process of assigning and managing memory segments for various data structures, variables, and objects used by a program. It involves allocating memory space from the system's memory pool and releasing it when it is no longer needed to prevent memory leaks.
- The stack pointer is a register used by a program to keep track of the current position of the program's execution on the call stack.

# Labwork for RISCV toolchain
# #c program 
Writing C program using Leaf editor
**Writing a c program to find sum of integers from 1 to N**
`leafpad sum1ton.c`
+ code
  ![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/10a287e5-fc35-4266-81ab-c5fc1d59b62d)
`gcc leafpad sum1ton.c`
`./a.out`
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/d8e8b254-2cb8-4321-ac3d-23723944dd2a)
## RISCV GCC Compiler and Dissemble

Using the riscv gcc compiler
`riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c`
`spike pk sum1ton.o`
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/9cdddf6c-95c7-4a55-a78c-61697f1d0cd7)

For Assembly Code
`riscv64-unknown-elf-objdump -d sumton.o | less`
type /main to go to the main section
`/main`


For -O1 optimization


![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/af34dd3c-06d0-4d58-8f98-6f019a8bc8c6)

For -OFast optimization


![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/4e15a810-46a6-45a7-b883-d19d655dcf3b)

# Spike Simulation and Debug
`spike -d pk sum1ton.c` is used for debugging.

Contents of the register can be viewed as shown in the image below

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/64944ba9-08b0-4dbd-a86d-9af8255e28f9)

# Integer Number Representation 

## Unsigned Numbers
- Unsigned numbers, also known as non-negative numbers, are numerical values that represent magnitudes without indicating direction or sign.
- Range: 0 to 2^(N) - 1.

## Signed Numbers
- Signed numbers are numerical values that can represent both positive and negative magnitudes, along with zero.
- Range : -(2^(N-1)) to 2^(N-1) - 1.

64 bit Number System For Unsigned Numbers

+ RISC-V doubleword can represent 0 to (2^(64) - 1) unsigned numbers or positive numbers

+ RISC-V doubleword can represent 0 to (2^(63) - 1)positive & (-1) to (-2^63) negative numbers
+ 
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/0c8c40bd-85c6-403b-bda7-2d5f9929acb3)

##Lab
**UnSigned 64-bit Number**
``` c
#include <stdio.h>
#include <math.h>

int main(){
	unsigned long long int max = (unsigned long long int) (pow(2,64) -1);
	unsigned long long int min = (unsigned long long int) (pow(2,64) *(-1));
	printf("lowest number represented by unsigned 64-bit integer is %llu\n",min);
	printf("highest number represented by unsigned 64-bit integer is %llu\n",max);
	return 0;
}
```
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/45f6236a-9d45-495f-b735-1d8b32df82cd)


**Signed 64-bit Number**
``` c
#include <stdio.h>
#include <math.h>

int main(){
	long long int max = (long long int) (pow(2,63) -1);
	long long int min = (long long int) (pow(2,63) *(-1));
	printf("lowest number represented by signed 64-bit integer is %lld\n",min);
	printf("highest number represented by signed 64-bit integer is %lld\n",max);
	return 0;
}
```
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/f3bbdfcd-1a5b-40e9-a004-77773f87fcef)

# Application Binary Interface
## Introduction to ABI
An Application Binary Interface (ABI) is a set of conventions or rules that govern how functions, data structures, and system calls should be organized and accessed in a binary program or library. It defines the low-level interface between different parts of a program or between a program and the operating system. Here are the key points about an ABI:

1. **Binary Compatibility**: ABIs ensure that binary code produced by one compiler or platform can work seamlessly with code produced by another, as long as they adhere to the same ABI.

2. **Function Calling Convention**: ABIs specify how functions are called, including the order and location of arguments and return values, as well as how the call stack is managed during function calls.

3. **Register Usage**: ABIs define which registers are reserved for certain purposes (e.g., argument passing, return values, temporary storage) and how they should be managed during function calls.

4. **Data Layout**: ABIs specify how data structures like structs and arrays are laid out in memory, including rules for alignment and padding.

5. **Exception Handling**: They define how exceptions (such as hardware or software interrupts) are handled, including how control is transferred between user code and exception handlers.

6. **System Calls**: ABIs detail how programs interact with the operating system through system calls, including how arguments are passed and results are retrieved.

7. **Platform Independence**: ABIs help maintain compatibility across different platforms (e.g., different CPU architectures or operating systems) by providing a standardized interface.

8. **Dynamic Linking**: They cover aspects of dynamic linking, such as how shared libraries (DLLs on Windows or shared objects on Unix-based systems) are loaded and linked at runtime.

9. **Versioning**: Some ABIs include mechanisms for versioning so that future changes can be made without breaking compatibility with existing code.

10. **Documentation**: ABIs are typically documented and published, allowing developers to write code that conforms to the ABI's specifications.

11. **Toolchain Support**: Compilers and assemblers are designed to generate code that follows the ABI, ensuring that code produced by different tools can interoperate.

12. **Cross-Platform Development**: ABIs are especially important for cross-platform development, where code needs to run on multiple platforms with potentially different hardware architectures and operating systems.

13. **Security**: ABIs may include security-related aspects, such as buffer overflow protection mechanisms and stack canaries.


## Memmory Allocation for Double Words
64-bit number (or any multi-byte value) can be loaded into memory in little-endian or big-endian. It involves understanding the byte order and arranging the bytes accordingly
1. **Little-Endian:**
In little-endian representation, you store the least significant byte (LSB) at the lowest memory address and the most significant byte (MSB) at the highest memory address.
2. **Big-Endian:**
In big-endian representation, you store the most significant byte (MSB) at the lowest memory address and the least significant byte (LSB) at the highest memory address.

![WhatsApp Image 2023-08-20 at 17 38 47](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/9d25d09f-9f95-4ec7-8844-44f3ddad9254)
## Load, Add and Store Instructions
Load, Add, and Store instructions are fundamental operations in computer architecture and assembly programming. They are often used to manipulate data within a computer's memory and registers.

Example `ld x8, 16(x23)`

In this Example
- `ld` is the load double-word instruction.
- `x8` is the destination register.
- `16(x23)` is the memory address pointed to by register `x5` (base address + offset).

![WhatsApp Image 2023-08-20 at 17 42 56](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/7a5ebb35-92f6-4a27-b40f-e30812cae1c0)

Example `add x8, x24, x8`

In this Example
- `add` is the add instruction.
- `x8` is the destination register.
- `x24` and `x8` are the source registers.

![WhatsApp Image 2023-08-20 at 17 47 25](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/5704ff1b-2008-4154-a835-569651f75e19)

## 32-Registers and their ABI Names
The choice of the number of registers in a processor's architecture, such as the RISC-V RV64 architecture with its 32 general-purpose registers, involves a trade-off between various factors. While modern processors can have more registers but increasing the number of registers could lead to larger instructions, which would take up more memory and potentially slow down instruction fetch and decode.

#### ABI Names
ABI names for registers serve as a standardized way to designate the purpose and usage of specific registers within a software ecosystem. These names play a critical role in maintaining compatibility, optimizing code generation, and facilitating communication between different software components. 

![WhatsApp Image 2023-08-20 at 17 51 23](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/46f38e30-4c21-458f-84cc-2ee2381b8b13)

# LabWork using ABI function calls

![WhatsApp Image 2023-08-20 at 17 54 26](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/a64bce17-042a-4dfa-a788-0b71e8778687)

**C Program**
`custom1to9.c`
  ``` c
  #include <stdio.h>
  
  extern int load(int x, int y);
  
  int main()
  {
    int result = 0;
    int count = 9;
    result = load(0x0, count+1);
    printf("Sum of numbers from 1 to 9 is %d\n", result);
  }
```
**Asseembly File**
`load.s`
``` s
.section .text
.global load
.type load, @function
load:
add a4, a0, zero
add a2, a0, a1
add a3, a0, zero
loop:
add a4, a3, a4
addi a3, a3, 1
blt a3, a2, loop
add a0, a4, zero
ret
```
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/4d109bc3-c119-4835-b32c-1d2a00b6d5e6)

# Introduction to Verilog RTL design and synthesis

## Introduction to iverilog design testbench

RTL Design, which stands for Register Transfer Level design, is a crucial phase in digital circuit design, where the functionality of digital systems is described at a level that specifies how data moves between registers. Let's expand on the key points you've mentioned:

1. **Data Transfer between Registers**: RTL design focuses on defining how data is transferred between registers within a digital circuit. Registers are small memory elements capable of storing binary data. The movement of data between these registers represents the fundamental operations of a digital system.

2. **Hardware Description Language (HDL)**: RTL designs are typically written using Hardware Description Languages like Verilog or VHDL. These languages allow designers to specify the behavior and structure of digital circuits at the register transfer level. HDLs provide a way to describe the desired functionality of the hardware without getting into the specifics of how it will be implemented.

3. **Combinational and Sequential Circuits**: RTL design involves creating descriptions for both combinational and sequential circuits. Combinational circuits are those where the output depends solely on the current input, while sequential circuits have memory elements (like registers) and the output depends on both the current input and the previous state.

4. **Logical and Hardware Operation Modeling**: RTL designs in HDLs enable modeling of logical operations (e.g., AND, OR, NOT) as well as hardware operations (e.g., addition, subtraction) at a level of abstraction that reflects the actual hardware behavior.

5. **Optimization**: RTL design involves optimizing the description to achieve specific goals. These goals might include improving performance, reducing power consumption, or minimizing the area required on a chip. Optimization techniques are applied to the RTL code to make it more efficient.

6. **Synthesizable Code**: One of the most critical aspects of RTL design is that the RTL code must be synthesizable. Synthesis is the process of translating RTL code into a netlist of gates and flip-flops that can be physically implemented on hardware. Synthesis tools, often provided by FPGA or ASIC vendors, take RTL code as input and produce a gate-level representation that can be fabricated into physical hardware.

7. **Hierarchical Design**: In complex digital systems, RTL designs are typically broken down into modules or blocks, each representing a specific function or component of the system. These modules can be designed independently and then integrated to create the complete system.

8. **Testing and Verification**: RTL designs also involve the development of testbenches and verification strategies to ensure that the designed digital circuit behaves correctly under various conditions.

**Simulation**: RTL design is checked for adherence to its design specification using simulation by giving sample inputs. This helps finding and fixing bugs in the RTL design in the early stages of design development. 

**Simulator**: Simulator is the tool used for this process. It looks for changes on input signals to evaluate outputs. No change in output if there is no change in input signals

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/d45720cb-c8ad-4715-b5e8-09578ac146fa)

# Testbench: 
***A test bench in Verilog is an essential component of the verification process for digital designs. It serves as a simulation environment where you can apply stimulus to the RTL (Register Transfer Level) design and verify its functionality. Here, let's expand on the key components and functions of a Verilog test bench:***

1. **Stimulus Generation**: The test bench generates input signals that simulate real-world conditions or user interactions with the designed hardware. These input signals are applied to the RTL design to test its behavior. Stimulus generation can include tasks like creating clock signals, generating test vectors, or mimicking user inputs.

2. **Instantiating the Design**: In the test bench, you instantiate the RTL design under test. This means you include the design's module within the test bench code. The test bench communicates with the design module, providing inputs and monitoring outputs.

3. **Output Checking**: The other critical part of a test bench is output checking. After applying stimulus to the design, the test bench monitors the design's output signals. It compares the expected output, which is determined based on the input stimulus and the expected behavior of the design, with the actual output produced during simulation.

4. **Assertion Checks**: To ensure that the design behaves correctly, assertions are often used in the test bench. Assertions are statements in the test bench code that express expected conditions or properties of the design. If an assertion fails during simulation, it indicates a problem with the design.

5. **Timing Simulation**: The test bench allows for timing simulation, where you can evaluate how the design behaves in terms of delays, setup times, and hold times. This is crucial for ensuring that the design meets its timing requirements.

6. **Functional Coverage**: Test benches can include functional coverage checks to ensure that various aspects of the design's functionality have been thoroughly tested. Coverage metrics track which parts of the design have been exercised during simulation.

7. **Test Cases**: In a comprehensive verification process, multiple test cases are often created within the test bench. Each test case represents a specific scenario or condition that the design must handle correctly. These test cases collectively ensure thorough testing of the design.

8. **Simulation Results Comparison**: After simulation, the test bench compares the actual simulation results with the expected results. If there are discrepancies, it indicates potential issues in the RTL design.

9. **Debugging and Analysis**: When discrepancies or errors are detected, the test bench provides valuable information for debugging. Designers can analyze the simulation waveforms and debug their RTL code accordingly.

10. **Regression Testing**: As the project progresses and the design evolves, it's common to perform regression testing using the test bench. This ensures that changes or updates to the design do not introduce new issues and that existing functionality remains intact.

In summary, a Verilog test bench is a critical tool for verifying the correctness of an RTL design. It generates input stimuli, monitors output responses, checks assertions, performs timing analysis, and helps ensure that the design meets its functional and timing requirements. By thoroughly testing the design with various test cases, designers can have confidence in its reliability and correctness before moving to the synthesis and implementation stages.

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/a220c299-a94c-4fce-9f0f-ed3e5d1131f9)

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/a7e494b5-1cc7-4367-97cf-45614fa313e1)

## **Introduction to yosys synthesizer**

**synthesis**: is a crucial step in the design process for creating digital integrated circuits. It involves transforming a high-level RTL (Register Transfer Level) design, which describes how data moves between registers and the desired functionality, into a gate-level netlist that represents the physical implementation of the design using specific logic gates. Here's an expanded explanation of the synthesis process:

1. **Converting RTL into Logic Gates**: The first step in synthesis is to convert the RTL description, written in a hardware description language like Verilog or VHDL, into a netlist consisting of basic logic gates (e.g., AND, OR, NOT). This process is sometimes referred to as "RTL synthesis." The synthesizer tool analyzes the RTL code and generates an intermediate representation in terms of logic gates.

2. **Technology Mapping**: After obtaining a netlist with basic logic gates, the synthesizer maps these gates to specific technology-dependent gates available in the target technology library. Different semiconductor technologies (e.g., CMOS, FPGA) have their own libraries of standard cells or configurable logic blocks. The synthesizer selects the appropriate gates from this library to match the desired functionality while considering factors like area, power consumption, and speed.

3. **Optimization**: The next critical phase of synthesis is optimization. The synthesizer applies various algorithms and techniques to optimize the mapped netlist. Optimization aims to improve the design in terms of performance, area utilization, and power efficiency while adhering to constraints set by the designer. Common optimization techniques include logic minimization, retiming, and resource sharing.

4. **Constraint Preservation**: Throughout the synthesis process, the synthesizer must ensure that the constraints set by the designer are preserved. These constraints may include timing requirements (e.g., clock frequency, setup and hold times), power consumption limits, or area constraints. The synthesizer makes optimization decisions while respecting these constraints.

5. **Timing Analysis**: Timing analysis is a crucial aspect of synthesis. It evaluates whether the design meets its timing requirements, such as setup and hold times for flip-flops and the maximum clock frequency. If the design doesn't meet these requirements, the synthesizer may need to make adjustments or provide recommendations for meeting them.

6. **Area and Power Analysis**: Synthesis tools also provide estimates of the chip's area utilization and power consumption based on the synthesized netlist. Designers can use this information to assess whether the design meets their area and power targets.

7. **Gate-Level Simulation**: Before proceeding to physical implementation, gate-level simulation is often performed to validate that the synthesized design behaves as expected and meets functional requirements.

8. **Documentation and Reporting**: Synthesis tools generate reports and documentation that include information about the synthesized design, including gate-level representations, critical paths, timing analysis results, and resource utilization.

Synthesis is a pivotal step in the design flow for creating digital chips. It transforms an abstract RTL design into a gate-level netlist that can be physically implemented. During this process, the synthesizer selects technology-dependent gates, optimizes the design for performance and resource utilization, ensures constraint compliance, and provides essential analysis and documentation to guide the subsequent stages of the design process. The choice of synthesis tool and the expertise of the designer significantly influence the quality and efficiency of the final chip implementation.

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/c0cbcee9-0794-4efa-8dc3-62fd4cf74ec6)

***Below are the commands to perform above synthesis.***

+ RTL Design - read_verilog
+ .lib - read_liberty
+ netlist file- write_verilog

- .lib: It is a collection of logical modules like, And, Or, Not etc...It has different flvors of same gate like 2 input AND gate, 3 input AND gate etc... with different performace speed.


![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/06308534-18d0-4c24-b793-2c0db59036b9)

**Verification of Synthesized design**: In order to make sure that there are no errors in the netlist, we'll have to verify the synthesized circuit. The netlist verification flow can be seen in the below image:

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/ce15fea5-9836-404e-b9be-fa1a086bd1ca)

**Need for different flavours of gate**: In order to make a faster circuit, the clock frequency should be high. For that the time period of the clock should be as low as possible. However, in a sequential circuit, clock period depends on three factors so that data is not lost or to be glitch free.

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/def5a0ec-f884-417d-9d24-b3e2d622c827)

+ Tclk > Tcq_a + Tcombi + Tsetup_b
+ Fclk = 1 / Tclk

**Why we need slower cells**:
To ensure there is no HOLD issues at flipflop B we need the cells to work at a slower rate.
Hence we need cells that work fast to meet the required performance and we also need cells that work slow to meet HOLD.

**Faster Cells vs Slower Cells**: 
Load in digital circuit is of **Capacitence**. Faster the charging or dicharging of capacitance, lesser is the celll delay. However, for a quick charge/ discharge of capacitor, we need transistors capable of sourcing more current i.e, we need WIDE TRANSISTORS. 

Wider transistors have lesser delay but consume more area and power. Narrow transistors are other way around. Faster cells come with a cost of area and power.

**Selection of the Cells**: We'll need to guide the Synthesizer to choose the flavour of cells that is optimum for implementation of logic circuit. Keeping in view of previous observations of faster vs slower cells,to avoid hold time violations, larger circuits, sluggish circuits, we offer guidance to synthesizer in the form of **Constraints**.

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/986d04c5-73de-483a-9c7c-cb78d9f55f42)

### Labs on Yosys introduction

Invoking Yosys:
`yosys`
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/48ae79a9-ac5d-476e-8348-9533a78b3e3d)

Snippet below illustrates reading .lib, design and choosing the module to synthesize:
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/3e0de64b-28a8-4e5b-8723-253d2b776dfb)
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/75072a0f-9aaf-4022-8832-cedc3b709bc6)
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/8b58f250-15bf-4959-98bb-05875965729b)

`gvim good_mux.v`
+ `to run this file download sudo apt install vim-gtk3`

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/43ac037a-dd95-4d92-9b39-4af13967102d)

- To synthesize use command `synth -top good_mux`

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/88939bb8-32e3-431b-b268-36735af13927)

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/d46fbc9c-c2d5-4037-9b46-f1d2f6df33fc)

`abc -liberty sky130_fd_sc_hd__tt_025C_1v80.lib`

**abc:** ABC is a tool within Yosys used for technology mapping and optimization. It's often used in the synthesis flow to map a high-level RTL description to a lower-level gate-level representation.

**liberty** This flag indicates that you are providing a Liberty library file as input. A Liberty library file is a file that describes the timing, power, and other characteristics of the cells in a digital standard cell library. These libraries are essential for synthesis tools to perform accurate timing analysis and optimization.

**sky130_fd_sc_hd__tt_025C_1v80.lib:** This is the name of the Liberty library file you are providing to Yosys. The name appears to follow a specific naming convention, indicating it's likely part of the SkyWater 130nm process technology, which is a popular open-source process technology for ASIC (Application-Specific Integrated Circuit) design.

**In summary**, The command is using Yosys with the ABC tool to perform synthesis and optimization operations on a design, and it's using a specific Liberty library file tailored for the SkyWater 130nm process technology. This is a typical step in the process of converting a high-level RTL design into a gate-level representation suitable for further steps in the ASIC design flow, such as place and route.

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/c186e404-bbb7-49a9-8df1-07c43fa90f22)

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/5f6c0770-3c2c-4e88-b12b-c13ad909adcf)

+ From the above picture we can infer that the MUX we have used has
  - 3 Input Signals
  - 1 Output Signal
  - 0 Internal Signal
  - Cells used
    - mux2
  
   
Command `show` gives us the graphical version of the logics we have used as shown in the below picture

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/7a52fcc9-e68a-4642-b7dc-bfd08232035e)

**Netlist code**:
Command to load netlist is  `write_verilog good_mux_netlist.v` and to open it use the command `!gvim good_mux_netlist.v`

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/36b660f1-b629-492b-85d2-de63735efbba)

**Simplified netlist code**: This code consisits of additional switch. To further simplify, we use below command

![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/2cad4a95-5bee-4086-b736-93e2a2e7d8dc)

It has created:
 - instantiation of mux2
 - name to instantiation
 - interal nets


 
 










    













































  






