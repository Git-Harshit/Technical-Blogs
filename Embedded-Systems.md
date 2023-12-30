# Introduction

Technical Systems that are built on a Hardware and Software are likely **Embedded Systems**. An Embedded System is built upon a set of components, processor(s) and software logic programmed into each processor chip in order to achieve an intelligent working solution. Unlike general purpose devices like computers, embedded systems are built to target a specific set of applications and they only involve the required limited resources due to this nature.

# Hardware Fundamentals

* Microprocessor ( $\mu$ P )
* Microcontroller ( $\mu$ C )
* System on Chip (SoC)
* System on Module (SoM)

<u> Architecture: </u>
* Reduced Instruction Set Computing (RISC)
    * Example: ARM architecture
* Complex Instruction Set Computing (CISC)
    * Example: Intel x86 architecture

<!-- Microprocessors features, built-ins as auxiliary circuits or internal peripherals (timer, GPI/O, DMA, Memory caches and instruction pipelines) -->

Clock signal is used for synchronization.
Clock Sources can be a crystal or oscillator circuit.

Peripherals are Input-Output (I/O) devices.
<!-- Various peripherals like UART, SPI, I2C, IPC, DMA, GPIO, ADC, DAC, Timer. -->

# Software Fundamentals

Commonly used languages to develop an Embedded Software are Assembly, C and C++. Each of these languages have their own set of advantages and challenges.

| Language | Advantage | Disadvantage |
|:--------:|-----------|--------------|
| Assembly | Closeness to hardware     | Difficult to learn, processor-specific  |
| C | Low level language | Not as close as Assembly |
| C++ | Classes and Exception Handling features over C | Object Oriented Programming concepts to be learnt |

Development can be either Baremetal (also known as No RTOS) or RTOS.

# Debugging Tools

* Logic Analyzer
* JTAG and Pin Connections
* Oscilloscope
* `assert` and logs

# Did You Know?

* Double Data Rate (DDR) RAM memory uses both rising and falling edge of clock signal for data transmission, instead of just rising one as in older models, and hence it is named as 'double' data rate because of effectively doubling the rate of transfer.

# Useful Resources

## Documentation

* Technical Reference Manual (TRM)
* Processor Datasheet
* Register Addendum
* Hardware User's Guide

## Some References

* An Embedded Software Primer by David E. Simon, Pearson Education Publications, ISBN - 978-81-7758-154-6
* Computer Organization and Architecture by William Stallings, Pearson India Education Services Publications, ISBN - 978-93-560-6159-0

# Disclaimer

This blog post is only meant to document the understanding of the author, [Harshit Gupta](https://github.com/Git-Harshit) and is not meant to reserve ownership level rights to the published content. Information provided above has been studied and confirmed from the rest of the information over internet for validation, yet any user of the above information may validate it for assuring its correctness. Though the content has been documented on own words, any overlap with any other source shall not be considered as an attempt to plagiarize from any source.
