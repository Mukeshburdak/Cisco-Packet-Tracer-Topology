Task: To configure and test a DNS Server in Cisco Network Tracer 

(a) Objective 

The objective of this experiment is to configure and test a DNS (Domain Name System) Server in Cisco Packet Tracer to understand how domain name resolution works in computer networks. 

This experiment aims to demonstrate how a DNS Server translates domain names (such as www.example.com) into their corresponding IP addresses, allowing users to access network resources easily without remembering numerical IP addresses. 

Students will configure a DNS Server with domain name entries, assign proper IP addresses to network devices, and verify connectivity by accessing the web server or other hosts using domain names through a web browser or command prompt. 

(b) Network Topology 

<img width="1200" height="460" alt="Screenshot 2025-11-08 100810" src="https://github.com/user-attachments/assets/97b8542a-20f2-4817-9ea1-00960cfe6821" />

(c) Configuration of different components of network topology 

1. Router 

Device Name: Router0 

Model: Cisco 2911 

Purpose: 

Connects two different networks (192.170.50.0/24 and 192.170.60.0/24). 

Performs inter-network communication (routing between LANs). 

2. Switches 

Switch0 (Left side) 

Model: Cisco 2960-24TT 

Connected Devices: 

PC-PT (192.170.50.2) 

Laptop-PT (192.170.50.3) 

PC-PT (192.170.50.4) 

Laptop-PT (192.170.50.5) 

Network/Subnet: 192.170.50.0/24 

Switch1 (Right side) 

Model: Cisco 2960-24TT 

Connected Devices: 

PC-PT (192.170.60.2) 

Laptop-PT (192.170.60.3) 

PC-PT (192.170.60.4) 

Laptop-PT (192.170.60.5) 

DNS Server (192.170.60.x) 

HTTP Server (192.170.60.x) 

Network/Subnet: 192.170.60.0/24 

 

3. End Devices 

Left LAN (192.170.50.0/24) 

| Device Type | Device Name | IP Address   | Subnet Mask   | Default Gateway |
| ----------- | ----------- | ------------ | ------------- | --------------- |
| PC          | PC-PT       | 192.170.50.2 | 255.255.255.0 | 192.170.50.1    |
| Laptop      | Laptop-PT   | 192.170.50.3 | 255.255.255.0 | 192.170.50.1    |
| PC          | PC-PT       | 192.170.50.4 | 255.255.255.0 | 192.170.50.1    |
| Laptop      | Laptop-PT   | 192.170.50.5 | 255.255.255.0 | 192.170.50.1    |

Right LAN – 192.170.60.0/24

| Device Type | Device Name | IP Address   | Subnet Mask   | Default Gateway |
| ----------- | ----------- | ------------ | ------------- | --------------- |
| PC          | PC-PT       | 192.170.60.2 | 255.255.255.0 | 192.170.60.1    |
| Laptop      | Laptop-PT   | 192.170.60.3 | 255.255.255.0 | 192.170.60.1    |
| PC          | PC-PT       | 192.170.60.4 | 255.255.255.0 | 192.170.60.1    |
| Laptop      | Laptop-PT   | 192.170.60.5 | 255.255.255.0 | 192.170.60.1    |
| Server      | DNS Server  | 192.170.60.7 | 255.255.255.0 | 192.170.60.1    |
| Server      | HTTP Server | 192.170.60.6 | 255.255.255.0 | 192.170.60.1    |

4. Servers

| Server Type | Function               | IP Address   | Description                                                                              |
| ----------- | ---------------------- | ------------ | ---------------------------------------------------------------------------------------- |
| DNS Server  | Domain Name Resolution | 192.170.60.7 | Resolves domain names (e.g., [www.example.com](http://www.example.com)) to IP addresses. |
| HTTP Server | Web Hosting            | 192.170.60.6 | Hosts web pages accessible by clients in both LANs.                                      |

5. Connections

| Connection Type | Devices Connected             | Description                        |
| --------------- | ----------------------------- | ---------------------------------- |
| Ethernet Cable  | Router0 ↔ Switch0             | Connects router to Left LAN        |
| Ethernet Cable  | Router0 ↔ Switch1             | Connects router to Right LAN       |
| Ethernet Cable  | Switch0 ↔ PCs/Laptops         | Provides connectivity in Left LAN  |
| Ethernet Cable  | Switch1 ↔ PCs/Laptops/Servers | Provides connectivity in Right LAN |

6. IP Configuration Summary

| Network         | Subnet Mask   | Default Gateway | Connected Devices         |
| --------------- | ------------- | --------------- | ------------------------- |
| 192.170.50.0/24 | 255.255.255.0 | 192.170.50.1    | 4 PCs/Laptops             |
| 192.170.60.0/24 | 255.255.255.0 | 192.170.60.1    | 4 PCs/Laptops + 2 Servers |

(d) Testing of network communication 

<img width="535" height="253" alt="Screenshot 2025-11-08 100839" src="https://github.com/user-attachments/assets/0e8ab304-1cb2-49ae-9953-ff330e038f43" />

<img width="851" height="307" alt="image" src="https://github.com/user-attachments/assets/2e837595-a7ed-459d-90b7-c198bc424baa" />
