# Day 1 — Introduction to RISC-V ISA and GNU Compiler Toolchain

Day 1 covers the basics of RISC-V ISA keywords, the GNU cross-compiler toolchain, and simulating a compiled RISC-V binary using Spike.

---

## RV-D1SK1 — Introduction to RISC-V Basic Keywords

A conceptual introduction to the RISC-V ISA — instruction formats, registers, and how a program moves from C code to machine code. (Notes/summary can go here if you took any.)

---

## RV-D1SK2 — Labwork for RISC-V Software Toolchain

### Lab 1 — Compile and Run a C Program Natively

Wrote a simple C program (`sum1ton.c`) that computes the sum from 1 to n, compiled it with the native `gcc`, and ran it to confirm correct output before cross-compiling for RISC-V.

```c
#include <stdio.h>

int main(){
    int i, sum=0, n=1807;
    for(i=1;i<=n;i++)
        sum = sum + i;
    printf("Sum from 1 to %d is %d \n",n,sum);
    return 0;
}
```

```
$ gcc sum1ton.c
$ ./a.out
Sum from 1 to 1807 is 1633528
```

![Lab 1 - Native compile and run](./lab1&2.png)

---

### Lab 2 — Cross-Compile with the RISC-V GNU Toolchain

Cross-compiled the same program using `riscv64-unknown-elf-gcc`, then used `objdump` to view the generated RISC-V assembly for the `main` function.

```
$ riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
$ riscv64-unknown-elf-objdump -d sum1ton.o
```

> **Note:** initially mistyped `-01` (zero-one) instead of `-O1` (capital-O-one) — GCC rejected it with `unrecognized command line option '-01'`. Fixed by correcting the flag.

![Lab 2 - Disassembly with -O1](./lab2.png)

Also compared the disassembly using the `-Ofast` optimization flag to see how instruction count/selection changes with a more aggressive optimization level:

```
$ riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
```

![Lab 2 - Disassembly with -Ofast](./lab2_ofast.png)

---

### Lab 3 — Simulate the RISC-V Binary with Spike

Used **Spike**, the RISC-V ISA simulator, to run the cross-compiled binary and confirm it produces the same output as the native run.

```
$ spike pk sum1ton.o
bbl loader
Sum from 1 to 1807 is 1633528
```

![Lab 3 - Spike simulation](./lab3_spike.png)

Then used Spike's interactive debug mode (`-d`) to step through the program instruction-by-instruction and inspect register values directly, to verify the compiled instructions matched the expected program logic.

```
$ spike -d pk sum1ton.o
(spike) until pc 0 10158
(spike) reg 0 sp
(spike) reg 0 a5
...
```

![Lab 3 continued - Spike debug mode, register stepping](./spike_lab3_contd.png)

---

## RV-D1SK3 — Integer Number Representation

*(To be completed — signed and unsigned 64-bit number representation lab)*

---

## Key Takeaways from Day 1

- How a C program is compiled and cross-compiled for a different ISA (host `gcc` vs `riscv64-unknown-elf-gcc`)
- How to read RISC-V disassembly output (`objdump -d`) and map it back to the C source
- How optimization flags (`-O1` vs `-Ofast`) affect instruction selection
- How to run and debug a RISC-V binary using Spike's functional simulator