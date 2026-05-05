# Context-Aware Emotion Recognition via Multi-Modal VLMs
Comparative analysis of Qwen2.5-VL, Llama 3.2-Vision, and LLaVA-v1.6 on the EMOTIC dataset, exploring the impact of environmental context on affective computing.

## 📌 Project Overview
This project explores the critical role of environmental context in affective computing. By evaluating state-of-the-art Vision Language Models (VLMs) on the **EMOTIC dataset**, we analyze how model predictions shift when restricted to facial morphology versus the complete scene. 

The study focuses on 26 distinct emotion categories, categorizing them based on their dependency on situational context.

### 🤖 Models Evaluated
* **Qwen2.5-VL-3B-Instruct**: Demonstrated the highest robustness to context removal.
* **Llama-3.2-11B-Vision**: Showed a high dependency on global scene semantics.
* **LLaVA-v1.6-Mistral-7b-hf**: Balanced performance with a focus on social storytelling.

---

## 📊 Key Findings
* **The Proximity Paradox**: Without context, models often misclassify high-arousal social proximity (e.g., *Affection*) as conflict or avoidance (*Aversion*).
* **Semantic Anchoring**: For relational emotions like *Confidence* and *Anticipation*, the environment provides a "logic anchor" that overrides ambiguous facial features.
* **Environmental Bias**: In some cases, a vibrant background can act as "noise," causing models to predict *Happiness* based on the scene while ignoring *Pain* or *Sadness* on the face.
* **Architectural Robustness**: Qwen2.5-VL’s dynamic resolution allows it to maintain feature density in small crops, outperforming larger models like Llama 3.2 in Task 2.

---

## 🛠️ Methodology
The experiment is divided into two primary tasks:

1. **Task 1 (Full Image)**: The model analyzes the original scene to predict one of 26 labels.
2. **Task 2 (Cropped Face)**: The image is cropped to the subject's face using Ground Truth bounding boxes and the PIL library.

### Data Cleaning
Since base VLMs can be "chatty," a regex-based `rigorous_clean` function was implemented to map raw model completions back to the 26 standard EMOTIC categories, ensuring valid classification metrics.

---

## 🚀 Installation & Setup

### Prerequisites
* Python 3.10+
* CUDA-compatible GPU (Recommended: 16GB+ VRAM for Llama 11B)
* Hugging Face Access Token (Required for Llama 3.2 models)

---

## 📈 Results Summary

| Model | Task | Accuracy | F1-Score |
| :--- | :--- | :--- | :--- |
| **Qwen2.5-VL** | Full / Crop | 12.9% / 13.8% | 0.09 / 0.10 |
| **Llama 3.2** | Full / Crop | 7.6% / 4.7% | 0.05 / 0.02 |
| **LLaVA-v1.6** | Full / Crop | 10.3% / 8.6% | 0.07 / 0.06 |

---

## 🎓 Author
**Ravuri Sivaram** *MS in Computer Science, University of South Florida* **Focus:** Building scalable intelligent systems and bridging the gap between technical modeling and business solutions.
