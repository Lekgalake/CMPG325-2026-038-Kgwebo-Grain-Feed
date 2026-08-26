# Topology Design

## 2. Physical Topology
The physical topology for **Kgwebo Grain & Feed (Klerksdorp)** will use a hierarchical network design consisting of a router, distribution switches, access switches, servers, and end-user devices.

The topology includes redundant connections between switches to provide network resilience and to support the implementation of **Spanning Tree Protocol (STP)** for loop prevention and root bridge design.

### Physical Topology Diagram
*(To be added: physical-topology.png)*

### Devices
- 1 × Router
- 2 × Distribution switches
- 2 × Access switches
- End-user computers
- Server(s)
- Internet connection

**Design consideration:** Redundant switch connections are included to support network availability and provide the required environment for demonstrating STP loop prevention and root-switch selection. The planned branch office is not physically implemented, in accordance with **CR6**.

## 3. Logical Topology
The logical topology for **Kgwebo Grain & Feed (Klerksdorp)** separates network users into logical network segments using VLANs. This provides better traffic management and allows the organisation to apply different access policies to Management and Staff.

The design also supports **STP** by providing redundant Layer 2 connections between the distribution switches.

### Logical Topology Diagram
*(To be added: logical-topology.png)*

### VLAN Structure
| VLAN | Network Purpose |
|---|---|
| Management VLAN | Management users and devices |
| Staff VLAN | General staff users and devices |
| Server VLAN | Network servers and services |
| Future/Reserved Network | Address space reserved for the planned branch office |

The **Management VLAN** will be configured so that Management can access the Internet even when restrictions are applied to the Staff network.
The **Staff VLAN** will be logically separated from Management so that appropriate restrictions can be applied without affecting Management's Internet access.

The distribution switches will participate in **STP**, with a designated root bridge to control the preferred Layer 2 forwarding paths and prevent switching loops.
The IP networks for these VLANs will be allocated from the assigned **10.20.0.0/16** address block.
