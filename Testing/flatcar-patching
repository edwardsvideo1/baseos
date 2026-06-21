#  Flatcar "Patching Process" with kexec
Normally on Container platforms with Flatcar, patching is done by updating configuration files to point to a kernel versions and/or ignition templates and rebooting.  In a multi-site, multi-cluster environment with thousands of nodes, the hope is to get faster with kexec.  Here are the steps used for this test:
1. Stage the updated kernel and initrd in `/tmp/` on the node.  This could be done via ansible, systemd unit, curl or other various methods.
