# Revisi Metode Perpetual dan Nomor Bukti

## Metode persediaan
- Modul transaksi persediaan menggunakan metode perpetual dengan aliran biaya FIFO.
- Barang masuk langsung mendebit Persediaan dan mengkredit Kas/Bank atau Utang.
- Barang keluar otomatis mencatat Kas/Bank atau Piutang, Penjualan, HPP, dan pengurangan Persediaan berdasarkan alokasi FIFO.
- Penjualan/pembelian barang dagang melalui jurnal otomatis umum diarahkan ke menu Transaksi Persediaan agar kuantitas dan HPP tidak terlewat.
- Tidak mengubah model data atau database; transaksi dan saldo yang sudah ada dipertahankan.

## Nomor bukti otomatis
- BKM: penerimaan kas/bank.
- BKK: pengeluaran kas/bank.
- FJ: faktur penjualan kredit.
- FP: faktur pembelian kredit.
- JU: jurnal umum lainnya.
- JP: jurnal penyesuaian.
- Jurnal penutup tetap memakai nomor TUTUP yang sudah ada.
- Nomor berjalan otomatis per prefix: BKM 01, BKM 02, dan seterusnya.
- Transaksi stok saldo awal tetap memakai referensi AWAL per kode produk.
