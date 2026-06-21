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
    participant BMC as BMC / iDRAC
    participant iPXE as iPXE
    participant Net as Network (SLAAC)
    participant Cfg as Config Server
    participant Kernel as Flatcar Kernel
    participant Systemd as Systemd

    BMC->>iPXE: Mount Virtual CD-ROM & boot iPXE custom image
    iPXE->>Net: SLAAC — request IPv6 address
    Net-->>iPXE: IPv6 address assigned
    iPXE->>Cfg: Fetch baseipxe.cfg
    Cfg-->>iPXE: baseipxe.cfg returned
    iPXE->>Cfg: Fetch discovery_ipxe.cfg
    Cfg-->>iPXE: discovery_ipxe.cfg returned
    iPXE->>Kernel: Boot Flatcar kernel
    Kernel->>Net: SLAAC — request IPv6 address
    Net-->>Kernel: IPv6 address assigned
    Kernel->>Cfg: GET Ignition config
    Cfg-->>Kernel: Ignition config returned
    Kernel->>Systemd: Apply Ignition & run Systemd
```
