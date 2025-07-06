
# Adaptive Variational Neural Network for Singularly Perturbed Problems

This repository contains the research work and implementation related to the paper:

**"Adaptive Variational Neural Network for Singularly Perturbed Problems with Continuous and Discontinuous Boundary States"**

## 📄 Abstract

This study proposes an adaptive deep learning framework—**Adaptive Variational Neural Network (VarNet)**—to solve 1D singularly perturbed differential equations (SPDEs), especially those with sharp boundary or interior layers due to small perturbation parameters (𝜖). Traditional numerical methods like FEM require fine-tuned meshes in regions of rapid variation, making them computationally expensive.

To overcome this, VarNet employs:
- A **variational (weak-form) loss function** inspired by Finite Element Methods.
- An **adaptive sampling strategy**, concentrating training points in regions with steep solution gradients.
- A standard **multi-layer perceptron (MLP)** trained in supervised mode using FEM-generated reference solutions.

The result is a smooth, differentiable approximation of the solution that closely matches FEM results, even for problems with discontinuous source terms.

## 🚀 Key Contributions

- **Physics-guided Learning:** Uses FEM-generated weak form data to guide training.
- **Adaptive Sampling:** Efficiently targets boundary/interior layers by adjusting input density using σ = 2𝜖ln(n).
- **Robustness:** Handles both continuous and piecewise-discontinuous source terms.
- **Training Efficiency:** Achieves target accuracy (∼10⁻⁵) with significantly fewer data points and epochs.
- **Generalizability:** Offers insights for extending to higher-dimensional PDEs and unsupervised PINNs.

## 🧠 Method Overview

- **Network:** Fully-connected MLP with tanh activation (3 hidden layers).
- **Loss Function:** Mean Squared Error (MSE) against FEM output.
- **Training Data:** Adaptively distributed across the domain [0, 1] based on 𝜖.
- **Optimization:** Adam optimizer with early stopping based on error threshold.

## 📊 Results

| Test Case | Activation | Epochs to Converge | Accuracy Achieved |
|-----------|------------|--------------------|--------------------|
| Smooth Source Term | tanh | ~376 | ≤ 1e-5 |
| Discontinuous Source | tanh | ~1774 | ≤ 1e-5 |



