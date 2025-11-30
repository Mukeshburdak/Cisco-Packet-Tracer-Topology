🌐 Inter-VLAN & Router-on-a-Stick Network Topology

This project demonstrates a Router-on-a-Stick Inter-VLAN Routing setup using a Cisco 2911 Router and two 2960 switches.
Two VLAN networks (10.x.x.x and 20.x.x.x) are configured on different switches and routed using subinterfaces.

---
📘 Network Topology
<img width="1098" height="640" alt="Screenshot 2025-11-30 085454" src="https://github.com/user-attachments/assets/5142ef57-cfe5-4fa0-8e14-836a62ea8ad8" />

---
🖥 Devices Used
| Device Type | Model      | Quantity |
| ----------- | ---------- | -------- |
| Router      | Cisco 2911 | 1        |
| Switch      | Cisco 2960 | 2        |
| PC          | PC-PT      | 4        |
| Laptop      | Laptop-PT  | 4        |

---
📡 VLAN Details
| VLAN Name  | Purpose                                   | Subnet          | Gateway      |
| ---------- | ----------------------------------------- | --------------- | ------------ |
| **VLAN-M** | Main / Marketing / Management (as needed) | 192.168.10.0/24 | 192.168.10.1 |
| **VLAN-B** | Backup / Business / Guest Dept            | 192.168.20.0/24 | 192.168.20.1 |

---
🧩 IP Addressing Table
VLAN-M (192.168.10.0/24)
| Device | IP Address   |
| ------ | ------------ |
| PC-PT  | 192.168.10.2 |
| PC-PT  | 192.168.10.3 |
| PC-PT  | 192.168.10.4 |
| PC-PT  | 192.168.10.5 |

---
VLAN-B (192.168.20.0/24)
| Device    | IP Address   |
| --------- | ------------ |
| Laptop-PT | 192.168.20.2 |
| Laptop-PT | 192.168.20.3 |
| Laptop-PT | 192.168.20.4 |
| Laptop-PT | 192.168.20.5 |

---
🔧 Configuration Steps

1️⃣ Create VLAN-M and VLAN-B on both switches

vlan 10

 name VLAN-M
 
vlan 20

 name VLAN-B

2️⃣ Assign Access Ports

Switch0

interface range fa0/1-3

 switchport mode access
 
 switchport access vlan 10   # VLAN-M

interface range fa0/4-6

 switchport mode access
 
 switchport access vlan 20   # VLAN-B

Switch1

interface range fa0/1-3

 switchport mode access
 
 switchport access vlan 10   # VLAN-M

interface range fa0/4-6

 switchport mode access
 
 switchport access vlan 20   # VLAN-B
 
 ---
 3️⃣ Configure Trunk Between Both Switches
 
interface fa0/24

 switchport mode trunk


(Repeat on both switches.)

---
4️⃣ Router-on-a-Stick Configuration (Inter-VLAN Routing)

interface g0/0.10

 encapsulation dot1Q 10
 
 ip address 192.168.10.1 255.255.255.0   # Gateway for VLAN-M

interface g0/0.20

 encapsulation dot1Q 20
 
 ip address 192.168.20.1 255.255.255.0   # Gateway for VLAN-B

interface g0/0

 no shutdown
 
 ---
 🔍 Verification Commands
 
On Switch

show vlan brief

show interfaces trunk

On Router

show ip interface brief

show running-config

On PCs/Laptops

ping 192.168.10.1      # Gateway VLAN-M

ping 192.168.20.1      # Gateway VLAN-B

ping <other VLAN devices>

---
✅ Expected Results

✔ VLAN-M devices communicate across switches

✔ VLAN-B devices communicate across switches

✔ Router enables VLAN-M ↔ VLAN-B communication

✔ Trunk carries both VLANs properly
