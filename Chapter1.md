# Chapter 1
Introducing Low-latency Application Development in C++

### What is latency?
Latency is the time delay between when a task is started to the time when it is finished.

Latency-sensitive: as performance latencies are reduced, it improves the business impact or profitability.


Latency-critical: fails completely if performance latency is higher than a certain threshold.

Example:

T<sub>1</sub> -> Time server puts first byte of packet.

T<sub>2</sub> -> Time client reads first byte of packet.

T<sub>3</sub> -> Time client puts a packet containing a response.

T<sub>4</sub> -> Time server reads first byte of packet containing the response.

### Measuring Latency

**Time to first byte**: T<sub>4</sub> - T<sub>3</sub>

**Round-trip time (RTT)**: Sum of the time it takes for a packet to travel from one process to another, then the time it takes for the response packet to reach the original process.

**Tick-to-trade (TTT)**: Time from when a packet first hits a participant's infrastructure -> time when the participant is done processing and sents a packet out.

T<sub>3</sub> - T<sub>2</sub>

**CPU clock cycles**: Smallest increment of work that can be done by the CPU processor.

### Why C++?

Compiled language
- Source code is translated into a machine code binary.
- != interpreted languages, runs through the source line by line and executes each cmd.
- Speed: compiled > interpreted.
- Control over hardware - memory mgmt, CPU, cache, etc. 

Closer to hardware, low-level
- Direct access to memory and objects in memory.

Deterministic usage of resources
- Explicit creation, mgmt, deallocation of memory resources.
- Java and Python rely on automatic garbage collection.

Speed and high performance
- Concurrency and multithreading support.
- Compile-time optimization ability.
- Pre-processor directives, `constexpr` specifier.
- Move processing to compilation step -> minimize work done during runtime.

### Language constructs and features

Portability
- Compatible with different OS, platforms, CPU architectures, etc.
- Just build correct binaries at compile time.

Compiler optimizations
- Compiled language -> no additional runtime costs.
- Analyze all objects and code paths -> high levels of optimization at compile times.
- Directly inline assembly code -> greater chance to work with the compiler.

Statically typed
- Statically typed language -> performs checks around datatypes during compilation.
- Dynamically typed language -> during runtime.
- Eliminate bugs before the program is run.
- Additional opportunity for compiler to optimize the types and type interations at compile time.

Multiple paradigms
- Support for different programming paradigmes, e.g. OOP.

### Libraries

Standard Template Library (STL)
- Data structures and containers, algorithms.

Boost
- Multithreading, network ops, image processing, reges, linear algebra, unittesting, etc.

Asio (asynchronous input/output)
- Support for multithreading concurrency.
- Implementing and using asynchronous I/O.

GNU Scientific Library (GSL)
- Mathematical concepts and operations.
- Complex numbers, matrices, calculus, etc.

Active Template Library (ATL)
- Help program the Component Object Model (COM).
- Replaces Microsoft Foundation Classes (MFC).

Eigen
- Mathematical and scientific applications.

LAPACK (Linear Algebra Package)
- Linear algebra and linear equations, large matrices.
- Simultaneous linear equations, LSM, eigenvalues, SVD, etc.

OpenCV
- Computer graphics and vision-related apps.

mlpack
- ML models and mathematical ops.

QT
- Cross-platform graphical programs, GUI.

Crypto++
- Algorithms, operations, utilities for cryptography.
- Rand number generators, block ciphers, functions, pubkey ops, secret sharing, etc.

### Development

C++ is 40 years old.

C++ 98, C++ 03, C++ 0X, C++ 11, C++ 14, C++ 17, C++ 20

Most recent is C++ 23
