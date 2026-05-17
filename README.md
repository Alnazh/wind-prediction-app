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
- **Stasiun:** Klimatologi Jawa Barat (ID WMO: 96753, 6.50°LS / 106.75°BT, 207 mdpl)
- **Rentang:** 14 Mei 2024 – 12 Mei 2026
- **Total Data:** 729 baris observasi harian
- **Target Variable:** `FF_AVG` (kecepatan angin rata-rata, m/s)

---

## 🤖 Algoritma & Hasil

| Algoritma | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | — | — | — |
| ANN (TensorFlow) | — | — | — |
| RNN/LSTM | — | — | — |
| Backpropagation (NumPy) | — | — | — |
| K-Means Clustering | — | Silhouette: — | — |

> Isi tabel dengan hasil aktual setelah `python train.py`

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
├── data/               # Dataset BMKG (mentah & preprocessed)
├── models/             # File model tersimpan (.pkl, .h5, .npz)
├── notebooks/          # Jupyter Notebook EDA & training
├── app/
│   ├── static/         # CSS, JS, gambar
│   ├── templates/      # Template HTML Jinja2
│   └── app.py          # Flask application
├── train.py            # Script training semua model
├── requirements.txt
├── Procfile
└── README.md
```

---

## 🔗 Links

| | |
|---|---|
| **Demo Aplikasi** | [ URL deploy .my.id ] |
| **Laporan PDF** | [ Link Google Classroom ] |
| **Video YouTube** | [ Link YouTube ] |

---

## 📄 Lisensi Dataset

Data bersumber dari **Open Data BMKG** yang tersedia secara bebas untuk keperluan akademik dan penelitian. Lihat: [bmkg.go.id](https://www.bmkg.go.id)
