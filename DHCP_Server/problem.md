Task No. 6: To configuring a DHCP Server & test the network configuration.

(a) Objective :-

The objective of this experiment is to configure a DHCP (Dynamic Host Configuration Protocol) 
server in Cisco Packet Tracer and test the network configuration by automatically assigning IP 
addresses to client devices within a given network. This helps in understanding how DHCP simplifies 
IP management, reduces manual configuration errors, and ensures efficient network connectivity. 

(b) Network Topology :-
<img width="1236" height="486" alt="image" src="https://github.com/user-attachments/assets/d4486474-eb24-44f2-ba6c-d7737db22566" />
Fig. No. 3.1: DHCP Server 

(c) Configuration of different components of network topology :-
| **Component**            | **Purpose**                                                    | **Configuration Details**                                                               |
| ------------------------ | -------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| **Router**               | Connects different networks and acts as a DHCP Server.         | Configured with DHCP service, IP addresses on interfaces, and default gateway settings. |
| **Switch**               | Connects multiple end devices in the same LAN.                 | No IP assigned (Layer 2 device); ensures connectivity between DHCP server and clients.  |
| **PCs/Laptops**          | Acts as DHCP clients to obtain IP configuration automatically. | Set to “DHCP” mode in IP Configuration to receive IP address from the DHCP server.      |
| **Server (DHCP Server)** | Provides automatic IP address allocation to connected clients. | DHCP service enabled; configured with IP pool, subnet mask, default gateway, and DNS.   |

(d) Testing of network communication :-

<img width="478" height="252" alt="image" src="https://github.com/user-attachments/assets/d41a072c-0832-4565-a9f2-f309f6e1fa78" />

Fig. No. 3.2: DHCP Server Ping Command 
