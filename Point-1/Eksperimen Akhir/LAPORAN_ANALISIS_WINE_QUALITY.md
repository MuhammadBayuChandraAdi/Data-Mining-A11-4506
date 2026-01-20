# LAPORAN ANALISIS REGRESI: KUALITAS WINE MERAH

Analisis ini bertujuan untuk memodelkan hubungan antara fitur fisikokimia wine terhadap skor kualitas sensorik menggunakan teknik Regresi Linear.

---

## [1] Deskripsi Dataset
Dataset yang digunakan adalah **Red Wine Quality** yang bersumber dari UCI Machine Learning Repository. Dataset ini mencakup 1.599 sampel wine merah dari wilayah Portugal utara.

- **Struktur**: 1.599 baris, 11 fitur prediktor (fisikokimia), dan 1 variabel target (skor kualitas 0-10).
- **Variabel Utama**:
    - `Fixed Acidity`, `Volatile Acidity`, `Citric Acid`
    - `Residual Sugar`, `Chlorides`, `Density`, `pH`, `Sulphates`
    - `Free/Total Sulfur Dioxide`, `Alcohol`
    - **Target**: `Quality` (Median: 6, Range: 3-8)

---

## [2] Objektif Analisis
1. Membangun model prediksi kualitas wine menggunakan Regresi Linear Berganda.
2. Mengidentifikasi variabel fisikokimia yang memiliki pengaruh paling signifikan terhadap kualitas wine.
3. Membandingkan performa model regresi sederhana vs berganda.

---

## [3] Perbandingan Model
Berdasarkan eksperimen di Notebook, kami membandingkan tiga pendekatan:

| Model | Fitur Utama | R-squared | RMSE |
|-------|-------------|-----------|------|
| Simple Linear Regression | Alcohol | 0.22 | 0.71 |
| Multiple Linear Regression | All (11 features) | 0.40 | 0.62 |
| Optimized Regression | Significant Features | 0.39 | 0.63 |

**Justifikasi**: Model **Multiple Linear Regression (All Features)** dipilih karena memberikan R-squared tertinggi (0.40), yang berarti model mampu menjelaskan 40% variansi dalam data kualitas wine, dengan error terendah (RMSE 0.62).

---

## [4] Temuan & Interpretasi
Berdasarkan hasil OLS Summary, fitur yang paling berpengaruh adalah:

1. **Alcohol (Coef: 0.276)**: Setiap kenaikan 1% alkohol cenderung meningkatkan skor kualitas sebesar ~0.28 poin. Ini adalah faktor positif terkuat.
2. **Volatile Acidity (Coef: -1.083)**: Peningkatan asam asetat berlebihan (bau cuka) menurunkan kualitas secara drastis.
3. **Sulphates (Coef: 0.916)**: Kandungan sulfat yang tepat berkontribusi positif terhadap kualitas wine sebagai anti-mikroba.
4. **Chlorides (Coef: -1.874)**: Kandungan garam yang tinggi berkolerasi negatif dengan kualitas sensorik.

**Signifikansi Statistik**: Fitur `alcohol`, `volatile_acidity`, `sulphates`, `total_sulfur_dioxide`, dan `chlorides` memiliki **P-value < 0.000**, menunjukkan tingkat kepercayaan yang sangat tinggi.

---

## [5] Evaluasi & Langkah Selanjutnya

### Evaluasi Model (Residual Analysis)
- **Normalitas**: Residual berdistribusi mendekati normal di sekitar angka nol.
- **Homoskedastisitas**: Plot residual menunjukkan penyebaran yang relatif konsisten, meskipun terdapat sedikit penyempitan pada skor kualitas ekstrim (3 & 8).
- **Limitasi**: Model linear sederhana memiliki keterbatasan dalam menangkap interaksi non-linear yang kompleks antara fitur kimia.

### Langkah Selanjutnya
1. **Model Non-Linear**: Menggunakan Random Forest atau Gradient Boosting untuk menangkap pola non-linear.
2. **Feature Engineering**: Mencoba kombinasi fitur atau transformasi logaritma pada fitur dengan pencilan tinggi.
3. **Data Tambahan**: Menambahkan fitur sensorik atau data varietas anggur yang spesifik.

---
*Laporan ini dihasilkan untuk memenuhi kriteria penugasan Regression Analysis.*
