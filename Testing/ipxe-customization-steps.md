# iPXE Customization

The Default ipxe.iso from https://boot.ipxe.org/ipxe.iso will will not meet the requirements for this effort and needs to be customized.  Here are the steps:

1. Find or build an amd64 or x86_64 Rocky machine.  I used an Ubuntu VM and created a Docker image for rocky-latest.
2. From the command line on Rocky, follow the steps on https://ipxe.org/download to clone the ipxe git repo (iPXE's source code) and download necessary packages needed for the compilation of iPXE.
