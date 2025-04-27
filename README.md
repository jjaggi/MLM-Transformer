# Transformer-based Masked Language Model & Hangman Solver

## 🚀 Project Overview

This repo dives into **transformer architectures** applied to a character-level masked language task and pairs it with a strategic Hangman solver:

1. **Transformer-based Masked Language Model (MLM)** – Custom tokenizers, multi-head attention, and positional embeddings trained on millions of masked sequences.
2. **Heuristic Hangman Solver** – A light-weight complement using entropy and suffix cues to guess words under limited attempts.

Most of the work focuses on understanding and tuning the transformer—how it learns patterns in character sequences—while the Hangman solver demonstrates a practical use of those insights.

## 🧠 Key Learnings

- Visualized multi-head **self-attention** to inspect character dependencies.
- Designed a **character tokenizer** with learnable positional embeddings.
- Trained on a **3 GB masked corpus** with mixed-precision and gradient accumulation.
- Analyzed **loss curves**, **accuracy**, and **perplexity** to fine-tune hyperparameters.
- Explored **model variations** (layer depth, head count).
- Applied **learning-rate warmup**, **cosine decay**, **weight decay**, and **gradient clipping**.

## 📂 Repository Structure

```
├── assets/
│   └── images/                  # Screenshots and visual aids
├── final.ipynb                  # Final notebook for MLM
├── hangman final.ipynb          # Hangman solver walkthrough
├── words_250000_train.txt       # Training word list
├── Hangman Solver final.docx    # Strategy document
└── README.md
```

## 📊 Performance Metrics

| Metric                                | Value   |
| ------------------------------------- | ------- |
| MLM Train Loss (Epoch 1)              | 0.0169  |
| MLM Val Loss (Epoch 1)                | 0.0164  |
| Masked-Character Accuracy             | 63.17%  |
| Overall Solver Success Rate           | 69.8%   |
| Practice Success Rate (100K runs)     | ~71.1%  |

### Training & Evaluation Curves

<div align="center">
  <img src="assets/images/Screenshot 2025-03-18 062644.png" alt="Train vs Val Loss" width="600"/>
</div>

<div align="center">
  <img src="assets/images/Screenshot 2025-03-17 122909.png" alt="Accuracy Progression" width="600"/>
</div>

<div align="center">
  <img src="assets/images/Screenshot 2025-03-18 105609.png" alt="Practice Success Rate" width="600"/>
</div>

## 📥 Download the Repo

The repository is packaged and ready for download:

- **ZIP Archive**: [Download ZIP](sandbox:/mnt/data/hangman-transformers.zip)

---

## 📄 License

MIT License. See [LICENSE](LICENSE) for details.
