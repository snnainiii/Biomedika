# 🧬 Klasifikasi Leukemia Menggunakan Ekstraksi Fitur GLCM dan Naive Bayes  

![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-FFD43B?style=for-the-badge)
![GLCM](https://img.shields.io/badge/Feature%20Extraction-GLCM-blue?style=for-the-badge)
![Naive Bayes](https://img.shields.io/badge/Classifier-Naive%20Bayes-orange?style=for-the-badge)

> Proyek ini disusun untuk memenuhi tugas **Ujian Akhir Semester (UAS)**  
> Mata Kuliah **Biomedika** – Dosen Pengampu: *Prof. Dr. Arif Muntasa, S.Si., M.T.*

---

## 📘 Deskripsi Proyek  
Proyek ini bertujuan untuk **mengklasifikasikan citra sel darah** antara **normal dan leukemia** menggunakan metode **Ekstraksi Fitur GLCM (Gray-Level Co-occurrence Matrix)** serta algoritma **Naive Bayes Classifier**.  
Dataset yang digunakan adalah **ALL_IDB2**, yang berisi citra digital sel darah dengan ukuran 103x103 piksel.

---

## 🧩 Dataset  
- **Sumber:** ALL_IDB2 (berasal dari ALL_IDB1)  
- **Jumlah Data:** 260 citra  
  - 🟩 **Kelas 1 (Normal)**: 130 data  
  - 🟥 **Kelas 2 (Leukemia)**: 130 data  
- **Ukuran Citra:** 103 × 103 piksel  

Dataset berisi gambar sel darah normal dan sel leukemia yang akan dianalisis secara tekstural.

---

## 🧠 Tahapan Sistem  

### 🔹 1. Segmentasi  
Segmentasi bertujuan memisahkan objek utama (sel) dari latar belakang.  
Langkah-langkah segmentasi:
1. Pisahkan citra ke channel **R, G, dan B**  
2. Perbaiki channel **G dan R**  
3. Gabungkan kembali channel yang telah diperbaiki  
4. Konversi citra **RGB → HSV**  
5. Pilih channel **H**, terapkan *median filtering*  
6. Konversi menjadi citra biner  
7. Terapkan operasi morfologi  
8. Lakukan *labeling* dan pilih objek dengan luas maksimum  

---

### 🔹 2. Ekstraksi Fitur – GLCM (Gray-Level Co-occurrence Matrix)  
Ekstraksi fitur dilakukan untuk mengubah informasi citra menjadi representasi numerik.  
Parameter GLCM yang digunakan:
- Jarak (d = 1)  
- Sudut (0°, 45°, 90°, 135°)  

Fitur yang diambil dari hasil GLCM:
| Fitur | Deskripsi |
|-------|------------|
| **Contrast** | Mengukur perbedaan intensitas antar piksel |
| **Correlation** | Mengukur keterkaitan linear antar piksel |
| **Energy** | Menunjukkan keseragaman tekstur citra |
| **Homogeneity** | Mengukur kesamaan nilai piksel yang berdekatan |

Semua fitur disimpan ke dalam file `.csv` sebagai dataset untuk klasifikasi.

---

### 🔹 3. Klasifikasi – Naive Bayes  
Metode **Naive Bayes Classifier** digunakan untuk memprediksi jenis sel darah berdasarkan fitur hasil ekstraksi.  
Langkah-langkah:
1. Membaca dataset hasil ekstraksi  
2. Melakukan **normalisasi data**  
3. Memisahkan fitur (X) dan target (y)  
4. Melakukan **train-test split (80:20)**  
5. Inisialisasi model Naive Bayes  
6. Melakukan **10-fold cross validation**  
7. Evaluasi model menggunakan:
   - Confusion Matrix  
   - Akurasi  
   - Presisi  
   - Recall  
   - F1-Score  

---

## 🧮 Perhitungan Manual  

### 📊 GLCM  
Perhitungan manual dilakukan dengan:
- Jarak = 1  
- Sudut = 45°  
Hasil dihitung untuk melihat bagaimana GLCM bekerja dalam memetakan hubungan antar-piksel.


---

## 🏗️ Arsitektur Sistem  
```text
Dataset (ALL_IDB2)
        │
        ▼
Segmentasi Citra
        │
        ▼
Ekstraksi Fitur (GLCM)
        │
        ▼
Klasifikasi (Naive Bayes)
        │
        ▼
Evaluasi & Analisis

```


