🔐 VLAN Segmentation & Inter-VLAN Routing
Cisco Packet Tracer | SOC / Blue Team Network Security Lab
<p align="center"> <img src="https://img.shields.io/badge/Network_Security-Blue_Team-0A66C2?style=for-the-badge" /> <img src="https://img.shields.io/badge/Cisco-Packet_Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white" /> <img src="https://img.shields.io/badge/VLAN_Segmentation-Enterprise_LAN-2E8B57?style=for-the-badge" /> <img src="https://img.shields.io/badge/SOC_Relevant-Yes-8B0000?style=for-the-badge" /> </p>
🛡️ Project Overview

This lab simulates enterprise-grade network segmentation using VLANs and inter-VLAN routing, a foundational security control used in Security Operations Centers (SOC) to reduce attack surface and limit lateral movement.

Using Cisco Packet Tracer, the network is architected to isolate departmental traffic at Layer 2 while enabling controlled Layer 3 communication through a routing device. This mirrors real-world enterprise environments where segmentation is critical for threat containment, monitoring, and incident response.

🎯 Security Objectives

Enforce network segmentation using VLANs

Reduce lateral movement between departments

Implement controlled inter-VLAN communication

Apply least-privilege network design principles

Strengthen SOC understanding of internal network visibility

🖧 SOC-Relevant Network Architecture

The simulated enterprise environment consists of:

Cisco 2911 Router

Central Layer 3 routing point

Enforces traffic flow between VLANs

2 Cisco 2960 Layer 2 Switches

Enforce VLAN-based isolation

2 Security Zones (VLANs)

Department-based segmentation

4 Endpoints

Simulated user devices generating internal traffic

This design reflects real SOC-monitored internal networks, where east–west traffic is closely observed.

🏷️ VLAN-Based Security Zones
🔹 VLAN 10 — HR Security Zone

Contains sensitive personnel systems

Isolated to protect confidential HR data

Limits exposure to internal threats

🔹 VLAN 20 — Sales Security Zone

Handles business and customer-related systems

Segmented to prevent unauthorized access to HR assets

Security Benefit:
Segmentation ensures that a compromise in one department does not automatically expose other internal systems.

🌐 IP Addressing (Logical Separation)
HR VLAN (VLAN 10)

PC0 → 192.168.29.11

PC1 → 192.168.20.12

Sales VLAN (VLAN 20)

PC2 → 192.168.10.13

PC3 → 192.168.10.14

Distinct subnets enhance traffic visibility, policy enforcement, and incident scoping during investigations.

⚙️ Security Configuration Summary
🔹 Switch Hardening & VLAN Enforcement

VLANs explicitly created and named

Access ports locked to assigned VLANs

Prevents VLAN hopping via proper port configuration

vlan 20
 name Sales_Dept

interface range fa0/1 - 24
 switchport mode access
 switchport access vlan 20


SOC Value:
Clear Layer 2 boundaries simplify traffic analysis and alert triage.

🔹 Router as a Controlled Trust Boundary

Router interfaces configured as VLAN gateways

All cross-VLAN traffic forced through Layer 3

Enables future implementation of:

ACLs

Traffic inspection

Logging & monitoring

This reflects how SOC teams enforce inter-zone visibility and control.

🔍 Validation & Monitoring Checks

Verification steps aligned with SOC operational workflows:

show vlan brief confirms segmentation enforcement

Cross-VLAN ICMP tests validate allowed communication

Routing verification ensures predictable traffic paths

Result:
Traffic behaves as expected with no unauthorized cross-zone access.

📸 Evidence: VLAN Configuration Verification
<p align="center"> <img src="./images/vlan-brief.png" alt="VLAN Verification Output" width="650"> </p>
🧠 Blue Team Skills Demonstrated

Network segmentation as a security control

VLAN enforcement and validation

Inter-VLAN traffic analysis

Internal attack surface reduction

Enterprise LAN security design

Network troubleshooting and verification

🚨 Threats Mitigated

Unauthorized lateral movement

Internal reconnaissance across departments

Accidental data exposure between business units

Flat network security risks

📊 SOC Relevance

This lab directly supports SOC responsibilities such as:

Understanding internal network architecture

Interpreting east–west traffic patterns

Designing defensible enterprise networks

Supporting SIEM correlation with segmented traffic

🚀 Summary

VLAN segmentation combined with controlled inter-VLAN routing is a core defensive strategy in modern enterprises. This project demonstrates how network design directly supports SOC detection, containment, and response efforts.
