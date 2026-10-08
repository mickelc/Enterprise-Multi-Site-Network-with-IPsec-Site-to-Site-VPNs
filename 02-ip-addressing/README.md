# Enterprise Network Lab — Layer 3 Interface Configuration

## Overview

This section documents the Layer 3 interface configurations implemented across the three enterprise network sites

The objective was to establish IP connectivity between the site routers, Cisco ASA firewalls, and Layer 3 core switches.

## 1. ASA Firewall Outside Interface Configuration

### 1.1 Configuring the Firewall Outside Interface

Configured the outside interface of the Cisco ASA firewall at Branch 2 with an IP address to establish Layer 3 connectivity to the site router.

The outside interface serves as the firewall's connection toward the WAN-facing router.

The configuration includes:

- Assigning an IP address and subnet mask.
- Configuring the ASA interface name as `outside`.
- Applying the appropriate security level.
- Enabling the interface.

Similar configurations were implemented on the ASA firewalls at HQ and BR1 using their respective IP addressing schemes.

**BR2 — ASA Outside Interface Configuration**

<img width="527" height="215" alt="BR2 ASA firewall outside interface IP configuration" src="https://github.com/user-attachments/assets/25791c65-ce11-4c9d-8db8-a10f0f8f71be" />

---

## 2. Site Router Inside Interface Configuration

### 2.1 Configuring the Router-to-Firewall Connection

Configured the inside-facing interface of the Branch 2 router with an IP address to establish a routed connection to the ASA firewall.

This interface connects the site router to the firewall's outside interface.

The configuration includes:

- Assigning an IP address and subnet mask.
- Enabling the router interface.
- Establishing the router-side connection to the firewall transit subnet.

Equivalent configurations were completed on the routers at HQ and BR1.

**BR2 — Router Inside-Facing Interface Configuration**

<img width="675" height="212" alt="BR2 router interface IP addressing configuration" src="https://github.com/user-attachments/assets/b478b2e0-4624-4d5b-a35d-0d8b86ea938c" />

---

## 3. ASA Firewall Inside Interface Configuration

### 3.1 Configuring the Firewall-to-Core Switch Connection

Configured the inside interface of the Cisco ASA firewall at Headquarters to establish Layer 3 connectivity with the site's core switch.

The inside interface serves as the firewall's connection toward the internal LAN infrastructure.

The configuration includes:

- Assigning an IP address and subnet mask.
- Configuring the ASA interface name as `inside`.
- Applying the appropriate security level.
- Enabling the interface.

The same configuration approach was applied to the ASA firewalls at BR1 and BR2.

**HQ — ASA Inside Interface Configuration**

<img width="708" height="345" alt="HQ ASA firewall inside interface configuration" src="https://github.com/user-attachments/assets/4de0094d-d169-43d3-993b-c40410dffe18" />

---

## 4. Layer 3 Core Switch Routed Interface Configuration

### 4.1 Configuring the Core Switch Uplink

Configured the firewall-facing interface on the Layer 3 core switch with an IP address to establish connectivity with the ASA firewall's inside interface.

This connection provides a routed path between the internal VLAN networks and the site's firewall.

The configuration includes:

- Configuring the switch interface as a Layer 3 routed port.
- Assigning an IP address and subnet mask.
- Enabling the interface.
- Preparing the connection for routing between the core switch and firewall.

Equivalent configurations were implemented on the Layer 3 switches at the remaining sites.

**Layer 3 Core Switch — Firewall-Facing Interface Configuration**

<img width="902" height="424" alt="Layer 3 core switch routed interface IP configuration" src="https://github.com/user-attachments/assets/0ac1f573-f3da-47e0-a613-1c0b40174e47" />

---
