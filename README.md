# Self-Supervised Anomaly Detection for Industrial IoT (SWaT Dataset)

[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.9+-red.svg)](https://pytorch.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📌 Overview

This project implements **six self-supervised and unsupervised anomaly detection models** to identify cyber-attacks in Industrial Control Systems (ICS) using the **Secure Water Treatment (SWaT)** dataset. The models learn normal system behavior and detect deviations indicative of malicious intrusions targeting sensors and actuators.

## 🏗️ Models Implemented

| Model | Type | Key Metric |
|-------|------|------------|
| **VAE** (Variational Autoencoder) | Generative | ROC AUC: 0.993 |
| **LSTM Autoencoder** | Recurrent | ROC AUC: 0.99 |
| **USAD** (UnSupervised Anomaly Detection) | Adversarial Autoencoder | ROC AUC: 0.976 |
| **Isolation Forest** | Ensemble | Accuracy: 0.95 |
| **One-Class SVM** | Kernel Method | ROC AUC: 0.79 |
| **K-Means** | Clustering | ROC AUC: 0.14 |

## 👥 Team Members & Contributions

| Name | Contribution | GitHub |
|------|--------------|--------|
| **Saja Rafat Gaber Mahmoud** | Preprocessing & USAD Model | [@Sajatronic](https://github.com/Sajatronic) |
| **Nourhan Mohsen Mohamed** | EDA & VAE Model | [@nourhan](https://github.com/nourhan03) |
| **Nada Emad Mahmoud** | Isolation Forest & LSTM Autoencoder | [@nada](https://github.com/NadaEmad2002) |
| **Aya Ibrahim Ramadan** | One-Class SVM & K-Means | [@aya](https://github.com/ayaibrahimramadan5-ai) |

## 🔗 Individual Notebooks

| Model | Author | Notebook Link |
|-------|--------|----------------|
| USAD | Saja | [View Notebook](notebooks/Saja_USAD_Model.ipynb) |
| VAE | Nourhan | [View Notebook](notebooks/Nourhan_VAE_Model.ipynb) |
| LSTM + Isolation Forest | Nada | [View Notebook](notebooks/Nada_LSTM_IsolationForest.ipynb) |
| OC-SVM + K-Means | Aya | [View Notebook](notebooks/Aya_OCSVM_KMeans.ipynb) |

## 📊 Dataset: SWaT (Secure Water Treatment)

- **Source**: Singapore University of Technology and Design (SUTD)
- **Features**: 51 continuous/discrete variables (sensors + actuators)
- **Duration**: 11 days (7 days normal + 4 days under attack)
- **Total Records**: 900,000+ timestamped data points
- **Access**: Request from [iTrust, SUTD](https://itrust.sutd.edu.sg/itrust-labs_datasets/dataset_info/) [citation:8]

## 🔧 Preprocessing Steps

1. **Cleaning**: Strip whitespace, remove duplicates
2. **Missing Values**: 
   - Binary actuators → 0
   - Critical sensors → Linear interpolation
   - Others → Forward fill + median imputation
3. **Normalization**: MinMaxScaler [0,1]
4. **Split**: 70% training (normal only) / 30% testing (normal + attacks)
5. **Tensor Preparation**: PyTorch tensors with batch size 1024

## 🚀 Quick Start

### Prerequisites

```bash
pip install -r requirements.txt
