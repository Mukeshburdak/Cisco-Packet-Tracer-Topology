🔀 VLAN Inter-Switch Communication – Packet Tracer Project
-
This repository contains a VLAN-based Layer-2 Network Topology created in Cisco Packet Tracer.
The project demonstrates VLAN creation, access port assignment, trunk links, and communication between two switches.

---
📁 Files Included
-
File	Description
vlan_topology.pkt	Complete Packet Tracer simulation file.
README.md	Project documentation (this file).

---
🖼 Topology Overview
-
The topology contains:

Two 2960 Switches (Switch0 & Switch1)

Two VLANs used to segment users:

VLAN 10 – SY

VLAN 20 – PB

Four PCs and Four Laptops, evenly divided across switches

Trunk link between both switches for inter-switch VLAN propagation

This setup shows how multiple switches can share VLAN information and ensure users in the same VLAN can communicate even across different switches.

---
🌐 IP Addressing Scheme
-
All devices belong to the same network: 192.168.10.0/24

| Device    | IP Address     | VLAN         |
| --------- | -------------- | ------------ |
| PC-PT     | `192.168.10.2` | SY (VLAN 10) |
| Laptop-PT | `192.168.10.3` | PB (VLAN 20) |
| PC-PT     | `192.168.10.4` | SY (VLAN 10) |
| Laptop-PT | `192.168.10.5` | PB (VLAN 20) |
| PC-PT     | `192.168.10.6` | SY (VLAN 10) |
| Laptop-PT | `192.168.10.7` | PB (VLAN 20) |
| PC-PT     | `192.168.10.8` | SY (VLAN 10) |
| Laptop-PT | `192.168.10.9` | PB (VLAN 20) |

---
🛠 Configuration Summary
-
✔ VLANs Created
VLAN 10 name SY
VLAN 20 name PB

✔ Access Ports Assigned

Example (Switch0):

interface fa0/1  
 switchport mode access  
 switchport access vlan 10  

interface fa0/2  
 switchport mode access  
 switchport access vlan 20  

✔ Trunk Link Configuration

The link between Switch0 and Switch1 is configured as a trunk.

interface fa0/24
 switchport mode trunk
 switchport trunk allowed vlan 10,20


Trunking ensures VLAN 10 & VLAN 20 traffic is carried between both switches.

---
🧪 Testing
-
You can perform the following tests inside Packet Tracer:

VLAN Communication (Should Work)

PC 192.168.10.2 ↔ PC 192.168.10.4 ↔ PC 192.168.10.6 ↔ PC 192.168.10.8 (All SY – VLAN 10)

Laptop 192.168.10.3 ↔ Laptop 192.168.10.5 ↔ Laptop 192.168.10.7 ↔ Laptop 192.168.10.9 (All PB – VLAN 20)

Inter-VLAN Communication (Should NOT Work)

Devices in VLAN10 cannot reach VLAN20 unless a router-on-a-stick is added.

---
🚀 How to Use
-
Download Cisco Packet Tracer 8.x or later

Open the .pkt file

Verify VLAN creation and port assignments

Test pings within the same VLAN

Observe trunk operation between switches

---
📘 Learning Outcomes
-
By studying this topology, you will understand:

VLAN creation and management

Access & trunk port configuration

Inter-switch VLAN communication

Basic network segmentation for security

How trunk links carry multiple VLANs

---
<img width="1088" height="402" alt="image" src="https://github.com/user-attachments/assets/d051756f-5c47-4257-8eb9-4b08d7664754" />

---
<img width="636" height="535" alt="image" src="https://github.com/user-attachments/assets/1e5d6c03-5ad0-4c7c-9755-17adee306147" />

---
