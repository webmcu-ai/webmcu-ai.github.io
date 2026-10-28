# webmcu-ai

**TinyML and WebAI — from a $15 microcontroller to a Chrome browser, no cloud required.**

Hi, I'm [Jeremy Ellis](https://github.com/hpssjellis) — a high school Computing, Machine Learning and Robotics teacher in British Columbia, Canada, with about 35 years in the classroom and a deep interest in making AI genuinely understandable. Not black-box AI. Not cloud-dependent AI. The kind where you can read every weight, every gradient, every line of code, and know exactly what the machine is doing and why.

This organization collects my open-source work at the intersection of **TinyML** (machine learning on microcontrollers) and **WebAI** (machine learning in the browser via TensorFlow.js and the WebSerial API). The hardware is cheap enough for a classroom. The code is single-file and dependency-free. The goal is that a student, or a researcher in a global south university with unreliable internet, can train and deploy a working vision classifier in under ten minutes without sending any data to the cloud.

Nothing here is intended to be a polished, final, error-free product. Instead, these projects serve as proofs of ability and accessible learning blueprints where students can read, experiment with, and even have an AI explain every single line of both the webpage interface and the tinyML firmware.

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
| Vision Classification | [firmware](https://github.com/webmcu-ai/on-device-vision-and-web/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-vision-and-web) | [index.html](https://github.com/webmcu-ai/on-device-vision-and-web/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/on-device-vision-and-web/) |
| Vision FOMO object x, y detection | [firmware](https://github.com/webmcu-ai/on-device-fomo/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/on-device-fomo) | [index.html](https://github.com/webmcu-ai/on-device-fomo/blob/main/index.html)| [live demo](https://webmcu-ai.github.io/on-device-fomo/index.html) |
| Vision Regression | [firmware](https://github.com/webmcu-ai/on-device-regression/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/on-device-regression)  | [index.html](https://github.com/webmcu-ai/on-device-regression/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/on-device-regression/index.html) |
| Vision Anomaly | [firmware](https://github.com/webmcu-ai/on-device-vision-anomaly/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/on-device-vision-anomaly) | [index.html](https://github.com/webmcu-ai/on-device-vision-anomaly/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/on-device-vision-anomaly/index.html) |
| Sound / Wake Word(s) Detection | [firmware](https://github.com/webmcu-ai/on-device-sound/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-sound) | [index.html](https://github.com/webmcu-ai/on-device-sound/blob/main/index.html)| [live demo](https://webmcu-ai.github.io/on-device-sound/index.html) |
| Motion X, Y, Z Acceleration (webBLE for Cell Phone) | [firmware](https://github.com/webmcu-ai/on-device-motion/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-motion) | [index.html](https://github.com/webmcu-ai/on-device-motion/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/on-device-motion/index.html) |
| Motion Anomaly (WebBLE for Cell Phone) | [firmware](https://github.com/webmcu-ai/on-device-motion-anomaly/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-motion-anomaly) | [index.html](https://github.com/webmcu-ai/on-device-motion-anomaly/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/on-device-motion-anomaly/index.html) |




---


## Proof of on-device WebBLE  
Latest bluetooth BLE work with the XIAO esp32s3 and the nano33BleSense and your cell phone motion sensor.   

| ML | on-device firmware Xiao ML Kit | on-device firmware Nano33BleSense | on-device github | index.html | WebBLE Live Demo |
|:---|:---|:---|:---|:---|:---|
|BLE Sensor Fusion XIAO and Nano33BleSense| [firmware-XIAO-ML-Kit](https://github.com/webmcu-ai/on-device-ble-sensor-fusion-nano33/blob/main/esp32-v15.ino) | [firmware-nano33bleSense](https://github.com/webmcu-ai/on-device-ble-sensor-fusion-nano33/blob/main/nano33-v15.ino)  | [github](https://github.com/webmcu-ai/on-device-ble-sensor-fusion-nano33) | [index.html](https://github.com/webmcu-ai/on-device-ble-sensor-fusion-nano33/blob/main/index.html) | [WebBLE Live Demo](https://webmcu-ai.github.io/on-device-ble-sensor-fusion-nano33/index.html) | 

---

## Proof of on-device LoRa
Latest LoRa work with the XIAO esp32s3 sense with camera, Mic, SD Card and the wio-sx1262 LoRa Module 

| ML | on-device firmware | on-device github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|:---|
| Vision Classification with LoRa Transmission | [firmware.ino](https://github.com/webmcu-ai/vision-classification-lora/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/vision-classification-lora) | [index.html](https://github.com/webmcu-ai/vision-classification-lora/blob/main/index.html) | [live web Demo](https://webmcu-ai.github.io/vision-classification-lora/index.html) |


---


## Proof of on-device Sensor Fusion with the Arduino Nano33BleSense 
$39.70 USD Nano 33 BLE Sense REV1 or REV 2 at the Arduino Store https://store-usa.arduino.cc/products/nano-33-ble-sense-rev2-with-headers

| ML | on-device firmware | on-device github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|:---|
| Nano33ble-sense-web-ble-and Serial sensor-fusion| [firmware](https://github.com/webmcu-ai/nano33ble-sense-web-ble-sensor-fusion/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/nano33ble-sense-web-ble-sensor-fusion) | [index.html](https://github.com/webmcu-ai/nano33ble-sense-web-ble-sensor-fusion/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/nano33ble-sense-web-ble-sensor-fusion/index.html) |

---



## Proof of on-device Vision Classification Federated Learning
Back to using the XIAO ML Kit, full multi location Federated Vision Learning.
Note: This has not been fully tested since I just have so many things on the go at the moment. 

| ML | on-device firmware | on-device github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|:---|
| Federated Vision Learning | [firmware](https://github.com/webmcu-ai/vision-federated-webble/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/vision-federated-webble) | [index.html](https://github.com/webmcu-ai/vision-federated-webble/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/vision-federated-webble/index.html) |

---


## Proof of on-device Dual Core ML 
Latest LoRa work with the XIAO esp32s3 sense with camera, Mic, SD Card and the wio-sx1262 LoRa Module 

| ML | on-device firmware | on-device github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|:---|
| Vision & Sound on Dual Core Device| [firmware](https://github.com/webmcu-ai/on-device-vision-sound/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-vision-sound) | [index.html](https://github.com/webmcu-ai/on-device-vision-sound/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/on-device-vision-sound/index.html) |


---



## Proof of Spiking Neural Networks SNN

| ML | on-device firmware | on-device github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|:---|
| SNN and ANN Motion | [firmware.ino](https://github.com/webmcu-ai/on-device-motion-snn/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/on-device-motion-snn) | [index.html](https://github.com/webmcu-ai/on-device-motion-snn/blob/main/index.html) | [motion SNN Live Demo](https://webmcu-ai.github.io/web-vision-snn/) |
| SNN and ANN Vision| [firmware.ino](https://github.com/webmcu-ai/web-vision-snn/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/web-vision-snn) | [index.html](https://github.com/webmcu-ai/web-vision-snn/blob/main/index.html) |  [vision SNN Live Demo](https://webmcu-ai.github.io/web-vision-snn/) |
| SNN and ANN Video (Multi-image) | [firmware.ino](https://github.com/webmcu-ai/web-video-snn/blob/main/firmware.ino) | [github](https://github.com/webmcu-ai/web-video-snn) | [index.html](https://github.com/webmcu-ai/web-video-snn/blob/main/index.html) |  [video SNN Live Demo](https://webmcu-ai.github.io/web-video-snn/index.html)|


---






## Proof of web Trained Device running int8 Quantization From Float32
The biggest complaint about all these on-device projects is that they are float32 and not int8. The reason was
to stick to traditional machine learning and not do the more complex quantization. This project 
is testing web float32 training and int8 conversion then getting it working on the device. Looking into having it train in float32 on the device and converting it to int8 on the device. 

| ML | on-device firmware | on-device github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|:---|
| web to int8 Vision Model| [firmware](https://github.com/webmcu-ai/web-train-int8/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/web-train-int8) | [index.html](https://github.com/webmcu-ai/web-train-int8/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/web-train-int8/index.html) |

---



## Proof of on-device full IoT (WebSerial, WebWiFi, WebBLE, partial LoRa)
First attempt at web WiFi so far a bit irritating that we need a local websocket using python or Node. I am debating a render.com cloud version but that destroys the local private tone of most of what we are working with here. This is not yet very smooth. Note the local server generates the webpage that communicates with the device.

Note: WebWifi needs the webpage downloaded or the node or python webserver.

| ML | on-device Firmware | Github | Node version  | Python version (not tested) | Live Demo (Works for WebSerial, WebBLE, WebLoRa) |
|:---|:---|:---|:---|:---|:---|
| Island CNN Interpretability | [firmware](https://github.com/webmcu-ai/on-device-full-iot/blob/main/firmware.ino) |[github](https://github.com/webmcu-ai/on-device-full-iot) | [server-node.js](https://github.com/webmcu-ai/on-device-full-iot/blob/main/server-node.js) | [server-python.py](https://github.com/webmcu-ai/on-device-full-iot/blob/main/server-python.py) | [Live Demo (download for webWiFi)](https://webmcu-ai.github.io/on-device-full-iot/index.html)

---


## Proof of Island CNN
Early 1990 I was making 3 layer 8 nodes per layer Neural Networks using Quick Pascal to try to get a human understanding of how
they work, now called Interpretability and is now understood to be nearly impossible and that Machine Learning is basically a black box. (I probably should not have spent a decade manually adjusting weights, I also should have looked up Geoffrey Hinton, another Canadian, as I knew nothing about back propagation while he was working on it. My Neural Networks always oscillated between classes). <br><br>
This site is basically a Claude improved version of what I was trying to do, with the added interesting concept that if a human can understand a small CNN to potentially improve it or reduce the number of connections, perhaps a machine can do the same for a larger model. <br><br>
Unlike most of my pages that I fully undersstand this one is a bit above my IQ. I would love if a few researchers had a look at what it is trying to do and give me some feedback or DM me on [linkedIn jeremy-ellis-4237a9bb](https://www.linkedin.com/in/jeremy-ellis-4237a9bb)

| ML | on-device firmware | Github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|:---|
| Island CNN  | Not yet on-device  | [github](https://github.com/webmcu-ai/island-cnn) | [index.html](https://github.com/webmcu-ai/island-cnn/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/island-cnn/index.html) |

---






# Resources


## Local Private WebAI Agentic Agent
Similar to my Gemma4 code https://webmcu-ai.github.io/local-gemma4-pwa/index.html  
and the ollama webpage supporting code at https://webmcu-ai.github.io/ollama-gemma4-12b-pwa/index.html

| ML |  github | index.html | Web Training Assist Demo |
|:---|:---|:---|:---|
| Local Private Agentic Agent | [github](https://github.com/webmcu-ai/local-agentic-web) | [index.html](https://github.com/webmcu-ai/local-agentic-web/blob/main/index.html) | [live demo](https://webmcu-ai.github.io/local-agentic-web/index.html) |

---


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
