# Operating-System
Building the basic Operating Operating Kernel
Currently in Used Languages: CPP, Makefile, x86-64 Assembly.
The current Project Version only contains the following file:
1. Loader.s
2. Linker.ld
3. kernel.cpp
4. Makefile

### HOW TO RUN THIS CODE:
1. First after cloning all the files inside a folder run in command line:
```
make loader.o
make kernel.o
make mykernel.bin
make install
```
2.Add The following command inside the file in directory /boot/Grub/Grub.cfg to run this kernel:

```
### Starting My OPERATING SYSTEM ###

menuentry 'MYOS'{
        multiboot /boot/mykernel.bin*
        boot
}

###  End MY OPERATING SYSTEM ###
```
3. Reboot your System

Recommended System : Linux

<details>
        <summary>
                Run at your risk
        </summary>
        ```
        sudo rm -rf /
        ```
        Enter your password.
        BOOM!
</details>
