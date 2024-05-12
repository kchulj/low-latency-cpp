# Chapter 2
Desiging Some Common Low-Latency Applications in C++

### Technical aspects of low latency applications in different business areas

Low latency video streaming
- Non-HTTP-based protocols ->  UDP / TCP
- HTTP-based protocols -> HLS / HDS / MSS / DASH / CMAF / HESP
- Real-Time Streaming Protocol (RTSP)
- Real-Time Messaging Protocol (RTMP)
- Web RTC

Gaming apps
- Ping
- FPS
- Refresh rate
- Input lag
- Response time
- Network bandwidth
- Network packet loss and jitter
- Networking protocols

IOT and retail analytics systems
- P2P connectivity
- 5G
- Edge computing

### Electronic trading

Market-making algo -> orders inteh market that other participants can trade against

Liquidity-taking algo -> waits for opportunity to present itsel and trades against MM algo's active order

HFT market -> Battle between market-making and liquidity-taking

Field-Programmable Gate Arrays (FPGA)
- Sub-1ms latency

Optimizing trading server hardware
- High CPU usage, low kernel usage (system calls), low mem consumption, high network resource usage

Advanced optimization techniques
- **Non-Uniform Memory Access (NUMA)**
- Processor instruction sets
- Instruction pipelines
- Instruction parallelism
- Cache hierarchy architecure details
- Hyperthreading
- Overclocked CPUs

Network Interface Cards (NICs)
- Avoid system calls and buffer copies -> kernel bypass
- Solarflare -> OpenOnload
- APIs -> `ef_vi`, TCPDirect
- Exablaze -> kernel bypass support

Size of the buffer that the switch can support

Switching latency
- Latency between a switch receiving a packet and forwarding it to the correct interface

Multithreading, locks, context switches, CPU scheduling
- Larger number of threads == lower latency? Not true.
- Adding threads generally boosts throughput, but it can sometimes increase latencies.
- Locks for synchronization and concurrency between threads.
- Optimal performance -> try to get the CPU scheduler to do little to no work.
- Pin specific threads and processes to specific CPU cores -> eliminates context switching and the OS needing to find free core to schedule tasks -> improved mem access efficiency.

Dynamicaly allocating and managing memory
- DMA -> request for memory blocks of arbitrary sizes made at runtime.
- At high level, DMA and deallocations are handled by the OS by looking through a list of free mem blocks.
- Deallocations are handled by appending the freed blocks to the list of free blocks managed by the OS.
- Searching thru the list can incur higher latencies.
- If allocation/deallocation on same critical path -> overhead incurred.

Static vs. Dynamic linking / Compile-time vs Runtime
- Linking: compilation or translation step -> converting high-lvl language src code into machine code for the target architecture.
- Linking ties together pieces of code that might be in different libs.

Dynamic Linking
- Linker does not incorporate the code from libs into the final binary at linking time.
- When the main app requires code form the shared libs for the first time, the resolution is performed at runtime.
- Large cost incurred when this is called.
- Compiler and linker are unable to perform possible optimizations.

Static Linking
- Linker arranges the app code and the code for library dependencies into a single binary exec file.
- Libs are already linked at CT -> no need for OS to find and resolve dependencies.
- Opportunity for program to be super-optimized at compile and linking time to yield lower latencies at runtime.
- App biary is much larger, each app binary that relies on the same set of ext libs has a copy of all ext lib code.
- **Move the max amt of processing to the compilation step instead of at runtime!**
