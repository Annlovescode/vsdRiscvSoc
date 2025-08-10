# Instruction Decoding – bitops.c (main section)

Below are 5 decoded instructions from the `main` section of `bitops` program, compiled for RV64IMAC.

---

## 1. `addi sp, sp, -32`

- **Type:** I-type  
- **Opcode bits:** `000000000000 00000 000 00010 0010011`  
  - imm[11:0] = `111111000000` (-32 in decimal, two's complement)  
  - rs1 = `sp` (x2) → `00010`  
  - funct3 = `000`  
  - rd = `sp` (x2) → `00010`  
  - opcode = `0010011` (OP-IMM)  
- **Meaning:** Add immediate `-32` to `sp` and store result in `sp`.  
- **Plain English:** Decrement the stack pointer by 32 bytes to allocate stack space.

---

## 2. `sd ra, 24(sp)`

- **Type:** S-type  
- **Opcode bits:** `0000000 00001 00010 011 11000 0100011`  
  - imm[11:5] = `0000000`  
  - rs2 = `ra` (x1) → `00001`  
  - rs1 = `sp` (x2) → `00010`  
  - funct3 = `011` (store doubleword)  
  - imm[4:0] = `11000` (24 decimal)  
  - opcode = `0100011` (STORE)  
- **Meaning:** Store the value in `ra` into memory at address `(sp + 24)`.  
- **Plain English:** Save the return address onto the stack at offset 24.

---

## 3. `lui a5, %hi(.LC20)`

- **Type:** U-type  
- **Opcode bits:** `xxxxxxxxxxxxxxxxxxxxx 01111 0110111`  
  - imm[31:12] = upper 20 bits of `.LC20` label  
  - rd = `a5` (x15) → `01111`  
  - opcode = `0110111` (LUI)  
- **Meaning:** Load upper immediate 20 bits of `.LC20` address into `a5`.  
- **Plain English:** Prepare register `a5` with high part of address for string `"bitops"`.

---

## 4. `and a5, a4, a5`

- **Type:** R-type  
- **Opcode bits:** `0000000 01111 00100 111 01111 0110011`  
  - funct7 = `0000000`  
  - rs2 = `a5` (x15) → `01111`  
  - rs1 = `a4` (x14) → `00100`  
  - funct3 = `111` (AND)  
  - rd = `a5` (x15) → `01111`  
  - opcode = `0110011` (OP)  
- **Meaning:** Perform bitwise AND between `a4` and `a5`, store result in `a5`.  
- **Plain English:** Compute `x & y` for printing.

---

## 5. `slliw a5, a5, 3`

- **Type:** I-type (shift-immediate variant for 32-bit result)  
- **Opcode bits:** `0000000 00011 01111 001 01111 0011011`  
  - funct7 = `0000000`  
  - shamt = `00011` (3 decimal)  
  - rs1 = `a5` (x15) → `01111`  
  - funct3 = `001` (SLLI / shift left logical immediate)  
  - rd = `a5` (x15) → `01111`  
  - opcode = `0011011` (OP-IMM-32)  
- **Meaning:** Shift `a5` left by 3 bits, keeping only lower 32 bits, sign-extended.  
- **Plain English:** Multiply the value in `a5` by 8 (32-bit arithmetic).

---

**Note:** All register names follow the standard RISC-V calling convention:  
`sp` = stack pointer (x2), `ra` = return address (x1), `a0`–`a7` = function arguments/return values, etc.

---
