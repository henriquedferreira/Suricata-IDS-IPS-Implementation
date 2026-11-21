# Network Threat Detection & Performance Analysis with Suricata

Project developed for the **Security** course as part of the BSc in Informatics Engineering at **ISEC** (Coimbra Institute of Engineering)

## Architecture & Scope

This project explores the deployment and stress-testing of **Suricata** as an Intrusion Detection System (IDS) within a simulated corporate topology built in **GNS3**, segmenting an internal network from an external hostile zone.

To inspect inter-router traffic without impacting network latency, the sensor was configured in a passive (Out-of-Band) architecture using **SPAN (Port Mirroring)** on a central Cisco Layer 2 switch. Beyond signature validation, the study focused on evaluating sensor resilience and CPU overhead under high-volume traffic spikes.

## Simulated Threat Vectors

* **Denial of Service (DoS/DDoS):** Volumetric single-source and distributed TCP SYN flood attacks to evaluate detection accuracy and hardware resource exhaustion.
* **Port Reconnaissance:** Stealth TCP SYN scanning using Nmap to identify exposed services and protocol anomalies.
* **Service Enumeration:** Unauthorized SNMP device discovery targeting default community strings.
* **Credential Brute Force:** Automated Telnet dictionary attacks against network infrastructure using Hydra.

## Tech Stack & Tools

* **IDS & OS:** Suricata, Ubuntu Linux
* **Network Emulation:** GNS3
* **Offensive Security & Testing:** Kali Linux (Nmap, Hydra, hping3, snmpwalk)
