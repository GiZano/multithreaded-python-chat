<div align="center">

# 💬 Private On-Premise TCP Chat System

### High-Concurrency LAN Communication Architecture

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![TCP/IP](https://img.shields.io/badge/Protocol-TCP%2FIP-orange?style=for-the-badge)
![Multithreading](https://img.shields.io/badge/Concurrency-Multithreading-9cf?style=for-the-badge)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Capacity](https://img.shields.io/badge/Capacity-%3E6000_Clients-brightgreen?style=for-the-badge)

</div>

---

## 📖 About The Project

An ultra-lightweight, high-performance, on-premise chat solution designed for secure communication strictly within local networks (LAN). By keeping all traffic internal and independent of external internet routing, this system ensures absolute data privacy and zero external interception risks.

## ✨ Key Features

* **🚀 Massive Scalability:** Engineered with optimized multithreading to handle over **6,000 concurrent connections** without hardware bottlenecking.
* **🛡️ Zero-Internet Dependency:** Operates entirely within your LAN (Air-Gapped ready), ensuring strict data compliance and security.
* **🐳 Dockerized Deployment:** Includes a containerized environment configuration, making the server instantly deployable across any OS.
* **📦 Strict JSON Protocol:** Implements a standardized, parseable messaging format to route data seamlessly between all architecture components.
* **🎛️ Interactive Endpoints:** Built-in server commands for real-time monitoring (listing active users, broadcasting alerts, and server-time synchronization).

---

## 🏗️ System Architecture

The project implements a classic **Client-Server architecture** (Star Topology) relying on raw TCP Sockets:

* **The Server:** A multithreaded TCP engine. It manages a centralized active-client registry, handles incoming socket streams, and routes JSON packets to their correct destination.
* **The Client:** Utilizes an asynchronous approach via two independent threads to handle simultaneous, non-blocking message sending and receiving.

---

## 🚀 Quick Start

### Option A: Running with Docker (Recommended)
**1. Clone the repository:**
```bash
git clone https://github.com/gizano/multithreaded-python-chat.git
cd multithreaded-python-chat
```

**2. Launch the server container:**
```bash
docker-compose up -d
```

### Option B: Manual Execution
**1. Start the Server:**
```bash
python server/server_main.py
```

**2. Launch the Client:**
```bash
python client/client_main.py
```

---

## 📊 Performance & Stress Testing

System stability under heavy load is a priority. I utilized **AI-generated testing suites** to push the server's concurrency limits.

* **Stress Test:** Simulated 50 autonomous bots performing simultaneous handshakes and rapid random messaging.
* **Breakpoint Test:** Confirmed hardware-bound stability at **6,000+ active users** on standard commercial hardware.

> [!NOTE] 
> **Technical Challenge Solved:** During high-frequency automated testing, the classic **"TCP Coalescing"** (packet merging) issue occurred. This was successfully addressed at the application layer to prevent payload corruption during simultaneous client registrations.

---

## 📡 Protocol Standard

To ensure flawless routing, all TCP payload communication adheres strictly to the following JSON schema:

```json
{
  "from": { 
    "name": "SenderUsername", 
    "ip": "192.168.1.X" 
  },
  "to": "RecipientUsername",
  "msg": "Hello, this is a secure message."
}
```

---

<div align="center">

**Developed by [GiZano](https://giovanni-zanotti.is-a.dev)**

</div>
