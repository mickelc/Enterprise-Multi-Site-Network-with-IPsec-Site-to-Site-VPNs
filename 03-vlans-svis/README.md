# Enterprise Network Lab — VLANs, Trunking & Inter-VLAN Routing
## Overview
This section documents the Layer 2 and Layer 3 switching configurations implemented across three enterprise network sites:

- Headquarters (HQ)
- Branch 1 (BR1)
- Branch 2 (BR2)

The configuration includes VLAN segmentation, access port assignments, spanning-tree features, 802.1Q trunking, and Switch Virtual Interfaces (SVIs) for inter-VLAN routing.

---

## 1. Access Switch Configuration

### 1.1 VLAN Access Port Assignments

Configured access switch interfaces to assign endpoint devices to their respective VLANs.

The screenshot below demonstrates the access port configuration on BR1. Similar configurations were implemented across HQ and BR2.

**BR1 — Access Port Configuration**

<img width="604" height="516" alt="BR1 access switch port configuration" src="https://github.com/user-attachments/assets/22c6cae5-cdbb-49e3-b460-2b1dffc0362d" />

### 1.2 VLAN Configuration Verification

Verified VLAN creation and port assignments using the VLAN tables on each site's access switches.

#### Branch 1 — VLAN Table

<img width="613" height="225" alt="BR1 VLAN table" src="https://github.com/user-attachments/assets/c3bc0eb8-1172-407f-9056-be3ad53ca53d" />

#### Headquarters — VLAN Table

<img width="638" height="221" alt="HQ VLAN table" src="https://github.com/user-attachments/assets/0eeba56f-0571-42d3-92aa-33526bff3df1" />

#### Branch 2 — VLAN Table

<img width="651" height="200" alt="BR2 VLAN table" src="https://github.com/user-attachments/assets/1d06cb5a-79e2-42ad-9693-4eda57b56ebf" />

---

## 2. VLAN Trunking Configuration

### 2.1 Configuring 802.1Q Trunk Links

Configured trunk interfaces between the Layer 3 core switches and access switches to transport traffic from multiple VLANs over a single physical connection.

**BR2 — Layer 3 Switch Trunk Configuration**

<img width="532" height="165" alt="BR2 trunk interface configuration" src="https://github.com/user-attachments/assets/2c6df8d2-8481-4308-b247-ce186f198cb6" />

### 2.2 Restricting Allowed VLANs

Configured trunk interfaces to permit only the VLANs required at each site.

This helps limit unnecessary VLAN propagation across trunk links.

**Allowed VLAN Configuration**

<img width="564" height="306" alt="Trunk allowed VLAN configuration" src="https://github.com/user-attachments/assets/8e2ed938-d8d8-46c1-b2eb-cf51975db899" />

---

## 3. Layer 3 Switching & Inter-VLAN Routing

### 3.1 Configuring Switch Virtual Interfaces (SVIs)

Created SVIs on the Layer 3 core switches to provide default gateways for the respective VLANs and enable inter-VLAN routing.

Each SVI is assigned an IP address corresponding to its VLAN subnet.

**HQ — SVI Configuration**

<img width="833" height="573" alt="HQ switch virtual interface configuration" src="https://github.com/user-attachments/assets/91afe8e6-9e12-473e-877a-2540b1956696" />

### 3.2 SVI Interface Verification

Verified the configured SVIs and their operational status using the following Cisco IOS command:

```bash
show ip interface brief
```

**HQ — Interface Status After SVI Configuration**

<img width="670" height="206" alt="HQ SVI interface status verification" src="https://github.com/user-attachments/assets/240a4453-86f9-4934-8f30-98a86a01928f" />

---





