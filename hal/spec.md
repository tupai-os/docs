
# HAL - Specification `0.1.0`

Here follows a specification containing details of what modules, structures and functions must be provided by a compliant HAL.

|-- `module: isa` Provides Instruction Set Architecture features
    |-- `module: simd` Provides support for Single Instruction Multiple Data (SIMD)
	|-- `module: fp` Provides support for IEEE-754 floating point arithmetic
|-- `module: irq` Provides support for an interrupt-driven architecture
    |-- `function: enable()` Enables interrupts on the current CPU
	|-- `function: disable()` Disables interrupts on the current CPU
	|-- `function: halt()` Temporarily halts execution on the current CPU
|-- `module: mem` Provides support for memory isolation, protection and address translation
    |-- `constant: PAGE_SIZE` Determines the size, in kilobytes, of a single address translation unit
