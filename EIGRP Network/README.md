# 🔄 EIGRP Enterprise Network Implementation

![Cisco Packet Tracer](https://img.shields.io/badge/Tool-Cisco%20Packet%20Tracer-blue?logo=cisco&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
This project demonstrates the configuration of **EIGRP (Enhanced Interior Gateway Routing Protocol)** to facilitate dynamic routing across a scalable enterprise network. The design features a mesh topology with three routers exchanging routes within **Autonomous System (AS) 1**.

Key objectives include achieving full convergence, verifying neighbor adjacencies, and analyzing the DUAL algorithm's path selection.

## 🖧 Network Topology
The network consists of three routers connected via Serial WAN links, each serving a distinct LAN:

* **Router 0:** Connects LAN `192.168.10.0/24`.
* **Router 1:** Connects LAN `192.168.20.0/24`.
* **Router 2:** Connects LAN `192.168.30.0/24`.
* **WAN Mesh:**
    * **Net 10.0.0.0/8:** Router 0 ↔ Router 1
    * **Net 11.0.0.0/8:** Router 1 ↔ Router 2
    * **Net 12.0.0.0/8:** Router 0 ↔ Router 2


## ⚙️ Configuration Details

### 1. EIGRP Configuration (AS 1)
EIGRP was configured on all routers using **Autonomous System 1**. Network statements were added for both the local LANs and the connected Serial WAN links.

**Router Configuration:**
```cisco
Router(config)# router eigrp 1
Router(config-router)# network 192.168.20.0
Router(config-router)# network 10.0.0.0
Router(config-router)# network 11.0.0.0
Router(config-router)# exit
```
###  ✅ Verification & Testing
The network was verified by checking neighbor relationships and end-to-end connectivity.

1. Neighbor Adjacency
The CLI output confirms that new adjacencies were formed immediately after configuration: ```%DUAL-5-NBRCHANGE: IP-EIGRP 1: Neighbor 10.0.0.1 (Serial0/0) is up: new adjacency```

2. Connectivity Test (Ping)
A ping test was performed from Laptop0 (192.168.10.10) to PC3 (192.168.30.15) in a remote network.

Result: Successful replies were received, confirming that EIGRP is correctly routing traffic across the mesh.


