# Enterprise Network Architecture & Security Implementation 🏨

![Network Topology](topology.png) 
*(Note: Upload a screenshot of your Packet Tracer topology and name it topology.png)*

## 📌 Executive Summary
This repository contains the complete design, simulation, and implementation of a secure, scalable, and highly efficient enterprise network for **VIC Modern Hotel**. Designed using Cisco Packet Tracer, this project demonstrates advanced system architecture, logical network segmentation, dynamic routing, and robust security protocols across a multi-floor infrastructure.

As a System Architect, my goal was to bridge the gap between physical hardware and secure digital communication, ensuring seamless departmental isolation, centralized management, and high availability.

## 🚀 Key Technologies & Protocols Implemented
- **Routing & Switching:** OSPF (Area 0), Inter-VLAN Routing (Router-on-a-Stick), Serial DCE Links.
- **Network Services:** DHCP Server Configuration, DNS Setup.
- **Security Posture:** SSH (RSA Encryption) for remote management, Layer 2 Port Security (Sticky MAC).
- **Infrastructure:** VLAN Segmentation, Wireless Access Point Integration.

---

## 🏗️ Network Architecture Overview
The network follows a hierarchical and modular design spanning three floors. The core infrastructure is housed in the IT Server Room, featuring interconnected routers utilizing `/30` subnets for efficient IP allocation.

### 1. Logical Segmentation (VLAN & IP Scheme)
To reduce broadcast domains and enforce strict security policies, each department is isolated into its own VLAN with a dedicated `/24` subnet.

| Floor | Department | VLAN ID | Network Address |
| :--- | :--- | :--- | :--- |
| **1st Floor** | Reception | VLAN 80 | `192.168.8.0 /24` |
| | Store | VLAN 70 | `192.168.7.0 /24` |
| | Logistics | VLAN 60 | `192.168.6.0 /24` |
| **2nd Floor** | Finance | VLAN 50 | `192.168.5.0 /24` |
| | HR | VLAN 40 | `192.168.4.0 /24` |
| | Sales & Marketing | VLAN 30 | `192.168.3.0 /24` |
| **3rd Floor** | IT | VLAN 10 | `192.168.1.0 /24` |
| | Admin | VLAN 20 | `192.168.2.0 /24` |

### 2. Dynamic Routing & Connectivity
- **OSPF Configuration:** Implemented Open Shortest Path First (OSPF) across all routers to ensure dynamic, fast, and reliable exchange of routing information.
- **Inter-VLAN Routing:** Configured IEEE 802.1Q encapsulation on router sub-interfaces to allow controlled communication between isolated departments.
- **Wireless Integration:** Deployed secure Wi-Fi networks on each floor, allowing mobile devices and laptops to dynamically acquire IP addresses via DHCP.

### 3. Enterprise-Grade Security
- **Secure Remote Access:** Configured SSH with hostname, domain name, and RSA key generation on all routers. VTY lines are strictly restricted to SSH-only access.
- **Switch Port Security:** Enforced strict Layer 2 security on the IT department switch. Implemented Sticky MAC addressing on port `fa0/1` (Test-PC), with the violation mode set to `shutdown` to instantly block unauthorized hardware.

---

## ⚙️ How to Run & Test the Simulation
1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer).
2. Clone this repository and open the `VIC_Hotel_Network.pkt` file.
3. **Test DHCP:** Open any PC, navigate to IP Configuration, and verify it receives an IP dynamically.
4. **Test Routing:** Ping a PC on the 1st Floor (e.g., Reception) from the 3rd Floor (e.g., Admin) to verify OSPF and Inter-VLAN routing.
5. **Test Security:** Attempt to connect an unauthorized PC to the IT switch port `fa0/1` to observe the port shutting down automatically.

---
*Designed and engineered by Hafiz Muhammad Deen.*
