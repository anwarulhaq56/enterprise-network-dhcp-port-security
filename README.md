# enterprise-network-dhcp-port-security
Cisco Packet Tracer enterprise network implementing DHCP, VLANs, inter-VLAN routing, and switch port security.
# Enterprise Network — DHCP & Port Security

A practical Cisco Packet Tracer project demonstrating enterprise network segmentation, DHCP services, inter-VLAN routing, and switch port security.

## 📌 Project Overview

This project presents the design and implementation of a small enterprise network for three departments:

- Human Resources (HR)
- Information Technology (IT)
- Finance

The network uses VLAN segmentation to logically separate departmental traffic and Router-on-a-Stick to provide communication between VLANs.

The Cisco 2911 router is configured as a DHCP server to automatically provide IP addressing information to the client PCs. Cisco switch Port Security is implemented to restrict access to authorized devices and detect unauthorized MAC addresses.

The project also includes network verification, connectivity testing, an intentional Port Security violation, interface recovery, and configuration verification.

## 🏗️ Network Topology

**Devices:**
- 1 × Cisco 2911 Router
- 1 × Cisco 2960 Switch
- 6 × PCs

**Departments:**
- HR → VLAN 10
- IT → VLAN 20
- Finance → VLAN 30

**Router:** R1 — Router-on-a-Stick + DHCP Server

**Switch:** SW1 — VLAN Segmentation + Port Security

**Trunk:** SW1 Fa0/1 ↔ R1 G0/0

## 🌐 IP Addressing & VLAN Design

| VLAN | Department | Network | Default Gateway |
|---|---|---|---|
| 10 | HR | 192.168.10.0/24 | 192.168.10.1 |
| 20 | IT | 192.168.20.0/24 | 192.168.20.1 |
| 30 | Finance | 192.168.30.0/24 | 192.168.30.1 |

Client IP addresses are assigned automatically through DHCP.

## 🔐 Port Security

Port Security was configured on all access ports with a maximum of one secure MAC address per port.

- Fa0/2 → Static MAC address
- Fa0/3–Fa0/7 → Sticky MAC learning
- Maximum MAC addresses → 1
- Violation mode → Shutdown

An unauthorized-device test was performed by connecting PC2 to the secured Fa0/2 port. The switch detected the MAC address violation and placed the interface into the Secure-shutdown state.

The authorized PC was then reconnected and the interface was successfully recovered.

## ⚙️ Technologies Implemented

- IPv4 Addressing
- VLANs
- IEEE 802.1Q Trunking
- Router-on-a-Stick
- Inter-VLAN Routing
- DHCP
- DHCP Pools
- DHCP Address Exclusion
- MAC Address Security
- Static Port Security
- Sticky MAC
- Network Verification
- Connectivity Testing
- Troubleshooting

## 🧪 Verification & Testing

The following verification and testing procedures were performed:

```text
show vlan brief
show interfaces trunk
show ip interface brief
show ip dhcp pool
show ip dhcp binding
show port-security
show port-security interface fa0/2
show running-config
```

Connectivity was tested between:

- PC1 → PC2 (same VLAN)
- PC1 → PC3 (HR → IT)
- PC1 → PC5 (HR → Finance)

All required connectivity tests were successful during normal operation.

## 🛠️ Troubleshooting Case Study

A Port Security violation was intentionally simulated.

**Scenario:**
- Fa0/2 was authorized for PC1.
- PC2 was connected to Fa0/2.
- PC2 had a different MAC address.
- The switch detected the violation.
- Fa0/2 entered Secure-shutdown.
- PC2 was removed.
- PC1 was reconnected.
- The interface was reset using `shutdown` and `no shutdown`.
- Network access was successfully restored.

This demonstrated practical Port Security verification, violation detection, and recovery.

## 📂 Repository Structure

```text
enterprise-network-dhcp-port-security/
│
├── Configuration/
│   ├── router-config.txt
│   └── switch-config.txt
│
├── Documentation/
│   └── Project-02-Report.pdf
│
├── Screenshots/
│   ├── 01-final-topology.png
│   ├── 02-vlan-verification.png
│   ├── 03-trunk-verification.png
│   ├── 04-router-verification.png
│   ├── 05-dhcp-pool-verification.png
│   ├── 06-dhcp-bindings.png
│   ├── 07-PC1-DHCP-configuration.png
│   ├── 08a-same-vlan-ping.png
│   ├── 08b-inter-vlan-it-ping.png
│   ├── 08c-inter-vlan-finance-ping.png
│   ├── 09-port-security-summary.png
│   ├── 10-port-security-violation.png
│   ├── 11-port-security-recovery.png
│   ├── 12a-router-running-config-part1.png
│   ├── 12b-router-running-config-part2.png
│   ├── 13a-switch-running-config-part1.png
│   └── 13b-switch-running-config-part2.png
│
├── Enterprise-Network-DHCP-Port-Security.pkt
└── README.md
```

## 📄 Documentation

The complete project report is available in the `Documentation` folder.

The report includes:

- Project Overview
- Project Objectives
- Network Scenario
- Network Topology
- IP Addressing & VLAN Design
- Device Configuration
- Verification & Testing
- Troubleshooting Case Study
- Results
- Future Improvements

## 🎯 Learning Outcomes

This project strengthened practical skills in:

- Enterprise VLAN design
- Cisco IOS configuration
- Router-on-a-Stick
- DHCP configuration and verification
- Switch Port Security
- MAC address management
- Network troubleshooting
- Connectivity testing
- Technical documentation

## 🚀 Future Development

Future projects will build upon this foundation by introducing:

- OSPF dynamic routing
- ACLs
- NAT/PAT
- SSH
- STP and EtherChannel
- VPN and firewall concepts
- IDS/IPS
- Linux networking
- Python network automation
- Cloud networking

## 📌 Project Information

**Project:** Project 02 — Enterprise Network with DHCP & Port Security  
**Type:** Networking / Network Engineering  
**Platform:** Cisco Packet Tracer  
**Focus:** Network Engineering & Network Security  
**Author:** Anwar Ul Haq
