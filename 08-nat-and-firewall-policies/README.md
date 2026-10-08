# Enterprise Network Lab — ASA Firewall ACL Configuration & ICMP Troubleshooting

## 1. Troubleshooting ICMP Traffic on the ASA Firewall

### 1.1 Identifying Blocked ICMP Traffic

During connectivity testing, ICMP traffic entering the ASA firewall's outside interface was blocked by the firewall's default security policy.

Used the following command to simulate an ICMP echo request entering the outside interface of the BR2 firewall:

```bash
packet-tracer input outside icmp 10.0.2.1 8 0 10.2.10.2 detailed
```

This simulated traffic from the site router (10.0.2.1) destined for a VLAN 10 endpoint (10.2.10.2).

**BR2 ASA — ICMP Traffic Denied**

<img width="832" height="282" alt="ASA packet tracer showing ICMP traffic denied by firewall policy" src="https://github.com/user-attachments/assets/541bb166-4197-4f24-960c-d61e8c94431a" />

---

## 2. Configuring ASA Firewall Access Control Lists

### 2.1 Creating an Extended ACL

Configured an extended ACL to permit ICMP traffic entering the ASA outside interface from the site router to the internal 10.2.0.0/16 network.

```bash
access-list OUTSIDE_IN extended permit icmp host 10.0.2.1 10.2.0.0 255.255.0.0
```

### 2.2 Applying the ACL to the Outside Interface

Applied the ACL inbound on the ASA outside interface.

```bash
access-group OUTSIDE_IN in interface outside
```

This allows matching ICMP traffic from the router to enter the internal network.

### 2.3 Verifying the Firewall ACL

Repeated the packet-tracer test to confirm that the simulated ICMP traffic was now permitted by the firewall.

**BR2 ASA — ICMP Traffic Permitted**

<img width="779" height="294" alt="ASA packet tracer showing ICMP traffic permitted after ACL configuration" src="https://github.com/user-attachments/assets/22779abc-4dfb-43ac-9327-4b8658140efa" />

---

## 3. Verifying Router-to-LAN Connectivity

### 3.1 Testing Connectivity from an Internal Endpoint

Performed an ICMP connectivity test from USER 1 on the BR2 LAN to the connected site router.

Successful ping responses confirmed connectivity between the internal endpoint and router.

**BR2 — USER 1 Connectivity Verification**

<img width="472" height="195" alt="Successful ping from BR2 USER 1 to the site router" src="https://github.com/user-attachments/assets/d2624159-036b-4ceb-86c5-ad62ad2d8d77" />

---

## 4. Configuring ACLs for IPsec VPN Traffic

### 4.1 Allowing ICMP Between HQ and BR1

During IPsec VPN testing in Section 07, ICMP traffic between the HQ and BR1 internal networks required additional firewall permissions.

Configured ACL entries on both ASA firewalls to permit the required traffic between the two LAN networks.

**HQ ASA — VPN ICMP ACL Configuration**

<img width="1118" height="193" alt="HQ ASA firewall ACL permitting ICMP traffic between VPN networks" src="https://github.com/user-attachments/assets/a27ba2aa-c0d1-4b00-84aa-6d3a82c30dab" />

**BR1 ASA — VPN ICMP ACL Configuration**

<img width="1066" height="137" alt="BR1 ASA firewall ACL permitting ICMP traffic between VPN networks" src="https://github.com/user-attachments/assets/fcfa303a-318b-4cbd-98ce-4218ae98a4ce" />

---

## 5. Verifying Inter-Site ICMP Connectivity

### 5.1 Testing HQ-to-BR1 Connectivity

Performed an ICMP connectivity test from USER 3 at HQ to USER 5 at BR1 (10.3.10.2).

Successful ping responses confirmed that traffic was permitted between the two internal networks.

**HQ to BR1 — Successful ICMP Connectivity Test**

<img width="471" height="268" alt="Successful ping from HQ USER 3 to BR1 USER 5 at 10.3.10.2" src="https://github.com/user-attachments/assets/05b4c30a-ae9c-4bdd-bb29-98c345429f11" />

---
