# CASUAL
1. Just as a photograph represents the reality exactly as it was when shooting, an image of an executable program (or kernel) represents the program in a state, where it can be loaded (or unpacked) in the systems memory exactly as it is and then given control to it. That program can then start running from that state in a consistent manner. So the Linux kernel image is an image (a picture of the state) of the Linux kernel that is able to run by itself after giving the control to it. The bootloader loads such an image from the hard disk’s filesystem (driver is needed), replaces itself with it and so gives the control to it.
	- (KEY: Kernel, Image, Bootloader)
	- (REF: https://unix.stackexchange.com/questions/208407/why-is-the-linux-kernel-called-an-image)
	- (CONCLUSION: **Image** is a snapshot of memory)

2. The BIOS loads the bootloader that is also an image, for example called boot.img in case of grub. That boot.img is not a file (if grub is installed); it is the name for the part that is in the Master Boot Record (MBR). If you dump that to a file it would then be an image in form of a file not rawly written to disk, but rawly written in a file. This is also a representation (image) of the earliest state where grub is able to load the rest of itself. grub then has its own mechanism how to fully load itself by loading other images. This is represented by the different stages in grub. After that, the bootloader loads the kernel image by replacing itself with the extracted contents of that file.
	- (KEY: Bootloader, boot.img, grub)
	- (REF: https://unix.stackexchange.com/questions/208407/why-is-the-linux-kernel-called-an-image)
