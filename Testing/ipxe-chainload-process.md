#iPXE Chainload Process - Multiple Configurations

1. It will attempt to chainload a `baseipxe.cfg` file which has logic to load unique provisioning templates from unique provisioning systems OR if that fails, iPXE will chainload to the static `discovery_ipxe.cfg` ipxe script.  See example `baseipxe.cfg` script below:
```
#!ipxe
chain http://[<IPv6_Webserver_IP>]/hosts/ipxe-${netX/mac}.cfg || goto try_fallback

# Fallback section (processed if the primary file fails)
:try_fallback
echo Primary iPXE file for Final OS isn't present (yet). Trying discovery image as a fallback plan...
chain http://[<IPv6_Webserver_IP>]/discovery_ipxe.cfg
```
2. For the purposes of this baseOS effort, we focused on the path to load the discovery_ipxe.cfg, which would be during pre-prod deployment in theory.  The example `discovery_ipxe.cfg` script is below:
```
#!ipxe
kernel http://[IPv6_Webserver_IP]/flatcar/flatcar_production_pxe.vmlinuz rootdev0=/dev/nvme0n1 rootvol=/dev/nvme0n1p1 flatcar.first_boot=1 initrd=flatcar_production_pxe_image.cpio.gz rd.neednet=1 flatcar.config.url=http://[IPv6_Webserver_IP]/discovery_ignition.json
initrd http://[IPv6_Webserver_IP]/flatcar/flatcar_production_pxe_image.cpio.gz
boot
```
