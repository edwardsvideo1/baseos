## Results
Flatcar doesn't support UEFI by default.  Today in Production, this is achieved by using iPXE as a bootloader, which bypasses limitations of flatcar's EFI support.
- NoGo - If using the Virtual CDROM approach via Out-of-Band (OOB) for the full image install, UEFI isn't supported by default.  CoPilot + Claude was used to help achieve this goal and I was never able to get it to work with TPM Enabled.
- NoGo - If using UEFI HTTP Boot with grubx64.efi method of loading kernel + initrd, TPM enabled looks to limit the memory for Flatcar's kernel.  Disabling TPM eliminates this error:
  <img width="1258" height="506" alt="image" src="https://github.com/user-attachments/assets/812c131f-4458-4ee4-bce9-27cf101046a4" />
- NoGo - If using UEFI HTTP Boot with ipxe.efi method of loading kernel + initrd, SLAAC does assign the IPv6 addresses, but since there's no way to configure the MTU in UEFI HTTP Boot mode, the ipxe.efi file download fails.  Production router configs require MTU of 9100 and it appears UEFI Firmware is defaulting to 1500 with no easy way to override.
- Go - If using a customized ipxe.iso (about 2MB) mounted via Virtual CDROM, SLAAC, TPM, Intel TXT, UEFI are all supported and Flatcar proceeds without any customized image tweaks.
