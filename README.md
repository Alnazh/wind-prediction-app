# 💨 WindPred — Prediksi Kecepatan Angin BMKG Jawa Barat

**Tugas UTS Praktikum Kecerdasan Buatan — Semester 4 (Genap) 2025/2026**

> Analisis komparatif 5 algoritma machine learning untuk prediksi kecepatan angin rata-rata harian (FF_AVG) berbasis data observasi BMKG Stasiun Klimatologi Jawa Barat.

---

## 👤 Identitas

| | |
|---|---|
| **Nama** | [ Nama Mahasiswa ] |
| **NIM** | [ NIM ] |
| **Program Studi** | Teknik Informatika |
| **Mata Kuliah** | Praktikum Kecerdasan Buatan |

---

## 📊 Dataset

- **Sumber:** Open Data BMKG — [dataonline.bmkg.go.id](https://dataonline.bmkg.go.id)
- **Stasiun:** Klimatologi Jawa Barat (ID WMO: 96753, 207 mdpl)
- **Rentang:** Mei 2024 – Mei 2026
- **Target Variable:** `FF_AVG` (kecepatan angin rata-rata harian, m/s)
- **Fitur Input:** TN, TX, TAVG, RH_AVG, RR, SS, FF_X, DDD_X, day_of_year, month, FF_AVG_lag1, FF_AVG_lag7, FF_AVG_roll7, time_index

---

## 🤖 Algoritma & Hasil

| Algoritma | Tipe | MAE ↓ | RMSE ↓ | R² ↑ | Evaluasi |
|---|---|---|---|---|---|
| Linear Regression | Supervised Regression | 0.6724 | 0.8685 | -0.1851 | Perlu Tuning |
| **ANN (TensorFlow)** ⭐ | Supervised Regression | **0.6065** | **0.7864** | **0.0284** | **Terbaik** |
| RNN/LSTM | Supervised Sequential | 0.6367 | 0.8318 | -0.0758 | Perlu Tuning |
| Backpropagation (NumPy) | Supervised Regression | 0.6307 | 0.7895 | 0.0207 | Normal |
| K-Means Clustering | Unsupervised | — | — | Silhouette: 0.3941 (K=3) | — |

> Model terbaik: **ANN** berdasarkan MAE, RMSE, dan R² tertinggi.  
> K-Means menghasilkan K=3 optimal (Angin Tenang, Angin Ringan, Angin Sedang) berdasarkan Silhouette Score — data Stasiun Klimatologi Jawa Barat tidak memiliki cluster angin kencang yang signifikan secara statistik.

---

## 🛠 Cara Instalasi & Menjalankan

```bash
# 1. Clone repository
git clone https://github.com/[username]/windpred.git
cd windpred

# 2. Install dependensi
pip install -r requirements.txt

# 3. Jalankan training (wajib sekali sebelum run app)
python train.py

# 4. Jalankan aplikasi
python -m flask --app app/app.py run

# Atau menggunakan gunicorn (production)
gunicorn app.app:app
```

Aplikasi berjalan di: `http://localhost:5000`

---

## 📁 Struktur Project

```
windpred/
├── data/
│   ├── bmkg_merged.csv          # Data mentah hasil merge
│   ├── bmkg_preprocessed.csv    # Data setelah feature engineering
│   └── clustered_data.csv       # Hasil K-Means clustering
├── models/
│   ├── linear_regression.pkl    # Model Linear Regression
│   ├── ann_model.keras/.h5      # Model ANN (TensorFlow)
│   ├── rnn_lstm_model.keras/.h5 # Model RNN/LSTM
│   ├── backprop_weights.npz     # Bobot Backpropagation manual
│   ├── kmeans_model.pkl         # Model K-Means
│   ├── scaler_X.pkl / scaler_y.pkl / scaler_kmeans.pkl
│   ├── model_metrics.json       # Metrik semua model
│   ├── kmeans_metrics.json      # Metrik & elbow K-Means
│   └── lstm_seq_buffer.json     # Buffer sekuens LSTM
├── notebooks/
│   └── windpred_eda_training.ipynb
├── app/
│   ├── static/                  # CSS, JS
│   ├── templates/               # HTML Jinja2
│   └── app.py                   # Flask application
├── train.py                     # Script training semua model
├── requirements.txt
├── Procfile
└── README.md
```

---

## 🔗 Links

| | |
|---|---|
| **Demo Aplikasi** | [ URL deploy ] |
| **Laporan PDF** | [ Link Google Classroom ] |
| **Video YouTube** | [ Link YouTube ] |

---

## 📄 Lisensi Dataset

Data bersumber dari **Open Data BMKG** yang tersedia secara bebas untuk keperluan akademik dan penelitian. Lihat: [bmkg.go.id](https://www.bmkg.go.id)
