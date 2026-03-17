#  Spatio-Temporal Climate Prediction using GNN + LSTM

##  Overview

This project implements a **Spatio-Temporal Deep Learning Model** to predict climate variables using:

*  Temperature (tmp)
*  Precipitation (pre)
*  Vapor Pressure (vap)

The model combines:

* **Graph Convolutional Networks (GCN)** → for spatial learning
* **LSTM (Long Short-Term Memory)** → for temporal learning

📍 The system models **real-world climate behavior**, where nearby regions influence each other over time.

---

## 🎯 Problem Statement

Traditional models fail in climate prediction because:

❌ Ignore spatial relationships (locations treated independently)
❌ Cannot model long-term temporal dependencies effectively
❌ Assume linear relationships
❌ Poor handling of complex climate dynamics

 Climate systems are inherently **spatio-temporal and non-linear**, requiring advanced architectures.

---

##  Proposed Solution

We design a **Hybrid GNN + LSTM Model**:

### 🔗 Spatial Learning (GCN)

* Each grid point = **Node**
* Neighboring regions = **Edges**
* Captures **geographical dependencies**

### ⏳ Temporal Learning (LSTM)

* Processes sequences of climate data
* Learns:

  * Seasonal trends
  * Temporal dependencies

### 🧠 Combined Pipeline

```
Climate Data → Graph Construction → GCN → LSTM → Prediction
```

---

## 📊 Dataset

### 📦 Source

* CRU TS Climate Dataset (NetCDF format)

### 🌍 Region Selected

* Latitude: **33° to 35°**
* Longitude: **74° to 76°**

### 🧾 Features Used

* Temperature (tmp)
* Precipitation (pre)
* Vapor Pressure (vap)

---

## 🛠️ Data Processing Pipeline

### 1️⃣ Data Extraction

* Loaded using **xarray**
* Selected specific geographic region

### 2️⃣ Alignment

* All variables aligned across time and space

### 3️⃣ Conversion to DataFrame

* Flattened into tabular format

### 4️⃣ Tensor Formation

Data reshaped into:

```
(T, N, F)

T = Time Steps  
N = Number of Nodes (Locations)  
F = Features (3)
```

---

## 🔗 Graph Construction

* Nodes represent geographic grid points
* Edges created based on **adjacency rule**:

✔ Connected if:

* Same latitude, longitude difference = 0.5
* Same longitude, latitude difference = 0.5

 This forms a **grid-based spatial graph**

---

## 🧠 Model Architecture

### 🔹 GCN Layers

* 3 Graph Convolution Layers
* Capture spatial relationships

### 🔹 LSTM Layer

* Input: Flattened GCN output across nodes
* Learns temporal patterns

### 🔹 Fully Connected Layer

* Outputs predictions for all nodes and features

---

## ⚙️ Training Details

* Loss Function: **Smooth L1 Loss**
* Optimizer: **Adam**
* Sequence Length: **24 time steps**
* Train/Test Split: **80/20**

---

## 📈 Evaluation Metrics

* **RMSE (Root Mean Squared Error)**

---

## 📊 Results & Performance

### 📈 RMSE Scores

| Feature           | RMSE       |
| ----------------- | ---------- |
|     Temperature   | ~1.4 – 1.6 |
|     Precipitation | ~50 – 55   |
|    Vapor Pressure | ~1.1 – 1.3 |

---

### 📌 Interpretation

* ✅ Temperature predictions are **highly accurate**
* ⚠️ Precipitation is harder due to:

  * High variability
  * Sudden spikes
* ✅ Vapor pressure shows **stable predictions**

---

### 🧠 Key Insights

✔ GCN successfully captures **spatial dependencies**
✔ LSTM learns **temporal trends & seasonality**
✔ Combined model handles **complex climate dynamics**

---

## 📉 Visualization

The project includes:

* 📈 Time-series plots (Actual vs Predicted)
* 🌍 Spatial heatmaps (Temperature distribution)

---

## 🔍 Comparison with Traditional Models

| Model             | Limitation                   |
| ----------------- | ---------------------------- |
| Linear Regression | No spatial/temporal modeling |
| ARIMA             | Only temporal, no spatial    |
| LSTM only         | Ignores spatial relations    |
| ✅ GNN + LSTM    | Captures both                |

---

## 🚀 Key Features

✅ Spatio-temporal modeling
✅ Graph-based learning
✅ Multi-variable prediction
✅ Real-world dataset
✅ End-to-end pipeline
✅ Visualization included

---

## 📁 Project Structure

```
├── main.ipynb          # Complete pipeline
├── data/               # Climate dataset (NetCDF)
├── models/             # Saved model (.pth)
├── scaler.pkl          # Data scaler
├── requirements.txt
└── README.md
```

---

## 🛠️ How to Run

### 1️⃣ Clone Repository

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

### 2️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Run Notebook

```bash
jupyter notebook main.ipynb
```

---

## 💾 Model Saving

* Model saved as: `gnn_lstm_model.pth`
* Scaler saved as: `scaler.pkl`

---

## 👨‍💻 Author

**Umer Rafiq**

* 🎓 BTech CSE Student

---

## ⭐ Why This Project Matters

This project demonstrates how **modern AI (GNN + LSTM)** can solve problems that traditional models cannot, especially in **complex, real-world systems like climate prediction**.


---
