# ESA-Det: Edge-Prior and Spatial Adaptive Fusion for Remote Sensing Object Detection

## Overview

This repository provides the **core implementation** of the key modules proposed in our paper:

> **ESA-Det: Enhancing Remote Sensing Object Detection via Edge-Prior Infused Attention and Spatial Adaptive Fusion**

To promote reproducibility and further research, we release **lightweight and modular implementations** of the two main contributions:

* **Edge-Prior Infused Attention (EPIA)**
* **Spatial Adaptive Fusion (SAF) Block**

⚠️ Note: The full training pipeline is currently being organized and will be released in a subsequent update. This repository focuses on **clean, minimal, and reusable core modules**.

---

## 🔧 Key Components

### 1. Edge-Prior Infused Attention (EPIA)

**File:** `epia.py`
**Core Module:** `C3k2_EPIA`

#### Description

EPIA integrates **classical edge operators** into CNN feature learning to explicitly enhance boundary-aware representations.

#### Features

* Multi-operator edge extraction:

  * Sobel
  * Prewitt
  * Scharr
  * Robert
* Depthwise convolution implementation (efficient & parameter-free)
* Residual fusion with learnable convolution branch

#### Motivation

Remote sensing objects often exhibit:

* weak boundaries
* low contrast
* cluttered backgrounds

EPIA introduces **explicit structural priors** to address these issues.

---

### 2. Spatial Adaptive Fusion (SAF) Block

**File:** `saf.py`
**Core Module:** `A2C2f_SAF`


#### Structure

SAF follows a **three-stage pipeline**:

1. **AFC (Calibration)**
   Adaptive nonlinear feature normalization

2. **Fusion Gate**
   Frequency-aware spatial fusion

3. **FEA (Enhancement)**
   Multi-scale structural refinement

#### Characteristics

* Lightweight design
* Spatially adaptive feature fusion
* Strong performance on:

  * small objects
  * dense scenes
  * low-contrast targets

---

## 📦 Installation

```bash
git clone https://github.com/yourname/ESA-Det.git
cd ESA-Det
pip install -r requirements.txt
```

---

## 🚀 Usage

### Import Modules

```python
from epia import C3k2_EPIA
from saf import A2C2f_SAF
```

### Example Integration

```python
# Replace backbone block
backbone_block = C3k2_EPIA(c1=256, c2=256, n=2)

# Replace neck/head block
fusion_block = A2C2f_SAF(c1=512, c2=512, n=2)
```

---

## 📄 License

This project is released under the AGPL-3.0 License.
