# Hukum dan Kebijakan Teknologi Informasi

## Buku Ajar untuk Mahasiswa Teknik Informatika (Edisi 2026/2027)

|Keterangan|Isi|
|---|---|
|Versi|1.0|
|Tanggal penyusunan|21 Oktober 2026|
|Cakupan|Hukum dan kebijakan TI di Indonesia, dengan perbandingan internasional|
|Sasaran pembaca|Pemula, tidak perlu latar belakang hukum|
|Bahasa|Indonesia, dengan istilah teknis yang dijelaskan|

---

## Catatan Penting Sebelum Membaca

1. **Buku ini bukan nasihat hukum.** Buku ini alat belajar. Untuk perkara nyata, konsultasikan dengan advokat atau konsultan hukum.
2. **Hukum cepat berubah.** Beberapa peraturan di bidang TI masih berupa rancangan atau baru berlaku. Setiap bab penting memuat kotak "Status regulasi" dengan keterangan tanggal. Bab 16 menjelaskan cara memeriksa pembaruan sendiri.
3. **Pembacaan angka pasal.** Jika ditulis "Pasal 27A", artinya pasal tersebut berada di undang-undang yang sedang dibahas pada bagian itu. Nomor pasal dapat bergeser jika undang-undang diubah.
4. **Tentang kutipan peraturan.** Isi peraturan dijelaskan dengan bahasa sederhana, bukan disalin. Teks resmi tetap harus dibaca di sumber resminya (lihat Lampiran E).
5. **Nama kementerian.** Sejak Oktober 2024, kementerian yang mengurus TI bernama Kementerian Komunikasi dan Digital (Komdigi), sebelumnya Kementerian Komunikasi dan Informatika (Kominfo). Peraturan lama masih menyebut "Kominfo" atau "Menteri Komunikasi dan Informatika".

## Cara Menggunakan Buku Ini

Setiap bab memiliki struktur yang sama:

- **Tujuan pembelajaran**: apa yang akan Anda kuasai.
- **Materi inti**: penjelasan konsep, contoh, dan analogi.
- **Sudut pandang developer**: apa artinya bagi pekerjaan Anda sehari-hari (menulis kode, merancang basis data, mengelola server).
- **Ringkasan**: poin terpenting.
- **Latihan**: soal untuk menguji pemahaman.

Jalur belajar yang disarankan:

|Jalur|Bab|Cocok untuk|
|---|---|---|
|Dasar|1, 2, 3, 5|Semester awal, ingin gambaran cepat|
|Praktisi pengembang|3, 5, 6, 8, 11, 12|Programmer, software engineer, DevOps|
|Keamanan dan tata kelola|5, 6, 7, 12, 14|Calon analis keamanan, auditor TI|
|Lengkap|1 sampai 16|Mata kuliah satu semester|

## Daftar Isi

1. Pengantar Hukum dan Kebijakan Teknologi Informasi
2. Ruang Siber, Yurisdiksi, dan Peta Regulasi
3. Undang-Undang Informasi dan Transaksi Elektronik (UU ITE)
4. Penyelenggara Sistem Elektronik (PSE) dan Sertifikasi Elektronik
5. Pelindungan Data Pribadi
6. Kejahatan Siber, Bukti Digital, dan Batas Hukum Pengujian Keamanan
7. Keamanan Siber Nasional dan Infrastruktur Informasi Vital
8. Hak Kekayaan Intelektual dan Lisensi Perangkat Lunak
9. Transaksi Elektronik, E-Commerce, Fintech, dan Kontrak Digital
10. Konten Digital, Kebebasan Berekspresi, dan Pelindungan Anak
11. Kecerdasan Artifisial dan Teknologi Baru
12. Kebijakan TI dalam Organisasi dan Program Kepatuhan
13. Etika Profesi dan Tanggung Jawab Profesional
14. Perspektif Internasional dan Perbandingan
15. Studi Kasus Terpadu
16. Tren 2026 sampai 2030 dan Cara Menjaga Pengetahuan Tetap Mutakhir

Lampiran:

- A. Peta Peraturan Ringkas
- B. Glosarium
- C. Kuis Pilihan Ganda dan Kunci Jawaban
- D. Templat Praktis
- E. Sumber Resmi dan Sumber Pemutakhiran

---

# Bab 1. Pengantar Hukum dan Kebijakan Teknologi Informasi

## Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

- Menjelaskan perbedaan hukum, regulasi, kebijakan, standar, dan etika.
- Menyebutkan hierarki peraturan perundang-undangan Indonesia.
- Membedakan tanggung jawab pidana, perdata, dan administratif.
- Mengenali lembaga-lembaga yang berperan di bidang TI.
- Membaca sebuah peraturan dengan urutan yang benar.

## 1.1 Mengapa Mahasiswa Teknik Informatika Perlu Memahami Hukum

Banyak orang mengira hukum hanya urusan pengacara. Padahal, keputusan teknis yang Anda ambil punya akibat hukum. Beberapa contoh:

- Aplikasi Anda menyimpan foto KTP pengguna. Jika basis data bocor, siapa yang bertanggung jawab?
- Anda memakai pustaka (_library_) dari internet dalam produk komersial. Apakah lisensinya mengizinkan?
- Anda mengambil data dari sebuah situs dengan _web scraping_. Apakah itu sah?
- Anda diminta menguji keamanan sebuah server. Apa bedanya dengan peretasan ilegal?
- Chatbot AI buatan Anda memberi informasi yang merugikan pengguna. Siapa yang menanggung?

Analogi sederhana: seorang insinyur sipil tidak boleh membangun jembatan tanpa mengikuti standar keselamatan. Insinyur perangkat lunak juga bekerja dengan sistem yang memengaruhi uang, data, dan keselamatan orang lain, sehingga wajib memahami batas-batas yang ditetapkan hukum.

## 1.2 Hukum, Regulasi, Kebijakan, Standar, dan Etika

Lima istilah ini sering tertukar. Berikut perbedaannya.

|Istilah|Pengertian|Daya ikat|Contoh|
|---|---|---|---|
|Hukum|Aturan yang dibuat negara dan dapat dipaksakan dengan sanksi|Mengikat dan memaksa|UU ITE, UU PDP|
|Regulasi|Peraturan teknis turunan hukum, dibuat pemerintah atau otoritas sektor|Mengikat|Peraturan Pemerintah, Peraturan Menteri, Peraturan OJK|
|Kebijakan|Arah dan keputusan, bisa dari pemerintah maupun organisasi|Tergantung pembuatnya|Kebijakan kata sandi perusahaan, strategi nasional AI|
|Standar|Acuan teknis yang disepakati|Sukarela, kecuali diwajibkan regulasi|ISO/IEC 27001, SNI|
|Etika|Nilai tentang apa yang pantas dilakukan|Moral dan profesional|Kode etik profesi|

Analogi untuk programmer:

- **Hukum** seperti spesifikasi protokol yang wajib dipatuhi agar sistem diterima jaringan. Jika dilanggar, paket ditolak (sanksi).
- **Standar** seperti panduan praktik terbaik (_best practice_), tidak wajib tetapi sangat disarankan.
- **Kebijakan** seperti berkas konfigurasi: menentukan perilaku sistem dalam batas yang diizinkan hukum.
- **Etika** seperti prinsip desain: tidak ada yang memaksa, tetapi menentukan kualitas.

## 1.3 Hierarki Peraturan Perundang-undangan

Di Indonesia, aturan tersusun berjenjang. Dasarnya adalah Undang-Undang Nomor 12 Tahun 2011 tentang Pembentukan Peraturan Perundang-undangan (sebagaimana diubah beberapa kali). Urutan dari yang tertinggi:

```
1. Undang-Undang Dasar Negara Republik Indonesia Tahun 1945
2. Ketetapan MPR
3. Undang-Undang (UU) / Peraturan Pemerintah Pengganti UU (Perppu)
4. Peraturan Pemerintah (PP)
5. Peraturan Presiden (Perpres)
6. Peraturan Daerah Provinsi
7. Peraturan Daerah Kabupaten/Kota
```

Selain itu ada peraturan menteri, peraturan lembaga (misalnya OJK, BSSN, Bank Indonesia), dan surat edaran. Peraturan jenis ini tetap berlaku sepanjang diperintahkan oleh peraturan yang lebih tinggi atau dibuat berdasarkan kewenangan.

Tiga asas penyelesaian pertentangan aturan, penting untuk diingat:

|Asas|Arti|Contoh|
|---|---|---|
|_Lex superior derogat legi inferiori_|Aturan lebih tinggi mengalahkan yang lebih rendah|UU mengalahkan Peraturan Menteri|
|_Lex specialis derogat legi generali_|Aturan khusus mengalahkan aturan umum|UU ITE (khusus transaksi dan informasi elektronik) dapat didahulukan dari ketentuan umum KUHP|
|_Lex posterior derogat legi priori_|Aturan baru mengalahkan aturan lama yang setingkat|UU baru menggantikan UU lama yang bertentangan|

Analogi: seperti urutan prioritas aturan pada _firewall_, aturan yang lebih spesifik dan lebih tinggi prioritasnya dievaluasi lebih dulu.

## 1.4 Tiga Jenis Pertanggungjawaban Hukum

Satu peristiwa dapat memicu lebih dari satu jenis tanggung jawab sekaligus.

|Jenis|Fokus|Penegak|Akibat|Contoh pada kasus kebocoran data|
|---|---|---|---|---|
|Pidana|Pelanggaran terhadap kepentingan umum|Polisi, jaksa, hakim|Penjara, denda|Orang yang menjual data curian dapat dipidana|
|Perdata|Hubungan antarpihak|Pengadilan negeri|Ganti rugi, pembatalan kontrak|Pengguna menggugat perusahaan yang lalai menjaga data|
|Administratif|Kepatuhan terhadap izin dan kewajiban|Kementerian atau otoritas sektor|Teguran, denda administratif, pemutusan akses|Otoritas menjatuhkan sanksi karena tidak melapor insiden|

Istilah tambahan:

- **Delik aduan**: tindak pidana yang hanya diproses jika korban mengadu (misalnya pencemaran nama baik).
- **Delik biasa**: dapat diproses tanpa pengaduan korban.
- **Subjek hukum**: pihak yang dapat memiliki hak dan kewajiban, yaitu orang (manusia) dan badan hukum (perusahaan, yayasan). Program komputer dan AI **bukan** subjek hukum.

## 1.5 Lembaga yang Berperan di Bidang TI

|Lembaga|Peran singkat|
|---|---|
|Kementerian Komunikasi dan Digital (Komdigi)|Regulator utama TI: pendaftaran PSE, pemblokiran konten, sertifikasi elektronik, pengawasan ruang digital|
|Badan Siber dan Sandi Negara (BSSN)|Keamanan siber nasional, penanganan insiden, kriptografi, sertifikasi elektronik pemerintah|
|Otoritas Jasa Keuangan (OJK)|Mengawasi sektor jasa keuangan, termasuk fintech, pinjaman daring, dan aset keuangan digital|
|Bank Indonesia (BI)|Sistem pembayaran, uang elektronik, QRIS|
|Kepolisian RI (unit siber)|Penyelidikan dan penyidikan tindak pidana siber|
|Kejaksaan|Penuntutan|
|Mahkamah Konstitusi (MK)|Menguji undang-undang terhadap UUD 1945|
|Mahkamah Agung (MA)|Menguji peraturan di bawah undang-undang, memutus kasasi|
|Komisi Pengawas Persaingan Usaha (KPPU)|Persaingan usaha, termasuk platform digital|
|Direktorat Jenderal Kekayaan Intelektual (DJKI)|Pencatatan hak cipta, paten, merek|
|Lembaga Pelindungan Data Pribadi|Diamanatkan UU PDP sebagai pengawas independen (status pembentukan dibahas di Bab 5 dan 16)|

## 1.6 Cara Membaca Sebuah Peraturan

Jangan membaca dari pasal pertama sampai terakhir. Gunakan urutan berikut:

1. **Judul dan nomor.** Pastikan Anda memegang peraturan yang benar dan memeriksa apakah sudah diubah atau dicabut.
2. **Konsiderans (Menimbang dan Mengingat).** Menjelaskan alasan dan dasar hukum pembuatan.
3. **Ketentuan Umum (Bab I).** Berisi definisi. Untuk TI, definisi sangat menentukan, misalnya apa yang dimaksud "sistem elektronik" atau "data pribadi".
4. **Ruang lingkup dan siapa yang diatur.** Apakah Anda termasuk subjek aturan ini?
5. **Kewajiban dan larangan.**
6. **Sanksi.** Administratif, perdata, dan pidana.
7. **Ketentuan Peralihan dan Penutup.** Bagian ini sering menjelaskan kapan aturan berlaku dan aturan lama mana yang dicabut. Bagian ini sering terlewat padahal sangat penting.
8. **Penjelasan.** Memberi tafsir resmi atas pasal.

## Ringkasan Bab 1

- Hukum mengikat dan memaksa, standar dan etika bersifat pedoman.
- Peraturan tersusun berjenjang, dan ada tiga asas untuk menyelesaikan pertentangan aturan.
- Satu peristiwa dapat menimbulkan tanggung jawab pidana, perdata, dan administratif sekaligus.
- Baca peraturan dengan mulai dari definisi, ruang lingkup, kewajiban, sanksi, lalu ketentuan penutup.

## Latihan Bab 1

1. Jelaskan perbedaan hukum dan standar dengan contoh dari bidang keamanan informasi.
2. Sebuah Peraturan Menteri bertentangan dengan Undang-Undang. Aturan mana yang berlaku? Asas apa yang dipakai?
3. Aplikasi toko daring Anda dibobol dan data pelanggan bocor karena Anda tidak memperbarui perangkat lunak. Sebutkan tiga jenis tanggung jawab yang mungkin timbul dan contohnya.
4. Mengapa bagian "Ketentuan Penutup" penting dibaca saat Anda ingin mengetahui apakah aturan lama masih berlaku?

---

# Bab 2. Ruang Siber, Yurisdiksi, dan Peta Regulasi

## Tujuan Pembelajaran

- Menjelaskan apa itu hukum siber dan tantangan khususnya.
- Memahami konsep yurisdiksi di ruang siber.
- Mengenali pendekatan pengaturan teknologi.
- Mengetahui peta besar regulasi TI di Indonesia.

## 2.1 Apa Itu Hukum Siber

**Hukum siber** (_cyber law_) adalah kumpulan aturan yang mengatur aktivitas di ruang digital: transaksi, komunikasi, penyimpanan data, dan penggunaan sistem komputer. Di Indonesia, hukum siber tidak terkumpul dalam satu undang-undang. Ia tersebar di banyak peraturan, dengan UU ITE sebagai pusatnya.

## 2.2 Tantangan Khas Hukum di Ruang Siber

|Tantangan|Penjelasan|Contoh|
|---|---|---|
|Lintas batas|Data dan pelaku dapat berada di negara berbeda|Peretas di negara A menyerang server di negara B dengan korban di Indonesia|
|Anonimitas|Identitas pelaku sulit dilacak|Akun palsu, VPN, jaringan Tor|
|Bukti mudah berubah|Log dapat terhapus atau tertimpa|Data tertimpa karena rotasi log|
|Kecepatan teknologi|Hukum selalu tertinggal|Aturan AI baru dibahas ketika AI generatif sudah dipakai luas|
|Perantara|Banyak pihak terlibat: pengguna, platform, penyedia hosting, penyedia jaringan|Siapa yang bertanggung jawab atas konten yang diunggah pengguna|

## 2.3 Yurisdiksi di Ruang Siber

**Yurisdiksi** adalah kewenangan suatu negara untuk menerapkan hukumnya dan mengadili perkara. Dalam konteks TI, ada beberapa dasar:

|Dasar yurisdiksi|Arti|Contoh|
|---|---|---|
|Teritorial|Perbuatan dilakukan di wilayah negara|Server dan pelaku berada di Indonesia|
|Personal|Berdasarkan kewarganegaraan|WNI melakukan kejahatan siber di luar negeri|
|Efek (_effects doctrine_)|Perbuatan di luar negeri tetapi akibatnya terasa di negara itu|Penipuan dari luar negeri yang merugikan korban di Indonesia|

UU ITE mengadopsi pendekatan ini. Ketentuan yurisdiksinya menyatakan bahwa undang-undang berlaku bagi setiap orang yang melakukan perbuatan hukum, baik di wilayah Indonesia maupun di luar wilayah Indonesia, yang memiliki akibat hukum di Indonesia dan/atau di luar Indonesia dan merugikan kepentingan Indonesia.

**Sudut pandang developer:** jika layanan Anda dapat diakses dan digunakan oleh orang Indonesia, bersiaplah bahwa hukum Indonesia dapat berlaku, meskipun server Anda di luar negeri. Hal yang sama berlaku sebaliknya: jika Anda melayani pengguna Eropa, aturan seperti GDPR dapat berlaku bagi Anda.

## 2.4 Pendekatan Pengaturan Teknologi

|Pendekatan|Penjelasan|Kelebihan|Kekurangan|
|---|---|---|---|
|Netral teknologi|Aturan tidak menyebut teknologi tertentu|Awet saat teknologi berganti|Bisa terlalu umum|
|Sektoral|Aturan per sektor (keuangan, kesehatan)|Sesuai kebutuhan sektor|Tumpang tindih antarsektor|
|Menyeluruh (omnibus)|Satu undang-undang besar|Seragam|Rumit dan lama dibuat|
|Berbasis risiko|Kewajiban sebanding dengan tingkat risiko|Proporsional|Sulit menentukan kategori|
|Swa-regulasi|Industri membuat aturan sendiri|Fleksibel|Penegakan lemah|

Indonesia cenderung memakai kombinasi: undang-undang pokok (ITE, PDP), aturan sektoral (OJK, BI, kesehatan), dan mulai bergerak ke pendekatan berbasis risiko untuk kecerdasan artifisial.

## 2.5 Peta Besar Regulasi TI Indonesia

Peta lengkap ada di Lampiran A. Ringkasan per tema:

|Tema|Peraturan utama|
|---|---|
|Informasi dan transaksi elektronik|UU ITE dan perubahannya, PP tentang Penyelenggaraan Sistem dan Transaksi Elektronik|
|Data pribadi|UU Pelindungan Data Pribadi|
|Pidana|KUHP baru dan KUHAP baru (berlaku 2 Januari 2026), UU ITE|
|Keamanan siber|Peraturan Presiden tentang BSSN, infrastruktur informasi vital, strategi keamanan siber|
|Kekayaan intelektual|UU Hak Cipta, Paten, Merek, Rahasia Dagang, dan lainnya|
|Perdagangan|Peraturan Pemerintah dan Peraturan Menteri Perdagangan tentang perdagangan melalui sistem elektronik|
|Keuangan digital|UU P2SK dan peraturan OJK dan BI|
|Konten dan anak|UU Pornografi, UU Perlindungan Anak, PP tentang pelindungan anak di sistem elektronik|
|Pemerintahan digital|Peraturan Presiden tentang SPBE dan Satu Data|
|Kecerdasan artifisial|Surat edaran etika AI, rancangan Peraturan Presiden (Bab 11)|

## 2.6 Instrumen Internasional yang Perlu Diketahui

- **Konvensi Budapest tentang Kejahatan Siber (2001)**: perjanjian internasional pertama dan paling banyak dirujuk untuk kejahatan siber. Dijadikan rujukan banyak negara dalam menyusun hukum nasional.
- **Konvensi PBB tentang Kejahatan Siber**: disetujui Majelis Umum PBB pada Desember 2024 dan dibuka untuk penandatanganan pada Oktober 2025. Status keikutsertaan Indonesia perlu diperiksa pada sumber resmi Kementerian Luar Negeri.
- **GDPR (Uni Eropa)**: standar pelindungan data yang banyak ditiru.
- **Pedoman OECD dan UNESCO tentang etika AI**.

Pembahasan lebih lengkap ada di Bab 14.

## Ringkasan Bab 2

- Hukum siber di Indonesia tersebar di banyak peraturan.
- Yurisdiksi di ruang siber dapat didasarkan pada wilayah, kewarganegaraan, dan akibat.
- Pendekatan pengaturan beragam dan sering digabungkan.

## Latihan Bab 2

1. Sebuah startup di Singapura melayani pengguna Indonesia tanpa kantor di Indonesia. Apakah hukum Indonesia dapat berlaku? Jelaskan dasar yurisdiksinya.
2. Mengapa pendekatan "netral teknologi" berguna bagi regulasi di bidang yang cepat berubah?
3. Sebutkan tiga tantangan pembuktian di ruang siber dan satu cara teknis mengurangi masing-masing.

---

# Bab 3. Undang-Undang Informasi dan Transaksi Elektronik (UU ITE)

## Tujuan Pembelajaran

- Menjelaskan sejarah dan struktur UU ITE.
- Memahami istilah kunci: informasi elektronik, dokumen elektronik, sistem elektronik, agen elektronik, tanda tangan elektronik.
- Memahami kedudukan alat bukti elektronik.
- Mengenali perbuatan yang dilarang dan batas-batasnya.
- Memahami hubungan UU ITE dengan KUHP baru.

## 3.1 Sejarah Singkat

|Tahun|Peraturan|Inti|
|---|---|---|
|2008|UU Nomor 11 Tahun 2008|Undang-undang siber pertama Indonesia: pengakuan dokumen dan tanda tangan elektronik, transaksi elektronik, perbuatan yang dilarang|
|2016|UU Nomor 19 Tahun 2016 (perubahan pertama)|Menurunkan ancaman pidana pencemaran nama baik, menambah ketentuan penghapusan informasi (hak untuk dilupakan)|
|2024|UU Nomor 1 Tahun 2024 (perubahan kedua)|Disahkan DPR pada 5 Desember 2023, ditandatangani dan diundangkan 2 Januari 2024. Mengubah 14 pasal dan menambah 5 pasal baru. Menambah ketentuan pelindungan anak, sertifikasi elektronik, kontrak elektronik internasional, dan menyelaraskan pidana dengan KUHP baru|

Perubahan kedua tetap menuai kritik dari masyarakat sipil, terutama karena beberapa pasal pidana dinilai masih dapat ditafsirkan terlalu luas. Pemerintah menyatakan perubahan ini bertujuan meningkatkan kepastian hukum.

## 3.2 Struktur Besar UU ITE

1. Ketentuan umum dan asas
2. Informasi, dokumen, dan tanda tangan elektronik
3. Penyelenggaraan sertifikasi elektronik dan sistem elektronik
4. Transaksi elektronik
5. Nama domain, hak kekayaan intelektual, dan pelindungan hak pribadi
6. Perbuatan yang dilarang
7. Penyelesaian sengketa
8. Peran pemerintah dan masyarakat
9. Penyidikan
10. Ketentuan pidana

## 3.3 Istilah Kunci

|Istilah|Penjelasan sederhana|Contoh|
|---|---|---|
|Informasi elektronik|Data elektronik yang sudah diolah dan memiliki arti|Teks, gambar, suara, email, EDI, kode akses|
|Dokumen elektronik|Informasi elektronik yang dibuat, diteruskan, dikirim, diterima, atau disimpan dan dapat dilihat atau didengar|Berkas PDF, rekaman suara, tangkapan layar|
|Sistem elektronik|Rangkaian perangkat dan prosedur untuk mengolah, menyimpan, dan mengirim informasi elektronik|Aplikasi web, server, jaringan|
|Agen elektronik|Perangkat dari sistem elektronik yang melakukan tindakan otomatis atas informasi tertentu|Bot pemesanan, sistem pembelian otomatis|
|Tanda tangan elektronik|Tanda berupa informasi elektronik yang melekat pada dokumen elektronik, dipakai untuk verifikasi dan autentikasi|Tanda tangan digital pada kontrak|
|Sertifikat elektronik|Sertifikat yang memuat tanda tangan elektronik dan identitas pemiliknya|Sertifikat dari penyelenggara sertifikasi elektronik|

## 3.4 Alat Bukti Elektronik

UU ITE menyatakan bahwa informasi elektronik, dokumen elektronik, dan hasil cetaknya merupakan **alat bukti hukum yang sah** dan merupakan perluasan dari alat bukti dalam hukum acara yang berlaku.

**Syarat agar bukti elektronik dapat dipercaya:**

1. **Keutuhan (_integrity_):** isi tidak berubah.
2. **Ketersediaan:** dapat ditampilkan kembali.
3. **Dapat dipertanggungjawabkan:** asal dan cara memperolehnya jelas.
4. **Diperoleh secara sah:** misalnya penyadapan oleh pihak yang tidak berwenang dapat membuat bukti dipersoalkan (ada putusan MK yang menekankan bahwa intersepsi untuk bukti harus dilakukan oleh penegak hukum atas dasar kewenangan).

**Pengecualian:** informasi elektronik tidak dapat menjadi alat bukti untuk surat yang menurut undang-undang harus dibuat tertulis, dan surat yang harus dibuat dalam bentuk akta notaris atau akta pejabat pembuat akta.

**Sudut pandang developer:** sistem Anda dapat menjadi sumber bukti. Rancang log yang tidak dapat diubah (_append-only_), sinkronkan waktu server (NTP), dan simpan _hash_ untuk mendeteksi perubahan. Pembahasan teknis ada di Bab 6.

## 3.5 Perbuatan yang Dilarang

Berikut ringkasan larangan utama dalam UU ITE (sebagaimana diubah). Ini penjelasan umum, bukan kutipan pasal.

|Pasal|Inti larangan|Catatan|
|---|---|---|
|27 ayat (1)|Menyiarkan atau mendistribusikan konten yang melanggar kesusilaan untuk diketahui umum, dengan sengaja dan tanpa hak|Berkaitan dengan UU Pornografi dan KUHP|
|27 ayat (2)|Perjudian|Berkaitan dengan pemberantasan judi daring|
|27A|Menyerang kehormatan atau nama baik orang dengan menuduhkan suatu hal agar diketahui umum|Delik aduan. Ancaman pidana hingga 2 tahun atau denda hingga Rp400 juta menurut Pasal 45 ayat (4). Putusan MK menegaskan korban adalah orang perseorangan, bukan lembaga atau korporasi|
|27B|Memaksa atau mengancam untuk memperoleh keuntungan (pemerasan atau pengancaman)|Jenis perbuatan baru dalam perubahan kedua|
|28 ayat (1)|Menyebarkan berita bohong atau informasi menyesatkan yang merugikan konsumen dalam transaksi elektronik|Fokus pada kerugian konsumen|
|28 ayat (2)|Menyebarkan informasi yang menimbulkan kebencian atau permusuhan terhadap individu atau kelompok berdasarkan SARA|Terkait ujaran kebencian|
|28 ayat (3)|Menyebarkan pemberitahuan bohong yang menimbulkan kerusuhan|Telah diuji MK; baca putusan terbaru untuk tafsir unsur "kerusuhan"|
|29|Mengirim ancaman kekerasan atau menakut-nakuti yang ditujukan secara pribadi||
|30|Mengakses komputer atau sistem elektronik milik orang lain tanpa hak, termasuk dengan menjebol sistem pengamanan|Akses ilegal (_illegal access_)|
|31|Intersepsi atau penyadapan informasi elektronik tanpa hak|Ada pengecualian untuk penegak hukum yang berwenang|
|32|Mengubah, merusak, memindahkan, atau menyembunyikan informasi atau dokumen elektronik milik orang lain atau publik tanpa hak|Gangguan terhadap data|
|33|Mengganggu sistem elektronik sehingga tidak bekerja sebagaimana mestinya|Misalnya serangan penolakan layanan (DoS)|
|34|Menyediakan atau memiliki perangkat atau sandi akses untuk melakukan perbuatan terlarang|Ada pengecualian untuk penelitian atau pengujian sistem yang sah|
|35|Memanipulasi data agar seolah-olah otentik|Pemalsuan digital|

### Peringatan tentang Status Pasal

Dua perkembangan membuat status beberapa pasal pidana UU ITE perlu diperiksa ulang pada saat Anda membaca buku ini:

1. **KUHP baru berlaku 2 Januari 2026.** Perubahan kedua UU ITE sengaja menyelaraskan ketentuan pidananya dengan KUHP baru. Sebagian materi pidana UU ITE dialihkan ke KUHP. Ada perbedaan pandangan di kalangan praktisi hukum:
    
    - Satu pandangan: UU ITE tetap menjadi aturan khusus (_lex specialis_) untuk perbuatan yang dilakukan lewat sistem elektronik.
    - Pandangan lain: untuk beberapa perbuatan, terutama pencemaran nama baik, pemidanaan seharusnya memakai pasal dalam KUHP baru (misalnya Pasal 433), karena pasal terkait di UU ITE telah dicabut atau disesuaikan.
    
    Sebagai pemula, jangan memilih salah satu secara buru-buru. Cara memastikan: baca Pasal II pada UU 1/2024 dan Ketentuan Penutup KUHP baru, lalu cek putusan pengadilan terbaru.
    
2. **Putusan Mahkamah Konstitusi** (misalnya Putusan Nomor 105/PUU-XXII/2024 dan Nomor 115/PUU-XXII/2024) telah menafsirkan ulang beberapa pasal. Putusan MK mengikat dan dapat mengubah makna pasal tanpa mengubah teksnya.
    

> **Status regulasi (per 21 Oktober 2026):** UU 1/2024 adalah perubahan terakhir yang diketahui penulis. KUHP dan KUHAP baru berlaku sejak 2 Januari 2026. Hubungan pasal pidana ITE dengan KUHP baru masih menjadi bahan diskusi dan perkembangan putusan pengadilan.

### Perbandingan Ancaman Pidana Pencemaran Nama Baik (Ilustrasi)

|Sumber|Ancaman|Catatan|
|---|---|---|
|UU ITE Pasal 27A dan Pasal 45 ayat (4)|Hingga 2 tahun penjara atau denda hingga Rp400 juta|Perbuatan melalui sistem elektronik|
|KUHP baru Pasal 433|Hingga 9 bulan penjara atau denda kategori II (hingga Rp10 juta) untuk pencemaran lisan|Pencemaran secara tertulis atau gambar diatur dengan ancaman lebih berat|
|Penghinaan ringan (KUHP baru)|Hingga 6 bulan atau denda hingga Rp10 juta||

Perhatikan bahwa pencemaran nama baik adalah **delik aduan**: harus ada pengaduan dari korban.

## 3.6 Kritik dan Kebebasan Berekspresi

Pasal-pasal tentang kesusilaan, pencemaran, dan berita bohong sering disebut "pasal karet" oleh sebagian kalangan karena rumusannya dapat ditafsirkan luas. Untuk mengurangi penyalahgunaan, pemerintah, Kapolri, dan Jaksa Agung pernah menerbitkan Surat Keputusan Bersama pedoman implementasi UU ITE pada 2021. Pedoman ini menekankan antara lain bahwa kritik, penilaian, atau hasil evaluasi dan ungkapan yang bersifat opini bukan penghinaan. Setelah KUHP baru, pedoman semacam ini dapat diperbarui.

Prinsip dasarnya: kebebasan berekspresi dijamin konstitusi, tetapi dapat dibatasi dengan undang-undang untuk menghormati hak orang lain, ketertiban umum, dan moral. Pembahasan lanjut ada di Bab 10.

## 3.7 Kontrak Elektronik dan Tanda Tangan Elektronik

- Transaksi elektronik yang dituangkan dalam kontrak elektronik mengikat para pihak.
- Kontrak elektronik sah jika ada kesepakatan para pihak, dilakukan oleh pihak yang cakap atau berwenang, ada hal tertentu, dan tidak bertentangan dengan hukum.
- Perubahan kedua menegaskan ketentuan mengenai kontrak elektronik internasional dan penggunaan hukum Indonesia pada klausul baku yang dibuat sepihak oleh pelaku usaha untuk pengguna Indonesia, dalam kondisi tertentu.
- Tanda tangan elektronik terbagi dua: **tersertifikasi** (dibuat dengan jasa penyelenggara sertifikasi elektronik yang berizin, kekuatan pembuktian lebih kuat) dan **tidak tersertifikasi** (kekuatan pembuktian lebih lemah, perlu dibuktikan keabsahannya).

## 3.8 Hak untuk Dilupakan

Sejak perubahan 2016, orang dapat meminta penghapusan informasi elektronik yang tidak relevan, dengan penetapan pengadilan. Konsep ini berdampingan dengan hak atas penghapusan data pribadi pada UU PDP (Bab 5).

## 3.9 Pelindungan Anak dalam UU ITE

Perubahan kedua menambahkan kewajiban bagi penyelenggara sistem elektronik untuk melindungi anak yang menggunakan atau mengakses sistem elektronik, dengan sanksi administratif. Aturan pelaksananya adalah PP Nomor 17 Tahun 2025 (PP TUNAS), dibahas di Bab 10.

## 3.10 Penyidikan

Penyidik tindak pidana ITE adalah Polri dan Penyidik Pegawai Negeri Sipil (PPNS) di lingkungan kementerian yang mengurus TI. Dalam melakukan penggeledahan dan penyitaan sistem elektronik, penyidik wajib menjaga kepentingan pelayanan publik dan menjaga keutuhan data. Dengan berlakunya KUHAP baru, tata cara penggeledahan, penyitaan, dan pembuktian elektronik perlu dibaca bersama aturan acara yang baru.

## Ringkasan Bab 3

- UU ITE telah diubah dua kali (2016 dan 2024), dan terus dinamis karena KUHP baru dan putusan MK.
- Dokumen dan informasi elektronik adalah alat bukti sah, dengan pengecualian untuk akta tertentu.
- Pasal 30 sampai 35 melarang akses ilegal, intersepsi, gangguan data dan sistem, pembuatan alat peretasan, dan manipulasi data. Pengecualian ada untuk penelitian dan pengujian yang sah.
- Pencemaran nama baik adalah delik aduan dan status pemidanaannya perlu diperiksa bersama KUHP baru.

## Latihan Bab 3

1. Jelaskan perbedaan informasi elektronik dan dokumen elektronik, beri satu contoh masing-masing.
2. Apakah tangkapan layar percakapan dapat menjadi alat bukti? Apa saja yang harus dijaga agar bukti itu kuat?
3. Seorang mahasiswa memindai jaringan kampus tanpa izin dan masuk ke server dosen "hanya untuk belajar". Pasal apa yang berpotensi dilanggar? Mengapa niat baik tidak otomatis menghapus kesalahan?
4. Mengapa seorang pembaca hukum harus memeriksa Ketentuan Penutup KUHP baru ketika mempelajari pasal pidana UU ITE?

---

# Bab 4. Penyelenggara Sistem Elektronik (PSE) dan Sertifikasi Elektronik

## Tujuan Pembelajaran

- Menjelaskan apa itu PSE dan jenisnya.
- Memahami kewajiban PSE menurut PP 71 Tahun 2019 dan aturan turunannya.
- Memahami pendaftaran PSE, moderasi konten, dan akses penegak hukum.
- Memahami sertifikasi elektronik.

## 4.1 Siapa PSE

**Penyelenggara Sistem Elektronik (PSE)** adalah setiap orang, penyelenggara negara, badan usaha, atau masyarakat yang menyediakan, mengelola, dan/atau mengoperasikan sistem elektronik, baik sendiri maupun bersama-sama, untuk keperluan dirinya atau pihak lain. Dengan kata lain, hampir semua pemilik aplikasi, situs, marketplace, media sosial, atau layanan SaaS adalah PSE.

|Jenis|Siapa|Contoh|
|---|---|---|
|PSE Lingkup Publik|Instansi pemerintah atau institusi yang ditunjuk|Portal layanan pemerintah, aplikasi dinas|
|PSE Lingkup Privat|Orang, badan usaha, masyarakat|Marketplace, aplikasi transportasi, media sosial, penyedia gim, aplikasi startup|

## 4.2 Landasan Hukum

- **Peraturan Pemerintah Nomor 71 Tahun 2019** tentang Penyelenggaraan Sistem dan Transaksi Elektronik (PSTE). Menggantikan PP 82 Tahun 2012.
- **Peraturan Menteri Kominfo Nomor 5 Tahun 2020** tentang PSE Lingkup Privat, sebagaimana diubah dengan Permenkominfo Nomor 10 Tahun 2021. Kementerian kini bernama Komdigi, tetapi peraturan lama tetap berlaku sampai diganti.

## 4.3 Kewajiban Utama PSE

|Kewajiban|Penjelasan|Wujud praktik teknis|
|---|---|---|
|Andal, aman, bertanggung jawab|Sistem harus dapat beroperasi dengan baik, dilindungi dari gangguan, dan penyelenggaranya akuntabel|Redundansi, pembaruan keamanan, pemantauan, rencana pemulihan bencana|
|Pendaftaran|PSE Lingkup Privat wajib mendaftar sebelum layanannya digunakan pengguna|Mengurus pendaftaran melalui kanal resmi pemerintah|
|Pelindungan data pribadi|Mengikuti UU PDP|Bab 5|
|Tata kelola sistem|Memiliki kebijakan dan prosedur keamanan|Bab 12|
|Menyediakan akses bagi penegak hukum|Dalam batas hukum untuk kepentingan pengawasan dan penegakan hukum|Prosedur permintaan data resmi, log permintaan|
|Moderasi konten|Mencegah sistemnya memuat atau memfasilitasi konten terlarang|Fitur pelaporan, tinjauan moderator|
|Lokasi pusat data|Aturan berbeda untuk publik dan privat; PSE publik pada dasarnya mengelola dan menyimpan data di Indonesia, dengan pengecualian terbatas|Pilih lokasi hosting sesuai aturan|

## 4.4 Moderasi Konten dan Pemutusan Akses

Menurut aturan PSE Lingkup Privat:

- PSE wajib memastikan sistemnya tidak memuat atau memfasilitasi informasi yang dilarang.
- Pemerintah dapat memerintahkan penghapusan konten terlarang. Batas waktu umum adalah 1 x 24 jam setelah perintah, dan untuk keadaan mendesak (misalnya terorisme, pornografi anak, atau konten yang meresahkan masyarakat dan mengganggu ketertiban umum) dapat jauh lebih singkat, yaitu 4 jam.
- PSE yang tidak patuh dapat dikenai sanksi administratif, mulai dari teguran sampai pemutusan akses (pemblokiran).

**Sudut pandang developer:** bangun alur moderasi sejak awal: tombol laporan, penyimpanan bukti laporan, antrean peninjauan, serta kemampuan menyembunyikan atau menghapus konten dengan cepat. Mekanisme yang bisa merespons dalam hitungan jam jauh lebih mudah dirancang di awal daripada ditambahkan setelah ada teguran.

## 4.5 Pendaftaran PSE: Langkah Konseptual

1. Siapkan identitas badan usaha atau perorangan dan deskripsi layanan.
2. Siapkan informasi sistem: nama, kategori layanan, domain atau URL, ringkasan pemrosesan data.
3. Ajukan melalui sistem yang ditetapkan pemerintah.
4. Simpan bukti pendaftaran, dan perbarui jika terjadi perubahan layanan.

Prosedur teknis kanal pendaftaran dapat berubah, jadi periksa situs resmi Komdigi.

## 4.6 Sertifikasi Elektronik

**Penyelenggara Sertifikasi Elektronik (PSrE)** memberikan layanan sertifikat elektronik, tanda tangan elektronik tersertifikasi, segel elektronik, penanda waktu elektronik, dan layanan terkait. PSrE berinduk (terhubung ke akar kepercayaan nasional) di bawah pengawasan pemerintah.

Konsep teknis di balik tanda tangan elektronik:

```
Penandatangan: hash(dokumen) --dienkripsi dengan kunci privat--> tanda tangan
Penerima:      tanda tangan --didekripsi dengan kunci publik--> hash A
               hash(dokumen yang diterima) --> hash B
               Jika hash A = hash B maka dokumen utuh dan penanda tangan terautentikasi
```

Sertifikat elektronik mengikat identitas pemilik dengan kunci publiknya, dan PSrE yang terpercaya menjamin keabsahan ikatan itu. Pengelolaan kunci privat adalah tanggung jawab penanda tangan. Jika kunci privat dicuri dan tidak dicabut, penanda tangan dapat dirugikan.

## 4.7 Tanggung Jawab atas Agen Elektronik

Agen elektronik (misalnya sistem pemesanan otomatis) bertindak atas nama penyelenggaranya. Secara umum, penyelenggara bertanggung jawab atas akibat hukum agen elektroniknya, kecuali dapat dibuktikan bahwa kerugian terjadi karena keadaan memaksa, kesalahan pengguna, atau kelalaian pihak lain. Konsep ini menjadi pijakan awal diskusi pertanggungjawaban sistem AI (Bab 11).

## Ringkasan Bab 4

- Hampir semua penyedia aplikasi dan situs adalah PSE.
- PSE wajib andal, aman, bertanggung jawab, terdaftar (untuk lingkup privat), dan responsif terhadap perintah penghapusan konten.
- Tanda tangan elektronik tersertifikasi memberi kekuatan pembuktian lebih kuat.

## Latihan Bab 4

1. Aplikasi marketplace buatan Anda memiliki fitur ulasan pengguna. Apa saja kewajiban PSE yang relevan?
2. Rancang alur sederhana (diagram alur) penanganan perintah penghapusan konten dalam 24 jam.
3. Jelaskan mengapa hash dokumen dipakai dalam tanda tangan elektronik, bukan seluruh isi dokumen.

---

# Bab 5. Pelindungan Data Pribadi

## Tujuan Pembelajaran

- Menjelaskan jenis data pribadi dan peran para pihak menurut UU PDP.
- Memahami hak subjek data dan kewajiban pengendali data.
- Menerapkan prinsip pelindungan data dalam desain sistem.
- Mengetahui sanksi dan status pelaksanaan UU PDP.

## 5.1 Dasar Hukum

**Undang-Undang Nomor 27 Tahun 2022 tentang Pelindungan Data Pribadi (UU PDP)**, diundangkan pada 17 Oktober 2022. UU ini memberi masa penyesuaian dua tahun, sehingga efektif berlaku penuh sejak 17 Oktober 2024.

> **Status regulasi (informasi yang tersedia hingga 2026):** Pada pemberitaan Februari 2026, pemerintah menyatakan bahwa Rancangan Peraturan Pemerintah (RPP) pelaksana UU PDP telah diajukan untuk ditetapkan Presiden sejak Oktober 2025 dan masih dalam proses harmonisasi. Lembaga Pelindungan Data Pribadi yang diamanatkan undang-undang belum terbentuk secara penuh. Selama itu fungsi pengawasan dijalankan sementara oleh unit di Kementerian Komdigi. UU PDP juga tercatat dalam daftar Prolegnas Prioritas 2026 menurut pemberitaan. Periksa perkembangan terbaru sebelum menyusun kebijakan perusahaan.

## 5.2 Istilah Utama

|Istilah|Arti|Padanan sederhana|
|---|---|---|
|Data pribadi|Data tentang orang perseorangan yang teridentifikasi atau dapat diidentifikasi, sendiri atau digabung dengan informasi lain|Nama, nomor telepon, alamat IP yang dapat dikaitkan dengan orang|
|Subjek data|Orang yang datanya diproses|Pengguna aplikasi|
|Pengendali data (_controller_)|Pihak yang menentukan tujuan dan cara pemrosesan|Perusahaan pemilik aplikasi|
|Prosesor data (_processor_)|Pihak yang memproses data atas nama pengendali|Penyedia cloud, vendor email blast|
|Pemrosesan|Pengumpulan, penyimpanan, penggunaan, pengungkapan, penghapusan, dan lainnya|Hampir semua operasi pada data|

### Dua Kategori Data Pribadi

|Kategori|Isi|Perlakuan|
|---|---|---|
|Umum|Nama lengkap, jenis kelamin, kewarganegaraan, agama, status perkawinan, dan data yang digabung untuk mengidentifikasi seseorang|Standar|
|Spesifik|Kesehatan, biometrik, genetika, catatan kejahatan, data anak, data keuangan pribadi, dan data lain sesuai peraturan|Risiko lebih tinggi, pelindungan lebih ketat|

## 5.3 Hak Subjek Data

Subjek data memiliki hak, antara lain:

- Memperoleh informasi tentang kejelasan identitas, dasar hukum, tujuan, dan akuntabilitas pihak yang meminta data.
- Melengkapi, memperbarui, atau memperbaiki data.
- Mengakses dan mendapatkan salinan data.
- Mengakhiri pemrosesan, menghapus, atau memusnahkan data.
- Menarik persetujuan.
- Mengajukan keberatan atas keputusan yang diambil semata-mata berdasarkan pemrosesan otomatis, termasuk pemrofilan, yang berdampak hukum atau signifikan.
- Menunda atau membatasi pemrosesan.
- Menggugat dan menerima ganti rugi.
- Memperoleh dan menggunakan data dalam bentuk yang lazim digunakan (portabilitas).

Hak-hak ini diatur pada pasal-pasal awal UU PDP. Untuk anak, persetujuan diberikan oleh orang tua atau wali.

## 5.4 Dasar Pemrosesan yang Sah

Pengendali data hanya boleh memproses data pribadi jika ada salah satu dasar:

1. Persetujuan yang sah dan eksplisit dari subjek data.
2. Pemenuhan kewajiban perjanjian.
3. Pemenuhan kewajiban hukum.
4. Pelindungan kepentingan vital subjek data.
5. Pelaksanaan tugas dalam rangka kepentingan umum atau kewenangan pengendali.
6. Pemenuhan kepentingan yang sah lainnya dengan memperhatikan keseimbangan kepentingan.

**Ciri persetujuan yang baik:** spesifik per tujuan, jelas, dapat ditarik, dan tidak dipaksakan. Kotak centang yang sudah tercentang sebelumnya dan persetujuan "paket" untuk semua tujuan sebaiknya dihindari.

## 5.5 Kewajiban Pengendali Data

|Kewajiban|Penjelasan|
|---|---|
|Transparansi|Memberi tahu tujuan, jenis data, jangka waktu, dan hak subjek data|
|Pembatasan tujuan|Data dipakai hanya untuk tujuan yang disampaikan|
|Keamanan|Menjaga kerahasiaan, keutuhan, dan ketersediaan data dengan langkah teknis dan organisasi|
|Akurasi|Memastikan data akurat dan lengkap|
|Pembatasan retensi|Menghapus data jika tujuan tercapai atau subjek data menarik persetujuan|
|Penilaian dampak (DPIA)|Untuk pemrosesan berisiko tinggi, misalnya pemrofilan, data spesifik skala besar, atau pemantauan sistematis|
|Pejabat pelindungan data (DPO)|Wajib pada kondisi tertentu, seperti pelayanan publik atau pemrosesan skala besar atas data spesifik atau pemantauan teratur|
|Pencatatan|Menyimpan catatan kegiatan pemrosesan|
|Pemberitahuan kegagalan pelindungan data|Memberitahu subjek data dan lembaga paling lambat 3 x 24 jam sejak terjadi kegagalan, dengan informasi yang diwajibkan|
|Transfer lintas negara|Memastikan negara tujuan memiliki tingkat pelindungan setara atau ada jaminan memadai|

## 5.6 Sanksi

|Jenis|Isi|
|---|---|
|Administratif|Peringatan tertulis, penghentian sementara pemrosesan, penghapusan atau pemusnahan data, ganti rugi, dan denda administratif hingga 2 persen dari pendapatan atau penerimaan tahunan terhadap variabel pelanggaran|
|Pidana (orang)|Mengumpulkan atau memperoleh data yang bukan miliknya untuk keuntungan sendiri atau orang lain hingga 5 tahun penjara dan/atau denda hingga Rp5 miliar. Mengungkapkan data yang bukan miliknya hingga 4 tahun dan/atau Rp4 miliar. Menggunakan data yang bukan miliknya hingga 5 tahun dan/atau Rp5 miliar. Membuat data pribadi palsu hingga 6 tahun dan/atau Rp6 miliar|
|Pidana (korporasi)|Pidana denda dapat dijatuhkan hingga sepuluh kali dari denda maksimal, ditambah pidana tambahan seperti perampasan keuntungan dan pembekuan usaha|

## 5.7 Sudut Pandang Developer: Privasi dalam Desain

**Privacy by design** berarti pelindungan data dibangun ke dalam arsitektur sejak awal, bukan ditambahkan di akhir.

Daftar prinsip teknis:

1. **Minimalisasi data.** Kumpulkan hanya yang benar-benar dibutuhkan. Jika aplikasi senter tidak butuh lokasi, jangan minta izin lokasi.
2. **Pembatasan akses.** Prinsip _least privilege_ dan kontrol akses berbasis peran.
3. **Enkripsi.** Saat transit (TLS) dan saat disimpan (_at rest_), terutama data spesifik.
4. **Pseudonimisasi.** Pisahkan identitas langsung dari data analitik.
5. **Retensi.** Tentukan masa simpan dan hapus otomatis.
6. **Log audit.** Catat siapa mengakses data apa dan kapan.
7. **Manajemen persetujuan.** Simpan bukti persetujuan dan sediakan cara menariknya.
8. **Respons insiden.** Siapkan rencana yang memungkinkan pemberitahuan dalam 3 x 24 jam.

Contoh pseudonimisasi sederhana dengan HMAC (Python), supaya nomor identitas tidak disimpan dalam bentuk asli tetapi tetap dapat dicocokkan:

```python
import hmac
import hashlib
import os

KUNCI = os.environ["PSEUDONIM_KEY"].encode()  # simpan di secret manager, bukan di kode

def pseudonim(nilai: str) -> str:
    return hmac.new(KUNCI, nilai.encode(), hashlib.sha256).hexdigest()
```

Catatan penting: data yang dipseudonimkan **masih dapat dianggap data pribadi** jika dapat dikaitkan kembali dengan orang menggunakan informasi tambahan. Jadi pseudonimisasi mengurangi risiko, tetapi tidak menghapus kewajiban hukum.

Contoh catatan persetujuan (_consent log_):

```json
{
  "subjek_id": "u-1029",
  "tujuan": "pengiriman_promosi_email",
  "versi_kebijakan": "2026-09-01",
  "persetujuan": true,
  "waktu": "2026-10-21T06:39:00+07:00",
  "kanal": "formulir_web",
  "dapat_ditarik": true
}
```

## 5.8 Contoh Peta Data (_Data Mapping_)

Langkah pertama kepatuhan adalah mengetahui data apa yang Anda miliki.

|Sistem|Jenis data|Kategori|Tujuan|Dasar|Retensi|Lokasi|Akses|
|---|---|---|---|---|---|---|---|
|Basis data pengguna|Nama, email, nomor telepon|Umum|Layanan akun|Perjanjian|Selama akun aktif + 1 tahun|Pusat data A|Tim backend|
|Verifikasi identitas|Foto KTP, swafoto|Spesifik (biometrik)|Verifikasi pengguna|Persetujuan|90 hari setelah verifikasi|Penyimpanan terenkripsi|Tim kepatuhan|
|Analitik|ID pseudonim, perilaku|Umum|Perbaikan produk|Kepentingan sah|12 bulan|Gudang data|Tim data|

## 5.9 Contoh Kasus Singkat

Sebuah aplikasi pinjaman mengakses seluruh kontak ponsel pengguna dan menggunakannya untuk menagih. Analisis dengan prinsip PDP: pengumpulan melebihi yang diperlukan (melanggar minimalisasi), tujuan penagihan kepada pihak ketiga tidak disepakati (melanggar pembatasan tujuan), dan pihak ketiga (kontak) tidak memberi persetujuan. Praktik seperti ini juga dilarang oleh regulator sektor keuangan.

## 5.10 Perbandingan Singkat dengan GDPR

|Aspek|UU PDP Indonesia|GDPR Uni Eropa|
|---|---|---|
|Dasar pemrosesan|Enam dasar|Enam dasar|
|Denda administratif maksimum|2 persen pendapatan tahunan|Hingga 20 juta euro atau 4 persen omzet global tahunan|
|Notifikasi insiden|3 x 24 jam|72 jam|
|Otoritas independen|Diamanatkan, belum terbentuk penuh|Ada di setiap negara anggota|

## Ringkasan Bab 5

- UU PDP efektif sejak 17 Oktober 2024. Aturan pelaksana dan lembaga pengawas masih dalam proses pembentukan menurut informasi yang tersedia.
- Pengendali data wajib memiliki dasar pemrosesan, menjaga keamanan, dan melapor insiden dalam 3 x 24 jam.
- Developer berperan besar: minimalisasi data, enkripsi, akses terbatas, retensi, log audit.

## Latihan Bab 5

1. Bedakan pengendali data dan prosesor data. Perusahaan Anda memakai layanan email massal dari vendor. Siapa pengendali, siapa prosesor?
2. Aplikasi Anda mengumpulkan tanggal lahir, alamat lengkap, dan nomor KTP padahal hanya butuh email untuk login. Prinsip mana yang dilanggar?
3. Susun peta data untuk aplikasi kampus Anda: minimal tiga sistem.
4. Terjadi kebocoran data pada pukul 09.00 hari Senin. Susun garis waktu respons hingga batas pemberitahuan.

---

# Bab 6. Kejahatan Siber, Bukti Digital, dan Batas Hukum Pengujian Keamanan

## Tujuan Pembelajaran

- Mengklasifikasikan jenis kejahatan siber dan dasar hukumnya.
- Memahami prosedur penegakan hukum dan peran bukti digital.
- Menerapkan praktik dasar forensik digital (rantai penguasaan bukti).
- Membedakan pengujian keamanan yang sah dengan peretasan ilegal.

## 6.1 Klasifikasi Kejahatan Siber

|Kategori|Contoh|Rujukan hukum (umum)|
|---|---|---|
|Kejahatan terhadap sistem (_cyber-dependent_)|Akses ilegal, intersepsi, perusakan data, DoS, malware, ransomware|UU ITE Pasal 30 sampai 35|
|Kejahatan konvensional berbantuan siber (_cyber-enabled_)|Penipuan daring, pemerasan, pencurian identitas, judi daring|KUHP, UU ITE, UU TPPU|
|Konten ilegal|Pornografi, pornografi anak, ujaran kebencian, terorisme|UU Pornografi, UU Perlindungan Anak, UU ITE|
|Kekerasan berbasis elektronik|Penyebaran konten intim tanpa persetujuan, pemerasan seksual|UU Tindak Pidana Kekerasan Seksual (UU TPKS)|
|Pelanggaran data|Jual beli data pribadi, kebocoran akibat kelalaian|UU PDP, UU ITE|

## 6.2 Contoh Modus dan Pencegahan Teknis

|Modus|Cara kerja singkat|Pencegahan|
|---|---|---|
|_Phishing_|Pesan palsu menipu korban agar memberi kredensial|Autentikasi multifaktor, filter email, edukasi|
|_Ransomware_|Mengenkripsi data dan meminta tebusan|Cadangan terpisah (_offline_), segmentasi jaringan, pembaruan sistem|
|_Credential stuffing_|Mencoba kombinasi sandi bocor|Pembatasan percobaan, deteksi anomali, MFA|
|_Business email compromise_|Meniru atasan atau mitra untuk meminta transfer|Verifikasi di luar kanal, kebijakan dua persetujuan|
|_SIM swap_ dan rekayasa sosial|Mengambil alih nomor telepon|Hindari SMS sebagai satu-satunya faktor, gunakan aplikasi autentikator atau kunci keamanan|

## 6.3 Proses Penegakan Hukum

1. **Pelaporan** oleh korban atau pihak lain, atau temuan aparat.
2. **Penyelidikan:** mencari tahu apakah peristiwa merupakan tindak pidana.
3. **Penyidikan:** mengumpulkan bukti dan menetapkan tersangka.
4. **Penuntutan** oleh jaksa.
5. **Persidangan** dan putusan.

Dalam kasus penipuan keuangan, pelaporan cepat penting. Platform dan bank memiliki mekanisme pemblokiran sementara rekening, dan OJK membentuk pusat pelaporan penipuan keuangan daring bernama Indonesia Anti-Scam Centre pada 2024. Periksa kanal resmi terbaru sebelum melapor.

## 6.4 Bukti Digital dan Forensik

Bukti digital bersifat **mudah berubah dan mudah dipalsukan**. Karena itu ada prinsip:

1. **Identifikasi** sumber bukti.
2. **Pengamanan:** cegah perubahan (isolasi perangkat, gunakan _write blocker_ bila memungkinkan).
3. **Akuisisi:** buat salinan bit demi bit (_forensic image_).
4. **Verifikasi:** bandingkan hash asli dan salinan.
5. **Analisis** dilakukan **pada salinan**, bukan yang asli.
6. **Dokumentasi** setiap langkah.
7. **Pelaporan.**

Acuan internasional: ISO/IEC 27037 (identifikasi, pengumpulan, akuisisi, dan pelestarian bukti digital).

### Rantai Penguasaan Bukti (_Chain of Custody_)

Catatan yang menunjukkan siapa memegang bukti, kapan, di mana, dan untuk apa. Contoh format:

|No|Waktu|Barang bukti|Hash SHA-256|Dari|Kepada|Tujuan|Tanda tangan|
|---|---|---|---|---|---|---|---|
|1|2026-10-21 09:00|Server log 20 Okt|a3f1...|Admin|Analis A|Akuisisi|...|
|2|2026-10-21 11:30|Salinan forensik|a3f1...|Analis A|Lemari bukti|Penyimpanan|...|

Contoh verifikasi integritas di Linux:

```bash
# Hitung hash berkas asli dan salinan, lalu bandingkan
sha256sum bukti_asli.img salinan_analisis.img
# Dua baris hash harus identik. Jika berbeda, salinan tidak dapat dipercaya.
```

**Sudut pandang developer:** pastikan log aplikasi mencantumkan waktu dengan zona yang jelas, ID pengguna, dan tindakan. Kirim log ke penyimpanan terpisah yang tidak dapat diubah oleh administrator aplikasi. Log yang bisa diedit tidak banyak berguna sebagai bukti.

## 6.5 Pengujian Keamanan: Batas yang Sah

Pengujian penetrasi dan program _bug bounty_ adalah bagian sah dari keamanan, tetapi tindakan yang sama secara teknis dengan peretasan. Yang membedakan adalah **izin dan batasan**.

Ciri pengujian yang sah:

1. **Izin tertulis** dari pemilik sistem sebelum pengujian.
2. **Ruang lingkup yang jelas:** alamat IP, domain, aplikasi yang boleh diuji, dan yang dilarang.
3. **Aturan keterlibatan (_rules of engagement_):** jam pengujian, teknik yang dilarang, kontak darurat.
4. **Perjanjian kerahasiaan** atas temuan.
5. **Pelaporan bertanggung jawab (_responsible disclosure_):** temuan dilaporkan kepada pemilik, diberi waktu memperbaiki, tidak diumbar atau diperjualbelikan.
6. **Tidak mengambil, menyalin, atau menyebarkan data** di luar yang diperlukan sebagai bukti kerentanan.

Jika Anda menemukan kerentanan pada sistem orang lain tanpa izin, jangan mengeksploitasi lebih jauh. Catat seperlunya, hentikan, dan laporkan lewat kanal resmi pemilik atau tim tanggap insiden (CSIRT). Pengecualian dalam UU ITE untuk pengujian dan penelitian yang sah hanya berlaku untuk kegiatan yang benar-benar sah dan tidak melawan hukum; tanpa izin, Anda tidak dapat berlindung di balik niat baik.

## Ringkasan Bab 6

- Kejahatan siber terbagi menjadi serangan terhadap sistem dan kejahatan konvensional yang dibantu siber.
- Bukti digital harus dijaga integritasnya dengan hash dan rantai penguasaan bukti.
- Pengujian keamanan hanya sah dengan izin tertulis dan ruang lingkup jelas.

## Latihan Bab 6

1. Mengapa analisis forensik harus dilakukan pada salinan, bukan pada bukti asli?
2. Susun daftar isi surat izin pengujian penetrasi (minimal enam butir).
3. Anda menemukan celah SQL injection di situs sebuah kampus lain saat menjelajah. Apa langkah yang benar dan apa yang harus dihindari?
4. Rancang desain log yang layak sebagai bukti untuk aplikasi perbankan sederhana.

---

# Bab 7. Keamanan Siber Nasional dan Infrastruktur Informasi Vital

## Tujuan Pembelajaran

- Mengetahui lembaga dan kerangka keamanan siber nasional.
- Memahami konsep infrastruktur informasi vital (IIV).
- Memahami standar dan kerangka tata kelola keamanan informasi.
- Mengetahui status rancangan undang-undang keamanan siber.

## 7.1 Lembaga dan Kerangka

- **BSSN** adalah lembaga pemerintah yang membidangi keamanan siber dan sandi. Menjalankan pengamanan siber nasional, penanganan insiden, dan pembinaan tim tanggap insiden.
- **Peraturan Presiden Nomor 47 Tahun 2023** tentang Strategi Keamanan Siber Nasional dan Manajemen Krisis Siber.
- **Peraturan Presiden Nomor 82 Tahun 2022** tentang Pelindungan Infrastruktur Informasi Vital.
- **SPBE (Sistem Pemerintahan Berbasis Elektronik)**: tata kelola pemerintahan digital, antara lain melalui Peraturan Presiden Nomor 95 Tahun 2018 dan Peraturan Presiden tentang Arsitektur SPBE Nasional. Aturan keamanan informasi SPBE ditetapkan oleh BSSN.

## 7.2 Infrastruktur Informasi Vital

**IIV** adalah sistem elektronik yang memuat data strategis, dan gangguan terhadapnya berdampak serius terhadap kepentingan publik, pelayanan publik, pertahanan, keamanan, atau perekonomian nasional.

Sektor yang umumnya dikategorikan sebagai IIV:

- Pemerintahan
- Energi dan sumber daya mineral
- Transportasi
- Keuangan
- Kesehatan
- Teknologi informasi dan komunikasi
- Pangan
- Pertahanan
- Sektor lain yang ditetapkan

Pengelola IIV memiliki kewajiban lebih berat: manajemen risiko, pemantauan, uji keamanan berkala, pelaporan insiden, dan memiliki tim tanggap insiden. Periksa peraturan sektoral untuk daftar kewajiban lengkap.

## 7.3 Standar dan Kerangka Kerja

|Kerangka|Fokus|Kegunaan|
|---|---|---|
|ISO/IEC 27001|Sistem manajemen keamanan informasi (SMKI)|Sertifikasi, kepatuhan pelanggan dan regulator|
|ISO/IEC 27701|Perluasan 27001 untuk manajemen informasi privasi|Mendukung kepatuhan PDP|
|NIST Cybersecurity Framework|Identifikasi, lindungi, deteksi, respons, pulihkan (dan tata kelola pada versi terbaru)|Peta kapabilitas keamanan|
|COBIT|Tata kelola dan manajemen TI perusahaan|Audit dan kontrol TI|
|ISO/IEC 42001|Sistem manajemen AI|Tata kelola AI|

Standar bersifat sukarela kecuali diwajibkan regulasi atau kontrak. Namun, ketika terjadi insiden, kepatuhan pada standar sering dijadikan indikator bahwa organisasi telah berusaha wajar.

## 7.4 Manajemen Insiden

Tahapan umum:

1. **Persiapan:** kebijakan, tim, alat, pelatihan.
2. **Deteksi dan analisis:** menentukan apakah ini insiden dan seberapa besar.
3. **Penahanan, pemberantasan, pemulihan.**
4. **Pasca-insiden:** evaluasi dan perbaikan.
5. **Pelaporan:** kepada regulator dan pihak terdampak sesuai kewajiban (misalnya 3 x 24 jam untuk kegagalan pelindungan data pribadi).

## 7.5 Rancangan Undang-Undang Keamanan dan Ketahanan Siber

> **Status regulasi (per akhir Juni 2026 menurut informasi yang tersedia):** Rancangan Undang-Undang Keamanan dan Ketahanan Siber (RUU KKS) diusulkan pemerintah melalui Menteri Hukum dan mulai dibahas bersama Komisi I DPR pada 29 Juni 2026. Materinya mencakup penyelenggaraan keamanan siber, tata laksana insiden, ketahanan sistem jaringan, perlindungan infrastruktur kritis, kerja sama internasional, penguatan peran pemerintah, mekanisme penyidikan, sanksi administratif, dan partisipasi masyarakat. Karena masih rancangan, isi akhir dapat berubah. Pantau perkembangan melalui situs DPR dan JDIH.

Diskusi publik yang lazim mengiringi RUU semacam ini: keseimbangan antara keamanan nasional dan hak privasi, peran institusi (sipil atau militer), kewenangan penyidikan, dan beban kepatuhan bagi sektor swasta.

## Ringkasan Bab 7

- BSSN, Perpres tentang strategi keamanan siber dan IIV adalah fondasi saat ini.
- Pengelola IIV memiliki kewajiban keamanan lebih berat.
- ISO 27001 dan kerangka sejenis membantu menunjukkan tata kelola yang baik.
- RUU KKS masih rancangan pada informasi terakhir yang tersedia.

## Latihan Bab 7

1. Mengapa sistem rumah sakit dan pembangkit listrik dikategorikan sebagai IIV, sedangkan aplikasi permainan biasanya tidak?
2. Jelaskan perbedaan standar dan regulasi dengan contoh ISO 27001.
3. Tuliskan lima langkah rencana tanggap insiden untuk startup sepuluh orang.

---

# Bab 8. Hak Kekayaan Intelektual dan Lisensi Perangkat Lunak

## Tujuan Pembelajaran

- Memahami hak cipta atas program komputer.
- Mengenali bentuk kekayaan intelektual lain yang relevan bagi TI.
- Memahami lisensi perangkat lunak, termasuk sumber terbuka.
- Menerapkan kepatuhan lisensi dalam proyek.

## 8.1 Hak Cipta atas Program Komputer

Dasar hukum: **Undang-Undang Nomor 28 Tahun 2014 tentang Hak Cipta**.

Hal penting:

- **Program komputer termasuk ciptaan yang dilindungi.** Perlindungan mencakup kode sumber dan kode objek (ekspresi), bukan ide, algoritma, atau konsep itu sendiri.
- **Perlindungan timbul otomatis** sejak ciptaan diwujudkan dalam bentuk nyata. Pencatatan di DJKI tidak wajib, tetapi berguna sebagai bukti.
- **Pencipta adalah manusia.** Badan hukum dapat menjadi pemegang hak cipta, tetapi pencipta dalam definisi undang-undang adalah orang.
- **Masa perlindungan program komputer** adalah 50 tahun sejak pertama kali diumumkan.
- **Hak moral dan hak ekonomi.** Hak moral mencakup pencantuman nama pencipta. Hak ekonomi mencakup memperbanyak, menerbitkan, mengadaptasi, dan mendistribusikan.
- **Ciptaan dalam hubungan dinas:** jika program dibuat oleh karyawan dalam hubungan kerja, pemegang hak ciptanya pada umumnya adalah instansi atau perusahaan pemberi kerja, kecuali diperjanjikan lain.
- **Pembatasan.** Penggunaan wajar tertentu diperbolehkan, misalnya untuk pendidikan, penelitian, dan kritik, dengan syarat tidak merugikan kepentingan wajar pencipta dan menyebut sumber.
- **Pemblokiran.** Pemerintah dapat menutup akses konten dan situs yang melanggar hak cipta atas laporan.

**Sudut pandang developer:** kode di repositori publik tanpa lisensi **bukan** domain publik. Secara default, semua hak tetap pada penulisnya. Anda tidak boleh menyalin dan memakainya tanpa izin.

## 8.2 Bentuk Kekayaan Intelektual Lain

|Bentuk|Dasar|Relevansi TI|
|---|---|---|
|Paten|UU Paten|Perangkat lunak murni (aturan atau metode yang hanya berisi program komputer) tidak dianggap invensi; invensi dengan efek teknis yang nyata dapat dipertimbangkan|
|Merek|UU Merek dan Indikasi Geografis|Nama dan logo aplikasi, perusahaan|
|Rahasia dagang|UU Rahasia Dagang|Algoritma internal, daftar pelanggan, arsitektur yang dijaga kerahasiaannya|
|Desain industri|UU Desain Industri|Tampilan produk fisik|
|Desain tata letak sirkuit terpadu|UU DTLST|Desain chip|
|Nama domain|Pengelola nama domain (.id oleh PANDI)|Sengketa domain, penyalahgunaan nama pihak lain|

Rahasia dagang hanya terlindungi jika pemiliknya **menjaga kerahasiaannya** secara wajar, misalnya melalui perjanjian kerahasiaan dan kontrol akses.

## 8.3 Lisensi Perangkat Lunak

Lisensi adalah izin dari pemegang hak untuk menggunakan karya dengan syarat tertentu.

|Jenis|Ciri|Contoh|
|---|---|---|
|Proprietari|Kode tertutup, penggunaan sesuai perjanjian lisensi pengguna akhir|Perangkat lunak komersial|
|Sumber terbuka permisif|Boleh dipakai, diubah, dan didistribusikan, termasuk dalam produk tertutup, dengan syarat mencantumkan pemberitahuan hak cipta dan lisensi|MIT, BSD, Apache 2.0|
|Sumber terbuka _copyleft_|Turunan yang didistribusikan harus dilisensikan dengan lisensi sejenis dan menyediakan kode sumber|GPL|
|_Copyleft_ jaringan|Kewajiban berlaku juga bila perangkat lunak digunakan sebagai layanan lewat jaringan|AGPL|
|Lisensi konten|Untuk karya non-kode|Creative Commons|

Ringkasan perbandingan praktis:

|Lisensi|Boleh dipakai komersial|Boleh digabung ke produk tertutup|Wajib membuka kode turunan|
|---|---|---|---|
|MIT / BSD|Ya|Ya|Tidak|
|Apache 2.0|Ya (termasuk hibah paten)|Ya|Tidak|
|GPL|Ya|Umumnya tidak jika didistribusikan|Ya, untuk karya turunan yang didistribusikan|
|AGPL|Ya|Umumnya tidak|Ya, termasuk jika dipakai sebagai layanan jaringan|

Tabel ini penyederhanaan. Penafsiran "karya turunan" dan penggabungan dinamis atau statis dapat rumit. Untuk produk komersial, tinjau teks lisensi atau minta nasihat hukum.

### Praktik Kepatuhan Lisensi

1. **Inventarisasi dependensi** dengan _Software Bill of Materials (SBOM)_, termasuk dependensi transitif.
2. **Catat lisensi** setiap komponen dengan pengenal standar SPDX (contoh: `MIT`, `Apache-2.0`, `GPL-3.0-only`).
3. **Tetapkan kebijakan** lisensi yang diizinkan dan dilarang untuk produk Anda.
4. **Otomasi** pemeriksaan di CI/CD dengan alat pemindai lisensi.
5. **Penuhi kewajiban atribusi**, misalnya berkas NOTICE atau halaman "Lisensi pihak ketiga".

Contoh penanda lisensi pada berkas kode:

```python
# SPDX-License-Identifier: Apache-2.0
# Hak Cipta (c) 2026 Nama Perusahaan
```

## 8.4 Kekayaan Intelektual dan Kecerdasan Artifisial

Pertanyaan yang masih berkembang:

- **Siapa pencipta karya yang dihasilkan AI?** Karena pencipta menurut UU Hak Cipta adalah manusia, karya yang dihasilkan sepenuhnya oleh AI tanpa kontribusi kreatif manusia menimbulkan ketidakpastian pelindungan. Kontribusi manusia yang signifikan (pemilihan, penyuntingan, pengarahan) lebih mudah diklaim.
- **Data pelatihan.** Apakah penggunaan karya berhak cipta untuk melatih model diperbolehkan masih diperdebatkan di berbagai negara dan belum diatur tegas di Indonesia.
- **Kode yang dihasilkan AI.** Periksa kebijakan lisensi alat yang dipakai, dan tinjau kode untuk kemungkinan kemiripan dengan kode berlisensi tertentu.

Praktik aman: tinjau kode hasil AI seperti kode dari kontributor eksternal, jalankan pemindai lisensi, dan dokumentasikan penggunaan alat AI sesuai kebijakan organisasi.

## Ringkasan Bab 8

- Program komputer dilindungi hak cipta secara otomatis, selama 50 tahun sejak pertama kali diumumkan.
- Kode tanpa lisensi tidak bebas dipakai.
- Lisensi permisif dan _copyleft_ membawa kewajiban berbeda. Kelola dengan SBOM dan pemindai lisensi.
- Status hak cipta karya AI masih berkembang.

## Latihan Bab 8

1. Anda mengambil fungsi dari sebuah repositori tanpa berkas lisensi untuk produk komersial. Apa risikonya?
2. Bandingkan MIT dan GPL dari sisi kewajiban bagi perusahaan yang menjual produk tertutup.
3. Seorang karyawan menulis aplikasi di luar jam kerja tetapi menggunakan aset kantor. Siapa kemungkinan pemegang hak cipta, dan apa yang perlu diperiksa?
4. Susun kebijakan singkat penggunaan kode hasil AI di tim Anda (lima butir).

---

# Bab 9. Transaksi Elektronik, E-Commerce, Fintech, dan Kontrak Digital

## Tujuan Pembelajaran

- Memahami keabsahan kontrak elektronik dan syarat sahnya.
- Mengenali aturan perdagangan melalui sistem elektronik (PMSE).
- Memahami perlindungan konsumen dan klausul baku.
- Mengenali kerangka pengaturan fintech dan aset digital.

## 9.1 Kontrak Elektronik

Kontrak elektronik adalah perjanjian para pihak yang dibuat melalui sistem elektronik. Contoh sehari-hari: menyetujui "Syarat dan Ketentuan" saat mendaftar, membeli barang di marketplace, atau menandatangani perjanjian dengan tanda tangan elektronik.

Syarat sah perjanjian (KUH Perdata) tetap berlaku:

1. Sepakat mereka yang mengikatkan diri.
2. Kecakapan untuk membuat perikatan.
3. Suatu hal tertentu.
4. Suatu sebab yang halal.

Bentuk klik: _click-wrap_ (pengguna mengklik "Saya setuju") umumnya lebih mudah dibuktikan daripada _browse-wrap_ (hanya menampilkan tautan syarat tanpa tindakan persetujuan).

**Sudut pandang developer:** rekam persetujuan (versi dokumen, waktu, ID pengguna, jenis perangkat) dan tampilkan perubahan syarat sebelum berlaku.

## 9.2 Klausul Baku dan Perlindungan Konsumen

**UU Nomor 8 Tahun 1999 tentang Perlindungan Konsumen** berlaku juga pada transaksi daring. Prinsipnya:

- Konsumen berhak atas keamanan, informasi yang benar dan jelas, memilih, didengar keluhannya, dan mendapat kompensasi atau ganti rugi.
- Pelaku usaha dilarang mencantumkan klausul baku tertentu, misalnya yang mengalihkan tanggung jawab pelaku usaha, atau menyatakan bahwa pelaku usaha berhak mengubah aturan secara sepihak setelah konsumen membeli.
- Sengketa konsumen dapat diselesaikan melalui Badan Penyelesaian Sengketa Konsumen (BPSK) atau pengadilan.

Contoh klausa yang bermasalah:

> "Perusahaan dapat mengubah seluruh syarat kapan saja tanpa pemberitahuan dan pengguna dianggap setuju."

Klausa seperti ini berpotensi bertentangan dengan larangan klausul baku. Alternatif yang lebih patut: pemberitahuan perubahan beserta masa tenggang dan hak pengguna untuk berhenti.

## 9.3 Perdagangan Melalui Sistem Elektronik (PMSE)

Dasar utama: **Peraturan Pemerintah Nomor 80 Tahun 2019 tentang PMSE** dan **Peraturan Menteri Perdagangan Nomor 31 Tahun 2023** tentang perizinan usaha, periklanan, pembinaan, dan pengawasan pelaku usaha dalam PMSE.

Poin umum:

- Pelaku usaha PMSE wajib menyediakan informasi yang benar tentang identitas, barang atau jasa, harga, syarat, dan kebijakan pengembalian.
- Penyelenggara PMSE (_marketplace_) memiliki kewajiban terhadap pedagang dan konsumen di platformnya, termasuk menyediakan mekanisme pengaduan dan memastikan keamanan transaksi.
- Pengaturan khusus mencakup perdagangan sosial (_social commerce_) sehingga platform sosial tidak boleh sekaligus berfungsi tanpa batas sebagai penyelenggara transaksi dan perdagangan tanpa memenuhi ketentuan yang ditetapkan.
- Pelaku usaha luar negeri yang memenuhi kriteria tertentu dapat diwajibkan menunjuk perwakilan di Indonesia.

## 9.4 Aspek Pajak (Gambaran Umum)

Pajak digital mencakup antara lain PPN atas barang atau jasa digital dari luar negeri yang dipungut oleh pelaku usaha yang ditunjuk, serta pajak penghasilan. Aturan pajak, termasuk atas aset kripto dan transaksi digital, sering diperbarui. Pastikan Anda memeriksa peraturan Direktorat Jenderal Pajak yang berlaku, atau berkonsultasi dengan konsultan pajak.

## 9.5 Fintech dan Aset Digital

|Bidang|Regulator|Catatan|
|---|---|---|
|Pembayaran, uang elektronik, QRIS|Bank Indonesia|Perizinan penyelenggara jasa pembayaran, standar keamanan|
|Pinjaman daring (LPBBTI atau pinjol)|OJK|Wajib berizin, pembatasan akses data pribadi, aturan penagihan|
|Aset keuangan digital dan aset kripto|OJK (sejak pengalihan pengawasan dari Bappebti pada awal 2025 berdasarkan UU P2SK)|Aturan perdagangan, penyimpanan, dan pelindungan konsumen|
|Penghimpunan dana (_equity crowdfunding_, urun dana)|OJK|Batasan penawaran dan kewajiban keterbukaan|

Layanan yang tidak berizin (pinjol ilegal, investasi bodong) dikoordinasikan penanganannya oleh satuan tugas lintas lembaga, antara lain Satgas PASTI. Periksa daftar penyelenggara berizin di situs resmi OJK dan Bank Indonesia sebelum menggunakan atau membangun layanan keuangan digital.

**Sudut pandang developer:** jika aplikasi Anda menyentuh uang pengguna (pembayaran, dompet, pinjaman, investasi), tanyakan terlebih dahulu apakah kegiatan tersebut memerlukan izin. Membangun fitur "kirim dan simpan saldo" tanpa izin dapat dianggap menyelenggarakan jasa keuangan tanpa izin.

## 9.6 Kontrak Pintar dan Blockchain

Kontrak pintar (_smart contract_) adalah program yang menjalankan ketentuan secara otomatis pada blockchain. Dari sisi hukum:

- Kode saja tidak otomatis menjadi kontrak sah; yang menentukan adalah ada atau tidaknya kesepakatan, kecakapan, objek, dan sebab yang halal.
- Kesalahan kode (_bug_) dapat menimbulkan kerugian yang tidak dapat dibatalkan. Siapa yang menanggung perlu diatur dalam perjanjian pendukung.
- Pencatatan di blockchain bersifat sulit diubah, bertentangan dengan hak penghapusan data pribadi. Hindari menyimpan data pribadi langsung di rantai. Simpan di luar rantai dan hanya taruh hash atau referensi.

## 9.7 Penyelesaian Sengketa

Pilihan: negosiasi, mediasi, arbitrase, pengadilan, atau penyelesaian sengketa daring (_online dispute resolution_). Kontrak sebaiknya memuat klausul pilihan hukum dan forum penyelesaian sengketa.

## Ringkasan Bab 9

- Kontrak elektronik sah bila memenuhi syarat sahnya perjanjian.
- Klausul baku yang berat sebelah dapat dibatalkan, dan pelaku usaha PMSE punya kewajiban informasi yang jelas.
- Layanan keuangan digital umumnya memerlukan izin OJK atau Bank Indonesia.

## Latihan Bab 9

1. Tinjau syarat dan ketentuan sebuah aplikasi yang Anda gunakan. Temukan dua klausul yang berpotensi bermasalah dan jelaskan alasannya.
2. Apa perbedaan _click-wrap_ dan _browse-wrap_? Mana yang lebih kuat sebagai bukti persetujuan?
3. Anda ingin menambahkan fitur dompet digital ke aplikasi Anda. Apa pertanyaan hukum yang harus dijawab sebelum membangunnya?
4. Mengapa menyimpan data pribadi langsung di blockchain publik bermasalah?

---

# Bab 10. Konten Digital, Kebebasan Berekspresi, dan Pelindungan Anak

## Tujuan Pembelajaran

- Memahami kebebasan berekspresi dan batasannya.
- Memahami tanggung jawab platform atas konten.
- Memahami pelindungan anak di ruang digital menurut PP TUNAS.
- Menerapkan fitur teknis yang mendukung kepatuhan.

## 10.1 Kebebasan Berekspresi dan Batasannya

UUD 1945 menjamin hak untuk berkomunikasi, memperoleh, dan menyampaikan informasi. Hak ini dapat dibatasi melalui undang-undang untuk menjamin pengakuan dan penghormatan hak orang lain, dan memenuhi tuntutan moral, nilai agama, keamanan, dan ketertiban umum.

Beberapa konsep yang sering membingungkan:

|Konsep|Arti|
|---|---|
|Kritik|Penilaian atau koreksi atas kebijakan atau perilaku, biasanya disertai fakta dan alasan; dilindungi|
|Opini|Pendapat pribadi yang bukan pernyataan fakta|
|Pencemaran nama baik|Menuduhkan suatu hal tertentu yang menyerang kehormatan seseorang agar diketahui umum|
|Fitnah|Tuduhan yang diketahui tidak benar atau tidak dapat dibuktikan kebenarannya|
|Ujaran kebencian|Menyebarkan kebencian atau permusuhan berdasarkan SARA|
|Hoaks (disinformasi)|Informasi bohong yang disebarkan; pidana hanya jika memenuhi unsur-unsur tertentu, misalnya merugikan konsumen atau menimbulkan kerusuhan menurut tafsir pengadilan|

Perbedaan kritik dan penghinaan terus dibahas, terutama setelah KUHP baru berlaku sejak 2 Januari 2026. Kriteria praktis yang sering dipakai: apakah pernyataan menyasar kebijakan atau perilaku publik dengan dasar yang dapat dipertanggungjawabkan (kritik) atau menyerang pribadi dengan tuduhan tanpa dasar (penghinaan).

## 10.2 Tanggung Jawab Platform

Platform digital umumnya tidak serta-merta bertanggung jawab atas setiap unggahan pengguna, tetapi wajib melakukan langkah wajar:

1. Menyediakan mekanisme pelaporan konten.
2. Menindaklanjuti laporan dan perintah penghapusan dalam batas waktu yang ditetapkan peraturan (Bab 4).
3. Tidak memfasilitasi konten terlarang.
4. Menjaga transparansi aturan komunitas.

**Sudut pandang developer (alur moderasi):**

```
Pengguna melapor konten
   -> Sistem mencatat laporan (ID, waktu, alasan, tautan, bukti)
   -> Klasifikasi otomatis (prioritas tinggi untuk anak, terorisme, kekerasan)
   -> Tinjauan moderator manusia
   -> Tindakan: biarkan / sembunyikan / hapus / suspend akun
   -> Pemberitahuan ke pelapor dan pengunggah (dengan hak banding)
   -> Catat keputusan dalam log audit
```

## 10.3 Pelindungan Anak di Ruang Digital (PP TUNAS)

**Peraturan Pemerintah Nomor 17 Tahun 2025 tentang Tata Kelola Penyelenggaraan Sistem Elektronik dalam Pelindungan Anak**, disingkat **PP TUNAS**, ditandatangani Presiden pada 28 Maret 2025. Alasannya: hampir separuh pengguna internet Indonesia adalah anak dan remaja di bawah 18 tahun.

Inti kewajiban bagi PSE:

- Melakukan **penilaian risiko** produk terhadap anak.
- Menerapkan **verifikasi usia** dan membatasi akses sesuai kelompok usia dan tingkat risiko layanan.
- Menyediakan **fitur pengamanan**: penyaringan konten, kontrol orang tua, pembatasan fitur berisiko, pengaturan akun anak.
- Menjaga **data pribadi anak** dengan ketat, termasuk batasan pemrofilan untuk tujuan komersial.
- Memberikan **edukasi** dan mekanisme pengaduan.

> **Status regulasi:** PP TUNAS memiliki masa penyesuaian bagi penyelenggara dan aturan pelaksana yang masih disusun. Pemberitaan menyebut masa penyesuaian dua tahun sejak penetapan, sementara pemberitaan lain menyebut penerapan mulai Maret 2026. Pemerintah juga menyatakan harapan penerapan penuh pada 2026. Karena sumber berbeda, baca teks PP dan peraturan pelaksana terbaru untuk kepastian tenggat. Beberapa pihak, termasuk asosiasi industri dan anggota DPD, meminta keseimbangan antara pelindungan anak, keamanan data (karena verifikasi usia dapat menimbulkan penyimpanan data pribadi skala besar), dan keberlanjutan ekosistem digital.

**Sudut pandang developer:** verifikasi usia adalah tantangan teknik sekaligus privasi. Pertimbangkan pendekatan yang meminimalkan data: verifikasi oleh pihak ketiga tepercaya yang hanya mengembalikan hasil "memenuhi usia" tanpa menyimpan dokumen identitas di sistem Anda.

## 10.4 Kekerasan Seksual Berbasis Elektronik dan Konten Intim

UU Tindak Pidana Kekerasan Seksual (UU TPKS) mengatur kekerasan seksual berbasis elektronik, misalnya merekam atau menyebarkan konten bermuatan seksual tanpa persetujuan, atau mengancam menyebarkannya. Korban berhak atas pelindungan, penghapusan konten, dan pemulihan. Platform sebaiknya menyediakan jalur cepat penghapusan untuk kasus ini.

## 10.5 Disinformasi, Deepfake, dan Pemilu

Deepfake (media sintetis yang meniru wajah atau suara seseorang) dapat melanggar:

- Pelindungan data pribadi (wajah dan suara adalah data yang dapat mengidentifikasi orang, termasuk bila berupa biometrik).
- Pencemaran nama baik, penipuan, atau pemerasan.
- Hak atas citra dan kehormatan.

Dalam konteks pemilu, penyebaran informasi bohong dapat dikenai ketentuan hukum pemilu dan hukum pidana. Platform dan pengembang alat AI generatif perlu mempertimbangkan fitur penandaan konten sintetis dan pembatasan penyalahgunaan.

## 10.6 Hak Atas Informasi Publik

UU Keterbukaan Informasi Publik mewajibkan badan publik membuka informasi tertentu. Aplikasi pemerintah perlu menyediakan informasi yang dapat diakses, dengan tetap menjaga informasi yang dikecualikan, termasuk data pribadi.

## Ringkasan Bab 10

- Kebebasan berekspresi dijamin, tetapi dapat dibatasi untuk melindungi hak orang lain dan ketertiban umum.
- Platform wajib menyediakan mekanisme pelaporan dan menindaklanjuti perintah penghapusan.
- PP TUNAS menetapkan kewajiban pelindungan anak bagi PSE, termasuk verifikasi usia dan fitur pengamanan.

## Latihan Bab 10

1. Bedakan kritik terhadap kebijakan pemerintah dan pencemaran nama baik. Beri contoh kalimat untuk masing-masing.
2. Rancang fitur verifikasi usia yang meminimalkan penyimpanan data pribadi.
3. Mengapa jalur penghapusan cepat penting untuk kasus penyebaran konten intim tanpa persetujuan?

---

# Bab 11. Kecerdasan Artifisial dan Teknologi Baru

## Tujuan Pembelajaran

- Memahami posisi hukum Indonesia terhadap AI saat ini.
- Mengenali isu hukum utama AI: tanggung jawab, bias, privasi, hak cipta, transparansi.
- Membandingkan pendekatan global.
- Menerapkan daftar periksa tata kelola AI.

## 11.1 Posisi Hukum Indonesia

Indonesia hingga akhir 2026 belum memiliki undang-undang khusus tentang AI. Pengaturan yang ada tersebar:

- **UU ITE:** konsep agen elektronik dan kewajiban PSE menjadi pijakan. Pemerintah pernah menyatakan akan menggunakan UU ITE untuk mengatur pemanfaatan AI.
- **UU PDP:** berlaku untuk data pribadi yang digunakan dalam pelatihan dan operasi AI, termasuk hak keberatan atas keputusan otomatis.
- **UU Hak Cipta:** isu karya AI dan data pelatihan.
- **Aturan sektoral** (keuangan, kesehatan, dan lainnya) yang mulai menerbitkan pedoman.
- **Surat Edaran Menteri Komunikasi dan Informatika Nomor 9 Tahun 2023** tentang Etika Kecerdasan Artifisial: pedoman nilai (inklusivitas, kemanusiaan, keamanan, aksesibilitas, transparansi, kredibilitas dan akuntabilitas, pelindungan data pribadi, pembangunan dan lingkungan berkelanjutan, serta kekayaan intelektual). Bersifat pedoman, bukan sanksi pidana.
- **Strategi Nasional Kecerdasan Artifisial Indonesia 2020 sampai 2045.**

> **Status regulasi (informasi hingga September 2026):** Pemerintah menyiapkan dua Peraturan Presiden: Peta Jalan (_roadmap_) AI Nasional 2026 sampai 2029 dan Etika AI. Pada September 2026 pejabat Komdigi menyampaikan bahwa kedua Perpres tersebut "tinggal menunggu tanda tangan Presiden". Pendekatannya berbasis risiko, dengan klasifikasi penggunaan AI menjadi risiko tinggi, sedang, dan rendah. Proses penyusunan sempat tertunda karena pembahasan ulang dengan beberapa pihak, termasuk perusahaan asing. Penulis tidak dapat memastikan apakah kedua Perpres sudah ditandatangani dan diundangkan pada saat Anda membaca. Periksa JDIH.

## 11.2 Isu Hukum Utama AI

|Isu|Pertanyaan|Catatan|
|---|---|---|
|Pertanggungjawaban|Siapa yang menanggung jika AI menyebabkan kerugian: pengembang, penyedia, pengguna?|AI bukan subjek hukum. Tanggung jawab melekat pada manusia atau badan hukum di baliknya, tergantung peran dan kelalaian|
|Bias dan diskriminasi|Model menghasilkan keputusan yang merugikan kelompok tertentu|Risiko hukum: pelanggaran hak, tuntutan perdata, sanksi sektoral|
|Transparansi dan penjelasan|Dapatkah keputusan dijelaskan?|Terkait hak keberatan atas keputusan otomatis (UU PDP)|
|Privasi|Data pelatihan mengandung data pribadi? Model mengingat data?|Dasar pemrosesan, minimalisasi, penghapusan|
|Hak cipta|Data pelatihan dan keluaran|Bab 8|
|Keamanan|Serangan terhadap model (_prompt injection_, peracunan data, kebocoran model)|Termasuk kewajiban keamanan PSE|
|Konten sintetis|Deepfake, disinformasi|Bab 10|

## 11.3 Pendekatan Global

|Pendekatan|Ciri|Contoh|
|---|---|---|
|Regulasi komprehensif berbasis risiko|Kategori risiko, kewajiban bertingkat, larangan praktik tertentu|EU AI Act: mulai berlaku Agustus 2024 dengan penerapan bertahap, dengan kewajiban utama menyusul pada 2026 sampai 2027. Ada usulan penyesuaian jadwal sehingga periksa jadwal terbaru|
|Pedoman dan kerangka sukarela|Prinsip dan praktik terbaik|NIST AI Risk Management Framework, ISO/IEC 42001, OECD AI Principles, ASEAN Guide on AI Governance and Ethics (2024)|
|Pendekatan sektoral|Aturan AI mengikuti sektor|Banyak negara, termasuk pada keuangan dan kesehatan|

## 11.4 Daftar Periksa Tata Kelola AI untuk Tim Pengembang

1. **Tujuan dan batas penggunaan** didokumentasikan.
2. **Klasifikasi risiko:** apakah keputusan berdampak signifikan pada orang (kredit, kesehatan, pekerjaan, pendidikan)?
3. **Asal data pelatihan:** sumber, lisensi, persetujuan, dan pembersihan data pribadi.
4. **Evaluasi bias dan kinerja** pada kelompok relevan, dengan dokumentasi (_model card_).
5. **Pengawasan manusia** (_human in the loop_) untuk keputusan berdampak tinggi.
6. **Transparansi kepada pengguna:** beri tahu bahwa mereka berinteraksi dengan AI, jelaskan keterbatasan.
7. **Keamanan:** uji ketahanan terhadap serangan, batasi data sensitif dalam _prompt_ dan log.
8. **Pencatatan dan pemantauan:** simpan log keputusan yang dapat diaudit.
9. **Mekanisme keberatan** bagi pengguna terdampak.
10. **Rencana respons insiden** khusus AI.

## 11.5 Teknologi Baru Lainnya

- **Komputasi awan (_cloud_):** pahami model tanggung jawab bersama. Penyedia mengamankan infrastruktur, Anda mengamankan konfigurasi, data, dan akses. Perhatikan lokasi data, kewajiban lintas negara, SLA, dan klausul keluar (_exit_).
- **IoT:** perangkat yang mengumpulkan data pribadi (kamera, wearable) tunduk pada UU PDP. Pastikan pembaruan keamanan dan kata sandi bawaan tidak lemah.
- **Biometrik:** data spesifik. Gunakan hanya jika perlu, dengan persetujuan dan pelindungan lebih ketat.
- **Kriptografi pasca-kuantum:** organisasi yang menyimpan data jangka panjang perlu merencanakan migrasi. Belum ada kewajiban umum, tetapi tren standar bergerak ke arah ini.

## Ringkasan Bab 11

- Belum ada UU khusus AI di Indonesia. Pengaturan bertumpu pada UU ITE, UU PDP, hukum sektoral, dan pedoman etika. Dua Perpres AI sedang difinalisasi.
- AI bukan subjek hukum, sehingga tanggung jawab melekat pada manusia dan organisasi.
- Pengembang perlu menerapkan tata kelola praktis: dokumentasi data, uji bias, pengawasan manusia, keamanan, dan transparansi.

## Latihan Bab 11

1. Sebuah model penilaian kredit menolak pelamar dari wilayah tertentu secara tidak proporsional. Identifikasi isu hukum dan langkah mitigasi.
2. Jelaskan mengapa AI tidak dapat dipidana atau digugat, dan siapa yang berpotensi bertanggung jawab.
3. Terapkan daftar periksa 11.4 pada aplikasi chatbot layanan pelanggan buatan Anda.
4. Bandingkan pendekatan berbasis risiko dengan pendekatan sukarela. Kapan masing-masing tepat?

---

# Bab 12. Kebijakan TI dalam Organisasi dan Program Kepatuhan

## Tujuan Pembelajaran

- Memahami siklus kebijakan publik di bidang TI.
- Menyusun hierarki dokumen kebijakan organisasi.
- Membangun program kepatuhan (_compliance_) sederhana.
- Memahami peran DPO, CISO, dan tim hukum.

## 12.1 Kebijakan Publik di Bidang TI

Siklus kebijakan publik:

1. **Penetapan agenda:** isu diangkat (contoh: maraknya kebocoran data).
2. **Perumusan:** alternatif disusun (RUU, RPP, Perpres), melibatkan konsultasi publik.
3. **Adopsi:** ditetapkan menjadi peraturan.
4. **Implementasi:** dijalankan lembaga dan pelaku usaha.
5. **Evaluasi:** dikaji dan diperbaiki (contoh: perubahan UU ITE).

Anda sebagai warga dan profesional dapat berpartisipasi pada tahap perumusan dengan menyampaikan masukan saat uji publik, melalui asosiasi profesi, atau melalui penelitian.

Kebijakan nasional TI yang sering dirujuk: transformasi digital pemerintah (SPBE), Satu Data Indonesia, Pusat Data Nasional, identitas digital kependudukan, Strategi Nasional Kecerdasan Artifisial, dan peta jalan ekonomi digital.

## 12.2 Hierarki Dokumen Kebijakan Organisasi

|Tingkat|Dokumen|Isi|Contoh|
|---|---|---|---|
|1|Kebijakan|Pernyataan arah dari pimpinan|Kebijakan Keamanan Informasi|
|2|Standar|Persyaratan yang terukur|Standar kata sandi: minimal 12 karakter dan MFA|
|3|Prosedur|Langkah rinci siapa melakukan apa|Prosedur pencabutan akses karyawan keluar|
|4|Pedoman|Saran praktik terbaik|Pedoman pengamanan laptop saat perjalanan|

Contoh dokumen kebijakan yang umum:

- Kebijakan penggunaan yang dapat diterima (_acceptable use policy_)
- Kebijakan kata sandi dan autentikasi
- Kebijakan klasifikasi dan penanganan data
- Kebijakan retensi dan pemusnahan data
- Kebijakan cadangan dan pemulihan bencana
- Kebijakan respons insiden
- Kebijakan perangkat pribadi (_BYOD_)
- Kebijakan penggunaan AI generatif
- Kebijakan privasi (untuk publik)

## 12.3 Membangun Program Kepatuhan

Langkah praktis:

1. **Inventarisasi regulasi (register hukum).** Daftar peraturan yang berlaku bagi organisasi, siapa pemilik kepatuhan, dan tanggal tinjauan.
2. **Analisis kesenjangan (_gap analysis_).** Bandingkan kondisi saat ini dengan persyaratan.
3. **Penilaian risiko.** Tentukan prioritas berdasarkan dampak dan kemungkinan.
4. **Rencana pemenuhan.** Tentukan kontrol teknis dan organisasi, tenggat, dan penanggung jawab.
5. **Implementasi kontrol.**
6. **Pelatihan dan kesadaran.**
7. **Pemantauan dan audit internal.**
8. **Perbaikan berkelanjutan** dan pembaruan saat regulasi berubah.

### Contoh Register Regulasi (Cuplikan)

|Regulasi|Persyaratan relevan|Kontrol teknis|Pemilik|Tinjauan|
|---|---|---|---|---|
|UU PDP|Dasar pemrosesan, hak subjek data, notifikasi insiden|Manajemen persetujuan, portal hak subjek, rencana respons insiden|DPO|Per kuartal|
|UU ITE dan PP 71/2019|Sistem andal dan aman, moderasi konten|Pemantauan, pencadangan, alur moderasi|CTO|Per tahun|
|PP TUNAS (jika melayani anak)|Verifikasi usia, kontrol orang tua|Layanan verifikasi, pengaturan akun anak|Produk|Per kuartal|
|UU Hak Cipta dan lisensi|Kepatuhan lisensi|SBOM, pemindai lisensi|Engineering|Per rilis|

## 12.4 Peran dalam Organisasi

|Peran|Fokus|
|---|---|
|Pejabat atau petugas pelindungan data pribadi (DPO)|Memantau kepatuhan PDP, penasihat, titik kontak dengan subjek data dan lembaga|
|CISO (_Chief Information Security Officer_)|Strategi dan operasi keamanan informasi|
|Penasihat hukum (_legal counsel_)|Tafsir hukum, kontrak, hubungan dengan regulator|
|Kepatuhan (_compliance officer_)|Memastikan kebijakan dan kontrol berjalan|
|Auditor TI|Menilai efektivitas kontrol secara independen|
|Developer dan DevOps|Menerapkan kontrol dalam kode dan infrastruktur|

Prinsip pembagian: DPO sebaiknya tidak menentukan sendiri tujuan dan cara pemrosesan sehingga menghindari konflik kepentingan. DPO memberi masukan.

## 12.5 Templat Kebijakan Penggunaan AI Generatif (Contoh)

1. **Tujuan:** memandu penggunaan alat AI generatif yang aman dan sesuai hukum.
2. **Alat yang disetujui:** daftar alat dan akun korporat yang diizinkan.
3. **Data yang dilarang dimasukkan:** data pribadi spesifik, rahasia dagang, kredensial, dokumen klien yang dilindungi perjanjian kerahasiaan.
4. **Tinjauan manusia:** keluaran AI untuk kode, hukum, keuangan, atau komunikasi eksternal wajib ditinjau manusia.
5. **Atribusi dan lisensi:** periksa kemungkinan kemiripan dengan karya berhak cipta, dan catat penggunaan AI pada proyek.
6. **Pelaporan insiden:** laporkan kebocoran data atau keluaran berbahaya.
7. **Pelatihan:** pelatihan wajib tahunan.
8. **Sanksi:** pelanggaran kebijakan dapat berujung tindakan disiplin.

## Ringkasan Bab 12

- Kepatuhan adalah proses berkelanjutan: inventarisasi, analisis kesenjangan, kontrol, pelatihan, audit.
- Dokumen kebijakan berjenjang: kebijakan, standar, prosedur, pedoman.
- Peran DPO, CISO, hukum, dan developer saling melengkapi.

## Latihan Bab 12

1. Susun register regulasi untuk startup aplikasi kesehatan dengan lima baris.
2. Tulis satu standar dan satu prosedur turunan dari kebijakan "Semua akses administratif wajib memakai autentikasi multifaktor".
3. Mengapa seorang DPO sebaiknya tidak merangkap sebagai kepala yang menentukan tujuan pemrosesan data?

---

# Bab 13. Etika Profesi dan Tanggung Jawab Profesional

## Tujuan Pembelajaran

- Memahami kode etik profesi TI.
- Mengenali dilema etika umum.
- Memahami tanggung jawab profesional dalam kontrak kerja dan freelance.

## 13.1 Mengapa Etika Diperlukan Selain Hukum

Hukum menetapkan batas minimum. Banyak perbuatan legal tetapi tidak etis, misalnya menggunakan _dark pattern_ untuk menipu pengguna agar berlangganan. Etika profesi membantu Anda mengambil keputusan di area abu-abu.

## 13.2 Prinsip dalam Kode Etik Profesi

Kode etik ACM (_Association for Computing Machinery_) dan IEEE memuat prinsip serupa:

1. Berkontribusi pada kesejahteraan masyarakat dan manusia.
2. Menghindari bahaya.
3. Jujur dan dapat dipercaya.
4. Adil dan tidak diskriminatif.
5. Menghormati hak kekayaan intelektual.
6. Menghormati privasi.
7. Menjaga kerahasiaan.
8. Bekerja secara kompeten dan mengakui batas kompetensi.
9. Bertanggung jawab atas kerja yang dilakukan.
10. Menyampaikan risiko kepada pihak yang berkepentingan.

Di Indonesia, organisasi profesi dan sertifikasi kompetensi (misalnya melalui skema BNSP dan SKKNI) juga menetapkan standar kompetensi dan etika.

## 13.3 Dilema Etika Umum dan Cara Berpikirnya

|Dilema|Pertanyaan bantu|
|---|---|
|Atasan meminta mengumpulkan data pengguna melebihi kebutuhan|Apakah ada dasar hukum dan tujuan jelas? Bagaimana jika pengguna mengetahuinya?|
|Menemukan celah keamanan serius pada produk perusahaan, dan manajemen ingin menunda|Apa dampak bagi pengguna jika dieksploitasi? Siapa yang harus diberi tahu?|
|Diminta memakai kode berlisensi tidak cocok demi tenggat|Apa risiko hukum bagi perusahaan dan Anda? Apa alternatifnya?|
|Mendesain fitur yang mendorong kecanduan|Apakah fitur ini menghormati otonomi pengguna, terutama anak?|
|Membangun sistem pengawasan karyawan|Apakah proporsional, transparan, dan memiliki dasar hukum?|

Pendekatan sistematis: (1) kenali fakta, (2) identifikasi pihak terdampak, (3) periksa hukum dan kode etik, (4) pertimbangkan alternatif, (5) putuskan dan dokumentasikan, (6) eskalasi bila perlu.

## 13.4 Tanggung Jawab dalam Kontrak Kerja dan Freelance

Hal penting yang sebaiknya diatur dalam kontrak pengembangan perangkat lunak:

|Butir|Mengapa penting|
|---|---|
|Ruang lingkup dan penerimaan hasil|Menghindari sengketa tentang "selesai"|
|Kepemilikan hak cipta|Apakah dialihkan penuh ke klien, atau Anda memberi lisensi?|
|Komponen pihak ketiga dan sumber terbuka|Siapa yang menanggung kepatuhan lisensi?|
|Kerahasiaan|Data klien dan kode sumber|
|Pelindungan data pribadi|Siapa pengendali dan prosesor, kewajiban keamanan|
|Garansi dan batas tanggung jawab|Berapa lama perbaikan bug, batas ganti rugi|
|Pemeliharaan dan dukungan|Biaya dan tingkat layanan|
|Pengakhiran kontrak|Penyerahan kode, pembayaran|
|Hukum dan forum|Hukum Indonesia, mekanisme sengketa|

Catatan: dalam hubungan kerja, hak cipta atas karya yang dibuat sebagai bagian dari tugas pada umumnya dipegang pemberi kerja. Untuk pekerjaan lepas, hak cipta pada dasarnya tetap pada pencipta kecuali dialihkan secara tertulis. Selalu tuangkan secara tertulis.

## 13.5 Pelaporan Pelanggaran dan Perlindungan

Jika Anda menemukan pelanggaran hukum atau etika di organisasi, gunakan jalur internal (atasan, kepatuhan, saluran pelaporan pelanggaran). Dokumentasikan fakta secara obyektif. Jangan mengambil atau menyebarkan data rahasia di luar jalur yang sah, karena tindakan tersebut dapat melanggar kerahasiaan dan hukum lain.

## Ringkasan Bab 13

- Etika melengkapi hukum untuk area yang tidak diatur tegas.
- Kode etik ACM dan IEEE menekankan kesejahteraan publik, kejujuran, privasi, kompetensi, dan tanggung jawab.
- Kontrak tertulis yang jelas melindungi Anda dan klien.

## Latihan Bab 13

1. Berikan contoh perbuatan yang legal tetapi tidak etis dalam desain antarmuka aplikasi.
2. Susun lima klausul penting yang akan Anda minta dalam kontrak freelance pengembangan aplikasi.
3. Manajemen menolak menambal celah keamanan karena mengejar peluncuran. Apa langkah eskalasi Anda?

---

# Bab 14. Perspektif Internasional dan Perbandingan

## Tujuan Pembelajaran

- Mengenali regulasi internasional utama yang dapat berlaku pada layanan digital Anda.
- Memahami konsep transfer data lintas negara.
- Membandingkan pendekatan beberapa negara.

## 14.1 Regulasi Data Pribadi di Dunia

|Yurisdiksi|Regulasi|Catatan|
|---|---|---|
|Uni Eropa|GDPR|Berlaku ekstrateritorial bagi pihak yang menawarkan barang atau jasa kepada orang di UE atau memantau perilaku mereka. Denda hingga 20 juta euro atau 4 persen omzet global|
|Singapura|PDPA|Ada kewajiban notifikasi pelanggaran dan penunjukan DPO|
|Malaysia|PDPA (diubah pada 2024)|Penguatan kewajiban termasuk notifikasi kebocoran dan penunjukan petugas pelindungan data|
|Thailand|PDPA|Struktur mirip GDPR|
|Vietnam|Undang-undang Pelindungan Data Pribadi|Disahkan pada 2025 dengan rencana berlaku pada awal 2026; periksa status|
|Tiongkok|PIPL|Pembatasan transfer data lintas batas yang ketat|
|Amerika Serikat|Tidak ada UU federal menyeluruh; undang-undang negara bagian (misalnya California)|Pendekatan sektoral dan negara bagian|

Daftar ini ringkasan. Status dan detail perlu diverifikasi pada sumber resmi masing-masing negara.

## 14.2 Transfer Data Lintas Negara

UU PDP mengatur bahwa pengendali data yang mentransfer data ke luar wilayah Indonesia wajib memastikan negara penerima memiliki tingkat pelindungan setara atau lebih tinggi, atau memberikan jaminan pelindungan yang memadai dan mengikat, atau memperoleh persetujuan subjek data. Praktik yang lazim: klausul kontrak standar, perjanjian pemrosesan data, dan penilaian risiko.

**Sudut pandang developer:** pertimbangkan lokasi region cloud sejak awal. Memindahkan data setelah sistem berjalan jauh lebih mahal.

## 14.3 Regulasi Platform dan Anak di Negara Lain

- **Uni Eropa:** _Digital Services Act_ dan _Digital Markets Act_ mengatur tanggung jawab platform dan persaingan.
- **Australia:** menetapkan batas usia minimum 16 tahun untuk akun media sosial tertentu yang mulai berlaku pada Desember 2025. Model ini menjadi rujukan diskusi PP TUNAS di Indonesia.
- **Perbandingan:** banyak negara bergerak menuju verifikasi usia dan fitur keamanan anak, dengan perdebatan tentang privasi dan efektivitas.

## 14.4 Kerja Sama Ekonomi Digital

- **ASEAN Digital Economy Framework Agreement (DEFA):** kerangka kerja sama ekonomi digital kawasan, mencakup aliran data, pembayaran, dan keamanan siber. Periksa status finalisasi dan ratifikasi.
- Perjanjian perdagangan bebas yang memuat bab perdagangan digital.

## 14.5 Konvensi Kejahatan Siber

Konvensi Budapest dan Konvensi PBB tentang Kejahatan Siber menjadi dasar kerja sama internasional dalam penyelidikan, ekstradisi, dan bantuan hukum timbal balik. Dalam praktik, kerja sama sering lewat bantuan hukum timbal balik (_mutual legal assistance_) yang membutuhkan waktu, sehingga kecepatan pelestarian bukti penting.

## Ringkasan Bab 14

- Layanan digital lintas negara dapat tunduk pada beberapa hukum sekaligus.
- Transfer data lintas negara membutuhkan dasar hukum dan jaminan pelindungan.
- Banyak negara bergerak ke arah pelindungan anak dan regulasi platform yang lebih ketat.

## Latihan Bab 14

1. Aplikasi Anda memiliki pengguna di Indonesia dan Jerman. Regulasi apa saja yang berpotensi berlaku?
2. Susun daftar tiga pertanyaan sebelum memilih region cloud untuk menyimpan data pengguna Indonesia.
3. Mengapa kerja sama hukum internasional sering lambat, dan apa implikasinya bagi pelestarian bukti?

---

# Bab 15. Studi Kasus Terpadu

Kasus-kasus berikut **hipotetis** dan dirancang untuk latihan. Untuk setiap kasus, kerjakan dulu sendiri sebelum membaca panduan analisis.

## Kasus 1. Kebocoran Data Startup Kesehatan

**Cerita.** Startup "SehatKu" menyimpan hasil laboratorium dan KTP pengguna. Pada Senin pukul 09.00 tim keamanan menemukan basis data terbuka tanpa kata sandi akibat salah konfigurasi cloud. Data 200.000 pengguna diketahui diunduh pihak tidak dikenal.

**Pertanyaan.**

1. Jenis data apa yang terlibat dan mengapa risikonya tinggi?
2. Apa kewajiban hukum pasca-insiden?
3. Jenis tanggung jawab apa yang mungkin timbul?
4. Apa pencegahan teknis yang seharusnya ada?

**Panduan analisis.**

1. Data kesehatan, identitas, dan mungkin biometrik: kategori spesifik dalam UU PDP, sehingga dampak potensialnya lebih besar.
2. Pemberitahuan tertulis kepada subjek data dan lembaga paling lambat 3 x 24 jam, dengan informasi yang diperlukan; penahanan insiden; investigasi dan bukti (hash log, snapshot); koordinasi dengan CSIRT, regulator sektor kesehatan; komunikasi publik jika perlu.
3. Administratif (denda dan sanksi), perdata (gugatan ganti rugi dari pengguna), dan pidana terhadap pelaku pencuri data; potensi pertanggungjawaban perusahaan bila kelalaian terbukti.
4. Konfigurasi cloud yang aman (_policy as code_, pemindaian misconfiguration), enkripsi data, akses minimum, MFA, pemantauan, minimalisasi data, uji penetrasi berkala, dan rencana respons insiden.

## Kasus 2. Tangkapan Layar sebagai Bukti

**Cerita.** Rina menerima ancaman lewat aplikasi pesan. Ia mengambil tangkapan layar dan melapor ke polisi. Pelaku mengatakan tangkapan layar itu rekayasa.

**Pertanyaan.** Bagaimana Rina memperkuat bukti? Apa pasal yang mungkin relevan?

**Panduan.**

- Simpan perangkat asli dan percakapan aslinya, jangan hapus. Jangan hanya mengandalkan tangkapan layar. Catat nomor atau akun pelaku, waktu, dan konteks percakapan. Minta penyidik melakukan akuisisi forensik pada perangkat.
- Pasal tentang ancaman kekerasan atau menakut-nakuti yang ditujukan secara pribadi dan ketentuan pengancaman atau pemerasan dapat relevan, bergantung pada isi pesan. Penegak hukum menentukan kualifikasi.
- Perspektif developer: aplikasi pesan yang menyediakan ekspor percakapan berintegritas dan prosedur permintaan data resmi membantu pengguna.

## Kasus 3. Freelancer dan Kode Berlisensi GPL

**Cerita.** Dimas, freelancer, membuat aplikasi untuk klien dengan memakai pustaka berlisensi GPL, kemudian klien menjual aplikasi tersebut sebagai produk tertutup. Kontrak tidak mengatur lisensi.

**Pertanyaan.** Apa risikonya dan bagaimana mencegahnya?

**Panduan.** Distribusi produk yang menggabungkan kode GPL berpotensi mewajibkan pembukaan kode sumber turunan. Risiko: tuntutan pelanggaran lisensi dan hak cipta, dan sengketa antara klien dan Dimas. Pencegahan: inventarisasi dependensi (SBOM), pilih pustaka berlisensi permisif atau sesuai model bisnis, dokumentasikan, dan atur dalam kontrak siapa yang menanggung kepatuhan lisensi.

## Kasus 4. Chatbot AI Memberi Saran yang Merugikan

**Cerita.** Sebuah bank memasang chatbot AI. Chatbot menyatakan pelanggan "pasti disetujui" kreditnya, padahal ditolak, sehingga pelanggan membatalkan pembelian rumah dan mengalami kerugian.

**Pertanyaan.** Siapa yang bertanggung jawab? Apa kontrol yang diperlukan?

**Panduan.** AI bukan subjek hukum, jadi bank sebagai penyelenggara bertanggung jawab atas informasi yang disampaikan melalui agen elektroniknya, terutama bagi konsumen. Kontrol: batasan topik dan pernyataan terbatas, penyangkalan yang jelas bahwa keputusan kredit bukan oleh chatbot, pengalihan ke petugas manusia untuk topik berisiko, pengujian dan pemantauan, log percakapan, dan mekanisme pengaduan. Regulator sektor keuangan juga memperhatikan perlindungan konsumen.

## Kasus 5. Penguji Keamanan Tanpa Izin

**Cerita.** Bayu menemukan celah pada situs sebuah rumah sakit dan mengunduh 50 data pasien sebagai "bukti" lalu mengirim ke media.

**Pertanyaan.** Apa yang keliru dan bagaimana seharusnya?

**Panduan.** Akses tanpa izin dan pengambilan data pasien (data kesehatan: data spesifik) dapat melanggar larangan akses ilegal dan hukum pelindungan data. Mengirim data ke media memperbesar pelanggaran. Seharusnya: berhenti saat celah terkonfirmasi, mencatat bukti minimal tanpa membawa data pribadi, menghubungi rumah sakit atau CSIRT/BSSN lewat kanal resmi, memberi waktu perbaikan, dan tidak mengungkap publik sebelum diperbaiki.

## Proyek Akhir Mata Kuliah (Usulan)

Pilih sebuah aplikasi fiktif (misalnya aplikasi layanan kos, belajar daring, atau klinik). Susun paket kepatuhan:

1. Peta data (Bab 5).
2. Register regulasi dengan minimal enam regulasi yang berlaku (Bab 12).
3. Draf kebijakan privasi dan syarat dan ketentuan (Bab 9).
4. Rencana respons insiden dengan garis waktu 3 x 24 jam (Bab 5 dan 7).
5. Daftar lisensi dependensi (Bab 8).
6. Penilaian risiko AI jika ada fitur AI (Bab 11).
7. Presentasi 10 menit dan tanya jawab.

---

# Bab 16. Tren 2026 sampai 2030 dan Cara Menjaga Pengetahuan Tetap Mutakhir

## Tujuan Pembelajaran

- Mengetahui isu regulasi yang berkembang.
- Memiliki metode memverifikasi status sebuah peraturan.
- Menyusun rutinitas pemantauan regulasi.

## 16.1 Isu Regulasi yang Perlu Dipantau

|Isu|Status yang diketahui (informasi hingga 2026)|Mengapa penting|
|---|---|---|
|Lembaga Pelindungan Data Pribadi dan RPP PDP|Belum terbentuk penuh dan RPP masih dalam proses penetapan menurut pemberitaan Februari 2026. Fungsi pengawasan sementara di Komdigi|Menentukan penegakan UU PDP dan detail kewajiban|
|Peraturan Presiden AI (Peta Jalan dan Etika AI)|Dilaporkan menunggu tanda tangan Presiden pada September 2026; pendekatan berbasis risiko|Kerangka tata kelola AI nasional|
|RUU Keamanan dan Ketahanan Siber|Dibahas pemerintah dan Komisi I DPR sejak 29 Juni 2026|Kewajiban keamanan, tata laksana insiden, penyidikan siber|
|PP TUNAS dan aturan pelaksananya|Berlaku sejak ditetapkan 28 Maret 2025 dengan masa penyesuaian; aturan pelaksana sedang disusun|Kewajiban verifikasi usia dan fitur anak|
|KUHP dan KUHAP baru|Berlaku sejak 2 Januari 2026|Penyelarasan pidana siber dan acara pembuktian|
|UU ITE|UU 1/2024 dan putusan MK terkait|Tafsir pasal pidana dan transaksi elektronik|
|Perubahan peraturan telekomunikasi dan penyiaran|Perlu dipantau pada Prolegnas dan pembahasan DPR|Penyelenggaraan jaringan dan konten|
|Aset kripto dan keuangan digital|Pengawasan di OJK; aturan terus berkembang|Fintech dan Web3|

Catatan: baris pada tabel ini berasal dari informasi yang tersedia ketika buku ini disusun. Anggap sebagai titik awal pemeriksaan, bukan fakta final.

## 16.2 Cara Memverifikasi Status Sebuah Peraturan

1. **Cari di basis data resmi** (Lampiran E): peraturan.go.id, JDIH Kementerian Sekretariat Negara, JDIH Komdigi, JDIH BSSN, situs OJK dan BI.
2. **Periksa status:** berlaku, diubah, dicabut. Basis data resmi biasanya menampilkan peraturan yang mengubah atau mencabut.
3. **Baca versi terbaru.** Jika sebuah UU telah diubah, baca versi yang menggabungkan perubahan (jika ada) dan teks perubahan.
4. **Periksa putusan Mahkamah Konstitusi** (situs MK) untuk pasal yang sudah diuji.
5. **Periksa aturan pelaksana.** Banyak undang-undang tidak lengkap tanpa PP atau peraturan menteri.
6. **Bedakan rancangan dan peraturan.** RUU, RPP, dan rancangan Perpres belum mengikat.
7. **Gunakan sumber berita hukum** sebagai penunjuk, lalu rujuk teks resmi.

## 16.3 Rutinitas Pemantauan Regulasi (Contoh)

|Frekuensi|Aktivitas|
|---|---|
|Mingguan|Baca ringkasan berita regulasi TI dari sumber tepercaya|
|Bulanan|Periksa JDIH untuk peraturan baru pada bidang yang relevan|
|Per kuartal|Perbarui register regulasi organisasi|
|Per tahun|Tinjau seluruh kebijakan dan lakukan audit kepatuhan|

## 16.4 Keterampilan Masa Depan

Lulusan Teknik Informatika yang kuat di bidang hukum dan kebijakan akan semakin dicari pada peran: pejabat pelindungan data, analis kepatuhan, auditor TI, tata kelola AI, manajer produk yang memahami regulasi, dan peneliti kebijakan digital. Kemampuan menerjemahkan persyaratan hukum menjadi persyaratan teknis (_requirements engineering_ untuk kepatuhan) adalah keunggulan.

## Ringkasan Bab 16

- Beberapa regulasi utama di bidang TI masih berubah: pengawasan PDP, Perpres AI, RUU KKS, PP TUNAS.
- Verifikasi selalu lewat sumber resmi, dan periksa status berlaku, diubah, atau dicabut.
- Bangun rutinitas pemantauan, bukan menghafal pasal.

## Latihan Bab 16

1. Pilih satu peraturan dari Lampiran A dan telusuri status terbarunya (berlaku, diubah, dicabut) di basis data resmi. Catat langkah yang Anda lakukan.
2. Buat kalender pemantauan regulasi untuk satu tahun bagi perusahaan fiktif.
3. Berikan satu contoh kebutuhan hukum yang dapat diterjemahkan menjadi persyaratan teknis (misalnya "hak penghapusan data" menjadi fitur apa).

---

# Lampiran A. Peta Peraturan Ringkas

Tabel berikut ringkasan. Pastikan memeriksa status mutakhir pada sumber resmi.

|Peraturan|Fokus|Relevansi bagi TI|
|---|---|---|
|UUD 1945 (khususnya pasal tentang hak berkomunikasi, memperoleh informasi, dan pelindungan pribadi)|Hak asasi|Dasar kebebasan berekspresi dan privasi|
|UU 11/2008 jo. UU 19/2016 jo. UU 1/2024 (UU ITE)|Informasi, transaksi elektronik, perbuatan terlarang|Payung utama hukum siber|
|UU 27/2022 (UU PDP)|Pelindungan data pribadi|Hak subjek data, kewajiban pengendali|
|UU 1/2023 (KUHP) dan UU 20/2025 (KUHAP)|Hukum pidana dan acara pidana|Berlaku sejak 2 Januari 2026|
|UU 1/2026|Peraturan yang dirujuk pemberitaan hukum sebagai penyelaras ketentuan KUHP|Periksa isi dan relevansinya|
|UU 36/1999 (Telekomunikasi)|Penyelenggaraan telekomunikasi|Jaringan dan layanan telekomunikasi|
|UU 28/2014 (Hak Cipta)|Hak cipta|Program komputer, konten digital|
|UU 13/2016 (Paten), UU 20/2016 (Merek), UU 30/2000 (Rahasia Dagang), UU 31/2000 (Desain Industri), UU 32/2000 (DTLST)|Kekayaan intelektual lain|Perlindungan produk dan rahasia dagang|
|UU 8/1999 (Perlindungan Konsumen)|Hak konsumen|Transaksi daring, klausul baku|
|UU 14/2008 (Keterbukaan Informasi Publik)|Informasi publik|Aplikasi pemerintah|
|UU 44/2008 (Pornografi)|Konten pornografi|Konten digital|
|UU 12/2022 (TPKS)|Kekerasan seksual termasuk berbasis elektronik|Konten intim tanpa persetujuan|
|UU Perlindungan Anak|Hak anak|Konten dan layanan untuk anak|
|UU 4/2023 (P2SK)|Pengembangan dan penguatan sektor keuangan|Fintech, aset keuangan digital|
|UU 8/2010 (TPPU)|Pencucian uang|Transaksi digital, aset kripto|
|UU 17/2023 (Kesehatan)|Kesehatan|Data kesehatan, rekam medis elektronik|
|PP 71/2019|Penyelenggaraan sistem dan transaksi elektronik|Kewajiban PSE|
|PP 80/2019|Perdagangan melalui sistem elektronik|E-commerce|
|PP 17/2025 (PP TUNAS)|Pelindungan anak pada sistem elektronik|Verifikasi usia, fitur anak|
|Perpres 82/2022|Pelindungan infrastruktur informasi vital|Pengelola IIV|
|Perpres 47/2023|Strategi keamanan siber nasional dan manajemen krisis siber|Keamanan siber|
|Perpres 95/2018 dan Perpres Arsitektur SPBE Nasional|Pemerintahan berbasis elektronik|Aplikasi pemerintah|
|Permenkominfo 5/2020 jo. 10/2021|PSE Lingkup Privat|Pendaftaran, moderasi konten|
|Permendag 31/2023|Perizinan, periklanan, pembinaan, pengawasan PMSE|E-commerce dan social commerce|
|Surat Edaran Menkominfo 9/2023|Etika kecerdasan artifisial|Pedoman AI|
|Peraturan OJK dan Bank Indonesia|Keuangan digital, pinjaman daring, aset kripto, pembayaran|Fintech|
|RPP PDP|Aturan pelaksana UU PDP|Dalam proses menurut informasi yang tersedia|
|Perpres AI (Peta Jalan dan Etika)|Tata kelola AI|Dilaporkan menunggu penandatanganan (September 2026)|
|RUU Keamanan dan Ketahanan Siber|Keamanan siber nasional|Dibahas di DPR sejak Juni 2026|

---

# Lampiran B. Glosarium

|Istilah|Arti|
|---|---|
|Agen elektronik|Perangkat sistem elektronik yang melakukan tindakan otomatis terhadap informasi elektronik|
|Akses ilegal|Masuk ke sistem elektronik tanpa hak|
|Alat bukti elektronik|Informasi atau dokumen elektronik dan hasil cetaknya yang diakui sebagai bukti|
|Asas|Prinsip dasar hukum|
|BSSN|Badan Siber dan Sandi Negara|
|_Chain of custody_|Catatan rantai penguasaan bukti|
|CSIRT|Tim tanggap insiden keamanan siber|
|Data pribadi spesifik|Data pribadi yang berisiko tinggi, misalnya kesehatan, biometrik, genetika|
|Delik aduan|Tindak pidana yang diproses hanya atas pengaduan korban|
|DPIA|Penilaian dampak pelindungan data pribadi|
|DPO|Pejabat atau petugas pelindungan data pribadi|
|Dokumen elektronik|Informasi elektronik yang dapat dilihat, ditampilkan, atau didengar|
|Hash|Nilai ringkas hasil fungsi satu arah untuk memverifikasi keutuhan data|
|IIV|Infrastruktur informasi vital|
|Klausul baku|Aturan sepihak yang disiapkan pelaku usaha dan dituangkan dalam dokumen|
|Komdigi|Kementerian Komunikasi dan Digital|
|Lex specialis|Aturan khusus mengalahkan aturan umum|
|Lisensi|Izin menggunakan karya dengan syarat tertentu|
|Pengendali data|Pihak yang menentukan tujuan dan cara pemrosesan data pribadi|
|PMSE|Perdagangan melalui sistem elektronik|
|Prosesor data|Pihak yang memproses data atas nama pengendali|
|PSE|Penyelenggara sistem elektronik|
|PSrE|Penyelenggara sertifikasi elektronik|
|Pseudonimisasi|Mengganti pengenal langsung dengan pengenal buatan|
|SBOM|Daftar komponen perangkat lunak|
|SMKI|Sistem manajemen keamanan informasi|
|SPBE|Sistem pemerintahan berbasis elektronik|
|Subjek data|Orang yang datanya diproses|
|Tanda tangan elektronik|Tanda berupa informasi elektronik yang melekat pada dokumen untuk autentikasi|
|Yurisdiksi|Kewenangan negara menerapkan hukum dan mengadili|

---

# Lampiran C. Kuis Pilihan Ganda dan Kunci Jawaban

Pilih jawaban yang paling tepat.

1. Peraturan yang lebih tinggi mengalahkan peraturan lebih rendah. Asas ini disebut: a. Lex specialis b. Lex superior c. Lex posterior d. Lex mercatoria
2. Informasi elektronik dan dokumen elektronik menurut UU ITE merupakan: a. Bukan alat bukti b. Alat bukti yang sah, dengan pengecualian tertentu c. Alat bukti hanya untuk perkara perdata d. Alat bukti hanya jika dicetak dan dilegalisasi
3. UU Perubahan Kedua UU ITE adalah: a. UU 19/2016 b. UU 11/2008 c. UU 1/2024 d. UU 27/2022
4. KUHP baru Indonesia mulai berlaku pada: a. 2 Januari 2023 b. 2 Januari 2025 c. 2 Januari 2026 d. 1 Januari 2027
5. Batas waktu umum pemberitahuan kegagalan pelindungan data pribadi menurut UU PDP: a. 24 jam b. 3 x 24 jam c. 14 hari d. 30 hari
6. Pihak yang menentukan tujuan dan cara pemrosesan data pribadi disebut: a. Prosesor data b. Subjek data c. Pengendali data d. Penyidik
7. Contoh data pribadi spesifik: a. Nama panggilan b. Data biometrik c. Nama aplikasi favorit d. Merek ponsel
8. Pengujian penetrasi yang sah wajib memiliki: a. Izin tertulis dan ruang lingkup jelas b. Hanya niat baik c. Hanya persetujuan lisan teman d. Hanya pemberitahuan ke media
9. Program komputer menurut UU Hak Cipta dilindungi selama: a. 10 tahun b. 25 tahun c. 50 tahun sejak pertama kali diumumkan d. Selamanya
10. Kode di repositori publik tanpa lisensi: a. Domain publik b. Bebas dipakai komersial c. Pada dasarnya hak cipta tetap pada penulis, tidak bebas dipakai d. Otomatis berlisensi MIT
11. Lisensi yang mewajibkan pembukaan kode turunan yang didistribusikan adalah: a. MIT b. BSD c. Apache 2.0 d. GPL
12. PP TUNAS mengatur: a. Pajak digital b. Pelindungan anak pada penyelenggaraan sistem elektronik c. Hak cipta lagu d. Perizinan penyiaran
13. Pencemaran nama baik adalah delik: a. Biasa b. Aduan c. Perdata murni d. Administratif
14. Peraturan yang melindungi infrastruktur informasi vital adalah: a. Perpres 82 Tahun 2022 b. PP 80 Tahun 2019 c. UU 8 Tahun 1999 d. UU 28 Tahun 2014
15. Alasan analisis forensik dilakukan pada salinan: a. Agar lebih cepat b. Agar bukti asli tidak berubah c. Agar tidak perlu hash d. Agar tidak perlu dokumentasi
16. AI menurut hukum Indonesia saat ini: a. Subjek hukum b. Bukan subjek hukum; tanggung jawab pada manusia atau badan hukum c. Dapat dipidana d. Dapat memiliki hak cipta
17. Pendekatan berbasis risiko pada regulasi AI artinya: a. Semua AI diperlakukan sama b. Kewajiban sebanding dengan tingkat risiko penggunaan c. AI dilarang d. Tidak ada kewajiban
18. Dokumen kebijakan yang berisi langkah rinci siapa melakukan apa disebut: a. Kebijakan b. Standar c. Prosedur d. Visi
19. Dasar pemrosesan data pribadi yang sah, kecuali: a. Persetujuan b. Kewajiban hukum c. Kepentingan vital subjek data d. Keinginan pengendali tanpa dasar apa pun
20. Cara terbaik memverifikasi status berlakunya sebuah peraturan: a. Mengandalkan media sosial b. Memeriksa basis data hukum resmi dan putusan MK c. Bertanya teman d. Mengandalkan ingatan

**Kunci jawaban:**

|No|Jawaban|No|Jawaban|No|Jawaban|No|Jawaban|
|---|---|---|---|---|---|---|---|
|1|b|6|c|11|d|16|b|
|2|b|7|b|12|b|17|b|
|3|c|8|a|13|b|18|c|
|4|c|9|c|14|a|19|d|
|5|b|10|c|15|b|20|b|

---

# Lampiran D. Templat Praktis

## D.1 Kerangka Kebijakan Privasi

1. Siapa kami dan cara menghubungi kami (termasuk kontak DPO).
2. Data apa yang kami kumpulkan.
3. Untuk tujuan apa data digunakan, dan dasar pemrosesannya.
4. Dengan siapa data dibagikan (prosesor, mitra, otoritas).
5. Transfer data ke luar negeri (jika ada).
6. Berapa lama data disimpan.
7. Hak Anda dan cara menggunakannya.
8. Cara menarik persetujuan.
9. Keamanan data.
10. Data anak.
11. Perubahan kebijakan dan cara pemberitahuan.
12. Cara mengajukan keluhan.

## D.2 Daftar Periksa Kepatuhan Proyek Perangkat Lunak

- [ ] Peta data dan klasifikasi data dibuat.
- [ ] Dasar pemrosesan ditentukan untuk setiap tujuan.
- [ ] Persetujuan spesifik, dapat ditarik, dan dicatat.
- [ ] Enkripsi saat transit dan saat disimpan.
- [ ] Kontrol akses berbasis peran dan MFA untuk administrator.
- [ ] Log audit yang tidak dapat diubah.
- [ ] Kebijakan retensi dan penghapusan otomatis.
- [ ] Rencana respons insiden dengan jalur notifikasi 3 x 24 jam.
- [ ] SBOM dan pemeriksaan lisensi dalam CI/CD.
- [ ] Alur pelaporan konten dan moderasi (jika ada konten pengguna).
- [ ] Pendaftaran PSE (jika berlaku).
- [ ] Izin sektor (keuangan, kesehatan) bila berlaku.
- [ ] Pengaturan khusus anak dan verifikasi usia (jika melayani anak).
- [ ] Penilaian risiko AI (jika memakai AI).
- [ ] Uji penetrasi berkala dengan izin tertulis.

## D.3 Daftar Isi Surat Izin Pengujian Penetrasi

1. Para pihak dan kontak darurat.
2. Tujuan pengujian.
3. Ruang lingkup (aset yang boleh diuji) dan di luar lingkup.
4. Teknik yang diizinkan dan dilarang.
5. Jadwal dan jam pengujian.
6. Perlindungan data: larangan mengambil data pribadi selain bukti minimal.
7. Kerahasiaan temuan.
8. Pelaporan: format, tenggat, penerima.
9. Batas tanggung jawab dan asuransi.
10. Tanda tangan para pihak yang berwenang.

## D.4 Garis Waktu Respons Insiden Kebocoran Data (Contoh)

|Waktu|Tindakan|
|---|---|
|Jam 0|Deteksi, buka catatan insiden, kumpulkan tim|
|Jam 0 sampai 4|Penahanan (isolasi, cabut kredensial), pelestarian bukti (snapshot, hash)|
|Jam 4 sampai 24|Penilaian dampak: data apa, berapa banyak, siapa terdampak|
|Jam 24 sampai 48|Konsultasi hukum, koordinasi dengan CSIRT atau regulator sektor, draf pemberitahuan|
|Sebelum jam 72|Kirim pemberitahuan tertulis kepada subjek data dan lembaga yang berwenang|
|Setelah itu|Pemulihan, pemantauan, evaluasi akar masalah, perbaikan kontrol|

---

# Lampiran E. Sumber Resmi dan Sumber Pemutakhiran

## Sumber Hukum Resmi

- Basis data peraturan nasional: peraturan.go.id
- JDIH Kementerian Sekretariat Negara: jdih.setneg.go.id
- JDIH Kementerian Komunikasi dan Digital: jdih.komdigi.go.id
- Situs Mahkamah Konstitusi untuk putusan pengujian undang-undang: mkri.id
- Portal informasi pelindungan data pribadi: pdp.id
- Situs BSSN: bssn.go.id
- Situs OJK dan Bank Indonesia untuk peraturan sektor keuangan
- Situs DJKI untuk kekayaan intelektual

## Sumber Berita Hukum dan Kebijakan (sebagai penunjuk, lalu rujuk teks resmi)

Hukumonline, Bisnis.com, Kontan, CNBC Indonesia, Antara, dan media sejenis.

## Rujukan Internasional

- Teks GDPR dan EU AI Act pada portal hukum Uni Eropa
- NIST (Cybersecurity Framework dan AI Risk Management Framework)
- ISO/IEC 27001, 27701, 27037, 42001
- ASEAN Guide on AI Governance and Ethics

## Informasi Status yang Digunakan dalam Penyusunan Edisi Ini

Beberapa status regulasi dalam buku ini diperiksa melalui pemberitaan dan publikasi berikut (diakses sampai Oktober 2026):

- Hukumonline: ulasan UU 1/2024 dan perubahan pasal pencemaran nama baik.
- Antara dan Selular.id: penandatanganan UU 1/2024 pada 2 Januari 2024.
- CNBC Indonesia (4 Februari 2026): perkembangan RPP PDP dan lembaga pengawas PDP.
- detikInet (2 Oktober 2025): status Lembaga PDP.
- Bisnis.com dan Kontan (September dan Juli 2026): perkembangan dua Perpres AI.
- Bisnis.com dan Kementerian PANRB (akhir Juni 2026): pembahasan RUU Keamanan dan Ketahanan Siber di DPR.
- Antara dan Metro TV (Januari 2026): KUHP dan KUHAP baru berlaku 2 Januari 2026.
- Bisnis.com dan Investortrust (2025 sampai 2026): PP 17/2025 (PP TUNAS).
- Publikasi DPR (Info Singkat, Mei 2025) mengenai dampak Putusan MK 105/PUU-XXII/2024 pada delik pencemaran nama baik.

---

_Akhir buku. Edisi berikutnya sebaiknya dimutakhirkan saat Perpres AI, RPP PDP, RUU KKS, atau aturan pelaksana PP TUNAS ditetapkan._