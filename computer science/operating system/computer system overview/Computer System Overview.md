# Computer System Overview
## Basic Elements
- **Processor**
	Controls the operation of the computer and performs data processing functions 

- **Main Memory**
	Stores data and programs (instructions), the main memory is volatile.
	
- **I/O Modules**
	Move data between a computer and its external environments
	
- **System Bus**
	Provides communication among processors, main memory and I/O modules

## Instruction Execution
A program consists of instructions which are executed by the processor. The execution of a single instruction consists of two stages - fetch and execute.

A special register - the **program counter (PC)** keeps track of the memory location of the instruction. The processor first fetch the instruction based on the address given by the PC, then the processor interprets the instruction and perform the required action. In general, the actions are

1. Control Instruction - an instruction may alter the sequence of execution (`if, for, while, break`)

2. Data Processing Instruction - an instruction may perform arithmetic or logical operations on the data

3. Data Transfer Instruction - an instruction can move data in between the processor and I/O modules or main memory.

## [[Interrupts]]
All computers provide a mechanism by which other modules (I/O, memory) may interrupt the normal sequencing of the processor. The main objective of providing interrupts mechanism is to improve processor utilization.

## Memory Hierarchy

## Cache Memory

## Direct Memory Access

## Multiprocessor and Multicore Organization