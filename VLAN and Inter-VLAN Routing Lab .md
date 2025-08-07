# VLAN and Inter-VLAN Routing Lab

# Overview

This lab demonstrates how to configure VLANs on a Layer 2 switch and perform inter-VLAN routing using a Layer 3 switch. It also includes static routing to reach an external network (e.g., the internet) and troubleshooting common connectivity issues.

---

## Network Topology and Addressing Table

---

## Objectives

- Configure VLANs on SW1 and SW2
- Assign IP addresses to devices in VLANs
- Create SVI interfaces for inter-VLAN routing on SW2
- Enable IP routing on SW2
- Configure a default route to R1
- Troubleshoot connectivity to the internet

---

## Configuration Steps

### 1. VLAN Configuration on SW1 (Layer 2 Switch)

```bash
interface FastEthernet0/1
 switchport access vlan 10
 switchport mode access
!
interface FastEthernet0/2
 switchport access vlan 10
 switchport mode access
!
interface FastEthernet0/3
 switchport access vlan 30
 switchport mode access
!
interface FastEthernet0/4
 switchport access vlan 30
 switchport mode access

```

### 2. VLAN Configuration on SW2 (Layer 3 Switch)

```bash
interface GigabitEthernet1/0/3
 switchport access vlan 20
 switchport mode access
 switchport nonegotiate
!
interface GigabitEthernet1/0/4
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
!
interface GigabitEthernet1/0/5
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
```

### 3. VLAN Trunking Configuration on SW2 (Layer 3 Switch)

To allow multiple VLANs to communicate over a single link

```bash
interface GigabitEthernet1/0/1
 switchport trunk allowed vlan 10,30
 switchport mode trunk
```

### 4. SVI Configuration on SW2 (Layer 3 Switch)

To enable inter-VLAN routing on the layer 3 switch.

```bash
interface Vlan10
 mac-address 0060.5c04.5a01
 ip address 10.0.0.62 255.255.255.192
!
interface Vlan20
 mac-address 0060.5c04.5a03
 ip address 10.0.0.126 255.255.255.192
!
interface Vlan30
 mac-address 0060.5c04.5a02
 ip address 10.0.0.190 255.255.255.192
```

### 5. Default route Configuration on SW2 (Layer 3 Switch)

To provide internet access to any host in the local subnets by forwarding all requests to outside links to the gateway router 

```bash
ip route 0.0.0.0 0.0.0.0 10.0.0.194 
!
```

### 6. Static routes Configuration on R1 (Layer 3 Switch)

To enable communication with the LAN.

```bash
!
ip classless
ip route 0.0.0.0 0.0.0.0 GigabitEthernet0/0 
ip route 10.0.0.0 255.255.255.192 10.0.0.193 
ip route 10.0.0.128 255.255.255.192 10.0.0.193 
ip route 10.0.0.64 255.255.255.192 10.0.0.193
```

## Troubleshooting

### Issue

→ Hosts not able to access the internet on 1.1.1.1.

### Cause

→ No routes to the local subnets configured on the router.

### Fix

→ Configured static routes to all subnets in the LAN and solved the issue, now hosts are having connectivity to 1.1.1.1 (internet)

## What I learned

→ Even if packets go out successfully, there must always be a return path, especially with static routes.