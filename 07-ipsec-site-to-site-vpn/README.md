# Enterprise Network Lab — IPsec Site-to-Site VPN Configuration

## Overview

This section documents the IPsec site-to-site VPN configuration implemented across three enterprise network sites.

The configuration uses a hub-and-spoke topology, with HQ serving as the central hub and BR1 and BR2 acting as remote spokes.

The implementation includes IKE Phase 1, IPsec Phase 2, interesting traffic ACLs, crypto maps, and VPN tunnel verification.

---

## 1. Headquarters IPsec VPN Configuration

### 1.1 Configuring IKE Phase 1

Configured IKE Phase 1 on HQ-R1 to establish the security parameters used to negotiate the VPN connection with remote peers.

**HQ-R1 — IKE Phase 1 Configuration**

<img width="524" height="235" alt="HQ router IKE Phase 1 configuration" src="https://github.com/user-attachments/assets/ddea2be4-493c-4e74-b656-31d025c69441" />

### 1.2 Verifying the IKE Policy

Verified that IKE policy 10 was successfully created on HQ-R1.

**HQ-R1 — IKE Policy Verification**

<img width="668" height="177" alt="HQ router IKE policy 10 verification" src="https://github.com/user-attachments/assets/21a1223c-1919-40d0-bae2-8419eb8e8840" />

### 1.3 Configuring the IPsec Transform Set

Created an IPsec transform set on HQ-R1 to define the security protocols and algorithms used to protect traffic through the VPN tunnel.

**HQ-R1 — IPsec Transform Set Configuration**

<img width="552" height="60" alt="HQ router IPsec transform set configuration" src="https://github.com/user-attachments/assets/fab1e1a4-e6b0-466b-a297-412f10d8661c" />

### 1.4 Defining Interesting Traffic

Configured an extended access control list (ACL) to identify traffic that should be encrypted and transmitted through the IPsec VPN tunnel.

**HQ-R1 — VPN Interesting Traffic ACL**

<img width="612" height="59" alt="HQ router IPsec interesting traffic ACL configuration" src="https://github.com/user-attachments/assets/6db436d6-0bcf-4c25-b1d4-72bfbc0caaa1" />

### 1.5 Creating the IPsec Crypto Map

Created a crypto map to associate the remote VPN peer, IPsec transform set, and interesting traffic ACL.

**HQ-R1 — Crypto Map Configuration**

<img width="506" height="133" alt="HQ router IPsec crypto map configuration" src="https://github.com/user-attachments/assets/3f41ccff-5e52-497b-a9fc-d3d6a60efdac" />

### 1.6 Applying the Crypto Map to the WAN Interface

Applied the configured crypto map to the WAN-facing interface of HQ-R1 to enable IPsec processing for matching traffic.

**HQ-R1 — WAN Interface Crypto Map Assignment**

<img width="799" height="167" alt="HQ router crypto map applied to WAN interface" src="https://github.com/user-attachments/assets/ebb764c3-2b41-4092-b3e5-780f6c2e8a1d" />

---

## 2. Branch 1 IPsec VPN Configuration

### 2.1 Configuring IKE Phase 1

Configured IKE Phase 1 on BR1-R1 using compatible security parameters to establish a VPN connection with HQ-R1.

**BR1-R1 — IKE Phase 1 Configuration**

<img width="495" height="289" alt="Branch 1 router IKE Phase 1 configuration" src="https://github.com/user-attachments/assets/599e21db-b47a-4b91-a981-acab453d6e03" />

### 2.2 Configuring the IPsec Transform Set

Created an IPsec transform set on BR1-R1 to define the encryption and integrity protection parameters for the VPN tunnel.

**BR1-R1 — IPsec Transform Set Configuration**

<img width="574" height="76" alt="Branch 1 router IPsec transform set configuration" src="https://github.com/user-attachments/assets/20b4cd3d-06be-4969-a2b0-45146b4a41bd" />

### 2.3 Defining Interesting Traffic

Configured an ACL to identify traffic between the BR1 and HQ internal networks that should be encrypted through the VPN tunnel.

**BR1-R1 — VPN Interesting Traffic ACL**

<img width="609" height="57" alt="Branch 1 IPsec interesting traffic ACL configuration" src="https://github.com/user-attachments/assets/e00584d3-50c8-44de-bb06-24e04ac63fea" />

### 2.4 Creating and Applying the Crypto Map

Created the IPsec crypto map on BR1-R1 and applied it to the WAN-facing interface.

**BR1-R1 — Crypto Map Configuration and WAN Interface Assignment**

<img width="776" height="403" alt="Branch 1 crypto map configuration and WAN interface assignment" src="https://github.com/user-attachments/assets/280ce0b2-d76c-4da2-9824-e406c8444c6c" />

---

## 3. HQ-to-BR1 VPN Tunnel Verification

### 3.1 Verifying End-to-End Connectivity

Performed ICMP connectivity testing from USER 3 at HQ to USER 5 at BR1.

Successful ping responses confirmed connectivity between the two internal networks.

**HQ to BR1 — Successful ICMP Connectivity Test**

<img width="479" height="293" alt="Successful ping from HQ USER 3 to BR1 USER 5" src="https://github.com/user-attachments/assets/9d149a2c-67e9-444e-b0d3-d7e24fd9f761" />

### 3.2 Verifying IPsec Packet Encryption and Decryption

Verified IPsec Security Association (SA) statistics using the following Cisco IOS command:

```bash
show crypto ipsec sa
```

Observed increasing `pkts encaps` and `pkts decaps` counters, confirming that traffic was being encrypted and decrypted through the VPN tunnel.

**HQ-to-BR1 — IPsec SA Packet Counters**

<img width="551" height="313" alt="IPsec security association showing encapsulated and decapsulated packets" src="https://github.com/user-attachments/assets/6cce42df-4920-4186-be54-2c87d9a57583" />

---

## 4. HQ-to-BR2 IPsec VPN Configuration

### 4.1 Extending the Hub-and-Spoke VPN

Repeated the IPsec configuration process on BR2-R1 using the corresponding WAN IP addresses, internal subnets, and VPN peer settings.

Updated HQ-R1 to support an additional IPsec tunnel to BR2 while maintaining the existing HQ-to-BR1 connection.

### 4.2 Updating the HQ Crypto Map

Added the BR2 VPN peer configuration to the existing crypto map on HQ-R1.

Separate crypto map sequence entries were used to define the VPN policies for the remote branches.

**HQ-R1 — Crypto Map Configuration for BR1 and BR2**

<img width="736" height="553" alt="HQ router crypto map configuration supporting Branch 1 and Branch 2 VPN peers" src="https://github.com/user-attachments/assets/d76f445b-b0fa-493f-9c53-73225bcc2b3a" />

---

## 5. HQ-to-BR2 VPN Tunnel Verification

### 5.1 Verifying End-to-End Connectivity

Performed ICMP connectivity testing from USER 3 at HQ to USER 1 at BR2.

Successful ping responses confirmed connectivity between the HQ and BR2 internal networks through the site-to-site VPN.

**HQ to BR2 — Successful ICMP Connectivity Test**

<img width="476" height="221" alt="Successful ping from HQ USER 3 to BR2 USER 1" src="https://github.com/user-attachments/assets/1fca0947-3fe5-49c9-8187-f209cdd9924f" />

### 5.2 Verifying the IPsec Tunnel

Inspected the IPsec Security Association information to verify encrypted traffic between HQ and BR2.

**HQ-to-BR2 — IPsec Tunnel Verification**

<img width="579" height="227" alt="HQ to Branch 2 IPsec tunnel verification output" src="https://github.com/user-attachments/assets/08ce9f87-4619-4243-8021-4c5418b8bec5" />

---
