## 📌 Tentang Proyek

Repositori ini dibuat sebagai bagian dari tugas besar mata kuliah **Integrasi Aplikasi Enterprise** di Telkom University oleh **kelompok GTW1 dan GTW2**. Proyek ini membangun sistem informasi kesehatan berbasis **arsitektur microservices** yang dibagi menjadi dua bagian utama:

1. **Sistem Manajemen Informasi Kesehatan**, terdiri dari layanan:

   * **Data Individu**
   * **Rekam Medis**

2. **Sistem Pelayanan Kesehatan**, terdiri dari layanan:

   * **Rawat Jalan**
   * **Rawat Inap**
   * **Resep dan Distribusi Obat**

Seluruh layanan dihubungkan melalui sebuah **landing page** yang berfungsi sebagai portal utama untuk mengakses sistem manajemen maupun pelayanan.

---

## ✨ Fitur Utama

* ✉ Landing Page HTML sebagai portal layanan.
* ⚙ Layanan microservice modular:

  * Data Individu
  * Rekam Medis
  * Rawat Jalan
  * Rawat Inap
  * Resep Obat
* ♻ Integrasi GraphQL antar service.
* ☑ Siap deploy via Docker Compose atau Railway/Fly.io.

---

## 📁 Struktur Project

```
iae-gtw/
├── public/                    # Landing page (index.html)
├── server.js                  # Express server
├── Dockerfile                 # Untuk root landing page
├── docker-compose.yml         # Multi-service Docker setup
├── data-individu-service/     # Microservice Data Individu
├── rekam-medis-service/       # Microservice Rekam Medis
├── rawat-jalan-service/       # Microservice Rawat Jalan
├── rawat-inap-service/        # Microservice Rawat Inap
└── resep-service/             # Microservice Resep
```

---

## 🚀 Jalankan Secara Lokal

### Persiapan:

* Pastikan Docker & Docker Compose sudah terinstall.

### Langkah-langkah:

```bash
git clone https://github.com/fathyaa/iae-gtw.git
cd iae-gtw
git checkout run-local-dev
docker-compose up --build
```

### Akses:

* [http://localhost](http://localhost) → Landing Page
* [http://localhost:8000/graphql](http://localhost:8000/graphql) → Data Individu
* [http://localhost:8001/graphql](http://localhost:8001/graphql) → Rekam Medis
* [http://localhost:8002/graphql](http://localhost:8002/graphql) → Resep Obat
* [http://localhost:8003/graphql](http://localhost:8003/graphql) → Rawat Inap
* [http://localhost:8004/graphql](http://localhost:8004/graphql) → Rawat Jalan

> Jika service lambat saat diakses pertama kali, tunggu proses initial build container selesai.

---

## 🌐 Production Env

### Akses:

* [http://iae-gtw-production.up.railway.app](http://iae-gtw-production.up.railway.app) → Landing Page

---

## ⚡ Integrasi Antar Layanan

Tiap service saling berkomunikasi melalui GraphQL. Contoh:

* `rekam-medis-service` membutuhkan data dari:

  * `data-individu-service`
  * `rawat-inap-service`
  * `rawat-jalan-service`

* `resep-service` membutuhkan data dari:

  * `data-individu-service`

Konfigurasi URL layanan antar service diatur melalui environment variable di `docker-compose.yml`.

---

## 🎯 Tujuan Proyek

Memberikan contoh nyata bagaimana membangun sistem informasi kesehatan yang:

* Modular dan terpisah sesuai domain.
* Bisa dikembangkan tim berbeda.
* Mudah dideploy dan diuji.
