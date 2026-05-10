# 📡 VoidSignal | 2.4GHz & Bluetooth Jammer (College Exhibition Project)

![Project Type](https://img.shields.io/badge/Project-College_Miniature_Model-purple)
![Hardware](https://img.shields.io/badge/Hardware-ESP32%20%7C%20NRF24L01-red)
![UI Status](https://img.shields.io/badge/UI-Simulation_Only-blue)

**VoidSignal** is an electronics and web-design project created for a college miniature model exhibition. We chose to build a functioning electronic RF (Radio Frequency) project as an alternative to a traditional mechanical model.

> ⚠️ **DISCLAIMER:** This project was created strictly for educational purposes within a controlled academic environment. Operating a real Wi-Fi jammer is illegal in most jurisdictions. This repository provides the simulation UI and documentation for our project.

---

## 📖 Project Background

For our college miniature model exhibition, we decided to step away from mechanical models and delve into the world of cybersecurity and radio frequencies. 

We built a physical hardware model utilizing an **ESP32** and **NRF24L01+ transceivers**. This physical device is capable of transmitting noise over the **2.4 GHz frequency band**, effectively disrupting standard Wi-Fi and Bluetooth signals in its immediate vicinity.

### The Dashboard (This Repository)
To make the project visually impressive for the exhibition, we also built this futuristic, cyberpunk-style web dashboard. 

**Important Note:** *Currently, this website is **NOT** integrated with our physical hardware model.* 
The website acts as a high-fidelity simulation designed to demonstrate to viewers *how* the jammer works under the hood. It visually represents the processes that are happening invisibly in the air around the physical model.

---

## 💻 Dashboard Simulation Features

Even without hardware integration, the web dashboard acts as a standalone educational tool featuring:
* **Interactive Packet Scanner:** Simulates scanning 2.4GHz and 5GHz channels to discover target devices.
* **Interference Generator:** Visualizes different attack vectors (Deauth Injection, Beacon Flooding, RTS/CTS collisions).
* **Live Hardware Telemetry:** Animated CPU, Heap RAM, Core Temperature, and Battery charts simulating hardware strain under load.
* **Educational RF Visualizer:** Live canvas animations explaining complex RF concepts like Signal Attenuation, SNR, Channel Overlap, and Network Topology.
* **AI Threat Analysis:** Hooked up to the Gemini API to generate real-time vulnerability reports based on simulated network traffic.

---

## 🚀 Future Implementation Roadmap (Hardware + UI Integration)

While not currently integrated, the physical ESP32 model and this web dashboard are designed so they *could* be connected in the future. Here is how that integration would work:

1. **ESP32 Web Server:** The ESP32 would host this exact `index.html` file on its internal memory (SPIFFS/LittleFS).
2. **AP Mode:** The ESP32 acts as its own Wi-Fi Access Point. A user connects their phone/laptop directly to the ESP32 and navigates to the dashboard (e.g., `192.168.4.1`).
3. **WebSockets:** The simulated `setInterval` loops in the JavaScript would be replaced by a WebSocket listener. 
4. **Live Telemetry Data:** Instead of random numbers, the ESP32 pushes real-time data to the UI:
   * Real MAC addresses captured by the ESP32's promiscuous mode.
   * Real core temperature from the ESP32's internal sensor.
   * Real transmission packet counts sent to the NRF24L01+ modules.
5. **Two-Way Control:** Clicking "Jammer ON" in the browser would send a JSON command to the ESP32, triggering the NRF24L01+ modules to begin broadcasting RF interference.

---

## 🛠️ How to View the Simulation

Since this repository contains the standalone frontend simulation, no installation or compiling is required to view the UI:
1. Clone or download this repository.
2. Open `index.html` in any modern web browser.
3. Explore the tabs, toggle the scanner, and interact with the UI elements.

## 📄 License
Distributed under the MIT License. See `LICENSE` for more information.