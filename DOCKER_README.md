# Docker setup — Corpus-Indonesia

## Apa yang disiapkan

- `Dockerfile`: image Python untuk Jupyter, Polars, DuckDB, Pandas, dan Matplotlib.
- `compose.yaml`: menjalankan Jupyter pada `127.0.0.1:8888`.
- `.dockerignore`: mengecualikan dataset mentah dan file Parquet besar dari build context.
- `requirements.txt`: dependensi Python.

Dataset tidak disalin ke dalam image. Folder proyek di-mount ke `/workspace`, jadi file `data/raw/` lokal tetap bisa dibaca dari container dan hasil di `data/processed/` tetap tersimpan pada folder proyek Windows.

## Prasyarat

Docker Desktop harus berjalan. Buka CMD pada root proyek `tugas1-corpus-indonesia`.

## Build image

```cmd
docker compose build
```

## Jalankan Jupyter

```cmd
docker compose up -d
docker compose logs notebook
```

Cari URL Jupyter yang memuat token di output logs, lalu buka URL tersebut pada browser. Port hanya dipublikasikan ke localhost (`127.0.0.1`).

## Verifikasi paket di container

```cmd
docker compose exec notebook python -c "import polars as pl, duckdb, pandas, matplotlib; print('Polars:', pl.__version__); print('DuckDB:', duckdb.__version__); print('Pandas:', pandas.__version__); print('Matplotlib:', matplotlib.__version__)"
```

## Hentikan container

```cmd
docker compose down
```

## Catatan penting

- Build pertama perlu mengunduh image Python dan paket Python, jadi membutuhkan koneksi internet.
- Jangan tambahkan dataset mentah atau file Parquet hasil cleaning berukuran besar ke Git.
- Notebook yang menggunakan path relatif perlu dijalankan dari struktur folder proyek yang sama.
- Docker Engine yang aktif belum membuktikan image berhasil dibangun. Build dan verifikasi di atas tetap perlu dijalankan.
