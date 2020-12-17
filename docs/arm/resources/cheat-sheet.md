

# Cheat Sheet

## Table of Contents

| Entry                                                        | Purpose                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Load Instructions](/arm/resources/cheat-sheet?id=load-instructions) | Learn how to take data from memory (or a literal) and put it into a register |
| [Store Instructions](/arm/resources/cheat-sheet?id=store-instructions) | Learn how to take data from a register and put it into memory |
| [Endianness](/arm/resources/cheat-sheet?id=endianness)       | Which directions bit values in memory are read.              |
| [Register Usage](/arm/resources/cheat-sheet?id=register-usage) | What each register is used for.                              |
| [CPSR Flags](/arm/resources/cheat-sheet?id=cpsr-flags)       | A (Brief) Explanation of all CPSR Flags                      |
| [General Form of an Arm Instruction](/arm/resources/cheat-sheet?id=general-form-of-an-arm-instruction) | Showing the general form of an arm instruction               |
| [Examples of Arm Instructions](/arm/resources/cheat-sheet?id=examples-of-arm-instructions) | Examples of common arm instructions                          |
| [Immediate Values](/arm/resources/cheat-sheet?id=immediate-values) | Immediate values and loading values into registers           |
| [Branch Conditions](/arm/resources/cheat-sheet?id=branch-conditions) | Branching based on CMP conditions                            |
| [More Coming Soon !](/arm/resources/cheat-sheet?id=more-coming-soon-) | The Arm Section is WIP                                       |



## Load Instructions

| Instruction                                 | Purpose                                                      |
| ------------------------------------------- | ------------------------------------------------------------ |
| LDR R#<sub>1</sub>,  [R#<sub>2</sub>]       | Load a word from memory @ address in R#<sub>2</sub> into the register R#<sub>1</sub> |
| LDR**H** R#<sub>1</sub>,  [R#<sub>2</sub>]  | Load an unsigned half-word from memory @ address n R#<sub>2</sub> into the register R#<sub>1</sub> |
| LDR**SH** R#<sub>1</sub>,  [R#<sub>2</sub>] | Load a signed half-word @ address in R#<sub>2</sub> into the register R#<sub>1</sub> |
| LDR**B** R#<sub>1</sub>,  [R#<sub>2</sub>]  | Load an unsigned byte @ address in R#<sub>2 </sub>into the register R#<sub>1</sub> |
| LDR**SB** R#<sub>1</sub>,  [R#<sub>2</sub>] | Load a signed byte @ address in R#<sub>2 </sub> into the register R#<sub>1</sub> |

## Store Instructions

| Instruction                                 | Purpose                                                      |
| ------------------------------------------- | ------------------------------------------------------------ |
| STR R#<sub>1</sub>,  [R#<sub>2</sub>]       | Store a word from memory into address in R#<sub>2</sub> from the register R#<sub>1</sub> |
| STR**H** R#<sub>1</sub>,  [R#<sub>2</sub>]  | Store an unsigned half-word from memory into address R#<sub>2</sub> from the register R#<sub>1</sub> |
| STR**SH** R#<sub>1</sub>,  [R#<sub>2</sub>] | Store a signed half-word into address in R#<sub>2</sub> from the register R#<sub>1</sub> |
| STR**B** R#<sub>1</sub>,  [R#<sub>2</sub>]  | Store an unsigned byte into address in R#<sub>2 </sub>from the register R#<sub>1</sub> |
| STR**SB** R#<sub>1</sub>,  [R#<sub>2</sub>] | Store a signed byte into address in R#<sub>2 </sub> from the register R#<sub>1</sub> <sup>**†**</sup> |

<sup>**†**</sup> STR**SB** does not exist in Cortex M4 assembly language as the distinction between signed and unsigned bytes is unnecessary. 

## Endianness

| Term          | Definition                                                   |
| ------------- | ------------------------------------------------------------ |
| Endianness    | The difference is the byte-order in which each byte of an object is stored in memory. The term is a reference to Jonathon Swift's Gulliver's Travels. |
| Little-endian | The **least**-significant-byte is stored at the lowest address (the address closest to zero). x86 (Intel/AMD) is a little-endian architecture |
| Big-endian    | The **most**-significant-byte is stored at the lowest address. |
| Bi-endian     | Either endian-ness can be selected. ARM is bi-endian. You can switch the endianness by flipping the 9th bit in the CSPR |

## Register Usage

You won't encounter many of the non-general purpose registers in an introduction to computing course.

| Register Notation | Purpose                                                      |
| ----------------- | ------------------------------------------------------------ |
| R0 through to R10 | **General Purpose**: These are the registers you will use while running your programs. |
| R11 (FP)          | **Frame Pointer**: Points to the start of the stack frame and does not move for the duration of the subroutine call. |
| R12 (IP)          | **Intra Procedural Call**: (Scratch Register) Used by the linker to access the 32-bit address space that the Branch and Link (BL) instruction can not access. |
| R13 (SP)          | **Stack Pointer**: The stack is generally used to hold "automatic" variables and context/parameters across routine calls. |
| R14 (LR)          | **Link Register**: Used to store the return address from a subroutine. At other times, LR can be used for other purposes. |
| R15 (PC)          | **Program Counter**: Contains the address (location) of the instruction being executed at the current time |
| CPSR              | **Current Program State Register**: (Condition Flags) holds processor status and control information |

## CPSR Flags

Most of these you do not need to know for an introduction to computing course.

| Flag (B denotes the bit) | Bit Placement          | Purpose                                                      |
| ------------------------ | ---------------------- | ------------------------------------------------------------ |
| N [B31]                  | 31                     | Negative condition flag. Set to bit[31] of the result of the last  flag-setting instruction. If the result is regarded as a two's  complement signed integer, then N is set to 1 if the result was  negative, and N is set to 0 if the result was positive or zero. |
| Z [B30]                  | 30                     | Zero condition flag. Set to 1 if the result of the last flag-setting  instruction was zero, and to 0 otherwise. A result of zero often  indicates an equal result from a comparison. |
| C [B29]                  | 29                     | Carry condition flag. Set to 1 if the last flag-setting instruction  resulted in a carry condition, for example an unsigned overflow on an  addition. |
| V [B28]                  | 28                     | Overflow condition flag. Set to 1 if the last flag-setting instruction  resulted in an overflow condition, for example a signed overflow on an  addition. |
| Q [B27]                  | 27                     | Cumulative saturation bit. Set to 1 to indicate that overflow or saturation occurred in some instructions. |
| IT[1:0]                  | 26, 25                 | If-Then execution state bits for the Thumb IT (If-Then) instruction |
| J                        | 24                     | Jazelle bit. Third execution state that allows some ARM processors to execute Java bytecode in hardware. |
| SSBS [B23]               | 23                     | Speculative Store Bypass Safe.                               |
| PAN, bit [22]            | 22                     | Privileged Access Never.                                     |
| DIT, bit [21]            | 21                     | Data Independent Timing.                                     |
| Unallocated              | 20                     | N/A                                                          |
| GE                       | 19, 17, 16             | Greater than or Equal flags, for parallel addition and subtraction. |
| IT[7:2]                  | 15, 14, 13, 12, 11, 10 | If-Then execution state bits for the Thumb IT (If-Then) instruction |
| E                        | 9                      | Endianness state bit. {0b0 for little, 0b1 for big}          |
| A                        | 8                      | SError interrupt mask bit. {determines if an exception was masked or not.} |
| I                        | 7                      | IRQ mask bit:                                                |
| F                        | 6                      | FIQ mask bit: {determines if an exception was masked or not.} |
| T                        | 5                      | Thumb execution state bit                                    |
| M                        | 4, 3, 2, 1, 0          | Current PE mode. {User, FIQ, IRQ, Supervisor, Monitor, Abort, Hyp, Undefined, System} |

## General Form of an Arm Instruction

```asciiarmor
MNEMONIC{S}{condition} {Rd}, Operand1, Operand2
```

## Examples of Arm Instructions

This is by no means a complete list, but it does contain the most common instructions you will come across as a beginner.

| Instruction | Description                        | Instruction | Description                         |
| ----------- | ---------------------------------- | ----------- | ----------------------------------- |
| MOV         | **Mov**e                           | EOR         | Bitwise XOR                         |
| MVN         | **M**o**v**e and **n**egate        | LDR         | Load                                |
| ADD         | **Add**ition                       | STR         | **St**o**r**e                       |
| SUB         | **Sub**traction                    | LDM         | **L**oa**d** **M**ultiple           |
| MUL         | **Mul**tiplication                 | STM         | **S**tore **M**ultiple              |
| LSL         | **L**ogical **S**hift **L**eft     | PUSH        | **Push** on Stack                   |
| LSR         | **L**ogical **S**hift **R**ight    | POP         | **Pop** off Stack                   |
| ASR         | **A**rithmetic **S**hift **R**ight | B           | **B**ranch                          |
| ROR         | **Ro**tate **R**ight               | BL          | **B**ranch - **L**ink               |
| CMP         | **C**o**mp**are                    | BX          | **B**ranch - e**x**change           |
| AND         | Bitwise **AND**                    | BLX         | **B**ranch -**L**ink - e**x**change |
| ORR         | Bitwise **OR**                     | SWI/SVC     | System Call                         |

## Immediate Values

Due to ARM RISC Limitations (and how they dealt out bits) there was only 12 bits left of the 32 bit instruction for immediate values, Those 12 bits are then further split up into an 8 bit number and a 4 bit rotation (ROR) field this means immediate values have to be represented as a value between 0 and 255 or be constructible by performing 2 right-rotate operations (bytes rotated by an even number.) 

Immediate values are referenced by placing a # before them. Some assemblers also support other forms of literals you may be used to in high-level languages such as negative twos-complement integers (signified by a - prefix) e.g: `#-5` or an ascii character (char) signified by the character in question being placed in single quotes e.g: `#'G'`  

To be on the safe side, I would suggest using LDR for any immediate value over 255, if you do not have access to a debugger; such as in a written examination. 

This 255 limitation means it's impossible to populate an entire 32 bit value (to store 0xFFFFFFFF for example) in one single operation. Which gives us two operations

-   Perform a ridiculous amount of instructions 
-   Use LDR to load our value into a register

The latter is by far the preference,  as is much easier to read for yourself and the next person to stumble past your code. The assembler will convert this down into more simple instructions (ARM RISC only has 16 instructions, remember!)

You use LDR as such:

```armasm
LDR R#, ={literal}
```

For example

```armasm
LDR R0, =5
LDR R0, =0xFFFFFFFF
LDR R0, =-20000
LDR R0, #'G'
LDR R0, #'G'+0x30
```

The assembler is doing the majority of the work here, converting negatives into 32 bit two's complement values, performing literal arithmetic and so on. 

## Branch Conditions

Branch conditions are used by placing them directly after the letter B to form a 3-letter instruction. B on its own is considered an unconditional branch condition, and will branch no matter what. 

 ### Boolean-like Conditions

| Branch Code | Meaning (In the eyes of CMP/SUBS) | Java Equivalent | Flag Status |
| ----------- | --------------------------------- | --------------- | ----------- |
| EQ          | Equals                            | ==              | Z==1        |
| NE          | Not Equals                        | !=              | Z==0        |

### Signed Conditions

| Branch Code | Meaning (In the eyes of CMP/SUBS) | Java Equivalent | Flag Status      |
| ----------- | --------------------------------- | --------------- | ---------------- |
| GT          | Signed Greater Than               | >               | (Z==0) && (N==V) |
| LT          | Signed Less Than                  | <               | N!=V             |
| GE          | Greater Than or Equal             | >=              | N==V             |
| LE          | Less Than or Equal                | <=              | (Z==1)           |

### Unsigned Conditions

| Branch Code    | Meaning (In the eyes of CMP/SUBS) | Java Equivalent | Flag Status        |
| -------------- | --------------------------------- | --------------- | ------------------ |
| HI             | Unsigned Higher Than              | >               | (C==1) && (Z==0)   |
| LO<sup>1</sup> | Unsigned Lower Than               | <               | C==0               |
| HS<sup>1</sup> | Higher or Same                    | >=              | C==1               |
| LS             | Less Than or Equal                | <=              | (C==0) \|\| (Z==0) |

### Flag-Oriented Conditions

| Branch Code    | Meaning            | Java Equivalent | Flag Status |
| -------------- | ------------------ | --------------- | ----------- |
| MI             | Minus (negative)   | < 0             | N==1        |
| PL             | Positive           | >= 0            | N==0        |
| AL             | Always             | N/A             | N/A         |
| NV             | Never              | N/A             | N/A         |
| VS             | Signed Overflow    | N/A             | V==1        |
| VC             | No Signed Overflow | N/A             | V==0        |
| CS<sup>1</sup> | Carry Set          | >=              | C==1        |
| CC<sup>1</sup> | Carry Clear        | <               | C==0        |

<sup>1</sup> CS and HS are functionally the same as they check the same condition codes. The Same goes for CC and LO. 

## More Coming Soon !

This page is rather rushed and is actually just a copy and paste of my existing armasm notes taken throughout MT in my JF year from a variety of sources. 