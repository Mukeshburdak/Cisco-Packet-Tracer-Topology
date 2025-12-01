To implementation & study of dynamic routing in computer networks GUI and CLI mode.
-
---
✅ Objective
-
• To understand the concept of dynamic routing in computer networks.

• To configure and implement dynamic routing protocols (RIP, OSPF, or EIGRP) using GUI (Cisco Packet Tracer) and CLI (Router command line).

• To study how routers automatically update routing tables using dynamic routing protocols.

• To examine packet flow and path selection based on routing metrics.

• To verify connectivity between different networks using ping, tracert, and routing table commands.

---
✅ Configuration of Different Components of Network Topology
-
Below is the neatly formatted table used for Packet Tracer or CLI implementation.

1. End Devices (PCs, Laptops)

| Device Type | Device Name | IP Address   | Subnet Mask   | Default Gateway |
| ----------- | ----------- | ------------ | ------------- | --------------- |
| PC          | PC-PT       | 192.168.10.2 | 255.255.255.0 | 192.168.10.1    |
| Laptop      | Laptop-PT   | 192.168.20.2 | 255.255.255.0 | 192.168.20.1    |
| Laptop      | Laptop-PT   | 192.168.30.2 | 255.255.255.0 | 192.168.30.1    |

2. Routers

| Router  | Interface | IP Address   | Subnet Mask   | Network Connected |
| ------- | --------- | ------------ | ------------- | ----------------- |
| Router0 | Gig0/0    | 192.168.10.1 | 255.255.255.0 | LAN 1             |
| Router0 | Gig0/1    | 192.168.40.2 | 255.255.255.0 | Link to Router1   |
| Router0 | Gig0/2    | 192.168.50.2 | 255.255.255.0 | Link to Router2   |
| Router1 | Gig0/0    | 192.168.20.1 | 255.255.255.0 | LAN 2             |
| Router1 | Gig0/1    | 192.168.40.3 | 255.255.255.0 | Link to Router0   |
| Router1 | Gig0/2    | 192.168.60.2 | 255.255.255.0 | Link to Router2   |
| Router2 | Gig0/0    | 192.168.30.1 | 255.255.255.0 | LAN 3             |
| Router2 | Gig0/1    | 192.168.50.3 | 255.255.255.0 | Link to Router0   |
| Router2 | Gig0/2    | 192.168.60.3 | 255.255.255.0 | Link to Router1   |

3. Switches

| Switch              | Ports Used                    | Connected To       |
| ------------------- | ----------------------------- | ------------------ |
| Switch0 (2960-24TT) | F0/1 → PC, F0/2 → Router1     | PC-PT, Router0     |
| Switch1 (2960-24TT) | F0/1 → Laptop, F0/2 → Router2 | Laptop-PT, Router1 |
| Switch2 (2960-24TT) | F0/1 → Laptop, F0/2 → Router0 | Laptop-PT, Router2 |


4. Dynamic Routing Protocol Configuration (CLI)

👉 Router0 – RIP Configuration

enable

configure terminal

router rip

version 2

network 192.168.10.0

network 192.168.40.0

network 192.168.50.0

no auto-summary

end

👉 Router1 – RIP Configuration

enable

configure terminal

router rip

version 2

network 192.168.20.0

network 192.168.40.0

network 192.168.60.0

no auto-summary

end

👉 Router2 – RIP Configuration

enable

configure terminal

router rip

version 2

network 192.168.30.0

network 192.168.50.0

network 192.168.60.0

no auto-summary

end

5. Verification Commands

| Command                 | Purpose                |
| ----------------------- | ---------------------- |
| `show ip route`         | Displays routing table |
| `show ip ospf neighbor` | Shows OSPF neighbors   |
| `ping <IP>`             | Tests connectivity     |
| `tracert <IP>`          | Shows path of packets  |

---
✅ Network topology
-
<img width="615" height="417" alt="image" src="https://github.com/user-attachments/assets/a7679ff5-d729-4773-a327-1a7b4b2e9694" />

---
✅Testing of network communication
-
<img width="556" height="560" alt="image" src="https://github.com/user-attachments/assets/c1a22fc2-22cc-4af2-bd45-7454ae44fbe7" />

---
✅Router0 image
-
<img width="846" height="386" alt="image" src="https://github.com/user-attachments/assets/858e35be-1d31-4eac-89fa-8d8fa20ff395" />

---
