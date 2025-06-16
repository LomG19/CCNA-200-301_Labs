# 🌐 OSPF Lab – CCNA 200-301  
**Author:** Mugisha Loic  

---

## 🧠 Objective  
- Configure and verify OSPF on 3 routers  
- Ensure proper routing between all networks  
- Use clean subnetting and assign proper router IDs  

---

## 🖥️ Topology Overview  
*(Insert topology image if available)*

![OSPF Topology](./images/OSPF-LAB1-Topology.png)

---

## 📚 Lab Details  

| Device | Interfaces | IP Addresses              |
|--------|------------|---------------------------|
| R1     | G0/0, G0/1 | 192.168.10.1 / 10.0.0.1   |
| R2     | G0/0, G0/1 | 10.0.0.2 / 172.16.0.1     |
| R3     | G0/0       | 172.16.0.2                |

> Each router connects to two directly connected networks and runs OSPF process ID 1.

---

## ⚙️ OSPF Configuration Snippets

### 🔹 R1 OSPF
```bash
router ospf 1
 router-id 1.1.1.1
 network 192.168.10.0 0.0.0.255 area 0
 network 10.0.0.0 0.0.0.3 area 0
