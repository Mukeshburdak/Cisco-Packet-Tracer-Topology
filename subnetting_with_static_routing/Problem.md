🖧 Subnetting With Static Routing in Packet Tracer Topology
-
Description: Packet Tracer topology with one core router (Router3) connecting two /25 subnets, and two branch routers (Router1, Router2) each serving a /24 LAN. Routers are interconnected using /24 links.
<p align="center"> <img width="1539" height="686" alt="Screenshot 2025-12-05 161712" src="https://github.com/user-attachments/assets/c1176478-fad1-4e84-81b9-06b427b008dd" /></p>

<p align="center"> Figure: Topology diagram</p>

---
🔹 Network summary
-
Routers: Router3 (core), Router1 (branch), Router2 (branch)

Switches: One switch per LAN (access switches)

End devices: PCs and laptops in each LAN

Routing: Static routing (shown below). You may replace with a routing protocol (OSPF/EIGRP) if needed.

---
🔹 IP addressing plan (as shown in the diagram)
-
Router-to-Router links (point-to-point — /24)

| Link              | Network           | Router A addr           | Router B addr           |
| ----------------- | ----------------- | ----------------------- | ----------------------- |
| Router3 ↔ Router1 | `192.150.40.0/24` | Router1: `192.150.40.3` | Router3: `192.150.40.2` |
| Router3 ↔ Router2 | `192.150.50.0/24` | Router3: `192.150.50.2` | Router2: `192.150.50.3` |
| Router1 ↔ Router2 | `192.150.60.0/24` | Router1: `192.150.60.2` | Router2: `192.150.60.3` |

LAN subnets

| LAN                  | Network             | Subnet mask       | Gateway (router)          | Example hosts shown                |
| -------------------- | ------------------- | ----------------- | ------------------------- | ---------------------------------- |
| LAN-A (left)         | `192.150.10.0/25`   | `255.255.255.128` | Router3: `192.150.10.1`   | `192.150.10.2`, `192.150.10.3`     |
| LAN-B (left, second) | `192.150.10.128/25` | `255.255.255.128` | Router3: `192.150.10.129` | `192.150.10.130`, `192.150.10.131` |
| LAN-C (center)       | `192.150.20.0/24`   | `255.255.255.0`   | Router1: `192.150.20.1`   | `192.150.20.2`, `192.150.20.3`     |
| LAN-D (right)        | `192.150.30.0/24`   | `255.255.255.0`   | Router2: `192.150.30.1`   | `192.150.30.2`, `192.150.30.3`     |


Note: I used /25 to match the two contiguous 192.150.10.0 and 192.150.10.128 subnets shown in your image.

---
🔹 Router configuration snippets
-
Replace g0/0, g0/1, s0/0/0, s0/0/1 with the actual interfaces in your Packet Tracer device if they differ.

Router3 (core)

enable

conf t

🔥 LAN interfaces

interface g0/0

 ip address 192.150.10.1 255.255.255.128
 
 no shutdown

interface g0/1

 ip address 192.150.10.129 255.255.255.128
 
 no shutdown

🔥 P2P to Router1

interface s0/0/0

 ip address 192.150.40.3 255.255.255.0
 
 no shutdown

🔥 P2P to Router2

interface s0/0/1

 ip address 192.150.50.3 255.255.255.0
 
 no shutdown

end

write

Router1 (center branch)

enable

conf t

🔥 LAN-C

interface g0/0

 ip address 192.150.20.1 255.255.255.0
 
 no shutdown

🔥 P2P to Router3

interface s0/0/0

 ip address 192.150.40.2 255.255.255.0
 
 no shutdown

🔥 P2P to Router2

interface s0/0/1

 ip address 192.150.60.3 255.255.255.0
 
 no shutdown

end

write

Router2 (right branch)

enable

conf t

🔥 LAN-D

interface g0/0

 ip address 192.150.30.1 255.255.255.0
 
 no shutdown

🔥 P2P to Router1

interface s0/0/0

 ip address 192.150.60.2 255.255.255.0
 
 no shutdown

🔥 P2P to Router3

interface s0/0/1

 ip address 192.150.50.2 255.255.255.0
 
 no shutdown

end

write

---
🔹 Static routes 
-
To enable full connectivity using static routes, add the following:

🏷On Router3

ip route 192.150.20.0 255.255.255.0 192.150.40.3

ip route 192.150.30.0 255.255.255.0 192.150.50.3

🏷On Router1

ip route 192.150.10.0 255.255.255.128 192.150.40.2

ip route 192.150.10.128 255.255.255.128 192.150.40.2

ip route 192.150.30.0 255.255.255.0 192.150.60.3

🏷On Router2

ip route 192.150.10.0 255.255.255.128 192.150.50.2

ip route 192.150.10.128 255.255.255.128 192.150.50.2

ip route 192.150.20.0 255.255.255.0 192.150.60.2


These static routes make every network reachable from every router. If you prefer a dynamic protocol, use OSPF for simpler configuration.

---
🔹 PC / Laptop settings (examples)
-
🏷LAN-A PC

IP: 192.150.10.2

Mask: 255.255.255.128

Gateway: 192.150.10.1

🏷LAN-B Laptop

IP: 192.150.10.130

Mask: 255.255.255.128

Gateway: 192.150.10.129

🏷LAN-C PC

IP: 192.150.20.2

Mask: 255.255.255.0

Gateway: 192.150.20.1

🏷LAN-D Laptop

IP: 192.150.30.3

Mask: 255.255.255.0

Gateway: 192.150.30.1

---
🎯 Verification & troubleshooting
-
From any PC, run:

ping <other-host-ip>

e.g., ping 192.150.30.2


On routers:

show ip route

show ip interface brief

show running-config


If pings fail:

Check interface status (no shutdown) and link lights on switches.

Verify gateway, IP, and mask on end devices.

Verify static routes exist on each router.

Use traceroute or Packet Tracer simulation mode to inspect where packets are dropped.

---
🧩 Notes & suggestions
-
The two 192.150.10.x subnets are implemented as /25 segments (0–127 and 128–255) per your diagram. If you want smaller subnets, convert to /26 or use VLSM and adjust router IPs accordingly.

For learning, replacing static routes with OSPF (single area) will simplify configuration and automatically propagate routes.

---
