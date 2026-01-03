# 🛡️ Standard IPv4 ACL Configuration

![Cisco Packet Tracer](https://img.shields.io/badge/Tool-Cisco%20Packet%20Tracer-blue?logo=cisco&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
This project demonstrates the implementation of **Standard Access Control Lists (ACLs)** to secure a network by filtering traffic based on source IP addresses. The goal is to restrict access between specific subnets while ensuring all other legitimate traffic is permitted.

In this lab, **Standard ACLs** are applied closest to the **destination** routers (R2 and R3) to efficiently filter traffic before it exits the interface towards the protected networks.

## 🖧 Network Topology
The network consists of three routers connected in a mesh topology, managing traffic between multiple VLANs/Subnets:

* **R1:** Connects Subnets 192.168.10.0/24 (PC1) and 192.168.11.0/24 (PC2).
* **R2:** Connects the **WebServer** network (192.168.20.0/24).
* **R3:** Connects the remote LAN (192.168.30.0/24).


## 🎯 Security Policies Implemented

### Policy 1: Protect the WebServer (R2)
* **Requirement:** The **192.168.11.0/24** network must **NOT** access the WebServer (192.168.20.254).
* **Action:** A Standard ACL was created on **R2** and applied outbound on the interface connecting to the WebServer.

### Policy 2: Restrict Remote Access (R3)
* **Requirement:** The **192.168.10.0/24** network (PC1) must **NOT** communicate with the 192.168.30.0/24 network (PC3).
* **Action:** A Standard ACL was created on **R3** and applied outbound on the interface connecting to PC3.

## ⚙️ Configuration Details

### Router 2 (Web Server Protection)
Configuring ACL #1 to deny the specific subnet and permit everything else.
```cisco
R2(config)# access-list 1 deny 192.168.11.0 0.0.0.255
R2(config)# access-list 1 permit any
R2(config)# interface GigabitEthernet0/0
R2(config-if)# ip access-group 1 out```

###  Router 3 (Remote LAN Protection)
Configuring ACL #1 to deny PC1's subnet from reaching PC3.
```Cisco CLI
R3(config)# access-list 1 deny 192.168.10.0 0.0.0.255
R3(config)# access-list 1 permit any
R3(config)# interface GigabitEthernet0/0
R3(config-if)# ip access-group 1 out
