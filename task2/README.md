# 🛠️ Task 2: Local RISC-V Toolchain Proof, Execution & ISA Decoding

![Platform](https://img.shields.io/badge/Platform-VirtualBox-orange)
![Toolchain](https://img.shields.io/badge/Toolchain-RISC--V-blue)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Environment](https://img.shields.io/badge/Environment-Ubuntu%2022.04-yellow)

---

## 🎯 Overview

* ✅ Compile and execute 4 C programs using the RISC-V toolchain and `spike pk`
* ✅ Embed unique identifiers in each build (username, hostname, machine ID, timestamps)
* ✅ Disassemble and capture the `main` section from each binary
* ✅ Manually decode selected integer instructions

---

## 🧩 Task 2.1 — Define Unique Build Variables

### 🎯 Aim
Configure shell variables to embed build/run uniqueness into each program.

### ⚙️ Commands
```bash
export U=$(id -un)
export H=$(hostname -s)
export M=$(cat /etc/machine-id | head -c 16)
export T=$(date -u +%Y-%m-%dT%H:%M:%SZ)
export E=$(date +%s)
✅ Outcome
Stored username, hostname, machine ID, UTC time, and epoch time.

Passed as #define macros during compilation.

📷 Sample Output

🧩 Task 2.2 — Create unique.h Common Header
🎯 Aim
Provide a reusable header that prints build/run metadata & generates unique ProofID/RunID.

⚙️ Code (Header Snippet)
c
Copy
Edit
#ifndef UNIQUE_H
#define UNIQUE_H
#include <stdio.h>
#include <stdint.h>
#include <time.h>
/* ... macros for USERNAME, HOSTNAME, etc. ... */
static uint64_t fnv1a64(const char *s) { /* ... */ }
static void uniq_print_header(const char *prog) { /* ... */ }
#endif
✅ Outcome
Generates ProofID at compile-time and RunID at runtime.

Used in all 4 programs.

🧩 Task 2.3 — factorial.c
🎯 Aim
Run a recursive factorial program while embedding unique metadata.

⚙️ Compile
bash
Copy
Edit
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 \
-DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" \
-DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E \
factorial.c -o factorial
▶ Execute
bash
Copy
Edit
spike pk ./factorial
📷 Output

🛠 Disassembly
bash
Copy
Edit
riscv64-unknown-elf-objdump -d ./factorial | sed -n '/<main>:/,/^$/p'
🧩 Task 2.4 — max_array.c
⚙️ Compile
bash
Copy
Edit
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 \
-DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" \
-DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E \
max_array.c -o max_array
▶ Execute
bash
Copy
Edit
spike pk ./max_array
📷 Output

🧩 Task 2.5 — bitops.c
⚙️ Compile
bash
Copy
Edit
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 \
-DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" \
-DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E \
bitops.c -o bitops
▶ Execute
bash
Copy
Edit
spike pk ./bitops
📷 Output

🧩 Task 2.6 — bubble_sort.c
⚙️ Compile
bash
Copy
Edit
riscv64-unknown-elf-gcc -O0 -g -march=rv64imac -mabi=lp64 \
-DUSERNAME="\"$U\"" -DHOSTNAME="\"$H\"" -DMACHINE_ID="\"$M\"" \
-DBUILD_UTC="\"$T\"" -DBUILD_EPOCH=$E \
bubble_sort.c -o bubble_sort
▶ Execute
bash
Copy
Edit
spike pk ./bubble_sort
📷 Output

🧩 Task 2.7 — Instruction Decoding
🎯 Aim
Manually decode RISC-V integer instructions from .s or .objdump.

📄 Detailed decoding for all 4 programs:
➡️ View solutions.md

✅ Completion Checklist
Requirement	Status
Toolchain Installed	✅
Unique Build Variables Set	✅
All 4 Programs Compiled & Executed	✅
ProofID / RunID Visible in Outputs	✅
Disassembly of main Captured	✅
Instruction Decoding Documented	✅
