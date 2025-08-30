# Operating-System
Building the basic Operating Operating Kernel
Currently in Used Languages: CPP, Makefile, x86-64 Assembly.
The current Project Version only contains the following file:
1. Loader.s
2. Linker.ld
3. kernel.cpp
4. Makefile

Add The following command inside the file in directory /boot/Grub/Grub.cfg to run this kernel:

"### Starting My OS ###
menuentry 'lassanOS'{
        multiboot /boot/mykernel.bin*
        boot
}
### End MY OS ###"
