# Network Threat Detection & Performance Analysis with Suricata

Project developed for the **Security** course as part of the BSc in Informatics Engineering at **ISEC** (Coimbra Institute of Engineering)

## Project Summary & Architecture

Designed and deployed a controlled network testbed in **GNS3** simulating an internal corporate segment (*"green area"*) isolated from an external hostile zone (*"red area"*). To monitor traffic passively without adding latency, a central Cisco IOU L2 switch was configured with **SPAN (Port Mirroring)**, forwarding all inter-router packets to an Ubuntu-based **Suricata IDS** sensor.

## Core Methodology & Findings

* **Out-of-Band Traffic Inspection:** Validated real-time signature matching across mirrored traffic between internal and external gateways.
* **Attack Simulation & Signature Mapping:** Executed multi-vector attacks from a Kali Linux node and mapped exact triggered Suricata SIDs:
  * **Volumetric DoS/DDoS (`hping3`):** Single-source and spoofed (`--rand-source`) TCP SYN floods.
  * **Service Enumeration (`snmpwalk`):** Unauthorized queries via default `public` community strings (`sid:2101411`).
  * **Port Reconnaissance (`nmap`):** Stealth TCP SYN scans (`-sS`) flagging invalid TCP checksum anomalies (`sid:2200074`).
  * **Credential Brute Force (`Hydra`):** Automated Telnet (port 23) dictionary attacks against infrastructure routers (`sid:2060090`).
* **Resource & Stress Benchmarking:** Measured sensor resilience under sustained SYN flood conditions, recording a CPU utilization jump from ~50% (baseline) to ~80%, highlighting hardware sizing constraints for production deployments.

## Environment & Tooling

* **Detection Engine:** Suricata (Ubuntu Linux)
* **Emulation & Infrastructure:** GNS3, VirtualBox/VMware, Cisco IOU (L2/L3)
* **Offensive Security Suite:** Kali Linux (`hping3`, `nmap`, `Hydra`, `snmpwalk`)
