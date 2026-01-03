# 🛡️ Extended IPv4 ACL Configuration (Numbered & Named)

![Cisco Packet Tracer](https://img.shields.io/badge/Tool-Cisco%20Packet%20Tracer-blue?logo=cisco&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
This project demonstrates the implementation of **Extended Access Control Lists (ACLs)** to enforce granular security policies. Unlike Standard ACLs (which filter only by source IP), Extended ACLs filter traffic based on **Source IP, Destination IP, Protocol (TCP/UDP/ICMP), and Port Number**.

The goal is to allow specific services (FTP and HTTP) for specific departments while blocking unauthorized access, including peer-to-peer communication between LANs.

## 🖧 Network Topology
The network consists of a central router (R1) connecting three distinct subnets:
* **PC1 Subnet (172.22.34.64/27):** Requires FTP access to the Server.
* **PC2 Subnet (172.22.34.96/28):** Requires Web (HTTP) access to the Server.
* **Server Subnet (172.22.34.0/26):** Hosts the services at IP `172.22.34.62`.

## 🎯 Security Policies

### Policy 1: PC1 Access (Numbered ACL 100)
* **Permit:** FTP traffic (Port 21) from PC1 to Server.
* **Permit:** ICMP traffic (Ping) from PC1 to Server.
* **Deny:** All other traffic (Implicitly blocks PC1 from reaching PC2).

### Policy 2: PC2 Access (Named ACL "HTTP_ONLY")
* **Permit:** HTTP traffic (Port 80) from PC2 to Server.
* **Permit:** ICMP traffic (Ping) from PC2 to Server.
* **Deny:** All other traffic (Implicitly blocks PC2 from using FTP).

## ⚙️ Configuration Details

### 1. Extended Numbered ACL (R1)
Configured to filter traffic from PC1's subnet.
```cisco
R1(config)# access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp
R1(config)# access-list 100 permit icmp 172.22.34.64 0.0.0.31 host 172.22.34.62
R1(config)# interface GigabitEthernet0/0
R1(config-if)# ip access-group 100 in
```
### 2. Extended Named ACL (R1)
Configured to filter traffic from PC2's subnet.
```cisco
R1(config)# ip access-list extended HTTP_ONLY
R1(config-ext-nacl)# permit tcp 172.22.34.96 0.0.0.15 host 172.22.34.62 eq www
R1(config-ext-nacl)# permit icmp 172.22.34.96 0.0.0.15 host 172.22.34.62
R1(config-ext-nacl)# exit
R1(config)# interface GigabitEthernet0/1
R1(config-if)# ip access-group HTTP_ONLY in
```
✅ Verification & Testing
The implementation was verified by testing service accessibility and inter-VLAN connectivity.

| Source | Destination | Service/Protocol | Expected Result | Actual Result |
| :--- | :--- | :--- | :--- | :--- |
| **PC1** | Server | FTP (21) | ✅ **Allowed** | Connected |
| **PC1** | Server | ICMP (Ping) | ✅ **Allowed** | Reply Received |
| **PC1** | PC2 | ICMP (Ping) | ❌ **Denied** | Unreachable |
| **PC2** | Server | HTTP (80) | ✅ **Allowed** | Page Loaded |
| **PC2** | Server | FTP (21) | ❌ **Denied** | Request Failed |

🧠 Skills Demonstrated
* Extended ACLs: Filtering by Port (21/80) and Protocol (TCP/ICMP).
* Named vs. Numbered ACLs: Implementing both configuration styles.
* Wildcard Masks: Calculating precise masks for /27 and /28 subnets.
* Security Best Practices: Applying ACLs inbound on the source interface to save bandwidth.
