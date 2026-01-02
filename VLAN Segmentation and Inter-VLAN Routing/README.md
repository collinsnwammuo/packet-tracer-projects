🔐 VLAN Segmentation & Inter-VLAN Routing
SOC & Network Security Lab (Cisco Packet Tracer)
📌 Project Overview

This project demonstrates network segmentation as a security control using VLANs and controlled inter-VLAN routing in a simulated enterprise environment. The lab models how organizations reduce attack surface, limit lateral movement, and improve monitoring by separating departments into logical network segments.

The exercise is framed from a SOC and cybersecurity perspective, emphasizing traffic control, segmentation enforcement, and verification of secure communication paths.

🎯 Security Objectives

Implement VLAN-based network segmentation to isolate departments

Reduce lateral movement risk between user groups

Control inter-VLAN traffic using a Layer 3 gateway

Validate segmentation effectiveness through connectivity testing

Strengthen understanding of network-level security architecture

🛡️ Security Use Case (SOC Perspective)

In a real enterprise environment:

VLANs act as a first line of defense against internal threats

Segmentation limits the blast radius of:

Compromised endpoints

Malware outbreaks

Insider threats

Controlled routing enables:

Easier monitoring

Policy enforcement

Log correlation in SIEM systems

This lab simulates that defensive network design principle.

🖧 Network Architecture

The simulated environment includes:

Router (Cisco 2911)

Functions as a segmentation gateway

Layer 2 Switches (Cisco 2960)

Enforce VLAN separation at access layer

Departmental VLANs

VLAN 10 – HR (Sensitive Data)

VLAN 20 – Sales (Business Operations)

End Hosts

User endpoints representing employee devices

📸 Network Topology
<p align="center"> <img src="./images/topology.png" alt="VLAN Segmentation Topology" width="600"> </p>
🏷️ VLAN Security Design
VLAN ID	VLAN Name	Security Purpose
10	HR_Department	Protects sensitive employee data
20	Sales_Dept	Isolates business operations

Security Rationale:
HR systems often store PII and confidential records, requiring stronger isolation from general business traffic.

🌐 IP Addressing (Logical Segmentation)

Each VLAN operates in a separate IP subnet, enabling:

Clear traffic boundaries

Easier detection of abnormal cross-VLAN traffic

Improved log interpretation in monitoring tools

⚙️ Security-Focused Configuration Summary
🔹 Switch (Layer 2 Security Enforcement)

VLANs explicitly created and named

Access ports locked to specific VLANs

Prevents unauthorized VLAN hopping

Example:

vlan 20
 name Sales_Dept
interface range fa0/1 - 24
 switchport mode access
 switchport access vlan 20


SOC Relevance:
Improper VLAN configuration is a common root cause of internal breaches.

🔹 Router (Controlled Inter-VLAN Routing)

Router acts as a single choke point for cross-VLAN traffic

Each VLAN uses the router as its default gateway

Enables future application of:

ACLs

Traffic logging

IDS/IPS inspection

🔍 Validation & Security Testing
Tests Performed

Verified VLAN separation using show vlan brief

Tested permitted inter-VLAN connectivity using ICMP

Confirmed that communication occurs only via the router

📸 VLAN Verification
<p align="center"> <img src="./images/vlan-brief.png" alt="VLAN Verification Output" width="600"> </p>

Security Outcome:
Traffic between VLANs is predictable, controlled, and observable — a requirement for effective SOC monitoring.

🧠 SOC & Cybersecurity Skills Demonstrated

Network segmentation as a security control

Understanding of lateral movement prevention

Secure Layer 2 and Layer 3 design principles

Traffic flow analysis and verification

Enterprise network defense fundamentals

Foundations for IDS, firewall, and SIEM integration

🛠️ Tools & Technologies

Cisco Packet Tracer

Cisco IOS CLI

VLANs & subnetting

Routing and gateway enforcement

Network traffic validation

🔮 SOC Expansion Opportunities

This lab can be extended to simulate real SOC workflows:

Apply ACLs to restrict inter-VLAN access

Mirror traffic for IDS/IPS (Snort / Suricata) analysis

Generate logs for SIEM ingestion

Simulate insider threat or compromised host scenarios
