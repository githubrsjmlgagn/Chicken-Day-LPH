# Penjualan Item — CD

Webapp client-side (PWA, local-first) untuk input penjualan per item, rekonsiliasi dengan struk harian Casio, dan export Excel untuk dikirim ke pusat.

## Isi folder
- `index.html` — aplikasi utama
- `menu.js` — data 561 menu (nama, harga, channel toko/ojol, kategori)
- `manifest.json` — konfigurasi PWA
- `sw.js` — service worker (cache offline)
- `icon-192.png`, `icon-512.png` — ikon aplikasi

## Cara deploy ke GitHub Pages
1. Buat repo baru di GitHub (mis. `cda-penjualan`).
2. Unggah semua file di folder ini ke root repo.
3. Settings > Pages > Source: branch `main`, folder `/root`. Simpan.
4. Buka URL yang diberikan (mis. `https://username.github.io/cda-penjualan/`).
5. Di HP outlet: buka URL, lalu "Add to Home Screen" agar jadi seperti aplikasi.

## ATURAN PENTING (operasional)
Setiap kali ADA FILE yang diedit, NAIKKAN angka versi cache di `sw.js`:
`const CACHE = 'cda-penjualan-v1';` → `...-v2`, dst.
Jika tidak, HP staf akan tetap memuat versi lama dari cache.

## Cara pakai (staf)
1. Tab **Input**: cari menu (ketik nama), tap untuk menambah ke nota berjalan, atur qty.
   - Tombol **Toko / Ojol (G)** memilih daftar harga.
   - Tekan **Simpan nota** setiap satu nota/pesanan selesai (input dicicil sepanjang hari).
2. Tab **Transaksi**: lihat semua nota hari ini, hapus jika salah.
3. Tab **Rekonsiliasi**: isi total omzet & jumlah nota dari struk harian mesin (Z report).
   - Jika **✓ Cocok** → tekan **Export Excel** → kirim file ke pusat (WhatsApp).
   - Jika **✗ Belum cocok** → perbaiki input di tab Transaksi.

## Data
- Tersimpan di LocalStorage per tanggal (ganti tanggal di pojok kanan atas header).
- Data terikat ke perangkat & browser. Export Excel adalah arsip/backup utama.
