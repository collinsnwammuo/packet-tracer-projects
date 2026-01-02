🔐 VLAN Segmentation & Inter-VLAN Routing
Cisco Packet Tracer | SOC / Blue Team Network Security Lab
<p align="center"> <img src="https://img.shields.io/badge/Network_Security-Blue_Team-0A66C2?style=for-the-badge" /> <img src="https://img.shields.io/badge/Cisco-Packet_Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white" /> <img src="https://img.shields.io/badge/VLAN_Segmentation-Enterprise_LAN-2E8B57?style=for-the-badge" /> <img src="https://img.shields.io/badge/SOC_Relevant-Yes-8B0000?style=for-the-badge" /> </p>
🛡️ Project Overview

This project simulates enterprise-grade network segmentation using VLANs and inter-VLAN routing, a foundational security control widely used in Security Operations Centers (SOC).

The lab demonstrates how Layer 2 isolation combined with Layer 3 traffic control reduces attack surface, improves visibility, and supports effective threat containment.

🎯 Security Objectives

Enforce VLAN-based network segmentation

Reduce lateral movement between internal zones

Enable controlled inter-VLAN communication

Apply least-privilege network design principles

Strengthen SOC understanding of internal traffic flows

🖧 SOC-Relevant Network Architecture

The simulated enterprise network consists of:

1 × Cisco 2911 Router

Provides inter-VLAN routing

Serves as a controlled trust boundary

2 × Cisco 2960 Layer 2 Switches

Enforce VLAN segmentation

Limit unauthorized access

2 × VLAN Security Zones

Department-based logical separation

4 × End Devices (PCs)

Generate internal east–west traffic

🏷️ VLAN-Based Security Zones
VLAN 10 — HR Security Zone

Hosts sensitive HR systems

Isolated to protect confidential personnel data

Reduces exposure to internal threats

VLAN 20 — Sales Security Zone

Hosts sales and business systems

Segmented to prevent unauthorized access to HR assets

Security Benefit:
Compromise of one VLAN does not automatically propagate to others.

🌐 IP Addressing (Logical Separation)
VLAN 10 — Human Resources

PC0 → 192.168.29.11

PC1 → 192.168.20.12

VLAN 20 — Sales

PC2 → 192.168.10.13

PC3 → 192.168.10.14

Distinct subnets improve traffic attribution, alert correlation, and incident scoping.

⚙️ Security Configuration Summary
🔹 Switch Configuration (Segmentation Enforcement)

VLANs explicitly created and named

Access ports statically assigned

Prevents VLAN hopping attacks

vlan 20
 name Sales_Dept

interface range fa0/1 - 24
 switchport mode access
 switchport access vlan 20

🔹 Router Configuration (Controlled Inter-Zone Routing)

Router interfaces configured as VLAN gateways

All cross-VLAN traffic forced through Layer 3

Supports future controls such as:

Access Control Lists (ACLs)

Traffic logging

Security inspection

🔍 Validation & Monitoring

Verification steps aligned with SOC workflows:

show vlan brief to confirm VLAN enforcement

ICMP ping tests to validate authorized communication

Routing checks to ensure predictable traffic paths

Result:
VLAN isolation and routing function correctly with no unauthorized access.

📸 Evidence: VLAN Verification Output
<p align="center"> <img src="./images/vlan-brief.png" alt="VLAN Verification Output" width="650"> </p>
🧠 Blue Team Skills Demonstrated

Network segmentation as a defensive control

VLAN enforcement and verification

Inter-VLAN traffic analysis

Internal attack surface reduction

Enterprise LAN security design

Network troubleshooting

🚨 Threats Mitigated

Unauthorized lateral movement

Internal reconnaissance

Accidental cross-department data exposure

Flat network security risks

📊 SOC Relevance

This project supports SOC activities such as:

Understanding internal network architecture

Monitoring east–west traffic

Supporting SIEM correlation rules

Enabling effective incident containment

🚀 Summary

This lab demonstrates how secure network architecture directly supports SOC detection, investigation, and response. VLAN segmentation remains a core defensive control in modern enterprise security environments.
