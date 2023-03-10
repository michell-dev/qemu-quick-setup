# QEMU Quick Setup.
A quick setup guide for virtualization on Linux with kvm/qemu.


##### Package Installation:
```
Arch: sudo pacman -S qemu (optionally "qemu-arch-extra" for more architectures)
Debian/Ubuntu: sudo apt install qemu
Fedora: sudo dnf install qemu
```
##### Create a virtual image using:
```
qemu-img create -f qcow2 Image.img 10G
```
<sub>**create** is to create an image, **-f qcow2** sets the format to qcow2, Image.img is our final file and 10G is it's size</sub>

##### Launching the VM:
```
qemu-system-x86_64 -enable-kvm -cdrom OS_ISO.iso -boot menu=on -drive file=Image.img -m 2G
```
<sub>**-enable-kvm** enables KVM, **-cdrom** selects an iso to load as a cd, **-boot menu=on** enables a boot menu, **-drive file=** selects a file for the drive, **-m** sets the amount of dedicated RAM</sub>

##### Additional Options:
```
-cpu host -smp 2
```
<sub>**-cpu host** (sets the CPU to the hosts' CPU) **-smp 2** (sets the numbers of cores) </sub>

```
-vga virtio -display sdl,gl=on
```
<sub>the **-vga** option can be used to specify one of various vga card emulators: **qxl** (requires kernel modules: "qxl" and "bochs_drm") for 2D acceleration or **virtio** which is better and supports some 3D emulation.</sub>
