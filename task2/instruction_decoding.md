# Instruction Decoding — 'main'

Decode at least 5 RISC-V integer instructions from your .s or .objdump. Use the following format in a markdown.



# factorial.c



| Instruction      | Format | rd  | rs1 | rs2 / imm   | funct3 | funct7  | Opcode  | Binary (as shown)                       | Meaning / effect                |
| ---------------- | ------ | --- | --- | ----------- | ------ | ------- | ------- | --------------------------------------- | ------------------------------- |
| `addi sp,sp,-32` | I-type | x2  | x2  | imm=-32     | 000    | —       | 0010011 | `111000000000 00010 000 00010 0010011`  | Adjust stack pointer down by 32 |
| `sd ra,24(sp)`   | S-type | —   | x2  | x1 / imm=24 | 011    | —       | 0100011 | `0000001 00001 00010 011 11000 0100011` | Store return address at 24(sp)  |
| `li a5,12`       | I-type | x15 | x0  | imm=12      | 000    | —       | 0010011 | `000000001100 00000 000 01111 0010011`  | Load immediate 12 into a5       |
| `mv a0,a5`       | R-type | x10 | x15 | x0          | 000    | 0000000 | 0110011 | `0000000 01111 00000 000 01010 0110011` | Move value from a5 into a0      |





# max\_array.c 



| Instruction      | Format         | rd  | rs1 | rs2 / imm | funct3 | funct7  | Opcode  | Binary (as shown)                        | Meaning / effect                      |
| ---------------- | -------------- | --- | --- | --------- | ------ | ------- | ------- | ---------------------------------------- | ------------------------------------- |
| `addi sp,sp,-64` | I-type         | x2  | x2  | imm=-64   | 000    | —       | 0010011 | `110000000000 00010 000 00010 0010011`   | Allocate 64 bytes on stack            |
| `sd ra,56(sp)`   | S-type         | —   | x2  | x1/imm=56 | 011    | —       | 0100011 | `0000000 00001 00010 011 111000 0100011` | Save return address at 56(sp)         |
| `sd s0,48(sp)`   | S-type         | —   | x2  | x8/imm=48 | 011    | —       | 0100011 | `0000000 01000 00010 011 110000 0100011` | Save frame pointer at 48(sp)          |
| `ld a3,16(a5)`   | I-type (load)  | x13 | x15 | imm=16    | 011    | —       | 0000011 | `000000010000 01111 011 01101 0000011`   | Load word from address a5+16 into a3  |
| `slli a5,a5,2`   | I-type (shift) | x15 | x15 | shamt=2   | 001    | 0000000 | 0010011 | `0000000 00010 01111 001 01111 0010011`  | Multiply a5 by 4 (shift left by 2)    |
| `sext.w a5,a5`   | R-type         | x15 | x15 | x0        | 000    | 0000000 | 0111011 | `0000000 00000 01111 000 01111 0111011`  | Sign-extend 32-bit word in a5 to XLEN |





# bitop.c 



| Instruction      | Format         | rd  | rs1 | rs2 / imm | funct3 | funct7  | Opcode  | Binary (as shown)                       | Meaning / effect                   |
| ---------------- | -------------- | --- | --- | --------- | ------ | ------- | ------- | --------------------------------------- | ---------------------------------- |
| `addi sp,sp,-32` | I-type         | x2  | x2  | imm=-32   | 000    | —       | 0010011 | `111000000000 00010 000 00010 0010011`  | Decrease stack pointer by 32       |
| `sd ra,24(sp)`   | S-type         | —   | x2  | x1/imm=24 | 011    | —       | 0100011 | `0000000 00001 00010 011 11000 0100011` | Store return address               |
| `and a5,a5,a4`   | R-type         | x15 | x15 | x14       | 111    | 0000000 | 0110011 | `0000000 00100 01111 111 01111 0110011` | Bitwise AND a5 and a4              |
| `or a5,a5,a4`    | R-type         | x15 | x15 | x14       | 110    | 0000000 | 0110011 | `0000000 00100 01111 110 01111 0110011` | Bitwise OR a5 with a4              |
| `slli a5,a5,3`   | I-type (shift) | x15 | x15 | shamt=3   | 001    | 0000000 | 0010011 | `0000000 00011 01111 001 01111 0010011` | Shift left logical (multiply by 8) |




# bubble\_sort.c

| Instruction        | Format | rd  | rs1 | rs2 / imm   | funct3 | funct7 | Opcode  | Binary (as shown)                        | Meaning / effect                |
| ------------------ | ------ | --- | --- | ----------- | ------ | ------ | ------- | ---------------------------------------- | ------------------------------- |
| `addi sp,sp,-64`   | I-type | x2  | x2  | imm=-64     | 000    | —      | 0010011 | `110000000000 00010 000 00010 0010011`   | Allocate 64 bytes on the stack  |
| `sd ra,56(sp)`     | S-type | —   | x2  | x1/imm=56   | 011    | —      | 0100011 | `0000000 00001 00010 011 111000 0100011` | Save return address             |
| `li a5,9`          | I-type | x15 | x0  | imm=9       | 000    | —      | 0010011 | `000000001001 00000 000 01111 0010011`   | Load immediate 9 into a5        |
| `sw a5,-24(s0)`    | S-type | —   | x8  | x15/imm=-24 | 010    | —      | 0100011 | `1111111 00101 01000 010 100100 0100011` | Store word a5 at offset -24(s0) |
| `blt a4,a5,<loop>` | B-type | —   | x14 | x15         | 100    | —      | 1100011 | (binary shown in screenshot)             | Branch to loop if a4 < a5       |




