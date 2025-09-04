GCCPARAMS = -m32 -fno-use-cxa-atexit -nostdlib -fno-builtin -fno-rtti -fno-exceptions -fno-leading-underscore
ASPARAMS = --32
LDPARAMS = -melf_i386
objects = loader.o kernel.o

%.o: %.cpp
	gcc $(GCCPARAMS) -c -o $@ $<

%.o: %.s
	as $(ASPARAMS) -o $@ $<

mykernel.bin: linker.ld $(objects)
	ld $(LDPARAMS) -T $< -o $@ $(objects)

#test by booting it as a standalone kernel
install: mykernel.bin
	sudo cp $< /boot/mykernel.bin


#or test it in virtual machine
mykernel.iso: mykernel.bin
	mkdir iso
	mkdir iso/boot
	mkdir iso/boot/grub
	cp $< iso/boot/
	echo 'set timeout=0' >> iso/boot/grub/grub.cfg
	echo 'set default=0' >> iso/boot/grub/grub.cfg
	echo '' >> iso/boot/grub/grub.cfg
	echo 'menuentry "garlicOS" {' >> iso/boot/grub/grub.cfg
	echo '	multiboot /boot/mykernel.bin' >> iso/boot/grub/grub.cfg
	echo '	boot' >> iso/boot/grub/grub.cfg
	echo '}' >> iso/boot/grub/grub.cfg
	grub-mkrescue --output=$@ iso
	rm -rf iso

# depends on type of hypervisor you use, we suggest vmware for better performance 
# you can use virtual box as well, just uncomment the lines
run: mykernel.iso
# 	(killall VirtualBox && sleep 1) || true
# 	VirtualBox --startvm "Your vm name" &
	-(vmrun stop /home/vansh/vmware/MS-DOS/MS-DOS.vmx nogui || true)
	sleep 1
	vmrun start /home/vansh/vmware/MS-DOS/MS-DOS.vmx
