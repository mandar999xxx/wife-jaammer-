# 📡 VoidSignal | Advanced RF Research Platform

![UI Status](https://img.shields.io/badge/UI-Simulation_Only-blue)
![Tech Stack](https://img.shields.io/badge/Tech-HTML%20%7C%20TailwindCSS%20%7C%20JS-green)
![Educational](https://img.shields.io/badge/Purpose-Educational-orange)

**VoidSignal** is a futuristic, interactive web dashboard designed to simulate and visualize the operational mechanics of an ESP32-based Wi-Fi Jammer. 

> ⚠️ **DISCLAIMER:** This project was created purely as a **simulation-only coding project** to practice UI/UX design and visualize RF (Radio Frequency) concepts. **Operating an actual Wi-Fi jammer is strictly illegal in most countries (including via the FCC in the US).** This tool does not transmit any real radio waves and is meant strictly for educational and defensive research purposes.

---

## 💻 About the Project

This project started as a fun coding session to build a "cyberpunk-style" dashboard. It simulates what an advanced RF penetration testing tool might look like if it were running on an ESP32 microcontroller paired with NRF24L01+ transceivers. 

### Current Simulation Features:
* **Interactive Packet Scanner:** Simulates scanning 2.4GHz and 5GHz channels, generating realistic target data (SSID, BSSID, Vendor, dBm).
* **Interference Generator:** Visualizes different attack vectors (Deauth Injection, Beacon Flooding, RTS/CTS collisions).
* **Live Hardware Telemetry:** Animated CPU, Heap RAM, Core Temperature, and Battery charts.
* **Educational RF Visualizer:** Live canvas animations showing Signal Attenuation, SNR, Channel Overlap, and Network Topology.
* **AI Threat Analysis:** Hooked up to the Gemini API to generate real-time vulnerability reports based on simulated network traffic.

---

## 🛠️ How to Use (Simulation Mode)

Since this is purely a frontend simulation, no installation or compiling is required:
1. Clone or download the repository.
2. Open `index.html` in any modern web browser.
3. Explore the tabs, toggle the scanner, and interact with the UI elements.

---

## 🚀 Future Implementation (Bridging UI to Hardware)

While this is currently a static simulation, the dashboard was designed with real-world implementation in mind. If you are an RF researcher or cybersecurity student looking to implement this UI onto physical hardware (in a controlled, legal Faraday cage environment), here is the implementation roadmap:

### Phase 1: The Hardware Setup
To make the dashboard reflect reality, you would need:
* **ESP32 NodeMCU:** The main web server and control brain.
* **NRF24L01+ PA/LNA (x2):** Connected via HSPI and VSPI for raw 2.4GHz packet injection.
* **Sensors:** A 100k Thermistor (for core temp) and a voltage divider circuit (for battery monitoring).

### Phase 2: WebSockets & Backend Interface
1. **ESP32 Async Web Server:** Host this `index.html` file on the ESP32's SPIFFS or LittleFS memory.
2. **WebSocket Connection:** Replace the simulated `setInterval` loops in the JavaScript with a WebSocket listener. 
3. **Data Pipeline:** The ESP32 will push live JSON telemetry (Temp, CPU, Discovered MACs, RSSI) to the browser.
   ```json
   { "type": "scan_result", "ssid": "Target_AP", "rssi": -65, "vendor": "Cisco" }
