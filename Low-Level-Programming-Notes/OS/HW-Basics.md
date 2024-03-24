# Processor Basics

Byte ~ Word
Arithmetic Logical Unit
Program Counter ~ PC
Static Random Access Memory ~ SRAM
Process ~ an abstraction provided by the OS

## CPU Basic Operations

- Load: Copy a Byte from Main Memory to Register
- Store: Copy a Byte from Register to Main Memory
- Operate: Copy values from 2 Registers to ALU, store Result back in a Register
- Jump: Extract a Byte from Instruction and copy it to PC

## Caches

- L0: Registers are the Fastest Memory Access Devices
- L1: Stores tens of thousands of Bytes, Almost as fast as Registers
- L2: Stores Hundreds of Thousands of Bytes, 5 Times slower than L1
- L3: Larger than L2 but Slower

L1,L2,L3 are SRAM (faster than DRAM)

## Operating System

- Files are abstractions for I/O devices
- Virtual memory is an abstraction for both the Main Memory and Disk I/O devices
- Processes are abstractions for the Processor, Main Memory, and I/O devices.
- Provides the illusion that the program is the only one running on the system
- Context Switching manages multiple Processes Behaviours
