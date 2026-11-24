# Kebijakan Chart of Accounts, Jurnal Otomatis, dan SAK

## Prinsip penting

- SAK Indonesia tidak menetapkan satu daftar nomor akun wajib yang sama untuk semua entitas. Kode di aplikasi adalah rancangan COA internal dan dapat disesuaikan dengan kebijakan entitas.
- Pilih kerangka yang sesuai dengan kriteria entitas (misalnya SAK EMKM atau SAK Entitas Privat). SAK tidak dapat dinyatakan otomatis terpenuhi hanya karena aplikasi memakai akun tertentu.
- Metode persediaan perpetual mencatat pembelian barang dagang ke Persediaan. Ketika barang dijual, sistem mencatat pendapatan dan sekaligus Debit HPP/Kredit Persediaan berdasarkan lapisan biaya FIFO.
- Pembelian aset tetap dicatat sebagai aset, bukan beban langsung. Penyusutan dan pelepasan aset memerlukan umur manfaat, nilai residu, akumulasi penyusutan, dan nilai tercatat yang benar.
- Pembelian pupuk, pestisida, benih, dan bahan produksi untuk digunakan sendiri dapat dicatat sebagai persediaan bahan atau beban sesuai kebijakan dan kapan bahan digunakan. Barang yang dibeli untuk dijual kembali masuk persediaan barang dagang.
- Diskon pembelian yang diketahui saat pengakuan awal mengurangi biaya perolehan aset/persediaan. Diskon saat pelunasan utang yang berkaitan dengan persediaan perlu menyesuaikan lapisan FIFO; parser saat ini menolak transaksi tersebut sampai alur pembaruan lapisan tersedia. Akun 5120 adalah akun historis/nonperpetual dan tidak dipakai oleh parser perpetual.
- Secara prinsip, retur pembelian barang dagang dalam metode perpetual mengurangi Persediaan. Retur penjualan yang benar-benar mengembalikan barang perlu menambah kembali Persediaan dan membalik HPP. Karena retur memerlukan referensi bukti asal, kuantitas, kondisi barang, dan pembaruan lapisan FIFO, parser saat ini menolak retur otomatis agar tidak menghasilkan jurnal parsial.

## Kelompok COA

Jalankan `python manage.py seed_agriculture` untuk menambahkan/melengkapi 114 akun standar usaha pertanian dan perdagangan hasil tani. Perintah bersifat idempoten: akun yang sudah ada tidak dibuat ganda dan saldo awal yang ada tidak diubah.

Kelompok akun mencakup:
- Aset: kas/bank, piutang, cadangan kerugian piutang, persediaan barang/bahan, perlengkapan, pembayaran di muka, pajak dibayar di muka, tanah, bangunan, mesin, kendaraan, inventaris, aset biologis, aset hak guna, dan aset takberwujud.
- Liabilitas: utang usaha/nonusaha, pinjaman, pajak, gaji, beban akrual, uang muka pelanggan, provisi, dan liabilitas sewa.
- Ekuitas: modal, saldo laba, prive, tambahan modal, dan penghasilan komprehensif lain.
- Pendapatan, kontra-pendapatan, HPP, beban operasional, pendapatan lain, dan beban lain.

## Contoh pemetaan jurnal otomatis

| Transaksi | Debet | Kredit |
|---|---|---|
| Pembelian persediaan tunai | Persediaan | Kas |
| Pembelian persediaan kredit | Persediaan | Utang Usaha |
| Penjualan persediaan tunai | Kas | Penjualan; HPP | Persediaan |
| Pembelian mesin tunai | Mesin dan Peralatan | Kas |
| Pembelian perlengkapan tunai | Perlengkapan | Kas |
| Pembelian pupuk untuk digunakan sendiri | Beban Pupuk dan Pestisida | Kas/Utang |
| Pembayaran listrik | Beban Utilitas | Kas/Utang |
| Pembayaran gaji | Beban Gaji | Kas/Utang |
| Setoran modal | Kas/Bank | Modal |
| Penerimaan pinjaman | Kas/Bank | Utang Pinjaman |
| Pembayaran pokok pinjaman | Utang Pinjaman | Kas/Bank |
| Pendapatan jasa | Kas/Bank/Piutang | Pendapatan Jasa |

## Batasan dan pengendalian

- Sistem mengklasifikasikan transaksi berdasarkan frasa uraian. Selalu periksa pratinjau akun dan saldo debet/kredit sebelum menyimpan.
- Keterangan seperti "pembelian" atau "penjualan" saja tidak cukup untuk menentukan akun; objek dan cara penyelesaian harus disebutkan.
- Transaksi pajak (termasuk PPN/PPh), akrual, penyusutan, penurunan nilai, hibah, aset biologis, transaksi mata uang asing, pelepasan aset tetap, dan transaksi campuran dapat memerlukan informasi tambahan. Jangan memaksakan transaksi kompleks melalui parser sederhana.
- Bila sistem tidak dapat menentukan klasifikasi secara aman, transaksi ditolak. Gunakan jurnal manual/penyesuaian dengan akun dan dokumen pendukung yang benar.
- Nomor akun, kebijakan kapitalisasi, pengakuan beban, dan perlakuan pajak harus disetujui penanggung jawab akuntansi sesuai fakta transaksi dan standar yang berlaku.
