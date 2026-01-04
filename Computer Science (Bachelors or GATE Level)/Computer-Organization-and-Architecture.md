# Computer Organization and Architecture

## Computer Organization

- Processor Organization
    - Control Unit (CU)
    - Arithmetic and Logical Unit (ALU)
    - Pipelining and instruction-level parallelism.

- Memory Hierarchy
    - Cache memory (levels L1, L2, L3)
    - Virtual memory and paging
    - RAM vs. ROM, primary vs. secondary storage

- Input/Output Systems
    - I/O techniques: programmed I/O, interrupt-driven I/O, DMA
    - Peripheral devices and controllers

- Performance Enhancements (Implementation)
    - Parallel processing execution details
    - Concurrency and synchronization mechanisms

- Multiprocessor systems (organization of cores, interconnects)
- Emerging implementations (chip design, neuromorphic hardware organization)

## Computer Architecture

- Data Representation
    - Number systems (binary, octal, decimal, hexadecimal)
    - Character encoding (ASCII, Unicode)
    - Floating-point representation

- Instruction Set Architecture (ISA)
    - Types of instructions (data transfer, arithmetic, control)
    - Addressing modes
    - RISC vs. CISC architectures

- Performance Enhancements (Conceptual)
    - Flynn’s taxonomy (SISD, SIMD, MISD, MIMD)
    - Superscalar and multicore design philosophy

Von Neumann architecture is a stored-program model in which program instructions and data share the same unified memory and are accessed via the same system buses. This organization simplifies hardware design and enables programs to be treated as data, allowing self-modifying code and loadable programs. However, it also creates a performance limitation known as the Von-Neumann bottleneck, where instruction and data fetches contend for the same memory bandwidth, potentially restricting throughput.

Harvard architecture employs physically separate memories and buses for instructions and data, permitting simultaneous access to both and reducing contention between instruction fetches and data transfers. Classic Harvard designs are common in embedded and real-time systems (example, microcontrollers and Digital Signal Processors) where predictable timing and higher instruction/data throughput are critical; many modern processors use a modified Harvard approach that combines separate caches for instructions and data with a unified main memory to gain benefits of both models.

### Instruction Set Architecture (ISA)

Instruction Set Architecture (ISA) is the formal hardware–software interface that defines the set of machine-level instructions, instruction encodings, addressing modes, register set, memory model, and exception/interrupt semantics. It specifies the programmer-visible behavior and binary format that software targets, enabling portability across different implementations that adhere to the same ISA while allowing microarchitectural differences (pipelines, caches, execution units) underneath.

Types of instructions:
- Data Transfer Instructions: Move data between registers, memory, and I/O.
- Arithmetic Instructions: Perform mathematical operations on data.
- Control Instructions: Alter the sequence of execution (program flow).

Simplified Instructional Computer / Extra Equipment (SIC/XE) is a hypothetical computer architecture used in Computer Science courses to help students learn Assembly language, instruction formats, addressing modes and system software concepts. XE adds more features than the basic SIC, like more registers, different instructional formats (1, 2, 3, and 4 byte), advanced addressing modes (immediate, indirect, indexed, base-relative, PC-relative). A SIC/XE simulator can simulate CPU registers (A, X, L, B, S, T, PC, SW), memory, instruction execution, loads object code produced by SIC/XE assembler (generally two-pass assembler to use labels and forward references), and support debug features.

## Subject Topics (from [GATE 2026 CS](https://gate2026.iitg.ac.in/doc/GATE2026_Syllabus/CS_2026_Syllabus.pdf) syllabus)

Machine instructions and addressing modes. ALU, data‐path and control unit. Instruction pipelining, pipeline hazards. Memory hierarchy: cache, main memory and secondary storage; I/O interface (interrupt and DMA mode).