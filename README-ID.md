# Metabase Boilerplate

Boilerplate Docker untuk deploying Metabase dengan database PostgreSQL eksternal.

## Persyaratan

- [Docker](https://www.docker.com/) (versi 20.10 atau lebih tinggi)
- [Docker Compose](https://docs.docker.com/compose/) (versi 1.29 atau lebih tinggi)
- Database PostgreSQL eksternal

## Cara Menggunakan

1. Clone repository ini
2. Salin file environment:
   ```bash
   cp .env.example .env
   ```
3. Konfigurasi kredensial database di `.env`
4. Jalankan Metabase:
   ```bash
   docker-compose up -d
   ```
5. Akses Metabase di `http://localhost:{SERVER_PORT}`

## Konfigurasi

Semua konfigurasi dilakukan melalui file `.env`:

| Variabel | Deskripsi | Default |
|----------|-----------|---------|
| `SERVER_PORT` | Port host untuk Metabase | `3001` |
| `MB_DB_TYPE` | Tipe database | `postgres` |
| `MB_DB_HOST` | Host database | `host.docker.internal` |
| `MB_DB_PORT` | Port database | `5432` |
| `MB_DB_DBNAME` | Nama database | - |
| `MB_DB_USER` | Username database | - |
| `MB_DB_PASS` | Password database | - |
| `JAVA_TIMEZONE` | Zona waktu Java | `Asia/Jakarta` |

### Koneksi Database

- **MB_DB_HOST**: Gunakan `host.docker.internal` untuk terhubung ke database yang berjalan di host. Untuk container Docker lain, gunakan nama service.
- **MB_DB_PORT**: Port default PostgreSQL adalah `5432`.

## Perintah

```bash
# Menjalankan Metabase
docker-compose up -d

# Menghentikan Metabase
docker-compose down

# Melihat log
docker-compose logs -f

# Merestart Metabase
docker-compose restart
```

## Health Check

Container menyertakan health check yang memverifikasi API Metabase merespons. Anda dapat memeriksa status dengan:

```bash
docker-compose ps
```

## Persistence Data

Konfigurasi ini menggunakan database PostgreSQL eksternal. Tidak ada volume lokal yang di-mount untuk persistence data. Pastikan database eksternal Anda di-backup dengan baik.

## Lisensi

Lihat file [LICENSE](LICENSE) untuk detail.
