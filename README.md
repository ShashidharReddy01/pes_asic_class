
# VLSI Physical Design for ASICs
The objective of VLSI physical design for ASICsis to transform a digital circuit's logical representation into a physical layout that meets various performance, power, area, and manufacturability requirements.
# ****1. Installation of Virtual Machine and RISC-V GCC compiler****

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

# ***Command to download RISC-V toolchain on your ubuntu***

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



























  






