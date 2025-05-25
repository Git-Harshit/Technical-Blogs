# Introduction to RISC-V

[RISC-V](https://en.wikipedia.org/wiki/RISC-V) (read as RISC-Five, similar in pronounciation with *Risk-Five*) is an open-sourced architecture which is based on the [RISC](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer) Instruction Set Architecture.

## History

Its development commenced in May 2010 in the University of California, Berkeley. One of the first RISC architectures was created at Berkeley between 1980 and 1984. RISC-V is the 5th generation of Berkeley RISC.

## About RISC-V

RISC-V is open-source and modular, it allows for customization being extensible.

### Profile and Platform

Profile only describes ISA features, and does not cover the complete execution environment. Examples of profile are: RVA23, RVB23, RVA22, RVA20, RVI20.

Platform is a specificaton of the Execution Environment. Platform comprises of:
1. Software Platform
2. Hardware Platform

A Platform can add additional constraints, but not remove mandatory items or even reduce other requirements in a profile.
Examples:
    - PicoRV32: Size-optimized RISC-V core for FPGA design implementations and embedded system applications.
    - BeagleV: A BeagleBoard-based RISC-V platform for Linux development.
    - ESP32-C3: A RISC-V-based microcontroller from Espressif.

### Instruction-Set Architecture (ISA)

RISC-V supports several integer instruction set extensions, such as:

- RV32I: 32-bit base integer instruction set.
- RV64I: 64-bit base integer instruction set. It extends RV32I to a 64-bit architecture, allowing compatibility to 64-bit wide registers and a larger addressable memory space.
- RV128I: 128-bit base integer instruction set. It has been defined as of 2025, but is not widely used.
- RV32C: 16-bit compressed instructions that can be mixed with the standard 32-bit instructions. RV64C is like-wise available for use with 64-bit.
- RV32F: 32-bit Floating Point Extension, which extends the RV32I by adding floating-point instructions for handling 32-bit single-precision floating point numbers.
- RV64F: 64-bit Floating Point Extension that extends the RV64I base integer ISA with single-precision floating-point operations. Both RV32F and RV64F follow the IEEE 754 floating-point standard.
- RV32D: Double-precision (64-bit) Floating-point extension, extending the RV32F extension for 64-bit operations.
- RV64D: Double-precision (64-bit) Floating-point extension that extends RV64F with double-precision floating-point operations. Both RV32D and RV64D are also compatible with the IEEE 754 floating-point standard.

### Privilege levels

The RISC-V Instruction Set Manual, Volume II: Privileged Architecture, defines three privilege levels:

1. User/Application (U-mode): Intended for conventional application.
2. System (S-mode): Intended for usage by OS.
3. Machine (M-mode): It has the highest privileges and is the only mandatory privilege level for a RISC-V hardware platform.

Attempts to perform operations not permitted by the current privilege mode will cause an exception to be raised.

Additionally, implementations may include a debug mode (D-mode) to support off-chip debugging. D-mode can be considered as an additional privilege mode, even more than M-mode.

## Extensions

### Cryptographic Extensions

- Scalar Cryptography Extension
- Vector Cryptography Extension
- Entropy Source Instructions: Supports secure random number generation.

# References

1. [RISC-V International](https://riscv.org/)
2. https://www.wevolver.com/article/risc-v-vs-arm