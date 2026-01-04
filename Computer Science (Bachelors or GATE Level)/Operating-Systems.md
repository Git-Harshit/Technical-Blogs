# Operating System

Operating System is an intermediate software between a Hardware and a user program.

Threads are the smallest unit of execution within a process. Threads within a process share a same memory space.

Process is an instance of a running program. Each process has its own memory space.

- Deadlock: Processes waiting for a resource for ever, possibly due to the inter-related resources been held by another processes in the waiting queue.
- Livelock: Situation where two or more processes continuously change their state in response to each other without making any progress.

Priority Inversion is the situation where a lower-priority task holds a resource needed by a higher-priority task, causing the higher-priority task to be delayed. This happens as follows: Higher Priority task needs to access a shared resource, while lower priority task has been holding a lock or resource, and a medium priority that does not need that resource starts running and preempts the lower priority task because it has a higher priority than the lower priority task. As a result, the higher priority task is blocked on lower priority tasks to complete. One common solution to priority inversion is priority inheritance where the lower priority task temporarily inherits the higher priority until it releases the resource.

### Memory Management

Virtualization: Virtual Memory is allocated to separately provide extended RAM memory to an application by combining Paginations from the RAM and Hard Drive storage.

## Subject Topics (from [GATE 2026 CS](https://gate2026.iitg.ac.in/doc/GATE2026_Syllabus/CS_2026_Syllabus.pdf) syllabus)

System calls, processes, threads, inter‐process communication, concurrency and synchronization. Deadlock. CPU and I/O scheduling. Memory management and virtual memory. File systems.