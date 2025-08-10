# Instruction Decoding — 'main'

Decode at least 5 RISC-V integer instructions from your .s or .objdump. Use the following format in a markdown.
| Instruction      | Format | rd  | rs1 | rs2 / imm   | funct3 | funct7  | Opcode  | Binary (as shown)                       | Meaning / effect                |
| ---------------- | ------ | --- | --- | ----------- | ------ | ------- | ------- | --------------------------------------- | ------------------------------- |
| `addi sp,sp,-32` | I-type | x2  | x2  | imm=-32     | 000    | —       | 0010011 | `111000000000 00010 000 00010 0010011`  | Adjust stack pointer down by 32 |
| `sd ra,56(sp)`   | S-type         | —   | x2  | x1/imm=56 | 011    | —       | 0100011 | `0000000 00001 00010 011 111000 0100011` | Save return address at 56(sp) |         |
| `ld a3,16(a5)`   | I-type (load)  | x13 | x15 | imm=16    | 011    | —       | 0000011 | `000000010000 01111 011 01101 0000011`   | Load word from address a5+16 into a3  |
| `and a5,a5,a4`   | R-type         | x15 | x15 | x14       | 111    | 0000000 | 0110011 | `0000000 00100 01111 111 01111 0110011` | Bitwise AND a5 and a4              |
| `or a5,a5,a4`    | R-type         | x15 | x15 | x14       | 110    | 0000000 | 0110011 | `0000000 00100 01111 110 01111 0110011` | Bitwise OR a5 with a4              |
| `slli a5,a5,3`   | I-type (shift) | x15 | x15 | shamt=3   | 001    | 0000000 | 0010011 | `0000000 00011 01111 001 01111 0010011` | Shift left logical (multiply by 8) |

