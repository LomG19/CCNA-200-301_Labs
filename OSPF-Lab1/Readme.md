# OSPF Lab1 – Dynamic Routing with Packet Tracer

## Objective

Configure and verify OSPF (Open Shortest Path First) dynamic routing between three routers to enable full network connectivity.

## Topology Overview

- 3 Routers (R1, R2, R3)
- 3 Network segments
- Each router connected to one or two networks
- Use OSPF process ID 1
- Set router IDs manually for clarity

![Topology](./images/ospf-topology.png)

---

## ⚙️ Basic IP Schema

| Device | Interface    | IP Address     | Connected To |
|--------|--------------|----------------|--------------|
| R1     | G0/0         | 192.168.10.1/24 | PC1          |
| R1     | G0/1         | 10.0.0.1/30     | R2 (G0/1)    |
| R2     | G0/1         | 10.0.0.2/30     | R1 (G0/1)    |
| R2     | G0/0         | 10.0.0.5/30     | R3 (G0/1)    |
| R3     | G0/1         | 10.0.0.6/30     | R2 (G0/0)    |
| R3     | G0/0         | 192.168.30.1/24 | PC3          |

---

## 🔧 OSPF Configuration Summary

Apply the following on each router:

### 🔹 R1 Configuration
```bash
router ospf 1
 router-id 1.1.1.1
 network 192.168.10.0 0.0.0.255 area 0
 network 10.0.0.0 0.0.0.3 area 0

