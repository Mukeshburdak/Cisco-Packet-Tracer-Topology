To implement & test the IP addressing by creating a simple network 
topology in cisco packet tracer.
-
---
(a) Objective :- 
-
The main objective of this experiment is to design, implement, and test a simple computer network 
using proper IP addressing schemes in Cisco Packet Tracer. It aims to help students understand how 
to assign and configure IP addresses for different network devices such as PCs, switches, and routers 
to establish communication within a network. This exercise also focuses on testing the connectivity 
between devices using tools like the ping command, verifying that the assigned IP addresses allow 
successful data transmission. By the end of this experiment, learners will gain practical experience in 
network design, device configuration, and IP-based communication within a simulated 
environment.

---
(b) Network Topology :-
-
<img width="1046" height="471" alt="Screenshot 2025-11-12 221353" src="https://github.com/user-attachments/assets/3af366fc-7725-4d70-85d1-935062b5fe66" />

---
🧩 Network Topology Overview
-
The topology consists of:

Two LANs connected through a Router (ISR4331).

Each LAN has a Switch (2960-24TT) connecting multiple end devices (PCs and Laptops).

1. IP Addressing Scheme
 
| Network | Device Type     | Interface    | IP Address    | Subnet Mask   |
| ------- | --------------- | ------------ | ------------- | ------------- |
| LAN 1   | PC/Laptop       | NIC          | 192.168.10.x  | 255.255.255.0 |
| LAN 2   | PC/Laptop       | NIC          | 192.168.20.x  | 255.255.255.0 |
| Router  | G0/0 (to LAN 1) |              | 192.168.10.1  | 255.255.255.0 |
| Router  | G0/1 (to LAN 2) |              | 192.168.20.1  | 255.255.255.0 |

2. Router Configuration (ISR4331)

🔹 Commands:

Router> enable

Router# configure terminal

Router(config)# interface gigabitEthernet0/0

Router(config-if)# ip address 192.168.10.1 255.255.255.0

Router(config-if)# no shutdown

Router(config-if)# exit

Router(config)# interface gigabitEthernet0/1

Router(config-if)# ip address 192.168.20.1 255.255.255.0

Router(config-if)# no shutdown

Router(config-if)# exit

Router(config)# exit

Router# write memory

💡 Purpose:
-
The router acts as the gateway between two subnets (192.168.10.0/24 and 192.168.20.0/24) to enable inter-network communication.

3. Switch Configuration (2960-24TT)

🔹 Basic Configuration for Both Switches

Switch> enable

Switch# configure terminal

Switch(config)# hostname Switch0   # (or Switch1 for the second)

Switch(config)# no ip domain-lookup

Switch(config)# interface vlan 1

Switch(config-if)# ip address 192.168.10.10 255.255.255.0  # (or 192.168.20.10 for Switch1)

Switch(config-if)# no shutdown

Switch(config-if)# exit

Switch(config)# ip default-gateway 192.168.10.1  # (or 192.168.20.1 for Switch1)

Switch(config)# exit

Switch# write memory


💡 Purpose:
-
Switches provide local network connectivity and enable all hosts in the same LAN to communicate with each other and their default gateway.

4. End Devices (PCs and Laptops)

Each PC/Laptop gets a static IP configuration as follows:

| Device             | IP Address                | Subnet Mask   | Default Gateway |
| ------------------ | ------------------------- | ------------- | --------------- |
| PC/Laptop in LAN 1 | 192.168.10.2–192.168.10.5 | 255.255.255.0 | 192.168.10.1    |
| PC/Laptop in LAN 2 | 192.168.20.2–192.168.20.5 | 255.255.255.0 | 192.168.20.1    |

🔹 Steps in Packet Tracer:

Click the PC/Laptop → Desktop → IP Configuration.

Set IP Address, Subnet Mask, and Default Gateway as per the table above.

5. Testing Connectivity

After configuration, test using the ping command:

From PC in LAN 1 to Router (192.168.10.1)

From PC in LAN 1 to PC in LAN 2 (e.g., ping 192.168.20.2)

If routing is correct, all devices across both LANs should communicate successfully.

---
✅ Final Network Summary
-
Router (ISR4331) enables inter-LAN communication.

Switches (2960-24TT) manage local connectivity.

Static IP addressing ensures organized communication.

Successful pings verify complete configuration.

---
(d) Testing of network communication :-
-
<img width="495" height="297" alt="Screenshot 2025-11-12 222812" src="https://github.com/user-attachments/assets/66a7cb05-828e-45cd-be24-51aef4584e2a" />

---
