# Enterprise Network Lab — Static Routing & OSPF Default Route Advertisement

## Overview

This section documents the static routing and OSPF default route configurations implemented across three enterprise network sites:

- Headquarters (HQ)
- Branch 1 (BR1)
- Branch 2 (BR2)

The configuration includes default static routes on Cisco ASA firewalls, routing toward internal VLAN networks, OSPF default route advertisement, and routing table verification.

---

## 1. ASA Firewall Default Route Configuration

### 1.1 Configuring Default Static Routes

Configured default static routes on the ASA firewalls to forward traffic destined for unknown networks toward their respective site routers.

Similar configurations were implemented across HQ, BR1, and BR2.

**ASA Firewall — Default Static Route Configuration**

<img width="640" height="402" alt="ASA firewall default static route configuration" src="https://github.com/user-attachments/assets/09fff912-c099-4629-add9-f0a405ff5235" />

---

## 2. Internal Routing & OSPF Configuration

### 2.1 Configuring Routes Toward Internal VLAN Networks

Configured routing on the site routers to provide a return path toward the internal VLAN networks behind each site's ASA firewall.

**Site Router — Routing Configuration**

<img width="640" height="403" alt="Site router routing configuration" src="https://github.com/user-attachments/assets/25279bfd-1bd9-47ed-b170-bcecf9cf1b49" />

### 2.2 Advertising the Default Route Through OSPF

Configured OSPF to advertise the default route to participating routers within each site's OSPF routing domain.

This allows internal Layer 3 core switches to learn a default route dynamically.

**OSPF — Default Route Advertisement**

<img width="451" height="60" alt="OSPF default information originate configuration" src="https://github.com/user-attachments/assets/6b00d054-6014-4378-a806-bbcebd82cf92" />

---

## 3. Routing Table Verification

### 3.1 Verifying Default Route Propagation

Verified that the Layer 3 core switches learned the advertised default route through OSPF.

Used the following Cisco IOS command to inspect the routing table:

```bash
show ip route
```

**Core Switch — Default Route Verification**

<img width="552" height="241" alt="Core switch routing table showing learned default route" src="https://github.com/user-attachments/assets/1a314308-bc7a-483b-ba50-2d94b812c165" />
