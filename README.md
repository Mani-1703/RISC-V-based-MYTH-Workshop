# RISC-V based MYTH Workshop

**Microprocessor for You in Thirty Hours (MYTH)** — a 5-day hands-on workshop organized by **VSD (VLSI System Design)** and **Redwood EDA**, conducted by **Kunal Ghosh** and **Steve Hoover**, in partnership with **NASSCOM**. (Total time to complete - 10 Days) 

This repository documents my journey through the workshop: from writing and compiling a simple C program on the RISC-V toolchain, all the way to building a single-cycle RISC-V CPU core and then extending it into a pipelined RISC-V CPU, using TL-Verilog on Makerchip.

---

## About the Workshop

The workshop takes a software-to-hardware approach:

- Start with C programming and the RISC-V GNU toolchain
- Move into number systems, ABI, and assembly-level programming
- Learn digital logic design using TL-Verilog and Makerchip
- Build a single-cycle RISC-V CPU microarchitecture
- Extend it into a fully pipelined RISC-V CPU

---

## Table of Contents

| Day | Topic |
|-----|-------|
| [Day 1](./Day1/README.md) | Introduction to RISC-V ISA and GNU compiler toolchain |
| [Day 2](./Day2/README.md) | Introduction to ABI and basic verification flow |
| [Day 3](./Day3/README.md) | Digital Logic with TL-Verilog and Makerchip |
| [Day 4](./Day4/README.md) | Basic RISC-V CPU microarchitecture |
| [Day 5](./Day5/README.md) | Complete Pipelined RISC-V CPU microarchitecture |
---

## Tools Used

| Tool | Purpose |
|------|---------|
| RISC-V GNU Toolchain (GCC, GDB, Binutils) | Compile, debug, and disassemble RISC-V programs |
| Spike | RISC-V ISA simulator, used to run and debug compiled binaries |
| TL-Verilog & Makerchip IDE | Interactive digital logic design and simulation |
| picorv32 (open-source RISC-V core) | Used for Day 2 firmware/instruction-level testing |

---

## Repository Structure

```
.
├── README.md
├── Day1/
│   ├── README.md
│   ├── sum1ton.c
│   ├── unsignedHighest.c
│   ├── signed_highest.c
│   └── images/
├── Day2/
│   ├── README.md
│   └── images/
├── Day3/
│   ├── README.md
│   ├── *.v (TL-Verilog lab code, Makerchip's default download extension)
│   └── images/
├── Day4/
│   ├── README.md
│   ├── *.v (progressive single-cycle CPU build-up)
│   └── images/
└── Day5/
    ├── README.md
    ├── *.v (progressive pipelined CPU build-up)
    └── images/
```

---

## Acknowledgements

- **Kunal Ghosh**, Co-founder, VSD Corp. Pvt. Ltd.
- **Steve Hoover**, Redwood EDA, creator of TL-Verilog
- **NASSCOM**, for supporting this certification program

---

## Author

**Manivannan**
GitHub: [Mani-1703](https://github.com/Mani-1703)
