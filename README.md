# Laporan Proyek Machine Learning - Mochammad Ravly
## Domain Proyek : Pendidikan

> Latar belakang dari proyek ini adalah mengetahui prediksi nilai siswa, dengan apa saja yang dapat mempengaruhi siswa pada hasil nilai ujiannya.

Alasan masalah ini harus diselesaikan adalah untuk mengetahui prediksi nilai yang dihasilkan oleh siswa berdasarkan fitur-fitur yang ada pada data, sehingga nantinnya dapat mengantisipasi dampak buruk dan meningkatkan nilai ujian siswa berdasarkan hasil prediksi tersebut.

Referensi:["Pengaruh Latar Belakang Pendidikan Orangtua Terhadap Prestasi Belajar Anak di Sekolah Dasar Remang Ketike Jaya Bener Meriah"]

## Business Understanding

### Problem Statements
- Berapakah nilai ujian yang akan didapatkan oleh siswa yang dipengaruhi fitur-fitur tertentu seperti tingkat pendidikan orangtua?

### Goals

- Menciptakan model yang akan memprediksi nilai ujian siswa berdasarkan fitur-fitur yang ada dengan tingkat akurasi yang tinggi

## Data Understanding
Dataset yang digunakan dalam merancang model machine learning ini didapatkan pada "[How the Student's Test Scores are affected]"

### Variabel

Variabel-variabel pada dataset How the Student's Test Scores are affected adalah sebagai berikut:

- Gender : Merupakan gender dari siswa.
- Race/ethnicity : Merupakan Ras atau Etnis dari siswa.
- Parental level of education : Merupakan tingkat pendidikan dari orang tua siswa.
- Lunch : Merupakan makan siang yang didapatkan oleh siswa.
- Test preparation course : Merupakan test persiapan ujian yang dilakukan oleh siswa.
- Math score : Merupakan ilai ujian matematika siswa.
- Reading score : Merupakan nilai ujian membaca siswa.
- Writing score : Merupakan nilai ujian menulis siswa.

Tahapan dalam exploratory data analysis tersebut adalah :
1. Mengecek apakah ada data dengan kolom yang hilang
2. Menghitung rata-rata nilai ujian, membuat kolom baru dengan nama avg_score dan menghilangkan ketiga kolom nilai yang lain
3. Menghilangkan outliers dengan IQR Method
![Drop outliers](https://github.com/mch-rv/image/blob/main/download%20(4).png?raw=true)
4. Melakukan Univariate Analysis pada fitur dan membuat Visualisasi Data dengan plot
![Univariate Analysis Numerical](https://github.com/mch-rv/image/blob/main/download%20(3).png?raw=true)

5. Melakukan Multivariate Analysis pada fitur terhadap fitur target(avg_score) dan membuat Visualisasi Datanya
![Multivariate Analysis](https://github.com/mch-rv/image/blob/main/download%20(2).png?raw=true "Multivariate Analysis")

## Data Preparation

Pada Bagian periapan data dilakukan beberapa cara yaitu:

1. Melakukan one-hot-encoding terhadap fitur kategori
2. Melakukan Train-Test-Split dengan pembagian sebanyak 80:20, dengan data latih sebanyak 795 dan data test sebanyak 199

- Teknik one-hot encoding diperlukan untuk mengubah data kategorikal integer menjadi boolean (true false) dimana setiap data kategori unik akan di-expand menjadi kolom atau parameter baru.
- Teknik Train-Test-Split diperlukan untuk memisahkan data menjadi bagian data latih dan data uji untuk digunakan oleh model

## Modeling

Pada tahap pengembangan model, model akan menggunakan 3 algoritma yaitu, 
1. K-Nearest Neighbor, dengan tahapan:
    - Menyiapkan data frame
    - Melatih Data dengan KNN dengan parameter 10 tetangga (n_neighbors=10)
2. Random Forest, dengan tahapan:
    - Membuat dan melatih model prediksi dengan parameter estimator, kedalaman, state random dan jobs(n_estimators=50, max_depth=16, random_state=291, n_jobs=-1)
3. Boosting Algorithm, dengan tahapan:
    - Membuat dan melatih model prediksi dengan parameter learning rate dan state random(learning_rate=0.05, random_state=291)

## Evaluation

Pada tahap evaluasi matrik yang di gunakan untuk mengukur tingkat keberhasilan model adalah MSE (Mean Squared Error) yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi.

![MSE](https://www.gstatic.com/education/formulas2/472522532/en/mean_squared_error.svg "MSE")

Penjelasan : 
Yi = nilai sebenarnya (nilai observasi)
Yi' = nilai yang di prediksi
N = jumlah dari dataset

Mean squared error (MSE) mengukur jumlah kesalahan dalam model statistik. Ini menilai perbedaan kuadrat rata-rata antara nilai yang diamati dan diprediksi.

setelah menemukan model yang memiliki MSE terkecil sebagai nilai evaluasinya, maka model tersebut yang akan di gunakan kedalam tahap deployment hingga production.

![Hasil evaluasi algoritma](https://github.com/mch-rv/image/blob/main/download%20(1).png?raw=true "Hasil Evaluasi dari ketiga algoritma")

[How the Student's Test Scores are affected]: <https://www.kaggle.com/datasets/sanutribedi/how-the-students-test-scores-are-affected>

["Pengaruh Latar Belakang Pendidikan Orangtua Terhadap Prestasi Belajar Anak di Sekolah Dasar Remang Ketike Jaya Bener Meriah"]:<https://repository.ar-raniry.ac.id/id/eprint/12955/>