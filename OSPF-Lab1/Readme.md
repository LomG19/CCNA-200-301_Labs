# OSPF Lab – CCNA 200-301  
**Author:** Mugisha Loic  

---

##  Objective  
- Configure and verify OSPF on 4 routers  
- Ensure proper routing between all networks  
- Use clean subnetting and assign proper router IDs.
- Set interfaces that aren't facing other routers as passive to avoid unwanted neighbor relationships.
- Set one router connecting to the ISP as the ASBR.

---

## Topology Overview  


![OSPF Topology](./Images/OSPF-LAB1-Topology.png)

---
## Pre-Configuration Summary  
Before enabling OSPF, the following configurations were completed on all routers:
- Assigned hostnames (`R1`, `R2`, `R3`, `R4`,`ISP1`)
- Configured interface IP addresses and subnet masks
- Added loopback interfaces for router ID purposes
- Verified basic connectivity using `ping`
## 📚 Lab Details  

| Device | Interfaces          | IP Addresses                         | Loopback Address |
|--------|---------------------|--------------------------------------|------------------|
| R1     | G0/0, f2/1, s1/0    | 10.0.12.1 / 10.0.13.1, 203.0.113.1   |  1.1.1.1         |
| R2     | G0/0, G0/1          | 10.0.12.2 / 10.0.24.1                |  2.2.2.2         |
| R3     | f2/0, f2/1          | 10.0.34.1, 10.0.13.2                 |  3.3.3.3         |
| R4     | f2/1, f2/0, g3/0    | 10.0.34.2, 10.0.24.2, 192.168.4.254  |  4.4.4.4         |

> Each router connects to two directly connected networks and runs OSPF process ID 1.

---

## ⚙️ OSPF Configuration Snippets

### 🔹 R1 OSPF
```bash
router ospf 1
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.13.0 0.0.0.3 area 0
 network 1.1.1.1 0.0.0.0 area 0
 network 203.0.113.1 0.0.0.3 area 0
 passive-interface l0
 passive-interface s1/0
 default-information originate
```
### 🔹 R2 OSPF
```bash
router ospf 2
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.24.0 0.0.0.3 area 0
 network 2.2.2.2 0.0.0.0 area 0
 passive-interface l0
```
### 🔹 R3 OSPF
```bash
router ospf 3
 network 10.0.13.0 0.0.0.3 area 0
 network 10.0.34.0 0.0.0.3 area 0
 network 3.3.3.3 0.0.0.0 area 0
 passive-interface l0
```
### 🔹 R4 OSPF
```bash
router ospf 4
 network 10.0.34.0 0.0.0.3 area 0
 network 10.0.24.0 0.0.0.3 area 0
 network 192.168.4.0 0.0.0.255 area 0
 network 2.2.2.2 0.0.0.0 area 0
 passive-interface l0
 passive-interface g3/0
```

> Full configurations comands will be added in text files.
