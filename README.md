# NTI-Networking-labs
# Cisco Inter-VLAN Routing using SVI

## Project Overview

This project was created using Cisco Packet Tracer to demonstrate
Inter-VLAN Routing using Switched Virtual Interfaces (SVIs)
on a Multilayer Switch.

The network contains four VLANs representing different departments.

## VLANs

- VLAN 10 - HR
- VLAN 20 - Sales
- VLAN 30 - IT
- VLAN 40 - Accounting

## IP Addressing

- VLAN 10: 192.168.10.0/24
  - Default Gateway: 192.168.10.1

- VLAN 20: 192.168.20.0/24
  - Default Gateway: 192.168.20.1

- VLAN 30: 192.168.30.0/24
  - Default Gateway: 192.168.30.1

- VLAN 40: 192.168.40.0/24
  - Default Gateway: 192.168.40.1

## Network Design

The network consists of:

- One Multilayer Switch
- Four Access Switches
- Four PCs
- Four VLANs

The Access Switches connect the end devices to their
corresponding VLANs.

The links between the Access Switches and the Multilayer
Switch are configured as Trunk links using IEEE 802.1Q.

## Configuration

### VLAN Configuration

The following VLANs were created:

```cisco
vlan 10
name HR

vlan 20
name SALES

vlan 30
name IT

vlan 40
name ACCOUNTING



svi configured on multilayer switch
interface vlan 10
ip address 192.168.10.1 255.255.255.0
no shutdown

interface vlan 20
ip address 192.168.20.1 255.255.255.0
no shutdown

interface vlan 30
ip address 192.168.30.1 255.255.255.0
no shutdown

interface vlan 40
ip address 192.168.40.1 255.255.255.0
no shutdown



Inter-VLAN Routing
IP routing was enabled on the Multilayer Switch:
ip routing




This allows devices from different VLANs to communicate
with each other.
Trunk Configuration
The links between the Multilayer Switch and Access Switches
were configured as trunk links:

interface range fa0/1 - 4
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk native vlan 1
no shutdown

Access Ports
End-device ports were configured as access ports and assigned
to their corresponding VLANs.
Example:

interface fa0/2
switchport mode access
switchport access vlan 10
no shutdown


Useful verification commands:
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
