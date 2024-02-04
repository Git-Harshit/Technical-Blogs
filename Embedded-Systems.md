# Introduction

Technical Systems that are built on a Hardware and Software are likely **Embedded Systems**. An Embedded System is built upon a set of components, processor(s) and software logic programmed into each processor chip in order to achieve an intelligent working solution. Unlike general purpose devices like computers, embedded systems are built to target a specific set of applications and they only involve the required limited resources due to this nature.

<details>
<summary><h2>Full forms and Abbreviations</h2></summary>

| Short Form | Full Expansion |
|     :-:    |       ---      |
|     I/O    | **I**nput and/or **O**utput |
|     MCU    | **M**icro**c**ontroller **U**nit |
|     MPU    | **M**icro**p**rocessor **U**nit |
|     RAM    | **R**andom **A**ccess **M**emory |
|     ROM    | **R**ead **O**nly **M**emory |

</details>

# Hardware Fundamentals

* [Microprocessor ( $\mu$ P )](https://en.wikipedia.org/wiki/Microprocessor) - Programmable semiconductor electronic device that comprises of a Central Processing Unit (CPU)
    * Examples:
        * Earlist known - Intel 4004, Texas Instruments' TMS1000
        * More examples - Intel 8086, Texas Instruments AM62x Sitara MPU

* [Microcontroller ( $\mu$ C )](https://en.wikipedia.org/wiki/Microcontroller) - Comprises of Microprocessor, memory, I/O Ports and Peripherals in an Integrated Circuit (IC).
    * Examples: Intel 8051, Texas Instruments AM263x Sitara MCU

* [System on Chip (SoC)](https://en.wikipedia.org/wiki/System_on_a_chip) - Combines various components of a computer system in a single IC chip.

* [System on Module (SoM)](https://en.wikipedia.org/wiki/System_on_module) - Combines several computer system components on a electronic module or circuit board in simpler words.

### Architecture:

* [Reduced Instruction Set Computing (RISC)](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer)
    * Example: ARM architecture
* [Complex Instruction Set Computing (CISC)](https://en.wikipedia.org/wiki/Complex_instruction_set_computer)
    * Example: Intel x86 architecture

<!-- Addition: Microprocessors features, built-ins as auxiliary circuits or internal peripherals (timer, GPI/O, DMA, Memory caches and instruction pipelines) -->

A core is an individual processing unit on a processor. Based on the number of cores present, there exist Single-Core and Multi-Core processors. A core is further broken down into the following sections (exampled from IBM z13 Core Layout):
* Instruction Fetch and Branch (IFB)
* Instruction Cache and Merge (ICM)
* Instruction Sequence Unit (ISU)
* Instruction Decode Unit (IDU)
* Load-Store Unit (LSU)
* Translation Unit (XU)
* Core Pervasive unit (PC)
* Fixed-Point Unit (FPU)
* Vector and Floating-point Units (VFU)
* Recovery Unit (RU)
* dedicated CO-Processor (COP)
* Level 2 Data (L2D) and Instruction (L2I) caches.

Clock signal is used for synchronization of a processor execution.
Clock Sources can be a crystal or oscillator circuit.

Peripherals are Input-Output (I/O) devices.
<!-- Addition: Various peripherals like UART, SPI, I2C, IPC, DMA, GPIO, ADC, DAC, Timer. -->

# Software Fundamentals

Commonly used languages to develop an Embedded Software are Assembly, C and C++. Each of these languages have their own set of advantages and challenges.

| Language | Advantage | Disadvantage |
|:--------:|-----------|--------------|
| Assembly | Closeness to hardware access | Difficult to learn, processor-specific  |
| C | Low level language | Not as close as Assembly |
| C++ | Classes and Exception Handling features over C | Object Oriented Programming concepts to be learnt |

Linker is a utility program that combines one or more files containing object code from separately compiled program modules into a single file containing loadable or executable code. Loader is a program routine that copies an executable program into memory for execution. $^{[2]}$

Development can be either Baremetal (also known as No RTOS) or RTOS.

In case of Embedded software development, the device for which development is performed (the processor getting burned with the program output) is termed as *target* machine and the device on which this preparation can takes place is termed as a *host* machine.

# Debugging Tools

* Logic Analyzer
* Probe - JTAG and Pin Connections
* Oscilloscope
* `assert` and logs

# Did You Know?

* Double Data Rate (DDR) RAM memory uses both rising and falling edge of clock signal for data transmission, instead of just rising one as in older models, and hence it is named as 'double' data rate because of effectively doubling the rate of transfer.
* Many Operating Systems have derived an embedded flavor of them, including Embedded Windows and Embedded Linux.

# Useful Resources

## Documentation

* Technical Reference Manual (TRM)
* Processor Datasheet
* Register Addendum
* Hardware User's Guide

## Some References

1. An Embedded Software Primer by David E. Simon, Pearson Education Publications, ISBN - 978-81-7758-154-6
2. Computer Organization and Architecture by William Stallings, Pearson India Education Services Publications, ISBN - 978-93-560-6159-0

# Disclaimer

This blog post is only meant to document the understanding of the author, [Harshit Gupta](https://github.com/Git-Harshit) and is not meant to reserve ownership level rights to the published content. Information provided above has been studied and confirmed from the rest of the information over internet for validation, yet any user of the above information may validate it for assuring its correctness. Though the content has been documented on own words, any overlap with any other source shall not be considered as an attempt to plagiarize from any source.
