

---

# Analisis Data Peringkat Universitas Nasional

Dokumen ini merupakan `README` untuk proyek analisis data *National Universities Rankings*. Proyek ini mencakup proses dari pemeriksaan data mentah, pembersihan, hingga visualisasi untuk mendapatkan wawasan.

## Deskripsi Proyek

Proyek ini bertujuan untuk menganalisis dataset `National Universities Rankings.csv` untuk memahami karakteristik dan tren dari universitas-universitas yang terdaftar. Proses analisis melibatkan beberapa tahapan kunci, dimulai dengan *Data Profiling* untuk mendiagnosis kondisi awal data.

---
## Penjelasan Laporan Analisis Kualitas Data (ydata-profiling)

Dokumen ini menjelaskan informasi yang muncul setelah menggunakan `ydata-profiling` pada **dataset Peringkat Universitas Nasional** dan menguraikan dampak penting dari penggunaan alat ini dalam proses analisis data.

Laporan yang dihasilkan oleh `ydata-profiling` memberikan diagnosis lengkap mengenai "kesehatan" dataset kita. Berikut adalah temuan-temuan kunci yang terungkap:

### Temuan Kunci dari Profiling

1.  **Gambaran Umum (Overview):**
    * Dataset ini terdiri dari **230 baris** (universitas) dan **7 kolom** (atribut).
    * Terdapat **9 sel data yang kosong** (0.6% dari total data), yang menandakan adanya informasi yang tidak lengkap.

2.  **Masalah Tipe Data (Variables):**
    * `ydata-profiling` secara otomatis mendeteksi bahwa kolom `Tuition and fees` dan `Undergrad Enrollment` **salah diidentifikasi sebagai teks (`object`)**, bukan angka.
    * Penyebabnya adalah adanya karakter non-numerik seperti `$` dan `,` yang membuat kolom ini tidak bisa langsung diolah secara matematis.

3.  **Nilai Kosong (Missing Values):**
    * Laporan memvisualisasikan dengan jelas bahwa "kebolongan" data terdapat pada kolom:
        * **`Tuition and fees`**: 8 baris kosong.
        * **`Undergrad Enrollment`**: 1 baris kosong.

4.  **Kualitas Data Lainnya:**
    * Laporan mengonfirmasi bahwa **tidak ada baris data yang terduplikasi**, yang merupakan kabar baik dari segi kualitas data.

---
## Dampak Penggunaan `ydata-profiling` dan Langkah Selanjutnya

Penggunaan `ydata-profiling` di awal proyek memberikan dampak yang sangat signifikan:

* **Efisiensi:** Menghemat waktu dalam mengidentifikasi masalah. Tanpa alat ini, kita harus memeriksa setiap kolom secara manual.
* **Akurasi Diagnosis:** Memberikan gambaran yang komprehensif dan akurat tentang di mana letak masalah dalam data.
* **Menjadi Dasar Rencana Kerja:** Hasil profiling menjadi peta jalan yang jelas untuk tahap selanjutnya.

Berdasarkan temuan di atas, **langkah selanjutnya** yang harus dilakukan adalah **Data Cleaning**, yang mencakup:
1.  **Memperbaiki Tipe Data:** Menghapus karakter `$` dan `,` lalu mengubah kolom terkait menjadi tipe numerik.
2.  **Menangani Nilai Kosong:** Mengisi 9 sel data yang kosong dengan strategi yang tepat (misalnya, menggunakan nilai rata-rata atau median).

Setelah data bersih, barulah kita bisa melanjutkan ke tahap **analisis dan visualisasi** untuk menarik kesimpulan yang valid dan akurat.
