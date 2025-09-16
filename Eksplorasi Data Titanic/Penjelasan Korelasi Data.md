
## Ringkasan Korelasi Data Titanic 🚢

Berikut adalah penjelasan mengenai hubungan (korelasi) antara beberapa variabel kunci dari dataset Titanic dengan tingkat kelangsungan hidup penumpang.

### Korelasi 1: Jenis Kelamin (Sex) vs. Kelangsungan Hidup (Survived)

Terdapat korelasi yang **sangat kuat** antara jenis kelamin dan peluang untuk selamat. Penumpang wanita secara signifikan memiliki tingkat kelangsungan hidup yang jauh lebih tinggi dibandingkan penumpang pria.

* 👩 **Wanita**: Tingkat kelangsungan hidup sekitar **74.2%**.
* 👨 **Pria**: Tingkat kelangsungan hidup sekitar **18.9%**.

**Interpretasi:** Perbedaan drastis ini sangat dipengaruhi oleh protokol evakuasi maritim tidak resmi yaitu **"wanita dan anak-anak terlebih dahulu"** yang diterapkan saat proses penyelamatan.

---

### Korelasi 2: Kelas Penumpang (Pclass) vs. Kelangsungan Hidup (Survived)

Kelas sosial penumpang memiliki korelasi yang kuat dengan kelangsungan hidup. **Semakin tinggi kelas penumpang (ditandai dengan angka yang lebih kecil), semakin besar peluangnya untuk selamat.**

* ✅ **Kelas 1**: Tingkat kelangsungan hidup ~**63.0%**.
* ✅ **Kelas 2**: Tingkat kelangsungan hidup ~**47.3%**.
* ❌ **Kelas 3**: Tingkat kelangsungan hidup ~**24.2%**.

**Interpretasi:** Penumpang kelas satu umumnya memiliki kabin yang berlokasi di dek bagian atas, sehingga memberikan mereka **akses yang lebih mudah dan cepat ke sekoci penyelamat** dibandingkan penumpang kelas tiga yang kabinnya berada di bagian bawah kapal.

---

### Korelasi 3: Pelabuhan Keberangkatan (Embark Town) vs. Kelangsungan Hidup (Survived)

Pelabuhan tempat penumpang naik juga menunjukkan adanya korelasi dengan tingkat kelangsungan hidup, meskipun ini kemungkinan merupakan korelasi tidak langsung yang dipengaruhi oleh kelas penumpang.

* **Cherbourg (Prancis)**: Tingkat kelangsungan hidup ~**55.4%**.
* **Queenstown (Irlandia)**: Tingkat kelangsungan hidup ~**39.0%**.
* **Southampton (Inggris)**: Tingkat kelangsungan hidup ~**33.9%**.

**Interpretasi:** Tingginya tingkat kelangsungan hidup dari **Cherbourg** dapat dijelaskan karena pelabuhan ini memiliki proporsi penumpang **Kelas 1** yang lebih tinggi dibandingkan pelabuhan lainnya.

---

### **Kesimpulan**

Dari analisis ini, terlihat jelas bahwa faktor sosial seperti **jenis kelamin** dan **kelas ekonomi (diwakili oleh `pclass`)** merupakan prediktor yang jauh lebih signifikan untuk kelangsungan hidup dalam tragedi Titanic dibandingkan faktor lainnya seperti usia atau tarif tiket.
