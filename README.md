# 🚀 Private On-Premise TCP Chat System

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg?style=for-the-badge&logo=python)](https://www.python.org/)
[![Docker Support](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker)](https://www.docker.com/)
[![Server Capacity](https://img.shields.io/badge/Capacity-%3E6000_Clients-brightgreen?style=for-the-badge)](https://github.com/riccard00731/ChatBot)

An ultra-lightweight, high-performance, on-premise chat solution designed for secure communication within local networks. This system ensures data privacy by keeping traffic internal to the local network.

## 🌟 Key Features
* **Massive Scalability**: Engineered to handle over **6,000 concurrent connections** using optimized multithreading.
* **Zero-Internet Dependency**: Works entirely within your LAN, preventing external data interception.
* **Dockerized Deployment**: Includes a Docker configuration to make the server easily runnable everywher.
* **Strict JSON Protocol**: A standardized messaging format used to communicate between all architecture components.
* **Interactive Endpoints**: Built-in server commands for listing users, broadcasting, and server-time synchronization.

---

## 🏗️ Architecture
The project implements a **Client-Server architecture**, also known as a **Star Topology**.
* **Server**: A multithreaded TCP engine that manages a client registry and routes JSON packets.
* **Client**: Utilizes two independent threads to handle simultaneous message sending and receiving.

---

## 🛠️ Tech Stack
* **Language**: Python for rapid development and extensive library support.
* **Core Libraries**: `socket` for networking, `threading` for concurrency, and `json` for data management.
* **DevOps**: Docker for containerization and GitHub Actions for CI/CD.

---

## 🚀 Quick Start

### Running with Docker
1. **Clone the repo**:
   ```bash
   git clone https://github.com/gizano/multithreaded-python-chat.git
   cd multithreaded-python-chat
   ```
2. **Launch the server**:
   ```bash
   docker-compose up -d
   ```

### Manual Execution
1. **Start the Server**:
   ```bash
   python server/server_main.py
   ```
2. **Launch the Client**:
   ```bash
   python client/client_main.py
   ```

---

## 📊 Performance & Testing
Stability is our priority. We utilized **AI-generated testing suites** to push the server to its limits.
* **Stress Test**: Simulates 50 bots performing handshake and random messaging.
* **Breakpoint Test**: Confirmed hardware-bound stability at **6,000+ active users**.

> **Technical Note**: The "TCP Coalescing" issue was addressed using the `time` library to prevent packet merging during registration.

## 📡 Protocol Standard
All communication must adhere to the following JSON schema:
```json
{
  "from": { "name": "...", "ip": "..." },
  "to": "...",
  "msg": "..."
}
```