# 🖥️ Operating System (Kernel Project)

This repository is a **from-scratch operating system kernel project** created for learning purposes.  
It demonstrates the fundamentals of how an operating system boots, switches to protected mode,  
and runs a minimal C++ kernel after being loaded by GRUB.

> Think of this as a "Hello World" for OS development — small, simple, but powerful in showing  
> how high-level C++ code can run directly on bare metal hardware without an underlying OS.

---

## ✨ Features (Current Version)
- A **multiboot-compliant kernel** that GRUB can load.
- Written in **C++**, **x86-64 Assembly**, and linked with a **custom linker script**.
- A very **minimal but functional build system** using `Makefile`.
- Outputs text to the screen once the kernel is running.

**v1** is intentionally simple — the focus is on understanding the **bootstrapping process**,  
not building a full OS just yet.

---

## Structure

| File         | Purpose                                                                 |
|--------------|-------------------------------------------------------------------------|
| `Loader.s`   | Assembly bootstrap that sets up the environment for the kernel.         |
| `Linker.ld`  | Linker script that defines memory layout for the kernel binary.         |
| `kernel.cpp` | Entry point of the kernel, written in C++.                              |
| `Makefile`   | Build instructions for compiling and linking everything together.       |

---

## ⚙️ Building the Kernel

Clone the repository and run the following in the project directory:

```bash
make loader.o
make kernel.o
make mykernel.bin
make install
