
# Enterprise Network Lab — BGP WAN Routing Configuration


## 1. ISP Router BGP Configuration

### 1.1 Configuring BGP Neighbors

Configured BGP on the ISP router to establish external BGP (eBGP) peering sessions with the HQ, BR1, and BR2 routers.

Each site router was configured as a BGP neighbor using its respective WAN IP address and Autonomous System Number (ASN).

**ISP Router — Initial BGP Configuration**

<img width="468" height="151" alt="ISP router BGP neighbor configuration" src="https://github.com/user-attachments/assets/0871c2e3-dc7c-419d-bf9e-78d7cbf3918c" />

---

## 2. Site Router BGP Configuration

### 2.1 Headquarters BGP Configuration

Configured BGP on the HQ router to establish an eBGP session with the ISP router.

The configuration includes the local ASN, ISP neighbor IP address, remote ASN, and network advertisements.

**HQ Router — BGP Configuration**

<img width="537" height="216" alt="HQ router BGP configuration" src="https://github.com/user-attachments/assets/60896622-35bd-42b0-8fce-7632c2f3bd92" />

### 2.2 Branch 1 BGP Configuration

Repeated the BGP configuration on the BR1 router using its assigned ASN and ISP-facing WAN connection.

**BR1 Router — BGP Configuration**

<img width="536" height="220" alt="BR1 router BGP configuration" src="https://github.com/user-attachments/assets/a584d457-036f-4f42-aac4-2c4e93a86559" />

### 2.3 Branch 2 BGP Configuration

Configured the BR2 router to establish an eBGP peering session with the ISP router.

**BR2 Router — BGP Configuration**

<img width="531" height="164" alt="BR2 router BGP configuration" src="https://github.com/user-attachments/assets/2f2a0dff-dbef-4ce2-85e6-aa97a9927b21" />

---

## 3. BGP Network Advertisement

### 3.1 Advertising WAN Networks

Added the WAN network prefixes to the BGP configurations to advertise the respective networks between the ISP and site routers.

These advertisements allow participating BGP routers to learn network reachability information.

**BGP — WAN Network Advertisements**

<img width="512" height="106" alt="BGP WAN network advertisement configuration" src="https://github.com/user-attachments/assets/0097bb22-d31a-421c-bf49-351890898935" />

---

## 4. BGP Routing Verification

### 4.1 Verifying Learned BGP Routes

Inspected the ISP router's BGP table to verify that network prefixes were being advertised and learned through BGP.

Used the following Cisco IOS commands for verification:

```bash
show ip bgp summary
show ip bgp
show ip route bgp
```

**ISP Router — BGP Routing Table Verification**

<img width="648" height="648" alt="ISP router BGP routing table verification" src="https://github.com/user-attachments/assets/0682d163-01b8-4c40-8c39-0d71baac6efb" />

---
