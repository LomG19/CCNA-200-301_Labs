# Enterprise Network Lab - CCNA Practice Project

> A hands-on simulation of a two-branch enterprise network designed using the hierarchical model (Core, Distribution, Access).

## Objective

* To design and configure a functional, scalable, and redundant enterprise network in Cisco Packet Tracer.
* To demonstrate proficiency in core Cisco networking technologies, including Layer 2/3 redundancy, segmentation, and inter-VLAN routing.

## Tools Used

-> Cisco Packet Tracer

## Network Topology



## Implemented Protocols and Technologies

| Technology | Purpose in the Network | Key Configuration Points |
| :--- | :--- | :--- |
| **VLANs (10, 20, 30, 40, 99)** | Logically segmenting the network for security, performance, and broadcast domain control (e.g., separating Voice/Data/Wi-Fi). | PC, Phone, Server, Wi-Fi, and Management segmentation. |
| **VTPv2** | Centrally manage VLAN creation and modification on the server switch, propagating changes to VTP clients (Access Switches) across the domain. | Domain: **JeremysITLab**, Server/Client roles, pruning disabled. |
| **Layer-2 EtherChannel (LACP/PAgP)** | Provides link aggregation for **redundancy** and **increased bandwidth** between Distribution Switches in each office. | Office A: **PAgP** (Cisco Proprietary). Office B: **LACP** (Open Standard). |
| **Trunking** | Allows multiple VLANs to traverse a single link. Ensures proper VLAN encapsulation (802.1Q). | Explicitly set **Native VLAN 1000** for security. Explicitly disable DTP. |
| **Inter-VLAN Routing** | Configured on the Distribution/Core layers to allow traffic to flow between different VLANs (e.g., PCs to Servers). | Implemented using **Switched Virtual Interfaces (SVIs)** on the Distribution layer. |
| **Layer-3 EtherChannel** | Aggregates links between Core Switches for **high-speed backbone connectivity** and routing adjacency. | Configured using **PAgP** and assigned L3 IP addresses. |
| **Secure Management** | Secure access to devices. | **Enable Secret** configured, **Local User Authentication** on console line, **Unused Ports Disabled**. |
