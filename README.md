# NilamKu

Aplikasi pencatatan minyak nilam: penyulingan, stok, penjualan, biaya, dan untung bersih. Berjalan di browser — bisa dipasang seperti aplikasi di Android, laptop, dan PC, serta tetap terbuka tanpa internet.

Situs: https://nilamku-qn22ss.freebuff.site

## Fitur

- **Penyulingan** — catat daun basah dan minyak hasil; rendemen dihitung otomatis; biaya kayu bakar, upah, dan transport.
- **Penjualan** — pembeli, berat, harga per kg, metode bayar (tunai, transfer, DANA, OVO, GoPay, QRIS), status lunas/utang, dan tombol "Minta bayar" yang menyusun tagihan WhatsApp.
- **Ringkasan** — stok, produksi, rendemen, pendapatan, biaya, dan untung bersih.
- **Grafik bulanan** — produksi vs penjualan (kg) dan untung bersih (Rp).
- **Pengguna & peran** — user biasa, user profesional, admin.

## Masuk pertama kali

- Nama pengguna: `fajri`
- PIN: `12345`

Segera ganti PIN lewat tab **Pengguna → Ganti PIN**.

### Hak akses

| Peran | Boleh |
| --- | --- |
| User biasa | Catat penyulingan (tanpa biaya) dan penjualan, lihat stok/produksi/rendemen, grafik produksi |
| User profesional | Semua di atas + biaya, pendapatan, utang, laba, grafik laba, hapus catatan, cadangan data |
| Admin | Semua di atas + kelola pengguna + hapus seluruh data |

## Struktur

```
public/            berkas aplikasi yang ditayangkan
  index.html       seluruh aplikasi (HTML + CSS + JS)
  manifest.json    manifest PWA
  sw.js            service worker (offline)
  icon.svg         ikon aplikasi
worker.js          worker statis untuk hosting
site.manifest.json konfigurasi deploy
```

## Menjalankan lokal

```bash
cd public
python3 -m http.server 3000
```

Buka http://localhost:3000

## Catatan penting

- Data disimpan di `localStorage` perangkat, **tidak** dikirim ke server. Karena itu data di HP dan laptop terpisah; gunakan tab **Data → Unduh cadangan** untuk memindahkan.
- PIN hanya gerbang sederhana di perangkat, bukan autentikasi server. Untuk login aman dan data bersama antar perangkat, perlu backend (database + autentikasi).
- Untuk pembayaran otomatis lewat DANA/OVO/GoPay, perlu akun payment gateway (mis. Midtrans/Xendit) dan server sebagai perantara.
