# AIDI1002_Arpit_Kohli_FinalProject — LDM‑S Active Learning

Reproduction and extension of the paper **“Querying Easily Flip‑flopped Samples for Deep Active Learning” (ICLR 2024)**.  
This project demonstrates **label‑efficiency** using the LDM‑S strategy and adds three course‑aligned contributions:

1) **New dataset** (Fashion‑MNIST)  
2) **Parameter experiments** (query size, initial labeled pool, epochs)  
3) **Additional model** baseline (**MLP + entropy sampling**)

---

##  Project Overview
- **Goal:** Reproduce the paper’s MNIST/CIFAR‑10 experiments and evaluate LDM‑S under new datasets, settings, and baselines.
- **Why:** Reduce labeling cost by querying the most informative samples (near decision boundaries), and analyze robustness.

---

## 🔗 Paper & Official Code
- **Paper (arXiv):** Querying Easily Flip‑flopped Samples for Deep Active Learning (ICLR 2024)
- **Official LDM‑S repo used for reproduction:** U‑AIM‑SW‑STARLab/LDM‑S‑2024  
  *(contains `run_mnist.py`, `run_cifar10.py`, `strategies.py`, `main.py`, `utils.py`)*

> We clone and run the official scripts for “before‑changes” results, then add our contributions alongside.

---

## 🚀 Quickstart

### Run in **Google Colab** (recommended)
1. Open the notebook `AIDI1002_Arpit_Kohli_FinalProject.ipynb` in **Google Colab**.
2. Runtime → Change runtime type → **Hardware accelerator**: None (CPU) or GPU (T4).
3. Run all cells **top‑to‑bottom**:
   - Installs compatible TF/Keras & common libs.
   - Clones official LDM‑S repo.
   - **Reproduction**: runs `run_mnist.py` (and optionally `run_cifar10.py`).
   - **Contributions**:
     - Auto‑creates & runs `run_fashion_mnist.py` (Fashion‑MNIST).
     - Creates & runs a **parameter‑tuned MNIST** variant.
     - Executes **MLP + entropy** baseline (self‑contained).
   - Saves **CSV/PNG** to `results/`.

### Run **locally** (CPU is fine)
```bash
python -m venv .venv
# macOS/Linux:
source .venv/bin/activate
# Windows (PowerShell):
.venv\Scripts\activate

pip install "tensorflow==2.12.*" "keras==2.12.*" numpy scipy scikit-learn tqdm matplotlib pandas

# Clone official repo and reproduce:
git clone https://github.com/U-AIM-SW-STARLab/LDM-S-2024.git
cd LDM-S-2024
python run_mnist.py
# optional:
python run_cifar10.py

# Run our baseline (copy the file into this directory or use absolute path):
python entropy_baseline_mnist.py
```

---

## 🧱 Repository Structure
```
.
├─ notebooks/
│  ├─ AIDI_1002_Project_Report.ipynb     # report + code cells
│
├─ src/
│  ├─ run_fashion_mnist.py               # new dataset contribution (auto‑generated in Colab)
│  ├─ run_mnist_params10_100_8.py        # parameter‑tuned MNIST (auto‑generated in Colab)
│  ├─ entropy_baseline_mnist.py          # MLP + entropy AL baseline (standalone)
│
├─ results/                               # saved CSV/plots after runs
│  ├─ mnist_original.csv/png
│  ├─ cifar10_original.csv/png
│  ├─ fashion_mnist.csv/png
│  ├─ mnist_params_10_100_8.csv/png
│  ├─ baseline_mlp_entropy_mnist.csv/png
│  └─ combined_comparison.png
│
└─ README.md
```

---

## What’s Implemented
**Reproduction (before changes):** MNIST (`run_mnist.py`) — cycle‑level accuracy and labeled sample counts, plotted as **Accuracy vs Labeled Samples**.  
**Contribution — New dataset:** Fashion‑MNIST via `run_fashion_mnist.py`.  
**Contribution — Parameter experiments:** `query_size = 10`, `initial_size = 100`, `epochs = 8` (file: `run_mnist_params10_100_8.py`).  
**Contribution — Additional model baseline:** **MLP + entropy sampling** AL loop (`entropy_baseline_mnist.py`).

---

## Outputs
All runs save **CSV** (metrics) and **PNG plots** to `results/`.

Key figures:
- `mnist_original.png` (before changes)
- `fashion_mnist.png` (new dataset)
- `mnist_params_10_100_8.png` (tuned parameters)
- `baseline_mlp_entropy_mnist.png` (baseline)
- `combined_comparison.png` (overlay of curves)

---


---

## 📚 References
- Cho et al., *Querying Easily Flip‑flopped Samples for Deep Active Learning*, ICLR 2024 (arXiv:2401.09787).
- Official LDM‑S code: U‑AIM‑SW‑STARLab/LDM‑S‑2024.
- Keras/TensorFlow dataset APIs: MNIST, CIFAR‑10, Fashion‑MNIST.

---

## 🙋 Contact
- Author(s): Arpit Kohli, <add teammate>
- Course: AIDI 1002

