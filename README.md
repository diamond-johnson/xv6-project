# xv6 Multi-Threading Extension

## Overview

In xv6 operating system project, our goal is to add multi-threading capability to the xv6 educational kernel. This feature allows us to manage multiple threads within a single process simultaneously.

Currently, xv6 only supports processes, and each process runs independently of the others. By adding threads, we can execute different parts of a program simultaneously within a single process, which leads to increased efficiency in some scenarios.

We have covered two main tasks:

1. **Familiarity with Process Management in xv6**
   - Examining the stages of creation, scheduling, context switching, and termination of processes.
   - Understanding related structures such as `proc` and `trapframe` used for process management.

2. **Adding Multi-Threading Capability to xv6**
   - Creating, joining, and terminating threads.
   - Managing shared resources and synchronizing threads.
   - Adding thread management capabilities to the kernel by modifying existing data structures and functions.

## Goals

The goal of this project is to provide a deeper understanding of concurrency management in operating systems and to examine the challenges associated with implementing multi-threading in an educational kernel. Additionally, this project addresses topics such as shared resource management, deadlock prevention, and thread synchronization, which are key issues in designing stable and efficient systems.

## Prerequisites

- Basic knowledge of C programming and operating systems concepts.
- xv6 source code (available from the official repository or MIT's xv6 repository).
- A Unix-like environment (e.g., Linux or macOS) for building and running xv6 in QEMU.

## Installation and Setup

1. **Clone the xv6 Repository**:
   ```
   git clone https://github.com/mit-pdos/xv6-public.git
   cd xv6-public
   ```

2. **Apply Modifications**:
   - This project involves modifying kernel files (e.g., `proc.h`, `proc.c`, `trap.c`, etc.) to support threads.
   - After implementing the changes described in the tasks, rebuild the kernel.

3. **Build and Run**:
   ```
   make qemu
   ```
   This will compile xv6 and launch it in QEMU. Use the serial console for interaction.

## Usage

- **Testing Process Management**: Start by exploring existing xv6 process features using system calls like `fork()`, `exit()`, and `wait()`. Use tools like `ps` (if implemented) to observe processes.
  
- **Implementing Threads**:
  - Extend the kernel to support thread creation (e.g., a new system call like `thread_create()`).
  - Implement joining (e.g., `thread_join()`) to wait for thread completion.
  - Add synchronization primitives (e.g., mutexes or semaphores) to handle shared resources.
  - Test with user-space programs that spawn multiple threads and demonstrate concurrency.

- **Example Workflow**:
  1. Modify kernel structures (e.g., add a thread list to `struct proc`).
  2. Update scheduler to handle thread context switches.
  3. Build and boot xv6.
  4. Run a test program: e.g., a multi-threaded matrix multiplication or producer-consumer simulation.

## Challenges and Considerations

- **Synchronization**: Ensure thread-safe access to shared kernel data structures to avoid race conditions.
- **Deadlock Prevention**: Design locking mechanisms carefully to prevent circular waits.
- **Context Switching**: Extend `swtch()` to handle thread-level switches without full process overhead.
- **Resource Management**: Threads share the process's memory and file descriptors, so manage allocation/deallocation accordingly.

## References

- [xv6: a simple, Unix-like teaching operating system](https://pdos.csail.mit.edu/6.828/2023/xv6.html)
- xv6 Book: [xv6: a simple Unix-like teaching operating system](https://pdos.csail.mit.edu/6.828/2023/xv6/book-riscv-rev3.pdf)
