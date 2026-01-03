# 📚 Access Control Lists (ACL) - Core Concepts & Cheat Sheet

## 🧐 What is an ACL?
An **Access Control List (ACL)** is a set of rules defined on a router or switch interface to filter traffic. It acts as a sequential list of permit or deny statements that apply to IP addresses or upper-layer protocols.

### 🔑 Key Uses
* **Packet Filtering:** Controlling network access (Security).
* **NAT (Network Address Translation):** Identifying interesting traffic to translate.
* **QoS (Quality of Service):** Classifying traffic for priority queuing.
* **Route-Maps:** Filtering routing table updates.
* **VPNs:** Defining interesting traffic to be encrypted.

---

## 🚦 Inbound vs. Outbound
ACLs must be applied to an interface in a specific direction:

| Direction | Description |
| :--- | :--- |
| **Inbound (`in`)** | The router processes packets **before** they are routed. If the packet is denied, it is dropped immediately, saving router resources. |
| **Outbound (`out`)** | The router processes packets **after** the routing decision is made, just before they exit the interface. |

---

## 📋 Types of ACLs

### 1. Standard ACL
* **Filter Criteria:** Checks **Source IP Address** only.
* **Range:** `1-99` (Normal), `1300-1999` (Expanded).
* **Best Practice:** Apply **closest to the destination**.
    * *Why?* Since it only checks the source, applying it too close to the source might block that traffic from reaching valid destinations as well.

### 2. Extended ACL
* **Filter Criteria:** Checks **Source IP**, **Destination IP**, **Protocol** (TCP/UDP/ICMP), and **Port Numbers**.
* **Range:** `100-199` (Normal), `2000-2699` (Expanded).
* **Best Practice:** Apply **closest to the source**.
    * *Why?* It allows you to drop unwanted traffic immediately before it traverses the network, saving bandwidth.

### 3. Named ACL
* Allows you to use descriptive names (e.g., `BLOCK_SALES`) instead of numbers.
* Easier to edit and troubleshoot.
* Can be Standard or Extended.

### 4. Specialized ACLs (Layer 2)
* **Port ACL (PACL):** Filters traffic on Layer 2 switch ports.
    * *Restrictions:* Incoming traffic only; hardware-supported only; does not filter control packets (CDP, STP, etc.).
* **VLAN ACL (VACL):** Filters traffic within a VLAN (bridged traffic) or routed in/out of a VLAN.

---

## 🔢 Anatomy of an ACE (Access Control Entry)
An ACL is a container for individual rules called **ACEs**.

```cisco
access-list 10 deny host 192.168.1.2  <-- ACE Sequence 10
access-list 10 permit any             <-- ACE Sequence 20
```
##  🛠️ Modifying ACLs
Older IOS versions made numbered ACLs hard to edit (you had to delete the whole list). Modern IOS allows editing via Named ACL Configuration Mode.

Command:
```cisco
Router(config)# ip access-list [standard|extended] [number/name]
Router(config-std-nacl)# 15 permit host 192.168.1.5
Router(config-std-nacl)# no 20
