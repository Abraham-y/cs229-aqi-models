# Predicting Air Quality in Californian Counties

**CS229 Final Project | Stanford University**  
Abraham Yeung ([ayeung16](mailto:ayeung16@stanford.edu))  
Yashas Mattur ([ykmattur](mailto:ykmattur@stanford.edu))

---

## Overview

Air quality forecasting is vital for public health and disaster preparedness, especially in wildfire-prone California. In this project, we predict daily AQI (Air Quality Index) values at the county level using 10 years of EPA data and deep learning models that capture both spatial and temporal patterns. We design hybrid architectures combining **GNNs, CNNs, and LSTMs**, with novel attention mechanisms to model interactions across counties and time.

---

## Key Contributions

- **LSTM models** for capturing AQI temporal dependencies
- **Graph Neural Network embeddings** using k-nearest neighbor graphs across counties
- **Attention mechanisms**:
  - County-neighbor attention for spatial focus
  - Hidden-state attention for time-series emphasis
- **Genetic Algorithm** for hyperparameter tuning across LSTM/GNN models
- Ensemble methods and regularization (dropout, EMA, early stopping) to reduce overfitting

---

## Results

We evaluated models on **~500,000 samples** across 52 counties with RMSE and MAE:

| Model | RMSE |
|-------|------|
| Baseline (persistent) | 17.77 |
| Random Forest | ~15.6 |
| XGBoost / CatBoost | ~15.3 |
| LSTM + County Embeddings | 14.16 |
| **LSTM + CNN/Attention** | **14.08** |
| **LSTM + GNN/Neighbor Attention** | **14.10** |

**CNN and GNN spatial embeddings** improved accuracy by capturing pollution propagation patterns.  
**County-neighbor attention** improved interpretability and helped detect influential regions.

---

## Dataset

- **2015–2024 daily AQI data** from EPA across 52 California counties
- Features: AQI, PM2.5, county metadata, coordinates
- Preprocessing: Outlier removal (IQR), Fourier seasonal transforms, k-NN graph construction

---

## Future Work

- Incorporating **meteorological and satellite** data
- Training with **Transformers** or **masked autoencoders**
- Real-time sensor integration and **uncertainty estimation**
- Weighted loss functions for rare AQI spikes

---

## Project Structure

```
aqi-california-cs229/
├── notebook.ipynb               
├── CS_229_Project_Final_Report.pdf
├── README.md                    
```

---

## Acknowledgments

This project was completed for **CS229: Machine Learning** at Stanford University under supervision of course staff. Special thanks to the EPA for open AQI datasets.
