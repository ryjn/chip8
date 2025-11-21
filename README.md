# CHIP-8 Emulator in C++
To learn and practice C++, I've taken on building a CHIP-8 emulator! This README will serve as my notes as I go along.

## Emulator
An emulator is hardware or software that enables a computer system to behave like another system. This allows running software that was originally designed for a different system.

In the context of this project, our emulator will read instructions and emulate the behavior of a CHIP-8.

## CHIP-8
There are a few key elements of a CHIP-8 that will need to be imitated.

### 16 8-bit Registers
Registers are dedicated storage locations on a CPU where operations occur. CPUs have limited registers, so data is usually stored in memory before being transferred to registers for operations.

The CHIP-8 as 16 8-bit registers, labeled `V0` to `VF`, each holding a value from `0x00` to `0xFF`. The `VF` register is different, in that it is used as a flag to hold information about the result of operations.

### Memory
The CHIP-8 as 4096 bytes of memory, which it uses to store data at different memory addresses ranging from `0x000` to `0xFFF`.

The addresses are segmented into three sections:
  1. `0x000 - 0x1FF` - originally reserved for the CHIP-8 interpreter
  2. `0x050 - 0x0A0` - storage space of the 16 built-in characters (0 - F)
  3. `0x200 - 0xFFF` - instructions from the ROM

[!NOTE]
ROM files contain the instructions for the CHIP-8

### 16-bit Index Register
A special register used to hold memory addresses for use in operations.

### 16-bit Program Counter
A register used to hold the address of the next instruction. Instructions are stored in third memory section, starting at address `0x200`. The CPU needs a way to track which instruction to perform next.

An individual instruction is 2 bytes, but a memory address is a single byte. When fetching an instruction, we will need to fetch a byte from this register and a byte "+1". The next instruction, then, will be at the current address + 2.

### 16-level Stack
A stack is used by the CPU to keep track of the order of execution.

### 8-bit Stack Pointer
The Stack Pointer **points** to where in the stack the most recent value was placed.
