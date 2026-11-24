# Perubahan parser jurnal, COA, dan perpetual

- Memperluas COA standar usaha pertanian menjadi 114 kode akun, mencakup aset lancar, pajak, aset tetap/biologis/takberwujud, liabilitas, ekuitas, pendapatan, dan beban lebih terperinci.
- Memperluas pengenalan uraian untuk aset tetap, pembayaran di muka, perlengkapan, pupuk/bahan produksi, utilitas, sewa, gaji, panen/pengolahan/distribusi, modal, pinjaman, pendapatan jasa, dan bunga.
- Menambahkan kata pembayaran non-tunai seperti QRIS, giro, dan mobile banking sebagai penyelesaian melalui bank.
- Nama produk master saja tidak lagi memaksa transaksi menjadi mutasi stok. Pembelian pupuk/bibit untuk pemakaian sendiri dapat masuk beban budidaya; mutasi FIFO otomatis membutuhkan produk dan kuantitas, sedangkan stok untuk dijual harus dinyatakan secara eksplisit.
- Memperjelas bahwa bibit/benih yang disebut untuk ditanam sendiri dipetakan sebagai biaya budidaya, bukan otomatis barang dagang.
- Memperbaiki diskon pembelian: diskon yang diketahui saat pembelian langsung mengurangi biaya perolehan akun aset/persediaan dalam metode perpetual; tidak diposting ke akun kontra-pembelian periodik. Diskon saat pelunasan utang persediaan ditolak sampai sistem dapat memperbarui lapisan FIFO.
- Retur persediaan dan retur penjualan ditolak oleh parser umum sampai tersedia alur yang mengaitkan bukti asal, kuantitas, kondisi barang, dan lapisan FIFO; ini mencegah jurnal parsial yang membuat kartu stok dan buku besar berbeda.
- Menambahkan pengujian klasifikasi transaksi nonpersediaan dan pembelian aset.
- Tidak mengubah halaman, menu, tampilan, alur ekspor, dan fungsi lain yang tidak terkait.

## Penerapan

Setelah mengekstrak ZIP, jalankan `python manage.py migrate` lalu `python manage.py seed_agriculture`. Perintah seed menambah COA tanpa mengubah saldo awal akun yang sudah ada. Lakukan backup database sebelum menerapkan ke database operasional.
