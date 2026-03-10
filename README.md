# GreenEye: Development of Real-Time Traffic Signal Recognition System for Visual Impairments

[![Paper](https://img.shields.io/badge/Paper-arXiv-blue)](https://arxiv.org/abs/2410.19840)  
[![Demo](https://img.shields.io/badge/Demo-YouTube-red)](https://www.youtube.com/watch?v=MtvqqKo5j5k&t=67s)  
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

<p align="center">
  <img src="assets/greeneye_overview.png" alt="GreenEye system overview" width="900"/>
</p>

<p align="center">
  Overview of the GreenEye system for real-time pedestrian traffic light and countdown recognition.
</p>

Official repository for **GreenEye: Development of Real-Time Traffic Signal Recognition System for Visual Impairments**.

## Publication

- **Conference:** Korea Software Congress (KSC) 2023
- **Organization:** KIISE
- **Paper:** [arXiv:2410.19840](https://arxiv.org/abs/2410.19840)

## Overview

GreenEye is a real-time traffic signal recognition system designed to help visually impaired pedestrians cross roads more safely. Unlike prior approaches that focused only on recognizing red and green pedestrian signals, GreenEye was developed to recognize both the **traffic light state** and the **remaining countdown number** in real time.

## Method

GreenEye follows the pipeline below:

1. Collect traffic signal images from real roads using a smartphone
2. Label pedestrian signal colors and countdown digits
3. Train a custom YOLOv5-based object detection model
4. Perform real-time recognition on road images and videos

The model was implemented in **Google Colab** using **YOLOv5**.

## Dataset Availability

This repository contains a small sample subset of the GreenEye dataset for demonstration of the directory structure, annotation format, and training configuration.

The sample subset is provided to show:
- the image-label pairing format
- the repository data structure
- the configuration files used by the project

The complete dataset used in the paper is not fully uploaded to this repository. Researchers interested in the full dataset may contact the author. The full dataset may be shared upon reasonable request.

## Experimental Setting

- Model: **YOLOv5s**
- Input image size: **640**
- Epochs: **30**
- Batch size: **16**
- GPU: **NVIDIA V100 (Google Colab Premium)**

## Main Results

### Before balancing the dataset
- mAP@0.5: **0.64** (7:3), **0.75** (9:1)

### After resolving data imbalance
- mAP@0.5: **0.94** (7:3), **0.99** (9:1)
- Training time: **0.9 hr** (7:3), **1.1 hr** (9:1)
- All 14 classes achieved about **99% precision**
- Final F1 score reached **0.96** at confidence **0.574**

## Example Detection Results

<p align="center">
  <img src="assets/greeneye_result.png" alt="GreenEye detection results" width="900"/>
</p>

<p align="center">
  Example real-road detection results of pedestrian traffic lights using GreenEye.
</p>

## Demo Video

- [GreenEye Demo Video](https://www.youtube.com/watch?v=MtvqqKo5j5k&t=67s)

## Presentation

- [KSC 2023 Presentation Slides](slides/greeneye_presentation.pdf)

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dukim27/GreenEye-Development-of-Real-Time-Traffic-Signal-Recognition-System-for-Visual-Impairments/blob/main/GreenEye.ipynb)

## Installation

Clone the repository:

```bash
git clone https://github.com/dukim27/GreenEye-Development-of-Real-Time-Traffic-Signal-Recognition-System-for-Visual-Impairments.git
cd GreenEye-Development-of-Real-Time-Traffic-Signal-Recognition-System-for-Visual-Impairments
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Code

The main implementation is provided in:

- `GreenEye.ipynb`

This notebook contains the final Colab-based implementation of the GreenEye system.

For quick inference or demonstration, you may optionally place the pretrained weight file below in the `weights/` directory:

- `weights/Balanced_1113_9_1_best.pt`

## Repository Structure

```text
greeneye/
├── README.md
├── GreenEye.ipynb
├── requirements.txt
├── LICENSE
├── .gitignore
├── assets/
│   ├── greeneye_overview.png
│   └── greeneye_result.png
├── slides/
│   └── greeneye_presentation.pdf
├── weights/
│   └── Balanced_1113_9_1_best.pt   # optional
└── data/
    └── dataset_traffic/
        ├── data.yaml
        ├── train.txt
        ├── val.txt
        ├── images/
        └── labels/
```

## Citation

If you use this code or reference this project, please cite:

Kim, D. (2023). *GreenEye: Development of Real-Time Traffic Signal Recognition System for Visual Impairments*. In **2023 Korea Software Cogress (KSC)**.

```bibtex
@inproceedings{kim2023greeneye,
  author    = {Danu Kim},
  title     = {GreenEye: Development of Real-Time Traffic Signal Recognition System for Visual Impairments},
  booktitle = {2023 Korea Software Congress (KSC)},
  year      = {2023},
  pages     = {1981--1983}
}
```

## Contact

**Danu Kim**  
Korea International School, Jeju Campus  
Email: dukim27@kis.ac
