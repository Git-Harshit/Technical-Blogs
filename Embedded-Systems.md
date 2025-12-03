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

* [System on Chip (SoC)](https://en.wikipedia.org/wiki/System_on_a_chip) - Combines various components of a computer system in a single IC chip. SoC may be based out of either a microprocessor or a microcontroller.

* [System on Module (SoM)](https://en.wikipedia.org/wiki/System_on_module) - Combines several computer system components on an electronic module or circuit board in simpler words.

## Architecture:

Computer Architecture refers to those attributes of a system that have a direct impact on the logical execution of a program. Computer organization refers to the operational units and their interconnections that realize the architectural specifications. $^{[2]}$

### Instruction Set Architecture:

[Instruction Set Architecture](https://en.wikipedia.org/wiki/Instruction_set_architecture) is commonly classified by its architectural complexity as:

* [Reduced Instruction Set Computing (RISC)](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer)
    * Example: ARM architecture, RISC-V architecture
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

Microprocessors features built-ins as auxiliary circuits or internal peripherals (timer, GPI/O, DMA, Memory caches and instruction pipelines)

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
* Timers (Watchdog (WDG) Timer)

Some examples of Industrial Protocols are given below:
* Fieldbus Protocols: Designed for real-time distributed control, connecting sensors, actuators, and controllers on factory floors.
    * [Modbus](https://en.wikipedia.org/wiki/Modbus) - Serial Communication Protocol
    * [Process Field Bus (Profibus)](https://en.wikipedia.org/wiki/Profibus)
* Industrial Ethernet Protocols:
    * [Ethernet for Control Automation Technology (EtherCAT)](https://en.wikipedia.org/wiki/EtherCAT) - Reference: https://www.beckhoff.com/en-en/products/i-o/ethercat/
    * [Process Field Net (PROFINET)](https://en.wikipedia.org/wiki/Profinet)
    * [Time-Sensitive Networking (TSN)](https://en.wikipedia.org/wiki/Time-Sensitive_Networking)

Different categories of peripherals are given below:

### Communication

In Serial Communication, data is transmitted one bit at a time over a single-channel or wire. This method is efficient for long-distance communication as it minimizes the number of wires and has fewer chances of error. Example: UART, SPI, I2C, USB.

In Parallel Communication, multiple bits are transmitted simultaneously over multiple channels or wires. This method is often used for short distance communication where speed is critical. It has faster data transfer rates due to simultaneous transmission of multiple bits but requires more wires that makes it complex and expensive and it is more prone to cross-talk and signal degradation/noise over long distances. Example: Peripheral Component Interconnect (PCI), General Purpose Interface Bus (GPIB)

USART is Universal Synchronous/Asynchronous Receiver Transmitter, a serial communication protocol which communicates one-to-one with Transmission (Tx) and Reception (Rx) lines cross-connected. Having separate lines of connections, it is a Full-Duplex communication protocol which allows simultaneous Bi-Directional communication between the connected devices. A UART Packet contains 1 Start Bit, Data Bits (generally 5-9 bits), Parity Bit, optional Checksum (such as Cyclic Redundancy Check) bit and 1-2 Stop Bits. It's communication speed is measured in the Bits per second (bps) unit.

SPI is Serial Peripheral Interface which communicates serially between 1 Controller (formerly, Master) and many Peripheral (formerly, Slave in a non-inclusive terminology) devices. SPI uses four pin lines: Controller Out Peipheral In (COPI), Controller In Peripheral Out (CIPO), Clock (CLK) and Chip Select (CS) for connections. Chip select lines can be more than one and be used in combination like a Binary Decoder to select a Peipheral chip to enable communication. Having individual COPI and CIPO lines for Tansmission and Reception, SPI allows Full-Duplex communication. With clock signal used for communication, its speed is measured in Hz.
- Variants of SPI such as Quad Serial Peripheral Interface (QSPI) and Octal Serial Peripheral Interface (OSPI) have a different interface with 4 and 8 Bi-Directional Data Lines respectively which gives them the Quad and Octal naming respectively. Having Bi-Directional data lines, they are Half-Duplex and not Full-Duplex. And since the group of bits are sequentially transferred per clock cycle, they are still serial communication protocols and not parallel communication protocols.

I2C is Inter-Integrated Circuit Protocol. It is used for serial communication between multiple Controller (formerly, Master) and Peripheral (formerly, Slave) interfaces. I2C communication happens on an I2C Bus, where devices are connected using Two-wire Serial Clock Line (SCL) and Serial Data Line (SDA). With just one Data line available for communication, it is a Half-Duplex communication protocol. 'Arbitration' comes to picture for conflict resolution when multiple devices need to communicate over an I2C Bus.

### Crypto (Security)

Example: Advanced Encryption Standard (AES) Symmetric Encryption, Diffie Hellman (DH) key exchange

### I/O

Example: General Purpose IO (GPIO) Pins

### Memory

Example: DDR (RAM), Flash

Some Flash Memory supports Read While Write (RWW), while others support No Read While Write (NRWW). In Read-while-write (RWW), Flash can read other memory regions while writing to another region. As flash memory is directly mapped to a fixed address in the memory space, the processor is capable of sequentially fetching and executing single instructions from it with no intermediate steps. This mechanism is called eXecute-In-Place (XIP).

### Microcontroller

Example: Clock setting, Power Mode Configuration (could be taken care by Firmware), Peripheral Initialization control.

# Software Fundamentals

Software definition at a top level is given with the *Software Architecture*. Software architecture gives a high-level view of the components involved and their inter-dependency.

Commonly used languages to develop an Embedded Software are Assembly, C and C++. Each of these languages have their own set of advantages and challenges.

| Language | Advantage | Disadvantage |
|:--------:|-----------|--------------|
| Assembly | Closeness to hardware access | Difficult to learn, processor-specific (affects portability) |
| C | Low level language, compiles to efficient Assembly | Not as close as Assembly |
| C++ | Classes and Exception Handling features over C | Object Oriented Programming concepts to be learnt |

Considering the benefits of ease of development while maintaining the hardware memory access through pointers, and compiled source performance, with inline Assembly capability, C Programming is widely preferred for the development of Embedded Systems. A mix of Assembly and C is generally used, with Assembly source used for development like startup code, and calling some processor-specific instructions directly.

With memory safety aspects, programming languages like [Rust](https://en.wikipedia.org/wiki/Rust_(programming_language)) are also gaining popularity for the Embedded Software development.

Firmware is a low-level software that is tightly coupled with the hardware. It provides basic control, initialization, and functionality for the device.

Device Driver is a low-level software component that controls or communicates to a particular hardware device. It performs low-level hardware instructions.

Linker is a utility program that combines one or more files containing object code from separately compiled program modules into a single file containing loadable or executable code. Loader is a program routine that copies an executable program into memory for execution. $^{[2]}$ 
Many Embedded Linkers create an output \*.map file that lists placement of each segment in memory, also including the addresses of global data and public functions. Linker for embedded systems is also called as a *locator*.

Development can be either Baremetal (also known as No RTOS) or Operating-System based (such as RTOS, Linux).

In case of Embedded software development, the device for which development is performed (the processor getting burned with the program output) is termed as *target* machine and the device on which this preparation can takes place is termed as a *host* machine (host is also called as *workstation*).

[Executable and Linkable Format (ELF)](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format) is a standard output file format used to store executables, object code, shared libraries, and core dumps. ELF contains structured format of multiple sections, such as code (text section), data, and symbol tables, along with header tables and metadata about the program's structure and execution environment. ELF often include Debug Information (like symbols, line numbers, function) and Relocation Information (fixing addresses at runtime, which allows programs to be loaded dynamically at different memory addresses).
A Raw Flashable Binary is a simple binary file that contains only the raw machine code to be executed by the target processor. It strips away all the metadata, debug information, and section headers present in an ELF file, leaving simply the compiled program.

Loading the Binary or hex file onto the Embedded System processor can be done using a programmer/debugger or flashing tool. Tools like a USB Programmer (such as ST-Link, J-Link), a bootloader if the system supports (example: using a UART or USB connection), or a dedicated flashing utility (such as openocd for ARM-based systems, avrdude for AVR microcontrollers) can be used.

## Compilation

Compilation is the process of converting a higher-level language to a machine-understandable code. Unlike interpretation where the source is executed in a line-by-line fashion, compilation is performed at one go, with all the errors reported at once for a source file, except for a fatal error in C/C++ where compilation is stopped immediately. Examples of fatal error in C/C++ are: #include header file not found, #error directive.

Generally, as development (Host) machine is different than the target processor device, cross-compilation is performed for the source code using the target-specific compiler tool chain.

Compilation of Embedded Software involves two steps: Compiling and Linking. Each of it is performed separately and may not be clubbed into one step.

For example, on ARM compiler arm-none-eabi-gcc, the following steps are followed:

1. Compilation

Either generate individual object files per source file using:

```sh
arm-none-eabi-gcc -c <source_file(s)_.c>
```

or combine them to a single object file by adding `-o <combined_object>.o` at the end to the above command.

2. Linking

Linking may be done by either the compiler (arm-none-eabi-gcc) or linker (arm-none-eabi-ld).

    1. Using Compiler

        ```sh
        arm-none-eabi-gcc <object_file(s)> -T <linker.ld> -o <output.elf>
        ```

        This way, startup files and standard libraries are also added (unless suppressed with -nostartupfiles -nostdlib), C run-time dependencies are also added (example: initializing __libc_init_array) due to which it is easier and safer. Not recommended when full manual control is desired on these areas.

    2. Using Linker

        ```sh
        arm-none-eabi-ld <object_file(s)> -T <linker.ld> -o <output.elf>
        ```

## Bare-Metal Programming

Bare-Metal is a low-level programming done to interface the Hardware directly. Bare-Metal Programming instructions directly runs on the Hardware Processor & Memory, without any abstraction layer involved. As Instructions are carried out directly on Hardware Registers, Bare-Metal is also known as Register Level Programming. Primary references are device datasheet, Technical Brief Reference and header files.

Startup code is used as a starting point of Bare-metal applications to set up the entry point (set Reset Handler using interupt vector table), initialize globals from the .data and .bss sections (optional before call to main(), but usually practiced), and then jump to the entry function that is conventionally main().

In a C program development under the modern PC or an Operating System, the OS and compiler toolchain provide this code and it need not be setup by a developer. C Run-time (CRT) library provides the foundational environment required for a C/C++ progam to execute. Key components of the CRT are: Startup Code, Standard Library Functions, Exit and Cleanup, and Exception Handling (only for C++).

Note: With a custom startup source, any global function (global, because the assembler or linker need to find and reference it) can be used and application may then not have a main() function defined.

World Before main() execution:
- Reset Vector
- Hardware Init
- Startup Code
- Call to the entry function which is usually `main()`

## Operating System based Programming

Operating Systems provide features like scheduling and managing resources with context.

### Real-Time Operating Systems

Systems with a deterministic time bound for operations.
RTOS is a scheduler operating system.

Key components:
- Tasks and Co-routines
    - Task is a basic execution unit in an RTOS, with its own Task Control Block (TCB) maintaining its own Program Counter (PC), Stack, State (Ready, Running, Blocked, Suspended).
    - Coroutine is a smaller execution unit than a Task.
        - All of them sharing the same stack
        - Cannot be preempted (timeout) by the RTOS scheduler
        - Yield control explicitly (cooperative multi-tasking).
- Events
    - An event (or event flag/group) is a lightweight synchronization primitive used to notify tasks about occurrences (hardware interrupts, state changes, or other tasks).
    - Implemented as a bitmask: each bit represents a distinct event/condition. Tasks wait for one or more bits to be set.
- Queues (FIFO)
    - Queues are a primary RTOS IPC primitive for passing messages or pointers between tasks and ISRs using First-In‑First‑Out semantics.  
- Statically Dynamic Memory Management
    - Pre-reserving some memory statically and then allocating storage out of it as required, to save the overhead from the libraries.

#### Types of Multi-processing

- Asymmetric Multi-processing (AMP): Each core runs an independent OS instance or pinned bare-metal tasks with explicit inter-core communication and no OS-level task migration.
- Symmetric Multi-processing (SMP): A single RTOS kernel schedules and load-balances tasks across multiple cores with shared memory, allowing dynamic task migration and requiring SMP-safe drivers and synchronization.

Blackberry QNX Neutrino RTOS also offers Bound Multi-processing (BMP), which is said to be an improvement over the standard SMP.

## Safety - Automobile Software Development

*Risk* is known to occur. It cannot be completely eliminated. The goal of Functional Safety is to bring the risk down to an acceptable state.

### Safety Qualification

Automotive SPICE, [AUTomotive Open System ARchitecture (AUTOSAR)](https://autosar.org/), Functional Safety Qualification in compliance with the ISO 26262:2018 (Automobile Safety of Road Vehicles) and IEC 61508:2010 Safety standards.

# Debugging Tools

* Logic Analyzer
* Protocol Analyzer (also called as packet sniffer) - A protocol analyzer is a software or hardware that captures and analyzes data traffic over a network.
* Probe - JTAG and Pin Connections
    * Joint Test Action Group (JTAG) is a standardized interface (based on IEEE 1149.1) that allows you to directly communicate with the internals of a chip. It usually involves pins like Test Data In (TDI), Test Data Out (TDO), Test Clock (TCK), Test Mode Select (TMS), Test Reset (TRST, optional). JTAG can access CPU Registers, memory and peripherals directly - even before the system boots.
    * Serial Wire Debug (SWD) is a two-pin interface protocol developed by ARM for debugging and programming ARM-based microcontrollers. The Two pins used are: Serial Wire Data Input/Output (SWDIO) and Serial Wire Clock (SWCLK).
    * Open On-Chip Debugger ([OpenOCD](https://openocd.org/)) is an open-source software tool to access JTAG/SWD functionalities.
* Oscilloscope
* Multimeter
* Instruction Set Simulator
* In-Circuit Emulator (ICE)
* [GNU Project Debugger (GDB)](https://sourceware.org/gdb/)
* `assert` and logs

## Extracting symbols from ELF file

Executable and Linkable Format (ELF) file contains the ELF header, program header table, section header table, sections (such as .bss & .data uninit and init data, .rodata read-only data, .debug debugging info, .got global offset table & .plt procedure linkage table, .rel/.rela relocation info, .strtab string table, .symtab symbolic table, .text machine code) and the actual program data.

Several tools exist to help find the symbols of an ELF file. In Linux, the common ones used are as follows:

1. `gdb [<path-to-elf>]`

   The path to ELF file can be passed after launching the "(gdb)" prompt using `file <path-to-elf>`. On the "(gdb)" prompt, run "info symbol &lt;address&gt;" to query the symbol corresponding to a physical (not virtual) address.

2. `nm -nC <path-to-elf>`

    Lists the symbols with their addresses. -n sorts the symbols numerically by address.

3. `readelf -a <path-to-elf>`

    Reads the contents available on the given ELF file. -a flag displays all the information. Specific items like headers (-h), functions (-s) can be listed using their corresponding flags.

4. `addr2line -e <path-to-elf> [<address>|-i]`

    Outputs the corresponding file and line number as "path/to/source.c:line". Use -i for interactive mode (multiple inputs supported, each input to end with a new line followed by Ctrl+D to mark End of File)

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

Serial Network Topologies:
1. Point-to-Point: Here, exactly two devices are wired together.
2. Multi-drop topology, for a multi-drop communication setup, refers to a network configuration where multiple Peripheral devices are connected to a single Controller. In a multi-drop bus (MDB), all components are connected to the electrical circuit, and arbitration determines which device sends information.

Portable Operating System Interface (POSIX) is a set of standards defined by the IEEE to ensure compatibility between the operating systems, particularly Unix-like systems. It specifies application programming interfaces (APIs), command-line shells, and utility interfaces to improve software portability across different platforms. Windows is not POSIX-compliant by default, but offers POSIX compatibility through Windows Subsystem for Linux (WSL) and Cygwin. 
* In C, &lt;unistd.h&gt; header file provides access to POSIX APIs.
* Scatter-Gather I/O is a technique used for efficiently reading and writing data from and to multiple buffers at once. It allows the I/O operations to handle non-contiguous memory regions as if they were contiguous. 
    * In C, readv() for scatter read and writev() for gather write in system calls in Unix-like operating systems provide implementation for scatter-gather.

# Did You Know?

* Double Data Rate (DDR) RAM memory uses both rising and falling edge of clock signal for data transmission per clock cycle, instead of just rising one as in older models (Synchronous Dynamic RAM, SDRAM), and hence it is named as 'double' data rate because of effectively doubling the rate of transfer.
* Many Operating Systems have derived an embedded flavor of them, including Embedded Windows (Windows IoT) and Embedded Linux.

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
