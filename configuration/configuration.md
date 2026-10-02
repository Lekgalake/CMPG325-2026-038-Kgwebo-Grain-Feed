# Device Configurations

This document contains the core configurations applied to the network devices in Cisco Packet Tracer to meet the client requirements.

## 1. Core/Distribution Switches (STP Root Design)

To meet the requirement for Spanning Tree Protocol (STP) Loop Prevention & Root Design, we configure `Core-SW1` as the primary root bridge and `Core-SW2` as the secondary root bridge for all VLANs.

### Core-SW1 (Primary Root)
```text
enable
configure terminal
hostname Core-SW1

! Create VLANs
vlan 10
 name Management
vlan 20
 name Staff
vlan 30
 name Servers
vlan 99
 name Network_Mgmt
exit

! Configure STP Root Primary
spanning-tree mode rapid-pvst
spanning-tree vlan 10,20,30,99 root primary
```

### Core-SW2 (Secondary Root)
```text
enable
configure terminal
hostname Core-SW2

! Create VLANs
vlan 10,20,30,99
exit

! Configure STP Root Secondary
spanning-tree mode rapid-pvst
spanning-tree vlan 10,20,30,99 root secondary
```

## 2. Access Switches (Edge Ports and Loop Prevention)

Access switches connect to end devices. We configure `PortFast` and `BPDU Guard` on these edge ports to prevent accidental loops if a switch is plugged into an access port.

### Access-SW1 (Example)
```text
enable
configure terminal
hostname Access-SW1

! Configure Uplinks as Trunks
interface range GigabitEthernet0/1-2
 switchport mode trunk
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,99
exit

! Configure Access Ports for Staff (VLAN 20)
interface range FastEthernet0/1-10
 switchport mode access
 switchport access vlan 20
 spanning-tree portfast
 spanning-tree bpduguard enable
exit
```

## 3. Router Configuration (Inter-VLAN Routing & ACLs)

To address the requirement: *Management retains Internet access when the Staff network is restricted*, we configure an Access Control List (ACL) on the edge router.

### Edge-Router
```text
enable
configure terminal
hostname Edge-Router

! Sub-interfaces for Inter-VLAN Routing
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 10.20.10.1 255.255.255.0
 
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 10.20.20.1 255.255.255.0
 ip access-group STAFF_RESTRICT in

interface GigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 10.20.30.1 255.255.255.0

interface GigabitEthernet0/0.99
 encapsulation dot1Q 99 native
 ip address 10.20.99.1 255.255.255.0

! Access Control List (ACL) to restrict Staff Internet
! 1. Permit Staff to access local subnets (10.20.x.x)
! 2. Deny Staff to access anything else (Internet)
! 3. Permit all other traffic
ip access-list extended STAFF_RESTRICT
 permit ip 10.20.20.0 0.0.0.255 10.20.0.0 0.0.255.255
 deny ip 10.20.20.0 0.0.0.255 any
 permit ip any any
```
