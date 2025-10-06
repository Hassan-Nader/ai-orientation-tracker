**Employing an Artificial Intelligence Filter to Predict Orientation of Objects in 3D Space**

📘 **Overview**

Explores AI-based orientation tracking using IMU data.
Compares multiple neural network architectures (FFN, CNN, RNN–LSTM, GRU) and applies Bayesian optimization for hyperparameter tuning.
Validated through hardware testing to demonstrate reliable 3DOF motion sensing.

🎯 **Objectives**

Predict object orientation (3DOF) from IMU readings.

Identify the most effective NN architecture for sequential IMU data.

Apply Bayesian optimization to fine-tune hyperparameters.

Validate model performance through physical testing.

🧩 **Methodology******

Data collected from dual IMU setup (accelerometer, gyroscope, magnetometer).

Sequential training/validation splitting.

Models trained and compared on normalized sensor data.

LSTM selected for best temporal performance.

Hardware validation performed using microcontroller-controlled mechanism.

(Detailed docs available in /docs/ folder.)

⚙️ **Neural Network Comparison**
Model	     Type	            Key Feature	                Performance Summary
FFN	    Feedforward	    Baseline dense network	    Moderate accuracy
CNN	    Convolutional	  Spatial pattern learning	  Improved generalization
GRU	    Recurrent	      Simplified gating	          Efficient but less stable in Real Time
LSTM	  Recurrent	      Strong sequence memory	    Best performance

🔍 **Bayesian Optimization**

Used to tune learning rate, batch size, dropout rate, and neurons per layer.

Search space explored using probabilistic optimization for minimal validation loss.

📊 **Results**

LSTM achieved highest accuracy and lowest RMSE on validation and test data.

Predicted orientation closely matched measured hardware response.

Visuals and plots available in /results/.

### 🧾 Repository Structure

- **docs/** → Documentation (methodology, model comparison)  
- **results/** → Visuals, performance summaries  
- **media/** → Diagrams, demo GIFs  
- **README.md** → Project summary (this file)


**⚠️ Research Notice**

Due to ongoing research and pending publication, the dataset and source code are not publicly shared.
Summaries, figures, and performance results are provided for reference only.

**📚 Future Work**

Extend to real-time orientation tracking for multi-link systems.

Integrate transformer-based sequence models.

Publish full dataset and code post–paper acceptance.

Use of a supercomputer could speed up model training and allow faster hyperparameter tuning with Bayesian optimization
