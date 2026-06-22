# BaseOS (Base Operating System)
Pre-Prod BaseOS for MaaS-like initiatives.

## Requirements
-  Flatcar Operating System - Immutable - Ephemeral - Stateless
-  UEFI Support
-  TPM (Trusted Platform Module) Support
-  Intel TXT (Trusted Execution Technology) Support
-  SLAAC IPv6 for Data Interfaces
-  No PXE
-  No DHCP

## Goals
-  Build a lightweight image that requires minimal environmental configuration to load quickly and do discovery and inventory tasks.
-  Enable a framework for container workloads to be layered in over time, to possibly include cabling checks, hardware checks, health checks, firmware updates, etc.
-  Enable base shell of an OS that can be accessible on the network with minimal configuration.
-  Create simple chainload-like bootstrap design flexible enough to handle an environment that is in infant stages of configuration or has been fully configured for production.
-  Proof of Concept "patching" using kexec on Flatcar with Ignition.  Upgrade Kernels without Reboot to reduce downtime.

## Process Flow
```mermaid
sequenceDiagram
    participant Builder as Build System
    participant BMC as BMC / iDRAC
    participant iPXE as iPXE
    participant Net as Router (SLAAC)
    participant Cfg as Web Server
    participant Kernel as Flatcar Kernel
    participant Systemd as Systemd

    Builder->>Builder: Embed iPXE script into iPXE ISO
    Builder->>Cfg: Upload custom iPXE ISO
    BMC->>Cfg: Fetch custom iPXE ISO
    Cfg-->>BMC: Custom iPXE ISO returned
    BMC->>iPXE: Mount Virtual CD-ROM & boot iPXE custom image
    iPXE->>Net: SLAAC — request IPv6 address
    Net-->>iPXE: IPv6 address assigned
    iPXE->>Cfg: Fetch Base iPXE config
    Cfg-->>iPXE: Base iPXE config returned
    iPXE->>Cfg: Fetch final OS config else Discovery config
    Cfg-->>iPXE: final OS config or Discovery config returned
    iPXE->>Kernel: Boot Flatcar kernel
    Kernel->>Net: SLAAC — request IPv6 address
    Net-->>Kernel: IPv6 address assigned
    Kernel->>Cfg: GET Ignition config
    Cfg-->>Kernel: Ignition config returned
    Kernel->>Systemd: Apply Ignition & run systemd
```
