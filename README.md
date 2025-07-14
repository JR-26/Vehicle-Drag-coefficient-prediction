# 🚗 Predictive Analysis of Aerodynamic Drag Coefficient Using Neural Networks

## 📌 Abstract

This project presents a real-time, machine-learning-based system to predict the **Average Drag Coefficient (Cd)** of vehicles using a hybrid deep learning and ensemble learning approach. It eliminates the need for computationally intensive CFD simulations by learning patterns from a large parametric design dataset—**DrivAerNet**—and predicting aerodynamic efficiency with high accuracy.

## 🔍 Problem Statement

Traditional aerodynamic simulations using **CFD** and **CAE** are accurate but time- and resource-intensive. This makes rapid design iterations and large-scale studies infeasible. Our aim is to provide a **lightweight, data-driven** alternative for aerodynamic coefficient prediction without compromising accuracy.

## 🧠 ML Solution Overview

We propose a hybrid modeling approach combining:

- 📈 **Gradient Boosting Regressor**
- 🧠 **Deep Neural Networks (Tanh Activation + He Normal Init)**
- 🔁 **Stacking Ensemble Model**

This results in a highly efficient model with:
- ✅ MSE of **0.0002** (best case)
- ⚡ Faster inference than traditional simulations

## 📊 Dataset: [DrivAerNet](https://www.researchgate.net/publication/381470334_DrivAerNet_A_Large-Scale_Multimodal_Car_Dataset_with_Computational_Fluid_Dynamics_Simulations_and_Deep_Learning_Benchmarks)

- ✅ 4000 car designs
- ✅ 26 features (angles, dimensions, aerodynamic shapes)
- ✅ Includes **Average Cd** and **Standard Deviation**

### Key Feature Examples
- `B_Ramp_Angle`, `C_Side_Mirrors_Rotation`, `D_Rear_Window_Inclination`, `A_Car_Length`, `Average Cd`, etc.

## ⚙️ Model Architecture

### 🔸 Preprocessing
- `StandardScaler` for numerical features
- `OneHotEncoder` for categorical features

### 🔸 Neural Network
- Layers: `[Input → 512 (Tanh) → 256 (Tanh) → Dropout(0.3) → Output]`
- Weight Init: **He Normal**
- Optimizer: **Adam**, LR = `0.0003`
- Loss: **MSE**

### 🔸 Boosting + Stacking
- `GradientBoostingRegressor (100 estimators)`
- Final stacked regressor: `GradientBoostingRegressor (50 estimators)`

### 🧪 Performance

| Model                         | MSE         |
|------------------------------|-------------|
| Vanilla Neural Network       | 0.005       |
| ResNet Model                 | 0.0003      |
| Ensemble (only boosting)     | 0.0003      |
| Hybrid (Boosting + Stacking) | **0.0002**  |


