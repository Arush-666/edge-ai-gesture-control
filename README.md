# Edge AI Gesture Control & 3D Web Serial Showcase

Standalone, offline TinyML gesture-recognition controller built on **Arduino UNO Q** and an **MPU6050** 6-axis IMU (`accelX/Y/Z` + `gyroX/Y/Z` at `50 Hz`)[cite: 2, 4]. Uses **Spectral Analysis (FFT)** and an **`int8` quantized TensorFlow Lite** neural network to classify hand motions in real time and drive a browser-based **3D 6-DOF Robotic Arm** and **Smart Light Room** via the **Web Serial API**[cite: 2, 4].

## Key Performance Metrics
- **Validation Accuracy:** `100%` across `idle`, `up_down`, `circle`, and `wave`[cite: 2]
- **Total Inference Latency:** `126 ms` (`109 ms` FFT Spectral DSP + `17 ms` classifier)[cite: 2]
- **Memory Footprint:** `3.2 KB` Peak RAM | `35.7 KB` Flash (`int8` quantized)[cite: 2]
- **Windowing:** `2,000 ms` sliding window (`500 ms` stride) at `50 Hz`[cite: 2]

## 🔌 Hardware Pinout (MPU6050 → Arduino UNO Q)
| MPU6050 Pin | Arduino UNO Q Pin | Function |
| :--- | :--- | :--- |
| **VCC** | `3.3V` / `5V` | Power Supply[cite: 2] |
| **GND** | `GND` | Common Ground[cite: 2] |
| **SDA** | `A4` / `SDA` | I2C Serial Data (`400 kHz`)[cite: 2] |
| **SCL** | `A5` / `SCL` | I2C Serial Clock[cite: 2] |

##  Running the Live 3D Web Serial Interface
1. Flash `firmware/gesture_inference/gesture_inference.ino` to your **Arduino UNO Q** (`115200` baud).
2. Close the Arduino IDE Serial Monitor so the COM port is free.
3. Open `web-demo/gesture_live_3d_demo_2.html` in **Google Chrome** or **Microsoft Edge**[cite: 4].
4. Click **🔌 Connect Arduino** and select your board's USB port[cite: 4].