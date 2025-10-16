# 🌀 TCL Air Conditioner Integration for Home Assistant

> Successfully tested with **TCL TAC-12CHDA**  
> Simple DIY project with ESP32 + USB cable. No cloud required.

***

## 🛠️ What You Need

- **ESP32** (e.g., ESP32-C3, WROOM32, NodeMCU)
- **USB-A plug or cable**  
  👉 I used this one: [AliExpress link](https://www.aliexpress.com/item/1005005776162012.html)
- **Home Assistant with ESPHome (from version 2023.3.0)**

***

## 🔌 Wiring

| USB-A Pin | Wire Color | → ESP32 Pin |
|-----------|------------|--------------|
| GND       | Black      | VIN/VCC      |
| D+        | Green      | GND          |
| D-        | Gray       | RXD          |
| VBUS      | Red        | TXD          |

### 🔍 Example Images
(Note: I did not pay attention to the wire colors in these images. The colors in the table generally match common USB-A cables that you can simply cut open.)

<img src="https://github.com/user-attachments/assets/9b674e06-41ca-4bcf-b09b-691a5fbd8545" width="400"/>
<br/>

![Wiring Example 2](https://github.com/user-attachments/assets/e30fadd9-19cd-47ec5c07_2_296x500](https://github.com/user-attachments/assets/5b3ccbb8-eb62-474

## 🧠 Setup in Home Assistant

> The solution is based on **ESPHome** and works only with Home Assistant.

### 1. Install ESPHome

- In Home Assistant, go to **Settings → Add-ons → ESPHome** and install

### 2. Create New Device

- In the ESPHome dashboard → "New Device"
- Select your ESP32 type, e.g., `esp32-c3-devkitm-1` or `nodemcu-32s`

### 3. Insert Configuration

#### Option A: Simple Configuration
[📄 Sample_conf.yaml](https://github.com/sorz2122/tclac/blob/master/Sample_conf.yaml)

#### Option B: Advanced Configuration
[📄 TCL-Conditioner.yaml](https://github.com/sorz2122/tclac/blob/master/TCL-Conditioner.yaml)

📝 **Important:**  
- Adjust WiFi credentials, device name, etc.  
- Comments in the YAML will help with setup

### 4. Flash to ESP32

- Connect USB cable or use OTA (Over-the-Air)

***

## ✅ Compatible Air Conditioners

The following models were successfully tested:

- **TCL:** TAC-07CHSA / TAC-09CHSA / TAC-12CHSA / TAC-12CHDA
- **Daichi:** AIR20AVQ1, AIR25AVQS1R-1, DA35EVQ1-1
- **Axioma:** ASX09H1 / ASB09H1
- **Dantex:** RK-12SATI / RK-12SATIE  
- ...and similar models

⚠️ **Note:**  
Even if the model designation matches, there may be differences (no USB port, no UART on the board, etc.).

***

## ☕ Support

[https://buymeacoffee.com/sorz2122](https://buymeacoffee.com/sorz2122)

<img src="https://github.com/user-attachments/assets/87d5d62f-ba5c-4a7e-a4b8-4cf1fd3018af" width="400"/>
<br/>

***

## 🔧 Advanced Configuration via Remote Package

You can load the configuration modularly:

```yaml
packages:
  remote_package:
    url: [https://github.com/sorz2122/tclac.git](https://github.com/sorz2122/tclac.git)
    ref: master
    files:
      - packages/core.yaml   # Main module
      # - packages/leds.yaml # Optional
    refresh: 30s
```
