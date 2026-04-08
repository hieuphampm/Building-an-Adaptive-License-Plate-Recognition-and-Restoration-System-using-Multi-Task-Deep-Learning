# Adaptive Vietnamese License Plate Recognition and Retrieval System

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.8%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-ee4c2c)

This repository contains the official implementation of the paper/project: **"Building an Adaptive Vietnamese License Plate Recognition and Retrieval System using Multi-Task Deep Learning"**.

## 📖 Abstract
Automatic License Plate Recognition (ALPR) is an essential component of intelligent transportation, yet its performance is often degraded by real-world image distortions and regional plate complexities. We propose a highly adaptive, multi-task deep learning framework specifically designed for the Vietnamese license plate context. By dynamically routing images based on their quality, the system achieves significant robustness against real-world distortions while maintaining optimal computational throughput.

## ✨ Key Features
* **Adaptive Routing:** A lightweight Quality Assessment Module (QAM) classifies plates to bypass unnecessary processing, saving computational resources.
* **Text-Preserving Restoration:** Selectively enhances blurry or degraded plates using a Swin2SR backbone without hallucinating fake characters.
* **Robust OCR:** A hybrid ResNet18-PARSeq architecture specifically fine-tuned for the typographic constraints of Vietnamese license plates.
* **End-to-End Pipeline:** Seamless integration from full-frame vehicle detection to final character string retrieval.

## 🏗️ System Architecture

Our multi-task pipeline consists of four sequential, conditional stages:

1.  **Module 1: License Plate Detection:** A fine-tuned `YOLOv8-nano` localizes plate instances in real-time.
2.  **Module 2: Quality Assessment & Routing (QAM):** A `MobileNetV3-Small` classifier acts as an intelligent router, categorizing patches as *Clear*, *Restorable*, or *Unrestorable*.
3.  **Module 3: Conditional Image Restoration:** *Restorable* images are processed by a `Swin2SR` network to recover textual legibility.
4.  **Module 4: Character Recognition (OCR):** A hybrid `ResNet18 + PARSeq` model transcribes the characters for vehicle information retrieval.

*(Recommend adding a block diagram image here: `![Architecture](path/to/architecture_image.png)`)*

## 📊 Results

The system has been evaluated under challenging real-world conditions, demonstrating state-of-the-art performance for Vietnamese ALPR:

| Metric | Accuracy |
| :--- | :---: |
| **Character Accuracy** | 96.07% |
| **Sequence Accuracy** | 89.69% |
| **QAM Overall Accuracy** | 88.67% |
| **Restoration PSNR** | 27.39 dB |

## ⚙️ Installation

**1. Clone the repository:**
```bash
git clone [https://github.com/hieuphampm/Building-an-adaptive-Vietnamese-license-plate-recognition-and-retrieval-system-using-multi-task-deep.git](https://github.com/hieuphampm/Building-an-adaptive-Vietnamese-license-plate-recognition-and-retrieval-system-using-multi-task-deep.git)
cd Adaptive-VN-ALPR