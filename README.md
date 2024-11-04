# Hardened MINIX 3 with Zig-Enhanced musl libc
## Overview
This project refactors the MINIX 3 operating system with a hardened version of musl libc that includes security-enhanced functions implemented in Zig. By leveraging Zig’s safety features and modern syntax, this project aims to improve memory safety, error handling, and performance resilience in MINIX’s libc, creating a secure foundation for critical and embedded systems.

## Project Goals
Enhanced Security: Improve the robustness of MINIX 3 by replacing high-risk functions (such as string and memory manipulation functions) in libc with safer implementations in Zig.
Hybrid C-Zig Library: Maintain compatibility with standard C code in musl, while integrating Zig-based functions to provide added bounds checking, memory protection, and safer error handling.
Real-World Demonstration: Showcase the security improvements in a bootable MINIX 3 system, with demonstrations of vulnerability mitigations and performance benchmarks.

## Key Features
1. **Refactored musl libc**: Critical libc functions have been reimplemented or wrapped in Zig, such as `strcpy`, `memcpy`, `malloc`, and `free`, to incorporate safety features:
   
   * **Bounds Checking**: Functions like `strcpy` are replaced with `safeStrcpy`, a bounds-checked version that prevents buffer overflows.
   * **Memory Management**: Functions like `malloc` and `free` include security checks for buffer overflows and guard canaries to detect memory corruption.
   * **Improved Error Handling**: Enhanced error reporting for functions prone to misuse, ensuring safer operation in the OS.

2. **Security Focus**:

   * Protection against buffer overflows and use-after-free vulnerabilities.
   * Custom memory allocation strategies using Zig’s allocator capabilities.
   * Fuzz-tested functions to ensure resilience against malformed or malicious inputs.

3. **Seamless MINIX Integration**: The hardened libc is fully integrated into MINIX 3’s build system, replacing the standard libc. The result is a MINIX 3 image that runs with the security-enhanced library by default.

## Testing and Validation
### Basic Functionality Tests
Run basic commands and system calls in MINIX 3 to ensure compatibility with the new libc.

### Security Demonstrations
* **Buffer Overflow Mitigation**: Run tests with oversized inputs on string functions to confirm bounds-checking behaviour.
* **Memory Management Resilience**: Test memory allocation and deallocation functions to prevent double-free and detect use-after-free vulnerabilities.
* **Error Handling Examples**: Demonstrate safe error handling in I/O functions, such as safeScanf and `safeFgets`, showing how they handle malformed input securely.

### Performance Benchmarks
Benchmark enhanced functions against standard musl implementations to evaluate any performance impact from the additional safety checks.

## Documentation
* **Function Reference**: Detailed overview of each refactored function, including security enhancements.
* **Security Analysis**: In-depth analysis of how Zig’s safety features contribute to the overall security of MINIX.
* **Design Decisions**: Rationale for using Zig in specific `libc` functions and explanation of trade-offs made during refactoring.

## Future Enhancements
* **Expanded Zig Refactoring**: Additional `libc` functions in musl could be further enhanced with Zig’s safety features.
* **Community Feedback and Iteration**: Collect feedback on the hardened libc’s functionality and performance for further improvements.
* **Embedded System Applications**: Adapt the hardened MINIX 3 for embedded systems where security and resilience are critical.

## License
This project is licensed under the MIT License. See LICENSE for details.
