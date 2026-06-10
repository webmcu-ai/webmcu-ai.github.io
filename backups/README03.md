# webmcu-ai

> **TinyML and WebAI — from a $15 microcontroller to a Chrome browser, no cloud required.**

Hi, I'm [Jeremy Ellis](https://github.com/hpssjellis) — a high school Computing, Machine Learning and Robotics teacher in British Columbia, Canada, with about 35 years in the classroom and a deep interest in making AI genuinely understandable. Not black-box AI. Not cloud-dependent AI. The kind where you can read every weight, every gradient, every line of code, and know exactly what the machine is doing and why.

This organization collects my open-source work at the intersection of **TinyML** (machine learning on microcontrollers) and **WebAI** (machine learning in the browser via TensorFlow.js and the WebSerial API). The hardware is cheap enough for a classroom. The code is single-file and dependency-free. The goal is that a student — or a researcher in a global south university with unreliable internet — can train and deploy a working vision classifier in under ten minutes without sending any data to the cloud.

---

## 📄 Papers (webmcu-ai Series)

**Paper 1 — On-Device Vision Training, Deployment, and Inference on a Thumb-Sized Microcontroller**  
Complete CNN backpropagation on the ESP32-S3: 1,680 lines of C++, no cloud, no external ML dependencies.  
Github → [on-device-vision-ai](https://github.com/webmcu-ai/on-device-vision-ai).Paper 1 →  [arXiv April 2604.23012](https://arxiv.org/abs/2604.23012)

**Paper 2 — WebSerial Vision Training for Microcontrollers**  
A single-file browser companion to Paper 1: index.html, firmware flash, firmware.ino, image capture, TensorFlow.js training, weight export, and live activation heatmaps — all from one HTML file over WebSerial.  
Github → [webmcu-vision-web](https://github.com/webmcu-ai/webmcu-vision-web). Paper 2 → [arXiv April 2604.22834](https://arxiv.org/abs/2604.22834) 

Most important is the actively being developed webpage that conncets with the device at [webmcu-vision-web/index.htm](https://webmcu-ai.github.io/webmcu-vision-web/index.htm)

**Paper 3 — On-Device Audio Classification** *(planned)*  
**Paper 4 — On-Device IMU / Gesture Recognition** *(planned)*

---

## 🛠 Repositories

#### All use the XIAO ESP32-S3 for serial monitor only or use the [$15-40 USD xiaoML kit](https://www.seeedstudio.com/The-XIAOML-Kit.html) for full on-device training and inference.

| Repo | What it does |
|------|-------------|
| [on-device-vision-ai](https://github.com/webmcu-ai/on-device-vision-ai) | Complete on-device CNN training and inference. Uses a single `.ino` file, MIT licensed. |
| [webmcu-vision-web](https://github.com/webmcu-ai/webmcu-vision-web) | Browser companion: single `index.html`, no install, WebSerial + TensorFlow.js. Working demo webpage at [https://webmcu-ai.github.io/webmcu-vision-web/index.html](https://webmcu-ai.github.io/webmcu-vision-web/index.html)|
|[on-device-fomo](https://github.com/webmcu-ai/on-device-fomo)|on-device Vision FOMO (Faster Objects More Objects) Object detection with x,y centroid location capable of multiple detections.  |
|[on-device-regression](https://github.com/webmcu-ai/on-device-regression) | on-device Vision Regression (each trained object class is an integer number). Regression allows distance or size measurement based on how big or small a single object is from the camera. Now has an extrapolation linear equation. |
| [on-device-vision-anomaly](https://github.com/webmcu-ai/on-device-vision-anomaly)| on-device vision anomaly |
| [on-device-motion](https://github.com/webmcu-ai/on-device-motion)| on-device motion acceleration in x, y, z using the IMU. Collects 3x40 samples of x,y,z accelereration data, but could be any combination of sensor data up to 120 data points, so 2x60, 5x24 etc. Basic start of a sensor fusion model.|
| [on-device-sound](https://github.com/webmcu-ai/on-device-sound) | on-device sound machine learning model using FFT. Install the firmware on the xiao esp32s3 sense which has a microphone |


---

## 🔧 Hardware

The primary platform is the **Seeed Studio XIAO ESP32-S3 Sense**, available as:
- the bare [XIAO ESP32-S3](https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32S3-Pre-Soldered-p-6334.html) module ($8.49 USD full replacement only, does not run the above)
- the [XIAO ESP32-S3 Sense](https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32S3-Sense-Pre-Soldered-p-6335.html) board with OV2640 camera ($14.90 USD, runs only with serial monitor)
- the full [XIAO ML Kit](https://www.seeedstudio.com/The-XIAOML-Kit.html) with OLED display and IMU ($38.90 USD with cables, sd card etc, $22 USD just for the boards, runs everything)

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
