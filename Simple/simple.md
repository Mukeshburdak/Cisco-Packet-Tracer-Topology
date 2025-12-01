🖧 Simple Computer Network using IP Addressing
-
A Cisco Packet Tracer Practical Documentation

---
🎯 (a) Objective
-
The objective of this experiment is to design, configure, and test a simple computer network using proper IP addressing.
This practical helps students understand:

Assigning unique IP addresses to end devices (PCs, laptops, servers).

Understanding subnet mask, gateway, and LAN communication.

Building a working network topology in Cisco Packet Tracer.

Verifying device communication using commands like ping.

Observing how data flows between devices inside a Local Area Network (LAN).

By completing this activity, learners will gain hands-on skills in basic network creation, IP assignment, and connectivity testing.

---
🖥️ (b) Network Topology
-
<p align="center"> <img src="https://github.com/user-attachments/assets/c363f546-c103-4d62-bd2e-93e344fdfd32" width="100%" /> </p> <p align="center"><b>Fig. 1.1 — Simple Computer Network Topology</b></p>

---
⚙️ (c) Configuration of Network Components
-
Below is the configuration of each device used in the topology:

🔹 1. End Devices (PCs, Laptops, Servers)
-
Purpose: End devices communicate, send, and receive data in the network.

✔ Configuration Steps
-
Click the PC → Desktop tab → IP Configuration

Assign the following values:

| Parameter                 | Example Value |
| ------------------------- | ------------- |
| **IP Address**            | 192.168.1.2   |
| **Subnet Mask**           | 255.255.255.0 |
| **Default Gateway**       | 192.168.1.1   |
| **DNS Server (Optional)** | 8.8.8.8       |


These settings ensure that each device gets a unique address and can communicate within the LAN.

🔹 2. Switches
-
Purpose: Connect multiple devices inside the same LAN and forward frames.

✔ Configuration Steps
-
Switches operate at Layer 2, so basic operation requires no manual configuration.

However, ensure the following:

Use Copper Straight-Through cables to connect PCs to switches.

Verify that each FastEthernet interface shows green link lights.

(Optional) Assign a management IP:

Switch> enable

Switch# configure terminal

Switch(config)# interface vlan 1

Switch(config-if)# ip address 192.168.1.10 255.255.255.0

Switch(config-if)# no shutdown

🔹 3. Router (if used)
-
Purpose: Provides gateway for inter-network communication.

✔ Configuration Steps
-
Router> enable

Router# configure terminal

Router(config)# interface gigabitEthernet 0/0

Router(config-if)# ip address 192.168.1.1 255.255.255.0

Router(config-if)# no shutdown

🧪 (d) Connectivity Testing
-
Use the ping command from any PC:

ping 192.168.1.3

ping 192.168.1.1


Successful pings confirm that IP addressing and cabling are correctly implemented.

---
📘 Summary
-
This experiment guides students through:

Designing a basic LAN topology

Assigning valid IP addresses

Configuring PCs and routers

Testing communication using ping

---
