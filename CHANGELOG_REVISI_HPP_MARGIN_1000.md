# Revisi HPP dengan laba kotor Rp1.000/kg

## Harga produk
| Produk | Harga jual/kg | HPP/kg | Laba kotor/kg |
|---|---:|---:|---:|
| Panen Lahan 1 | Rp2.000 | Rp1.000 | Rp1.000 |
| Panen Lahan 2 | Rp1.750 | Rp750 | Rp1.000 |
| Panen Lahan 3 | Rp2.100 | Rp1.100 | Rp1.000 |
| Panen Lahan 4 | Rp4.000 | Rp3.000 | Rp1.000 |
| Panen Lahan 5 | Rp3.200 | Rp2.200 | Rp1.000 |

HPP saldo awal FIFO diubah sesuai harga jual dikurangi Rp1.000/kg. Penjualan tetap menggunakan metode perpetual FIFO. Ketika transaksi penjualan dicatat melalui menu Transaksi Persediaan, sistem membuat jurnal penjualan dan jurnal HPP secara otomatis: Debit Kas/Piutang, Kredit Penjualan; Debit HPP (5110), Kredit Persediaan (1150). Untuk pembelian stok berikutnya, FIFO tetap memakai biaya perolehan aktual dari transaksi pembelian; karena itu margin Rp1.000/kg berlaku pada harga jual standar terhadap HPP standar saldo awal, bukan jaminan margin untuk pembelian baru yang memiliki biaya aktual berbeda.

Migrasi `0004_hpp_margin_seribu` memperbarui lapisan saldo awal dan saldo awal akun Persediaan serta Modal secara seimbang. Mutasi pembelian berikutnya tidak diubah.
