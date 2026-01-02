# 📡 DHCP Relay & Multi-Subnet Configuration

![Cisco Packet Tracer](https://img.shields.io/badge/Tool-Cisco%20Packet%20Tracer-blue?logo=cisco&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
This project demonstrates how to configure a **Centralized DHCP Server** to manage IP addresses for multiple distinct networks (subnets) separated by a router. 

Since routers do not forward broadcast traffic (like DHCP Discover messages) by default, this lab implements the **DHCP Relay Agent** feature using the Cisco IOS `ip helper-address` command. This allows clients in a remote network (Network B) to obtain IP addresses from a server located in Network A.

## 🖧 Network Topology
The network consists of two subnets connected via a **Cisco 2911 Router**:

* **Network A (Left Side):**
    * **Subnet:** `192.168.10.0/24`
    * **Devices:** DHCP Server, Switch0, PC0, PC1, Laptop0.
    * **Gateway:** Router G0/0 (`192.168.10.1`).

* **Network B (Right Side):**
    * **Subnet:** `192.168.20.0/24`
    * **Devices:** Switch1, PC2, Laptop1, Laptop2.
    * **Gateway:** Router G0/1 (`192.168.20.1`).


## ⚙️ Configuration Details

### 1. DHCP Server Setup
The server (at `192.168.10.2`) is configured with two distinct IP Pools:
* **Pool 1:** For the local 192.168.10.0 network.
* **Pool 2:** For the remote 192.168.20.0 network.

### 2. Router Configuration (DHCP Relay)
The Router is configured to act as the Relay Agent. The `ip helper-address` command is applied to the gateways to forward DHCP requests to the server IP (`192.168.10.2`).

**Router0 CLI Configuration:**
```cisco
Router> enable
Router# configure terminal

! Configure Gateway for Network A
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.10.1 255.255.255.0
Router(config-if)# ip helper-address 192.168.10.2  <-- Points to Server
Router(config-if)# no shutdown

! Configure Gateway for Network B
Router(config)# interface g0/1
Router(config-if)# ip address 192.168.20.1 255.255.255.0
Router(config-if)# ip helper-address 192.168.10.2  <-- Vital for remote clients
Router(config-if)# no shutdown
Router(config-if)# exit
