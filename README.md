
# ViSTA: Vibro-Sensory Travel Aid Headset

[![Hackaday.io Project](https://img.shields.io/badge/Hackaday.io-Project%20196160-orange)](https://hackaday.io/project/196160-vista-vibro-sensory-travel-aid-headset)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**ViSTA** (Vibro-Sensory Travel Aid) is an open-source, lightweight, and low-cost wearable Electronic Travel Aid (ETA) designed to assist visually impaired individuals in navigating unfamiliar environments.

By leveraging monocular depth estimation and intuitive haptic feedback, ViSTA provides real-time directional cues via subtle vibrations at the temples. This design ensures that the user's auditory senses remain completely unobstructed—a critical safety requirement for maintaining environmental awareness. 

DISCLAIMER: My code structuring skills were not particularly good when I originally built this project so the file structure is somewhat disorganized.

---

## Key Features

* **Non-Intrusive Haptics:** Utilizes Linear Resonant Actuators (LRAs) to provide directional guidance (Left/Right) and intensity-based depth cues.
* **Offloaded Computation:** To maintain a lightweight headset, heavy image processing is offloaded to a mobile device or server, achieving a processing loop of ~54ms.
* **Open Hardware:** Features a 3D-printed frame designed for comfort and safety, terminating in front of the ears to allow for natural hearing.
* **Cost-Effective:** The total Bill of Materials (BOM) is approximately **$80 USD**, making assistive technology more accessible.

---

## System Architecture



The system follows a Client-Server model:
1.  **The Headset (Client):** A Raspberry Pi Zero W captures environmental data via a spy camera and orientation via an IMU, then streams the data over a local network.
2.  **The Processing App (Server):** A high-performance device (Smartphone or Laptop) runs monocular depth estimation models (CNNs) to identify walkable paths and sends haptic commands back to the headset.

---

## Hardware Stack

| Component | Specification |
| :--- | :--- |
| **SoC** | Raspberry Pi Zero W |
| **Camera** | Raspberry Pi Zero Spy Camera |
| **IMU** | MPU6050 (9-Axis) |
| **Actuators** | 2x Linear Resonant Actuators (LRAs) |
| **Power** | 18650 Li-ion Battery + Charging/Protection Circuit |
| **Frame** | Custom 3D-Printed Chassis |

---

## 💻 Software Installation

### 1. Headset Setup (Raspberry Pi)
Ensure your Pi is running a lightweight Linux distribution (e.g., Raspberry Pi OS Lite).

```bash
# Clone the repository
git clone [https://github.com/Parzival129/ViSTA-Headset-Source-Code.git](https://github.com/Parzival129/ViSTA-Headset-Source-Code.git)
cd ViSTA-Headset-Source-Code/headset

# Install dependencies
pip install -r requirements.txt

```

### 2. Server Setup (Smartphone/Laptop)

The server requires Python 3.9+ and the necessary deep learning libraries for the depth estimation model.

```bash
cd ViSTA-Headset-Source-Code/server
pip install -r requirements.txt

# Start the processing server
python main.py

```

---

## Evaluation & Results

The project was validated through real-world testing in collaboration with the **Canadian National Institute for the Blind (CNIB)**.

* **Test Case:** A 1km walk through an unfamiliar route featuring 13 distinct turn points.
* **Performance:** Participants successfully completed the route with zero external assistance, reporting high levels of comfort and intuitive feedback for obstacle avoidance.

---

## 🤝 Contributing

Contributions are welcome! If you have ideas for optimizing the monocular depth CNN, improving the pathfinding algorithms, or refining the 3D frame ergonomics:

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

## 👤 Author

**Russell Tabata** - [@Parzival129](https://github.com/Parzival129)

*University of Toronto*

