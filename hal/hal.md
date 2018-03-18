# HAL - Hardware Abstraction Layer

To improve portability, Tupai implements the notion of a Hardware Abstraction Layer (HAL). This is a specification that provides an abstract interface that allows the rest of the OS to access hardware without requiring architecture-specific specialization.

As a result, the HAL guarantees that any platform that may act as a target for Tupai porting implements certain minimum features and therefore provides strict definitions for which platforms Tupai may or may not run on. Note that it is possible for many of these features to be emulated, and as such Tupai may also run within environments that implement the HAL even if the underlying hardware is not strictly HAL-capable. In general, Tupai's HAL assumes the existence of the following features at a minimum:

- Interrupts and interrupt-driven I/O
- Page-based memory isolation, protection and virtual address translation
- A minimum of 2 execution privilege levels
- Von Neumann memory architecture
- Linearly addressable memory

Additional features may be provided by the HAL, but are not a requirement for the execution of Tupai's core systems.

## Implementation

Tupai's HAL is defined as a series of Rust library interfaces separated into modules. They are:

- `isa`: Provides access to instruction-level features such as SIMD, division, floating-point support, etc.
- `irq`: Provides access and support for interrupts and exceptions
- `mem`: Provides access and support for hardware-driven memory isolation, protection and virtual address translation
- `bus`: Provides support for hardware device enumeration and device access

## Purpose

The primary objective of the HAL is to keep code that is not portable to a minimum and to make porting to other platforms in the future significantly easily. In essense, a platform should be considered 'supported' if it implements the minimum requirements of the HAL. 'Port the HAL, get the rest free' is the overarching goal.
