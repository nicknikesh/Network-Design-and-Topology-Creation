## CaseStudy: Network Design and Topology Creation

# Name:NIKESH KUMAR C
# Reg No:212223040137

## INTRODUCTION:

*    In modern enterprise environments, network design plays a crucial role in ensuring seamless communication, secure data flow, and efficient resource sharing. This case study involves the design and simulation of three enterprise network topologies, each functioning as an independent LAN and interconnected through routers to form a scalable multi-network architecture.

*    The objective of this experiment is to configure and test an enterprise-style network that uses proper IP addressing, routing, and connectivity validation. By assigning IPs to end devices, configuring router interfaces, and enabling static routing, we ensure that all three networks communicate effectively. The simulation also verifies network performance using the ping command, demonstrating reliable end-to-end connectivity.

*  This experiment also verifies whether the configured network supports successful end-to-end connectivity using the ping command.

## NETWORK DIAGRAM:
<img width="1410" height="879" alt="Screenshot 2025-11-21 195833" src="https://github.com/user-attachments/assets/8e341e8c-09b1-49e6-856d-6e2b919e4fdf" />


## DESCRIPTION:
The enterprise network model contains three separate LAN topologies, each representing a department-level network. These LANs are connected to routers, which form the backbone of the inter-network communication.
| LAN      | Network Address | Default Gateway | PCs                    |
| -------- | --------------- | --------------- | ---------------------- |
| **LAN1** | 192.168.10.0/24 | 192.168.10.1    | PC0 – 10.2, PC1 – 10.3 |
| **LAN2** | 192.168.20.0/24 | 192.168.20.1    | PC2 – 20.2, PC3 – 20.3 |
| **LAN3** | 192.168.30.0/24 | 192.168.30.1    | PC4 – 30.2, PC5 – 30.3 |

The design includes:

Configuring router interfaces to establish backbone connectivity

Assigning static routes to ensure enterprise-wide reachability

Setting up end devices with proper IP configurations

Validating the connectivity across the entire simulated enterprise topology


Routers are also interconnected using Serial interfaces forming:

* 10.0.0.0/30 (Router0 ↔ Router1)

* 11.0.0.0/30 (Router1 ↔ Router2)

The main goal is to configure:

* 1.Router interfaces with proper IPs

* 2.Static routes so all routers know each other's networks

* 3.PC configurations using correct IP, subnet mask, and gateway

* 4.Testing connectivity using ping

## PROCEDURE:
# Step 1 — Configure PC IP Addresses:

* PC0 (LAN1)
IP Address: 192.168.10.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.10.1

* PC1 (LAN1)
IP Address: 192.168.10.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.10.1

* PC2 (LAN2)
IP Address: 192.168.20.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.20.1

* PC3 (LAN2)
IP Address: 192.168.20.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.20.1

* PC4 (LAN3)
IP Address: 192.168.30.2
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.30.1

* PC5 (LAN3)
IP Address: 192.168.30.3
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.30.1

# Step 2 — Configure Router Interfaces:
* Router0
```
int fa0/0
 ip address 192.168.10.1 255.255.255.0
 no shut
!
int s2/0
 ip address 10.0.0.1 255.255.255.252
 clock rate 64000
 no shut
```

* Router1
```
int fa0/0
 ip address 192.168.20.1 255.255.255.0
 no shut
!
int s2/0
 ip address 10.0.0.2 255.255.255.252
 no shut
!
int s3/0
 ip address 11.0.0.1 255.255.255.252
 no shut
```
* Router2
```
int fa0/0
 ip address 192.168.30.1 255.255.255.0
 no shut
!
int s2/0
 ip address 11.0.0.2 255.255.255.252
 clock rate 64000
 no shut
```
# Step 3 — Configure Static Routing
* Router0
```
ip route 192.168.20.0 255.255.255.0 10.0.0.2
ip route 192.168.30.0 255.255.255.0 10.0.0.2
```
* Router1
``
ip route 192.168.10.0 255.255.255.0 10.0.0.1
ip route 192.168.30.0 255.255.255.0 11.0.0.2
```
* Router2
```
ip route 192.168.10.0 255.255.255.0 11.0.0.1
ip route 192.168.20.0 255.255.255.0 11.0.0.1
```
```
# Step 4 — Verify Using PING:

* From PC0 → PC3

C:\> ping 192.168.20.3
Reply from 192.168.20.3: bytes=32 time<1ms TTL=128


* From PC4 → PC1

C:\> ping 192.168.10.3
Reply from 192.168.10.3: bytes=32 time<1ms TTL=128


All PCs across three LANs should successfully communicate.

## OUTPUR:

* All PC IP-confrations:

<img width="541" height="367" alt="image" src="https://github.com/user-attachments/assets/43889710-d0e9-4977-b634-10c6c5c33a7d" />

<img width="542" height="356" alt="image" src="https://github.com/user-attachments/assets/174ff855-1eaf-4d7e-acd4-4758bf62a999" />

<img width="542" height="367" alt="image" src="https://github.com/user-attachments/assets/d683fd66-e7ae-4d78-b971-0ac871ea3c36" />

* All  successful ping connections:

<img width="545" height="367" alt="image" src="https://github.com/user-attachments/assets/328878fb-932d-44f4-a97b-5c11d35c58e2" />


## RESULT:

* The network was successfully configured with three LAN segments connected through routers using static routing. All PCs received valid IPv4 addresses, and routing ensured cross-network communication.

* The ping results confirmed successful connectivity between all devices in LAN1, LAN2, and LAN3. This shows that the IP addressing, router configuration, and static routing were implemented correctly.
