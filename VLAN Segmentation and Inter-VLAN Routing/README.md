# VLAN Segmentation and Inter-VLAN Routing

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco-Packet%20Tracer-blue?logo=cisco&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📖 Project Overview
This project demonstrates the implementation of **VLAN (Virtual Local Area Network) Segmentation** and **Inter-VLAN Routing** using Cisco Packet Tracer. The network design separates traffic between different departments (HR and Sales) to enhance security and network performance, while using a router to allow controlled communication between these isolated networks.

## 🏗️ Network Topology
The network consists of the following components:

* **1 x Router (Cisco 2911):** Configured as the gateway to facilitate routing between the different VLAN subnets.
* **2 x Switches (Cisco 2960):** * **Switch0:** Dedicated to the **HR Department** (VLAN 10).
    * **Switch1:** Dedicated to the **Sales Department** (VLAN 20).
* **4 x End Devices (PCs):** Configured with static IP addresses corresponding to their respective VLAN subnets.

### Diagram
![Network Topology](path/to/your/topology-screenshot.png)
*(Replace the path above with the actual link to your network diagram screenshot)*

## ⚙️ Configuration Details

### 1. VLAN Segmentation
Two distinct VLANs were created to logically separate the network traffic:
* **VLAN 10:** Named `HR_Dept`
* **VLAN 20:** Named `Sales_Dept`

### 2. Switch Configuration
Each switch was configured using the Cisco IOS CLI. Access ports were assigned to their specific VLANs to ensure device isolation.

**Example Configuration (Switch 1 - Sales Dept):**
```cisco
Switch> enable
Switch# configure terminal
Switch(config)# vlan 20
Switch(config-vlan)# name Sales_Dept
Switch(config-vlan)# exit
Switch(config)# interface range fa0/1 - 24
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit
Switch# write memory
