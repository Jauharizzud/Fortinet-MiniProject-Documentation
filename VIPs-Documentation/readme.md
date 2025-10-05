# FortiGate VIP Configuration Lab

This repository documents the **Virtual IP (VIP) configuration** using **FortiGate Firewall** with **MikroTik Router** integration on GNS3 topology, demonstrating Destination NAT (DNAT) and port forwarding.

## 🚀 Topology Overview

- **Firewall:** FortiGate VM 7.0.9
- **Server:** MikroTik RouterOS 6.49.11
- **Client:** VPC/PC

**IP Addressing:**

| Device    | Interface | IP Address        | Role    |
|-----------|-----------|-------------------|---------|
| FortiGate | port10    | 192.168.0.162/24  | WAN     |
| FortiGate | port10    | 192.168.0.169/24  | WAN (VIP) |
| FortiGate | port1     | 172.16.100.254/24 | DMZ     |
| FortiGate | port2     | 192.168.10.254/24 | LAN     |
| MikroTik  | ether0    | 172.16.100.1/24   | DMZ     |
| Client    | ether0    | 192.168.10.1/24   | LAN     |

## ⚙️ Configuration Highlights

### ✅ On FortiGate

- VIP created with secondary IP (192.168.0.169)
- Port forwarding: External 80 → Internal 80 (MikroTik)
- Firewall policy: WAN → DMZ (VIPs-Mikrotik)
- Zone-based security implemented

### ✅ On MikroTik

- Default gateway: 172.16.100.254 (FortiGate)
- Webfig service enabled on port 80

## 🔍 Useful Commands

### On FortiGate

```bash
show firewall vip                     # Check VIP configuration
show firewall policy                  # Check firewall policies
get router info routing-table all     # Check routing table
diagnose firewall vip list            # Monitor VIP traffic
```

### On MikroTik

```bash
/ip address print                     # Check IP addresses
/ip route print                       # Check routes
/ip service print                     # Check enabled services
/ping 172.16.100.254                  # Test connectivity to FortiGate
```

## 🧪 Testing

**Access MikroTik Webfig via VIP:**
- Browser: `http://192.168.0.169:80`
- CLI: `telnet 192.168.0.169 80`

**Verify VIP Status:**
- GUI: Policy & Objects → Virtual IPs
- CLI: `diagnose firewall vip list VIPs-Mikrotik`

