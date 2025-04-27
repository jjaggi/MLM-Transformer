# Transformer-based Masked Language Model & Hangman Solver

## 🚀 Project Overview

This repo dives into **transformer architectures** applied to a character-level masked language task and pairs it with a strategic Hangman solver:

1. **Transformer-based Masked Language Model (MLM)** – Custom tokenizers, multi-head attention, and positional embeddings trained on millions of masked sequences.  
2. **Heuristic Hangman Solver** – A light-weight complement using entropy and suffix cues to guess words under limited attempts.

Most of the work focuses on understanding and tuning the transformer—how it learns patterns in character sequences—while the Hangman solver demonstrates a practical use of those insights.

## 🧠 Key Learnings

- Visualized multi-head **self-attention** to inspect character dependencies.  
- Designed a **character tokenizer** with learnable positional embeddings.  
- Trained on a **3 GB masked corpus** with mixed-precision and gradient accumulation.  
- Analyzed **loss curves**, **accuracy**, and **perplexity** to fine-tune hyperparameters.  
- Explored **model variations** (layer depth, head count).  
- Applied **learning-rate warmup**, **cosine decay**, **weight decay**, and **gradient clipping**.


## 📊 Performance Metrics

| Metric                                | Value   |
| ------------------------------------- | ------- |
| MLM Train Loss (Epoch 1)              | 0.0169  |
| MLM Val Loss (Epoch 1)                | 0.0164  |
| Masked-Character Accuracy             | 63.17%  |
| Overall Solver Success Rate           | 69.8%   |
| Practice Success Rate (100 K runs)    | ~71.1%  |

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

## 🕹️ Hangman Solver: Data-Driven Strategy

> Core insights and heuristics driving the lightweight Hangman solver :contentReference[oaicite:0]{index=0}&#8203;:contentReference[oaicite:1]{index=1}

### 1. Dataset Analysis
- **Vocabulary Size**: ~250 000 unique words.  
- **Word Length Distribution**:  
  - Min = 1, Max = 29 (buffered to 32)  
  - Mean = 9.3, Median = 9  

### 2. Strategic Inferences
1. **Early Vowel Prioritization**  
   - Guess `e`, `a`, `i` first; adapt when vowel ratio < 0.3 or > 0.6.  
2. **Disjoint Training/Test Sets**  
   - Avoid words seen during model training; always pick the next best candidate.  
3. **Positional Letter Frequencies**  
   - Build heatmaps per length; use cosine similarity to focus high-certainty positions.  
4. **Maximize Information Gain**  
   - Pick letters that eliminate the largest remaining set (entropy-based).  
5. **Suffix Exploitation**  
   - Leverage common endings (`-ing`, `-ion`, `-ous`, `-ted`, `-ate`) for longer words.

### 3. What *Not* to Use
- **Global Frequency Fallback**: Lacks context accuracy.  
- **Basic Length-Based Frequency** (±2 letters): Marginal gain.  
- **N-Gram Heuristics**: Zero-probability issues on unseen sequences.  
- **Hard-Coded Rules**: Overfitting to vowel ratios; limited flexibility.

### 4. Alternative Approaches Explored
- **Bayesian & Probabilistic Models**: Good on train, poor on disjoint test.  
- **Reinforcement Learning**: Reward structure but no convergence in time.  
- **Char-Based MLM Constraints**: Masked corpus (~3 GB), negative constraints on top 11 letters.

### 5. Final Solver Design
- **Heuristic + MLM Hybrid**  
  - Start with letter-frequency and entropy heuristics.  
  - Use the trained character-level MLM for final guess steps.  
- **Overall Success Rate**: ~69.8% on 1 000 official games.

### 6. Acknowledgments
Special thanks to my brother for GPU training support. Valuable lessons in heuristic modeling and transformer insights.

## 📄 License

MIT License. See [LICENSE](LICENSE) for details.
