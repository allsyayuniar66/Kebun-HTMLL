# Revisi Buku Pembantu, Harga Jual, HPP, dan Urutan Menu

## Perubahan
1. Menambahkan tiga kartu buku pembantu piutang (PIU-001 s.d. PIU-003) dan tiga kartu buku pembantu utang (UTG-001 s.d. UTG-003). Nama awal Pelanggan/Pemasok 1–3 dapat diubah melalui menu Relasi.
2. Kode relasi dibuat otomatis saat relasi baru disimpan. Form tidak lagi meminta pengguna mengetik kode. Pada transaksi, pengguna memilih nama relasi; sistem menyimpan kode terkait.
3. Mengatur harga jual master produk:
   - Panen Lahan 1: Rp2.000/kg
   - Panen Lahan 2: Rp1.750/kg
   - Panen Lahan 3: Rp2.100/kg
   - Panen Lahan 4: Rp4.000/kg
   - Panen Lahan 5: Rp3.200/kg
4. Untuk transaksi barang keluar/penjualan, harga jual diambil otomatis dari Master Produk. Kebijakan HPP saldo awal kemudian diperbarui pada revisi `CHANGELOG_REVISI_HPP_MARGIN_1000.md`: HPP standar ditetapkan sebesar harga jual dikurangi Rp1.000/kg dan tetap mengalir melalui lapisan FIFO.
5. Memindahkan menu Jurnal Penutup ke bawah Neraca pada navigasi.

## Catatan akuntansi
Catatan pembaruan: sesuai permintaan berikutnya, biaya lapisan saldo awal telah disesuaikan menjadi harga jual dikurangi Rp1.000/kg. Untuk pembelian persediaan baru, sistem perpetual FIFO tetap menggunakan biaya perolehan aktual pada saat pembelian.

Migrasi data `0003_party_auto_codes_and_sale_prices` mengisi enam relasi awal dan harga jual untuk database baru maupun database yang belum memiliki nilai harga jual.
