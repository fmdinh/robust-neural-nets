# Adversarial Attacks on Deep Neural Networks

## Context

Recent work in machine learning has shown that even state-of-the-art deep neural networks are vulnerable to **adversarial examples**.

These are carefully crafted inputs that are:

- Almost indistinguishable from natural data
- Yet systematically misclassified by the model
- A serious security risk in applications such as malware detection and image classification

---

## Adversarial Examples

Small, imperceptible modifications to input data can:

- Fool a trained classifier
- Preserve visual similarity for humans
- Break model robustness assumptions

Example:  
A malicious file can be slightly modified so that a model predicts it as benign and fails to detect it.

---

## Attack Methods

This project studies three main adversarial attack strategies:

### 1. Fast Gradient Sign Method (FGSM)

FGSM generates adversarial examples by perturbing inputs in the direction of the gradient sign:

- Uses the gradient of the loss w.r.t. input
- Applies a constrained L∞ perturbation
- Controls perturbation strength via ε

Two variants:
- Standard FGSM
- Partial FGSM (only perturbing image boundaries)

---

### 2. Projected Gradient Descent (PGD)

An iterative extension of FGSM:

- Repeated small gradient steps
- Projection back into ε-ball constraint
- Stronger and more robust adversarial attacks

---

### 3. Black-box Attacks

Assumes **no access to model internals**.

Three settings:

- Full probability outputs available
- Only top-k class probabilities available (k = 5)
- Only ranked outputs available

Gradient estimation is performed using **NES (Natural Evolution Strategies)**.

## 📊 Key Observations

- FGSM significantly reduces model accuracy even under small ε
- Partial FGSM (boundary-only perturbation) is less aggressive but still effective
- PGD produces stronger adversarial examples than FGSM
- Black-box attacks remain effective even with limited model access

---

## 🧠 Insight

Adversarial vulnerability is not due to noise, but to **structural weaknesses in decision boundaries of deep networks**, which can be exploited even under strict constraints.
