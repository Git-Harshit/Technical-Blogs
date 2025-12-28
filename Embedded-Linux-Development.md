# Introduction

[Linux](https://en.wikipedia.org/wiki/Linux) is a family of open-source Operating Systems based on the Linux [Kernel](https://en.wikipedia.org/wiki/Kernel_%28operating_system%29). Linux designed for Embedded Systems is called Embedded Linux.

## Address Spaces

Linux Kernel and processes use virtual addresses. Addresses are translated basis of the address space.
Processes execute in user mode and Kernel mode.

User mode is unprivileged.

Kernel mode is privileged.

## Operating System

Open Firmware Device Tree, or simply Device Tree (DT) describes hardware. It is a description of hardware that is readable by an operating system so that it does not have to separately store this hardware information within itself.
Operating System uses Device Tree to get hardware information like the number of processors, total connected memory and so on. Generally, information from the Device Tree is loaded during the Boot Time.

### Device Drivers

They make a particular hardware respond to a well-defined programming interface.

Types:

- Char Drivers - Handle devices that transfer data character-by-character, such as serial ports.
- Block Drivers - Manage devices that transfer data in blocks, such as hard drives or SSDs.
- Network Drivers - Responsible for network interfaces and devices, such as Ethernet cards, Wi-Fi adapters, and Bluetooth.

#### Building a Kernel Device Driver

Source files for the Linux Device Driver uses headers from the &lt;linux/&gt;
Use `$(MAKE) -C <Kernel_Dir> M=<Module_Path>` where &lt;Kernel_Dir&gt; is "/lib/modules/$(KERNEL_VERSION)/build" and &lt;Module_Path&gt; is the location of the source file(s) of the device driver.

## Obtaining the Kernel

1. Download the latest stable kernel from the [kernel.org](https://kernel.org/) website.
2. Clone the https://github.com/torvalds/linux repository using Git.

### Configuring the Kernel

Before compiling the Kernel or modules, Kernel needs to be configured for the options (such as features, drivers) to be included. The configuration can be done using a menu-based interface by running `make menuconfig` (other options like `make xconfig` or `make nconfig` give different types of interfaces) or manually editing configuration files. The Kernel configuiration is stored in the .config file.

## Virtual Devices

/dev is a device node.

- /dev/null
- /dev/zero is a special file in Linux that produces an infinite stream of null bytes (infinite 0x00).
- /dev/random
- "loop" devices
- "dummy" network interfaces
- "ramdisk"
- "virtio"

## References

1. [Linux Device Drivers - LinkedIn Learning course](https://www.linkedin.com/learning/linux-device-drivers)
2. [Linux and the Device Tree - The Linux Kernel Documentation](https://www.kernel.org/doc/html/latest/devicetree/usage-model.html)

# ChatGPT 5-mini

## Getting Started with Embedded Linux Development

This section presents foundational theory and practical considerations for embedded Linux development. It complements the practical workflow earlier by explaining system-level concepts you should understand to design, build, and maintain embedded Linux systems.

### What is Embedded Linux
- Linux kernel + tailored userspace for resource-constrained or single-purpose devices.
- Common objectives: small footprint, deterministic behavior, controlled boot sequence, hardware abstraction, and secure update mechanisms.

### System architecture and address spaces
- Two address spaces: kernel space (privileged) and user space (unprivileged). CPU enforces isolation using MMU/MPU.
- Virtual memory: processes use virtual addresses translated to physical memory by the MMU. The kernel maps physical devices into its address space for drivers.
- Memory layout considerations: kernel text/data, modules, vmalloc, physical memory zones (DMA, normal, highmem).

### Processor modes, context and concurrency
- Modes: user mode vs kernel mode (system calls and interrupts switch contexts).
- Context switch: saving/restoring process state, TLB/shootdown implications on SMP.
- Concurrency primitives: spinlocks, mutexes, semaphores, RCU—use appropriate primitive depending on IRQ context and sleeping behavior.
- SMP considerations: cache coherency and per-CPU data.

### Interrupts, bottom halves and deferred work
- Interrupt handlers must be fast; use threaded IRQs, tasklets, or workqueues for deferred processing.
- Edge vs level-triggered interrupts and proper masking/unmasking.
- Latency trade-offs between top-half and bottom-half execution.

### Boot process (theory)
- Typical sequence: ROM/bootloader -> bootloader (U-Boot) loads kernel and device tree -> kernel decompression/init -> initramfs or rootfs mount -> init system starts userspace.
- Bootloader responsibilities: initialize minimal hardware, device tree/environment, choose kernel and rootfs, handoff and kernel command line.
- Initramfs roles: early userspace for complex mount setups or device provisioning.

### Device model and drivers
- Linux device model: struct device, driver, bus abstractions; match devices to drivers via bus-specific probing (platform, of_match, PCI, etc.).
- Driver frameworks: platform, I2C, SPI, GPIO, regulator, clk. Prefer reuse of kernel frameworks to reduce maintenance.
- User interfaces: sysfs, debugfs, character devices, netlink, ioctl (minimize custom ioctls; prefer generic interfaces).

### Device Tree (DT) theory
- DT describes hardware topology and parameters for non-discoverable devices.
- DT structure: nodes, compatible strings, reg/interrupts/pinctrl bindings, phandles.
- Binding documents define property semantics — kernel checks properties during probe.
- Keep DTS minimal and prefer overlays for runtime or board-specific modifications.

### Kernel modules and ABI stability
- Modules extend kernel at runtime; build against exact kernel headers and config.
- Kernel exports symbols — internal APIs can change across versions. For production, prefer in-tree drivers or vendor-maintained stable modules.
- Module signing and CONFIG_MODULE_SIG for secure loading.

### Cross-compilation and toolchains (theory)
- Cross toolchain produces binaries for target ISA. ABI choices: OABI vs EABI (modern kernels use EABI).
- Sysroot and staged rootfs must match target libraries and headers for correct linking.
- Reproducible builds: pin toolchain versions, use deterministic build systems (Buildroot/Yocto).

### Root filesystem and init
- Minimal rootfs contains busybox or small init; production images use systemd or alternate init systems.
- Filesystem layout: /sbin, /usr, /lib, /etc, device nodes in /dev (mdev/udev), runtime mounts (/proc, /sys).
- Persistent vs ephemeral storage and overlay strategies (squashfs + writable overlay) for atomic updates.

### Debugging, tracing and observability (theory)
- Early boot: serial console, earlyprintk, initramfs logs.
- Kernel logs: dmesg, printk levels, dynamic printk.
- Tracing: ftrace, perf, tracepoints, BPF (bpftrace) for low-overhead observability.
- Userland debugging: gdbserver, strace, ltrace, valgrind where applicable.

### Real-time and determinism
- PREEMPT_RT patch or CONFIG_PREEMPT for low-latency scheduling; use high-priority real-time threads and CPU isolation.
- Understand wakeup/interrupt latency sources, tickless kernel (NO_HZ), and tick granularity.

### Power management and thermal
- Suspend/resume lifecycle and device pm callbacks.
- Runtime PM: drivers implement runtime suspend/resume to reduce power during idle.
- Manage clocks, regulators, and wakeup sources carefully to avoid unwanted wakeups.

### Security and updates
- Apply secure boot and module signing for kernel authenticity.
- Use read-only rootfs with atomic update mechanisms (A/B partitions) and rollback capability.
- Harden kernel: enable seccomp, SELinux/AppArmor where feasible, minimize attack surface and unused modules.

### Testing, validation and maintenance
- Boot and smoke tests, regression tests for drivers, hardware-in-the-loop for lifecycle testing.
- Traceability: record kernel config, toolchain, BSP, and patch set used to build images.
- Long-term maintenance: plan for kernel updates, backporting, and CVE management.

### Recommended incremental learning path
1. Build a minimal image (busybox + kernel) for a target board and boot it.
2. Add and test a simple kernel module and a userspace app that uses a device driver (e.g., GPIO LED toggle).
3. Learn to read and modify a device tree for pinmux and peripheral enablement.
4. Introduce Buildroot or Yocto, reproduce the image, and automate builds.
5. Add tracing and implement a basic power management policy.

Further reading: kernel documentation for driver models and device tree bindings, Buildroot and Yocto guides, and books/online courses on Linux kernel internals and device drivers.

This section gives a concise, practical path for beginners to start developing software for embedded Linux devices.

### Prerequisites
- Basic C programming and Linux command-line skills.
- Familiarity with cross-compilation concepts and SSH/serial communications.
- A development host (Linux workstation or WSL) with Git, make, gcc, and required tools installed.

### Key Concepts
- Cross toolchain: Compiler and tools that generate binaries for the target architecture (arm, aarch64, etc.).
- Root filesystem (rootfs): Collection of user-space programs and libraries that run on the device.
- Bootloader (e.g., U-Boot): Initializes hardware and loads the kernel.
- Kernel and device tree: Kernel provides drivers; Device Tree describes hardware to the kernel.
- Userspace vs kernel space: Device drivers and kernel modules run in kernel space; applications run in userspace.

### Common Toolchains and Build Systems
- Buildroot — quick way to generate minimal rootfs and toolchain.
- Yocto Project — more flexible and suitable for production-ready images.
- GCC cross toolchains — prebuilt toolchains available from vendors or toolchain builders (e.g., Linaro).

### Quick Getting-Started Workflow
1. Choose a board or SoC and obtain its BSP (board support package) or device tree.
2. Install or build a cross toolchain for the target architecture.
3. Build a kernel (configure with menuconfig; ensure device tree and drivers are enabled).
4. Create a rootfs using Buildroot or Yocto, or assemble a simple rootfs with busybox and required libraries.
5. Deploy artifacts to storage on the board (SD card, eMMC, or via network/USB).
6. Boot the board, connect over serial console, and iterate.

### Example Commands (high-level)
- Clone kernel:
    - git clone https://github.com/torvalds/linux.git
- Cross-compile kernel:
    - make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- <defconfig>
    - make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- zImage dtbs modules -j$(nproc)
- Build a module for target (on host):
    - make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- M=$(pwd) modules
- Create a minimal rootfs with busybox:
    - Configure and install busybox to a staging directory, create /dev, /proc, /sys, and tar the filesystem.

(Replace CROSS_COMPILE and ARCH with values for your target.)

### Developing Kernel Modules and Drivers
- Use the kernel's module build infrastructure (Kbuild). Modules are built against the exact kernel headers used on the target.
- For device drivers, prefer registering with existing kernel frameworks (platform, i2c, spi, misc, etc.) and expose user-space interfaces (sysfs, char devices, netlink) as needed.
- Test drivers as loadable modules before integrating into the kernel.

### Device Tree Tips
- Start from a working device tree for your board and make incremental changes.
- Use dtc (device tree compiler) to compile and decompile (.dts ↔ .dtb).
- Validate hardware node compatible strings and pinmux/clock/provider bindings.

### Debugging and Diagnostics
- Serial console: Primary debugging channel for boot logs (use minicom, picocom, screen).
- dmesg and journalctl: Kernel and system logs.
- gdb / gdbserver: Debug user-space processes on target.
- strace / ltrace: Trace system/library calls.
- perf / ftrace: Performance and tracing for kernel and applications.
- kgdb: Kernel remote debugging (advanced).

### Deployment and Updating
- Flash images to SD card or write to eMMC/flash using vendor tools or dd.
- Consider atomic update patterns and rollback strategies for production devices.
- Use init systems (systemd, busybox init) appropriate for your rootfs size and complexity.

### Helpful Practices
- Keep build artifacts reproducible: document versions of toolchain, kernel, and BSP.
- Use git for configuration and kernel patches.
- Start simple: a small rootfs and a single blinky or UART test application proves your toolchain and boot flow.
- Enable CONFIG_MODULE_SIG if you need module signing, and ensure kernel .config matches target.

### Learning Resources
- Try Buildroot and Yocto basic tutorials to learn image creation.
- Read kernel documentation for driver models and device tree bindings.
- Use vendor reference BSPs as a starting point for board-specific details.

This should give you a clear, practical roadmap to begin building, deploying, and debugging embedded Linux systems.