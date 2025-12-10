# LAPORAN ANALISA PREDIKSI BIAYA KULIAH (TUITION) MENGGUNAKAN KNIME

## Pendahuluan
Proyek ini dilakukan dengan membuat workflow di KNIME. Memiliki tujuan untuk membangun model *Machine Learning* (Regresi) yang dapat memprediksi biaya kuliah (*out-of-state tuition*) universitas di Amerika Serikat berdasarkan fasilitas, kualitas akademik, dan profil kampus lainnya. Dimulai dari *data preparation*, pemrosesan data, visualisasi, hingga pemodelan regresi untuk mendapatkan prediksi harga yang akurat.

Dataset berisi informasi statistik universitas tahun 1995, variabel utama meliputi:
- **Target Variabel:** *Out-of-state tuition* (Biaya kuliah yang akan diprediksi)
- Status Universitas (*Public/Private*)
- Biaya Hidup (*Room & Board*)
- Kualitas Dosen (*% Faculty with PhD*)
- Kepadatan Kelas (*Student/Faculty Ratio*)
- Tingkat Kelulusan (*Graduation Rate*)
- Tingkat Penerimaan (*Acceptance Rate*)

Nama dataset: `Universities.csv`, dataset diinputkan melalui node *CSV Reader* di KNIME.

---

## Data Preparation
Proses ini dilakukan untuk menyiapkan data agar siap dianalisis dan memastikan model tidak terganggu oleh data kotor.
Node yang digunakan:
- **CSV Reader**
  Digunakan untuk membaca dataset mentah `Universities.csv`.
- **Missing Value**
  Mengatasi nilai yang kosong pada dataset (misalnya dengan mengisi rata-rata atau menghapus baris).
- **Partitioning**
  Membagi data menjadi dua bagian (80% Training, 20% Testing) untuk mencegah kecurangan (*overfitting*) saat validasi model.

---

## Data Process
Mengubah data mentah menjadi fitur yang lebih bermakna untuk membantu model menebak harga.
Node yang digunakan:
- **Math Formula**
  Membuat variabel baru, seperti menghitung *Total Living Cost* (Room + Board) atau *Acceptance Rate* (Accepted / Applied).
- **Column Filter**
  Membuang kolom yang tidak relevan untuk prediksi, seperti *College Name* (agar model memprediksi berdasarkan kualitas, bukan menghafal nama kampus) dan *Phone Number*.

---

## Visualisasi Data
Tahapan ini untuk mencari *insight* dan melihat hubungan antara biaya kuliah dengan variabel lainnya.
Node yang digunakan:
- **Scatter Plot**
  Melihat korelasi positif antara Biaya Kuliah (*Tuition*) dengan Tingkat Kelulusan (*Graduation Rate*) dan Biaya Hidup.
- **Box Plot**
  Membandingkan distribusi biaya hidup dan kualitas dosen antara universitas Negeri dan Swasta.
- **Histogram**
  Melihat sebaran rasio mahasiswa per dosen (*Student/Faculty Ratio*) untuk mengetahui standar kepadatan kelas.
- **Correlation Matrix (Statistics)**
  Melihat seberapa kuat hubungan antar variabel angka.

---

## Regresi (Modeling)
Tujuannya adalah melatih komputer untuk menebak angka biaya kuliah (*Tuition*) seakurat mungkin.
Menggunakan node:
- **Random Forest Learner (Regression)**
  Melatih model menggunakan algoritma "Hutan Acak" untuk mempelajari pola harga berdasarkan fitur-fitur kampus (tanpa menghafal nama kampus).
- **Random Forest Predictor (Regression)**
  Menggunakan model yang sudah dilatih untuk menebak biaya kuliah pada data ujian (20% data testing).
- **Numeric Scorer**
  Menilai kinerja model dengan membandingkan **Harga Asli** vs **Harga Prediksi**. Metrik yang dilihat adalah **R²** (seberapa baik model menjelaskan data) dan **MAE** (rata-rata kesalahan tebakan dalam Dolar).

---

# Insight dan Interpretasi
Setelah melakukan tahapan analisis data dan pemodelan regresi, didapatkan wawasan sebagai berikut:

1.  **Faktor Penentu Harga Terbesar:** Status *Public/Private* dan Biaya Hidup (*Room & Board*) memiliki pengaruh paling besar terhadap tingginya biaya kuliah (*Tuition*).
   <img width="1097" height="294" alt="Prediction Tuition Vs Room" src="https://github.com/user-attachments/assets/48ed8785-b36d-48cb-ae00-47184a59fdcb" />

2.  **Korelasi Kualitas:** Kampus dengan biaya kuliah tinggi cenderung memiliki *Graduation Rate* yang lebih tinggi. Ada pepatah "Ada harga ada rupa" yang berlaku di dataset ini.
   <img width="1097" height="294" alt="Price Vs Gradutaion" src="https://github.com/user-attachments/assets/a67394a2-4574-4ba3-b994-0f91869cf1a1" />

3.  **Biaya Hidup:** Biaya asrama dan makan (*Living Cost*) berbanding lurus dengan SPP. Kampus dengan SPP mahal biasanya juga memiliki biaya hidup yang mahal.
   <img width="1097" height="294" alt="Total Living COst Staswa VS negeri" src="https://github.com/user-attachments/assets/9d9047fa-b7fb-435a-8a3b-62f8729518c3" />

4.  **Prediksi Model (R²):** Model Random Forest berhasil mendapatkan nilai R-Squared yang tinggi (mendekati 1), yang artinya fitur-fitur seperti rasio dosen dan fasilitas asrama sangat kuat dalam menjelaskan mahal/murahnya sebuah kampus.
   <img width="346" height="216" alt="image" src="https://github.com/user-attachments/assets/09c692ca-ea4f-472b-a642-93c785ee49db" />
   
5.  **Akurasi Tebakan (MAE):** Berdasarkan *Numeric Scorer*, rata-rata tebakan model meleset dalam rentang angka yang wajar (MAE rendah), membuktikan bahwa biaya kuliah sebenarnya bisa dihitung secara logis dari fasilitas yang ditawarkan.
   <img width="346" height="216" alt="image" src="https://github.com/user-attachments/assets/b039997e-bcf9-4391-9f22-550152fd060c" />

6.  **Anomali:** Terdapat beberapa kampus Negeri yang memiliki fasilitas setara Swasta namun harganya jauh lebih murah (dapat dilihat dari selisih harga asli dan prediksi), yang bisa menjadi rekomendasi "Best Value" bagi calon mahasiswa.
    
