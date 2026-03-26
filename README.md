# 🤖 CLIP Model vs Baby Dataset

An experiment evaluating **OpenAI's CLIP model** (ViT-L/14) on a visual object recognition dataset — and comparing its performance against human babies across 5 image conditions.

---

## 📌 Project Overview

This project investigates how well CLIP, a large vision-language model, recognizes objects under different visual conditions, and whether its recognition patterns align with or diverge from those of human infants. The dataset includes 8 object categories presented in 5 progressively abstract visual conditions.

**Model:** CLIP ViT-L/14 (`openai/clip-vit-large-patch14`)  
**Key Finding:** CLIP outperforms babies on Silhouettes (95%) and Blurred (83%) images, but underperforms on Geons (53%) — reversing the baby pattern.

---

## 📂 Project Structure

```
├── clip-vs-baby.ipynb    # Main Jupyter Notebook
└── README.md
```

> Dataset is downloaded automatically via URL inside the notebook.

---

## 🗂️ Dataset

| Property | Details |
|---|---|
| Source | [OSF - Model vs Baby dataset](https://osf.io/download/ba4g2/) |
| Conditions | Realistic, Features, Blurred, Geons, Silhouettes |
| Classes | Airplane, Car, Chair, Cup, Dog, Donkey, Duck, Hat |
| Model Input | RGB images resized to 224×224 |

---

## 🧪 Methodology

### 1. CLIP Model Analysis
- Loaded `openai/clip-vit-large-patch14` (~400M parameters)
- Inspected vision & text transformer architecture
- Analyzed parameter counts per module

### 2. Zero-Shot Classification
- Generated text prompts: `"a photo of a {label}"` for each of 8 classes
- Computed cosine similarity between image and text embeddings
- Predicted label = highest similarity text embedding

### 3. Evaluation Per Condition
- Computed accuracy and confusion matrix for each of the 5 conditions
- Saved results to JSON for reproducibility

### 4. CLIP vs Baby Comparison

| Condition | CLIP Accuracy | Baby Accuracy | Verdict |
|---|---|---|---|
| Realistic | 100% | high | Similar ✅ |
| Features | 83% | lower | CLIP better 🤖 |
| Blurred | 83% | lower | CLIP better 🤖 |
| Silhouettes | 95% | lower | CLIP better 🤖 |
| Geons | 53% | higher | Babies better 👶 |

---

## 💡 Key Insights

- **CLIP dominates** on silhouette and blurred conditions — suggesting strong shape recognition without texture cues
- **Babies outperform CLIP on Geons** — CLIP reverses the baby pattern, performing worse on geons than features
- **Both peak on Realistic** — confirming realistic images are easiest for both humans and models

---

## ▶️ How to Run

### Prerequisites

```bash
pip install transformers torch torchvision pillow numpy pandas matplotlib seaborn scikit-learn tqdm jupyter
```

### Run the Notebook

```bash
jupyter notebook clip-vs-baby.ipynb
```

> The dataset is automatically downloaded inside the notebook — no manual download needed.

---

## 🛠️ Tech Stack

- **Python 3**
- **HuggingFace Transformers** — CLIP model & processor
- **PyTorch** — model inference
- **PIL (Pillow)** — image loading
- **scikit-learn** — confusion matrix, accuracy
- **matplotlib**, **seaborn** — visualization

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
