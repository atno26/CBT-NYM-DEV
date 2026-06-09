Panduan Lengkap Instalasi CBT: Supabase & GitHub Pages

Ikuti langkah-langkah di bawah ini secara berurutan untuk mempublikasikan aplikasi Ujian Online (CBT) Anda ke internet agar dapat diakses oleh siswa.

TAHAP 1: Menyiapkan Database Backend (Supabase)

Kita akan menggunakan SQL Script otomatis agar Anda tidak perlu membuat tabel satu per satu secara manual.

Buka dashboard proyek Supabase Anda.

Di menu sebelah kiri, klik menu SQL Editor (ikon tanda kurung siku </>).

Klik tombol New Query.

Salin seluruh isi dari file supabase_schema.sql (yang ada di dokumen sebelah) lalu tempel (paste) ke dalam SQL Editor tersebut.

Klik tombol Run (warna hijau) di pojok kanan bawah.

Jika berhasil, akan muncul tulisan "Success, no rows returned". Semua tabel dan data awal admin otomatis sudah terbuat!

TAHAP 2: Menyiapkan Penyimpanan Gambar (Supabase Storage)

Ini wajib dilakukan agar fitur "Upload Gambar" pada admin berfungsi.

Di menu sebelah kiri Supabase, klik menu Storage (ikon folder).

Klik tombol New bucket.

Pada kolom nama bucket, ketik persis seperti ini: logos (huruf kecil semua).

Sangat Penting: Centang opsi Public bucket.

Klik tombol Save.

Klik bucket logos yang baru dibuat, lalu masuk ke tab Policies (atau Configuration > Policies).

Di bagian "Other policies under logos", pastikan Anda membuat policy baru dan memilih opsi "Enable full access to public" (izinkan SELECT, INSERT, UPDATE, DELETE) agar admin dapat mengunggah gambar dari aplikasi.

TAHAP 3: Menghubungkan File HTML dengan Supabase Anda

Agar aplikasi HTML Anda terhubung dengan database Anda sendiri (bukan milik orang lain), Anda harus mengganti URL dan API Key-nya.

Kembali ke Dashboard utama proyek Supabase Anda.

Buka menu Project Settings (ikon gerigi / roda gigi di kiri bawah).

Pilih menu API.

Di sana terdapat Project URL dan Project API Keys (anon public).

Buka file index.html aplikasi kita menggunakan teks editor (Notepad, VS Code, dll).

Cari baris kode (sekitar baris ke-600) berikut:

const SUPABASE_URL = "[https://gantidenganurlmilikanda.supabase.co](https://gantidenganurlmilikanda.supabase.co)"; 
const SUPABASE_ANON_KEY = "ganti_dengan_anon_key_anda"; 


Ganti nilai di dalam tanda kutip dengan URL dan Key dari Supabase Anda. Simpan (Save) file index.html tersebut.

TAHAP 4: Hosting Frontend ke GitHub Pages (Gratis)

Ini adalah langkah terakhir untuk membuat aplikasi Anda online.

Buat akun atau Login ke GitHub.com.

Di pojok kanan atas, klik tanda + dan pilih New repository.

Isi Repository name (misal: cbt-sekolah).

Pastikan opsi Public terpilih. Klik tombol Create repository.

Di halaman berikutnya, klik tautan bertuliskan "uploading an existing file".

Pilih dan drag and drop (seret) file index.html (yang URL Supabase-nya sudah diubah) ke dalam kotak unggahan GitHub.

Klik tombol hijau Commit changes.

Setelah file terunggah, klik menu Settings (ikon gerigi) di dalam repository tersebut.

Di menu sebelah kiri, cari bagian Code and automation dan klik Pages.

Pada bagian Build and deployment > Branch, ubah menu dropdown dari None menjadi main (atau master).

Klik tombol Save.

🎉 Selesai! Tunggu sekitar 1–3 menit. Refresh halaman GitHub Pages tersebut. Anda akan melihat tautan web aktif (biasanya berformat https://username-anda.github.io/cbt-sekolah/).

Bagikan link tersebut kepada siswa dan admin Anda. Aplikasi CBT sekarang sudah beroperasi penuh selama 24/7!
