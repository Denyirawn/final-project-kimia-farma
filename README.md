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
Berikut adalah langkah-langkah yang saya tempu untuk mengimpor dataset ke BigQuery umtuk pertama kalinya:
<br>

**A. Login ke Google Cloud Platform menggunakan akun Google.**

<p align="center">
   <kbd><img width="750" alt="sample"src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/d87f3a35-3323-482c-aef6-853d8825d0cd)."></kbd>
<p align="center">
Gambar 1 — Login ke Google Cloud Platform menggunakan akun Google
</p>
<br>
  

**B. Setelah login, buka Console GCP dengan mengklik console di pojok kanan atas.**
<p align="center">
   <kbd><img width="750" alt="sample"src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/ff2bba28-99a2-434b-af5b-4413d364b4fa)."></kbd>
<p align="center">
Gambar 2 — klik console 
</p>
<br>

**C. Dari Console GCP, navigasikan ke BigQuery dengan mengklik navigasi di sebelah kiri atas lalu klik "BigQuery" lalu klik BigQuery studio .**
<p align="center">
   <kbd><img width="750" alt="sample"src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/2eb035d4-4c8b-4d76-9dbe-5de8b6700d9f)"></kbd>
<p align="center">
Gambar 3 — BigQuery
</p>
<br>


**D. Di BigQuery, buat proyek baru dengan nama "Rakamin_KF_Analytics". dengan klik "Select a Project" di bagian atas dan pilih "Create Project".**
<p align="center">
   <kbd><img width="750" alt="sample"src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/8f3ecced-91df-4a29-a018-9afda8ca672e)"></kbd>
<p align="center">
Gambar 4 — create new project
</p>
<br>


<p align="center">
   <kbd><img width="750" alt="sample"src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/55f9c28f-993b-44e1-a410-1f81a77b7e46)"></kbd>
<p align="center">
Gambar 5 — create new project
</p>
<br>



**E. Setelah membuat proyek, buat dataset baru dengan nama "kimia_farma" di dalam proyek "Rakamin_KF_Analytics".**

<p align="center">
   <kbd><img width="750" alt="sample"src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/3d94d401-bd05-4874-8f3a-16e3545b4e7c)"></kbd>
<p align="center">
Gambar 6 — create new dataset
</p>
<br>

**F. inport data ke BigQuery.klik add di pojok kiri atas kemudian pilih lokal file** 


<p align="center">
   <kbd><img width="750" alt="sample"src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/1df33035-0038-4584-a7bb-ec991cadd73d)"></kbd>
<p align="center">
Gambar 7 — inport data
</p>
<br>

---
## **2. Buat tabel analisa**

Membuat tabel analisa berkaitan dengan kegiatan menyusun dan membentuk tabel yang menggabungkan dan merangkum data dari berbagai sumber untuk tujuan analisis. Tabel analisa biasanya mencakup data yang telah diproses, dihitung, dan diolah sehingga memudahkan untuk mendapatkan wawasan dan melakukan analisis mendalam. 
 <br>

<details>
  <summary> Klik untuk melihat Query </summary>
    <br>
    
```sql
CREATE OR REPLACE TABLE dataset_kimia_farma.tabel_analisis AS
SELECT 
    t.transaction_id,
    t.date,
    c.branch_id,
    c.branch_name,
    c.kota,
    c.provinsi,
    c.rating AS rating_cabang,
    t.customer_name,
    p.product_id,
    p.product_name,
    p.price AS actual_price,
    t.discount_percentage,
    CASE
        WHEN p.price <= 50000 THEN p.price * 0.1
        WHEN p.price <= 100000 THEN p.price * 0.15
        WHEN p.price <= 300000 THEN p.price * 0.20
        WHEN p.price <= 500000 THEN p.price * 0.25
        ELSE p.price * 0.30
    END AS persentase_gross_laba,
    (p.price * (1 - t.discount_percentage / 100)) AS nett_sales,
    (p.price * (1 - t.discount_percentage / 100)) *
     CASE
        WHEN p.price <= 50000 THEN 0.10
        WHEN p.price <= 100000 THEN 0.15
        WHEN p.price <= 300000 THEN 0.20
        WHEN p.price <= 500000 THEN 0.25
        ELSE 0.30
    END AS nett_profit,
    t.rating AS rating_transaksi
FROM 
    dataset_kimia_farma.kf_final_transaction t
JOIN 
    dataset_kimia_farma.kf_kantor_cabang c ON t.branch_id = c.branch_id
JOIN 
    dataset_kimia_farma.kf_product p ON t.product_id = p.product_id
JOIN 
    dataset_kimia_farma.kf_inventory i ON t.product_id = i.product_id AND t.branch_id = i.branch_id;
);


    


  
    

```
    
<br>
</details>
<br>

<p align="center">
   <kbd><img width="750" alt="sample tabel analisa "src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/93267847-3c02-4e90-88aa-155fbe3c8db4).png"></kbd>
<p align="center">
Gambar 8  — Report Dashboard PT. Kimia Farma
</p>
<br>



---
## **Data Visualization with looker studio**

[Lihat pada halaman Looker Data Studio](https://lookerstudio.google.com/reporting/3b0bd0e3-218e-4480-80ea-aa8952e098d0).

<p align="center">
   <kbd><img width="750" alt="Data Visualization"src="https://github.com/Denyirawn/final-project-kimia-farma/assets/170843873/dbd751df-a2dd-4380-ba17-08f4ae10c8c8)."></kbd>
<p align="center">
Gambar 8  — Report Dashboard PT. Kimia Farma
</p>
<br>

---
