# UTS Machine Learning — Bagas Arief Pratama

- Nama: Bagas Arief Pratama
- NIM: 241011400548
- Kelas: Reg C
- random_state: 48 (2 digit terakhir NIM)

## Isi Repositori

| File | Keterangan |
|---|---|
| `tugas_UTS.ipynb` | Notebook pengerjaan Linear Regression & Logistic Regression |
| `Ads_Data.csv` | Dataset biaya iklan vs penjualan (40 data) |
| `Email_Data.csv` | Dataset klasifikasi email spam (60 data) |
| `README.md` | Dokumentasi repositori ini |

## Cara Menjalankan

1. Pastikan Python 3 dan Jupyter Notebook sudah terinstall
2. Install library yang dibutuhkan:
   `pip install numpy pandas matplotlib scikit-learn`
3. Simpan semua file di folder yang sama
4. Buka `tugas_UTS.ipynb` di Jupyter Notebook atau VS Code
5. Klik Run All untuk menjalankan semua sel
6. Semua output dan grafik akan muncul

Catatan: Bagian bonus menggunakan scikit-learn sesuai izin pada instruksi tugas. Bagian utama mengimplementasikan model dan metrik dengan NumPy dari nol.

## Ringkasan Hasil

### Bagian A — Linear Regression (Ads_Data.csv)

- Persamaan regresi: y = 29.1879 + 8.9897 x BiayaIklan
- Interpretasi: Setiap kenaikan biaya iklan Rp1 juta, penjualan diperkirakan naik ~Rp8.99 juta
- R2 Training: 0.9548
- R2 Testing: 0.9029
- RMSE Testing: 8.5409 juta Rp

Eksperimen Learning Rate (Gradient Descent, 5000 iterasi):

| Learning Rate | Hasil |
|---|---|
| 0.001 | Terlalu lambat, belum konvergen setelah 5000 iterasi (loss akhir 29.0595) |
| 0.02 | Konvergen, hasil identik dengan normal equation (loss akhir 27.0972) |
| 0.1 | Divergen (loss overflow, parameter menjadi nan) |

Prediksi Penjualan:

| Biaya Iklan | Prediksi Penjualan |
|---|---|
| 4.5 juta | 69.64 juta |
| 7.0 juta | 92.12 juta |
| 12.0 juta | 137.06 juta (ekstrapolasi, kurang dapat dipercaya) |

### Bagian B — Logistic Regression (Email_Data.csv)

- Persamaan: P(Spam) = sigmoid(-10.4244 + 0.9246 x JumlahLink + 0.8837 x KataPromo)
- Decision boundary: KataPromo = 11.7959 - 1.0462 x JumlahLink
- Accuracy: 0.8000
- Precision: 0.7500
- Recall: 0.8571
- F1-Score: 0.8000

Confusion Matrix (Threshold 0.5):

| | Prediksi Bukan Spam | Prediksi Spam |
|---|---|---|
| Aktual Bukan Spam | 6 (TN) | 2 (FP) |
| Aktual Spam | 1 (FN) | 6 (TP) |

Eksperimen Threshold:

| Threshold | Precision | Recall |
|---|---|---|
| 0.3 | 0.6667 | 0.8571 |
| 0.5 | 0.7500 | 0.8571 |
| 0.7 | 1.0000 | 0.7143 |

Semakin tinggi threshold, precision naik (email biasa yang salah ditandai spam berkurang dari 3 menjadi 0), tetapi recall turun (email spam yang lolos bertambah dari 1 menjadi 2). Untuk filter spam, threshold yang lebih tinggi lebih aman agar email penting tidak masuk folder spam.

Prediksi email baru: E1 -> Bukan Spam (0.0004), E2 -> Bukan Spam (0.3777), E3 -> Spam (0.9988), E4 -> Spam (0.7587).

### Bagian C — Pemahaman Konsep

Terjawab lengkap di notebook (C1 sampai C5), meliputi:

- Alasan Logistic Regression termasuk klasifikasi
- Perbandingan normal equation vs gradient descent
- Pentingnya data training vs testing dan overfitting
- Perbedaan MSE (regresi) dan Log Loss (klasifikasi)
- Faktor yang memengaruhi perbedaan hasil antar mahasiswa

### Bonus — Perbandingan dengan scikit-learn (+5)

| Model | Implementasi Sendiri | scikit-learn |
|---|---|---|
| Linear Regression (koefisien) | 29.1879 / 8.9897 | 29.1879 / 8.9897 |
| Logistic Regression (koefisien) | -10.4244 / 0.9246 / 0.8837 | -9.6239 / 0.8408 / 0.8208 |
| Accuracy Testing | 0.8000 | 0.8000 |

Analisis: Perbedaan koefisien Logistic Regression terjadi karena scikit-learn secara default menggunakan regularisasi L2, sedangkan implementasi gradient descent di notebook ini tidak memakai regularisasi. Meskipun koefisiennya berbeda, seluruh prediksi pada data testing identik.

## Teknologi

- Python 3
- NumPy — implementasi model & metrik dari nol
- pandas — manipulasi data
- matplotlib — visualisasi
- scikit-learn — hanya untuk soal bonus

## Deadline Pengumpulan

- Reg B: Jumat, 23 Oktober 2026, 23:59 WIB
- Reg C: Sabtu, 24 Oktober 2026, 23:59 WIB

---

Tugas ini dibuat untuk memenuhi UTS mata kuliah Machine Learning.
