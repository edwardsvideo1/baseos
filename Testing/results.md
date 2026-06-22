## Results
Note:  All testing for this effort thus far was on the Dell R660 hardware platform.  Detailed Hardware/Firmware information [here](dell-r660.md): 

### Flatcar OS Versions
| OS | Release | kernel | containerd | docker | ignition | kernel | systemd |
| - | - | - | - | - | - | - | - |
| 4081.3.8 | LTS | 6.6.141-flatcar | 1.7.21 | 26.1.0 | 2.19.0 | 6.6.141 | 255 |

Flatcar doesn't support UEFI by default.  Today in Production, this is achieved by using iPXE as a bootloader, which bypasses limitations of flatcar's EFI support.
- $$\color{red}{FAILED}$$ - If using the Virtual CDROM approach via Out-of-Band (OOB) for the full image install, UEFI isn't supported by default.  CoPilot + Claude was used to help achieve this goal and I was never able to get it to work with TPM Enabled.
- $$\color{red}{FAILED}$$ - If using UEFI HTTP Boot with grubx64.efi method of loading kernel + initrd, TPM enabled looks to limit the memory for Flatcar's kernel.  Disabling TPM eliminates this error:
  <img width="1258" height="506" alt="image" src="https://github.com/user-attachments/assets/812c131f-4458-4ee4-bce9-27cf101046a4" />
- $$\color{red}{FAILED}$$ - If using UEFI HTTP Boot with ipxe.efi method of loading kernel + initrd, SLAAC does assign the IPv6 addresses, but since there's no way to configure the MTU in UEFI HTTP Boot mode, the ipxe.efi file download fails.  Production router configs require MTU of 9100 and it appears UEFI Firmware is defaulting to 1500 with no easy way to override.  There could be more testing on this as well, but time did not permit.
- $$\color{green}{PASSED}$$ - If using a customized ipxe.iso (about 2MB) mounted via Virtual CDROM, SLAAC, TPM, Intel TXT, UEFI are all supported and Flatcar proceeds without any customized image tweaks.  Successful Screenshot with these configs and process working successfully:
  <img width="795" height="483" alt="Screenshot 2026-06-21 at 7 32 07 PM" src="https://github.com/user-attachments/assets/bd62ffb8-6135-4b3d-9dd9-ceb613ec33d3" />
- $$\color{red}{FAILED}$$ - Secureboot for all scenarios.  This might be a limitation of Flatcar, but it might also be a limitation of grub and iPXE as well.  Below is a snapshot of the error when using iPXE.
  <img width="799" height="84" alt="Screenshot 2026-06-21 at 7 41 50 PM" src="https://github.com/user-attachments/assets/f116c2c9-5cf3-4ac5-86fe-d9eddb5c8a28" />

