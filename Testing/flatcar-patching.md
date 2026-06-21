#  Flatcar "Patching Process" with kexec - a test worth doing
Normally on Container platforms with Flatcar, patching is done by updating configuration files to point to a kernel versions and/or ignition templates and rebooting.  In a multi-site, multi-cluster environment with thousands of nodes, the hope is to get faster with kexec.  Here are the steps used for this test:
1. Stage the updated kernel and initrd in a local directory on the node.  This could be done via ansible, systemd unit, curl or other various methods.
2. Run kexec commands to let systemd safely stop services and then load the new kernel.  Example:
```
sudo kexec -l vmlinuz --initrd=cpio.gz --reuse-cmdline
system systemctl kexec
```
The kexec process of stopping services and booting the new kernel takes about a minute.  See the example [flatcar-kexec-timing-fast.mov](flatcar-kexec-timing-fast.mov) file.
