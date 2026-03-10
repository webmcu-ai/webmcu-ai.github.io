# WebMCU-AI Research Lab

> **Bridging browser-based WebAI and microcontroller TinyML 
> through transparent, single-file implementations.**

Welcome to **WebMCU-AI Lab**. Led by a veteran Technology & Robotics 
educator with over 35 years of experience, this organization focuses on 
demystifying "Black Box" AI through **Transparent TinyML** and 
**WebAI** integration — from a $15 microcontroller to a Chrome browser, 
no cloud required.

---

## 🔬 Research Focus

We specialize in **On-Device Machine Learning (TinyML)** with 
browser-based interaction via **WebSerial** and **TensorFlow.js**. 
Our work spans the full training spectrum:

- **Fully on-device** — complete CNN training and inference on 
  ESP32-S3 with no external computation
- **Browser-assisted** — TensorFlow.js trains in Chrome, weights 
  transfer to the MCU via WebSerial
- **Hybrid** — on-device fine-tuning of browser-trained weights

All implementations are single-file, dependency-free, and designed 
to make every step of the ML pipeline visible and modifiable.

### Core Pillars

- 🔍 **Transparent AI** — no black boxes; every weight, gradient, 
  and activation is accessible and documented
- 🎓 **Inquiry-Path Pedagogy** — foundational numeracy and logic 
  before tool-based abstraction; designed for K-12 through 
  undergraduate research
- ⚡ **Edge-to-Web Integration** — seamless WebSerial communication 
  between microcontrollers (ESP32-S3, Arduino Portenta H7) and 
  browser interfaces
- 🔋 **Energy Transparency** — direct measurement of complete ML 
  pipeline energy footprint, including training and inference

---

## 📄 Publications

- **"On-Device Vision Training, Deployment, and Inference on a 
  Thumb-Sized Microcontroller"**  
  Submitted to WCCI 2026 *(under review)*  
  Complete CNN backpropagation on ESP32-S3 — 1,750 lines of C++, 
  no cloud, no external dependencies.

<!--
- **"Browser-Assisted On-Device Training via WebSerial"**  
  In preparation — TorchJS webpage + ESP32 firmware hybrid system.
  
- **"On-Device Audio Training on a Thumb-Sized Microcontroller"**  
  Planned.

- **"On-Device Motion Training on a Thumb-Sized Microcontroller"**  
  Planned.
-->

---

## 🛠 Active Repositories

| Repo | Description | Status |
|------|-------------|--------|



<!--
| [on-device-vision-training](.) | Complete CNN train/infer on ESP32-S3. WCCI 2026 paper code. | 🟢 Active |
| [browser-edge-vision-training](.) | TorchJS webpage + WebSerial firmware. Paper 2 code. | 🟡 In Progress |
-->
<!--
| [on-device-audio-training](.)  | Sound classification on MCU. | 🔵 Planned |
| [on-device-motion-training](.) | IMU/gesture classification on MCU. | 🔵 Planned |
| [on-device-sensor-fusion](.)   | Multi-modal sensor fusion on MCU. | 🔵 Planned |
-->

---

## 📋 Coding Standards

All lab repositories follow these standards for clarity and 
reproducibility:

- **Vanilla Everything** — minimize dependencies; prioritize 
  single-file HTML and vanilla JS with inline CSS
- **Naming Convention** — descriptive `camelCase` with a `my` 
  prefix for all internal functions  
  (e.g., `async function myTrainModel()`)
- **Logic First** — `async/await` over `.then()` promises for 
  readable, linear control flow
- **Single-File Firmware** — complete Arduino sketches in one 
  `.ino` file; every component visible without navigating a 
  library tree
- **MIT License** — all code open source and freely reusable

---

## 🔧 Hardware Platforms

- **Seeedstudio XIAO ESP32-S3 Sense** — primary platform  
  ($15-40 USD, 8MB PSRAM, OV2640 camera, touch, OLED)
- **Arduino Portenta H7** — secondary platform  
  *(ports in progress)*

<!--
- **XIAO ESP32-S3 + Microphone** — audio work  
- **XIAO ESP32-S3 + IMU** — motion work
-->

---

## 🤝 Community & Collaboration

We collaborate with industry and academic researchers to bring 
Edge AI into the K-12 and hobbyist ecosystem.

**Member:** TinyML4D / MLSys Community

Contributions, ports to new hardware, and curriculum adaptations 
are welcome. See individual repository CONTRIBUTING.md files.

---

## 📬 Contact

- GitHub: [@hpssjellis](https://github.com/hpssjellis)
- LinkedIn: [Jeremy Ellis](https://www.linkedin.com/in/jeremy-ellis-4237a9bb/)

---

*"Master the logic, then command the machine."*
