# Sistem Informasi Absensi & Monitoring Prakerin

Aplikasi berbasis Vue.js 3 + Express.js + MySQL (XAMPP), disusun mengikuti rancangan dashboard Admin, Guru, dan Siswa yang diberikan.

## Persyaratan
- Node.js 18 atau lebih baru
- XAMPP dengan MySQL/MariaDB aktif
- Browser modern

## 1. Instalasi database
1. Jalankan XAMPP Control Panel, aktifkan **Apache** dan **MySQL**.
2. Buka `http://localhost/phpmyadmin`.
3. Pilih menu **Import**, pilih file `mysql/db_prakerin.sql`, lalu klik **Import**.
4. Database `db_prakerin` beserta tabel dan data contoh akan dibuat.

## 2. Jalankan backend Express
Buka terminal pada folder `backend`, lalu jalankan:

```bash
npm install
```
Salin `.env.example` menjadi `.env`. Sesuaikan konfigurasi database jika username/password MySQL berbeda. Default XAMPP biasanya user `root` dan password kosong.

```bash
npm run dev
```
API berjalan di `http://localhost:3000`. Tes status di `http://localhost:3000/api/health`.

## 3. Jalankan frontend Vue
Buka terminal baru pada folder `frontend`:

```bash
npm install
npm run dev
```
Buka alamat yang ditampilkan Vite (umumnya `http://localhost:5173`). Frontend mengakses API `http://localhost:3000/api`.

Jika backend ditempatkan di alamat lain, buat file `frontend/.env` dari `.env.example` dan isi `VITE_API_URL`.

## Akun demo
Semua akun demo menggunakan password: **password**

| Peran | Username | Password |
|---|---|---|
| Admin | `admin` | `password` |
| Guru | `guru1` | `password` |
| Siswa | `budi` | `password` |
| Siswa | `siti` | `password` |

## Fitur yang tersedia
- Login berbasis peran dan token JWT.
- Admin: tambah, lihat, ubah, dan hapus data siswa/guru/DU-DI/akun melalui API; melihat absensi dan laporan.
- Guru: melihat siswa bimbingan, memantau absensi dan jurnal, menyetujui/revisi jurnal dan pengajuan izin, melihat rekap.
- Siswa: mencatat absensi masuk/pulang, mengirim jurnal harian, mengajukan izin, melihat riwayat absensi dan profil.
- Cetak halaman laporan melalui dialog Print browser (pilih Save as PDF).

## Catatan pengembangan
- Form tambah data telah disediakan. Endpoint API juga menyediakan `PUT` untuk memperbarui dan `DELETE` untuk menghapus resource admin; antarmuka edit/hapus dapat dikembangkan sesuai kebijakan sekolah.
- ID guru dan ID DU/DI pada form siswa merujuk pada ID yang tampil pada daftar data terkait.
- Untuk penggunaan produksi, ganti `JWT_SECRET`, gunakan HTTPS, buat password unik, batasi CORS, validasi input lebih ketat, dan siapkan backup database rutin.
- Akun demo dan data contoh wajib diganti sebelum aplikasi digunakan dengan data siswa sebenarnya.
