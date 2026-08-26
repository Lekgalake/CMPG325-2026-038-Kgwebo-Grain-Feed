# 1. Client Requirements

## 1.1 Client Overview
**Kgwebo Grain & Feed**, located in **Klerksdorp**, operates within the **agriculture industry**. The organisation requires a reliable computer network to support communication, access to network services, Internet connectivity, and the exchange of data between authorised devices.

The proposed network must be designed and simulated using **Cisco Packet Tracer** and must provide a working and testable implementation that satisfies the client's specified requirements.

## 1.2 Network Requirements
The network must satisfy the following requirements:

| Requirement | Description |
|---|---|
| Reliable connectivity | Provide appropriate connectivity between authorised network devices and users within the organisation. |
| Network services | Provide the necessary network services required for the assigned scenario and support normal organisational operations. |
| IP addressing | Use the assigned address block **10.20.0.0/16** as the basis for the network's IP addressing plan. |
| Network segmentation | Separate appropriate network groups to support security, management and traffic control requirements. |
| Internet access | Provide Internet connectivity for the organisation, with particular consideration for the management requirement. |
| Management access | Management must retain Internet access even when the Staff network is restricted. |
| Loop prevention | Implement **Spanning Tree Protocol (STP)** to prevent Layer 2 switching loops and provide a controlled root-switch design. |
| Future expansion | Accommodate the planned branch office through the network's addressing/design structure without implementing a second physical site. |
| Testing | The completed network must support end-to-end connectivity testing and verification of the STP implementation. |
| Simulation | Produce a working Cisco Packet Tracer implementation that can be opened and reproduced for assessment. |
| Documentation | Document important design decisions, configurations, testing results, troubleshooting and evidence in the GitHub portfolio. |

## 1.3 Specific Client Constraints

### Management Internet Access
A key requirement is:
> Management requires Internet access even when the Staff network is restricted.

Therefore, the network design must ensure that Management and Staff can be appropriately separated. Restrictions applied to Staff must not prevent Management from accessing the Internet.
This requirement will influence the logical topology, VLAN/subnet design, routing and access-control configuration.

### STP Requirement
The assigned technical challenge is: **STP Loop Prevention & Root Design**

The network must therefore include an appropriate redundant switching topology where STP can be configured and demonstrated.
The implementation must allow us to verify:
- The selected STP root bridge.
- Forwarding paths.
- Redundant/blocked paths.
- Prevention of Layer 2 loops.
- STP behaviour during a topology change.

### Future Branch Office
The client has a planned branch office under CR6.
The requirement is specifically: **Design/addressing accommodation only; no second-site build required.**

Therefore, the current network will reserve appropriate addressing/design capacity for future expansion without creating a second branch-office topology in Packet Tracer.

## 1.4 Addressing Requirement
The client has been assigned: **10.20.0.0/16**

The entire IP addressing plan must therefore be derived from this address block.
The final addressing plan should clearly identify the networks allocated to the different logical parts of the organisation and reserve appropriate address space for the future branch.
We will determine the actual subnet sizes and ranges after designing the required network segments, rather than choosing arbitrary ranges now.

## 1.5 Implementation Requirement
The final solution must be implemented in **Cisco Packet Tracer** and must be:
- Configured correctly.
- Operational.
- Testable.
- Reproducible from the submitted .pkt file.
- Supported by screenshots/command output demonstrating successful configuration and testing.
