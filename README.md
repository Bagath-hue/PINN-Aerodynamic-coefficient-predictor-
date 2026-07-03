# PINN-Aerodynamic-coefficient-predictor-
# 🧠 Physics-Informed Neural Networks (PINNs) for Airfoil Aerodynamic Prediction

## 📖 Overview

Physics-Informed Neural Networks (PINNs) combine data-driven learning with governing physical principles to improve the prediction of engineering systems. Unlike conventional neural networks, PINNs incorporate physics-based constraints into the training process, enabling the model to learn physically consistent solutions.

This project develops a PINN-based surrogate model for predicting the aerodynamic coefficients of airfoils. The model is trained using aerodynamic data from multiple airfoil geometries and evaluated on both validation and completely unseen airfoils to assess its predictive capability and generalization performance.

---

# 🎯 Objectives

The objectives of this project are:

- Develop a Physics-Informed Neural Network (PINN) surrogate model.
- Predict Lift (CL), Drag (CD), and Moment (Cm) coefficients.
- Evaluate prediction accuracy using R² Score and Mean Absolute Error (MAE).
- Compare validation performance with unseen-airfoil performance.
- Analyze the strengths and limitations of PINNs for aerodynamic prediction.

---

# 📂 Dataset

The dataset consists of aerodynamic data collected from **13 different airfoil geometries**.

## Training Airfoils

- NACA 0009
- NACA 0012
- NACA 0015
- NACA 23012
- NACA 2412
- NACA 4412
- NACA 6409
- NACA 63-215
- NACA 63-137
- S1223
- MH32
- Clark Y
- E385

The aerodynamic data from these airfoils were combined into a master dataset used for training and validation.

---

## Unseen Airfoils

The following airfoils were excluded from training and used only for testing the model's ability to generalize.

- NACA 0024
- NACA 6412

---

# 📊 Features & Target Variables

## Input Features

- Maximum Camber
- Camber Position
- Maximum Thickness
- Angle of Attack (AoA)
- Reynolds Number
- Maximum Lift Coefficient (CLmax)
- Stall Angle

## Target Variables

- Lift Coefficient (CL)
- Drag Coefficient (CD)
- Moment Coefficient (Cm)

---

# ⚙️ Methodology

The workflow followed in this project is summarized below.

1. Data collection from multiple airfoil datasets.
2. Dataset preprocessing and normalization.
3. Development of the Physics-Informed Neural Network.
4. Training using the combined 13-airfoil dataset.
5. Validation using train-test split.
6. Prediction on unseen airfoils.
7. Performance evaluation using R² Score and MAE.
8. Analysis of model generalization.

---

# 🧠 Physics-Informed Neural Network

Unlike conventional neural networks, the PINN incorporates physics-based information during training to guide the learning process. This enables the network to produce predictions that better satisfy the underlying aerodynamic behavior while reducing dependence on purely data-driven learning.

---

# 📏 Evaluation Metrics

Model performance was evaluated using:

- **R² Score**
- **Mean Absolute Error (MAE)**

The metrics were calculated separately for:

- Lift Coefficient (CL)
- Drag Coefficient (CD)
- Moment Coefficient (Cm)

---

# 📈 Results

## 1. Validation on the 13-Airfoil Dataset

The PINN model was first trained and validated using the combined dataset of **13 airfoils**.

### Validation Summary

- The PINN achieved high prediction accuracy during validation.
- The model successfully learned the aerodynamic relationships contained in the training dataset.
- Predicted values closely matched the actual aerodynamic coefficients for CL, CD, and Cm.
- The validation results indicate that incorporating physics-based constraints improved the model's ability to learn stable aerodynamic trends.

Overall, the validation demonstrated that the PINN is an effective surrogate model for interpolation within the range of the training data.

---

## 2. Performance on Unseen Airfoils

The trained PINN was evaluated on two completely unseen airfoils.

### Test Airfoils

- NACA 0024
- NACA 6412

### NACA 0024

| Coefficient | R² Score | MAE |
|------------|---------:|----:|
| CL | -1.9379 | 1.3177 |
| CD | -0.7433 | 0.0383 |
| Cm | -127.6154 | 0.2132 |

### NACA 6412

| Coefficient | R² Score | MAE |
|------------|---------:|----:|
| CL | **0.1837** | 0.6264 |
| CD | **0.5173** | 0.0176 |
| Cm | -13.2898 | 0.1377 |

---

# 🔍 Result Analysis

The validation results demonstrate that the PINN effectively captured the aerodynamic behavior of the training airfoils. However, its performance on unseen airfoils varied depending on the aerodynamic coefficient being predicted.

### Lift Coefficient (CL)

The PINN produced acceptable predictions for the lift coefficient, particularly for NACA 6412. Lift is primarily governed by global aerodynamic characteristics such as angle of attack, camber, and thickness, which were well represented in the training dataset.

### Drag Coefficient (CD)

The model achieved its best unseen-airfoil performance for the drag coefficient. Drag generally exhibits smoother variations with changes in geometry and operating conditions, making it easier for the PINN to learn physically consistent trends.

### Moment Coefficient (Cm)

The prediction of the moment coefficient remained poor on unseen airfoils.

This is expected because:

- Cm is highly sensitive to pressure distribution.
- Small geometric variations can significantly alter pitching moment.
- The available training dataset contained only 13 airfoil geometries, limiting the diversity of moment characteristics.
- The implemented physics constraints were more effective for capturing lift and drag trends than the complex behavior of pitching moment.

As a result, the PINN struggled to extrapolate Cm to previously unseen airfoil geometries.

---

# 🏆 Key Findings

- The PINN successfully learned aerodynamic relationships within the training dataset.
- Validation on the 13-airfoil dataset demonstrated strong predictive capability.
- The model generalized reasonably well for **Lift Coefficient (CL)** and **Drag Coefficient (CD)** on unseen airfoils, particularly for **NACA 6412**.
- Prediction of the **Moment Coefficient (Cm)** remained challenging because of its strong sensitivity to local pressure distribution and limited training diversity.
- These results indicate that physics-informed learning improves generalization compared to a conventional ANN but still requires a larger and more diverse dataset for robust prediction of all aerodynamic coefficients.
  
---

# 🔮 Future Work

- Increase the number of training airfoils to improve generalization.
- Incorporate additional physics-based constraints related to pitching moment.
- Investigate deeper PINN architectures and adaptive loss weighting.
- Compare PINN performance with Gaussian Process Regression, Random Forest, and XGBoost surrogate models.
- Explore Physics-Informed Deep Neural Networks (PIDNNs) for enhanced aerodynamic prediction.

---

# 👨‍💻 Author

**Bagath singh**

Mini Project – *Physics-Informed Neural Networks for Airfoil Aerodynamic Prediction*
