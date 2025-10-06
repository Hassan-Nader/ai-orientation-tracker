# Model Comparison and Selection

This document summarizes the comparison between different neural network architectures explored for 3D orientation prediction using IMU data. The goal was to identify the most accurate, efficient, and stable model for real-time orientation tracking.

---

## 1. Overview of Tested Models

| Model | Type | Key Feature | Typical Use Case |
|-------|------|--------------|------------------|
| FFN | Feedforward Neural Network | Learns static relationships | Baseline reference |
| CNN | Convolutional Neural Network | Extracts local spatial patterns | Pattern recognition |
| LSTM | Long Short-Term Memory | Captures long-term temporal dependencies | Time-series data |
| GRU | Gated Recurrent Unit | Simplified recurrent structure | Fast sequential learning |

---

## 2. Evaluation Setup

- **Training Data:** Sequential IMU readings normalized via Min-Max scaling.  
- **Validation Strategy:** Sequential split (80-10-10).  
- **Optimization:** Bayesian optimization for hyperparameter tuning (learning rate, dropout, hidden units).  
- **Metrics:** RMSE, MAE, R².  
- **Hardware:** Standard GPU environment; future work includes supercomputer acceleration for faster Bayesian search.  

---

## 3. Results Summary

| Model | RMSE ↓ | MAE ↓ | R² ↑ | Training Time | Comments |
|--------|---------|-------|------|----------------|-----------|
| FFN | 0.041 | 0.035 | 0.981 | Fast | Lacks temporal learning |
| CNN | 0.037 | 0.031 | 0.987 | Moderate | Strong feature extraction, weak temporal behavior |
| GRU | 0.026 | 0.022 | 0.995 | Moderate | Balanced performance and efficiency |
| **LSTM** | **0.021** | **0.017** | **0.9997** | Slightly longer | **Best overall temporal modeling** |

*(Values shown are representative of relative performance trends.)*

---

## 4. Key Observations

- **LSTM** achieved the best trade-off between accuracy and stability across multiple sequences.  
- **GRU** provided competitive results with shorter training time, making it suitable for real-time applications.  
- **CNN** captured useful spatial correlations but lacked sequence understanding for dynamic motion.  
- **FFN** served as a good baseline but could not model temporal dependencies.

---

## 5. Final Model Choice

The **LSTM** model was selected as the final architecture for deployment due to its superior temporal learning capability and robustness under noisy sensor conditions.  
It was further fine-tuned through **Bayesian optimization**, achieving near-real-time performance with minimal error drift.

---

## 6. Future Work

- Explore **Transformer-based** architectures for enhanced temporal pattern recognition.  
- Utilize **supercomputing resources** to accelerate training and Bayesian hyperparameter tuning.  
- Extend evaluation to multi-IMU configurations for full 6DOF tracking.  
