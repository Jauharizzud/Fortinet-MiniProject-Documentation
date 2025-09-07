# FortiGate Inter-VLAN Routing Lab

This repository documents the Inter-VLAN Routing setup using **FortiGate Firewall** on a GNS3/PNETLab topology with a **Cisco IOU Layer 2 Switch** and VPCs.

## 🚀 Topology Overview

- **Firewall:** FortiGate (VM/Device / Cloud)
- **Switch:** SW1 → Cisco IOU Layer 2 Switch
- **VLANs & Gateways:**
  | VLAN  | Subnet           | Gateway         | Switch |
  |-------|-----------------|----------------|--------|
  | VLAN10| 192.168.10.0/24 | 192.168.10.1   | SW1    |
  | VLAN20| 192.168.20.0/24 | 192.168.20.1   | SW1    |
- **Trunk port:** Cisco Switch ↔ FortiGate (includes VLAN10 & VLAN20)
- **VPCs:** Connected to access ports according to their VLANs

## ⚙️ Configuration Highlights

### ✅ On FortiGate
- VLAN interfaces created for each VLAN with IP gateway
- DHCP pool enabled for each VLAN
- Firewall policies configured for **intra- and inter-VLAN traffic**
- Aliases can be used for documentation purposes

### ✅ On Switch (Cisco IOU / L2)
- Access ports assigned to respective VLANs
- Trunk port to FortiGate configured with all VLANs
- **Useful commands:**
  - `show vlan brief` 
  - `show interfaces trunk` 
  - `show mac address-table` 

## 🔍 Useful Commands

### On FortiGate
```bash
show system interface                 # Check interface & VLAN IP
show firewall policy                  # Check firewall policies
show system dhcp server               # Check DHCP leases
