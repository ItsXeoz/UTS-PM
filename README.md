# Oranges vs Grapefruit Classification

Repositori ini dibuat untuk memenuhi tugas Ujian Tengah Semester (UTS) mata kuliah Pembelajaran Mesin. Fokus utama dari proyek ini adalah membangun model *machine learning* untuk mengklasifikasikan buah Jeruk (Orange) dan Jeruk Bali (Grapefruit) berdasarkan karakteristik fisik dan warnanya.


- **Nama:** Abidzar Giffari
- **NIM:** 1227050001

## Ringkasan Proyek

Dataset yang digunakan adalah dataset `citrus` dari Kaggle yang berisi 10.000 data buah (50:50 proporsinya). Setiap baris data memiliki informasi berupa diameter, berat, dan nilai warna (RGB).

Proyek ini dikerjakan dengan mengikuti standar alur kerja **CRISP-DM** (Cross-Industry Standard Process for Data Mining). Algoritma yang dibandingkan adalah Decision Tree, Naive Bayes, dan Support Vector Machine (SVM).

## Alur Kerja (CRISP-DM)

1. **Business Understanding:** Tujuannya sederhana, yaitu membuat model prediksi yang akurat untuk otomatisasi penyortiran buah jeruk dan jeruk bali agar tidak perlu dilakukan manual.
2. **Data Understanding:** Mengecek kelengkapan data `citrus.csv` dan melihat sebaran fiturnya.
3. **Data Preparation:** - Mengubah label kelas (Orange = 0, Grapefruit = 1).
   - Membagi data untuk proses latih (80%) dan uji (20%).
   - Melakukan standarisasi data dengan `StandardScaler`. Ini wajib dilakukan terutama karena kita menggunakan SVM yang sangat sensitif terhadap perbedaan skala angka.
4. **Modeling:** Melatih ketiga algoritma. Untuk mencegah model sekadar menghafal data (*overfitting*), saya menggunakan `GridSearchCV` untuk mencari hyperparameter terbaik. Misalnya, pada Decision Tree, kedalaman pohon (`max_depth`) dibatasi agar tidak *unpruned*.
5. **Evaluation:** Metrik yang dinilai adalah akurasi dan membandingkan hasil prediksi data latih vs data uji. Evaluasi juga didukung oleh visualisasi *Confusion Matrix Heatmap* dan *Scatter Plot*.
6. **Deployment:** Source code dirapikan dalam format Jupyter Notebook dan dipublikasikan ke GitHub.

## Kesimpulan Evaluasi

Dari ketiga model yang diuji, **Support Vector Machine (SVM)** dengan `kernel='linear'` keluar sebagai model dengan performa paling stabil dan optimal. 

Model SVM mendapatkan akurasi di kisaran **~96%**. Selain itu, selisih (*gap*) antara Akurasi Training dan Akurasi Testing sangat kecil. Ini membuktikan bahwa model memiliki generalisasi yang sangat baik (*Good Fit*) dan berhasil menghindari jebakan *overfitting* yang sempat dialami oleh Decision Tree saat parameternya tidak dibatasi.