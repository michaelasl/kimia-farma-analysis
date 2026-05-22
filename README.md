## Kimia Farma Big Data Analytics

### Project Overview

Project ini bertujuan untuk menganalisis kinerja bisnis Kimia Farma selama periode **2020–2023** dengan memanfaatkan teknologi Big Data Analytics. Analisis difokuskan pada evaluasi performa penjualan, profitabilitas, serta kinerja cabang di berbagai wilayah Indonesia guna menghasilkan insight yang dapat mendukung pengambilan keputusan strategis.

---

### Objectives

* Menganalisis tren pendapatan dan profit dari tahun ke tahun
* Mengidentifikasi cabang dengan performa terbaik dan terendah
* Mengevaluasi hubungan antara rating cabang dan jumlah transaksi
* Menyajikan insight berbasis data untuk mendukung pengambilan keputusan bisnis

---

### Dataset

Dataset yang digunakan dalam proyek ini meliputi:

* **kf_final_transaction** → Data transaksi penjualan
* **kf_inventory** → Data persediaan produk
* **kf_kantor_cabang** → Informasi cabang (lokasi dan rating)
* **kf_product** → Informasi produk obat

---

### Tools & Technologies

* **Google BigQuery** → Data warehouse dan pemrosesan data
* **Looker Studio** → Visualisasi data dan dashboard
* **SQL** → Transformasi dan analisis data

---

### Data Processing (BigQuery)

### 1. Import Dataset

Seluruh dataset diimpor ke dalam dataset:

```sql
kimia_farma
```

---

### 2. Data Transformation

Dilakukan proses transformasi data dengan menggabungkan beberapa tabel menggunakan operasi **JOIN** untuk membentuk tabel analisa yang terintegrasi.

```sql
CREATE OR REPLACE TABLE kimia_farma.tabel_analisa AS
SELECT ...
```

---

### 3. Calculated Fields

Beberapa metrik tambahan dibuat untuk mendukung analisis:

* **nett_sales** → Harga setelah diskon
* **nett_profit** → Keuntungan bersih berdasarkan nett sales
* **persentase_gross_laba** → Ditentukan berdasarkan kategori harga produk

**Klasifikasi persentase gross laba:**

* ≤ 50.000 → 10%
* 50.000 – 100.000 → 15%
* 100.000 – 300.000 → 20%
* 300.000 – 500.000 → 25%
* > 500.000 → 30%

---

### Dashboard (Looker Studio)
https://datastudio.google.com/reporting/207b492f-233b-404b-b957-b278c6ce82ae 

Dashboard interaktif dikembangkan untuk menampilkan insight utama, meliputi:

*  Ringkasan kinerja (Total Sales, Total Profit, Total Transaksi, Total Customer)
*  Tren pendapatan tahunan (2020–2023)
*  Top 10 cabang berdasarkan jumlah transaksi
*  Top 10 cabang berdasarkan nett sales
*  Top 5 cabang dengan rating tinggi namun transaksi rendah
*  Peta distribusi profit berdasarkan provinsi di Indonesia

---

### Key Insights

* Terdapat tren pertumbuhan penjualan yang konsisten dari tahun ke tahun
* Beberapa provinsi memberikan kontribusi signifikan terhadap total profit perusahaan
* Rating cabang yang tinggi tidak selalu berbanding lurus dengan jumlah transaksi
* Cabang dengan volume transaksi tinggi menjadi kontributor utama terhadap profit

---

### Repository Content

* `query_analisa.sql` → Query SQL untuk membangun tabel analisa
* `dashboard_screenshot.png` → Tampilan dashboard
* `README.md` → Dokumentasi proyek

---

### Conclusion

Analisis ini menunjukkan bahwa performa bisnis Kimia Farma dipengaruhi oleh berbagai faktor, seperti lokasi cabang, harga produk, serta strategi pemberian diskon. Melalui dashboard yang dibangun, perusahaan dapat memonitor kinerja secara lebih efektif dan mengambil keputusan yang lebih tepat berbasis data.

