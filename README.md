# LateRegistration

A Linux Kernel Snapshot Fuzzer using KVM.

This fuzzer allows us to run snapshot instances of the linux kernel for use in fuzzing. This allows us incredible
performance and determinism since we can control what gets executed inside the kernel and know about it. Performance has
been possible because of the [Kernel Virtual Machine](https://www.linux-kvm.org/page/Main_Page) (KVM). A bootloader
allows us to boot linux from start, create the snapshot, fuzz, and restore all in KVM.

## Usage

`./LateRegistration <bzImage> <initrd>`

## Future Plans

* Guest Memory Access System
    * An API to access and modify vm memory. Useful for the breakpoint system
* Breakpoint System
    * We place a breakpoint at the start of all kernel basic blocks. This allows us to track if we're hitting new kernel
      code
    * Breakpoints feed by file with a format provided in a python script that uses Binary Ninja
* Syscall Fuzzing
    * Basic version of syscall fuzzing
        * Likely restricted set because of parameters and structs
