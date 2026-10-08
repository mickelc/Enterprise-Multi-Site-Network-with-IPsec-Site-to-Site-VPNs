# Enterprise Network Lab - OSPF Internal Routing Configuration

## 1. Layer 3 Core Switch OSPF Configuration

### 1.1 Configuring OSPF on the Core Switch

Configured OSPF on the Layer 3 core switch to advertise internal VLAN networks and establish dynamic routing with the connected ASA firewall.

**Core Switch — OSPF Configuration**

<img width="501" height="100" alt="Layer 3 core switch OSPF configuration" src="https://github.com/user-attachments/assets/f38bef9a-57f2-4ddc-a052-34e83c159feb" />

### 1.2 Configuring Passive Interfaces

Configured VLAN interfaces as passive to prevent unnecessary OSPF neighbor formation on endpoint-facing networks.

The interface connecting to the ASA firewall was excluded from passive mode to allow OSPF adjacency formation.

**Core Switch — OSPF Passive Interface Configuration**

<img width="434" height="43" alt="Core switch OSPF passive interface configuration" src="https://github.com/user-attachments/assets/52d39e9e-db3e-45da-9bc3-339e056ac7bd" />

---

## 2. Cisco ASA Firewall OSPF Configuration

### 2.1 Configuring OSPF on the ASA Firewall

Configured OSPF on the Cisco ASA firewall to establish a dynamic routing relationship with the Layer 3 core switch.

This allows routing information to be exchanged between the internal VLAN networks and the firewall.

**ASA Firewall — OSPF Configuration**

<img width="533" height="62" alt="Cisco ASA firewall OSPF configuration" src="https://github.com/user-attachments/assets/54819728-ce6c-422a-8a1b-a33eb0907fff" />

---

## 3. OSPF Neighbor Verification

### 3.1 Verifying OSPF Adjacency

Verified that an OSPF neighbor adjacency was successfully established between the Layer 3 core switch and ASA firewall.

Used the following command to inspect OSPF neighbor relationships:

```bash
show ip ospf neighbor
```

**OSPF — Neighbor Adjacency Verification**

<img width="689" height="80" alt="OSPF neighbor adjacency verification between core switch and ASA firewall" src="https://github.com/user-attachments/assets/26b65cdd-7a31-465f-800f-f9eff54c58dd" />

---

## 4. Multi-Site OSPF Implementation

Repeated the OSPF configuration across HQ, BR1, and BR2.

Each site was configured with:

- OSPF routing between the Layer 3 core switch and ASA firewall.
- Passive interfaces on endpoint-facing VLAN networks.
- Active OSPF neighbor formation on the firewall-facing transit interface.
- OSPF neighbor adjacency verification.

---
