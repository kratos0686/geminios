# Geminios Development Container

This dev container provides a complete development environment for Geminios OS development.

## What's Included

### Compilers & Build Tools
- GCC and G++ (latest)
- Clang and LLVM
- Make, CMake, Ninja
- Autotools (autoconf, automake, libtool)

### Cross-Compilation Support
- ARM 32-bit toolchain (gcc-arm-linux-gnueabihf)
- ARM 64-bit toolchain (gcc-aarch64-linux-gnu)

### Kernel Development Tools
- Linux headers
- Essential kernel build dependencies (libelf, libssl, flex, bison)

### Debugging Tools
- GDB and LLDB debuggers
- Valgrind for memory debugging
- Strace for system call tracing

### VS Code Extensions
- C/C++ IntelliSense
- CMake Tools
- Makefile Tools
- Hex Editor
- Docker support

## Getting Started

1. Open this repository in GitHub Codespaces or VS Code with Dev Containers extension
2. Wait for the container to build (first time only)
3. Start developing!

## Building Geminios

```bash
# Your build commands will go here
# Example:
# make all
# or
# cmake -B build && cmake --build build
```

## Useful Commands

```bash
# Check compiler versions
gcc --version
clang --version

# Check available cross-compilers
arm-linux-gnueabihf-gcc --version
aarch64-linux-gnu-gcc --version

# List installed tools
dpkg -l | grep -E 'gcc|make|cmake'
```

## Customization

Edit `.devcontainer/devcontainer.json` and `.devcontainer/Dockerfile` to add or modify tools and settings.