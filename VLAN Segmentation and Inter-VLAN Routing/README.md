🔹 VLAN Segmentation and Inter-VLAN Routing (Cisco Packet Tracer)
📌 Project Overview

This project demonstrates VLAN segmentation and inter-VLAN routing in a simulated enterprise network using Cisco Packet Tracer. The network is designed to separate departments into different VLANs while allowing controlled communication between them through a router.
The lab highlights best practices in Layer 2 segmentation, Layer 3 routing, and basic enterprise LAN design.

🎯 Objectives

Implement VLAN-based network segmentation for multiple departments

Configure access ports and assign VLANs on Cisco switches

Enable inter-VLAN communication using a router

Verify connectivity between hosts across different VLANs

Reinforce practical understanding of VLANs, routing, and subnetting

🖧 Network Topology

The topology consists of:

1 Router (Cisco 2911) for inter-VLAN routing

2 Layer 2 Switches (Cisco 2960)

2 VLANs representing departments

VLAN 10 – HR Department

VLAN 20 – Sales Department

4 End Devices (PCs)


🏷️ VLAN Design
VLAN ID	VLAN Name	Department
10	HR_Department	Human Resources
20	Sales_Dept	Sales
| VLAN ID                                       | VLAN Name       | Department     |
|-----------------------------------------------|-----------------|----------------|
| 10                                            | HR_Dept         | Human Resources|
| 20                                            | Sales_Dept      | Sales          |

🌐 IP Addressing Scheme
| VLAN ID                                       | VLAN Name       | Department     |
|-----------------------------------------------|-----------------|----------------|
| 10                                            | HR_Dept         | Human Resources|
| 20                                            | Sales_Dept      | Sales          |VLAN 10 – HR Department
Device	IP Address
PC0	192.168.29.11
PC1	192.168.20.12
VLAN 20 – Sales Department
Device	IP Address
PC2	192.168.10.13
PC3	192.168.10.14
⚙️ Configuration Summary
🔹 Switch Configuration

VLANs created and named

Access ports assigned to respective VLANs

Configuration saved to NVRAM

Example:

vlan 20
 name Sales_Dept
interface range fa0/1 - 24
 switchport mode access
 switchport access vlan 20

🔹 Router Configuration

Router interfaces configured with IP addresses

Acts as the default gateway for VLANs

Enables inter-VLAN routing

🔍 Verification & Testing

show vlan brief used to verify VLAN creation and port assignments

Successful ping tests between hosts in different VLANs

Confirmed correct routing and VLAN segmentation

📸 VLAN Verification Output
<p align="center"> <img src="./images/vlan-brief.png" alt="VLAN Brief Output" width="600"> </p>
🧠 Skills Demonstrated

VLAN creation and management

Access port configuration

Inter-VLAN routing concepts

IP addressing and subnetting

Enterprise LAN design principles

Network verification and troubleshooting
