# 🛡️ CyberGuard — ML-Based Real-Time De-Authentication Attack Detection & Prevention


A real-time wireless network security system that detects and prevents **de-authentication (De-Auth) attacks** using a **Random Forest machine learning classifier**. The system captures live IEEE 802.11 management frames, extracts statistical features, classifies traffic, and automatically triggers prevention mechanisms — all visualized through a live Flask dashboard.

---

## 📌 Table of Contents

- [About the Project](#about-the-project)
- [System Architecture](#system-architecture)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Future Work](#future-work)
- [Authors](#authors)

---

## 📖 About the Project

Wireless networks based on IEEE 802.11 are vulnerable to de-authentication attacks, where an adversary injects forged frames to disconnect legitimate clients from access points — leading to **Denial of Service (DoS)**, **session hijacking**, or **man-in-the-middle exploits**.

This project proposes a robust solution by:
- Passively monitoring Wi-Fi traffic in real time using monitor mode
- Extracting features like frame counts, MAC diversity, inter-arrival time, and signal strength
- Classifying traffic as **Normal** or **Attack** using a trained Random Forest model
- Automatically sending corrective packets to restore connectivity when an attack is detected

> ✅ Achieves **96.8% accuracy**, **97.2% recall**, and **AUC = 1.00**

---

## 🏗️ System Architecture

```
Wi-Fi Traffic Capture (Monitor Mode Adapter)
            ↓
Preprocessing & Feature Extraction
            ↓
Machine Learning Classifier (Random Forest)
       ↙             ↘
Normal Traffic     Attack Detected
                       ↓
             Prevention Mechanism (Corrective Packets)
                       ↓
          Dashboard (Flask API — Alerts & Monitoring)
```

---

## ✨ Features

- 📡 **Real-time packet capture** using Scapy in monitor mode
- 🧠 **ML-based classification** with Random Forest (scikit-learn)
- 🔔 **Instant alerts** via Flask + WebSocket dashboard
- 🛑 **Automated prevention** — identifies attacker MAC and sends re-auth/re-association packets
- 📊 **Live dashboard** with attack graph, logs, and system status
- 🪶 **Lightweight** — deployable on existing wireless infrastructure

---

## 🛠️ Tech Stack
```
Technology Stack
├── Language: Python 3.8+
├── ML Library: scikit-learn
├── Packet Capture: Scapy
├── Traffic Analysis: Wireshark
├── Web Framework: Flask
└── Platform: Kali Linux
```
---

## 📁 Project Structure

```
cyberguard-deauth-detection/
│
├── model/
│   ├── train_model.py            # Train Random Forest classifier
│   ├── test_model.py             # Evaluate and test the model
│   └── deauth_detector.pkl       # Saved trained model
│
├── capture/
│   ├── capture_attack.py         # Capture attack traffic
│   └── capture_normal.py         # Capture normal traffic
│
├── dashboard/
│   ├── app.py                    # Flask backend
│   ├── templates/
│   │   └── 1index.html           # Main dashboard HTML
│   └── static/
│       ├── 1script.js            # Frontend JS
│       └── 1style.css            # Frontend CSS
│
├── screenshots/
│   └── Screenshot_2025-08-24.png # Dashboard screenshot
│
├── requirements.txt
├── .gitignore
└── README.md
```

---

## ⚙️ Installation

### Prerequisites

- Kali Linux (recommended) or any Linux distro
- Python 3.8+
- A Wi-Fi adapter that supports **monitor mode**
- Root/sudo privileges

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/cyberguard-deauth-detection.git
cd cyberguard-deauth-detection

# 2. Install dependencies
pip install -r requirements.txt

# 3. Enable monitor mode on your Wi-Fi adapter
sudo airmon-ng start wlan0

# 4. Train the model (or use the pre-trained one)
python model/train_model.py

# 5. Start the detection system
sudo python capture/packet_capture.py

# 6. Launch the dashboard (in a new terminal)
python dashboard/app.py
```

Then open your browser at `http://localhost:5000` to view the live dashboard.

---

## 🚀 Usage

| Script | Description |
|---|---|
| `model/train_model.py` | Train the Random Forest classifier on collected data |
| `capture/packet_capture.py` | Start real-time monitoring and detection |
| `prevention/prevention_module.py` | Standalone prevention module |
| `dashboard/app.py` | Launch the Flask web dashboard |

---

## 📊 Results

### Model Performance

| Metric | Value |
|---|---|
| Accuracy | **96.8%** |
| Precision | **95.4%** |
| Recall | **97.2%** |
| F1-Score | **96.3%** |
| AUC | **1.00** |

### Comparison with Other Models

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---|---|---|---|
| SVM | 91.2% | 89.5% | 92.0% | 90.7% |
| KNN | 88.7% | 87.3% | 89.2% | 88.2% |
| Decision Tree | 93.0% | 91.2% | 92.5% | 91.8% |
| **Random Forest** | **96.8%** | **95.4%** | **97.2%** | **96.3%** |

> Random Forest outperformed all other models while maintaining low computational overhead, making it ideal for real-time deployment.

---

## 🔭 Future Work

- Extend detection to **packet injection** and **man-in-the-middle attacks**
- Improve prevention by **blacklisting attacker MAC addresses**
- Explore **federated learning** for privacy-preserving detection
- Deploy on **IoT/embedded devices** using Tiny-ML
- Integrate with **SDN** for automated network-wide response

---

## 👩‍💻 Authors
```
Naimisha Kundrapu
Siva Yadala
```
---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

> ⚠️ **Disclaimer:** This tool is intended for educational and authorized security research purposes only. Do not use it on networks you do not own or have explicit permission to test.
