# webmcu-ai

**TinyML and WebAI — from a $15 microcontroller to a Chrome browser, no cloud required.**

Hi, I'm [Jeremy Ellis](https://github.com/hpssjellis) — a high school Computing, Machine Learning and Robotics teacher in British Columbia, Canada, with about 35 years in the classroom and a deep interest in making AI genuinely understandable. Not black-box AI. Not cloud-dependent AI. The kind where you can read every weight, every gradient, every line of code, and know exactly what the machine is doing and why.

This organization collects my open-source work at the intersection of **TinyML** (machine learning on microcontrollers) and **WebAI** (machine learning in the browser via TensorFlow.js and the WebSerial API). The hardware is cheap enough for a classroom. The code is single-file and dependency-free. The goal is that a student, or a researcher in a global south university with unreliable internet, can train and deploy a working vision classifier in under ten minutes without sending any data to the cloud.

---

## 📄 Papers (webmcu-ai Series)

**Paper 1 — On-Device Vision Training, Deployment, and Inference on a Thumb-Sized Microcontroller**  
Complete CNN backpropagation on the ESP32-S3: 1,680 lines of C++, no cloud, no external ML dependencies.  
Github → [on-device-vision-ai](https://github.com/webmcu-ai/on-device-vision-ai) , Paper 1 →  [arXiv April 2604.23012](https://arxiv.org/abs/2604.23012)

**Paper 2 — WebSerial Vision Training for Microcontrollers**  
A single-file browser companion to Paper 1: index.html, firmware flash, firmware.ino, image capture, TensorFlow.js training, weight export, and live activation heatmaps — all from one HTML file over WebSerial.  
Github → [webmcu-vision-web](https://github.com/webmcu-ai/webmcu-vision-web) ,  Paper 2 → [arXiv April 2604.22834](https://arxiv.org/abs/2604.22834) 



---





# Flagship WebSerial and on-Device Vision

| ML | Firmware | Github | index.html | Web-Demo | Web-PWA-for-offline | ArXIV Pre-Print Paper |
|:---|:---|:---|:---|:---|:---|:---|
| Web and On Device webSerial Vision Classification | [web-firmware](https://github.com/webmcu-ai/webmcu-vision-web/blob/main/firmware.ino) | [web-github](https://github.com/webmcu-ai/webmcu-vision-web) | [index.html](https://github.com/webmcu-ai/webmcu-vision-web/blob/main/index.html) | [web-demo](https://webmcu-ai.github.io/webmcu-vision-web/index.html) | [web-pwa-offline-demo](https://webmcu-ai.github.io/webmcu-vision-pwa/index.html) |[arXiv April 2604.22834](https://arxiv.org/abs/2604.22834) |
| On-Device Vision Classification | [on-device firmware](https://github.com/webmcu-ai/on-device-vision-ai/blob/main/firmware.ino) |[on-device github](https://github.com/webmcu-ai/on-device-vision-ai) | | | | [arXiv April 2604.23012](https://arxiv.org/abs/2604.23012) |



---


# Bread and Butter. All the Main on-device TinyML 
Soon with supporting webpages for sd card data transfer
## Complete webMCU-AI table

| ML | on-device firmware | on-device github | index.html| Live Web Demo |
|:---|:---|:---|:---|:---|
| Vision Classification | [firmware](https://github.com/webmcu-ai/on-device-vision-and-web/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-vision-and-web) | [index.html](https://github.com/webmcu-ai/on-device-vision-and-web/blob/main/index.html) | [Live Demo](https://webmcu-ai.github.io/on-device-vision-and-web/) |
| Vision FOMO object x, y detection | [firmware](https://github.com/webmcu-ai/on-device-fomo/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/on-device-fomo) | | |
| Vision Regression | [firmware](https://github.com/webmcu-ai/on-device-regression/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/on-device-regression) | | |
| Vision Anomaly | [firmware](https://github.com/webmcu-ai/on-device-vision-anomaly/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/on-device-vision-anomaly) | | |
| Sound / Wake Word(s) Detection | [firmware](https://github.com/webmcu-ai/on-device-sound/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-sound) | |  |
| Motion X, Y, Z Acceleration | [firmware](https://github.com/webmcu-ai/on-device-motion/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-motion) | | |
| Motion Anomaly | [firmware](https://github.com/webmcu-ai/on-device-motion/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-motion) | | |
| Vision Sound Dual Core | [firmware](https://github.com/webmcu-ai/on-device-vision-sound/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-vision-sound) | | |



---


## Proof of on-device WebBLE  
Latest bluetooth BLE work with the XIAO esp32s3 and the nano33BleSense and your cell phone motion sensor.   

| ML | on-device firmware Xiao ML Kit | on-device firmware Nano33BleSense | on-device github | index.html | WebBLE Live Demo |
|:---|:---|:---|:---|:---|:---|
|BLE Sensor Fusion XIAO and Nano33BleSense| [firmware-XIAO-ML-Kit](https://github.com/webmcu-ai/on-device-ble-sensor-fusion-nano33/blob/main/esp32-v15.ino) | [firmware-nano33bleSense](https://github.com/webmcu-ai/on-device-ble-sensor-fusion-nano33/blob/main/nano33-v15.ino)  | [github](https://github.com/webmcu-ai/on-device-ble-sensor-fusion-nano33) | [index.html](https://github.com/webmcu-ai/on-device-ble-sensor-fusion-nano33/blob/main/index.html) | [WebBLE Live Demo](https://webmcu-ai.github.io/on-device-ble-sensor-fusion-nano33/index.html) | 


---


## Spiking Neural Networks SNN

| ML | on-device firmware | on-device github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|:---|
| SNN and ANN Motion | [firmware.ino](https://github.com/webmcu-ai/on-device-motion-snn/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/on-device-motion-snn) | [index.html](https://github.com/webmcu-ai/on-device-motion-snn/blob/main/index.html) | [motion SNN Live Demo](https://webmcu-ai.github.io/web-vision-snn/) |
| SNN and ANN Vision| [firmware.ino](https://github.com/webmcu-ai/web-vision-snn/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/web-vision-snn) | [index.html](https://github.com/webmcu-ai/web-vision-snn/blob/main/index.html) |  [vision SNN Live Demo](https://webmcu-ai.github.io/web-vision-snn/) |
| SNN and ANN Video (Multi-image) | [firmware.ino](https://github.com/webmcu-ai/web-video-snn/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/web-video-snn) | [index.html](https://github.com/webmcu-ai/web-video-snn/blob/main/index.html) |  [video SNN Live Demo](https://webmcu-ai.github.io/web-video-snn/index.html)|


---


## BioComputing Demo's  

[https://github.com/hpssjellis/neuro-ml](https://github.com/hpssjellis/neuro-ml)

---


## Resources



For offline LLM using Gemma4:E2B PWA, first time 2 GB install, [https://webmcu-ai.github.io/local-gemma4-pwa/index.html](https://webmcu-ai.github.io/local-gemma4-pwa/index.html)

For offline LLM using Gemma4:12B PWA, first time 7 GB install, must also install [ollama.com](https://ollama.com/) and run this command for windows 
``` setx OLLAMA_ORIGINS "https://webmcu-ai.github.io"  ```
[https://webmcu-ai.github.io/ollama-gemma4-12b-pwa/index.html](https://webmcu-ai.github.io/ollama-gemma4-12b-pwa/index.html)

The Maker 100 Leaders Robotics [https://github.com/hpssjellis/maker100-leaders-robotics](https://github.com/hpssjellis/maker100-leaders-robotics)

The maker100 Curriculum [https://github.com/hpssjellis/maker100-curriculum](https://github.com/hpssjellis/maker100-curriculum)

All on-device firmware for offline flashing [https://github.com/webmcu-ai/download-for-offline-webmcu-ai](https://github.com/webmcu-ai/download-for-offline-webmcu-ai) for when using 
any of the [web-PWA](https://webmcu-ai.github.io/webmcu-vision-pwa/index.html) to flash all the code without the Arduino IDE or PlatformIO.


#### All use the XIAO ESP32-S3 for serial monitor only or use the [$15-40 USD xiaoML kit](https://www.seeedstudio.com/The-XIAOML-Kit.html) for full on-device training and inference.








---

## 🔧 Hardware

The primary platform is the **Seeed Studio XIAO ESP32-S3 Sense**, available as:
- the bare [XIAO ESP32-S3](https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32S3-Pre-Soldered-p-6334.html) module ($8.49 USD full replacement only, does not run the above)
- the [XIAO ESP32-S3 Sense](https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32S3-Sense-Pre-Soldered-p-6335.html) board with OV2640 camera ($14.90 USD, runs only with serial monitor)
- the full [XIAO ML Kit](https://www.seeedstudio.com/The-XIAOML-Kit.html) with OLED display and IMU ($38.90 USD with cables, sd card etc, $22 USD just for the boards, runs everything)

All three run the same firmware. The OLED and IMU degrade gracefully if the expansion board is absent. The price point is intentional — the whole system should fit in a classroom budget.
- For the complete ability I strongley recommend the full XIOA ML Kit. If you have cables and a micro sd card then the $22.00 USD
- version is probably fine  
- See the chart below for the costs of each part of the XIAO ESP32 S3 Sense as the kits get better.  
- 
<img width="800"  alt="image02-xiao" src="https://github.com/user-attachments/assets/96d9cd35-9808-4ca8-aab4-f28a21e5fa42" />



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
- Now AiEng4D new website coming for now use [mlsysbook.ai](https://mlsysbook.ai/)

Contributions, hardware ports, and curriculum adaptations are welcome. MIT license throughout.

---

*"Master the logic, then command the machine."*
