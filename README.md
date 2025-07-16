# 🛰️ SuperSR - Dual-Image Super Resolution for Satellite Imagery

> ✨ Unlocking Ultra-High Clarity from the Sky — Two Views, One Sharper Truth.

---

## 📌 Table of Contents

- [🔭 Inspiration](#-inspiration)
- [🚀 What it does](#-what-it-does)
- [🧱 Architecture](#-architecture)
- [🧪 Dataset & Preprocessing](#-dataset--preprocessing)
- [🧠 Model Overview](#-model-overview)
- [📊 Results](#-results)
- [⚙️ Tech Stack](#-tech-stack)
- [😤 Challenges](#-challenges)
- [🎉 Accomplishments](#-accomplishments)
- [📚 What we learned](#-what-we-learned)
- [🔮 What’s next?](#-whats-next)
- [💡 Usage](#-usage)
- [📎 References](#-references)

---

## 🔭 Inspiration

Every satellite tells a story — but when resolution is low, the story is blurred.  
We wanted to **reveal fine-grained details** in satellite imagery by **combining two low-res images** and reconstructing a sharper image using deep learning.

Whether for disaster relief, urban mapping, or agricultural monitoring — clarity matters.

---

## 🚀 What it does

- Takes **two low-res satellite images** of the same location  
- Fuses temporal/spatial data intelligently  
- Outputs a **high-resolution enhanced image**  
- All powered by deep learning and super-resolution techniques 🧠

---

## 🧱 Architecture



      Input Image 1           Input Image 2
          │                       │
     ┌────▼────┐           ┌──────▼──────┐
     │ Feature │           │ Feature     │
     │ Extract │           │ Extract     │
     └────┬────┘           └──────┬──────┘
          │                         │
          └─────► Feature Fusion ◄──┘
                      │
              Super-Resolution Head
                      │
              High-Resolution Output




---

## 🧪 Dataset & Preprocessing

- 🛰️ Source: [DIV2K](https://data.vision.ee.ethz.ch/cvl/DIV2K/) + Custom Synthetic Satellite Dataset  
- 📏 Resolutions: LR (64x64), HR (256x256)  
- 🌀 Augmentation:
  - Rotation, flipping, noise injection
  - Random patch cropping

---

## 🧠 Model Overview

We use a **Fusion-based CNN architecture** with optional attention module:

- Dual input streams (Siamese-like encoders)  
- Cross-channel fusion with residual blocks  
- Output through an upsampling decoder

---

## 📊 Results

### 📈 Quantitative Metrics

| Metric   | Bicubic | EDSR (Baseline) | 🛰️ SuperSR |
|----------|---------|-----------------|-------------|
| PSNR ↑   | 21.45   | 26.32           | **28.90**   |
| SSIM ↑   | 0.702   | 0.834           | **0.885**   |
| LPIPS ↓  | 0.310   | 0.212           | **0.145**   |

> 🔍 The improvements are not just numerical — they're **visually stunning** and contextually important for geo-spatial tasks.

---

## ⚙️ Tech Stack

| Layer        | Tools Used                   |
|--------------|------------------------------|
| Framework    | 🐍 Python, PyTorch            |
| Notebook     | 🧪 Jupyter, Google Colab      |
| Visuals      | Matplotlib, Seaborn, PIL     |
| Logs         | TensorBoard / Weights & Biases|
| Packaging    | Docker (optional), pipenv     |

---

## 😤 Challenges

- Aligning two temporally displaced satellite images  
- Retaining fine details while avoiding hallucinations  
- Balancing training time and image quality  
- Memory constraints on high-res patch processing

---

## 🎉 Accomplishments

- 🚀 Successfully created a dual-image super-resolution model  
- 🔬 Achieved **~28.9 PSNR**, **0.88 SSIM** on test set  
- ✨ Developed clean, scalable, and modular codebase  
- 💡 Created flexible preprocessing + training pipelines

---

## 📚 What We Learned

- The power of **multi-image fusion** in SR tasks  
- Trade-offs in architecture depth vs. output sharpness  
- Satellite-specific augmentation techniques  
- Interpreting PSNR/SSIM in meaningful visual terms

---

## 🔮 What’s Next?

- 🔍 Add temporal consistency for video-style SR  
- 🧠 Explore GAN-based output for crisper results  
- 🌍 Real-world dataset testing (e.g., Planet, Sentinel)  
- 📱 Deploy a mini demo app or API using Gradio / FastAPI

---

## 💡 Usage

```bash
# Clone repo
git clone https://github.com/vanshsaxena04/SuperSR.git
cd SuperSR

# Install dependencies
pip install -r requirements.txt

# Run Inference
python inference.py --img1 path/to/image1.png --img2 path/to/image2.png

# Or launch demo notebook
jupyter notebook SuperSR_Demo.ipynb