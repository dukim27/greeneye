# GreenEye

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

GreenEye is a real-time traffic signal recognition system designed to help visually impaired pedestrians cross roads more safely. Unlike approaches that recognize only red and green pedestrian signals, GreenEye was developed to recognize both the **traffic light state** and the **remaining countdown number** in real time.

The project was implemented in **Google Colab** using **YOLOv5** and a custom traffic-signal dataset collected from real road environments.

## Method

GreenEye follows the pipeline below:

1. Collect traffic signal images from real roads using a smartphone
2. Annotate pedestrian signal colors and countdown digits
3. Train a custom YOLOv5-based object detection model
4. Perform real-time recognition on road images and videos
5. Optionally convert detection results into assistive voice guidance for visually impaired users

## Dataset Availability

This repository contains a **small sample subset** of the GreenEye dataset for demonstration of the directory structure, annotation format, and training configuration.

The sample subset is composed of:
- **8 training image-label pairs**
- **2 validation image-label pairs**

These sample files are included to show the expected dataset format:
- `images/` contains input images
- `labels/` contains YOLO-format annotation files
- `train.txt` and `val.txt` define the training and validation splits
- `data.yaml` defines dataset paths and class names

The **full dataset used in the paper is not fully uploaded** to this repository in order to keep the repository lightweight and manageable. Researchers interested in the complete dataset may contact the author. The full dataset **may be shared upon reasonable request**.

To reproduce the full training results reported in the paper, the complete dataset should be organized in the same directory structure described in this repository.

## Classes

The dataset uses **14 classes**:

- `Green_Light`
- `Green_1`
- `Green_2`
- `Green_3`
- `Green_4`
- `Green_5`
- `Green_6`
- `Green_7`
- `Green_8`
- `Green_9`
- `Green_10`
- `Green_11`
- `Green_12`
- `Red_Light`

## Experimental Setting

The main setting reported in the paper includes:

- Model: **YOLOv5s**
- Input image size: **640**
- Epochs: **30**
- Batch size: **16**
- GPU: **NVIDIA V100 (Google Colab Premium)**

## Main Results

### Before balancing the dataset
- mAP@0.5: **0.64** (7:3 split)
- mAP@0.5: **0.75** (9:1 split)

### After resolving data imbalance
- mAP@0.5: **0.94** (7:3 split)
- mAP@0.5: **0.99** (9:1 split)
- Training time: **0.9 hr** (7:3 split), **1.1 hr** (9:1 split)
- Final F1 score: **0.96** at confidence **0.574**
- Red/Green recognition average: **99.5%**

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

## Code

The main implementation is provided in:

- `GreenEye.ipynb`

This notebook contains the final Colab-based implementation used for the project. A publicly cleaned version may also be provided as `GreenEye_public_ready.ipynb` if needed.

## Repository Structure

```text
.
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
│   └── Balanced_1113_9_1_best.pt   # optional pretrained weight
└── data/
    └── dataset_traffic/
        ├── images/
        ├── labels/
        ├── train.txt
        ├── val.txt
        └── data.yaml
```

## Quick Start

1. Clone the repository.
2. Open `GreenEye.ipynb` in Google Colab.
3. Prepare the dataset under `data/dataset_traffic/` using the structure shown above.
4. If available, place the pretrained weight file under `weights/`.
5. Run the notebook cells from top to bottom.

## Notes

- This repository archives the implementation and materials associated with the GreenEye project.
- The included sample dataset is for demonstration only and is not sufficient to reproduce the full paper results.
- Full-dataset access may be available upon reasonable request.
- Some paths and helper code may be lightly cleaned from the original development version for public release.

## Citation

If you use this code or reference this project, please cite:

@inproceedings{kim2023greeneye,
  author    = {Danu Kim},
  title     = {GreenEye: Development of Real-Time Traffic Signal Recognition System for Visual Impairments},
  booktitle = {Proceedings of the Korea Software Congress 2023},
  year      = {2023}
}

## Contact

**Danu Kim**  
Korea International School, Jeju Campus  
Email: dukim27@kis.ac
