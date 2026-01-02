# 🔄 OSPF Dynamic Routing Configuration

![Cisco Packet Tracer](https://img.shields.io/badge/Tool-Cisco%20Packet%20Tracer-blue?logo=cisco&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
This project demonstrates the implementation of the **OSPF (Open Shortest Path First)** link-state routing protocol. The network is configured as a **Single-Area OSPF** (Area 0), allowing three distinct LANs to communicate dynamically over a WAN mesh topology.

Unlike static routing, OSPF allows the routers to automatically discover neighbors, calculate the shortest path (using Dijkstra's algorithm), and adapt to network topology changes in real-time.

## 🖧 Network Topology
The topology consists of three routers connected in a mesh using serial WAN links:

* **Router 0:** Connects LAN `192.168.1.0/24` and links to Router 1 & 2.
* **Router 1:** Connects LAN `192.168.2.0/24` and links to Router 0 & 2.
* **Router 2:** Connects LAN `192.168.3.0/24` and links to Router 0 & 1.
* **WAN Links:**
    * **Net 10.0.0.0/8:** Connects Router 0 ↔ Router 1
    * **Net 11.0.0.0/8:** Connects Router 1 ↔ Router 2
    * **Net 12.0.0.0/8:** Connects Router 0 ↔ Router 2

## ⚙️ Configuration Details

### 1. Interface Configuration
Serial interfaces functioning as **DCE (Data Circuit-terminating Equipment)** were configured with a clock rate to synchronize the link.
* **Command:** `clock rate 64000`

### 2. OSPF Configuration (Process ID 1)
OSPF was enabled on all routers using Process ID 1. Network statements used **Wildcard Masks** to assign interfaces to **Area 0** (Backbone).

**Sample Configuration (Router 0):**
```cisco
Router> enable
Router# configure terminal
Router(config)# router ospf 1
Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router(config-router)# network 10.0.0.0 0.255.255.255 area 0
Router(config-router)# network 12.0.0.0 0.255.255.255 area 0
Router(config-router)# exit
