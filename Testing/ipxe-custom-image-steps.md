# iPXE custom image steps

The Default ipxe.iso from https://boot.ipxe.org/ipxe.iso will will not meet the requirements for this effort and needs to be customized.  Here are the steps:

1. Find or build an amd64 or x86_64 Rocky machine.  I used an Ubuntu VM and created a Docker image for rocky-latest.
2. From the command line on Rocky, follow the steps on https://ipxe.org/download to clone the ipxe git repo (iPXE's source code) and download necessary packages needed for the compilation of iPXE.
3. Edit the ipxe/src/config/general.h file and make these changes:
```/* Protocols supported on all platforms */
#undef NET_PROTO_EAPOL		/* EAP over LAN protocol */
//#define NET_PROTO_FCOE	/* Fibre Channel over Ethernet protocol */
#define NET_PROTO_IPV4		/* IPv4 protocol */
#define NET_PROTO_IPV6		/* IPv6 protocol */
#define NET_PROTO_LACP		/* Link Aggregation control protocol */
#define NET_PROTO_LLDP		/* Link Layer Discovery protocol */
#define NET_PROTO_STP		/* Spanning Tree protocol */
```
5.  Create a customized iPXE Script to be used to embed into the ISO.  Name it `slaacifconf.ipxe`  (Basic process referenced here https://ipxe.org/scripting).  This script loops through all the interfaces until an SLAAC IPv6 address has been assigned succesfully via the upstream router.  It then reaches out to a hardcoded IPv6 destination for its base `baseipxe.cfg`.  $$\color{red}{This \ is \ likely \ the \ only \ stuff \ that \ will \ be \ hardcoded \ as \ part \ of \ this \ design.}$$  A DNS name would be ideal, but time didn't allow for that testing.
```
#!ipxe
# Label to retry if the initial attempt fails
:loop
# ifconf will automatically try all interfaces and configurators (e.g., ifconf || goto loop
ifconf || goto loop

# Once configuration succeeds, the script proceeds
echo Successfully configured network interface ${netX/ifname} !
echo ${netX/ifname} MAC Address: ${netX/mac}
echo ${netX/ifname} IPv6 Address: ${netX/ip6}

# Chainload the base iPXE configuration file
chain http://[<IPv6_Webserver_IP>]/baseipxe.cfg
```
5. Embed the script into the image.  Process here https://ipxe.org/embed.
```make bin-x86_64-efi/ipxe.iso EMBED=slaacifconf.ipxe```
6. Assuming compilation is successful, proceed to use this `ipxe.iso` as a bootable image via virtual CD ROM.
