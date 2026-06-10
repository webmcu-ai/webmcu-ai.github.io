# webmcu-ai

> **TinyML and WebAI — from a $15 microcontroller to a Chrome browser, no cloud required.**

Hi, I'm [Jeremy Ellis](https://github.com/hpssjellis) — a high school Computing, Engineering and Robotics teacher in British Columbia, Canada, with about 35 years in the classroom and a deep interest in making AI genuinely understandable. Not black-box AI. Not cloud-dependent AI. The kind where you can read every weight, every gradient, every line of code, and know exactly what the machine is doing and why.

This organization collects my open-source work at the intersection of **TinyML** (machine learning on microcontrollers) and **WebAI** (machine learning in the browser via TensorFlow.js and the WebSerial API). The hardware is cheap enough for a classroom. The code is single-file and dependency-free. The goal is that a student — or a researcher in a school with unreliable internet — can train and deploy a working vision classifier in under ten minutes without sending any data to the cloud.

---

## 📄 Papers (webmcu-ai Series)

**Paper 1 — On-Device Vision Training, Deployment, and Inference on a Thumb-Sized Microcontroller**  
Complete CNN backpropagation on the ESP32-S3: 1,750 lines of C++, no cloud, no external ML dependencies.  
→ [on-device-vision-ai](https://github.com/webmcu-ai/on-device-vision-ai) · arXiv April 2026

**Paper 2 — WebSerial Vision Training for Microcontrollers**  
A single-file browser companion to Paper 1: firmware flash, image capture, TensorFlow.js training, weight export, and live activation heatmaps — all from one HTML file over WebSerial.  
→ [webmcu-vision-web](https://github.com/webmcu-ai/webmcu-vision-web) · arXiv April 2026

**Paper 3 — On-Device Audio Classification** *(planned)*  
**Paper 4 — On-Device IMU / Gesture Recognition** *(planned)*

---

## 🛠 Repositories

| Repo | What it does |
|------|-------------|
| [on-device-vision-ai](https://github.com/webmcu-ai/on-device-vision-ai) | Complete on-device CNN training and inference on ESP32-S3. Single `.ino` file, MIT licensed. |
| [webmcu-vision-web](https://github.com/webmcu-ai/webmcu-vision-web) | Browser companion: single `index.html`, no install, WebSerial + TensorFlow.js. |

More repos will appear here as Papers 3 and 4 progress.

---

## 🔧 Hardware

The primary platform is the **Seeed Studio XIAO ESP32-S3 Sense**, available as:
- the bare ESP32-S3 chip (~$8 USD)
- the XIAO ESP32-S3 Sense board with OV2640 camera (~$15 USD)
- the full XIAO ML Kit with OLED display and IMU (~$39 USD)

All three run the same firmware. The OLED and IMU degrade gracefully if the expansion board is absent. The price point is intentional — the whole system should fit in a classroom budget.

---

## 💡 What this is really about

Most AI education either stays at the toy-demo level (drag and drop, no understanding of what's happening) or jumps straight to Python and cloud APIs where the pipeline is opaque. This project sits in the middle: real backpropagation, real Adam optimization, real weights you can read out and inspect — but running on hardware cheap enough that every student in a class can have one.

The WebSerial browser interface extends this further: train at browser speed (~1 min per run versus ~9 min on-device), then deploy to the microcontroller over USB with no drivers, no Python, no cloud account.

Both the firmware and the browser page are single-file by design. That means you can read the entire source, modify it, and ask an LLM to help you adapt it to your own sensors and tasks. The whole thing fits in a context window.

---

## 📬 Contact

- Personal GitHub: [@hpssjellis](https://github.com/hpssjellis)
- LinkedIn: [Jeremy Ellis](https://www.linkedin.com/in/jeremy-ellis-4237a9bb/)
- TinyML4D community: [tinyml.seas.harvard.edu/team](https://tinyml.seas.harvard.edu/team)

Contributions, hardware ports, and curriculum adaptations are welcome. MIT license throughout.

---

*"Master the logic, then command the machine."*
