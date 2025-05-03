# Introduction

Technical Systems that are built on a Hardware and Software are likely **Embedded Systems**. An Embedded System is built upon a set of components, processor(s) and software logic programmed into each processor chip in order to achieve an intelligent working solution. Unlike general purpose devices like computers, embedded systems are built to target a specific set of applications and they only involve the required limited resources due to this nature.

<details>
<summary><h2>Full forms for Abbreviations and Acronyms</h2></summary>

| Short Form | Full Expansion |
|     :-:    |       ---      |
|     I/O    | **I**nput and/or **O**utput |
|     MCU    | **M**icro**c**ontroller **U**nit |
|     MPU    | **M**icro**p**rocessor **U**nit |
|     RAM    | **R**andom **A**ccess **M**emory |
|     ROM    | **R**ead **O**nly **M**emory |

</details>

# Hardware Fundamentals

* [Microprocessor](https://en.wikipedia.org/wiki/Microprocessor) ($\mu$ P) - Programmable semiconductor electronic device that comprises of a Central Processing Unit (CPU)
    * Examples:
        * Earlist known - Intel 4004, Texas Instruments' TMS1000
        * More examples - Intel 8086, Texas Instruments AM62x Sitara MPU

* [Microcontroller](https://en.wikipedia.org/wiki/Microcontroller) ($\mu$ C) - Comprises of Microprocessor, memory, I/O Ports and Peripherals in an Integrated Circuit (IC).
    * Examples: Intel 8051, Texas Instruments AM263x Sitara MCU

* [System on Chip (SoC)](https://en.wikipedia.org/wiki/System_on_a_chip) - Combines various components of a computer system in a single IC chip.

* [System on Module (SoM)](https://en.wikipedia.org/wiki/System_on_module) - Combines several computer system components on an electronic module or circuit board in simpler words.

## Architecture:

Computer Architecture refers to those attributes of a system that have a direct impact on the logical execution of a program. Computer organization refers to the operational units and their interconnections that realize the architectural specifications. $^{[2]}$

### Instruction Set Architecture:

[Instruction Set Architecture](https://en.wikipedia.org/wiki/Instruction_set_architecture) is commonly classified by its architectural complexity as:

* [Reduced Instruction Set Computing (RISC)](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer)
    * Example: ARM architecture
* [Complex Instruction Set Computing (CISC)](https://en.wikipedia.org/wiki/Complex_instruction_set_computer)
    * Example: Intel x86 architecture

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

## Peripherals

Peripherals are Input-Output (I/O) devices which can be utilised by any processor.

Various peripherals are available to facilitate specific purposes:
* [Analog to Digital Converter (ADC)](https://en.wikipedia.org/wiki/Analog-to-digital_converter)
* [Controller Area Network (CAN)](https://www.allaboutcircuits.com/technical-articles/introduction-to-can-controller-area-network/), [CAN Bus](https://en.wikipedia.org/wiki/CAN_bus)
* [Digital to Analog Converter (DAC)](https://en.wikipedia.org/wiki/Digital-to-analog_converter)
* [Direct Memory Access (DMA)](https://en.wikipedia.org/wiki/Direct_memory_access)
* [General Purpose I/O (GPIO)](https://en.wikipedia.org/wiki/General-purpose_input/output)
* [Inter-Integrated Circuit (I2C)](https://en.wikipedia.org/wiki/I%C2%B2C)
* [Inter Process Communication (IPC)](https://en.wikipedia.org/wiki/Inter-process_communication)
* [Pulse Width Modulation (PWM)](https://en.wikipedia.org/wiki/Pulse-width_modulation)
* [Serial Peripheral Interface (SPI)](https://en.wikipedia.org/wiki/Serial_Peripheral_Interface)
* [Universal Synchronous Asynchronous Receiver-Transmitter (USART)](https://en.wikipedia.org/wiki/Universal_synchronous_and_asynchronous_receiver-transmitter)
* Timers

Different categories of peripherals are given below:
- Communication
- Crypto (Security)
- I/O
- Memory
- Microcontroller

In Serial Communication, data is transmitted one bit at a time over a single-channel or wire. This method is efficient for long-distance communication as it minimizes the number of wires and has fewer chances of error. Example: UART, SPI, I2C, USB.

In Parallel Communication, multiple bits are transmitted simultaneously over multiple channels or wires. This method is often used for short distance communication where speed is critical. It has faster data transfer rates due to simultaneous transmission of multiple bits but requires more wires that makes it complex and expensive and it is more prone to cross-talk and signal degradation/noise over long distances.

USART is Universal Synchronous/Asynchronous Receiver Transmitter, a serial communication protocol which communicates one-to-one with Transmission (Tx) and Reception (Rx) lines cross-connected. Having separate lines of connections, it is a Full-Duplex communication protocol which allows simultaneous Bi-Directional communication between the connected devices. A UART Packet contains 1 Start Bit, Data Bits (generally 5-9 bits), Parity Bit, optional Checksum (such as Cyclic Redundancy Check) bit and 1-2 Stop Bits. It's communication speed is measured in the Bits per second (bps) unit.

SPI is Serial Peripheral Interface which communicates serially between 1 Controller (formerly, Master) and many Peripheral (formerly, Slave in a non-inclusive terminology) devices. SPI uses four pin lines: Controller Out Peipheral In (COPI), Controller In Peripheral Out (CIPO), Clock (CLK) and Chip Select (CS) for connections. Chip select lines can be more than one and be used in combination like a Binary Decoder to select a Peipheral chip to enable communication. Having individual COPI and CIPO lines for Tansmission and Reception, SPI allows Full-Duplex communication. With clock signal used for communication, its speed is measured in Hz.
- Variants of SPI such as Quad Serial Peripheral Interface (QSPI) and Octal Serial Peripheral Interface (OSPI) have a different interface with 4 and 8 Bi-Directional Data Lines respectively which gives them the Quad and Octal naming respectively. Having Bi-Directional data lines, they are Half-Duplex and not Full-Duplex. And since the group of bits are sequentially transferred per clock cycle, they are still serial communication protocols and not parallel communication protocols.

I2C is Inter-Integrated Circuit Protocol. It is used for serial communication between multiple Controller (formerly, Master) and Peripheral (formerly, Slave) interfaces. I2C communication happens on an I2C Bus, where devices are connected using Two-wire Serial Clock Line (SCL) and Serial Data Line (SDA). With just one Data line available for communication, it is a Half-Duplex communication protocol. 'Arbitration' comes to picture for conflict resolution when multiple devices need to communicate over an I2C Bus.

# Software Fundamentals

Commonly used languages to develop an Embedded Software are Assembly, C and C++. Each of these languages have their own set of advantages and challenges.

| Language | Advantage | Disadvantage |
|:--------:|-----------|--------------|
| Assembly | Closeness to hardware access | Difficult to learn, processor-specific  |
| C | Low level language, compiles to efficient Assembly | Not as close as Assembly |
| C++ | Classes and Exception Handling features over C | Object Oriented Programming concepts to be learnt |

Firmware is a low-level software that is tightly coupled with the hardware. It provides basic control, initialization, and functionality for the device.

Device Driver is a low-level software component that controls or communicates to a particular hardware device. It performs low-level hardware instructions.

Linker is a utility program that combines one or more files containing object code from separately compiled program modules into a single file containing loadable or executable code. Loader is a program routine that copies an executable program into memory for execution. $^{[2]}$ 
Many Embedded Linkers create an output \*.map file that lists placement of each segment in memory, also including the addresses of global data and public functions. Linker for embedded systems is also called as a *locator*.

Development can be either Baremetal (also known as No RTOS) or Operating-System based (such as RTOS, Linux).

In case of Embedded software development, the device for which development is performed (the processor getting burned with the program output) is termed as *target* machine and the device on which this preparation can takes place is termed as a *host* machine (host is also called as *workstation*).

[Executable and Linkable Format (ELF)](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format) is a standard output file format used to store executables, object code, shared libraries, and core dumps. ELF contains structured format of multiple sections, such as code (text section), data, and symbol tables, along with header tables and metadata about the program's structure and execution environment. ELF often include Debug Information (like symbols, line numbers, function) and Relocation Information (fixing addresses at runtime, which allows programs to be loaded dynamically at different memory addresses).
A Raw Flashable Binary is a simple binary file that contains only the raw machine code to be executed by the target processor. It strips away all the metadata, debug information, and section headers present in an ELF file, leaving simply the compiled program.

Loading the Binary or hex file onto the Embedded System processor can be done using a programmer/debugger or flashing tool. Tools like a USB Programmer (such as ST-Link, J-Link), a bootloader if the system supports (example: using a UART or USB connection), or a dedicated flashing utility (such as openocd for ARM-based systems, avrdude for AVR microcontrollers) can be used.

## Bare-Metal Programming

Bare-Metal is a low-level programming done to interface the Hardware directly. Bare-Metal Programming instructions directly runs on the Hardware Processor & Memory, without any abstraction layer involved. As Instructions are carried out directly on Hardware Registers, Bare-Metal is also known as Register Level Programming. Primary references are device datasheet, Technical Brief Reference and header files.

Startup code is used as a starting point of Bare-metal applications to set up the entry point (set Reset Handler using interupt vector table), initialize globals from the .data and .bss sections (optional before call to main(), but usually practiced), and then jump to the entry function that is conventionally main().

In a C program development under the modern PC or an Operating System, the OS and compiler toolchain provide this code and it need not be setup by a developer. C Run-time (CRT) library provides the foundational environment required for a C/C++ progam to execute. Key components of the CRT are: Startup Code, Standard Library Functions, Exit and Cleanup, and Exception Handling (only for C++).

Note: With a custom startup source, any global function (global, because the assembler or linker need to find and reference it) can be used and application may then not have a main() function defined.

World Before main() execution: Reset Vector, Hardware Init, Startup Code, call to the entry function `main()`

# Debugging Tools

* Logic Analyzer
* Protocol Analyzer (also called as packet sniffer) - A protocol analyzer is a software or hardware that captures and analyzes data traffic over a network.
* Probe - JTAG and Pin Connections
    * JTAG (Joint Test Action Group) is a standardized interface (based on IEEE 1149.1) that allows you to directly communicate with the internals of a chip. It usually involves pins like Test Data In (TDI), Test Data Out (TDO), Test Clock (TCK), Test Mode Select (TMS), Test Reset (TRST, optional). JTAG can access CPU Registers, memory and peripherals directly - even before the system boots.
* Oscilloscope
* Multimeter
* Instruction Set Simulator
* In-Circuit Emulator (ICE)
* `assert` and logs

# Miscellaneous content

A digital signal processor (DSP) is a specialized microprocessor designed specifically for processing digital signals in real-time. (Good for multimedia including Audio, Image, Video). DSP's ability to perform mathematical operations very quickly lets them process large data efficiently.

Hypervisor, also known as a Virtual Machine Monitor (VMM), is a software or hardware that creates or manages virtual machines (VMs) by allowing single hardware host sharing. They allocate physical resources as CPU, memory, storage among VMs and keep them isolated from one another.
- Type 1 Hypervisor (Bare-Metal Hypervisor):
    - Runs directly on the host's hardware
    - Examples: Xen, VMware ESXi, Microsoft Hyper-V
- Type 2 Hypervisor (Hosted Hypervisor):
    - Runs on top of an Operating System
    - Easier to setup and manage, but offers slightly lower performance than Type 1.
    - Examples: QEMU, Oracle VM VirtualBox, VMware workstation.

Reset instruction clears state and brings the execution back to a starting point.
- Warm Reset (Soft Reset): It is initiated without completely cutting off power. This resets software components but may retain RAM memory. It doesn't reinitialize every physical circuit but clears the running state. This is faster than cold reset.
- Cold Reset (Hard Reset): It resets all components of a device, including registers and memory. This occurs when the system is power-cycled or restarted manually.

Types of resets for system reliability and fault-tolerant machanisms:
- Power-On Reset (POR): This feature ensures the device starts in a known state when power is first applied. It resets the system when supply voltage rises above a threshold voltage.
- Brown-Out Reset (BOR): This is a safeguard that resets the microcontoller when the supply voltage drops below a specific level. This prevents the device from operating unpredictably due to insufficient voltage.
- Watchdog Timer Reset: A Hadware timer that resets the microcontroller if the software fails to reset (also called as kick, service) the timer within a predefined period.
- Manual Reset: This is initiated by a user, typically using a reset button on the device or via a call to the software reset API.

# Did You Know?

* Double Data Rate (DDR) RAM memory uses both rising and falling edge of clock signal for data transmission per clock cycle, instead of just rising one as in older models (Synchronous Dynamic RAM, SDRAM), and hence it is named as 'double' data rate because of effectively doubling the rate of transfer.
* Many Operating Systems have derived an embedded flavor of them, including Embedded Windows and Embedded Linux.

# Useful Resources

## Documentation

* Technical Reference Manual (TRM)
* Processor Datasheet
* Register Addendum
* Hardware User's Guide
* CPU and Instruction Set (Assembly level, Architecture)

## Software

* Hardware Abstraction Layer (HAL) or Software Development Kit (SDK) from a semiconductor manufacturer.

## Some References

1. An Embedded Software Primer by David E. Simon, Pearson Education Publications, ISBN - 978-81-7758-154-6
2. Computer Organization and Architecture by William Stallings, Pearson India Education Services Publications, ISBN - 978-93-560-6159-0
3. [Intro to Bare Metal Programming - Episode 1: How to Get Started - Microchip Developer Help - YouTube](https://www.youtube.com/watch?v=_73WcZMLHzo&list=PLtQdQmNK_0DQ8KGcZ1BOPv-3RDPvtqJ1H)
4. [ARM Compiler for Embedded Reference Guide - ARM Developer](https://developer.arm.com/documentation/101754/0623)

# Disclaimer

This blog post is only meant to document the understanding of the author, [Harshit Gupta](https://github.com/Git-Harshit), and is not meant to reserve ownership level rights to the published content. Information provided above has been studied and confirmed from the existing information over internet and reference materials for validation, yet any user of the above information may validate it for assuring its correctness. Though the content has been documented on own words, any overlap with any other source shall not be considered as an attempt to plagiarize from any source.
