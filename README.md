Virtual Internship Experience: Big Data Analytics - Kimia Farma

# **Virtual Internship Experience: Big Data Analytics - Kimia Farma**
Tool : MySQL Workbench - [Lihat script](https://github.com/faizns/VIX-Big-Data-Analytics-Kimia-Farma/blob/a4da84f3d2fb45693599c279747cabf271cfd866/vix_kimia_farma_script.sql) <br>
Visualization : Looker Data Studio - [Lihat dashboard](https://lookerstudio.google.com/reporting/3c67b292-3be2-484d-bc29-27bd0b4015fd) <br>
Dataset : [VIX Kimia Farma](https://www.rakamin.com/virtual-internship-experience/kimiafarma-big-data-analytics-virtual-internship-program)
<br>

---

##  **Introduction**
VIX Big Data Analytics Kimia Farma merupakan virtual internship experience yang diadakan oleh [Rakamin Academy](https://www.rakamin.com/virtual-internship-experience/kimiafarma-big-data-analytics-virtual-internship-program) dan berkolaborasi dengan PT Kimia Farma. Pada project ini saya berperan sebagai Data Analyst Intern yang diminta untuk membuat Analisis kinerja bisnis Kimia Farma Tahun 2020-2023. adapun tugas tugasnya sebagai berikut :
1. Importing Dataset to BigQuery
2. Buat tabel analisa
3. Create Dashboard Performance Analytics Kimia Farma Business Year 2020-2023
<br>

**Dataset** <br>
Berikut Dataset yang disediakan terdiri dari tabel-tabel berikut:
- kf_final_transaction.csv [Lihat data](https://drive.google.com/file/d/1SYy33VGnB0K4al0hqwuDqrnnrN10sUpD/view?usp=sharing)
- kf_inventory.csv [Lihat data](https://drive.google.com/file/d/18WzXfFEP5AhXve8uWJa_wudXRliPoWy4/view?usp=sharing)
- kf_kantor_cabang.csv [Lihat data](https://drive.google.com/file/d/1QkReg7vIDDzeagrLuYV_Q3eb-WqwDI6N/view?usp=sharing)
- kf_product.csv [Lihat data](https://drive.google.com/file/d/1fXGc2S90ElpsWzewlf4K8ODkJMU30REa/view?usp=sharing)
<br>


---


## **1. Importing Dataset to BigQuery**
Berikut adalah langkah-langkah yang saya tempu untuk mengimpor dataset ke BigQuery:
<br>

**a. Login ke Google Cloud Platform menggunakan akun Google.**

**b. Setelah login, buka Console GCP dengan mengklik ikon navigasi di pojok kiri atas dan memilih "Console".**

**c. Dari Console GCP, navigasikan ke BigQuery dengan mengklik "BigQuery" atau dapat diakses melalui menu navigasi di sebelah kiri.**

**d. Di BigQuery, buat proyek baru dengan nama "Rakamin_KF_Analytics". Klik pada nama proyek (atau klik "Select a Project" di bagian atas) dan pilih "Create Project".**

**e. Setelah membuat proyek, buat dataset baru dengan nama "kimia_farma" di dalam proyek "Rakamin_KF_Analytics".**
<br>


### Tabel Aggregat
Tabel agregat adalah tabel yang dibuat dengan mengumpulkan dan menghitung data dari tabel basis. Tabel aggregat ini berisi informasi yang lebih ringkas dan digunakan untuk menganalisis data lebih cepat dan efisien. Hasil tabel ini akan digunakan untuk sumber pembuatan dashboard laporan penjualan.

<details>
  <summary> Klik untuk melihat Query </summary>
    <br>
    
```sql
CREATE TABLE agg_table (
SELECT
    tanggal,
    MONTHNAME(tanggal) AS bulan,        -- kolom nama bulan
    id_invoice,
    cabang_sales AS lokasi_cabang,
    nama AS pelanggan,
    nama_barang AS produk,
    lini AS merek,
    jumlah AS jumlah_produk_terjual,
    harga AS harga_satuan,
    (jumlah * harga) AS total_pendapatan  -- kolom baru total pendapatan
FROM base_table
ORDER BY 1, 4, 5, 6, 7, 8, 9, 10
);
```
    
<br>
</details>
<br>

<p align="center">
    <kbd> <img width="750" alt="sample aggregat" src="https://user-images.githubusercontent.com/115857221/222876809-62000814-75b6-4f82-b6b7-05d00e618315.png"> </kbd> <br>
    Gambar 2 — Sampel Hasil Pembuatan Tabel Aggregat
</p>
<br>

---
## **2. Buat tabel analisa**



---
## 📂 **Data Visualization**

[Lihat pada halaman Looker Data Studio](https://lookerstudio.google.com/reporting/3b0bd0e3-218e-4480-80ea-aa8952e098d0).

![Screenshot 2024-06-01 213933](https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/dbd751df-a2dd-4380-ba17-08f4ae10c8c8)
<p align="center">
    Gambar  — Report Dashboard PT. Kimia Farma
</p>
<br>

---
