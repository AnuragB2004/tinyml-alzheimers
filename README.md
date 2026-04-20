# 🧠 TinyML-Based Real-Time Alzheimer’s Detection on Edge Devices

> Lightweight, real-time, four-class Alzheimer’s classification using quantized MobileNetV2 deployed on microcontrollers (ESP32)

📄 Based on our research paper:  
**TinyML-Based Real-Time Alzheimer's Disease Detection Using Quantized MobileNetV2 on Wearable IoT Edge Devices**

---

## 🚀 Overview

Alzheimer’s Disease (AD) affects over 55 million people globally. Early detection is critical, but current diagnostic methods require expensive MRI infrastructure and expert radiologists.

This project introduces a **TinyML-based pipeline** that enables:

- 📉 On-device inference (no cloud required)
- ⚡ Real-time detection (18 ms latency)
- 🔋 Ultra-low power (78 mW)
- 📦 Tiny model size (0.85 MB)

---

## 🧩 Key Features

- 🧠 **4-Class Classification**
  - NonDemented  
  - VeryMildDemented  
  - MildDemented  
  - ModerateDemented  

- ⚙️ MobileNetV2 (Transfer Learning)  
- 📉 INT8 Quantization (TensorFlow Lite)  
- 🔬 Grad-CAM Explainability  
- 📡 Edge Deployment (ESP32 + TinyML)  

---

## 📊 Dataset

- 📦 44,000 MRI images  
- 🧼 Skull-stripped  
- ⚖️ Balanced across 4 classes  

### Dataset Distribution
<img width="1966" height="856" alt="fig1_dataset_distribution" src="https://github.com/user-attachments/assets/df784abc-a618-42ff-9785-404181eaa635" />

---

## 🔄 Preprocessing Pipeline

- Resize → 224×224  
- Normalize → ImageNet statistics  
- Augmentation:
  - Rotation (±15°)
  - Horizontal flip
  - Brightness adjustment  

### Pipeline Visualization
<img width="1347" height="883" alt="fig12_preprocessing" src="https://github.com/user-attachments/assets/45e7ddfa-2109-4966-a05e-a05b81214d8d" />

---

## 🏗️ System Architecture

Pipeline stages:

1. MRI Input  
2. Preprocessing  
3. Feature Extraction (MobileNetV2)  
4. Fine-tuning  
5. Quantization (INT8)  
6. TFLite Conversion  
7. ESP32 Deployment  

### Architecture Diagram
<img width="1387" height="779" alt="fig2_system_architecture" src="https://github.com/user-attachments/assets/e5912eb8-5d4e-4827-a6fc-9a53803cc995" />

---

## 🧠 Model Architecture

- Backbone: MobileNetV2  
- Depthwise separable convolutions  
- Inverted residual blocks  
- Custom classification head  

### MobileNetV2
<img width="1483" height="741" alt="fig3_mobilenetv2" src="https://github.com/user-attachments/assets/31301496-1fd6-416c-8b97-a93295188c25" />

---

## 📈 Training Strategy

**Phase 1 (Epochs 1–10):**
- Freeze backbone
- Train classifier head

**Phase 2 (Epochs 11–50):**
- Fine-tune last layers
- Exponential learning rate decay

---

## 📊 Results

### 🔥 Performance

| Metric        | Value     |
|--------------|----------|
| Accuracy      | **91.8%** |
| Macro F1      | **0.917** |
| AUC-ROC       | **0.978** |
| Model Size    | **0.85 MB** |
| Latency       | **18 ms** |

## 🆚 Model Comparison

| Model | Size | Latency | Accuracy |
|------|------|--------|---------|
| VGG-16 | 138 MB | 812 ms | 88.2% |
| ResNet-50 | 25.6 MB | 456 ms | 90.4% |
| MobileNetV2 | 13.6 MB | 98 ms | 92.7% |
| **Ours (INT8)** | **0.85 MB** | **18 ms** | **91.8%** |

---

## 🧠 Explainability (Grad-CAM)

The model focuses on clinically relevant regions:
- Hippocampus  
- Entorhinal cortex  

### Grad-CAM Visualizations
<img width="1228" height="743" alt="fig10_gradcam" src="https://github.com/user-attachments/assets/81dbf4fa-27ed-4183-ad57-ec63c7efac49" />

---

## ⚡ Edge Deployment

- Device: ESP32  
- Runtime: TensorFlow Lite Micro  
- Connectivity: BLE / Wi-Fi  

### IoT Deployment
<img width="1391" height="803" alt="fig11_iot_deployment" src="https://github.com/user-attachments/assets/65f7c4d8-523e-439c-ae81-b27872504327" />

---

## 🔋 Power Consumption

| Mode        | Power |
|------------|------|
| Idle        | 12 mW |
| Inference   | 78 mW |
| BLE         | 42 mW |
| Sleep       | 8 mW |

---

## 🛠️ Tech Stack

- Python 3.10  
- TensorFlow 2.13  
- TensorFlow Lite / TFLite Micro  
- ESP32 (Xtensa LX6)  
- CUDA (training)  

---

## 📂 Project Structure

```

├── data/
├── models/
├── tflite/
├── esp32/
├── notebooks/
├── figures/
└── README.md

````

---

## ▶️ How to Run

### 1. Train Model
```bash
python train.py
````

### 2. Convert to TFLite

```bash
python convert.py --quantize int8
```

### 3. Deploy on ESP32

```bash
idf.py build flash monitor
```

---

## 🌍 Impact

* Enables AI on ultra-low-power devices
* Supports early-stage Alzheimer’s detection
* Useful for low-resource healthcare systems

---

## ⚠️ Limitations

* Uses 2D MRI slices (no 3D context)
* No demographic metadata
* Requires clinical validation

---

## 🔮 Future Work

* 3D MRI models
* Federated learning
* Multi-modal fusion (EEG + MRI)
* Portable MRI integration

---

