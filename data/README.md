# Data Tugas 1

## 1. Dataset yang Dipilih

Dataset yang digunakan dalam proyek ini adalah **Corpus-Indonesia**, yaitu kumpulan teks berbahasa Indonesia yang tersedia secara publik melalui Hugging Face Datasets. Dataset ini digunakan sebagai bahan praktik pengolahan data berskala besar (*Big Data Processing*), dengan fokus pada data profiling, data cleaning, dan validasi kualitas data.

| Item | Keterangan |
|---|---|
| Nama dataset | Corpus-Indonesia |
| Sumber dataset | [Hugging Face Datasets - Lyon28/Corpus-Indonesia](https://huggingface.co/datasets/Lyon28/Corpus-Indonesia) |
| Pemilik/pengunggah | Lyon28 |
| Lisensi yang tercantum | Apache License 2.0 (sesuai metadata repositori Hugging Face) |
| Format data | Parquet |
| Ukuran unduhan | Sekitar 1,90 GB |
| Jumlah data awal | 19.483.721 baris |
| Jumlah file mentah | 7 file Parquet |
| Jumlah kolom | 1 kolom, yaitu `text` |
| Bahasa | Bahasa Indonesia |
| Periode data | Tidak dinyatakan secara spesifik dalam metadata dataset |
| Unit analisis | Satu entri teks pada setiap baris |

**Sumber:** [Repositori Corpus-Indonesia di Hugging Face](https://huggingface.co/datasets/Lyon28/Corpus-Indonesia).

**Catatan lisensi:** Apache License 2.0 tercantum pada metadata repositori dataset. Informasi tersebut dicatat sebagai lisensi yang dinyatakan oleh pengunggah. Asal dan ketentuan penggunaan setiap teks sumber tetap perlu diperhatikan apabila digunakan di luar kebutuhan akademik proyek ini.

## 2. Karakteristik Dataset

Corpus-Indonesia merupakan dataset berbentuk korpus teks yang dapat digunakan untuk mempelajari pengolahan data tekstual dalam jumlah besar. Struktur awal dataset terdiri atas satu kolom bernama `text`, dengan setiap baris berisi teks berbahasa Indonesia.

Berdasarkan pemeriksaan awal, isi dataset mencakup teks informatif mengenai berbagai topik, seperti geografi, sejarah, lingkungan, kependudukan, pemerintahan, dan perkembangan teknologi di Indonesia. Topik tersebut merupakan contoh dari data yang diperiksa dan tidak dimaksudkan sebagai klasifikasi lengkap seluruh isi korpus.

Ukuran dataset dan jumlah barisnya memenuhi persyaratan tugas, yaitu lebih dari 1.000.000 baris dan ukuran berkas unduhan di atas 500 MB. Dengan karakteristik tersebut, dataset sesuai digunakan untuk mempraktikkan pemrosesan data berskala besar menggunakan Python, Polars, dan DuckDB.

## 3. Tujuan Penggunaan Dataset

Dataset ini digunakan untuk melaksanakan tahapan pengolahan data dalam Tugas 1, dengan tujuan sebagai berikut.

1. **Data profiling:** mengidentifikasi struktur dataset, jumlah baris, tipe data, panjang teks, nilai kosong, dan duplikasi.
2. **Data cleaning:** menangani teks kosong atau hanya berisi spasi serta memastikan kualitas data yang dipertahankan.
3. **Data validation:** memeriksa kembali hasil pembersihan untuk memastikan tidak terdapat teks kosong dan duplikasi persis yang tidak diinginkan.
4. **Data summarization:** menghasilkan ringkasan statistik menggunakan DuckDB sebagai pendukung analisis kualitas data.
5. **Reproducibility:** mendokumentasikan kode dan hasil analisis dalam Jupyter Notebook agar proses dapat ditinjau dan dijalankan kembali.

## 4. Cara Memperoleh Data

Dataset diperoleh dari repositori publik Hugging Face berikut:

- **URL:** https://huggingface.co/datasets/Lyon28/Corpus-Indonesia
- **Format unduhan:** Parquet
- **Jumlah berkas:** 7 file
- **Lokasi penyimpanan lokal:** `data/raw/corpus-indonesia/data/`

Dataset diunduh menggunakan `huggingface_hub` melalui fungsi `snapshot_download`. Seluruh file mentah disimpan pada direktori `data/raw/` dan dipertahankan sebagai sumber asli untuk proses profiling serta cleaning.

Notebook `notebooks/01_data_profiling.ipynb` digunakan untuk memeriksa dataset awal, sedangkan `notebooks/02_data_cleaning.ipynb` digunakan untuk menjalankan proses pembersihan dan validasi.

## 5. Aturan Penyimpanan dan Pengelolaan Data

Untuk menjaga keteraturan proyek dan menghindari penyimpanan berkas berukuran besar di GitHub, pengelolaan data dilakukan dengan ketentuan berikut.

- `data/raw/` digunakan untuk menyimpan dataset mentah dan tidak diubah selama proses analisis.
- `data/processed/` digunakan untuk menyimpan hasil transformasi yang dihasilkan dari proses cleaning.
- `output/tables/` digunakan untuk menyimpan laporan kualitas data dan ringkasan statistik.
- `notebooks/` digunakan untuk menyimpan kode analisis, dokumentasi proses, dan hasil eksekusi notebook.
- Dataset mentah dan berkas Parquet hasil olahan yang berukuran besar tidak dimasukkan ke Git.
- File `.gitignore` digunakan untuk mengecualikan berkas data berukuran besar dan file sementara notebook dari pelacakan Git.

## 6. Ringkasan

Corpus-Indonesia dipilih karena memiliki jumlah data yang besar, struktur yang relatif sederhana, dan format penyimpanan yang mendukung pemrosesan data secara efisien. Dataset ini menjadi dasar pelaksanaan Milestone 1 melalui data profiling dan Milestone 2 melalui data cleaning serta validasi kualitas data.

Penggunaan Polars dan DuckDB membantu pemrosesan serta peringkasan data, sedangkan Jupyter Notebook digunakan untuk mendokumentasikan tahapan analisis. Seluruh proses dirancang agar dapat ditinjau, dijelaskan, dan direproduksi berdasarkan kode serta laporan yang disimpan dalam repositori proyek.
