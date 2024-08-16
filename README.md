# RISC-V Processor Verilog Code

## Overview

This repository contains Verilog code for a 32-bit RISC-V processor implementation. The code includes the processor's main components, instruction decoding, arithmetic operations, and branching logic.

## Features

- **Instruction Fetching**: Handles the fetching of instructions from memory.
- **Instruction Decoding**: Decodes various RISC-V instructions including R-type, I-type, S-type, B-type, U-type, and J-type instructions.
- **Arithmetic Operations**: Supports arithmetic and logical operations such as addition, subtraction, multiplication, bitwise operations, and shifting.
- **Branching**: Implements conditional and unconditional branching.

## Components

### PC Logic
The PC logic is responsible for the program counter (PC). The PC identifies the instruction the CPU will execute next. Most instructions execute sequentially, meaning the default behavior of the PC is to increment to the following instruction each clock cycle. Branch and jump instructions, however, are non-sequential. They specify a target instruction to execute next, and the PC logic must update the PC accordingly.

### Fetch
The instruction memory (IMem) holds the instructions to execute. To read the IMem, or "fetch," we simply pull out the instruction pointed to by the PC.

### Decode Logic
Once an instruction is fetched, it must be interpreted, or decoded. The instruction is broken into fields based on its type. These fields tell us which registers to read, which operation to perform, etc.

### Register File Read
The register file is a small local storage of values the program is actively working with. After decoding the instruction to determine which registers are needed, we read those registers from the register file.

### Arithmetic Logic Unit (ALU)
With the register values in hand, the ALU performs the specified operations such as addition, subtraction, multiplication, and shifting based on the instruction's operation code.

### Register File Write
The result value from the ALU is then written back to the destination register specified in the instruction.

### DMem
The test program executes entirely out of the register file and does not require a data memory (DMem). However, a complete CPU includes a DMem. The DMem is written to by store instructions and read from by load instructions.


![image](https://github.com/user-attachments/assets/584173af-9595-48f9-a86b-3d0c4646ae7b)




