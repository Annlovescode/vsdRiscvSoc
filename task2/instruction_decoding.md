# Instruction Decoding — 'main'

Decode at least 5 RISC-V integer instructions from your .s or .objdump. Use the following format in a markdown.
# RISC-V Integer Instruction Decoding

| Instruction      | Opcode  | rd       | rs1      | rs2      | funct3 | funct7  | Binary (32-bit)                              | Meaning / effect                                            |
| ---------------- | ------- | -------- | -------- | -------- | ------ | ------- | -------------------------------------------- | ---------------------------------------------------------- |
| addi sp,sp,-32   | 0010011 | sp (x2)  | sp (x2)  | ---      | 000    | ---     | 111111111100 00010 000 00010 0010011         | Decrease stack pointer by 32 to allocate stack space       |
| sd s0,16(sp)     | 0100011 | ---      | sp (x2)  | s0 (x8)  | 011    | 0000000 | 0000000 01000 00010 011 10000 0100011         | Store the value of s0 into memory at address sp + 16       |
| lw a4,-20(s0)    | 0000011 | a4 (x14) | s0 (x8)  | ---      | 010    | ---     | 111111111100 01000 010 01110 0000011         | Load 32-bit word from memory at address s0 - 20 into a4    |
| xor a5,a5,a4     | 0110011 | a5 (x15) | a5 (x15) | a4 (x14) | 100    | 0000000 | 0000000 01110 01111 100 01111 0110011         | Bitwise XOR of a5 and a4, store result back in a5          |
| lw a5,-24(s0)    | 0000011 | a5 (x15) | s0 (x8)  | ---      | 010    | ---     | 111111111000 01000 010 01111 0000011         | Load 32-bit word from memory at address s0 - 24 into a5    |
| addi a0,a5,1752  | 0010011 | a0 (x10) | a5 (x15) | ---      | 000    | ---     | 000001101101 01111 000 01010 0010011         | Add immediate 1752 to a5 and store result in a0            |
| srliw a5,a5,0x2  | 0011011 | a5 (x15) | a5 (x15) | ---      | 101    | 0000000 | 0000000 00010 01111 101 01111 0011011         | Shift a5 right logically by 2 bits, 32-bit result stored   |
