# **Introduction to Computer Systems and Operating Systems**

### Session Content:

- Computer System Components
- Von Neumann Architecture
- Computer Operating System
- Importance and Responsibilities of an OS
- Complex and Multiprocessor Systems
- Multi-user Systems
- OS Components

# 1 Computer System Components

### 1.1 Computer System Components:

- **Hardware**: CPU, memory, I/O devices
- **Operating System**: Manages hardware and application programs
- **Application Programs**: Utilize system resources (e.g., compilers, databases, games)
- **Users**: Humans, machines, or other computers

### 1.2 Von Neumann Architecture:

- Introduced by John von Neumann (1945)
- Components: Control Unit (CU), Arithmetic and Logic Unit (ALU), Memory, Registers, I/O
- Uses stored-program concept, still fundamental in modern computing

#### 1.2.1 Central Processing Unit (CPU):

- Executes program instructions
- Consists of ALU, CU, and Registers
- **Registers**: High-speed storage areas for data processing
  - MAR: Holds memory addresses
  - MDR: Stores data being transferred
  - AC: Stores intermediate results
  - PC: Holds next instruction address
  - CIR: Holds current instruction

#### 1.2.2 Arithmetic and Logic Unit (ALU):

- Performs arithmetic (add, subtract) and logical (AND, OR, NOT) operations

#### 1.2.3 Control Unit (CU):

- Manages ALU, memory, and I/O operations
- Issues control signals for execution

#### 1.2.4 Buses:

- **Address Bus**: Transfers memory addresses
- **Data Bus**: Transfers data between CPU, memory, and I/O
- **Control Bus**: Sends control signals

#### 1.2.5 Memory Unit:

- **RAM (Random Access Memory)**: Fast, volatile memory
- **ROM (Read-Only Memory)**: Stores firmware (e.g., BIOS)
- **Storage Hierarchy**: Data moves from permanent storage to RAM for faster processing

#### 1.2.6 Input and Output Devices:

- **Input Devices**: Keyboard, mouse, microphone, scanner, barcode reader, touchpad
- **Output Devices**: Monitor, projector, speakers, printer, plotter
- **I/O Devices**: Touchscreen, network ports, USB, external storage (hard drives, flash memory, CDs/DVDs)

### 1.3 Computer Operating System (OS):

- Boots the computer using **BIOS (Basic Input/Output System)**
- Manages applications and connected devices
- Provides seamless execution for users

#### 1.3.1 What is an OS?

- A software layer managing hardware and applications
- Key objectives: **Efficiency, Usability, and Extensibility**
- Components: **Kernel (core functionalities), Libraries, Applications**
- Examples: Windows, macOS, Linux, iOS, Android

#### 1.3.2 OS Categories:

**By Usage Type:**

1. **Batch OS**: Executes repetitive tasks without human intervention (e.g., DOS)
2. **Time-Sharing OS**: Shares hardware among multiple users (e.g., Windows, Linux)
3. **Distributed OS**: Manages multiple interconnected systems (e.g., AIX, Solaris)
4. **Network OS**: Facilitates remote computing over networks (e.g., Windows Server)
5. **Real-Time OS**: Ensures precise execution timing (e.g., Embedded systems)

**By Design Features:**

1. **Monolithic OS**: All core functions run in kernel space (e.g., UNIX)
2. **Modular OS**: Uses plug-and-play components (e.g., Windows, Linux)
3. **Microservice OS**: Breaks functions into independent modules (e.g., Red Hat OS)

### 1.4 Why We Need an OS?

- Runs and manages applications efficiently
- Ensures security (authentication, encryption)
- Abstracts hardware complexity
- Manages multiprocessing, multitasking, and multi-user environments

#### 1.4.1 Complex and Multiprocessor Systems:

- **Homogeneous Systems**: Identical CPU cores
- **Heterogeneous Systems**: Mixed CPU capabilities
- OS manages CPU scheduling, hardware differences, and performance optimization

#### 1.4.2 Multitasking and Multi-user Systems:

- **Foreground & Background Tasks**: OS balances execution
- **User Access Management**: Ensures privacy, security, and resource allocation

### 1.5 Operating System Components:

- **User Applications**: Programs interacting with the OS
- **Kernel/OS Modules**: Core functionalities
- **Microservices**: Independent components for modular operation
- **APIs**: Allow applications to interact with system resources
- **Schedulers & Managers**: Handle resource allocation and conflict resolution

### 1.6 Importance of Understanding the OS:

- Developers must know the OS environment for optimal coding
- Affects programming language choice, IPC mechanisms, debugging, and performance tuning
- Essential for interfacing with hardware, handling security, and optimizing applications

### 1.7 Responsibilities of an OS:

| Requirement         | Solution                                   |
| ------------------- | ------------------------------------------ |
| CPU time allocation | Scheduling algorithms                      |
| Memory management   | API-based allocation                       |
| Device access       | I/O and device management                  |
| Storage management  | File systems & directories                 |
| Security            | Authentication, encryption, virtualization |
| Usability           | GUI and accessibility features             |

### Summary:

The OS enables efficient resource management, multitasking, security, and a seamless user experience. It ensures software compatibility, enhances system usability, and optimizes performance.

# 2 Processes and Scheduling

### Content Overview:

- Introduction to Scheduling
- Process Concept
- Process Contents
- Process States
- Process Control Block (PCB)
- Context Switching
- Scheduling

## 2.1 Introduction to Scheduling

A key responsibility of the operating system is enabling the execution of multiple concurrent applications while managing their access to system resources effectively.

As several programs may try to run simultaneously, they often compete for hardware resources such as CPU, memory, and devices.

The OS efficiently handles these competing requests by scheduling the execution and managing resources to avoid conflicts.

Before delving into scheduling algorithms and responsibilities, it's crucial to understand basic concepts like processes and threads, which form the foundation of program execution.

## 2.2 Program and Process Concept

When a software developer creates an application, it usually consists of static capabilities embedded as processed code tailored to the operating system. This is known as a program.

Once the program is triggered for execution, the OS assigns it a process ID and other tracking metrics.

At its core, a running program is referred to as a process within the OS.

In some OS contexts, "jobs" and "processes" might be used interchangeably, but a process refers specifically to a program in execution.

## 2.3 Process Contents

A process typically includes:

- **Text Section**: Program instructions.
- **Program Counter (PC)**: Points to the address of the next instruction.
- **Stack Section**: Contains local variables, return addresses, and method parameters.
- **Heap Section**: Holds global and static variables and supports dynamic memory allocation during runtime.
- **Data Section**: Global and static variables.

## 2.4 Process States

A process transitions through various states in its lifecycle:

- **New**: The process is being created.
- **Running**: The process is actively executing.
- **Waiting**: The process is waiting for an event to occur.
- **Ready**: The process is ready to be assigned to a CPU.
- **Terminated**: The process has completed execution.

The OS may manage these transitions across multiple CPU cores, minimizing frequent context switches between cores to improve performance.

## 2.5 Process Control Block (PCB)

The Process Control Block (PCB) stores essential information about a process:

- **Process ID**: A unique identifier for the process.
- **Process State**: Describes the current state (New, Running, Waiting, Ready, or Terminated).
- **Pointer**: May link to parent or related processes.
- **Priority**: Defines the process's scheduling priority.
- **Program Counter**: Points to the next instruction to execute.
- **CPU Registers**: Holds processor-specific data required for execution.
- **Memory Management Info**: Details on the process's memory allocation.
- **I/O Status Information**: Tracks assigned devices and usage.
- **Accounting Information**: Stores statistics such as time units remaining or memory requirements.

## 2.6 Context Switching

Context switching occurs when the OS swaps the currently executing process with another to allow multiple applications to run concurrently:

1. Pause the current process and save its context (e.g., program counter and register states).
2. Switch to the new process.
3. Restore the context for the new process to ensure it continues executing from where it left off.

## 2.7 Scheduling

The OS uses scheduling to manage which processes get executed and when. The most common process states are **Ready**, **Waiting**, and **Running**. The OS utilizes various queues to manage these processes:

- **Ready Queue**: Stores processes that are ready to be assigned to a CPU.
- **Waiting Queue**: Holds processes waiting for a resource (e.g., I/O).
- **Job Queue**: A global queue that maintains all processes in the system, used primarily for bookkeeping.

### 2.7.1 Scheduling Queues

- **Ready Queue**: Holds processes that are prepared for execution.
- **I/O Queue**: Stores processes waiting for I/O operations.

Processes may also undergo context switching or handle interruptions.

### 2.7.2 Scheduling Criteria

The OS uses various metrics to determine the scheduling priority of processes:

- **CPU Utilization**: The amount of time the process uses the CPU, excluding idle periods.
- **Execution Throughput**: The rate at which processes are executed.
- **Responsiveness**: The time taken for processes to complete and the average time spent in different queues.
- **Resource Waiting Time**: The time spent waiting for external resources like I/O devices.

Common scheduling algorithms include:

1. **First Come, First Serve (FCFS)**
2. **Shortest Job First (SJF)**
3. **Round Robin (RR)**
4. **Priority Scheduling** (static/dynamic)

## 2.8 Thread Concepts

- A thread is essentially a lightweight process.
- A process can spawn multiple threads, each of which has its own context (program counter, registers, etc.) and is managed separately by the OS.
- Threads allow for parallel execution within the same process. For instance:
  - In a chat program, sending and receiving messages can occur independently in separate threads.
  - In strategy games, multiple actions happen concurrently, each handled by its own thread.
- Threads can be classified into **user-mode threads** (for applications) and **kernel-mode threads** (for system-level processes). The OS manages the switching between these types of threads when needed.

# 3 Memory Management

### Content Overview:

- Need for Memory Management
- Address Binding
- Logical Address vs. Physical Address
- Inter-process Communication (IPC)
- Shared Memory Method
- Message Passing Method

## 3.1 Need for Memory Management

In systems running multiple programs concurrently, memory usage can become complex, with several processes occupying memory at the same time, each with distinct memory requirements.

Processes typically need memory for:

- **Executable Code**: The program itself must be loaded into memory to be executed.
- **Data**: This includes hardcoded values, variables, and strings that the program will reference during execution.
- **Runtime Memory Requests**: These may arise from the stack or heap, supporting dynamic memory allocation during program execution.
- **OS and Kernel Components**: The operating system and kernel also require memory to operate.
- **Device-Specific Memory**: Certain devices, like printers, may require dedicated memory (e.g., for spooling).

## 3.2 Address Binding

A program is typically loaded into different memory locations each time it is executed, depending on available space at the time of loading.

When a process is in a waiting state (e.g., waiting for I/O), it may be swapped out to virtual memory (secondary storage). When it transitions to the ready state, it may be swapped back into main memory at a different location.

This means that the memory addresses of the program's variables can change many times during execution.

The solution to this problem is **address binding**, which maps a program’s compiled addresses to physical memory addresses.

### 3.2.1 Logical Address vs. Physical Address

- A program’s variables, instructions, and references are initially part of the source code and are referred to as **symbolic addresses**.
- During compilation, these symbolic addresses are converted to **logical addresses** (relative addresses), which are used by the operating system to load the program into memory.
- Since there is often not enough physical memory to hold all programs simultaneously, **virtual memory** is used, which can be mapped to physical memory.
- The **Memory Management Unit (MMU)** is responsible for translating logical addresses (virtual memory addresses) into physical addresses.

## 3.3 Inter-process Communication (IPC)

Communication between processes is often necessary to coordinate their actions or share data.

The OS provides mechanisms for **Inter-process Communication (IPC)**, which typically involves one of two methods:

- **Shared Memory**
- **Message Passing**

### 3.3.1 Shared Memory Method

In the **shared memory method**, two or more processes communicate by creating a shared memory area that both can access.

- One process acts as the **producer** of data, while the other acts as the **consumer**.
- The shared memory acts as a **buffer** between the processes for data exchange.
- This method requires **synchronization** to prevent both processes from accessing the shared memory at the same time, which could lead to data inconsistencies or corruption.

### 3.3.2 Message Passing Method

The **message passing method** involves processes communicating via a predefined communication link, which can be a file system, socket, named pipe, etc.

- The communication link must first be established, such as when a server process waits for a client to connect via a specific port (e.g., using TCP/IP).
- Once the communication channel is set up, the processes exchange messages through defined protocols, using commands like **Send** and **Receive**.
- For successful message passing, both processes must agree on the communication flow and parameters.
- Some operating systems provide **system calls** or **APIs** for sending and receiving data between processes.

# 4 I/O Management

### Content Overview:

- Need for I/O Management
- I/O Subsystem
- I/O Device Categories: Block and Character Devices
- I/O Protocols: Special Instructions, Memory-Mapped I/O, DMA
- Interrupt Handling Mechanisms
- Synchronous vs. Asynchronous I/O
- Synchronization and Critical Sections
- Mutex, Semaphore, and Deadlocks

## 4.1 Need for I/O Management

- Systems connect multiple I/O devices, including human-interface devices (keyboards, displays), storage devices, and networking hardware (Wi-Fi, Ethernet).
- Devices vary in communication protocols, data formats, and speeds.
- The OS abstracts device complexity, providing unified I/O management via protocols and interfaces.

## 4.2 I/O Subsystem

- I/O devices (peripherals) communicate via buses (data, address, control) and protocols (e.g., PCIe, I2C).
- Devices interact with the OS through device drivers, which handle device-specific communication and abstraction.

## 4.3 I/O Device Categories

- **Block Devices**: Handle data in blocks (e.g., flash memory, hard drives).
- **Character Devices**: Handle data one byte at a time (e.g., keyboards, serial ports).

## 4.4 I/O Protocols

- **Special Instruction I/O**: Uses specific CPU instructions for device communication (e.g., embedded controllers).
- **Memory-Mapped I/O (MMIO)**: Devices interact with memory via a predefined address range, enabling high-speed data transfer without CPU intervention.
- **Direct Memory Access (DMA)**: Allows devices to transfer data directly to memory, bypassing the CPU for faster performance.

## 4.5 Interrupt Handling Mechanisms

- **Polling/Programmed I/O**: Periodically checks for interrupts.
- **Interrupt-Driven I/O**: Devices trigger interrupts, and the OS calls specific Interrupt Service Routines (ISRs) based on unique Interrupt Request Numbers (IRQs).

## 4.6 Synchronous vs. Asynchronous I/O

- **Synchronous I/O**: I/O operation blocks the process until complete (e.g., printing).
- **Asynchronous I/O**: I/O operation allows the process to continue while the I/O operation runs in the background (e.g., networking).

## 4.7 Synchronization and Critical Sections

- **Critical Sections**: Shared data accessed by multiple threads may lead to race conditions unless properly synchronized.
- The OS provides mutexes and semaphores to ensure safe access to shared resources.

### 4.7.1 Mutex

- A mutex ensures mutual exclusion, allowing only one thread/process to access a resource at a time.

### 4.7.2 Semaphore

- A semaphore generalizes mutexes, using a counter to control access to critical sections.

## 4.8 Deadlocks

- A deadlock occurs when processes are blocked, each holding a resource and waiting for another, leading to a circular wait.

### Conditions for Deadlock:

1. **Mutual Exclusion**: Resources cannot be shared.
2. **Hold and Wait**: A process holds one resource while waiting for others.
3. **No Preemption**: Resources cannot be forcibly taken.
4. **Circular Wait**: A cycle of waiting processes.

# 5 File Systems

### Content Overview:

- Need for File Systems
- File Concept
- Directory Name Space
- Access Control
- Concurrency

## 5.1 Need for File Systems

Applications rely on file systems for reading, writing, and managing files.

The OS manages files through:

- **Directory Service**: Organizes files, manages access, and provides read/write/edit controls.
- **Storage Service**: Interfaces with underlying hardware (e.g., disks, SSDs).

## 5.2 File Concept

A file is a structured data collection accessed using a unique file ID (filename).

Files vary in format: binary (.bin), executable (.exe), structured (JSON, XML).

Key file attributes include:

- Location
- Size
- Extension
- Access controls
- Operation history

The OS exposes file metadata via APIs or GUI tools.

## 5.3 Directory Name Space

The OS structures files hierarchically within directories for efficient access.

Directories enable file organization and support advanced searches (e.g., size, type, access level).

Modern OSs allow multi-level directory structures for better management.

## 5.4 Access Control

The OS enforces file and directory-level permissions:

- **Read**
- **Write**
- **Modify**

Different users may have distinct access levels to prevent unauthorized modifications.

Access control ensures security, especially in multi-user environments.

## 5.5 Concurrency and Cleanup Control

The OS prevents files from being deleted or moved while in use to maintain consistency.

Proper access modes (**Read/Write**) help avoid conflicts and ensure stable file operations.

Temporary files are managed using OS garbage collection, with settings for automated cleanup.

# 6 Access and Protection

### Content Overview:

- Access and Protection
- User Mode and Kernel Mode (Rings)

## 6.1 Access and Protection

- Even in single-user systems, program resources and critical devices require protection.
- Systems often share data and resources, necessitating security measures.
- The OS enforces access control through APIs, ensuring controlled resource allocation.

## 6.2 User Mode and Kernel Mode (Rings)

- OSs implement privilege separation using execution rings.
- **Ring 0 (Kernel Mode)**: Full hardware access, used by OS and drivers.
- **Ring 3 (User Mode)**: Restricted access, used by applications to prevent unauthorized system modifications.
- Most modern OSs primarily use Rings 0 and 3 for security and stability.

# 7 Virtualization and User Interface & Shells

### Content Overview:

- Virtualization
- Protection
- User Interface and Shell

## 7.1 Virtualization

- **Definition**: Virtualization allows multiple environments to operate as if they have dedicated hardware access.

### Virtual Machines (VMs):

- Each VM runs a guest OS, managed by the host OS through a hypervisor.
- The guest OS operates independently but relies on the host OS for hardware access.

### Advantages of Virtualization:

- Enables running OSs on hardware where they are not natively available.
- Simplifies system setup, backups, and testing.
- Supports running multiple isolated environments on a single machine.
- Facilitates debugging and migration of machines.
- Supports legacy systems.

## 7.2 Protection

### Security Threats:

- Malicious software or unauthorized access can compromise system integrity.

### Authentication & Authorization:

- **Authentication**: Verifies the user's identity.
- **Authorization**: Determines access rights to system resources.

### Access Control Lists (ACLs):

- The OS maintains a list of permissions for different users and processes.

### Encryption & Certificates:

- Enhance system security through encryption and identity verification.

## 7.3 User Interface and Shell

### User Interface (UI):

- The interaction layer between the user and the OS.

#### Graphical User Interface (GUI):

- Provides a visual and interactive way to use the OS.

#### Command-Line Interface (CLI) / Shell:

- A text-based interface used by developers for system interactions.

### Programming Considerations:

- UI choice affects language selection, argument handling, and system interactions.
- Different OSs provide varied UI/CLI features, requiring adaptability in programming.
