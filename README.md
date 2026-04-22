# 🔍 Real-Time Network Traffic Monitoring & Packet Analysis

> A lightweight, real-time network monitoring system built using native Kali Linux tools — no enterprise hardware or proprietary software required.

**Author:** C. Pravin Sai (`2420030777`) | Section S-11  
**Course:** Computer Networks | Instructor: Chandusha Kanda

---

## 📌 Project Overview

Modern networks generate vast streams of data every second. Without continuous visibility, performance issues and security threats can go completely undetected. This project demonstrates how **Kali Linux native tools** can be used to monitor live traffic and analyse packets in real time.

### Key Goals
- Track bandwidth usage across network interfaces in real time
- Intercept and log packets at the data-link layer
- Identify active communication paths between devices
- Visualize traffic flow dynamically as it happens
- Build understanding of typical vs. atypical network behaviour

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Kali Linux** | Security-focused OS — the complete environment for all tools |
| **nload** | Real-time terminal bandwidth visualiser (incoming/outgoing graphs) |
| **tcpdump** | Command-line packet analyser — captures raw packets at interface level |
| **ping** | ICMP utility — generates controlled traffic for live capture & observation |

---

## 🏗️ System Architecture

The system follows a **4-layer modular pipeline**:

```
┌─────────────────────────┐
│   Traffic Generation     │  ← ping / web browsing
└──────────┬──────────────┘
           ▼
┌─────────────────────────┐
│   Traffic Monitoring     │  ← nload monitors bandwidth in real time
└──────────┬──────────────┘
           ▼
┌─────────────────────────┐
│     Packet Capture       │  ← tcpdump captures packets from interface
└──────────┬──────────────┘
           ▼
┌─────────────────────────┐
│       Analysis           │  ← Identify source, destination, protocol
└─────────────────────────┘
```

---

## ⚙️ Implementation — Step by Step

### Step 1: Identify Network Interface
```bash
ip a
```
Lists all available network interfaces (e.g., `eth0`, `wlan0`). Select the active one for monitoring.

### Step 2: Real-Time Bandwidth Monitoring
```bash
sudo nload
```
Launches a live graph showing incoming (RX) and outgoing (TX) traffic in real time.

### Step 3: Packet Capture
```bash
sudo tcpdump -i eth0
```
Captures all packets passing through the `eth0` interface. Replace `eth0` with your active interface name.

### Step 4: Generate Controlled Traffic
```bash
ping google.com
```
Generates ICMP packets to ensure continuous traffic flow for observation and capture.

### Step 5: Analyse Captured Data
Observe the output from `tcpdump` to identify:
- **Source IP** — where the packet originated
- **Destination IP** — where the packet is headed
- **Protocol** — ICMP, TCP, DNS, etc.
- **Sequence numbers & TTL** — for ping traffic analysis

---

## 📸 Screenshots

| Description | Screenshot |
|-------------|-----------|
| nload — Bandwidth monitoring with active YouTube traffic | `screenshots/nload_active_traffic.png` |
| nload — Idle state (baseline) | `screenshots/nload_idle.png` |
| tcpdump + bmon — Packet capture with live ICMP traffic | `screenshots/tcpdump_icmp_capture.png` |
| bmon — Interface-level bandwidth monitor with tcpdump | `screenshots/bmon_interface_monitor.png` |
| nload — Initial baseline (zero traffic) | `screenshots/nload_baseline.png` |

---

## 📊 Results & Observations

- **nload** successfully visualised real-time bandwidth spikes when YouTube was streaming (~29 Mb/s RX peak)
- **tcpdump** captured and displayed ICMP echo request/reply pairs with sequence numbers, TTL values, and sub-millisecond timing (e.g., `icmp_seq=422 ttl=255 time=38.6 ms`)
- **bmon** confirmed per-interface traffic breakdown (loopback vs. eth0)
- The combination of these tools provides meaningful network visibility with zero cost and minimal setup

---

## 💡 Key Takeaway

> Simple, built-in Kali Linux tools are **sufficient** to achieve meaningful, real-time network monitoring — no expensive hardware or proprietary software required. Visibility and security can be accessible to any network engineer or student with the right open-source toolkit.

---

## 🖥️ Environment

- **OS:** Kali Linux 2025.3 (running on Oracle VirtualBox)
- **Platform:** Virtual Machine
- **Minimum Hardware:** 8 GB RAM recommended

---

## 📁 Repository Structure

```
network-traffic-monitor/
│
├── README.md                        ← You are here
├── docs/
│   ├── abstract.md                  ← Project abstract
│   └── design-and-development.md   ← Full design document
└── screenshots/
    ├── nload_active_traffic.png
    ├── nload_idle.png
    ├── tcpdump_icmp_capture.png
    ├── bmon_interface_monitor.png
    └── nload_baseline.png
```

---

## 📄 Related Documents

- [`docs/abstract.md`](docs/abstract.md) — Project abstract
- [`docs/design-and-development.md`](docs/design-and-development.md) — Full design & development document

---

*This project was submitted as part of the Computer Networks course (CN Hackathon), demonstrating practical application of network monitoring concepts.*
