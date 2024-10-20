# 🚨 Cloud logs Alert Classification with LSTM 🚨

![image](https://github.com/user-attachments/assets/0f03887d-7383-414d-83bd-c814d523a01b)


## 📄 Overview
This repository contains a solution to classify security alerts into three sequential categories: **Use Case**, **Alert Source Entity**, and **Alert Target Entity**. The classification process follows a hierarchical structure where each alert is first classified by its **Use Case**, followed by its **Source Entity**, and finally its **Target Entity**.

The project uses machine learning and an LSTM-based approach to extract features from the alert data, process them, and predict the correct classification for each category.

---

## 🎯 Purpose
In many organizations, security alerts are generated continuously by various systems. The goal of this project is to help in **automating the alert classification process** based on specific attributes in the data, such as:

1. **Use Case**: Categorizing the core issue of the alert.
2. **Source Entity**: Identifying the origin of the alert (e.g., application, host, identity).
3. **Target Entity**: Determining what part of the system the alert is targeting.

By classifying the alerts automatically, the system can save analysts' time and ensure quicker response actions.

---

## ⚙️ How It Works

### Classification Categories:
1. **Use Case** 🛡️:
    - IAM / Entitlement Issues
    - Compliance / Hygiene / Security Issues
    - Vulnerability Management
    - Known Malicious Artifacts
    - Key Management Issues

2. **Alert Source Entity** 🏗️:
    - Application / Process / File
    - Host
    - Identity
    - Resource Storage (e.g., S3)
    - Kubernetes, Lambda, and more

3. **Alert Target Entity** 🎯:
    - Host
    - Network Connection
    - Resource Storage
    - API
    - Security Monitoring, and more

---

## 🧠 Technical Details

### 🏗️ Model Structure:
The model uses **LSTM (Long Short-Term Memory)** layers to process textual alert data, combined with dense layers for multi-label classification (for the **Use Case**) and multi-class classification (for **Source Entity** and **Target Entity**).

Key technologies include:
- **Pandas & NumPy** for data manipulation.
- **TensorFlow/Keras** for building the LSTM model.
- **Kerastuner** for hyperparameter optimization.
- **LabelEncoder & Tokenizer** for preprocessing categorical and text data.
- **RandomSearch** to optimize model hyperparameters like LSTM units, embedding dimensions, and learning rates.

### 🛠️ Key Features:
1. **Preprocessing**: Alerts are cleaned, tokenized, and transformed into padded sequences.
2. **Model Training**: Three separate LSTM models are trained for:
   - Multi-label classification for **Use Case**.
   - Multi-class classification for **Source Entity** and **Target Entity**.
3. **Hyperparameter Tuning**: Each model’s hyperparameters are optimized using Random Search.

---

## 📊 Performance
After training and optimizing the models, the following accuracies were achieved:

- **Use Case**: 68.67% ✅
- **Source Entity**: 97.59% 🔥
- **Target Entity**: 72.29% 🛠️

---

## 🚀 How to Use

1. **Clone the Repo**:
   ```bash
   git clone https://github.com/your-repo/alert-classification-lstm.git
   cd alert-classification-lstm
   ```

2. **Install Dependencies**:
   Make sure you have the required libraries installed:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the jupyter notebook**:
   Place your alert dataset in CSV format as `task1.csv` in the root folder.
---

## 📈 Final Results

The results for the holdout dataset are saved in the file `holdout_alerts_results.csv`. This file contains the predicted categories for each alert, along with the model’s confidence probabilities for each classification.

---

## 🤖 Example Classification:
Here is an example of a JSON object you can classify:
```json
{
  "alert_name": "IAM role misconfiguration",
  "description": "User role has insecure permissions",
  "alert_type": "Security",
  "hostname": "server1",
  "instance_id": "i-12345",
  "user_name": "admin",
  "access_key_id": "ABC123XYZ"
}
```

After classification, the model will predict:
- **Use Case**: IAM / Entitlement Issues
- **Source Entity**: Identity
- **Target Entity**: Host

---

## 🏆 Evaluation Metrics
We use **accuracy** to evaluate how well the models perform:
- **Use Case Accuracy**: 68.67% 🔄
- **Source Entity Accuracy**: 97.59% ⚡
- **Target Entity Accuracy**: 72.29% 📡

---
