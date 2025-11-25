🏫 Campus Network Topology – Packet Tracer Project

This repository contains a complete Campus Network Topology designed and simulated in Cisco Packet Tracer.
The project demonstrates hierarchical networking, inter-VLAN routing, dynamic routing between routers, DHCP, DNS & HTTP services, and departmental segmentation.

📁 Files Included
File	Description
campus_topology.pkt	The full Cisco Packet Tracer simulation file containing the campus network.
README.md	Documentation explaining the topology, addressing, configurations, and components.
🖼 Topology Overview

The network consists of multiple departments, core routing, dynamic routing between campus routers, and server infrastructure.
It includes:

Admin Department

CSE Department

ECE Department

Guest Network

Multiple Remote LANs

Server Network (HTTP, DNS, DHCP)

Core Router (Campus Router)

Distribution & Access Layer Switches

🌐 IP Addressing Scheme
1. Server Network (192.168.10.0/24)

| Service     | IP Address            |
| ----------- | --------------------- |
| HTTP Server | `192.168.10.4`        |
| DNS Server  | `192.168.10.3`        |
| DHCP Server | `192.168.10.2`        |
| Switch      | `2960-24TT (Switch6)` |

2. Department LANs via Core Router

| Department | Subnet              | Connected Device |
| ---------- | ------------------- | ---------------- |
| Admin      | `192.168.10.32/27`  | Switch0          |
| CSE        | `192.168.10.64/27`  | Switch1          |
| ECE        | `192.168.10.96/27`  | Switch2          |
| Guest      | `192.168.10.128/27` | Switch3          |

Each LAN contains a PC and a Laptop with static/DHCP-assigned IP addresses.

3. Remote LANs (Connected via Routers 1, 2)

| Location          | Subnet                                                  |
| ----------------- | ------------------------------------------------------- |
| Remote LAN 1      | `192.168.20.0/24`                                       |
| Remote LAN 2      | `192.168.30.0/24`                                       |
| Router Interlinks | `192.168.40.0/30`, `192.168.50.0/30`, `192.168.60.0/30` |

🛠 Features Implemented
✔ 1. DHCP Server

Automatically assigns IPs to:

Admin PCs

CSE & ECE systems

Guest laptops

✔ 2. DNS Server

Resolves domain names across the entire campus network.

✔ 3. HTTP Server

Hosts a sample institutional webpage accessible from all networks.

✔ 4. Dynamic Routing

Routers use a dynamic routing protocol (RIP / OSPF / EIGRP — based on your configuration) to allow inter-LAN and inter-router communication.

✔ 5. Layer-2 Switching

Each department uses individual 2960 switches for segmentation.

✔ 6. Hierarchical Network Design

Core Layer: Campus Router

Distribution Layer: Department switches

Access Layer: PCs, Laptops

📡 Router Interconnections

| Link                    | Network           |
| ----------------------- | ----------------- |
| Campus Router ↔ Router1 | `192.168.40.0/30` |
| Router1 ↔ Router2       | `192.168.50.0/30` |
| Campus Router ↔ Router2 | `192.168.60.0/30` |

🚀 How to Use This Project

Download and install Cisco Packet Tracer 8.x or later

Open the .pkt file in Packet Tracer

Explore device configurations:

Server settings (DHCP/DNS/HTTP)

Router IPv4 addressing

Routing tables

Switch port assignments

Test connectivity using:

ping

nslookup

Web browsing via HTTP

📘 Learning Outcomes

By using this topology, students will understand:

IP addressing & subnetting

Server configuration in Packet Tracer

Inter-VLAN & inter-router communication

Hierarchical network architecture

Dynamic routing protocol configuration

Multi-department network segmentation
