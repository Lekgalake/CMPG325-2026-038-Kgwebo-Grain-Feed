# IP Addressing Plan

The IP addressing plan for **Kgwebo Grain & Feed (Klerksdorp)** is based on the assigned address block **10.20.0.0/16**. The address space is divided into separate subnets to support network segmentation, management, staff, servers, and future expansion.

## Network Segments

| Network Segment | VLAN | Network Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| Management | 10 | 10.20.10.0/24 | 255.255.255.0 | 10.20.10.1 |
| Staff | 20 | 10.20.20.0/24 | 255.255.255.0 | 10.20.20.1 |
| Servers | 30 | 10.20.30.0/24 | 255.255.255.0 | 10.20.30.1 |
| Network Management | 99 | 10.20.99.0/24 | 255.255.255.0 | 10.20.99.1 |
| Future Branch Office | Reserved | 10.20.100.0/24 | 255.255.255.0 | Reserved |

## Addressing Allocation
- **Management:** 10.20.10.0/24
- **Staff:** 10.20.20.0/24
- **Servers:** 10.20.30.0/24
- **Network Management:** 10.20.99.0/24
- **Future Branch:** 10.20.100.0/24

The remaining address space within `10.20.0.0/16` remains available for future expansion.

The `10.20.100.0/24` network is reserved for the planned branch office in accordance with **CR6**. The branch office will not be physically implemented in Packet Tracer.

The addressing plan also provides separate networks for Management and Staff, allowing Staff restrictions to be applied without preventing Management from accessing the Internet.
