Task No. 4: To implementation & test the static routing using GUI and CLI mode.

(a) Objective :-

The objective of this experiment is to implement and verify static routing between multiple networks 
using both the Graphical User Interface (GUI) and Command Line Interface (CLI) modes in Cisco 
Packet Tracer. 

This activity aims to demonstrate how routers can be manually configured with static routes to 
establish communication between different networks without using any dynamic routing protocols. 

By the end of this experiment, users will be able to: 

Configure static routes between routers. 

Assign appropriate IP addresses and subnet masks to interfaces. 

Verify network connectivity using ping and traceroute commands.

Understand the difference between GUI-based and CLI-based configuration methods for routing. 

(b) Network Topology :-

<img width="1033" height="490" alt="image" src="https://github.com/user-attachments/assets/0f0cda6a-7e82-4557-b45f-eeb594195e1e" />

(c) Componentand devices used and its configuration :-

1) IP addressing table

| Device Label (on diagram)      | Device Type | IP Address                                  |   Subnet Mask | Default Gateway |
| ------------------------------ | ----------: | ------------------------------------------- | ------------: | --------------- |
| PC-PT (left)                   |          PC | 192.168.10.2                                | 255.255.255.0 | 192.168.10.1    |
| Laptop-PT (left)               |      Laptop | 192.168.10.3                                | 255.255.255.0 | 192.168.10.1    |
| PC-PT (left)                   |          PC | 192.168.10.4                                | 255.255.255.0 | 192.168.10.1    |
| Laptop-PT (left)               |      Laptop | 192.168.10.5                                | 255.255.255.0 | 192.168.10.1    |
| PC-PT (right)                  |          PC | 192.168.20.2                                | 255.255.255.0 | 192.168.20.1    |
| Laptop-PT (right)              |      Laptop | 192.168.20.3                                | 255.255.255.0 | 192.168.20.1    |
| PC-PT (right)                  |          PC | 192.168.20.4                                | 255.255.255.0 | 192.168.20.1    |
| Laptop-PT (right)              |      Laptop | 192.168.20.5                                | 255.255.255.0 | 192.168.20.1    |
| Router (ISR4331)               |      Router | 192.168.10.1 (Gi0/0) / 192.168.20.1 (Gi0/1) | 255.255.255.0 | N/A             |
| Switch (Left) mgmt (optional)  |      Switch | 192.168.10.254                              | 255.255.255.0 | 192.168.10.1    |
| Switch (Right) mgmt (optional) |      Switch | 192.168.20.254                              | 255.255.255.0 | 192.168.20.1    |

3) Router routing table

   This is small — the router has two directly connected networks, so the routing table will show connected routes:
   Router# show ip route
Codes: C - connected, S - static, R - RIP, ...
C    192.168.10.0/24 is directly connected, GigabitEthernet0/0
C    192.168.20.0/24 is directly connected, GigabitEthernet0/1
      (other networks would appear here if added)

4) Sample configuration commands

Below are minimal, copy-paste friendly configs for the router and both switches (Cisco IOS style). Adjust interface names if your Packet Tracer device ports differ.

enable
configure terminal
hostname Router4

! Left LAN on Gi0/0
interface GigabitEthernet0/0
 description To-Left-Switch
 ip address 192.168.10.1 255.255.255.0
 no shutdown

! Right LAN on Gi0/1
interface GigabitEthernet0/1
 description To-Right-Switch
 ip address 192.168.20.1 255.255.255.0
 no shutdown

! Optional: simple security and name
ip route 0.0.0.0 0.0.0.0 <ISP-next-hop>   

write memory
4) Packet flow (step-by-step example)

Example: PC-left (192.168.10.2) pings Laptop-right (192.168.20.3).

Source forms packet: PC 192.168.10.2 wants to reach 192.168.20.3 → sees destination is outside its /24 → send to default gateway 192.168.10.1 (Router).

PC ARP for gateway: PC checks ARP table for 192.168.10.1. If no entry, it broadcasts ARP on left switch.

Switch forwards ARP: Left switch receives ARP broadcast and forwards to the switch port where router Gi0/0 is connected.

Router replies to ARP: Router responds with its MAC; PC updates ARP and sends the IP packet to router MAC.

Router receives and routes: Router accepts packet on Gi0/0, looks up destination 192.168.20.3 — finds directly connected network via Gi0/1.

Router forwards out Gi0/1: Router rewrites L2 (MAC) header to the next-hop on right LAN and sends packet to the right switch.

Right switch forwards to host: Right switch receives and forwards the frame out the port where 192.168.20.3 is connected (based on its MAC table).

Destination receives packet: Laptop-right receives, replies using the same procedure (dest is outside -> set gateway 192.168.20.1), router forwards back.

5) Useful verification / troubleshooting commands
On Router:

show ip interface brief — confirm interfaces and IPs

show ip route — view routing table

show arp — ARP entries

show ip interface GigabitEthernet0/0 — detailed interface status

ping 192.168.20.3 — test end-to-end from router

On Switch:

show vlan brief — check VLANs

show mac address-table — see learned MACs and ports

show ip interface Vlan1 — see management interface status

show running-config — inspect config

On PC (Packet Tracer end device):

Use ipconfig / ping / check default gateway and subnet mask.

If ping fails, check ARP table (on PC) and MAC table (on switch).

(d) ping command :-

<img width="513" height="248" alt="Screenshot 2025-11-15 205058" src="https://github.com/user-attachments/assets/ebea4d24-71ff-48a6-bce0-51dc40c8bbe0" />
<img width="752" height="494" alt="Screenshot 2025-11-15 204647" src="https://github.com/user-attachments/assets/7e0d5199-2733-4355-a7a3-0c0ae5b31dcc" />

