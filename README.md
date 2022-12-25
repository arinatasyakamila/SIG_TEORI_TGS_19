# SIG_TEORI_TGS_19
 Sampling Raster Data Using Points or Polygons
 Cara Membuatnya !

1. Buka zip dan ekstrak 2018_Gaz_ua_national.zip dan tl_2018_us_county.zip ke folder di komputer Anda. Buka QGIS dan temukan file us.tmax_nohads_ll_20190501_float.tif di Browser QGIS, seret ke kanvas.

2. Anda akan melihat layer raster baru us.tmax_nohads_ll_20190501_float dimuat di panel Layers. Lapisan raster ini berisi suhu maksimum yang tercatat pada setiap piksel dalam derajat Celcius. Selanjutnya kita akan memuat file titik area perkotaan. File ini hadir sebagai file teks dalam format Tab Separated Values (TSV). Klik tombol Buka Pengelola Sumber Data di Bilah Alat Sumber Data.


3. Beralih ke tab Teks Dibatasi. Klik tombol … di sebelah Nama file dan tentukan jalur ke file teks yang Anda unduh. Di bagian File format, pilih Custom delimiters dan centang Tab. Pilih INTPTLONG sebagai bidang X dan INTPTLAT sebagai bidang Y. Klik Tambah lalu Tutup.

4. Lapisan titik baru 2018_Gaz_ua_national akan dimuat di panel Lapisan. Sekarang kita siap untuk mengekstrak nilai dari lapisan raster pada titik-titik ini. Pergi ke Memproses ‣ Toolbox.

5. Cari dan temukan analisis Raster ‣ Contoh algoritme nilai raster. Klik dua kali untuk meluncurkannya.

6. Pilih 2018_Gaz_ua_national sebagai Lapisan Titik Input. Pilih us.tmax_nohads_ll_20190501_float sebagai Lapisan Raster untuk dijadikan sampel. Luaskan parameter Lanjutan dan masukkan tmax sebagai awalan kolom Keluaran. Klik Jalankan. Setelah pemrosesan selesai, klik Tutup.

7. Layer baru Sampled Points akan dimuat di panel Layers. Pilih alat Identifikasi di Bilah Alat Atribut dan klik titik mana saja. Anda akan melihat atribut ditampilkan di panel Identifikasi Hasil. Anda akan melihat atribut baru bernama tmax_1 ditambahkan ke setiap fitur. Ini adalah nilai piksel dari lapisan raster yang diekstraksi di lokasi titik. Angka 1 mewakili nomor pita raster. Jika lapisan raster memiliki banyak pita, Anda akan melihat banyak kolom baru di lapisan keluaran.

8. Bagian pertama dari analisis kami selesai. Mari kita hapus lapisan yang tidak perlu. Tahan tombol Shift dan pilih Sampled Points dan layer 2018_Gaz_ua_national. Klik kanan dan pilih Hapus untuk menghapusnya dari QGIS. Saat diminta untuk Hapus 2 entri legenda?, pilih OK.

9. Sekarang kita akan menggunakan lapisan kabupaten untuk mengambil sampel raster dan menghitung suhu rata-rata untuk setiap kabupaten. Temukan file tl_2018_us_county.shp di Browser QGIS, seret ke kanvas.

Catatan

Sebagian besar algoritme pemrosesan akan membaca lapisan masukan dan membuat lapisan baru. Tetapi algoritma Statistik Zona berbeda. Itu memodifikasi lapisan input dan menambahkan atribut baru ke dalamnya. Itulah mengapa penting untuk meng-unzip file input terlebih dahulu. QGIS dapat memuat lapisan dari arsip zip secara langsung, tetapi tidak dapat mengubah lapisan yang di-zip. Algoritme pemrosesan akan gagal jika tidak dapat memperbarui lapisan input.

10. Lapisan baru tl_2018_us_county akan dimuat ke panel Lapisan. Pergi ke Memproses ‣ Toolbox.


11. Cari dan temukan analisis Raster ‣ Algoritme statistik zona dan klik dua kali untuk meluncurkannya.

12. Pilih us.tmax_nohads_ll_20190501_float sebagai layer Raster dan tl_2018_us_county sebagai layer Vector yang berisi zona. Masukkan tmax_ sebagai awalan kolom Keluaran. Klik … di samping Statistik untuk menghitung.

13. Pilih hanya nilai Mean dan klik OK.

14. Klik Jalankan untuk memulai pemrosesan. Algoritme mungkin membutuhkan waktu beberapa menit untuk selesai. Klik Tutup.

15. Seperti disebutkan sebelumnya, algoritma Zonal Statistics tidak membuat layer baru, tetapi memodifikasi layer zona. Klik kanan layer tl_2018_us_county, dan pilih Open Attribute Table.

16. Anda akan melihat kolom baru bernama tmax_mean ditambahkan ke tabel atribut. Ini berisi nilai suhu rata-rata yang diekstraksi di atas poligon untuk setiap fitur. Ada beberapa nilai nol karena kabupaten tersebut (milik Alaska, Hawaii, dan Puerto Riko) berada di luar jangkauan lapisan raster.

