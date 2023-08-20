
# VLSI Physical Design for ASICs
The objective of VLSI physical design for ASICsis to transform a digital circuit's logical representation into a physical layout that meets various performance, power, area, and manufacturability requirements.
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
2. 
![image](https://github.com/ShashidharReddy01/pes_asic_class/assets/142148810/b1658f3c-375e-4b42-b489-82b5d3a0df30)

4. **Base Integer Instructions:** The term "base integer instructions" refers to the fundamental set of instructions that form the foundation for performing basic arithmetic, logical, and data movement operations.
6. **Multiply Extension Intructions:** The RISC-V architecture includes a set of multiply and multiply-accumulate (MAC) extension instructions that enhance the instruction set to perform efficient multiplication and multiplication-accumulate operations.
7. **Single and Double Precision Floating Point Extension:** The RISC-V architecture includes floating-point extensions that provide support for both single-precision (32-bit) and double-precision (64-bit) floating-point arithmetic operations. These extensions are often referred to as the "F" and "D" extensions, respectively. Floating-point arithmetic is essential for handling real numbers with fractional parts and for performing accurate calculations involving decimal values.
8. **Application Binary Interface:** ABI stands for "Application Binary Interface." It is a set of rules and conventions that govern how software components interact with each other at the binary level. The ABI defines various aspects of program execution, including how function calls are made, how parameters are passed and returned, how memory is allocated and managed, and more.
9. **Memory Allocation and Stack Pointer** 
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





  






