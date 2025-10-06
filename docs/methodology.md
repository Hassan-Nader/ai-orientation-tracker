# Methodology: A Data-Centric Approach to 3D Orientation Tracking

This project's core is a data science pipeline designed to solve a classical engineering problem: accurate 3D orientation estimation. My primary role centered on architecting and executing the machine learning lifecycle, from data strategy and feature engineering to model deployment, while collaborating with a team on the broader system integration.

---

## 1. Data Strategy & Engineering

**My Contribution:** I designed the entire data collection protocol and preprocessing pipeline to ensure the dataset's statistical robustness and suitability for training.

**Experimental Design:** I defined the systematic sampling strategy to move the robotic arm through its full 3D orientation space, ensuring comprehensive feature coverage and preventing model overfitting to specific motion paths.

**Data Preprocessing Pipeline:** I engineered the preprocessing steps, including:

- **Temporal Alignment:** Developed a method to synchronize dual-IMU data streams using hardware and software triggers.  
- **Noise Reduction:** Implemented and validated signal averaging and shielding techniques to minimize sensor noise, directly improving the signal-to-noise ratio of our training data.  
- **Feature Scaling:** Applied robust normalization to the input features to ensure stable and efficient model convergence.  

---

## 2. Feature Engineering & Representation Learning

**My Contribution:** I engineered the input feature space to enhance the model's ability to learn the underlying physical relationships, moving beyond raw sensor readings.

- **Multi-Sensor Fusion as Features:** The core engineered feature set was the synchronized concatenation of data from two IMUs. This created a 12-dimensional input vector that provided a richer, more spatially diverse representation of the system's state than a single sensor, effectively teaching the model about relative sensor behavior.  
- **Temporal Context Windowing:** For the recurrent models (LSTM/GRU), I structured the input data into sequential time windows, allowing the network to learn from temporal dynamics and dependencies between consecutive sensor readings, crucial for smoothing predictions and mitigating transient noise spikes.  
- **Statistical Feature Exploration:** Experiments with derived features, such as signal magnitudes and rolling statistical moments (mean, variance), were conducted. The finding that raw, synchronized data provided the best performance was a key result of this analysis.  

---

## 3. Model Development & Statistical Learning

**My Contribution:** I led end-to-end model development, from architecture selection to hyperparameter optimization and statistical evaluation.

- **Architecture Comparison:** Implemented and rigorously compared FNN, LSTM, and GRU models. The GRU was selected for its optimal balance of performance and computational efficiency.  
- **Advanced Hyperparameter Tuning:** Employed Bayesian Optimization to navigate the high-dimensional hyperparameter space (e.g., layer neurons, learning rate, batch size), efficiently converging to the optimal configuration.  
- **Robust Validation Framework:** Implemented K-Fold Cross-Validation with custom subset splitting to accurately estimate model generalization despite temporal sensor drift, a key challenge in time-series data.  

---

## 4. Model Evaluation & Inference

**My Contribution:** Established evaluation metrics and validated the model's performance both offline and in real-time inference.

- **Performance Metrics:** Evaluated using RMSE, MAE, and R². Our best model achieved an R² of 0.9997, indicating an almost perfect fit to ground truth.  
- **Real-Time Deployment:** Developed an inference pipeline that ingests live sensor data, applies preprocessing and feature engineering transforms, and executes the trained model to deliver low-latency orientation estimates.  

---

## 5. System Integration & Application

In collaboration with the team, we integrated the ML model into the broader system. My focus was on the data interface and the application of statistical methods to a new problem domain.

- The trained model served as the core of a relative orientation calculator. By applying rotation matrix transformations to the model's outputs, we demonstrated a novel, non-contact method for measuring angles between two mechanical links.  

---

## Conclusion

This project demonstrates the power of a principled data science methodology. By focusing on data quality, strategic feature engineering, rigorous model selection, and robust statistical validation, we developed a system that significantly outperforms traditional analytical approaches.  

Upon completion, the project provides a **cost-efficient 3D orientation tracking solution** applicable to classical fields such as robotics, offering a practical alternative to encoder-based systems. This highlights the potential of machine learning to enhance advanced sensing applications while reducing hardware complexity and cost.
