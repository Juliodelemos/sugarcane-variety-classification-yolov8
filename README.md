# sugarcane-variety-classification-yolov8
Code repository for the paper "Benchmarking sugarcane variety identification under controlled conditions"
# Benchmarking sugarcane variety identification under controlled conditions: a deep learning classification approach

[![DOI](https://img.shields.io/badge/Dataset_DOI-10.25824%2Fredu%2FS1OJFI-blue)](https://doi.org/10.25824/redu/S1OJFI)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.13.0-EE4C2C.svg)](https://pytorch.org/)
[![Ultralytics](https://img.shields.io/badge/YOLOv8-Ultralytics-black)](https://github.com/ultralytics/ultralytics)

This repository contains the official code implementation and supplementary materials for the paper **"Benchmarking sugarcane variety identification under controlled conditions: a deep learning classification approach"**, submitted to *PLOS One*.

## 📌 Overview

Accurate identification of sugarcane varieties is crucial for optimizing agricultural productivity and management. This project presents a Computer Vision (CV) approach using a customized **YOLOv8-cls** model to classify four commercially important sugarcane varieties in Brazil:
* **CTC-1007**
* **IAC-5503**
* **RB-5375**
* **RB-7515**

The methodology includes a deterministic image preprocessing step using OpenCV to remove backgrounds, followed by fine-tuning a pre-trained YOLOv8 classification model. To ensure statistical robustness, the training and evaluation process was validated across **10 independent runs** using different random seeds and dataset splits.

## 📊 Dataset Availability

The original dataset comprises 1,476 high-resolution images captured under controlled laboratory conditions. The full dataset is publicly available at the Repositório de Dados de Pesquisa da Unicamp (REDU):

* **Dataset Link:** [https://doi.org/10.25824/redu/S1OJFI](https://doi.org/10.25824/redu/S1OJFI)

> **Note:** Before running the training scripts, download the dataset from the link above and place it in the `Dataset_Original/` directory as structured in the notebooks.

## ⚙️ Requirements

To reproduce the experiments, you will need the following libraries:
* `python >= 3.8`
* `torch == 1.13.0`
* `torchvision`
* `ultralytics` (YOLOv8 framework)
* `opencv-python == 4.7.0`
* `matplotlib == 3.6.0`
* `seaborn == 0.11.2`
* `pandas`
* `numpy`

## 📂 Repository Structure

* `preprocessing.ipynb` / `preprocessing.py`: Script containing the OpenCV-based adaptive thresholding and contour detection workflow used to segment the sugarcane billets and remove the black background prior to training.
* `yolov8_repeated_runs_analysis.ipynb`: The main Google Colab notebook used to compute the repeated-run statistics. It includes the YOLOv8-cls fine-tuning configuration, the 10-seed loop with Monte Carlo Cross-Validation (Random Subsampling), and the generation of the final performance metrics.

## 🚀 How to Run (Reproducibility)

1.  **Clone this repository:**
    ```bash
    git clone [https://github.com/](https://github.com/)[YOUR_GITHUB_USERNAME]/[YOUR_REPOSITORY_NAME].git
    cd [YOUR_REPOSITORY_NAME]
    ```
2.  **Download and prepare the dataset:**
    Extract the REDU dataset into the root folder. Run the preprocessing script if you wish to apply the exact background removal step described in the paper.
3.  **Run the Statistical Analysis:**
    Open the `yolov8_repeated_runs_analysis.ipynb` notebook in Google Colab (or your local Jupyter environment). Update the dataset path variable (`DATASET_ORIGINAL`) and run all cells. The script will automatically perform the 10 training rounds and output the Confidence Intervals.

## 🏆 Main Results

Under controlled experimental conditions, the customized YOLOv8-cls model achieved the following performance on the independent test set (averaged across 10 independent runs):

* **Mean Top-1 Accuracy:** 99.59%
* **Standard Deviation:** ± 0.40%
* **95% Confidence Interval:** [99.31%, 99.88%]
* **Mean Average F1-Score:** 0.973 (Reference single-run)

## 📝 Citation

If you find this code or the associated dataset useful for your research, please consider citing our paper:

```bibtex
@article{delemos2026sugarcane,
  title={Benchmarking sugarcane variety identification under controlled conditions: a deep learning classification approach},
  author={de Lemos, Julio Cesar and de Angelis, Andr{\'e} Franceschi},
  journal={PLOS One},
  year={2026},
  note={Under Review}
}
