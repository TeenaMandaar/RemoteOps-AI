# 🕵️‍♀️ RemoteOps AI (Remote Work Anomaly Detection)

**A Deep Learning system that finds Burnout and Slacking in remote teams—without spying on screens.**

---

### ❓ The Problem
Remote managers have a "Trust Gap." They don't know if employees are working too hard (**Burnout**) or hardly working (**Quiet Quitting**).

Most companies solve this with invasive screen recording. **I wanted to solve it with Math.**

### 💡 The Solution
This project analyzes **digital footprints** (Work hours, Jira tickets, Git commits) to find anomalies ethically and by not ethically .

It uses two AI models working together:

**1. The Watcher (Behavioral Analysis)**
* **What it does:** Looks at *how* someone works (Hours, Lines of code).
* **The AI:** A **Deep Autoencoder** (Neural Network).
* **The Logic:** It learns what a "Normal" day looks like. If someone works 16 hours or closes 0 tickets, the math flags it as an "Anomaly."

**2. The Auditor (Truth Verification)**
* **What it does:** Checks if the employee is telling the truth.
* **The AI:** **SBERT (NLP Transformer)**.
* **The Logic:** It compares **Jira Tickets** ("I fixed the API") vs. **Git Commits** ("Updated Readme").
    * Match? ✅ Verified.
    * Mismatch? 🚨 Flagged.

---

### 🥊 The Experiment: Simple ML vs. Deep Learning
I didn't just use Deep Learning because it's cool. I proved it was necessary.

1.  **I tried a Simple Model (Isolation Forest):** It only caught the obvious outliers (people working 20 hours/day).
2.  **I tried the Deep Autoencoder:** It caught the **hidden patterns**—like someone working normal hours but producing zero code.


**Winner:** Deep Learning.

While the Isolation Forest only flagged "extreme" numbers, the Deep Learning model found the **hidden patterns** (like low-effort slackers).
Crucially, by combining the Autoencoder with NLP, the system provided a **reason** for every flag (e.g., *"Mismatch between Code and Logs"*). This solved the "Black Box" problem, whereas the simple model just gave a generic alert without context.

---

### 📊 The Final Output
The system generates a **Risk Report** classifying every employee:

| Status | Meaning |
| :--- | :--- |
| 🟢 **Safe** | Normal work patterns + Verified Code. |
| 🟠 **Burnout Risk** | Overworking (Anomaly) + Verified Code. |
| 🔴 **Slacking/Lying** | Low Output (Anomaly) + Mismatched Logs. |

---

### 💻 How to Run (Easiest Way)
This project uses Deep Learning, so it runs best on **Google Colab** (Free GPU).

1.  **Download** the `.ipynb` file from this repository.
2.  **Upload** it to [Google Colab](https://colab.research.google.com/).
3.  **Click "Run All"**.

### 🛠️ Tech Stack
* **Language:** Python
* **Deep Learning:** TensorFlow / Keras
* **NLP:** Sentence-Transformers (HuggingFace)
* **Data:** Pandas, NumPy, Scikit-Learn
* **Viz:** Seaborn, Matplotlib

**Developed by Teena**