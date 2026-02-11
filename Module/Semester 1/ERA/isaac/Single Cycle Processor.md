---
tags:
  - computer_architecture
  - logic
  - integrated_circuits
  - cpu
domain: E
finished: true
---
--- 
**Date**: 29.01.26
**Time**: 16:10 

> **Brief Summary**
> The Single Cycle Processor is a type of processor that processes each instruction entirely in a **single** CPU cycle. This processor is rather inefficient, but showcases the core functionality of a processor well.


---
# Single Cycle Processor

> [!info] 
> Please read [[RISC-V Assembly]] before learning about the single cycle processor!

A processor is built up of multiple key components. The main goal of a processor is to be able to **read** instructions, **execute** instructions, and **store** the results of these instructions continuously until there are no instructions left to read. 

CPU instructions are built according to the CPU's respective **ISA** (Instruction Set Architecture). This is because each assembly language encodes operations differently, and this is why a CPU needs to be specifically built for a target assembly language. For example, a RISC-V CPU cannot interpret raw x86 assembly instructions, and instead would require a translation. 

##### RISC-V Instructions

As seen in[[RISC-V Assembly | this note]] each instruction in RISC-V assembly is **encoded** (Assembly Instruction -> 32 Bit Binary Number) into machine-readable code a.k.a. a number. 

**RISC-V 32 Instruction Breakdown**
![[Pasted image 20260129162431.png]]

As seen in the diagram above, each instruction type is defined by the **first 7** bits of the instruction. This is known as the "opcode" and it specifies to the CPU which **type** of instruction is about to be executed. Other than the opcode everything else depends on the type of instruction. The **funct7** and **funct3** bits are used in instructions to tell the CPU what kind of **control signals** should be activated during the instruction, and help the CPU know exactly which **subtype** of the given operation it is executing. Registers require **5 bits** since RISCV offers **32** general purpose registers and we need $\large \log_{2}(32)$ bits to address those regesters individually. The rest of the free space is often preserved for **immediates** which are just hardcoded numbers. 

##### Structure of a Processer

**Program Counter**
- Input: 32 Bit Address (Old PC)
- Output: 32 Bit Address (New PC)

The program counter component stores the address of the current instruction to be executed. The program counter component is a simple D Flip Flop that is generally incremented by **four**[^1]  on each **rising edge**. If there has been a branch or jump then the target address is loaded into the program counter instead. The program counter gives it's address to the **instruction memory** component.

**Instruction Memory**
- Input: 32 Bit Address (Program Counter)
- Output: 32 Bit Instruction

This is a memory component that stores the instructions, and uses the program counter component's **output** as an address to load the next 32-bit instruction.

**Register Bank**
- Input: 2x32 Bit Register Addresses, 32 Bit Writeback Address, 32 Bit Writeback Value
- Output: 2x32 Bit Register Values

This is another memory component that holds our 32 **general-purpose registers**. It allows us to read from up to two register addresses, and write to one address. The Register Bank has a special **Write Signal** that stems from the **Control Unit** which only allows writing to the Register Bank if the **current** (single-cycle) instruction is an instruction that requires a value to be written back to a register.

**ALU**
- Input: 2x32 Bit Register Values
- Output: 32 Bit Value

Explained thoroughly in [[Integrated Circuit Arithmetic|this note]]. The operation that the ALU performs is determined by the **ALUControl** Signal.

**Data Memory (Main Memory)**

This component, similar to the register bank and instruction memory components, acts as a hub for reading data from and writing data to our main memory. This is only required for the special **lw** and **sw** instructions. 

**Control Unit**

The control unit can be seen as the **brain** of the CPU, as it uses the bits in each instruction to determine what **kind** of instruction is being loaded, and uses **signals** which are like **boolean flags** that determine how each component should work. For example, if we are fetching a R Type **`add`** instruction then we need to make sure that the **Write Signal** for the Register Bank is activated, and we need to make sure that the **ALUControl Signal** for the ALU is set to addition.

**Immediate Extender**

This component selects the required bits out of the instruction to interpret the provided immediate. As seen above, sometimes our immediates are strewn across the instructions, and therefore we use a **ImmSrc Signal** to tell the Extender which bits to combine that ultimately form our immediate. This is only relevant for **I Type** instructions.

**Summary of a RISC-V Single Cycle Processor**
![[Pasted image 20260129165723.png]]

##### The Big Problem with the Single Cycle Processor

**Definition**: A cycle is defined as the **time** between and including two rising clock edges. 

Since every instruction has to be performed in one cycle we need to define a **long** enough clock cycle to **fit** every instruction. There are some instructions like the "load" instructions that can take long due to the fact that we need to load a value out of memory, see [[CPU Cache |this note on caches for more info]]. However other operations like most of the R type operations are blazing fast, and therefore this imbalance leads to **slack**. The [[Multi Cycle Processor]] attempts to solve this issue, but raises other problems in the process. The [[Pipelined Processor]] is the real solution to this problem as it tries to **fully utilize** the CPU at all times.



---
## Related Topics
- [[RISC-V Assembly]]
- [[Integrated Circuit Arithmetic]]
- [[Multi Cycle Processor]]
- [[Pipelined Processor]]


[^1]: We increment the PC by four because RISC-V Assembly uses **byte-addressing** which means each address points to a single byte in memory. Our instructions in RISC-V are a constant 32-bits or **4** bytes long. Therefore we must increment by 4 to get to the next instruction.
