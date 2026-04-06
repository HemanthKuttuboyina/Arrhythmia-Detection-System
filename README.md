# Smart ECG Analysis System

Welcome to the **Smart ECG Analysis System**! This is an AI-powered healthcare web application that analyzes ECG (electrocardiogram) signals to detect heart rhythm irregularities (arrhythmias). 

Not only does the system provide an AI prediction (Normal/Abnormal), but it also explains *why* the decision was made using **SHAP (Explainable AI)** and secures the result using **Blockchain technology (Web3)**.

---

## 🌟 Key Features

1. **AI Arrhythmia Detection**: Uses a trained **HQCNN (High-Quality Convolutional Neural Network)** to analyze patient heartbeat segments.
2. **Explainable AI (XAI)**: Instead of a "black box" result, the application visualizes feature importance (Heart Rate, SDNN, RMSSD, Mean R-R) using **SHAP waterfall and bar plots**.
3. **Blockchain Security**: Digitally seals each prediction with a **SHA-256 hash** and stores it on a simulated Ethereum ledger using Web3. Ensures that medical records are tamper-proof.
4. **Data Validation**: Computes a "Quality Score" on the uploaded signal to prevent analysis of noisy or flatlined data.
5. **Django Dashboard**: A fully featured web application with user registration, login, profile management, and result history.

---

## 💻 Prerequisites

Before running the project, ensure you have the following installed:
* **Python 3.8+** (We recommend Python 3.9 or 3.10)
* **Pip** (Python package installer)
* **Git** (Optional)

---

## 🛠️ Installation & Setup Guide

### 1. Navigate to the project directory
Open your terminal (or Command Prompt / PowerShell) and navigate inside the main project directory:
```bash
cd path\to\arrhythmia-detection-master\arrhythmia-detection-master
```

### 2. Create and Activate a Virtual Environment (Recommended)
This keeps the project's dependencies isolated from your main system.
```bash
# Create the virtual environment
python -m venv venv

# Activate it (Windows)
venv\Scripts\activate

# Activate it (Mac/Linux)
source venv/bin/activate
```

### 3. Install Dependencies
Install all the necessary Python libraries required to run the Web server, AI models, and Blockchain simulations.
Run the following command:
```bash
pip install django numpy scipy matplotlib pandas scikit-learn shap wfdb python-dotenv web3 eth-tester
```
*(Note: `wfdb` is required to parse clinical `.dat`/`.hea` formats, and `eth-tester` is needed to simulate the local Web3 Ethereum blockchain.)*

### 4. Apply Database Migrations
Set up the SQLite database to hold user accounts, ECG test summaries, and Blockchain hashes.
```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Create an Admin Account (Optional)
If you'd like to access the Django built-in Administration panel, create a superuser:
```bash
python manage.py createsuperuser
```
Follow the prompt instructions to enter a username, email, and password.

---

## 🚀 How to Run the Project

1. **Start the Web Server:**
   Ensure your virtual environment is still activated and run:
   ```bash
   python manage.py runserver
   ```

2. **Open the Dashboard:**
   Open your preferred web browser and navigate to:  
   **➡️ [http://127.0.0.1:8000](http://127.0.0.1:8000)**

3. **Testing the Application:**
   * **Register/Login:** Create a new user account through the web interface.
   * **Upload an ECG:** Navigate to the analysis/upload page. You will be prompted to upload specific ECG files (`.dat`, `.hea`, and `.atr`). 
   * **Sample Data:** You can use the standard MIT-BIH test files provided in the `mit_bih/` directory. (e.g., upload `100.dat` and `100.hea`).
   * **View Results:** The system will process the file, invoke the HQCNN model, generate SHAP visuals, log the transaction to the simulated blockchain, and display a comprehensive medical report!

---

## 📂 Project Structure Overview
* `ecg/`: Core logic for biomedical signal processing, UI views, and file uploads.
* `mlmodel/`: Houses the pre-trained AI models (`ecg_model.pkl`) and `shap_explain.py` for interpretability.
* `blockchain/`: Web3 logic for hashing and securing prediction data onto a simulated ledger.
* `dashboard/`: Controls the frontend web interface users interact with.
* `quality/`: Implements the "Quality Score" screening of incoming ECG uploads.
* `modern_auth/`: Handles secure authentication and permissions.

For a deeper technical explanation on how each block communicates, refer to `project_explanation.md` and `technical_project_explanation.md`.
