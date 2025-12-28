# Introduction

ARM is a [RISC](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer)-based architecture developed by the [ARM](https://developer.arm.com/) company, previously short for Advanced RISC Machines.
ARM licenses its architecture and core specifications, has not been manufacturing its own hardware (planning in 2025).

## Cortex Processors

ARM has three profiles of CPU processors:

- Cortex-A: Application Profile, Higher-end, designed to run a complex Embedded Operating System
    - Cortex-X and Neoverse later got added in the same category. 
- Cortex-R: Real-time processor
- Cortex-M: Microcontroller profile. Low-end processor, small, highly power-efficient.

Other profiles of Processors by ARM are:

- Ethos - NPUs: High Performance for Machine Learning applications.
- Neoverse: Cloud-native, cloud-to-edge CPU. Highly scalable.
    - Example usage: Amazon Graviton, Microsoft Cobalt, Google Axion, Ampere
- SecurCore: Physical embedded security, with anti-tampering features. Example: SCS300, SC000
- Mali - GPUs (acquired by ARM)
- Immortalis - GPUs: High-performance GPUs for Mobiles. It is based on Arm's 3rd-Generation Valhall architecture and is their first GPU to support hardware-based ray tracing.

## ARM Architecture

Architecture is a functional specification. ARM Architecture is a functional specification for processors.
ARM Architecture commonly specifies the following items:

1. Instruction set
2. Register set
3. Exception Model
4. Memory model
5. Debug, trace and profiling

ARM Architecture Reference Manual describes an architecture specification relevant to any implementation of that Architecture. Arm system architectures define components and interfaces that simplify hardware and software interoperation. The CPU architecture defines the basic instruction set, and the exception and memory models.

Micro-architecture specifies the Build and Design of a processor. Each ARM Cortex processor counts as a micro-architecture. A feature which is implementation defined is defined under the specific micro-architecture. Each ARM Cortex processor has a Technical Reference Manual (TRM) documentation with features described specific to a processor, and a Configuration and Integration Manual (CIM) on integrating the processor into a system which is relevant to SoC designers. TRMs are available to download from ARM Developer site without a license whereas CIMs are only available to IP licensees.

"Processing Element (PE)" is a generic term for a machine that implements the ARM Architecture.

## Instruction Set

1. Thumb (16-bit)
2. ARM (32-bit)
3. Thumb-II (16-bit/32-bit, also called Thumb-32)
    1. It is Backward compatible with the original 16-bit Thumb instructions.
    2. Supports interleaved instructions, dynamically interpreting each fetch and decode instruction as 16-bit or 32-bit.

Other instruction set extensions seen with ARM cores:

- Vector Floating Point (VFP) instructions.
    - Requires floating coprocessor and/or software support.
    - Supports both Single Precision (32-bit) and double precision (64-bit) floating point operations.
- NEON (also known as Advanced SIMD)
    - Wide Single Instruction, Multiple Data (SIMD)
    - Intended for media applications (such as codecs)

* The Basic Instruction Set commands remain consistent for a given architecture.

## Versioning

ARM architecture has evolved currently to 9 defined versions until mid. 2025, denoted by versions 1-9, out of which, v1-3 are now obsolete. Some minor versions like v8.1, v8.2 are also noted in existence for Cortex-A.

## Core Components

* Cache - Multiple levels of Cache. L1, L2 and optional L3 (which may be external) commonly seen in Cortex-A. L1 is separate within each core, L2 is within processor/system.
* Memory Management Unit (MMU) - Translates Virtual Memory into Physical Memory, maintains using translation tables and a Translation Lookaside Buffer (TLB) to cache recent address translations. Virtual address is used by application, physical address is used by hardware. Virtual memory space is consistent in applications, regardless of the actual physical memory layout.
    * IO-MMU, System MMU (SMMU)
* Memory Protection Unit (MPU) - Configures Memory in regions for execution permissions, privileged/unprivileged access modes, caching and sharing.
* Generic Interrupt Controller (GIC) - Newer to the old and simpler Vectored Interrupt Controller (VIC), for interrupt management. GIC is only available currently (till this portion of the blog was last updated) for Cortex-A and Cortex-R, Cortex-M core uses Nested Vector Interrupt Controller (NVIC).

### Debug

Arm CoreSight is a debug and trace technology designed to provide visibility into the execution of software running on Arm-based processors. It enables real-time debugging, profiling, and performance analysis for complex systems.

#### Useful Registers for Debug

- Program Counter (PC): Holds the address of the next instruction to be executed.
- Stack Pointer (SP): Points to the top of the stack, which is used for function calls, local variables, and Interrupt Handling. 
- Link Register (LR): Special-purpose register used to store the return address when a subroutine or function is called.
- General Purpose Registers (R0-R12 in ARM v7-A and v7-R cores, X0-X28 in ARM v8-A AArch64): General purpose, available to store data during program execution.
- Debug Registers: Debug Registers like Breakpoint Value Register (DBGBVR), Breakpoint Control Register (DBGBCR), Watchpoint Value Register (DBGVWR), Watchpoint Control Register (DBGWCR) are used for setting and managing breakpoints and watchpoints.
- Floating-Point Unit (FPU) Registers:  Used for floating-point arithmetic operations.
- Status Registers 
    - Current Program Status Register (CPSR): Contains flags that indicate the result of arithmetic and logical operations.
    - Application Program Status Register (APSR): 

### Modes

Seven basic operating modes in v7 Cortex A and R cores:

- User Mode (usr): Normal mode where applications or OS tasks run.
- Supervisor Mode (svc): Entered on reset and when Supervisor call (SVC) is executed.
- System Mode (sys): Privileged mode using the same registers as User mode.
- Abort Mode (abt): Abort mode is entered when a data or instruction prefetch 
- Undefined (und): This mode is triggered when an undefined instruction is executed, typically used for handling undefined instruction exceptions.
- Interrupt Mode (irq): Used to handle standard interrupt requests. It's a privileged mode that allows the processor to respond to hardware interrupts.
- Fast Interrupt Mode (fiq): Mode for handling high-priority, fast interrupt requests. It has its own set of registers to minimize interrupt latency.

Each mode has its own stack space and a different subset of registers.

Mode can be read through in the Current Program Status Register (CPSR). Lower 5 bits indicate the mode.
- 0b10000 (0x10) for User Mode (usr)
- 0b11111 (0x1F) for System Mode (sys)
- 0b10011 (0x13) for Supervisor Mode (svc)
- 0b10111 (0x17) for Abort Mode (abt)
- 0b11011 (0x1B) for Undefined Mode (und)
- 0b10010 (0x12) for Interrupt Mode (irq)
- 0b10001 (0x11) for Fast Interrupt Mode (fiq)

Cortex-M core has two processor modes: 
- Thread Mode: Applications
- Handler Mode: Exceptions

xPSR is the program status register for Cortex-M core.

### Exceptions

Different ARM profiles have support for different exception types.

#### Exceptions on Cortex-A core:

(Exception Handling: https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-handling/Exception-priority-order?lang=en)

[ARM Exception Descriptions](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions?lang=en):
- [Data Abort exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Data-Abort-exception?lang=en): Synchronous data read or write, or asynchronous abort from data or instruction fetch can cause data abort exception.
- [Prefetch Abort exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Prefetch-Abort-exception?lang=en): Synchronous memory abort on an instruction fetch generates Prefetch Abort exception.
- [Reset](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Reset?lang=en): Caused on assertion of reset input, processor stops execution.
- [Undefined Instruction exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Undefined-Instruction-exception?lang=en):  Might be caused by an undefined instruction, attempt to execute an instruction in an unimplemented instruction set state, division by Zero, an unimplemented or inaccessible coprocessor instruction, or a coprocessor instruction that causes an exception during execution.
- [Hyp Trap exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Hyp-Trap-exception?lang=en): Generated if the processor running in a non-secure mode other than Hypervisor Mode (Hyp Mode) commits an instruction for execution that is trapped to Hyp Mode. It is only implemented as a part of the Virtualization Extensions.
- [Supervisor Call (SVC) exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Supervisor-Call--SVC--exception?lang=en): Raised by the Supervisor Call (`SVC`) Instruction, causing the processor to enter Supervisor mode.
- [Secure Monitor Call (SMC) exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Secure-Monitor-Call--SMC--exception?lang=en): Raised by the Secure Monitor Call (`SMC`) instruction which requests a Secure Monitor function, causing the processor to enter Monitor mode. 
- [Hypervisor Call (HVC) exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Hypervisor-Call--HVC--exception?lang=en): Raised by the Hypervisor Call (`HVC`) instruction which requests a hypervisor function, causing the processor to enter Hyp mode.
- [Virtual Abort exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Virtual-Abort-exception?lang=en)
- [IRQ exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/IRQ-exception?lang=en): IRQ exception is generated as implementation defined, typically by asserting an IRQ interrupt request input to the processor.
- [Virtual IRQ exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Virtual-IRQ-exception?lang=en)
- [FIQ exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/FIQ-exception?lang=en): Similar to IRQ, FIQ interrupts are also implementation defined.
- [Virtual FIQ exception](https://developer.arm.com/documentation/ddi0406/c/System-Level-Architecture/The-System-Level-Programmers--Model/Exception-descriptions/Virtual-FIQ-exception?lang=en).

#### Exception Levels on ARMv8-A (AArch64):

[In AArch64, privilege is named as Exception Level (EL)](https://developer.arm.com/documentation/102412/0103/Privilege-and-Exception-levels/Exception-levels?lang=en).

* Exception Level 0 (EL0) - Least Privileged, with limited access to System Registers. Typically used for user applications.
* Exception Level 1 (EL1) - Medium Privileged. Typically used for the Operating System Kernel.
* Exception Level 2 (EL2) - Highly Privileged. Typically used for the Hypervisor.
* Exception Level 3 (EL3) - Highest Privileged. Typically used for the Secure Monitor or Firmware.

### Optional Security Extensions

1. ARM TrustZone - Provides hardware-enforced isolation between secure and non-secure (normal) area. Available for all Cortex core profiles.

    - Processor provides two set of virtual machines running on the same Hardware: Secure (trusted) and Normal (non-secure, non-trusted).
    - Monitor mode acts as a gatekeeper for moving between these worlds (areas). A piece of software called the Secure Monitor is responsible for switching between the secure and non-secure worlds, through software exceptions using the Secure Monitor Call (SMC) instruction.
    - The secure system often runs a Trusted Execution Environment (TEE), which provides a secure area for executing trusted applications (such as cryptographic operations, secure boot, and handling sensitive data).

2. Virtualization Extensions - Support for Hardware-level virtualization. Added since v7, supported in modern cores too.

    - Use of Hypervisor

## Miscellaneous content

* ARM processors have banked registers, meaning some registers are duplicated across different execution modes to allow for rapid context switching during exceptions and privileged operations.
* Cortex-A, Cortex-R, Cortex-M came from 2005, older ARM cores (before 2005) were named ARM1-ARM11.
* Software Libraries offered by Arm:
    * ARM CMSIS
    * ARM Compute Library (ACL)
    * ARM NN
    * ARM Performance Libraries
    * ARM RAN Acceleration Library
    * Kleidi AI
    * Kleidi CV
* Tools offered by Arm:
    * Arm AMBA Viz
    * Arm Compiler for Embedded, Linux
    * Arm Development Studio
    * Arm DSTREAM Probes
    * Arm Fast Models or Fixed Virtual Platforms (FVP)
    * Arm GNU Toolchain
    * Arm IP Explorer
    * Arm Interconnect Performance Models
    * Arm Keil MDK
    * Arm Keil Studio (Cloud-based Browser IDE, and VS Code Extension)
    * Arm Performance Studio
    * Arm Socrates
    * Arm ULINK Probes
    * Arm Virtual Hardware
    * Arm GNU Toolchain
    * LLVM Embedded Toolchain for ARM

# References

* Coursera ARM Specialization: [Arm Cortex-M Architecture and Software Development Specialization](https://www.coursera.org/specializations/cortex-m-architecture-and-software-development)
* ARM Documentation (Introducing the ARM Architecture document) https://www.arm.com/architecture/learn-the-architecture
* [The ARM University Program, ARM Architecture Fundamentals - YouTube](https://youtu.be/7LqPJGnBPMM)
* https://www.arm.com/architecture/cpu
* ARM Processors - https://www.arm.com/products/silicon-ip-cpu