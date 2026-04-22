# Design and Development of the Project

**Project Title:** Real-Time Network Traffic Monitoring and Packet Analysis using Kali Linux  
**Author:** C. Pravin Sai (2420030777) | S-11

---

## 1. System Design Overview

The project implements a lightweight, real-time network monitoring system using native Kali Linux tools. The system focuses on capturing live network traffic, visualizing bandwidth usage, and analyzing packet-level communication — without relying on complex graphical interfaces or external software.

The design follows a **modular approach** where each component performs a specific function in the monitoring pipeline, ensuring continuous observation of network activity while maintaining simplicity and efficiency.

---

## 2. System Architecture

The architecture is divided into four main layers:

### Layer 1 — Traffic Generation
- Network traffic is generated using tools such as `ping` or web browsing.
- This simulates real-world network activity for observation.

### Layer 2 — Traffic Monitoring
- `nload` monitors real-time bandwidth usage.
- Provides dynamic incoming (RX) and outgoing (TX) traffic graphs.

### Layer 3 — Packet Capture
- `tcpdump` captures raw packets from the selected network interface.
- Provides detailed packet-level information including headers and payloads.

### Layer 4 — Analysis
- Captured packets are analyzed to identify:
  - Source IP address
  - Destination IP address
  - Protocol used (ICMP, TCP, DNS)
- Helps in understanding normal and anomalous communication patterns.

This layered design ensures **separation of responsibilities** and efficient processing of network data.

---

## 3. Design Components

### Kali Linux Environment
- Acts as the primary platform for executing all tools.
- Provides built-in networking and security utilities.

### Traffic Visualization Module — `nload`
- Displays real-time bandwidth usage.
- Graphical representation of network traffic in the terminal.

### Packet Capture Module — `tcpdump`
- Captures live packets from the network interface.
- Displays packet headers and communication details.

### Traffic Generation Module — `ping`
- Generates ICMP packets to simulate controlled network activity.

---

## 4. Development Methodology

### Step 1: Interface Identification
```bash
ip a
```
Identifies available network interfaces (e.g., `eth0`, `wlan0`). The active interface is selected for monitoring.

### Step 2: Real-Time Traffic Monitoring
```bash
sudo nload
```
Launches dynamic graphs showing incoming and outgoing bandwidth in real time.

### Step 3: Packet Capture
```bash
sudo tcpdump -i eth0
```
Captures packets passing through the specified network interface, displaying source, destination, and protocol information.

### Step 4: Traffic Generation
```bash
ping google.com
```
Generates ICMP traffic to ensure continuous packet flow for monitoring and capture.

### Step 5: Data Analysis
- Observe traffic patterns in `nload` (bandwidth spikes, idle periods).
- Analyse packet data in `tcpdump` (IP addresses, protocols, timing).
- Identify communication patterns between devices.

---

## 5. Development Environment

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux 2025.3 |
| Tools | nload, tcpdump, ping |
| Platform | Oracle VirtualBox VM |
| Hardware | Minimum 8 GB RAM |

---

## 6. System Workflow

1. User initiates traffic using `ping` or web browsing.
2. `nload` continuously monitors bandwidth usage.
3. `tcpdump` captures packets in real time.
4. System displays live traffic flow and packet data.
5. User analyses network behaviour based on captured output.

---

## 7. Design Advantages

- **Lightweight and efficient** — minimal system resource usage
- **No external tools required** — all tools are built into Kali Linux
- **Real-time visualization and analysis** — immediate feedback
- **Easy to implement and understand** — suitable for students and professionals
- **Practical and educational** — applicable in real-world network monitoring scenarios

---

## 8. Summary

The design and development of this project demonstrate how simple, built-in Kali Linux tools can be integrated to create an effective real-time network monitoring system. The modular architecture, combined with step-by-step implementation, ensures clarity, efficiency, and practical usability in real-world networking scenarios.
