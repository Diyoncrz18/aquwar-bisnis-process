# DOKUMEN KEBUTUHAN DAN RANCANGAN SISTEM

## Sistem Manajemen Penjualan, Produksi, Persediaan, dan Barang Reject

**Nama Proyek:** Sistem Manajemen Operasional Aquar dan Es Kristal
**Nama Perusahaan:** AQUWAR

---

# 1. Pendahuluan

Dokumen ini menjelaskan kebutuhan, ruang lingkup, alur kerja, hak akses pengguna, serta fitur-fitur utama yang akan dikembangkan untuk mendukung kegiatan operasional perusahaan yang bergerak dalam produk air minum Aquar, es kristal, dan tangki air.

Sistem akan dibangun dalam bentuk aplikasi berbasis web yang dapat diakses melalui komputer, laptop, tablet, maupun telepon seluler. Sistem ini bertujuan untuk menghubungkan proses penjualan, pembuatan invoice, produksi, persediaan barang jadi, persediaan bahan baku, pencatatan barang reject, serta penyajian laporan kepada pemilik usaha.

Pemesanan pelanggan dapat dibuat langsung melalui sistem oleh Tim Operasional atau diterima melalui WhatsApp. Pesanan yang dibuat langsung melalui sistem dicatat oleh Tim Operasional pada menu pesanan atau invoice. Pesanan yang diterima melalui WhatsApp harus dikonfirmasi terlebih dahulu, kemudian datanya diinput secara manual oleh Tim Operasional ke dalam sistem.

Sistem tidak secara otomatis mencatat seluruh pesan WhatsApp sebagai transaksi. Hal ini dilakukan untuk mencegah pesanan fiktif, pesanan yang belum dikonfirmasi, perubahan pesanan, serta pembatalan pesanan memengaruhi stok dan laporan penjualan.

## 1.1 Kesepakatan Utama Bersama Client

Pembahasan dengan client menetapkan ketentuan berikut sebagai dasar pengembangan sistem:

1. **Website company profile** menjadi halaman publik yang menampilkan produk Aquar, es kristal, dan tangki air, spesifikasi produk, foto pabrik, informasi kontak, serta tombol WhatsApp.
2. **Pemesanan pelanggan dilakukan melalui WhatsApp.** Pesan WhatsApp tidak diubah secara otomatis menjadi transaksi agar pesanan fiktif, perubahan pesanan, dan pembatalan tidak memengaruhi data operasional maupun performa website. Setelah pelanggan menyetujui pesanan, Tim Operasional menginput data tersebut secara manual ke sistem.
3. **Invoice merupakan dasar pembukuan dan pengeluaran barang.** Invoice mencatat pelanggan, produk, jumlah, harga, biaya pengiriman, dan detail transaksi dengan format/template perusahaan. Invoice berstatus Draft tidak mengubah stok. Setelah invoice dikonfirmasi, stok tersedia langsung berkurang melalui reservasi. Contoh: stok fisik 1.500 dos dan invoice dikonfirmasi untuk 500 dos menghasilkan stok tersedia 1.000 dos. Stok fisik baru berkurang ketika seluruh barang dikirim.
4. **Bahan baku Aquar berkurang saat produksi dicatat, bukan saat invoice penjualan dibuat.** Produksi 2 dos Aquar membutuhkan 96 cup, 96 lid, 96 sedotan, 2 kardus, dan lem sesuai formula. Pesanan pelanggan mengurangi stok barang jadi yang tersedia, sedangkan produksi mengurangi bahan baku; pemisahan ini mencegah pengurangan stok dua kali. Sistem mengonversi bahan baku yang diterima dalam kemasan besar, misalnya 1 kemasan berisi 38.000 cup, ke satuan dasar pemakaian dan memberi warning ketika stok menipis.
5. **Reject dicatat langsung oleh karyawan yang berwenang melalui sistem.** Data reject minimal mencatat produk atau bahan, jumlah, penyebab, lokasi, dan catatan/foto bukti apabila diwajibkan. Barang yang rusak dipisahkan dari stok layak jual. Barang pengganti untuk pelanggan tetap mengurangi stok, tetapi dicatat sebagai transaksi pengganti dan tidak menambah omzet.

---

# 2. Latar Belakang

Saat ini, sebagian besar proses penjualan dan operasional perusahaan masih dilakukan melalui komunikasi WhatsApp dan pencatatan manual.

Pelanggan menghubungi perusahaan melalui WhatsApp untuk menanyakan produk, harga, ketersediaan barang, serta melakukan pemesanan. Setelah pesanan diterima, data pesanan, invoice, barang keluar, produksi, penggunaan bahan baku, dan barang rusak perlu dicatat secara terpisah.

Kondisi tersebut berpotensi menimbulkan beberapa masalah, seperti:

* Pesanan pelanggan terlewat atau tidak tercatat.
* Data pelanggan tersebar di dalam percakapan WhatsApp.
* Kesalahan pencatatan jumlah produk dan harga.
* Invoice dibuat dengan format yang tidak seragam.
* Stok barang jadi tidak sesuai dengan kondisi fisik.
* Penggunaan bahan baku produksi masih dihitung secara manual.
* Bahan baku dapat habis tanpa diketahui lebih awal.
* Barang reject belum dicatat secara terstruktur.
* Barang pengganti berpotensi tercatat sebagai penjualan.
* Pemilik sulit mendapatkan laporan operasional secara cepat.
* Perbedaan data antara bagian penjualan, gudang, dan produksi.
* Sulit mengetahui siapa yang melakukan perubahan data.
* Sulit mengetahui jumlah kerugian akibat barang rusak atau reject.

Oleh karena itu, perusahaan membutuhkan sebuah sistem terintegrasi yang dapat mencatat dan menghubungkan seluruh aktivitas operasional tersebut.

---

# 3. Permasalahan yang Akan Diselesaikan

## 3.1 Pemesanan Belum Tercatat Secara Terpusat

Pesanan pelanggan dapat dibuat langsung melalui sistem atau diterima melalui WhatsApp. Tanpa sistem pencatatan yang terpusat, pesanan dapat terlewat, tercatat lebih dari satu kali, atau memiliki informasi yang tidak lengkap.

Sistem akan membantu Tim Operasional mencatat pesanan langsung di dalam sistem. Untuk pesanan yang berasal dari WhatsApp, Tim Operasional wajib menginput data pesanan secara manual setelah pesanan dikonfirmasi ke dalam satu database.

---

## 3.2 Pembukuan dan Invoice Belum Terintegrasi

Invoice menjadi dasar utama pencatatan transaksi dan pembukuan perusahaan.

Tanpa sistem invoice yang terpusat, perusahaan dapat mengalami kesulitan dalam:

* Mengetahui total penjualan.
* Mengetahui invoice yang sudah atau belum dibayar.
* Mengetahui jumlah barang yang keluar.
* Mencocokkan transaksi dengan stok.
* Menelusuri riwayat pembelian pelanggan.
* Membuat laporan penjualan.

Sistem akan menyediakan pembuatan invoice dengan nomor invoice otomatis dan format yang seragam.

---

## 3.3 Stok Barang Jadi Belum Diperbarui Secara Otomatis

Setiap transaksi penjualan perlu memengaruhi jumlah stok barang jadi.

Sebagai contoh, jika stok Aquar yang tersedia sebanyak 1.500 dos dan terdapat pesanan sebanyak 500 dos, maka sistem harus mencatat bahwa stok yang masih tersedia adalah 1.000 dos.

Namun, untuk menghindari kesalahan akibat invoice yang masih berupa draft atau pesanan yang dibatalkan, sistem akan menggunakan mekanisme reservasi stok.

Mekanismenya adalah sebagai berikut:

* Invoice berstatus **Draft** tidak mengubah stok.
* Invoice berstatus **Dikonfirmasi** akan mereservasi stok.
* Saat barang dikirim, stok fisik akan berkurang.
* Jika invoice dibatalkan sebelum pengiriman, stok reservasi akan dikembalikan.
* Jika transaksi dibatalkan setelah barang keluar, proses harus dilakukan melalui retur atau penyesuaian stok.

---

## 3.4 Penggunaan Bahan Baku Masih Dihitung Manual

Produksi Aquar menggunakan beberapa bahan baku, seperti:

* Cup.
* Plastik penutup atau lid.
* Sedotan.
* Kardus.
* Lem.

Setiap kali Tim Produksi mencatat hasil produksi, sistem harus mengurangi bahan baku secara otomatis berdasarkan formula produk.

---

## 3.5 Belum Ada Peringatan Stok Menipis

Perusahaan membutuhkan informasi lebih awal ketika bahan baku atau barang jadi mendekati batas minimum.

Tanpa peringatan tersebut, proses produksi dapat berhenti karena salah satu bahan baku telah habis.

Sistem akan memberikan peringatan pada dashboard jika:

* Stok bahan baku berada di bawah batas minimum.
* Stok barang jadi berada di bawah batas minimum.
* Bahan baku tidak mencukupi untuk rencana produksi.
* Stok menjadi negatif.
* Terdapat perbedaan hasil stock opname.

---

## 3.6 Barang Reject Belum Dicatat Secara Terstruktur

Barang reject dapat terjadi dalam beberapa tahap, antara lain:

* Saat proses produksi.
* Saat penyimpanan di gudang.
* Saat proses muat barang.
* Saat pengiriman.
* Saat dibawa oleh sopir canvassing.
* Saat barang diterima pelanggan.

Contoh barang reject meliputi:

* Cup bocor.
* Lid tidak tertutup rapat.
* Sedotan rusak.
* Kardus basah.
* Kemasan rusak.
* Produk es mencair.
* Produk rusak saat pengiriman.
* Produk tidak sesuai standar kualitas.

Sistem akan menyediakan form khusus agar karyawan dapat mencatat jumlah, jenis, penyebab, lokasi kejadian, serta foto barang reject.

---

## 3.7 Barang Pengganti Berpotensi Masuk ke Omzet

Barang yang diberikan kepada pelanggan sebagai pengganti barang rusak tidak boleh dihitung sebagai penjualan baru.

Barang pengganti tetap mengurangi stok barang jadi, tetapi tidak menambah omzet perusahaan.

Sistem akan membedakan transaksi berikut:

* Penjualan.
* Barang pengganti.
* Retur pelanggan.
* Barang reject.
* Barang bonus.
* Barang sampel.
* Pemakaian internal.
* Penyesuaian stok.

---

# 4. Tujuan Sistem

Sistem ini dikembangkan dengan tujuan:

1. Memusatkan seluruh data operasional perusahaan.
2. Mempermudah pembuatan pesanan langsung melalui sistem dan pencatatan manual pesanan dari WhatsApp.
3. Mempermudah pembuatan dan pencetakan invoice.
4. Menyediakan data stok barang jadi secara real-time.
5. Mengurangi bahan baku secara otomatis berdasarkan hasil produksi.
6. Menambah stok barang jadi secara otomatis berdasarkan hasil produksi.
7. Memberikan peringatan ketika stok mulai menipis.
8. Mencatat barang reject secara terstruktur.
9. Memisahkan barang pengganti dari transaksi penjualan.
10. Mengurangi risiko kesalahan pencatatan manual.
11. Menyediakan laporan yang transparan kepada Owner.
12. Mengetahui riwayat aktivitas setiap pengguna.
13. Membantu perusahaan mengambil keputusan berdasarkan data.
14. Menyediakan informasi produk melalui website company profile.
15. Meningkatkan profesionalitas perusahaan di hadapan pelanggan.

---

# 5. Ruang Lingkup Sistem

Sistem akan terdiri atas dua bagian utama:

1. Website publik atau company profile.
2. Sistem manajemen internal perusahaan.

---

# 6. Website Company Profile

Website company profile digunakan sebagai media informasi resmi perusahaan.

Website dapat diakses oleh masyarakat umum tanpa harus melakukan login.

## 6.1 Informasi yang Ditampilkan

Website akan menampilkan:

* Profil perusahaan.
* Sejarah singkat perusahaan.
* Visi dan misi.
* Informasi pabrik.
* Foto-foto pabrik.
* Informasi produk Aquar.
* Informasi produk es kristal.
* Informasi produk tangki air.
* Spesifikasi masing-masing produk.
* Ukuran atau varian produk.
* Kontak perusahaan.
* Nomor WhatsApp.
* Alamat perusahaan.
* Lokasi Google Maps, jika diperlukan.
* Jam operasional.
* Tombol pemesanan melalui WhatsApp.

---

## 6.2 Pemesanan Melalui Sistem dan WhatsApp

Kanal pemesanan yang digunakan pelanggan pada website adalah WhatsApp. Website company profile tidak menyediakan keranjang belanja, checkout, maupun konversi pesan WhatsApp menjadi transaksi secara otomatis. Tombol WhatsApp digunakan agar pelanggan dapat menghubungi perusahaan tanpa membebani website dengan proses transaksi yang belum pasti.

Pemesanan dapat dicatat melalui dua cara internal: Tim Operasional menginput pesanan yang sudah disepakati langsung ke sistem, atau Tim Operasional menginput manual pesanan yang diterima melalui WhatsApp. Istilah "pemesanan langsung melalui sistem" pada bagian ini berarti input oleh karyawan berwenang, bukan checkout otomatis oleh pelanggan di website.

### 6.2.1 Pemesanan Langsung Melalui Sistem

Tim Operasional dapat membuat pesanan langsung melalui menu pesanan atau invoice di sistem. Alurnya adalah sebagai berikut:

1. Tim Operasional login ke sistem.
2. Tim Operasional memilih atau menambahkan data pelanggan.
3. Tim Operasional memasukkan produk, jumlah, harga, alamat pengiriman, pembayaran, dan catatan pesanan.
4. Sistem membuat pesanan atau invoice berstatus Draft.
5. Setelah detail pesanan disetujui, Tim Operasional mengonfirmasi invoice.
6. Pesanan diproses sampai selesai sesuai alur invoice, pembayaran, dan pengiriman.

### 6.2.2 Pemesanan Melalui WhatsApp

Pelanggan dapat menekan tombol WhatsApp pada website untuk menghubungi perusahaan. Website dan sistem tidak langsung mencatat pesan WhatsApp tersebut sebagai transaksi.

Alur pemesanan melalui WhatsApp adalah sebagai berikut:

1. Pelanggan membuka website atau menghubungi nomor WhatsApp perusahaan.
2. Pelanggan melihat informasi produk dan menyampaikan detail pesanan melalui WhatsApp.
3. Tim Operasional mengonfirmasi produk, harga, jumlah, alamat, dan pembayaran.
4. Setelah pesanan disepakati, Tim Operasional menginput data pelanggan dan pesanan secara manual ke dalam sistem.
5. Sistem membuat pesanan atau invoice berstatus Draft.
6. Tim Operasional mengonfirmasi invoice.
7. Pesanan diproses sampai selesai.

Alur tersebut digunakan untuk mencegah pesan WhatsApp atau pesanan yang belum pasti masuk ke dalam laporan dan memengaruhi stok, serta menjaga website company profile tetap ringan karena tidak memproses transaksi atau pesan secara otomatis.

---

# 7. Pengguna Sistem

Sistem hanya akan memiliki tiga role utama:

1. Owner.
2. Tim Operasional.
3. Tim Produksi.

Setiap karyawan tetap disarankan memiliki akun masing-masing agar seluruh aktivitas dapat diketahui dan dicatat oleh sistem.

Sebagai contoh, beberapa karyawan dapat memiliki role Tim Operasional, tetapi setiap karyawan menggunakan nama pengguna dan kata sandi yang berbeda.

---

# 8. Role Owner

Owner memiliki akses tertinggi dalam sistem.

Owner bertugas melakukan pengawasan, pengaturan, pemeriksaan laporan, serta pengambilan keputusan.

## 8.1 Hak Akses Owner

Owner dapat:

---

# 7. Pengguna Sistem

Sistem hanya akan memiliki tiga role utama:

1. Owner.
2. Tim Operasional.
3. Tim Produksi.

Setiap karyawan tetap disarankan memiliki akun masing-masing agar seluruh aktivitas dapat diketahui dan dicatat oleh sistem.

Sebagai contoh, beberapa karyawan dapat memiliki role Tim Operasional, tetapi setiap karyawan menggunakan nama pengguna dan kata sandi yang berbeda.

---

# 8. Role Owner

Owner memiliki akses tertinggi dalam sistem.

Owner bertugas melakukan pengawasan, pengaturan, pemeriksaan laporan, serta pengambilan keputusan.

## 8.1 Hak Akses Owner

Owner dapat:

* Melihat dashboard keseluruhan.
* Melihat total penjualan.
* Melihat omzet.
* Melihat invoice.
* Melihat pembayaran.
* Melihat stok barang jadi.
* Melihat stok bahan baku.
* Melihat hasil produksi.
* Melihat data barang reject.
* Melihat data barang pengganti.
* Melihat data retur.
* Melihat warning stok.
* Melihat grafik penjualan.
* Melihat grafik produksi.
* Melihat produk terlaris.
* Melihat pelanggan dengan transaksi terbesar.
* Mengelola produk.
* Mengelola harga.
* Mengelola bahan baku.
* Mengelola formula produksi.
* Mengatur stok minimum.
* Mengelola akun pengguna.
* Mengaktifkan dan menonaktifkan akun.
* Melihat riwayat aktivitas pengguna.
* Menyetujui penyesuaian stok.
* Menyetujui transaksi tertentu.
* Melihat dan mengunduh laporan.
* Mengubah pengaturan perusahaan.
* Mengubah template invoice.

---

# 9. Role Tim Operasional

Tim Operasional menangani kegiatan yang berkaitan dengan pelanggan, transaksi penjualan, invoice, pembayaran, persediaan, dan pengiriman.

## 9.1 Hak Akses Tim Operasional

Tim Operasional dapat:

* Mengelola data pelanggan.
* Membuat pesanan langsung melalui sistem.
* Menginput secara manual pesanan yang diterima melalui WhatsApp.
* Membuat invoice.
* Mengubah invoice selama masih diperbolehkan.
* Membatalkan invoice sesuai prosedur.
* Mencetak invoice.
* Mengunduh invoice dalam bentuk PDF.
* Mencatat pembayaran.
* Mencatat pembayaran sebagian.
* Mengubah status pembayaran.
* Mengelola status pesanan.
* Mengelola status pengiriman.
* Melihat stok barang jadi.
* Melihat stok yang telah direservasi.
* Melihat stok yang tersedia.
* Mencatat barang keluar.
* Mencatat barang masuk.
* Mencatat penerimaan bahan baku.
* Mencatat barang pengganti.
* Mencatat retur pelanggan.
* Mencatat reject saat gudang atau pengiriman.
* Melakukan stock opname.
* Mengajukan penyesuaian stok.
* Melihat warning stok.
* Mengelola alamat pengiriman pelanggan.
* Melihat riwayat transaksi pelanggan.
* Mengunduh laporan operasional sesuai hak akses.

Tim Operasional tidak dapat mengubah formula produksi tanpa persetujuan Owner.

---

# 10. Role Tim Produksi

Tim Produksi menangani seluruh pencatatan proses produksi.

## 10.1 Hak Akses Tim Produksi

Tim Produksi dapat:

* Melihat dashboard produksi.
* Melihat daftar produk yang akan diproduksi.
* Melihat ketersediaan bahan baku.
* Menginput hasil produksi.
* Menginput tanggal produksi.
* Menginput jumlah produksi.
* Menginput shift produksi.
* Menginput penanggung jawab produksi.
* Menginput batch produksi.
* Menginput pemakaian aktual bahan baku.
* Mengonfirmasi penggunaan bahan baku.
* Mencatat hasil produksi yang baik.
* Mencatat jumlah reject produksi.
* Memilih penyebab reject.
* Mengunggah foto reject.
* Melihat warning bahan baku.
* Melihat riwayat produksi.
* Melihat formula bahan baku yang berlaku.

Tim Produksi tidak dapat melihat:

* Omzet.
* Harga jual.
* Pembayaran pelanggan.
* Laporan laba.
* Margin keuntungan.
* Informasi keuangan lainnya.

---

# 11. Modul Dashboard

Dashboard akan disesuaikan berdasarkan role pengguna.

## 11.1 Dashboard Owner

Dashboard Owner dapat menampilkan:

* Total penjualan hari ini.
* Total penjualan bulan berjalan.
* Total penjualan tahun berjalan.
* Jumlah invoice hari ini.
* Jumlah invoice belum dibayar.
* Total produksi hari ini.
* Total produksi bulan berjalan.
* Jumlah reject hari ini.
* Persentase reject.
* Stok barang jadi.
* Stok bahan baku.
* Daftar stok menipis.
* Produk paling banyak terjual.
* Pelanggan dengan pembelian terbesar.
* Grafik penjualan.
* Grafik produksi.
* Grafik reject.
* Aktivitas pengguna terbaru.

---

## 11.2 Dashboard Tim Operasional

Dashboard Tim Operasional dapat menampilkan:

* Pesanan terbaru.
* Pesanan menunggu konfirmasi.
* Invoice belum dibayar.
* Invoice dibayar sebagian.
* Pesanan siap dikirim.
* Pesanan dalam pengiriman.
* Pesanan terlambat.
* Stok barang jadi.
* Stok yang direservasi.
* Stok yang tersedia.
* Barang retur.
* Barang pengganti.
* Warning stok.

---

## 11.3 Dashboard Tim Produksi

Dashboard Tim Produksi dapat menampilkan:

* Produksi hari ini.
* Target produksi.
* Hasil produksi yang baik.
* Total reject hari ini.
* Bahan baku tersedia.
* Bahan baku menipis.
* Riwayat produksi terbaru.
* Rencana produksi.
* Perbandingan hasil produksi dan reject.

---

# 12. Modul Pelanggan

Modul pelanggan digunakan untuk menyimpan informasi pelanggan secara terpusat.

## 12.1 Data Pelanggan

Data pelanggan dapat terdiri atas:

* Kode pelanggan.
* Nama pelanggan.
* Nama toko atau perusahaan.
* Nomor WhatsApp.
* Nomor telepon.
* Alamat utama.
* Alamat pengiriman.
* Kecamatan.
* Kota atau kabupaten.
* Jenis pelanggan.
* Harga khusus.
* Metode pembayaran.
* Batas kredit.
* Catatan pelanggan.
* Status aktif atau tidak aktif.
* Tanggal pelanggan dibuat.

## 12.2 Jenis Pelanggan

Jenis pelanggan dapat dibedakan menjadi:

* Pelanggan eceran.
* Toko.
* Agen.
* Distributor.
* Pelanggan tetap.
* Pelanggan khusus.
* Pelanggan canvassing.

Jenis pelanggan dapat digunakan untuk menentukan harga atau ketentuan pembayaran.

---

# 13. Modul Produk

Modul produk digunakan untuk mengelola seluruh produk yang dijual.

## 13.1 Data Produk

Data produk dapat meliputi:

* Kode produk.
* Nama produk.
* Kategori produk.
* Varian produk.
* Satuan penjualan.
* Isi per kemasan.
* Harga jual.
* Harga khusus.
* Stok minimum.
* Foto produk.
* Deskripsi produk.
* Status aktif atau tidak aktif.

## 13.2 Kategori Produk

Kategori produk meliputi:

* Air minum Aquar.
* Es kristal.
* Tangki air.

## 13.3 Satuan Produk

Contoh satuan produk:

* Dos.
* Cup.
* Bungkus.
* Kilogram.
* Unit.
* Tangki.

Satuan setiap produk harus ditentukan secara jelas agar tidak terjadi kesalahan pencatatan.

---

# 14. Ketentuan Isi Produk Aquar

Untuk produk Aquar, telah ditentukan bahwa:

> **Satu dos Aquar berisi 48 cup.**

Ketentuan tersebut menjadi dasar sistem dalam menghitung kebutuhan bahan baku produksi.

Contoh perhitungan:

| Jumlah Produksi | Jumlah Cup |
| --------------: | ---------: |
|           1 dos |     48 cup |
|           2 dos |     96 cup |
|           5 dos |    240 cup |
|          10 dos |    480 cup |
|          50 dos |  2.400 cup |
|         100 dos |  4.800 cup |
|         500 dos | 24.000 cup |
|       1.000 dos | 48.000 cup |
|       1.500 dos | 72.000 cup |

Formula perhitungannya adalah:

```text
Jumlah cup yang dibutuhkan = Jumlah dos yang diproduksi × 48
```

Sebagai contoh:

```text
Produksi = 100 dos
Isi per dos = 48 cup

Kebutuhan cup = 100 × 48
Kebutuhan cup = 4.800 cup
```

Perhitungan yang sama dapat diterapkan untuk lid dan sedotan apabila setiap cup membutuhkan satu lid dan satu sedotan.

---

# 15. Modul Bahan Baku

Modul bahan baku digunakan untuk mencatat seluruh bahan yang diperlukan dalam proses produksi.

## 15.1 Contoh Bahan Baku Aquar

Bahan baku Aquar meliputi:

* Cup.
* Lid atau plastik penutup.
* Sedotan.
* Kardus.
* Lem.
* Air baku atau bahan lainnya jika perlu dicatat.

## 15.2 Data Bahan Baku

Data bahan baku dapat terdiri atas:

* Kode bahan baku.
* Nama bahan baku.
* Kategori.
* Satuan pembelian.
* Satuan penggunaan.
* Faktor konversi.
* Jumlah stok.
* Stok minimum.
* Harga pembelian.
* Supplier.
* Tanggal penerimaan.
* Nomor batch atau lot.
* Tanggal kedaluwarsa jika ada.
* Status bahan baku.

---

# 16. Konversi Satuan Bahan Baku

Bahan baku dapat dibeli dalam satuan besar, tetapi digunakan dalam satuan kecil.

Sebagai contoh, cup dapat dibeli dalam satu kemasan besar yang berisi 38.000 cup.

Pada saat bahan baku diterima, sistem harus mengubah jumlah tersebut ke satuan pemakaian.

Contoh:

```text
Jumlah kemasan diterima = 1 kemasan
Isi per kemasan = 38.000 cup

Stok yang masuk ke sistem = 38.000 cup
```

Jika kemudian dilakukan produksi sebanyak 100 dos Aquar:

```text
Kebutuhan cup = 100 dos × 48 cup
Kebutuhan cup = 4.800 cup
```

Maka stok cup setelah produksi adalah:

```text
Stok awal = 38.000 cup
Pemakaian = 4.800 cup

Stok akhir = 38.000 - 4.800
Stok akhir = 33.200 cup
```

Sistem harus menyimpan informasi berikut:

* Satuan pembelian.
* Isi dalam setiap satuan pembelian.
* Satuan penggunaan.
* Faktor konversi.
* Jumlah stok dalam satuan dasar.

Penggunaan satuan dasar bertujuan agar proses pengurangan stok dapat dilakukan dengan akurat.

---

# 17. Modul Formula Produksi

Formula produksi atau Bill of Materials digunakan untuk menentukan kebutuhan bahan baku setiap produk.

## 17.1 Contoh Formula Aquar

Untuk menghasilkan satu dos Aquar yang berisi 48 cup, formula awal dapat dibuat sebagai berikut:

| Bahan Baku |   Kebutuhan untuk 1 Dos |
| ---------- | ----------------------: |
| Cup        |                 48 buah |
| Lid        |                 48 buah |
| Sedotan    |                 48 buah |
| Kardus     |                  1 buah |
| Lem        | Sesuai standar produksi |

Jumlah lem perlu dikonfirmasi lebih lanjut karena dapat dicatat menggunakan satuan:

* Gram.
* Kilogram.
* Mililiter.
* Liter.
* Kemasan.
* Takaran produksi.

## 17.2 Contoh Produksi 100 Dos

Jika Tim Produksi menghasilkan 100 dos Aquar, sistem akan menghitung:

| Bahan Baku |       Formula |     Total Kebutuhan |
| ---------- | ------------: | ------------------: |
| Cup        |      100 × 48 |          4.800 buah |
| Lid        |      100 × 48 |          4.800 buah |
| Sedotan    |      100 × 48 |          4.800 buah |
| Kardus     |       100 × 1 |            100 buah |
| Lem        | 100 × standar | Berdasarkan formula |

## 17.3 Ketentuan Formula

* Formula hanya dapat diubah oleh Owner.
* Formula memiliki tanggal mulai berlaku.
* Perubahan formula tidak boleh mengubah transaksi produksi lama.
* Setiap produksi harus menggunakan formula yang aktif pada tanggal produksi.
* Sistem dapat membandingkan kebutuhan standar dengan pemakaian aktual.
* Selisih antara kebutuhan standar dan pemakaian aktual dapat dicatat sebagai waste.

---

# 18. Modul Produksi

Modul produksi digunakan oleh Tim Produksi untuk mencatat hasil produksi.

## 18.1 Alur Produksi

1. Tim Produksi login ke dalam sistem.
2. Tim Produksi membuka menu produksi.
3. Tim Produksi memilih produk.
4. Tim Produksi memasukkan jumlah yang akan diproduksi.
5. Sistem menghitung kebutuhan bahan baku.
6. Sistem memeriksa ketersediaan bahan baku.
7. Jika bahan baku mencukupi, produksi dapat dilanjutkan.
8. Jika bahan baku tidak mencukupi, sistem memberikan peringatan.
9. Tim Produksi memasukkan hasil produksi aktual.
10. Tim Produksi memasukkan jumlah reject.
11. Tim Produksi mengonfirmasi transaksi produksi.
12. Stok bahan baku otomatis berkurang.
13. Stok barang jadi otomatis bertambah.
14. Data reject tercatat secara terpisah.

## 18.2 Data Produksi

Data produksi dapat meliputi:

* Nomor produksi.
* Tanggal produksi.
* Waktu produksi.
* Produk.
* Jumlah rencana produksi.
* Jumlah hasil produksi.
* Jumlah hasil baik.
* Jumlah reject.
* Shift.
* Batch.
* Mesin yang digunakan.
* Penanggung jawab.
* Bahan baku standar.
* Bahan baku aktual.
* Catatan produksi.
* Pengguna yang melakukan input.
* Waktu data dibuat.

## 18.3 Perhitungan Hasil Produksi

Contoh:

```text
Total produksi = 100 dos
Reject produksi = 3 dos
Hasil baik = 97 dos
```

Maka sistem akan:

* Mengurangi bahan baku berdasarkan total bahan yang digunakan.
* Menambah stok barang jadi sebanyak 97 dos.
* Mencatat 3 dos sebagai reject.
* Tidak memasukkan 3 dos reject ke stok siap jual.

## 18.4 Pemisahan Produksi dan Penjualan

Pengurangan bahan baku hanya terjadi ketika transaksi produksi dikonfirmasi. Sebagai contoh, produksi 2 dos Aquar mengurangi 96 cup, 96 lid, 96 sedotan, 2 kardus, dan lem sesuai formula yang berlaku.

Invoice atau pesanan pelanggan tidak langsung mengurangi cup, lid, sedotan, kardus, atau lem. Invoice yang dikonfirmasi hanya mereservasi stok barang jadi Aquar dalam satuan dos. Ketentuan ini mencegah bahan baku terpotong dua kali apabila pesanan pelanggan kemudian dipenuhi melalui proses produksi.

---

# 19. Produksi Es Kristal

Produksi es kristal memiliki karakteristik yang berbeda dengan produksi Aquar.

Data yang perlu ditentukan bersama client meliputi:

* Satuan produksi es kristal.
* Berat setiap kemasan.
* Jumlah kemasan yang dihasilkan.
* Bahan baku yang digunakan.
* Jumlah plastik kemasan.
* Penggunaan air.
* Penggunaan bahan tambahan jika ada.
* Pencatatan es yang mencair.
* Pencatatan reject.
* Stok barang jadi.
* Masa simpan.
* Lokasi penyimpanan.

Contoh satuan es kristal:

* Bungkus.
* Kilogram.
* Karung.
* Balok.

Formula produksi es kristal akan dibuat setelah data produksi aktual diberikan oleh client.

---

# 20. Produk Tangki Air

Produk tangki air akan ditampilkan pada website company profile.

Untuk pengelolaan internal, perlu ditentukan apakah tangki air:

* Hanya ditampilkan sebagai informasi.
* Dapat dijual melalui invoice.
* Memiliki stok.
* Memiliki beberapa ukuran.
* Memiliki beberapa warna.
* Memiliki nomor seri.
* Memiliki garansi.
* Memiliki biaya pengiriman.
* Memiliki layanan instalasi.

Apabila tangki air masuk ke dalam transaksi penjualan, maka tangki air akan dikelola melalui modul produk, stok, invoice, pengiriman, retur, dan laporan.

---

# 21. Modul Invoice

Invoice menjadi dasar pencatatan transaksi penjualan.

## 21.1 Data Invoice

Invoice dapat berisi:

* Nomor invoice.
* Tanggal invoice.
* Data perusahaan.
* Data pelanggan.
* Nomor WhatsApp pelanggan.
* Alamat pelanggan.
* Alamat pengiriman.
* Daftar produk.
* Jumlah produk.
* Harga satuan.
* Diskon.
* Biaya pengiriman.
* Subtotal.
* Total tagihan.
* Metode pembayaran.
* Status pembayaran.
* Status pesanan.
* Status pengiriman.
* Catatan.
* Pengguna yang membuat invoice.

## 21.2 Status Invoice

Status invoice dapat terdiri atas:

* Draft.
* Dikonfirmasi.
* Menunggu pembayaran.
* Dibayar sebagian.
* Lunas.
* Diproses.
* Siap dikirim.
* Dalam pengiriman.
* Selesai.
* Dibatalkan.

## 21.3 Nomor Invoice

Nomor invoice harus dibuat secara otomatis dan unik.

Contoh:

```text
INV-2026-07-0001
INV-2026-07-0002
INV-2026-07-0003
```

Format nomor invoice dapat disesuaikan dengan kebutuhan perusahaan.

## 21.4 Invoice sebagai Dasar Pembukuan

Invoice merupakan dasar pembukuan dan pencatatan barang keluar. Template invoice perusahaan harus menampilkan identitas perusahaan, nomor invoice otomatis, tanggal, data pelanggan, daftar produk, jumlah, harga, diskon, biaya pengiriman, total tagihan, status pembayaran, serta catatan transaksi.

Invoice yang baru disimpan sebagai Draft belum memengaruhi stok. Ketika Tim Operasional mengonfirmasi invoice, stok barang jadi menjadi terreservasi sehingga stok tersedia langsung berkurang. Contoh: stok fisik 1.500 dos Aquar dengan invoice terkonfirmasi 500 dos menghasilkan stok tersedia 1.000 dos. Stok fisik baru berkurang saat seluruh pesanan dikirim.

---

# 22. Hubungan Invoice dan Stok

Untuk menjaga akurasi stok, sistem akan menggunakan tiga jenis stok:

1. Stok fisik.
2. Stok reservasi.
3. Stok tersedia.

Formula stok tersedia adalah:

```text
Stok tersedia = Stok fisik - Stok reservasi
```

Contoh:

```text
Stok fisik = 1.500 dos
Stok yang telah dipesan = 500 dos

Stok tersedia = 1.500 - 500
Stok tersedia = 1.000 dos
```

## 22.1 Aturan Pengurangan Stok

* Invoice Draft tidak mengubah stok.
* Invoice Dikonfirmasi menambah stok reservasi.
* Saat barang dikirim, stok fisik berkurang.
* Setelah barang dikirim, stok reservasi berkurang.
* Invoice yang dibatalkan sebelum pengiriman akan mengembalikan stok reservasi.
* Barang yang sudah dikirim tidak dapat dibatalkan langsung.
* Barang yang sudah dikirim harus diproses melalui retur jika dikembalikan.

---

# 23. Modul Pembayaran

Modul pembayaran digunakan untuk mencatat pembayaran pelanggan.

## 23.1 Metode Pembayaran

Metode pembayaran dapat berupa:

* Tunai.
* Transfer bank.
* Pembayaran sebagian.
* Tempo.
* Metode lainnya.

## 23.2 Status Pembayaran

Status pembayaran dapat terdiri atas:

* Belum dibayar.
* Dibayar sebagian.
* Lunas.
* Jatuh tempo.
* Terlambat.
* Dibatalkan.

## 23.3 Data Pembayaran

Data pembayaran dapat meliputi:

* Nomor pembayaran.
* Nomor invoice.
* Tanggal pembayaran.
* Nominal pembayaran.
* Metode pembayaran.
* Bukti pembayaran.
* Catatan.
* Pengguna yang mencatat pembayaran.

---

# 24. Modul Stok Barang Jadi

Modul stok barang jadi mencatat seluruh pergerakan produk.

## 24.1 Sumber Penambahan Stok

Stok barang jadi dapat bertambah dari:

* Hasil produksi.
* Retur pelanggan yang masih layak jual.
* Penyesuaian stok.
* Pemindahan stok.
* Koreksi data dengan persetujuan.

## 24.2 Sumber Pengurangan Stok

Stok barang jadi dapat berkurang dari:

* Penjualan.
* Barang pengganti.
* Barang reject.
* Barang bonus.
* Barang sampel.
* Pemakaian internal.
* Barang hilang.
* Penyesuaian stok.
* Pemindahan stok.

## 24.3 Riwayat Stok

Setiap pergerakan stok harus mencatat:

* Tanggal.
* Produk.
* Jenis transaksi.
* Jumlah masuk.
* Jumlah keluar.
* Stok sebelum transaksi.
* Stok setelah transaksi.
* Nomor referensi.
* Pengguna.
* Catatan.

---

# 25. Modul Stok Bahan Baku

Modul stok bahan baku mencatat:

* Stok awal.
* Penerimaan bahan baku.
* Penggunaan produksi.
* Reject bahan baku.
* Bahan baku kedaluwarsa.
* Bahan baku hilang.
* Penyesuaian stok.
* Stock opname.
* Stok akhir.

Setiap bahan baku harus memiliki batas minimum stok.

---

# 26. Warning Stok

Sistem akan memberikan warning apabila stok telah mencapai kondisi tertentu.

## 26.1 Jenis Warning

* Stok aman.
* Stok mulai menipis.
* Stok kritis.
* Stok habis.
* Stok negatif.
* Bahan tidak cukup untuk produksi.

## 26.2 Contoh

```text
Stok cup saat ini = 10.000 cup
Batas minimum = 15.000 cup
```

Sistem akan menampilkan peringatan bahwa stok cup telah berada di bawah batas minimum.

## 26.3 Pengaturan Batas Minimum

Batas minimum dapat diatur oleh Owner berdasarkan:

* Pemakaian rata-rata.
* Waktu pengiriman supplier.
* Kapasitas produksi.
* Permintaan pelanggan.
* Stok pengaman.
* Musim ramai.

---

# 27. Modul Barang Reject

Barang reject adalah barang yang rusak, tidak sesuai standar, atau tidak dapat dijual sebagai produk normal.

## 27.1 Jenis Reject

Reject dapat dibedakan menjadi:

* Reject bahan baku.
* Reject saat produksi.
* Reject saat penyimpanan.
* Reject saat pengiriman.
* Reject canvassing.
* Reject dari pelanggan.
* Produk kedaluwarsa.
* Produk hilang atau tidak ditemukan.

## 27.2 Contoh Penyebab Reject

* Cup bocor.
* Cup pecah.
* Lid tidak tertutup rapat.
* Sedotan rusak.
* Kardus basah.
* Kardus sobek.
* Kemasan kotor.
* Produk jatuh.
* Es mencair.
* Kesalahan penyimpanan.
* Kesalahan pengiriman.
* Kerusakan kendaraan.
* Kelalaian pengguna.
* Penyebab lainnya.

## 27.3 Data Reject

Data reject dapat meliputi:

* Nomor reject.
* Tanggal.
* Lokasi kejadian.
* Jenis reject.
* Produk atau bahan baku.
* Jumlah.
* Satuan.
* Penyebab.
* Penanggung jawab.
* Foto bukti.
* Catatan.
* Tindakan lanjutan.
* Status persetujuan.
* Pengguna yang membuat laporan.

---

# 28. Alur Barang Reject

Alur pencatatan barang reject adalah:

1. Karyawan menemukan barang rusak.
2. Karyawan login ke sistem.
3. Karyawan membuka menu reject.
4. Karyawan memilih produk atau bahan baku.
5. Karyawan memasukkan jumlah reject.
6. Karyawan memilih penyebab reject.
7. Karyawan mengunggah foto.
8. Karyawan menyimpan laporan.
9. Owner atau Tim Operasional melakukan pemeriksaan jika diperlukan.
10. Sistem mencatat pengurangan atau pemindahan stok.
11. Data reject masuk ke laporan.

## 28.1 Tindakan Lanjutan Reject

Setelah reject diperiksa, tindak lanjutnya harus dicatat agar barang rusak tidak kembali masuk ke stok layak jual tanpa pemeriksaan. Pilihan tindakan lanjutan dapat berupa:

* Dikemas ulang dan dikembalikan ke stok layak jual setelah lolos pemeriksaan kualitas.
* Diklaim kepada supplier apabila kerusakan berasal dari bahan baku atau kemasan dari supplier.
* Dimusnahkan atau didaur ulang apabila tidak layak diproses kembali.
* Diganti dengan barang baru untuk pelanggan melalui transaksi barang pengganti yang terpisah dari penjualan.

Setiap tindakan harus mempertahankan riwayat reject, pengguna yang mencatat, dan dampaknya terhadap stok maupun laporan kerugian.
* Produksi bulanan.
* Produksi per produk.
* Produksi per shift.
* Produksi per batch.
* Hasil baik.
* Total reject.
* Pemakaian bahan baku.

## 32.5 Laporan Stok

* Stok barang jadi.
* Stok bahan baku.
* Stok tersedia.
* Stok reservasi.
* Stok minimum.
* Stok kritis.
* Riwayat pergerakan stok.
* Hasil stock opname.

## 32.6 Laporan Reject

* Reject per periode.
* Reject per produk.
* Reject per penyebab.
* Reject per lokasi.
* Reject per shift.
* Reject per karyawan.
* Persentase reject terhadap produksi.
* Nilai kerugian reject.

## 32.7 Laporan Barang Pengganti

* Barang pengganti per pelanggan.
* Barang pengganti per produk.
* Barang pengganti per periode.
* Alasan penggantian.
* Total stok yang digunakan.
* Estimasi biaya penggantian.

## 32.8 Format Laporan

Laporan dapat:

* Dilihat melalui sistem.
* Difilter berdasarkan tanggal.
* Dicetak.
* Diunduh dalam bentuk PDF.
* Diunduh dalam bentuk Microsoft Excel (.xlsx) sesuai filter yang dipilih pengguna.

Export Excel termasuk dalam ruang lingkup tahap pertama untuk laporan penjualan,
invoice, pembayaran, stok barang jadi, stok bahan baku, produksi,
reject, retur, barang pengganti, dan stock opname.

File PDF dan Excel hanya dapat diunduh sesuai hak akses pengguna. Owner dapat
mengunduh seluruh laporan. Tim Operasional hanya dapat mengunduh laporan
operasional sesuai hak aksesnya. Tim Produksi hanya dapat mengunduh laporan
produksi, bahan baku, dan reject, serta tidak dapat mengunduh laporan omzet,
harga, HPP, margin, laba/rugi, maupun pembayaran.

---

# 33. Matriks Hak Akses

| Fitur                         | Owner | Tim Operasional | Tim Produksi |
| ----------------------------- | :---: | :-------------: | :----------: |
| Melihat dashboard keseluruhan |   Ya  |     Terbatas    |   Terbatas   |
| Melihat omzet                 |   Ya  |     Terbatas    |     Tidak    |
| Mengelola pengguna            |   Ya  |      Tidak      |     Tidak    |
| Mengelola pelanggan           |   Ya  |        Ya       |     Tidak    |
| Mengelola produk              |   Ya  |     Terbatas    |     Tidak    |
| Mengelola harga               |   Ya  |     Terbatas    |     Tidak    |
| Mengelola bahan baku          |   Ya  |        Ya       |   Terbatas   |
| Mengelola formula produksi    |   Ya  |      Tidak      |     Tidak    |
| Membuat invoice               |   Ya  |        Ya       |     Tidak    |
| Mencatat pembayaran           |   Ya  |        Ya       |     Tidak    |
| Mencatat produksi             |   Ya  |     Opsional    |      Ya      |
| Mencatat reject               |   Ya  |        Ya       |      Ya      |
| Mencatat barang pengganti     |   Ya  |        Ya       |     Tidak    |
| Mencatat retur                |   Ya  |        Ya       |     Tidak    |
| Melakukan stock opname        |   Ya  |        Ya       |   Terbatas   |
| Menyetujui penyesuaian stok   |   Ya  |      Tidak      |     Tidak    |
| Melihat laporan               |   Ya  |     Terbatas    |   Terbatas   |
| Mengunduh laporan             |   Ya  |     Terbatas    |     Tidak    |
| Melihat aktivitas pengguna    |   Ya  |      Tidak      |     Tidak    |

---

# 34. Aturan Bisnis Sistem

Aturan bisnis yang akan digunakan meliputi:

1. Pemesanan pelanggan dapat dibuat langsung melalui sistem oleh Tim Operasional atau diterima melalui WhatsApp.
2. Pesanan yang dibuat langsung melalui sistem dicatat oleh Tim Operasional sebagai pesanan atau invoice Draft dan mengikuti prosedur konfirmasi yang berlaku.
3. Pesanan dari WhatsApp baru masuk ke sistem setelah dikonfirmasi dan datanya diinput secara manual oleh Tim Operasional.
4. Pesan WhatsApp tidak otomatis menjadi transaksi.
5. Setiap invoice memiliki nomor yang unik.
6. Invoice Draft tidak memengaruhi stok.
7. Invoice Dikonfirmasi akan mereservasi stok.
8. Stok fisik berkurang ketika barang dikirim.
9. Invoice yang dibatalkan sebelum pengiriman akan mengembalikan stok reservasi.
10. Stok tidak boleh menjadi negatif tanpa persetujuan Owner.
11. Satu dos Aquar berisi 48 cup.
12. Produksi Aquar mengurangi cup, lid, sedotan, kardus, dan lem berdasarkan formula.
13. Sistem tidak dapat mengonfirmasi produksi jika bahan baku tidak mencukupi.
14. Hasil produksi yang baik akan menambah stok barang jadi.
15. Barang reject tidak menambah stok barang jadi.
16. Barang pengganti mengurangi stok tetapi tidak menambah omzet.
17. Retur harus memiliki referensi transaksi asal.
18. Penyesuaian stok harus disertai alasan.
19. Perubahan data penting harus dicatat dalam riwayat aktivitas.
20. Data transaksi lama tidak boleh dihapus secara langsung.
21. Transaksi yang salah harus dibatalkan atau dikoreksi melalui prosedur.
22. Perubahan harga tidak boleh mengubah invoice lama.
23. Perubahan formula tidak boleh mengubah data produksi lama.
24. Setiap pengguna menggunakan akun masing-masing.
25. Hak akses ditentukan berdasarkan role.
26. Tim Produksi tidak dapat melihat informasi keuangan.
27. Foto reject dapat diwajibkan untuk jumlah tertentu.
28. Reject dalam jumlah besar dapat memerlukan persetujuan Owner.
29. Stock opname harus menyimpan stok sistem dan stok fisik.
30. Semua aktivitas penting mencatat pengguna dan waktu.
31. Data laporan bersumber dari transaksi yang tercatat di sistem.

---

# 35. Audit Trail

Sistem harus mencatat riwayat aktivitas pengguna.

Riwayat tersebut dapat memuat:

* Nama pengguna.
* Role pengguna.
* Tanggal.
* Waktu.
* Jenis aktivitas.
* Data sebelum perubahan.
* Data setelah perubahan.
* Alasan perubahan.
* Perangkat atau alamat IP jika diperlukan.

Aktivitas yang perlu dicatat antara lain:

* Login.
* Pembuatan invoice.
* Perubahan invoice.
* Pembatalan invoice.
* Pencatatan pembayaran.
* Input produksi.
* Perubahan formula.
* Input reject.
* Penyesuaian stok.
* Perubahan harga.
* Aktivasi atau penonaktifan pengguna.

---

# 36. Kebutuhan Nonfungsional

## 36.1 Keamanan

* Sistem menggunakan koneksi HTTPS.
* Kata sandi disimpan secara aman.
* Hak akses dibatasi berdasarkan role.
* Setiap pengguna memiliki akun sendiri.
* Akun dapat dinonaktifkan.
* Sistem dapat keluar otomatis setelah tidak aktif.
* Data sensitif hanya dapat dilihat oleh pengguna berwenang.
* Aktivitas penting dicatat.

## 36.2 Performa

* Sistem harus dapat digunakan melalui komputer dan ponsel.
* Website publik harus memiliki waktu muat yang baik.
* Foto harus dioptimalkan.
* Daftar data menggunakan pagination.
* Laporan menggunakan filter tanggal.
* Database dirancang untuk transaksi yang terus bertambah.

## 36.3 Backup

* Database dibackup secara berkala.
* Backup disimpan terpisah dari server utama.
* Tersedia prosedur pemulihan data.
* Backup harus diuji secara berkala.

## 36.4 Kompatibilitas

Sistem dapat digunakan melalui:

* Google Chrome.
* Microsoft Edge.
* Browser Android.
* Browser iPhone.
* Komputer.
* Laptop.
* Tablet.
* Telepon seluler.

## 36.5 Koneksi Internet

Sistem berbasis web dan membutuhkan koneksi internet.

Tampilan untuk Tim Produksi harus dibuat ringan agar tetap nyaman digunakan melalui perangkat seluler.

---

# 37. Data yang Dibutuhkan dari Client

Sebelum sistem digunakan, client perlu menyediakan:

## 37.1 Data Perusahaan

* Nama perusahaan.
* Logo.
* Alamat.
* Nomor telepon.
* Nomor WhatsApp.
* Email.
* Rekening pembayaran.
* Informasi pajak jika diperlukan.
* Nama penanggung jawab.

## 37.2 Data Produk

* Nama produk.
* Kode produk.
* Kategori produk.
* Varian.
* Ukuran.
* Satuan.
* Harga.
* Foto.
* Deskripsi.
* Stok awal.
* Batas minimum.

## 37.3 Data Bahan Baku

* Nama bahan baku.
* Satuan pembelian.
* Isi per kemasan.
* Satuan pemakaian.
* Stok awal.
* Stok minimum.
* Supplier.
* Harga beli.

## 37.4 Formula Produksi

* Formula Aquar.
* Formula es kristal.
* Pemakaian lem.
* Faktor waste.
* Standar reject.
* Hasil produksi per batch.
* Satuan masing-masing bahan.

## 37.5 Data Pelanggan

* Nama pelanggan.
* Nama toko.
* Nomor WhatsApp.
* Alamat.
* Jenis pelanggan.
* Harga khusus.
* Ketentuan pembayaran.

## 37.6 Data Reject

* Kategori reject.
* Penyebab reject.
* Tindakan lanjutan.
* Batas persetujuan.
* Kewajiban foto.

## 37.7 Data Pengguna

* Nama pengguna.
* Nomor telepon.
* Email jika diperlukan.
* Role.
* Status aktif.

---

# 38. Ruang Lingkup Tahap Pertama

Fitur yang termasuk dalam tahap pertama:

* Website company profile.
* Informasi produk.
* Tombol WhatsApp.
* Login dan logout.
* Tiga role pengguna.
* Dashboard.
* Data pelanggan.
* Data produk.
* Data bahan baku.
* Formula produksi.
* Pencatatan produksi.
* Pengurangan bahan baku otomatis.
* Penambahan barang jadi otomatis.
* Pembuatan pesanan langsung melalui sistem.
* Penginputan manual pesanan yang diterima melalui WhatsApp.
* Invoice.
* Pembayaran.
* Stok barang jadi.
* Stok bahan baku.
* Warning stok.
* Barang reject.
* Barang pengganti.
* Retur.
* Stock opname.
* Laporan.
* Export laporan dalam bentuk PDF dan Microsoft Excel (.xlsx) sesuai filter dan hak akses pengguna.
* Audit aktivitas.
* Pengaturan perusahaan.

---

# 39. Fitur yang Tidak Termasuk Tahap Pertama

Kecuali disepakati dalam penawaran, fitur berikut tidak termasuk tahap pertama:

* Integrasi WhatsApp API otomatis.
* Chatbot WhatsApp.
* Pembayaran online.
* Payment gateway.
* Aplikasi Android native.
* Aplikasi iOS native.
* Integrasi marketplace.
* Integrasi sistem pajak.
* Integrasi sistem akuntansi eksternal.
* GPS kendaraan.
* Pelacakan pengiriman real-time.
* Sistem absensi.
* Sistem payroll.
* Portal supplier.
* Portal pelanggan.
* Mesin produksi otomatis.
* Integrasi sensor mesin.
* Sistem barcode.
* Sistem QR code.
* Integrasi timbangan digital.
* Sistem multi-cabang.
* Sistem multi-gudang.

Fitur-fitur tersebut dapat dikembangkan sebagai tahap lanjutan.

---

# 40. Alur Utama Sistem

## 40.1 Alur Pesanan

```text
Pemesanan dibuat langsung melalui sistem oleh Tim Operasional
atau
Pelanggan menghubungi WhatsApp, kemudian Tim Operasional mengonfirmasi pesanan dan menginput data pelanggan serta pesanan secara manual ke sistem
        ↓
Sistem membuat pesanan atau invoice Draft
        ↓
Invoice dikonfirmasi
        ↓
Stok direservasi
        ↓
Pembayaran dicatat
        ↓
Barang disiapkan
        ↓
Barang dikirim
        ↓
Stok fisik berkurang
        ↓
Transaksi selesai
```

## 40.2 Alur Produksi

```text
Tim Produksi memilih produk
        ↓
Jumlah produksi dimasukkan
        ↓
Sistem menghitung bahan baku
        ↓
Sistem memeriksa ketersediaan
        ↓
Produksi dilakukan
        ↓
Hasil baik dan reject dimasukkan
        ↓
Bahan baku berkurang
        ↓
Barang jadi bertambah
        ↓
Reject tercatat
```

## 40.3 Alur Reject dan Barang Pengganti

```text
Barang rusak ditemukan
        ↓
Reject dicatat
        ↓
Foto dan penyebab dimasukkan
        ↓
Data diverifikasi
        ↓
Stok reject diperbarui
        ↓
Jika pelanggan memerlukan penggantian
        ↓
Barang pengganti dibuat
        ↓
Stok berkurang
        ↓
Omzet tidak bertambah
```

---

# 41. Kriteria Penerimaan Sistem

Sistem dianggap memenuhi kebutuhan awal apabila:

1. Pengguna dapat login berdasarkan role.
2. Owner dapat melihat dashboard keseluruhan.
3. Tim Operasional dapat mencatat pelanggan.
4. Tim Operasional dapat membuat pesanan langsung melalui sistem.
5. Tim Operasional dapat menginput secara manual pesanan yang diterima melalui WhatsApp setelah pesanan dikonfirmasi.
6. Tim Operasional dapat membuat invoice.
7. Nomor invoice dibuat secara otomatis.
8. Invoice dapat dicetak atau diunduh.
9. Invoice Draft tidak mengurangi stok.
10. Invoice Dikonfirmasi dapat mereservasi stok.
11. Stok berkurang saat barang dikirim.
12. Pembatalan invoice mengembalikan stok reservasi.
13. Tim Produksi dapat mencatat produksi.
14. Produksi satu dos Aquar menggunakan 48 cup.
15. Produksi dua dos Aquar menggunakan 96 cup.
16. Produksi seratus dos Aquar menggunakan 4.800 cup.
17. Bahan baku otomatis berkurang setelah produksi.
18. Barang jadi otomatis bertambah setelah produksi.
19. Produksi tidak dapat dikonfirmasi jika bahan baku tidak cukup.
20. Warning muncul ketika stok berada di bawah batas minimum.
21. Pengguna dapat mencatat barang reject.
22. Reject dapat dilengkapi foto.
23. Barang pengganti tidak masuk ke omzet.
24. Retur dapat dihubungkan dengan transaksi asal.
25. Owner dapat melihat laporan penjualan.
26. Owner dapat melihat laporan produksi.
27. Owner dapat melihat laporan stok.
28. Owner dapat melihat laporan reject.
29. Tim Produksi tidak dapat melihat informasi keuangan.
30. Perubahan penting tercatat dalam audit trail.
31. Sistem dapat digunakan melalui komputer dan ponsel.
32. Data dapat dibackup dan dipulihkan.

---

# 42. Tahapan Pengembangan

Tahapan pengembangan sistem dapat dilakukan sebagai berikut:

## Tahap 1: Analisis

* Finalisasi kebutuhan.
* Pengumpulan data.
* Konfirmasi alur bisnis.
* Konfirmasi formula produksi.
* Konfirmasi role dan hak akses.

## Tahap 2: Wireframe

* Desain halaman login.
* Desain dashboard.
* Desain halaman invoice.
* Desain halaman produksi.
* Desain halaman reject.
* Desain halaman stok.
* Desain laporan.

## Tahap 3: Desain Antarmuka

* Pemilihan warna.
* Pemilihan tipografi.
* Desain website company profile.
* Desain sistem internal.
* Desain tampilan mobile.

## Tahap 4: Pengembangan

* Pengembangan database.
* Pengembangan backend.
* Pengembangan frontend.
* Pengembangan hak akses.
* Pengembangan formula produksi.
* Pengembangan laporan.

## Tahap 5: Pengujian

* Pengujian fungsi.
* Pengujian hak akses.
* Pengujian perhitungan.
* Pengujian stok.
* Pengujian invoice.
* Pengujian produksi.
* Pengujian reject.
* Pengujian tampilan mobile.

## Tahap 6: User Acceptance Testing

Client akan mencoba sistem menggunakan data simulasi.

Masukan dari client akan dicatat dan diperbaiki berdasarkan ruang lingkup yang telah disepakati.

## Tahap 7: Implementasi

* Memasukkan data awal.
* Memasukkan pengguna.
* Memasukkan stok awal.
* Pelatihan pengguna.
* Sistem mulai digunakan.

## Tahap 8: Pemeliharaan

* Perbaikan bug.
* Monitoring sistem.
* Backup.
* Pembaruan keamanan.
* Dukungan pengguna.

---

# 43. Batasan dan Asumsi

Dokumen ini menggunakan beberapa asumsi:

1. Pemesanan dapat dibuat langsung melalui sistem oleh Tim Operasional atau diterima melalui WhatsApp.
2. Pesanan yang diterima melalui WhatsApp harus dikonfirmasi dan diinput secara manual oleh Tim Operasional ke dalam sistem.
3. Satu dos Aquar berisi 48 cup.
4. Setiap cup membutuhkan satu lid.
5. Setiap cup membutuhkan satu sedotan.
6. Setiap dos membutuhkan satu kardus.
7. Jumlah penggunaan lem akan dikonfirmasi.
8. Formula es kristal akan diberikan oleh client.
9. Status tangki air dalam sistem akan dikonfirmasi.
10. Client menyediakan data stok awal yang benar.
11. Client menyediakan harga produk.
12. Client menyediakan formula produksi.
13. Setiap pengguna memiliki akun sendiri.
14. Sistem memerlukan koneksi internet.
15. Perubahan besar setelah persetujuan dokumen menjadi permintaan tambahan.
16. Integrasi pihak ketiga dapat memiliki biaya tambahan.
17. Data lama hanya dimasukkan jika termasuk ruang lingkup.
18. Ketepatan data operasional bergantung pada kedisiplinan pengguna.

---

# 44. Poin yang Perlu Dikonfirmasi oleh Client

Sebelum pengembangan dimulai, beberapa poin perlu dikonfirmasi:

1. Apakah stok berkurang saat barang dikirim atau saat invoice dikonfirmasi?
2. Apakah Tim Operasional dapat memberikan diskon?
3. Apakah diskon memerlukan persetujuan Owner?
4. Apakah pembayaran tempo digunakan?
5. Apakah terdapat batas kredit pelanggan?
6. Berapa batas minimum setiap bahan baku?
7. Berapa kebutuhan lem untuk satu dos Aquar?
8. Bagaimana formula produksi es kristal?
9. Apa satuan penjualan es kristal?
10. Apakah tangki air masuk ke stok dan invoice?
11. Apakah barang reject wajib menggunakan foto?
12. Siapa yang menyetujui reject dalam jumlah besar?
13. Apakah terdapat sistem canvassing?
14. Apakah stok kendaraan perlu dicatat?
15. Apakah laporan perlu diekspor ke Excel?
16. Apakah invoice perlu mencantumkan pajak?
17. Apakah invoice memerlukan tanda tangan?
18. Apakah sistem digunakan pada satu atau beberapa lokasi?
19. Apakah client membutuhkan barcode atau QR code?
20. Apakah terdapat data lama yang perlu dimigrasikan?

---

# 45. Persetujuan

Dokumen ini digunakan sebagai dasar perancangan dan pengembangan Sistem Manajemen Operasional Aquar dan Es Kristal.

Dengan menyetujui dokumen ini, kedua pihak menyatakan telah memahami:

* Tujuan sistem.
* Ruang lingkup sistem.
* Fitur yang akan dikembangkan.
* Hak akses pengguna.
* Alur penjualan.
* Alur produksi.
* Formula bahan baku.
* Alur stok.
* Alur barang reject.
* Alur barang pengganti.
* Kriteria penerimaan.
* Batasan pengembangan.

Perubahan setelah dokumen disetujui dapat diproses sebagai perubahan ruang lingkup atau pengembangan tambahan.

---

## PIHAK CLIENT

**Nama:** ______________________________

**Jabatan:** ___________________________

**Tanggal:** ___________________________

**Tanda Tangan:**

<br><br><br>

---

---

## PIHAK PENGEMBANG

**Nama:** ______________________________

**Jabatan:** ___________________________

**Tanggal:** ___________________________

**Tanda Tangan:**

<br><br><br>

---
