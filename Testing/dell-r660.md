# Dell R660 Hardware Platform
The following hardware inventory components and firmware versions were used for this test effort:

## BIOS System

| Property | Value |
| --- | --- |
| Manufacturer | Dell Inc. |
| Model | PowerEdge R660 |
| Form Factor | 1U |
| Generation | 16G Monolithic |
| CPU Sockets | 2 populated / 2 max |
| DIMM Slots | 16 populated / 32 max |
| PCIe Slots | 2 populated / 3 max |
| Total Memory | 524,288 MB (512 GB) |
| Max Memory Capacity | 12,582,912 MB (~12 TB) |
| Memory Mode | OptimizerMode |
| Memory ECC | Multi-bit ECC |
| Power Cap | 340W (disabled) |

## Processors

| Socket | Model | Cores | Threads | Base Clock | Max (Turbo) Clock | Hyper-Threading | Turbo Mode |
| --- | --- | --- | --- | --- | --- | --- | --- |
| CPU.Socket.1 | Intel(R) Xeon(R) Gold 6430 | 32 | 64 | 2100 MHz | 4000 MHz | Yes | Yes |
| CPU.Socket.2 | Intel(R) Xeon(R) Gold 6430 | 32 | 64 | 2100 MHz | 4000 MHz | Yes | Yes |

## Memory DIMMs

| Socket | Manufacturer | Type | Size | Rated Speed | Operating Speed | Rank | CPU Affinity |
| --- | --- | --- | --- | --- | --- | --- | --- |
| DIMM.Socket.A1 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 1 |
| DIMM.Socket.A2 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 1 |
| DIMM.Socket.A3 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 1 |
| DIMM.Socket.A4 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 1 |
| DIMM.Socket.A5 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 1 |
| DIMM.Socket.A6 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 1 |
| DIMM.Socket.A7 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 1 |
| DIMM.Socket.A8 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 1 |
| DIMM.Socket.B1 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 2 |
| DIMM.Socket.B2 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 2 |
| DIMM.Socket.B3 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 2 |
| DIMM.Socket.B4 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 2 |
| DIMM.Socket.B5 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 2 |
| DIMM.Socket.B6 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 2 |
| DIMM.Socket.B7 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 2 |
| DIMM.Socket.B8 | Hynix Semiconductor | DDR5 RDIMM | 32768 MB | 4800 MHz | 4400 MT/s | Double Rank | CPU 2 |

## Disks

### Disk Controllers

| Controller | Description | Product | Manufacturer | PCIe Speed | Encryption |
| --- | --- | --- | --- | --- | --- |
| AHCI.Embedded.1-1 | Embedded AHCI 1 | Sapphire Rapids SATA AHCI Controller | DELL (Intel) | N/A | Not Capable |
| AHCI.Embedded.2-1 | Embedded AHCI 2 | Sapphire Rapids SATA AHCI Controller | DELL (Intel) | N/A | Not Capable |
| BOSS.SL.12-1 | BOSS in SL 12 | BOSS-N1 Monolithic | DELL (Marvell) | Gen 3 | Capable (Disabled) |

### Virtual Disks

| Drive | Name | RAID Type | Media | Capacity | Status | Read Cache | Write Cache | Stripe Size |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Disk.Virtual.0:BOSS.SL.12-1 | VD_R1_0 | RAID1 | Solid State Drive | 480.0 GB | Online | No Read Ahead | Write Through | 128KB |

### Physical Disks

| Drive | Description | Manufacturer | Model | Media | Form Factor | Protocol | Max Speed | Capacity | RAID Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Disk.Direct.0-0:BOSS.SL.12-1 | Disk 0 on BOSS in SL 12 | SK hynix | Dell NVMe PE8010 RI M.2 480GB | Solid State Drive | M.2 | NVMe 1.3 | 8 GT/s | 480.1 GB | Online |
| Disk.Direct.1-1:BOSS.SL.12-1 | Disk 1 on BOSS in SL 12 | SK hynix | Dell NVMe PE8010 RI M.2 480GB | Solid State Drive | M.2 | NVMe 1.3 | 8 GT/s | 480.1 GB | Online |

### PCIe NVMe SSDs

| Drive | Description | Manufacturer | Model | Form Factor | Protocol | Max Speed | Negotiated Speed | Capacity |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Disk.Bay.0:Enclosure.Internal.0-1 | PCIe SSD in Slot 0 in Bay 1 | Samsung Electronics Co Ltd | Dell Ent NVMe v2 AGN MU U.2 1.6TB | 2.5 inch | NVMe 1.3 | 16 GT/s | 16 GT/s | 1600.3 GB |
| Disk.Bay.1:Enclosure.Internal.0-1 | PCIe SSD in Slot 1 in Bay 1 | Samsung Electronics Co Ltd | Dell Ent NVMe v2 AGN MU U.2 1.6TB | 2.5 inch | NVMe 1.3 | 16 GT/s | 16 GT/s | 1600.3 GB |
| Disk.Bay.2:Enclosure.Internal.0-1 | PCIe SSD in Slot 2 in Bay 1 | Samsung Electronics Co Ltd | Dell Ent NVMe v2 AGN MU U.2 1.6TB | 2.5 inch | NVMe 1.3 | 16 GT/s | 16 GT/s | 1600.3 GB |
| Disk.Bay.3:Enclosure.Internal.0-1 | PCIe SSD in Slot 3 in Bay 1 | Samsung Electronics Co Ltd | Dell Ent NVMe v2 AGN MU U.2 1.6TB | 2.5 inch | NVMe 1.3 | 16 GT/s | 16 GT/s | 1600.3 GB |

## Network Interfaces (NICs)

| Port | Description | Vendor | Product | Media | Protocol | Link Speed | Duplex | Slot Type | CPU Affinity |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| NIC.Embedded.1-1-1 | Embedded NIC 1 Port 1 Partition 1 | Broadcom Corp | Broadcom NetXtreme Gigabit Ethernet (BCM5720) | Base T | NIC | Unknown | Unknown | Unknown | Not Applicable |
| NIC.Embedded.2-1-1 | Embedded NIC 1 Port 2 Partition 1 | Broadcom Corp | Broadcom NetXtreme Gigabit Ethernet (BCM5720) | Base T | NIC | Unknown | Unknown | Unknown | Not Applicable |
| NIC.Slot.1-1-1 | NIC in Slot 1 Port 1 Partition 1 | Mellanox Technologies, Inc. | Mellanox ConnectX-6 Dx Dual Port 100 GbE QSFP56 Adapter | SFF_CAGE | NIC,RDMA | 100 Gbps | Full Duplex | PCI Express Gen 5 | 1 |
| NIC.Slot.1-2-1 | NIC in Slot 1 Port 2 Partition 1 | Mellanox Technologies, Inc. | Mellanox ConnectX-6 Dx Dual Port 100 GbE QSFP56 Adapter | SFF_CAGE | NIC,RDMA | Unknown | Unknown | PCI Express Gen 5 | 1 |
| NIC.Slot.2-1-1 | NIC in Slot 2 Port 1 Partition 1 | Mellanox Technologies, Inc. | Mellanox ConnectX-6 Dx Dual Port 100 GbE QSFP56 Adapter | SFF_CAGE | NIC,RDMA | Unknown | Unknown | PCI Express Gen 4 | 2 |
| NIC.Slot.2-2-1 | NIC in Slot 2 Port 2 Partition 1 | Mellanox Technologies, Inc. | Mellanox ConnectX-6 Dx Dual Port 100 GbE QSFP56 Adapter | SFF_CAGE | NIC,RDMA | 100 Gbps | Full Duplex | PCI Express Gen 4 | 2 |
| iDRAC.Embedded.1-1 | iDRAC Management Interface | | | | | 1Gbps | Full Duplex | | |

### Transceivers

| Port | Description | Vendor | Type | Interface | Revision |
| --- | --- | --- | --- | --- | --- |
| NetworkTransceiver.Integrated.1:NIC.Slot.1-1 | Network Transceiver in NIC in Slot 1 Port 1 | DELL EMC | QSFP28 or later | Optical Fiber | B1 |
| NetworkTransceiver.Integrated.1:NIC.Slot.2-2 | Network Transceiver in NIC in Slot 2 Port 2 | DELL EMC | QSFP28 or later | Optical Fiber | B1 |

### Additional Components

| Component | Description | Manufacturer | Model |
| --- | --- | --- | --- |
| Communicate.Embedded.1-1 | Communicate.Embedded.1-1 | Intel Corporation |  |
| Enclosure.Internal.0-1 | PCIe SSD Backplane 1 |  |  |
| Fan.Embedded.1A | Fan 1A |  |  |
| Fan.Embedded.1B | Fan 1B |  |  |
| Fan.Embedded.1C | Fan 1C |  |  |
| Fan.Embedded.1D | Fan 1D |  |  |
| Fan.Embedded.2A | Fan 2A |  |  |
| Fan.Embedded.2B | Fan 2B |  |  |
| Fan.Embedded.2C | Fan 2C |  |  |
| Fan.Embedded.2D | Fan 2D |  |  |
| Fan.Embedded.3A | Fan 3A |  |  |
| Fan.Embedded.3B | Fan 3B |  |  |
| Fan.Embedded.3C | Fan 3C |  |  |
| Fan.Embedded.3D | Fan 3D |  |  |
| Fan.Embedded.4A | Fan 4A |  |  |
| Fan.Embedded.4B | Fan 4B |  |  |
| Fan.Embedded.4C | Fan 4C |  |  |
| Fan.Embedded.4D | Fan 4D |  |  |
| ISABridge.Embedded.1-1 | Embedded ISA Bridge 1 | Intel Corporation |  |
| PSU.Slot.1 | Power Supply 1 | DELL | PWR SPLY,1100W,RDNT,LTON |
| PSU.Slot.2 | Power Supply 2 | DELL | PWR SPLY,1100W,RDNT,LTON |
| SerialBus.Embedded.4-1 | SerialBus.Embedded.4-1 | Intel Corporation |  |
| SMBus.Embedded.3-1 | Embedded SM Bus 3 | Intel Corporation |  |
| Video.Embedded.1-1 | Embedded Video Controller 1 | Matrox Electronics Systems Ltd. |  |

## Firmware
| Component | FW Version |
|:-|:-|
| Backplane 1 | 7.20 |
| BIOS | 2.10.1 |
| BOSS-N1 Monolithic |	2.1.13.2038 |
| Broadcom NetXtreme Gigabit Ethernet (BCM5720) | 22.31.6 |
| Broadcom NetXtreme Gigabit Ethernet (BCM5720) | 22.31.6 |
| Dell 64 Bit uEFI Diagnostics, version 4303, 4303A52, 4303.52 | 4303A52 |
| Dell iDRAC Service Module Embedded Package v5.2.0.0, A00 | 5.2.0.0 |
| Dell OS Driver Pack, 26.03.01, A00 | 26.03.01 |
| Disk 0 on BOSS in SL | 12	1.1.0 |
| Disk 1 on BOSS in SL | 12	1.1.0 |
| Integrated Dell Remote Access Controller |	7.30.10.50 |
| Lifecycle Controller |	7.30.10.50 |
| Mellanox ConnectX-6 Dx Dual Port 100 GbE QSFP56 Adapter | 22.36.10.10 |
| Mellanox ConnectX-6 Dx Dual Port 100 GbE QSFP56 Adapter | 22.36.10.10 |
| Mellanox ConnectX-6 Dx Dual Port 100 GbE QSFP56 Adapter | 22.36.10.10 |
| Mellanox ConnectX-6 Dx Dual Port 100 GbE QSFP56 Adapter | 22.36.10.10 |
| PCIe SSD in Slot 0 in Bay 1 |	2.5.0 |
| PCIe SSD in Slot 1 in Bay 1 |	2.5.0 |
| PCIe SSD in Slot 2 in Bay 1 |	2.5.0 |
| PCIe SSD in Slot 3 in Bay 1 |	2.5.0 |
| Power Supply.Slot.2 |	00.21.33 |
| System CPLD |	1.0.6 |
| TPM |	7.2.2.0 |
