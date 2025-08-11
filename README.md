# HQ_BR_Network_Topology
A Cisco Packet Tracer project demonstrating an enterprise network with Headquarters and Branch Office connectivity. Includes VLAN segmentation, inter-VLAN routing, trunk links, and static routing between sites for CCNA-level practice.
# Enterprise Branch & Headquarters Network Topology with VLANs and Inter-VLAN Routing

## 📋 Overview
This Packet Tracer project simulates a real-world enterprise network with two locations:
- **Headquarters (HQ)**
- **Branch Office (BR)**

The network is designed to demonstrate:
- VLAN segmentation for multiple departments
- Inter-VLAN routing using Layer 3 switches
- Router-to-router WAN connectivity
- Trunk links between switches
- Department-based IP addressing

---

## 🏢 Network Structure

### Headquarters (HQ)
- **Departments:**
  - IT
  - Logistics
  - HR
  - Sales
- **Core Switch (L3):** SW-HQ-CORE
- **Access Switch (L2):** SW-HQ-ACC
- **Router:** R-HQ

### Branch Office (BR)
- **Departments:**
  - IT
  - Logistics
  - HR
  - Finance
  - Sales
- **Core Switch (L3):** SW-BR-CORE
- **Access Switch (L2):** SW-BR-ACC
- **Router:** R-BR

---

## 📡 VLAN Configuration

| VLAN ID | Department | HQ Network      | BR Network      |
|---------|------------|-----------------|-----------------|
| 10      | IT         | 10.10.10.0/24   | 10.20.10.0/24   |
| 20      | Logistics  | 10.10.20.0/24   | 10.20.20.0/24   |
| 30      | HR         | 10.10.30.0/24   | 10.20.30.0/24   |
| 40      | Sales      | 10.10.40.0/24   | 10.20.40.0/24   |
| 50      | Finance    | -               | 10.20.50.0/24   |
| 99      | Management | 10.10.99.0/24   | 10.20.99.0/24   |

---

## 🔗 Trunk Configuration
- **HQ:**
  - SW-HQ-CORE Gi1/0/1 <-> SW-HQ-ACC Gi1/0/1
- **Branch:**
  - SW-BR-CORE Gi1/0/1 <-> SW-BR-ACC Gi1/0/1
- **Allowed VLANs:** `10,20,30,40,50,99`
- **Native VLAN:** `99`
- **Encapsulation:** `dot1q`

---

## 🌐 Routing
- **Inter-VLAN Routing:** Enabled on both L3 core switches (`ip routing`)
- **WAN Connection:** Point-to-point link between R-HQ and R-BR
- **Static Routes:** Configured on both routers to allow communication between HQ and Branch networks

---

## 🖥️ End Device Configuration
Each PC is assigned:
- An IP address within its department VLAN subnet
- The default gateway set to the VLAN SVI address on the L3 core switch

Example (HQ IT PC):
