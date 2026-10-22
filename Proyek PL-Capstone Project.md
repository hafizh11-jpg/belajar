# Buku Ajar Proyek Perangkat Lunak dan Capstone Project

**Program Studi Teknik Informatika - Edisi Tahun Akademik 2026/2027 dan Seterusnya**

Panduan lengkap untuk pemula: dari memilih topik, membentuk tim, merancang, membangun, menguji, mengamankan, sampai mempresentasikan sebuah proyek perangkat lunak.

---

## Daftar Isi

- Kata Pengantar dan Cara Memakai Buku Ini
- Bab 1. Memahami Capstone Project
- Bab 2. Membentuk dan Mengelola Tim
- Bab 3. Menentukan Topik dan Merumuskan Masalah
- Bab 4. Manajemen Proyek
- Bab 5. Rekayasa Kebutuhan
- Bab 6. Perancangan Sistem
- Bab 7. Memilih Teknologi (Tech Stack)
- Bab 8. Implementasi dan Kolaborasi Kode
- Bab 9. Memakai AI secara Bertanggung Jawab
- Bab 10. Basis Data dan API
- Bab 11. Pengujian Perangkat Lunak
- Bab 12. Keamanan dan Privasi
- Bab 13. CI/CD, Container, dan Deployment
- Bab 14. Dokumentasi
- Bab 15. Laporan, Presentasi, dan Demo
- Bab 16. Penilaian dan Rubrik
- Bab 17. Kesalahan Umum dan Cara Menghindarinya
- Bab 18. Studi Kasus Lengkap: SIPINJAM-LAB
- Lampiran A. Template Proposal
- Lampiran B. Template Spesifikasi Kebutuhan (SRS) Ringkas
- Lampiran C. Template Laporan Mingguan
- Lampiran D. Checklist Akhir Sebelum Sidang
- Lampiran E. Glosarium
- Lampiran F. Daftar Bacaan Lanjutan

---

## Kata Pengantar dan Cara Memakai Buku Ini

Capstone Project adalah proyek besar yang biasanya dikerjakan di semester akhir. Di sini Anda tidak lagi sekadar mengerjakan soal latihan per mata kuliah. Anda diminta menyelesaikan satu masalah nyata dari awal sampai akhir: memahami masalah, merancang solusi, membangun, menguji, lalu menyerahkannya kepada pengguna.

Buku ini ditulis dengan asumsi bahwa Anda adalah pemula. Anda sudah pernah belajar pemrograman dasar dan mungkin basis data, tetapi belum pernah mengelola proyek yang utuh. Setiap istilah teknis dijelaskan saat pertama kali muncul. Jika ada istilah yang terlewat, lihat Lampiran E (Glosarium).

### Cara membaca

1. Baca Bab 1 sampai 4 sebelum tim Anda mulai menulis kode. Bab-bab ini menentukan arah proyek.
2. Gunakan Bab 5 sampai 13 sebagai referensi kerja. Anda tidak harus membacanya berurutan, tetapi sebaiknya tidak melewati Bab 5 (kebutuhan) dan Bab 11 (pengujian).
3. Bab 18 adalah contoh proyek utuh. Bacalah sambil membuka bab terkait, supaya Anda melihat teori dipakai dalam praktik.
4. Lampiran berisi template yang bisa langsung disalin.

### Catatan tentang perubahan teknologi

Dunia perangkat lunak berubah cepat. Nama alat, versi, dan fitur yang disebut di buku ini adalah contoh yang umum dipakai pada periode 2026/2027. Prinsip yang diajarkan (misalnya memecah pekerjaan, menguji sebelum rilis, tidak menyimpan kata sandi dalam teks biasa) jauh lebih awet daripada nama alatnya. Jika sebuah alat sudah berubah atau digantikan, cari padanannya dan terapkan prinsip yang sama. Selalu periksa dokumentasi resmi alat tersebut untuk versi terbaru, dan cocokkan juga dengan pedoman resmi program studi Anda karena aturan tiap kampus berbeda.

---

# Bab 1. Memahami Capstone Project

## 1.1 Apa itu Capstone Project

Kata "capstone" berasal dari batu penutup di puncak sebuah bangunan. Dalam pendidikan, capstone project adalah proyek penutup yang menggabungkan semua ilmu yang telah dipelajari. Pada Teknik Informatika, hasilnya biasanya berupa produk perangkat lunak yang berjalan, ditambah dokumentasi dan laporan.

Nama mata kuliahnya bisa berbeda di tiap kampus: Proyek Perangkat Lunak, Proyek Akhir, Tugas Akhir Berbasis Proyek, Capstone Design, atau Studi Independen. Isinya mirip: Anda bekerja seperti pada pekerjaan profesional.

## 1.2 Tujuan pembelajaran

Setelah menyelesaikan capstone, Anda diharapkan mampu:

1. Mengidentifikasi masalah nyata dan memetakan pihak yang berkepentingan (stakeholder).
2. Menurunkan masalah menjadi kebutuhan yang jelas dan dapat diuji.
3. Merancang arsitektur dan antarmuka sistem.
4. Mengimplementasikan sistem secara berkelompok memakai kontrol versi.
5. Menguji sistem pada beberapa tingkat.
6. Menerapkan praktik keamanan dasar dan menghormati privasi data.
7. Menyampaikan hasil secara tertulis dan lisan.
8. Bekerja dalam tim: berbagi tugas, berkomunikasi, dan menyelesaikan konflik.

## 1.3 Perbedaan dengan tugas besar biasa dan skripsi

|Aspek|Tugas besar mata kuliah|Capstone Project|Skripsi (riset)|
|---|---|---|---|
|Cakupan|Satu topik mata kuliah|Banyak topik terintegrasi|Satu pertanyaan penelitian|
|Pengguna|Dosen/penilai|Pengguna atau mitra nyata (idealnya)|Komunitas ilmiah|
|Luaran utama|Program kecil, laporan|Produk berjalan, dokumentasi, laporan|Naskah ilmiah, temuan|
|Cara kerja|Sering individu|Umumnya tim|Umumnya individu|
|Fokus penilaian|Kebenaran materi|Proses dan hasil rekayasa|Kebaruan dan metodologi|

Bukan berarti capstone tidak boleh memuat unsur riset. Banyak proyek capstone yang membandingkan algoritma atau model sebelum memilih salah satunya. Namun inti penilaiannya adalah kemampuan rekayasa.

## 1.4 Siklus hidup proyek secara garis besar

```
Inisiasi -> Perencanaan -> Analisis Kebutuhan -> Perancangan
   -> Implementasi -> Pengujian -> Deployment -> Serah Terima -> Evaluasi
```

Pada proyek modern, tahap-tahap ini tidak dikerjakan sekali lurus (model air terjun atau waterfall), melainkan berulang dalam siklus pendek (iteratif). Ini dibahas di Bab 4.

## 1.5 Tren yang memengaruhi capstone pada 2026/2027 dan seterusnya

Beberapa hal yang kini hampir menjadi standar dan sebaiknya Anda pertimbangkan:

1. **Pengembangan dengan bantuan AI.** Asisten pemrograman berbasis AI sudah umum. Bab 9 membahas cara memakainya secara jujur dan aman. Kampus Anda mungkin memiliki aturan khusus; patuhi aturan itu.
2. **Cloud dan container.** Aplikasi biasanya dijalankan di server cloud atau dibungkus dalam container (misalnya Docker) agar mudah dipindahkan. Lihat Bab 13.
3. **Keamanan sejak awal (DevSecOps).** Keamanan dipikirkan sejak perancangan, bukan ditambal di akhir. Lihat Bab 12.
4. **Pelindungan data pribadi.** Di Indonesia, Undang-Undang Pelindungan Data Pribadi (UU Nomor 27 Tahun 2022) mengatur pemrosesan data pribadi. Jika sistem Anda menyimpan data orang, Anda harus memikirkan ini.
5. **Otomasi pengujian dan rilis (CI/CD).** Kode diuji dan dirilis lewat alur otomatis.
6. **Aksesibilitas dan pengalaman pengguna.** Produk harus bisa dipakai oleh beragam pengguna, termasuk di perangkat seluler dengan koneksi lambat.
7. **Keberlanjutan dan efisiensi.** Sistem yang hemat sumber daya (komputasi, energi, biaya cloud) makin dihargai.

## 1.6 Luaran yang biasanya diminta

1. Proposal proyek.
2. Dokumen kebutuhan (SRS) dan dokumen desain.
3. Kode sumber di repositori (misalnya Git) dengan riwayat commit yang rapi.
4. Aplikasi yang dapat dijalankan (demo atau deployment).
5. Rencana dan hasil pengujian.
6. Panduan pengguna dan panduan instalasi.
7. Laporan akhir.
8. Presentasi, demo, dan kadang poster atau video singkat.

Cocokkan daftar ini dengan pedoman resmi prodi Anda.

## 1.7 Latihan Bab 1

1. Tuliskan dengan kalimat sendiri perbedaan capstone dengan tugas besar mata kuliah.
2. Dari daftar tren di 1.5, pilih tiga yang paling relevan dengan minat Anda, lalu jelaskan alasannya.
3. Cari pedoman capstone di prodi Anda. Catat jumlah anggota tim, durasi, dan luaran wajib.

---

# Bab 2. Membentuk dan Mengelola Tim

## 2.1 Mengapa tim sering menjadi sumber masalah terbesar

Proyek capstone jarang gagal karena kode yang terlalu sulit. Lebih sering gagal karena komunikasi buruk, pembagian kerja tidak jelas, atau satu orang menanggung semuanya. Karena itu, hal pertama yang perlu dirancang adalah cara bekerja sama.

## 2.2 Peran dalam tim

Satu orang boleh memegang lebih dari satu peran, tetapi setiap peran harus ada pemiliknya.

|Peran|Tanggung jawab utama|
|---|---|
|Ketua tim / Project Manager|Menjaga jadwal, memimpin rapat, menjadi penghubung dengan dosen dan mitra|
|Analis kebutuhan|Menggali kebutuhan pengguna, menulis user story dan SRS|
|Perancang UI/UX|Membuat wireframe dan prototipe, memastikan kemudahan penggunaan|
|Pengembang front-end|Membangun antarmuka yang dilihat pengguna|
|Pengembang back-end|Membangun logika sistem, API, dan basis data|
|Penjamin mutu (QA) / Penguji|Menyusun dan menjalankan pengujian|
|DevOps / Rilis|Mengatur repositori, CI/CD, dan deployment|
|Penulis dokumentasi|Menjaga kualitas dokumen dan laporan|

Pada tim kecil (3 sampai 4 orang), misalnya, ketua tim bisa merangkap analis, dan semua anggota ikut menguji. Yang penting jelas siapa yang bertanggung jawab akhir atas setiap bidang.

## 2.3 Tahap perkembangan tim

Model Tuckman menjelaskan bahwa tim biasanya melewati empat tahap:

1. **Forming**: anggota baru saling mengenal, masih sopan dan hati-hati.
2. **Storming**: mulai muncul perbedaan pendapat dan gesekan. Ini normal.
3. **Norming**: tim menyepakati aturan main dan mulai bekerja selaras.
4. **Performing**: tim bekerja efektif.

Jangan panik saat storming. Cara terbaik melewatinya adalah dengan aturan kerja yang tertulis (lihat bagian berikut).

## 2.4 Kesepakatan kerja tim (Working Agreement)

Buat dokumen satu halaman berisi hal berikut, lalu disetujui semua anggota:

1. Jadwal rapat rutin (misalnya dua kali seminggu) dan durasinya.
2. Kanal komunikasi utama (misalnya grup pesan dan papan tugas) serta batas waktu membalas pesan.
3. Cara mengambil keputusan (konsensus, voting, atau ketua memutuskan jika buntu).
4. Standar pekerjaan selesai (Definition of Done, lihat Bab 4).
5. Aturan jika ada anggota tidak dapat hadir atau terlambat menyelesaikan tugas.
6. Cara menyelesaikan konflik dan kapan melibatkan dosen pembimbing.

## 2.5 Rapat yang efektif

Rapat yang baik singkat dan menghasilkan keputusan. Pola sederhana yang bisa dipakai:

1. Tiap anggota menjawab tiga pertanyaan: apa yang sudah saya selesaikan, apa yang akan saya kerjakan, apa hambatan saya.
2. Bahas hambatan yang membutuhkan keputusan tim.
3. Catat butir keputusan dan penanggung jawab beserta tenggat.
4. Kirim notulen singkat ke seluruh anggota.

## 2.6 Mengatasi anggota yang tidak berkontribusi

1. Pastikan dulu pembagian tugas jelas dan terukur. Kadang masalahnya adalah tugas yang kabur.
2. Bicarakan secara langsung dan sopan, dengan data (misalnya riwayat commit atau papan tugas), bukan tuduhan.
3. Tawarkan bantuan atau pasangan kerja (pair programming).
4. Jika tidak membaik, libatkan dosen pembimbing lebih awal. Jangan menunggu menjelang sidang.

## 2.7 Latihan Bab 2

1. Susun working agreement untuk tim Anda dan minta semua anggota menandatangani (atau menyetujui lewat pesan).
2. Pembagian peran tim Anda: siapa memegang apa? Adakah peran yang belum ada pemiliknya?

---

# Bab 3. Menentukan Topik dan Merumuskan Masalah

## 3.1 Sumber ide topik

1. **Masalah di sekitar Anda**: proses manual di kampus, organisasi mahasiswa, UMKM, desa, atau tempat kerja kerabat.
2. **Permintaan mitra**: perusahaan, instansi, atau dosen yang membutuhkan sistem tertentu.
3. **Peluang teknologi**: misalnya memanfaatkan data terbuka, sensor IoT, atau model AI untuk masalah yang jelas.
4. **Perbaikan sistem yang ada**: sistem lama yang lambat, sulit dipakai, atau tidak aman.

Tips penting: mulailah dari masalah, bukan dari teknologi. Kalimat "Saya ingin membuat aplikasi dengan AI" bukan masalah. Kalimat "Petugas lab membutuhkan 30 menit setiap hari untuk mencatat peminjaman alat secara manual dan sering terjadi kehilangan data" adalah masalah.

## 3.2 Kriteria topik yang baik

Gunakan checklist ini untuk menyaring ide:

|Kriteria|Pertanyaan penentu|
|---|---|
|Relevan|Apakah menyelesaikan masalah nyata? Siapa penggunanya?|
|Layak (feasible)|Apakah bisa selesai dalam durasi dan sumber daya yang ada?|
|Cakupan tepat|Tidak terlalu kecil (hanya CRUD sederhana) dan tidak terlalu besar (mustahil selesai)|
|Mengandung tantangan teknis|Ada hal yang menguji kompetensi Teknik Informatika|
|Dapat diukur|Keberhasilannya bisa dibuktikan dengan angka atau uji|
|Data dan akses tersedia|Anda dapat memperoleh data dan akses ke pengguna|
|Etis dan legal|Tidak melanggar privasi, hak cipta, atau aturan|

## 3.3 Merumuskan pernyataan masalah (Problem Statement)

Rumus sederhana:

> Saat ini **[pengguna]** mengalami **[masalah]** ketika **[situasi]**, yang menyebabkan **[dampak]**. Proyek ini bertujuan **[tujuan]** dengan cara **[pendekatan umum]**.

Contoh:

> Saat ini petugas laboratorium mengalami kesulitan melacak status alat ketika mahasiswa meminjam secara manual di buku, yang menyebabkan alat hilang tanpa jejak dan antrean panjang. Proyek ini bertujuan menyediakan sistem peminjaman berbasis web yang mencatat peminjaman dan pengembalian secara otomatis.

## 3.4 Tujuan yang SMART

SMART berarti Specific (spesifik), Measurable (terukur), Achievable (dapat dicapai), Relevant (relevan), Time-bound (berbatas waktu).

Contoh tujuan yang buruk: "Membuat sistem yang bagus."

Contoh tujuan SMART: "Dalam 14 minggu, membangun sistem peminjaman alat yang memungkinkan mahasiswa memesan alat dalam kurang dari 2 menit dan mengurangi pencatatan manual petugas hingga 80 persen, dibuktikan lewat uji coba dengan 20 pengguna."

## 3.5 Identifikasi stakeholder

Stakeholder adalah semua pihak yang memengaruhi atau dipengaruhi proyek. Petakan dengan tabel sederhana:

|Stakeholder|Kepentingan|Pengaruh|Cara melibatkan|
|---|---|---|---|
|Mahasiswa peminjam|Mudah meminjam|Sedang|Survei, uji coba|
|Petugas lab|Mengurangi kerja manual|Tinggi|Wawancara, demo tiap sprint|
|Kepala lab|Laporan dan akuntabilitas|Tinggi|Presentasi hasil|
|Dosen pembimbing|Kualitas akademik|Tinggi|Konsultasi berkala|

## 3.6 Memahami kondisi saat ini (As-Is) dan kondisi yang diharapkan (To-Be)

Gambarkan proses sebelum dan sesudah sistem Anda ada. Contoh sederhana memakai diagram teks:

```
AS-IS:  Mahasiswa datang -> Isi buku -> Petugas cek stok manual -> Serahkan alat -> Catat balik

TO-BE:  Mahasiswa buka aplikasi -> Pilih alat & jadwal -> Petugas setujui -> Alat diambil
        -> Sistem mencatat otomatis -> Notifikasi tenggat pengembalian
```

## 3.7 Studi pustaka dan sistem sejenis

Sebelum membangun, periksa apakah sudah ada solusi serupa:

1. Cari aplikasi atau penelitian sejenis. Apa kelebihan dan kekurangannya?
2. Buat tabel perbandingan fitur.
3. Tentukan nilai tambah proyek Anda. Bukan harus unik di dunia; cukup jelas relevan dan berbeda untuk konteks Anda.

## 3.8 Menentukan batasan proyek (Scope)

Tuliskan eksplisit:

- **In scope**: apa yang akan dikerjakan.
- **Out of scope**: apa yang sengaja tidak dikerjakan.
- **Asumsi**: hal yang dianggap benar (misalnya pengguna memiliki akses internet).
- **Kendala**: batas waktu, anggaran, perangkat keras, aturan.

Menulis out of scope itu penting. Tanpa itu, proyek rawan scope creep, yaitu permintaan tambahan yang terus bertambah hingga tidak selesai.

## 3.9 Menilai kelayakan (Feasibility)

1. **Teknis**: apakah teknologinya dikuasai atau bisa dipelajari tepat waktu?
2. **Operasional**: apakah pengguna mau dan mampu memakainya?
3. **Ekonomi**: apakah biaya (misalnya cloud) terjangkau?
4. **Jadwal**: apakah cukup waktu?
5. **Hukum dan etika**: apakah ada data pribadi, lisensi, atau izin yang perlu diurus?

## 3.10 Latihan Bab 3

1. Tuliskan tiga ide topik, lalu nilai masing-masing dengan tabel kriteria 3.2 (skor 1 sampai 5).
2. Tulis problem statement untuk ide terbaik.
3. Tulis dua tujuan SMART dan lima butir out of scope.

---

# Bab 4. Manajemen Proyek

## 4.1 Mengapa perlu manajemen proyek

Tanpa rencana, pekerjaan menumpuk di akhir. Manajemen proyek membantu Anda menjawab: apa yang harus dikerjakan, siapa yang mengerjakan, kapan, dan bagaimana mengetahui bahwa pekerjaan sudah selesai.

## 4.2 Memilih pendekatan: Waterfall, Agile, atau campuran

|Pendekatan|Ciri|Cocok bila|
|---|---|---|
|Waterfall|Tahap berurutan, dokumen lengkap di awal|Kebutuhan sangat jelas dan stabil|
|Agile (Scrum/Kanban)|Siklus pendek, umpan balik rutin|Kebutuhan bisa berubah, pengguna dapat dilibatkan|
|Campuran|Perencanaan awal ringan + iterasi|Banyak proyek capstone|

Rekomendasi untuk pemula: pakai Scrum ringan dengan sprint 2 minggu, disertai dokumen kebutuhan dan desain yang cukup di awal.

## 4.3 Scrum untuk tim kecil

Komponen utama:

1. **Product Backlog**: daftar semua hal yang ingin dibangun, diurutkan menurut prioritas.
2. **Sprint**: periode kerja tetap (misalnya 2 minggu) yang menghasilkan sebagian produk yang bisa didemokan.
3. **Sprint Planning**: rapat memilih item backlog untuk sprint.
4. **Daily Scrum (stand-up)**: pertemuan singkat. Pada capstone boleh dua atau tiga kali seminggu.
5. **Sprint Review**: demo hasil sprint kepada pengguna atau dosen.
6. **Sprint Retrospective**: tim membahas apa yang berjalan baik dan apa yang diperbaiki.

Peran Scrum: Product Owner (menentukan prioritas, boleh diperankan ketua tim atau perwakilan mitra), Scrum Master (menjaga proses), dan Developers.

Referensi resmi: Scrum Guide terbaru dari scrumguides.org.

## 4.4 Memecah pekerjaan: Work Breakdown Structure (WBS)

WBS memecah proyek besar menjadi bagian kecil hingga mudah dikerjakan dan diperkirakan.

```
SIPINJAM-LAB
  1. Manajemen Akun
     1.1 Registrasi
     1.2 Login dan logout
     1.3 Pengelolaan peran (mahasiswa, petugas, admin)
  2. Katalog Alat
     2.1 Daftar alat
     2.2 Detail alat dan stok
  3. Peminjaman
     3.1 Pengajuan
     3.2 Persetujuan petugas
     3.3 Pengembalian
  4. Laporan
```

Aturan praktis: sebuah tugas yang baik dapat diselesaikan satu orang dalam 1 sampai 3 hari. Lebih besar dari itu, pecah lagi.

## 4.4.1 Menulis user story yang dapat dikerjakan

Format:

> Sebagai **[peran]**, saya ingin **[kemampuan]** agar **[manfaat]**.

Contoh: "Sebagai mahasiswa, saya ingin melihat alat yang tersedia pada tanggal tertentu agar saya tidak mengajukan alat yang sedang dipinjam orang lain."

## 4.5 Estimasi usaha

Memperkirakan waktu itu sulit, apalagi bagi pemula. Beberapa teknik:

1. **Story points**: ukuran relatif (1, 2, 3, 5, 8, 13). Bandingkan tugas baru dengan tugas yang sudah dikenal.
2. **Planning poker**: setiap anggota memilih angka secara bersamaan, lalu perbedaan didiskusikan.
3. **Aturan emas**: kalikan estimasi pertama Anda dengan 1,5 sampai 2. Pemula hampir selalu terlalu optimis.
4. Sisakan waktu cadangan (buffer) sekitar 20 persen untuk hal tak terduga, perbaikan bug, dan integrasi.

Ukur kecepatan tim (velocity), yaitu jumlah story points yang diselesaikan per sprint, lalu gunakan itu untuk merencanakan sprint berikutnya.

## 4.6 Prioritas dengan MoSCoW

|Kategori|Arti|Contoh|
|---|---|---|
|Must have|Wajib, tanpa ini produk gagal|Login, pengajuan peminjaman|
|Should have|Penting, tetapi ada solusi sementara|Notifikasi email|
|Could have|Diinginkan bila sempat|Ekspor laporan ke PDF|
|Won't have (this time)|Sengaja ditunda|Aplikasi seluler asli|

Targetkan: semua Must selesai dengan kualitas baik, jauh lebih penting daripada banyak fitur setengah jadi.

## 4.7 Produk yang Dapat Dipakai Paling Awal (MVP)

Minimum Viable Product (MVP) adalah versi paling sederhana yang sudah memberi nilai kepada pengguna. Bangun MVP dulu, baru tambahkan fitur. Strategi ini menjaga Anda tetap punya produk yang berjalan saat waktu hampir habis.

## 4.8 Definition of Ready dan Definition of Done

- **Definition of Ready (DoR)**: syarat sebuah tugas boleh mulai dikerjakan. Contoh: kriteria penerimaan sudah jelas, desain tampilan sudah ada.
- **Definition of Done (DoD)**: syarat sebuah tugas dianggap selesai. Contoh:
    1. Kode lolos tinjauan (code review) oleh minimal satu anggota lain.
    2. Pengujian otomatis terkait lulus.
    3. Tidak ada peringatan keamanan kritis.
    4. Dokumentasi diperbarui.
    5. Sudah digabung ke cabang utama dan berjalan di lingkungan uji.

## 4.9 Manajemen risiko

Risiko adalah kejadian tak pasti yang dapat mengganggu proyek. Buat daftar risiko sejak awal:

|ID|Risiko|Kemungkinan|Dampak|Mitigasi|
|---|---|---|---|---|
|R1|Anggota sakit atau mundur|Sedang|Tinggi|Dokumentasi baik, tidak ada satu orang pemegang pengetahuan tunggal|
|R2|Mitra lambat memberi data|Tinggi|Sedang|Siapkan data contoh sintetis|
|R3|Teknologi baru terlalu sulit|Sedang|Tinggi|Lakukan spike (uji coba kecil) di minggu awal|
|R4|Layanan cloud gratis dibatasi|Sedang|Sedang|Rancang agar bisa dipindah, simpan cadangan|
|R5|Scope membesar|Tinggi|Tinggi|Backlog terkendali, perubahan harus disepakati|

Tinjau ulang daftar ini di setiap sprint review.

## 4.10 Jadwal contoh 16 minggu

|Minggu|Fokus|Luaran|
|---|---|---|
|1-2|Topik, tim, proposal|Proposal dan problem statement|
|3-4|Kebutuhan, riset awal|SRS awal, backlog, daftar risiko|
|5-6|Desain dan prototipe|Arsitektur, ERD, wireframe|
|7-10|Implementasi sprint 1 dan 2|MVP berjalan|
|11-12|Implementasi sprint 3, pengujian|Fitur Should have, laporan uji|
|13|Keamanan, performa, perbaikan bug|Perbaikan, pengujian penerimaan pengguna (UAT)|
|14|Deployment, dokumentasi|Sistem terpasang, panduan|
|15|Laporan dan latihan presentasi|Draf laporan akhir|
|16|Sidang dan serah terima|Laporan final, kode, demo|

Sesuaikan dengan kalender akademik kampus Anda.

## 4.11 Alat bantu manajemen

Contoh kategori alat (pilih yang gratis dan dikuasai tim):

1. **Papan tugas**: Trello, GitHub Projects, Jira, Notion, atau Linear.
2. **Komunikasi**: grup pesan, Discord, Slack.
3. **Dokumen bersama**: Google Docs atau Notion.
4. **Penjadwalan**: kalender bersama.

Satu alat yang dipakai konsisten lebih baik daripada lima alat yang setengah terpakai.

## 4.12 Latihan Bab 4

1. Buat WBS tingkat 3 untuk proyek Anda.
2. Tulis minimal 10 user story dan beri label MoSCoW.
3. Susun jadwal 16 minggu dan daftar 5 risiko beserta mitigasinya.

---

# Bab 5. Rekayasa Kebutuhan

## 5.1 Apa itu kebutuhan

Kebutuhan (requirement) adalah pernyataan tentang apa yang harus dilakukan atau dimiliki sistem. Kesalahan kebutuhan adalah sumber biaya perbaikan paling mahal, karena baru ketahuan ketika sistem sudah jadi.

Ada dua jenis utama:

1. **Kebutuhan fungsional**: apa yang dilakukan sistem. Contoh: "Sistem harus memungkinkan mahasiswa mengajukan peminjaman alat."
2. **Kebutuhan nonfungsional**: seberapa baik sistem melakukannya. Contoh: "Halaman daftar alat harus tampil dalam waktu kurang dari 2 detik pada koneksi 4G."

## 5.2 Kategori kebutuhan nonfungsional

|Kategori|Pertanyaan|Contoh terukur|
|---|---|---|
|Kinerja|Seberapa cepat?|95 persen permintaan selesai di bawah 500 ms|
|Keamanan|Siapa boleh mengakses apa?|Kata sandi disimpan dalam bentuk hash|
|Ketersediaan|Seberapa sering aktif?|Aktif 99 persen pada jam operasional|
|Kegunaan|Seberapa mudah dipakai?|Pengguna baru dapat meminjam alat dalam 3 menit tanpa bantuan|
|Skalabilitas|Seberapa banyak pengguna?|Mendukung 200 pengguna bersamaan|
|Keterpeliharaan|Seberapa mudah diubah?|Cakupan pengujian minimal 70 persen|
|Kompatibilitas|Di perangkat apa?|Peramban modern dan layar seluler|
|Aksesibilitas|Dapat dipakai semua orang?|Kontras warna memenuhi pedoman WCAG|

Kebutuhan nonfungsional yang tidak bisa diukur ("sistem harus cepat") tidak dapat diuji. Selalu ubah menjadi angka.

## 5.3 Teknik menggali kebutuhan

1. **Wawancara**: tanyakan dengan pertanyaan terbuka ("Ceritakan bagaimana proses peminjaman saat ini").
2. **Observasi**: amati pengguna bekerja langsung, sering kali mengungkap hal yang tidak mereka sebutkan.
3. **Kuesioner**: berguna untuk jumlah pengguna banyak.
4. **Analisis dokumen**: formulir, laporan, atau aturan yang sudah ada.
5. **Prototipe**: perlihatkan gambar kasar, minta tanggapan.
6. **Workshop**: pertemuan bersama stakeholder.

Tips wawancara untuk pemula:

- Siapkan 8 sampai 10 pertanyaan terbuka.
- Rekam atau catat (dengan izin).
- Tanyakan "kenapa" beberapa kali untuk menemukan akar masalah.
- Jangan menawarkan solusi terlalu cepat. Dengarkan dulu.

## 5.4 Menulis kebutuhan yang baik

Kebutuhan yang baik memiliki ciri:

1. **Jelas**: hanya satu tafsiran.
2. **Atomik**: satu kebutuhan per kalimat.
3. **Dapat diuji**: ada cara membuktikan terpenuhi atau tidak.
4. **Konsisten**: tidak bertentangan dengan kebutuhan lain.
5. **Dapat dilacak**: punya ID unik.
6. **Tidak menentukan solusi** tanpa alasan (tulis apa, bukan bagaimana).

Hindari kata ambigu: "cepat", "mudah", "fleksibel", "dll", "user-friendly".

Contoh buruk: "Sistem harus mudah digunakan." Contoh baik: "KF-03: Sistem harus menampilkan konfirmasi pengajuan peminjaman setelah mahasiswa menekan tombol Ajukan."

## 5.5 Kriteria penerimaan (Acceptance Criteria)

Kriteria penerimaan menjelaskan kapan user story dianggap benar. Format yang populer adalah Given-When-Then (Gherkin):

```gherkin
Fitur: Pengajuan peminjaman alat

  Skenario: Mahasiswa mengajukan alat yang tersedia
    Diberikan mahasiswa sudah login
    Dan alat "Osiloskop" tersedia pada 5 November 2026
    Ketika mahasiswa mengajukan peminjaman alat tersebut untuk tanggal itu
    Maka sistem menyimpan pengajuan dengan status "Menunggu"
    Dan sistem menampilkan pesan konfirmasi

  Skenario: Mahasiswa mengajukan alat yang sudah dipinjam
    Diberikan alat "Osiloskop" sudah dipinjam pada 5 November 2026
    Ketika mahasiswa mengajukan peminjaman alat tersebut untuk tanggal itu
    Maka sistem menolak pengajuan
    Dan menampilkan alasan "Alat tidak tersedia"
```

Kriteria penerimaan ini nantinya langsung menjadi dasar kasus uji (Bab 11).

## 5.6 Use case dan diagram use case

Use case menggambarkan interaksi antara aktor (pengguna atau sistem luar) dan sistem.

Contoh deskripsi use case:

|Elemen|Isi|
|---|---|
|Nama|Mengajukan peminjaman|
|Aktor|Mahasiswa|
|Prasyarat|Mahasiswa sudah login|
|Alur utama|1. Mahasiswa memilih alat. 2. Mahasiswa memilih tanggal. 3. Sistem memeriksa ketersediaan. 4. Mahasiswa menekan Ajukan. 5. Sistem menyimpan pengajuan.|
|Alur alternatif|3a. Alat tidak tersedia: sistem menampilkan pesan dan kembali ke langkah 1.|
|Pascakondisi|Pengajuan tersimpan dengan status Menunggu|

Diagram use case dengan Mermaid (dapat ditampilkan oleh banyak aplikasi pembaca Markdown):

```mermaid
flowchart LR
    M[Mahasiswa] --> U1((Login))
    M --> U2((Lihat Katalog))
    M --> U3((Ajukan Peminjaman))
    P[Petugas Lab] --> U4((Setujui atau Tolak))
    P --> U5((Catat Pengembalian))
    A[Admin] --> U6((Kelola Pengguna))
    A --> U7((Lihat Laporan))
```

## 5.7 Dokumen SRS

Software Requirements Specification (SRS) adalah dokumen resmi kebutuhan. Standar rujukan yang umum adalah ISO/IEC/IEEE 29148. Isi SRS ringkas ada di Lampiran B.

## 5.8 Matriks keterlacakan (Traceability Matrix)

Matriks ini menghubungkan kebutuhan dengan desain, kode, dan pengujian, sehingga Anda tahu tidak ada kebutuhan yang terlewat.

|ID Kebutuhan|Komponen desain|Modul kode|ID kasus uji|
|---|---|---|---|
|KF-01 Login|Auth service|auth/|TC-001, TC-002|
|KF-03 Ajukan peminjaman|Loan service|loans/|TC-010 sampai TC-014|

## 5.9 Mengelola perubahan kebutuhan

Perubahan itu wajar. Yang berbahaya adalah perubahan yang tidak terkendali. Gunakan proses sederhana:

1. Catat permintaan perubahan.
2. Nilai dampaknya pada jadwal dan fitur lain.
3. Putuskan bersama: terima, tunda, atau tolak.
4. Perbarui backlog dan dokumen.

## 5.10 Latihan Bab 5

1. Lakukan wawancara dengan satu calon pengguna dan catat lima temuan penting.
2. Tulis 10 kebutuhan fungsional dan 5 kebutuhan nonfungsional yang terukur.
3. Tulis kriteria penerimaan Given-When-Then untuk tiga user story.

---

# Bab 6. Perancangan Sistem

## 6.1 Dari "apa" ke "bagaimana"

Setelah kebutuhan jelas, Anda merancang bagaimana sistem akan membangun kebutuhan tersebut. Desain yang baik memudahkan pembagian tugas, mengurangi bug, dan memudahkan perubahan.

## 6.2 Prinsip desain dasar

1. **Modularitas**: pecah sistem menjadi bagian kecil yang punya satu tanggung jawab jelas.
2. **Low coupling, high cohesion**: antar modul sedikit bergantung, di dalam modul isinya saling terkait erat.
3. **Separation of concerns**: pisahkan tampilan, logika bisnis, dan akses data.
4. **DRY (Don't Repeat Yourself)**: hindari menulis logika yang sama berulang.
5. **KISS (Keep It Simple)**: pilih solusi paling sederhana yang memenuhi kebutuhan.
6. **YAGNI (You Aren't Gonna Need It)**: jangan membangun fitur yang belum dibutuhkan.
7. **Prinsip SOLID** untuk desain berorientasi objek:
    - Single Responsibility: satu kelas, satu alasan berubah.
    - Open/Closed: terbuka untuk perluasan, tertutup untuk perubahan.
    - Liskov Substitution: subtipe dapat menggantikan tipe induk.
    - Interface Segregation: antarmuka kecil dan spesifik.
    - Dependency Inversion: bergantung pada abstraksi, bukan implementasi konkret.

## 6.3 Pola arsitektur

|Pola|Penjelasan singkat|Cocok untuk capstone?|
|---|---|---|
|Monolit berlapis|Satu aplikasi, terpisah dalam lapisan (presentasi, bisnis, data)|Ya, pilihan paling aman untuk pemula|
|MVC / MVVM|Memisahkan Model, View, Controller|Ya, banyak kerangka kerja menyediakannya|
|Client-server dengan API|Front-end terpisah dari back-end lewat API|Ya, umum dan fleksibel|
|Microservices|Banyak layanan kecil terpisah|Jarang, kompleksitas tinggi. Pilih hanya bila ada alasan kuat|
|Serverless|Fungsi dijalankan sesuai permintaan|Bisa untuk bagian tertentu|
|Event-driven|Komponen berkomunikasi lewat peristiwa|Bila ada pemrosesan asinkron|

Saran: mulailah dari monolit yang rapi atau client-server sederhana. Memilih microservices tanpa alasan jelas hanya menambah beban waktu.

## 6.4 Arsitektur contoh (client-server dengan API)

```mermaid
flowchart TB
    subgraph Klien
        W[Aplikasi Web - Browser]
    end
    subgraph Server
        API[REST API]
        BL[Logika Bisnis]
        AU[Autentikasi]
    end
    DB[(Basis Data)]
    MAIL[Layanan Email]
    W -->|HTTPS| API
    API --> AU
    API --> BL
    BL --> DB
    BL --> MAIL
```

## 6.5 Model C4 untuk menggambarkan arsitektur

C4 membantu Anda menggambar arsitektur dalam empat tingkat zoom:

1. **Context**: sistem Anda dan pihak luar (pengguna, sistem lain).
2. **Container**: aplikasi dan penyimpanan data besar yang membentuk sistem (web app, API, basis data).
3. **Component**: komponen di dalam container.
4. **Code**: kelas dan fungsi (jarang digambar manual).

Untuk capstone, tingkat 1 sampai 3 biasanya cukup.

## 6.6 Pemodelan dengan UML

Unified Modeling Language (UML) adalah notasi standar untuk menggambar rancangan. Diagram yang paling bermanfaat:

|Diagram|Kegunaan|
|---|---|
|Use case|Interaksi pengguna dan sistem (Bab 5)|
|Activity|Alur proses|
|Sequence|Urutan pesan antar komponen dalam satu skenario|
|Class|Struktur kelas dan relasinya|
|ERD (bukan UML murni)|Struktur data|
|State machine|Status siklus hidup objek|

Contoh diagram sequence untuk pengajuan peminjaman:

```mermaid
sequenceDiagram
    participant M as Mahasiswa
    participant FE as Front-end
    participant API as API
    participant DB as Basis Data
    M->>FE: Pilih alat dan tanggal, tekan Ajukan
    FE->>API: POST /loans
    API->>DB: Cek ketersediaan alat
    DB-->>API: Tersedia
    API->>DB: Simpan pengajuan (status Menunggu)
    API-->>FE: 201 Created
    FE-->>M: Tampilkan konfirmasi
```

Contoh diagram status untuk peminjaman:

```mermaid
stateDiagram-v2
    [*] --> Menunggu
    Menunggu --> Disetujui: petugas setuju
    Menunggu --> Ditolak: petugas tolak
    Disetujui --> Dipinjam: alat diambil
    Dipinjam --> Dikembalikan: alat dikembalikan
    Dipinjam --> Terlambat: lewat tenggat
    Terlambat --> Dikembalikan: alat dikembalikan
    Ditolak --> [*]
    Dikembalikan --> [*]
```

## 6.7 Perancangan basis data

Langkah:

1. Identifikasi entitas (benda yang datanya disimpan): Pengguna, Alat, Peminjaman.
2. Tentukan atribut tiap entitas.
3. Tentukan relasi (satu-ke-banyak, banyak-ke-banyak).
4. Normalisasi hingga bentuk normal ketiga (3NF) untuk menghindari duplikasi.
5. Tentukan kunci primer, kunci asing, dan indeks.

Contoh ERD dengan Mermaid:

```mermaid
erDiagram
    USERS ||--o{ LOANS : mengajukan
    EQUIPMENT ||--o{ LOANS : dipinjam
    USERS {
        int id PK
        string name
        string email
        string password_hash
        string role
    }
    EQUIPMENT {
        int id PK
        string name
        string code
        int stock
    }
    LOANS {
        int id PK
        int user_id FK
        int equipment_id FK
        date start_date
        date due_date
        string status
    }
```

Pembahasan lebih jauh ada di Bab 10.

## 6.8 Perancangan antarmuka (UI/UX)

Alur kerja desain yang disarankan:

1. **Sketsa kasar** di kertas.
2. **Wireframe**: kerangka tampilan tanpa warna dan gambar (misalnya dengan Figma atau alat lain).
3. **Prototipe interaktif**: wireframe yang bisa diklik untuk menguji alur.
4. **Uji kegunaan**: minta 3 sampai 5 calon pengguna mencoba dan amati kesulitan mereka.
5. **Antarmuka final** dengan gaya visual yang konsisten.

Pedoman dasar:

1. Konsisten: tombol, warna, dan istilah sama di seluruh aplikasi.
2. Beri umpan balik: tampilkan status ("Menyimpan...", "Berhasil").
3. Cegah kesalahan: validasi masukan, konfirmasi sebelum aksi berbahaya.
4. Kontras dan ukuran huruf cukup (rujuk pedoman WCAG).
5. Responsif: nyaman di layar ponsel dan komputer.
6. Pesan galat yang membantu: "Email sudah terdaftar" lebih baik daripada "Error 500".

## 6.9 Perancangan API

API (Application Programming Interface) adalah pintu bagi program lain, misalnya front-end, untuk memakai fungsi back-end. Gaya yang paling umum adalah REST lewat HTTP.

Aturan praktis REST:

|Tujuan|Metode HTTP|Contoh URL|
|---|---|---|
|Ambil daftar|GET|/api/equipment|
|Ambil satu|GET|/api/equipment/12|
|Buat baru|POST|/api/loans|
|Ubah penuh|PUT|/api/equipment/12|
|Ubah sebagian|PATCH|/api/loans/5|
|Hapus|DELETE|/api/equipment/12|

Kode status penting: 200 (OK), 201 (dibuat), 400 (permintaan salah), 401 (belum login), 403 (tidak berhak), 404 (tidak ditemukan), 409 (konflik), 500 (galat server).

Dokumentasikan API dengan spesifikasi OpenAPI (sebelumnya Swagger) agar tim front-end dan back-end bisa bekerja paralel dengan kontrak yang sama.

## 6.10 Catatan keputusan arsitektur (ADR)

Setiap keputusan teknis besar sebaiknya dicatat singkat, supaya tidak dilupakan atau diperdebatkan ulang.

```
ADR-001: Memilih PostgreSQL sebagai basis data
Status: Disetujui
Konteks: Data relasional (pengguna, alat, peminjaman), butuh transaksi.
Keputusan: Memakai PostgreSQL.
Alternatif: MongoDB (ditolak: relasi kuat dan butuh konsistensi), SQLite (ditolak: kurang cocok untuk multi-pengguna produksi).
Konsekuensi: Perlu migrasi skema terkelola; tim sudah familiar dengan SQL.
```

## 6.11 Latihan Bab 6

1. Gambar diagram arsitektur tingkat Container untuk proyek Anda.
2. Buat ERD minimal 5 entitas.
3. Buat wireframe untuk 3 halaman utama.
4. Tulis daftar endpoint API beserta metode dan kode statusnya.

---

# Bab 7. Memilih Teknologi (Tech Stack)

## 7.1 Prinsip memilih

1. **Pilih yang dikuasai tim**, bukan yang paling populer. Belajar teknologi baru sambil mengerjakan proyek besar menambah risiko.
2. **Pilih yang punya komunitas dan dokumentasi baik**, supaya mudah mencari solusi.
3. **Pilih yang sesuai kebutuhan**, bukan yang paling canggih.
4. **Pertimbangkan hosting dan biaya**: apakah ada tingkat gratis yang cukup?
5. **Lakukan spike**: sebelum memutuskan, uji coba satu hari untuk memastikan teknologi bekerja untuk kasus Anda.

## 7.2 Kategori dan contoh pilihan

Contoh berikut hanyalah gambaran. Versi dan popularitas berubah dari tahun ke tahun.

|Lapisan|Contoh pilihan|
|---|---|
|Front-end web|React, Vue, Svelte, Next.js, Nuxt, atau HTML/CSS/JavaScript murni|
|Seluler|Flutter, React Native, Kotlin (Android), Swift (iOS)|
|Back-end|Node.js (Express, NestJS), Python (FastAPI, Django, Flask), Java/Kotlin (Spring Boot), PHP (Laravel), Go|
|Basis data relasional|PostgreSQL, MySQL/MariaDB, SQLite|
|Basis data lain|MongoDB (dokumen), Redis (cache), Elasticsearch (pencarian)|
|Autentikasi|Library bawaan kerangka kerja, OAuth 2.0 / OpenID Connect, layanan identitas pihak ketiga|
|Pengujian|pytest, Jest, Vitest, JUnit, Playwright atau Cypress (E2E)|
|Kontrol versi|Git dengan GitHub, GitLab, atau Bitbucket|
|CI/CD|GitHub Actions, GitLab CI|
|Container|Docker, Docker Compose|
|Cloud|Penyedia cloud besar atau platform hosting yang lebih sederhana|
|Machine learning|Python dengan scikit-learn, PyTorch, atau pemanfaatan API model yang sudah ada|

## 7.3 Matriks keputusan

Gunakan tabel berbobot supaya keputusan objektif.

|Kriteria|Bobot|Opsi A: Laravel|Opsi B: FastAPI|Opsi C: Express|
|---|---|---|---|---|
|Dikuasai tim|5|4|3|4|
|Dokumentasi|3|5|4|4|
|Cocok untuk kebutuhan|4|4|4|4|
|Kemudahan deployment|3|4|3|4|
|**Total (bobot x skor)**||**67**|**56**|**63**|

(Angka di atas hanya ilustrasi cara menghitung. Hasil nyata bergantung pada kondisi tim Anda.)

## 7.4 Hal yang perlu diwaspadai

1. **Tergoda teknologi baru** tanpa alasan kuat.
2. **Terlalu banyak teknologi berbeda**: setiap tambahan menambah beban belajar dan pemeliharaan.
3. **Ketergantungan pada satu penyedia (vendor lock-in)**.
4. **Lisensi**: periksa lisensi library (MIT, Apache 2.0, GPL, dan lain-lain). Pastikan kompatibel dengan tujuan proyek.

## 7.5 Latihan Bab 7

1. Buat matriks keputusan untuk memilih back-end dan basis data proyek Anda.
2. Lakukan spike satu hari untuk teknologi yang belum Anda kuasai dan catat hasilnya.

---

# Bab 8. Implementasi dan Kolaborasi Kode

## 8.1 Kontrol versi dengan Git

Git adalah sistem kontrol versi: mencatat setiap perubahan kode, memungkinkan kembali ke versi lama, dan memudahkan banyak orang bekerja bersamaan.

Istilah dasar:

|Istilah|Arti|
|---|---|
|Repository (repo)|Tempat penyimpanan proyek beserta riwayatnya|
|Commit|Satu catatan perubahan|
|Branch|Cabang pengembangan terpisah|
|Merge|Menggabungkan cabang|
|Pull request (PR) / Merge request (MR)|Permintaan menggabungkan cabang, disertai tinjauan|
|Conflict|Dua orang mengubah bagian yang sama sehingga perlu diselesaikan manual|
|Clone / Fork|Menyalin repositori|

Perintah yang sering dipakai:

```bash
git clone <url-repo>              # salin repo ke komputer
git checkout -b fitur/login       # buat dan pindah ke cabang baru
git status                        # lihat status perubahan
git add .                         # siapkan semua perubahan untuk commit
git commit -m "feat: tambah halaman login"
git pull --rebase origin main     # ambil perubahan terbaru dari main
git push origin fitur/login       # kirim cabang ke repo jarak jauh
```

## 8.2 Strategi percabangan

Untuk tim kecil, strategi sederhana ini cukup:

1. Cabang `main` selalu dalam kondisi stabil dan bisa dijalankan.
2. Setiap fitur atau perbaikan dikerjakan di cabang terpisah, misalnya `fitur/ajukan-peminjaman` atau `perbaikan/validasi-tanggal`.
3. Penggabungan ke `main` hanya lewat pull request yang ditinjau minimal satu anggota lain dan lolos pengujian otomatis.
4. Lindungi cabang `main` (branch protection) agar tidak ada push langsung.

Cabang berumur panjang menimbulkan konflik besar. Gabungkan sering, dalam potongan kecil.

## 8.3 Pesan commit yang baik

Pakai format Conventional Commits agar riwayat mudah dibaca:

```
feat: tambah endpoint pengajuan peminjaman
fix: perbaiki validasi tanggal kembali
docs: perbarui panduan instalasi
test: tambah uji untuk layanan peminjaman
refactor: pisahkan logika stok ke modul tersendiri
chore: perbarui dependensi
```

Aturan: kalimat singkat, menjelaskan apa dan mengapa, satu commit untuk satu perubahan logis.

## 8.4 Tinjauan kode (Code Review)

Tinjauan kode meningkatkan kualitas dan menyebarkan pengetahuan. Checklist peninjau:

1. Apakah kode menyelesaikan tugas sesuai kriteria penerimaan?
2. Apakah mudah dibaca (nama jelas, fungsi pendek)?
3. Apakah ada pengujian untuk perubahan ini?
4. Apakah ada risiko keamanan (masukan tidak divalidasi, rahasia tertulis di kode)?
5. Apakah ada duplikasi atau logika yang dapat disederhanakan?

Etika: kritik kode, bukan orangnya. Gunakan bahasa seperti "Bagaimana jika kita..." daripada "Ini salah."

## 8.5 Standar penulisan kode

1. Gunakan **konvensi penamaan** yang konsisten: nama variabel dan fungsi menjelaskan isinya (`jumlahStokTersedia`, bukan `x`).
2. Fungsi sebaiknya pendek dan melakukan satu hal.
3. Hindari angka ajaib (magic number): beri nama konstanta.
4. Komentar menjelaskan **mengapa**, bukan **apa** (apa sudah terlihat dari kode).
5. Gunakan **linter** dan **formatter** otomatis (misalnya ESLint dan Prettier untuk JavaScript, Ruff atau Black untuk Python) agar gaya seragam tanpa debat.

Contoh perbandingan:

```python
# Kurang baik
def f(a, b):
    if a > b:
        return a - b
    return 0

# Lebih baik
def hitung_hari_terlambat(tanggal_kembali, tenggat):
    """Mengembalikan jumlah hari keterlambatan; 0 bila tidak terlambat."""
    selisih = (tanggal_kembali - tenggat).days
    return max(selisih, 0)
```

## 8.6 Struktur folder proyek

Struktur yang teratur memudahkan anggota baru memahami proyek. Contoh untuk proyek web dengan back-end dan front-end terpisah:

```
sipinjam-lab/
  README.md
  docker-compose.yml
  .github/workflows/ci.yml
  docs/
    srs.md
    arsitektur.md
    keputusan/ADR-001.md
  backend/
    src/
      routes/
      services/
      models/
      middleware/
    tests/
    Dockerfile
    .env.example
  frontend/
    src/
      pages/
      components/
      api/
    tests/
    Dockerfile
```

## 8.7 Konfigurasi dan rahasia

1. Simpan konfigurasi yang berubah antar lingkungan (alamat basis data, kunci API) di **variabel lingkungan**, bukan di kode.
2. Sediakan berkas `.env.example` berisi nama variabel tanpa nilai rahasia.
3. Tambahkan `.env` ke `.gitignore` agar tidak ikut terkirim ke repositori.
4. Jika rahasia (kata sandi, token) pernah terlanjur ter-commit, anggap sudah bocor: ganti segera, jangan sekadar menghapus dari kode.

```
# .env.example
DATABASE_URL=
JWT_SECRET=
SMTP_HOST=
SMTP_USER=
SMTP_PASSWORD=
```

## 8.8 Contoh implementasi endpoint (Python, FastAPI)

Contoh berikut menunjukkan struktur sederhana dengan validasi. Anda dapat menerjemahkan ide yang sama ke kerangka kerja lain.

```python
from datetime import date
from fastapi import FastAPI, HTTPException, status
from pydantic import BaseModel, field_validator

app = FastAPI()

class LoanRequest(BaseModel):
    equipment_id: int
    start_date: date
    due_date: date

    @field_validator("due_date")
    @classmethod
    def due_after_start(cls, v, info):
        start = info.data.get("start_date")
        if start and v <= start:
            raise ValueError("Tanggal kembali harus setelah tanggal pinjam")
        return v

# Simulasi penyimpanan sederhana untuk ilustrasi
LOANS = []

@app.post("/api/loans", status_code=status.HTTP_201_CREATED)
def create_loan(payload: LoanRequest):
    if payload.start_date < date.today():
        raise HTTPException(status_code=400, detail="Tanggal pinjam tidak boleh di masa lalu")
    loan = {"id": len(LOANS) + 1, **payload.model_dump(), "status": "Menunggu"}
    LOANS.append(loan)
    return loan
```

Catatan: pada proyek nyata, data disimpan di basis data, bukan di daftar dalam memori, dan Anda wajib menambahkan autentikasi serta pemeriksaan ketersediaan stok.

## 8.9 Penanganan galat dan pencatatan (Logging)

1. Tangani galat yang bisa diperkirakan (masukan salah, data tidak ditemukan) dengan pesan jelas dan kode status yang tepat.
2. Jangan menampilkan detail internal (jejak tumpukan, kueri SQL) kepada pengguna.
3. Catat peristiwa penting ke log: login gagal, galat sistem, perubahan penting.
4. Jangan menulis data sensitif (kata sandi, nomor kartu) ke log.
5. Gunakan tingkat log: DEBUG, INFO, WARNING, ERROR.

## 8.10 Refactoring dan utang teknis

Utang teknis (technical debt) adalah kode yang dibuat cepat dengan kualitas kurang, yang menimbulkan biaya perbaikan di kemudian hari. Sedikit utang boleh diambil secara sadar, tetapi catat dan lunasi. Jadwalkan waktu khusus tiap sprint untuk merapikan kode (refactoring) tanpa mengubah perilaku, dengan dukungan pengujian otomatis.

## 8.11 Latihan Bab 8

1. Buat repositori, tambahkan `README.md`, `.gitignore`, dan lindungi cabang `main`.
2. Lakukan satu siklus lengkap: buat cabang, commit, buka pull request, tinjau oleh rekan, gabungkan.
3. Sengaja buat konflik penggabungan di repositori latihan, lalu selesaikan.

---

# Bab 9. Memakai AI secara Bertanggung Jawab

## 9.1 Mengapa bab ini ada

Asisten AI untuk pemrograman kini sangat umum dan dapat mempercepat pekerjaan. Namun AI dapat menghasilkan kode yang tampak meyakinkan tetapi salah, tidak aman, atau tidak Anda pahami. Capstone dinilai dari kemampuan Anda, jadi AI harus menjadi alat bantu belajar dan bekerja, bukan pengganti pemahaman.

## 9.2 Aturan dasar

1. **Patuhi kebijakan kampus dan dosen** tentang penggunaan AI. Jika ada kewajiban melaporkan penggunaan, lakukan dengan jujur.
2. **Anda bertanggung jawab penuh** atas semua yang Anda kumpulkan, termasuk bagian yang dibantu AI.
3. **Pahami sebelum memakai**: jika Anda tidak dapat menjelaskan sebuah baris kode, jangan masukkan ke proyek. Saat sidang, penguji dapat menanyakan bagian mana pun.
4. **Verifikasi**: jalankan, uji, dan tinjau keluaran AI seperti Anda meninjau kode rekan.
5. **Jangan membagikan data sensitif**: kata sandi, kunci API, data pribadi pengguna, atau dokumen rahasia mitra tidak boleh dimasukkan ke layanan AI pihak ketiga tanpa izin.
6. **Perhatikan hak cipta dan lisensi**: kode atau teks yang dihasilkan bisa menyerupai sumber lain. Periksa dan beri atribusi bila perlu.

## 9.3 Pemakaian yang sehat

|Pemakaian|Catatan|
|---|---|
|Menjelaskan konsep atau pesan galat|Bagus untuk belajar. Cocokkan dengan dokumentasi resmi|
|Menghasilkan kerangka awal (boilerplate)|Tinjau dan sesuaikan|
|Mengusulkan kasus uji|Periksa apakah mencakup kasus tepi dan sesuai kebutuhan Anda|
|Meninjau kode untuk bug atau kerentanan|Tetap lakukan tinjauan manusia|
|Merapikan tata bahasa laporan|Isi dan analisis tetap karya Anda; ikuti aturan kampus|
|Membuat seluruh sistem atau laporan tanpa Anda pahami|Tidak disarankan dan berpotensi melanggar aturan integritas akademik|

## 9.4 Cara menulis perintah (prompt) yang baik

Perintah yang jelas menghasilkan jawaban yang lebih berguna. Unsur yang membantu:

1. **Konteks**: bahasa pemrograman, kerangka kerja, tujuan.
2. **Tugas**: apa yang diminta, spesifik.
3. **Batasan**: gaya, versi, hal yang harus dihindari.
4. **Contoh**: masukan dan keluaran yang diharapkan.
5. **Format keluaran**: misalnya "berikan penjelasan singkat lalu kode".

Contoh kurang baik: "Buatkan login."

Contoh lebih baik:

```
Saya memakai FastAPI dan PostgreSQL. Jelaskan cara menyimpan kata sandi
dengan aman saat registrasi, memakai hash yang lambat dan bergaram
(bcrypt atau argon2). Berikan contoh kode singkat dan jelaskan mengapa
tidak boleh memakai MD5 atau SHA-256 polos untuk kata sandi.
```

## 9.5 Risiko khas kode buatan AI

1. **Halusinasi**: fungsi atau library yang sebenarnya tidak ada, atau versi yang tidak cocok.
2. **Kerentanan**: kueri SQL yang disusun dari string mentah, kunci rahasia tertulis di kode, validasi yang lemah.
3. **Kode usang** atau tidak mengikuti praktik terkini.
4. **Pengujian semu**: uji yang selalu lulus tetapi tidak menguji hal penting.
5. **Ketidakkonsistenan gaya** antarbagian proyek.

Mitigasi: tinjauan kode, pengujian otomatis, pemindaian keamanan (Bab 12), dan membaca dokumentasi resmi.

## 9.5.1 Jika proyek Anda sendiri memakai AI sebagai fitur

Jika capstone Anda memuat komponen kecerdasan buatan (misalnya klasifikasi, rekomendasi, atau chatbot), tambahkan hal berikut:

1. **Definisikan metrik**: akurasi, presisi, recall, F1, atau metrik lain sesuai masalah. Bandingkan dengan baseline sederhana.
2. **Pisahkan data**: data latih, validasi, dan uji. Jangan menguji pada data yang sama dengan yang dipakai melatih.
3. **Dokumentasikan data**: sumber, ukuran, cara pembersihan, dan keterbatasan.
4. **Evaluasi bias dan keadilan**: apakah kinerja berbeda signifikan antar kelompok?
5. **Rencanakan kegagalan**: apa yang terjadi bila model salah atau tidak yakin? Sediakan penanganan manusia (human-in-the-loop) untuk keputusan penting.
6. **Pantau setelah rilis**: kinerja model dapat menurun saat data berubah.
7. **Transparansi**: beri tahu pengguna ketika mereka berinteraksi dengan sistem berbasis AI.
8. **Reproduksibilitas**: catat versi data, kode, parameter, dan benih acak (random seed).

## 9.6 Mendokumentasikan penggunaan AI

Buat catatan sederhana (misalnya berkas `docs/penggunaan-ai.md`):

|Tanggal|Alat|Tujuan|Bagian proyek|Bagaimana diverifikasi|
|---|---|---|---|---|
|2026-11-02|Asisten AI|Contoh validasi tanggal|Modul peminjaman|Diuji dengan 6 kasus uji dan ditinjau rekan|

Catatan ini membantu transparansi dan melindungi Anda bila ada pertanyaan.

## 9.7 Latihan Bab 9

1. Minta asisten AI membuat fungsi sederhana, lalu tinjau: temukan minimal dua hal yang dapat diperbaiki.
2. Tulis kebijakan penggunaan AI untuk tim Anda (maksimal 10 butir) yang sesuai aturan kampus.

---

# Bab 10. Basis Data dan API

## 10.1 Basis data relasional dalam ringkas

Basis data relasional menyimpan data dalam tabel berisi baris dan kolom. Bahasa kueri standarnya adalah SQL.

Konsep penting:

1. **Primary key (PK)**: pengenal unik tiap baris.
2. **Foreign key (FK)**: kolom yang merujuk ke PK tabel lain, menjaga integritas relasi.
3. **Index**: struktur tambahan untuk mempercepat pencarian.
4. **Transaksi**: sekelompok operasi yang berhasil semua atau batal semua (sifat ACID: Atomicity, Consistency, Isolation, Durability).
5. **Migrasi**: skrip yang mengubah skema basis data secara terkendali dan dapat diulang.

## 10.2 Contoh skema SQL

```sql
CREATE TABLE users (
    id            SERIAL PRIMARY KEY,
    name          VARCHAR(100) NOT NULL,
    email         VARCHAR(255) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    role          VARCHAR(20)  NOT NULL CHECK (role IN ('mahasiswa', 'petugas', 'admin')),
    created_at    TIMESTAMP    NOT NULL DEFAULT NOW()
);

CREATE TABLE equipment (
    id    SERIAL PRIMARY KEY,
    code  VARCHAR(30)  NOT NULL UNIQUE,
    name  VARCHAR(150) NOT NULL,
    stock INTEGER      NOT NULL CHECK (stock >= 0)
);

CREATE TABLE loans (
    id           SERIAL PRIMARY KEY,
    user_id      INTEGER NOT NULL REFERENCES users(id),
    equipment_id INTEGER NOT NULL REFERENCES equipment(id),
    start_date   DATE    NOT NULL,
    due_date     DATE    NOT NULL,
    status       VARCHAR(20) NOT NULL DEFAULT 'Menunggu',
    CHECK (due_date > start_date)
);

CREATE INDEX idx_loans_user ON loans(user_id);
CREATE INDEX idx_loans_equipment_dates ON loans(equipment_id, start_date, due_date);
```

## 10.3 Kueri yang sering dipakai

```sql
-- Daftar peminjaman milik satu pengguna beserta nama alat
SELECT l.id, e.name AS alat, l.start_date, l.due_date, l.status
FROM loans l
JOIN equipment e ON e.id = l.equipment_id
WHERE l.user_id = 7
ORDER BY l.start_date DESC;

-- Peminjaman yang terlambat
SELECT l.id, u.name, e.name AS alat, l.due_date
FROM loans l
JOIN users u ON u.id = l.user_id
JOIN equipment e ON e.id = l.equipment_id
WHERE l.status = 'Dipinjam' AND l.due_date < CURRENT_DATE;
```

## 10.4 Mencegah SQL Injection

SQL injection terjadi bila masukan pengguna disambungkan langsung ke kueri. Jangan lakukan ini:

```python
# BERBAHAYA: menyambung string
query = "SELECT * FROM users WHERE email = '" + email + "'"
```

Gunakan kueri berparameter atau ORM:

```python
# Aman: parameter dipisahkan dari kueri
cursor.execute("SELECT * FROM users WHERE email = %s", (email,))
```

## 10.5 ORM dan migrasi

Object-Relational Mapper (ORM) menghubungkan tabel basis data dengan objek di kode (misalnya Eloquent, Prisma, SQLAlchemy, atau TypeORM). Kelebihan: mengurangi kode SQL berulang dan membantu mencegah injeksi. Kekurangan: dapat menghasilkan kueri tidak efisien bila dipakai sembarangan, sehingga tetap perlu memahami SQL.

Gunakan **alat migrasi** agar perubahan skema tercatat di repositori dan dapat diterapkan berurutan di setiap lingkungan.

## 10.6 Desain API yang baik

1. **Konsisten**: penamaan jamak untuk sumber daya (`/equipment`, `/loans`), format respons seragam.
2. **Versi**: awali dengan `/api/v1/` agar perubahan di masa depan tidak merusak klien lama.
3. **Paginasi**: untuk daftar panjang, kembalikan sebagian data per halaman (`?page=2&limit=20`).
4. **Validasi** semua masukan di sisi server, walaupun front-end sudah memvalidasi.
5. **Pesan galat seragam**:

```json
{
  "error": {
    "code": "EQUIPMENT_UNAVAILABLE",
    "message": "Alat tidak tersedia pada tanggal yang dipilih."
  }
}
```

6. **Idempotensi** bila relevan: mengirim permintaan yang sama dua kali tidak menimbulkan efek ganda yang tidak diinginkan.
7. **Pembatasan laju (rate limiting)** untuk mencegah penyalahgunaan.

## 10.7 Autentikasi dan otorisasi

- **Autentikasi**: memastikan siapa Anda (login).
- **Otorisasi**: menentukan apa yang boleh Anda lakukan (hak akses).

Praktik dasar:

1. Simpan kata sandi sebagai hash dengan algoritma yang dirancang untuk itu (bcrypt, scrypt, atau argon2) dan garam (salt). Jangan pernah menyimpan kata sandi dalam teks biasa.
2. Pakai HTTPS di semua lingkungan nyata.
3. Terapkan kontrol akses berbasis peran (RBAC) dan **periksa di server**, bukan hanya menyembunyikan tombol di tampilan.
4. Jika memakai token (misalnya JWT), beri masa berlaku pendek, simpan dengan aman, dan sediakan mekanisme pembaruan serta pencabutan.
5. Pertimbangkan autentikasi dua langkah untuk akun penting.

## 10.8 Latihan Bab 10

1. Implementasikan skema pada 10.2 di basis data pilihan Anda.
2. Tulis kueri untuk laporan "alat paling sering dipinjam".
3. Tulis ulang satu kueri yang rentan injeksi menjadi versi berparameter.

---

# Bab 11. Pengujian Perangkat Lunak

## 11.1 Mengapa menguji

Pengujian bertujuan menemukan cacat sebelum pengguna menemukannya dan memberi keyakinan bahwa perubahan baru tidak merusak fitur lama. Pengujian tidak membuktikan program bebas bug; ia hanya mengurangi risiko.

Istilah penting: **verifikasi** (apakah kita membangun produk dengan benar sesuai spesifikasi) dan **validasi** (apakah kita membangun produk yang benar sesuai kebutuhan pengguna).

## 11.2 Tingkat pengujian

```
        /\
       /  \      E2E / UI       (sedikit, lambat, mahal)
      /----\
     /      \    Integrasi / API (sedang)
    /--------\
   /          \  Unit           (banyak, cepat, murah)
  /------------\
```

Ini disebut piramida pengujian.

|Tingkat|Menguji apa|Contoh|
|---|---|---|
|Unit|Fungsi atau kelas tunggal|Fungsi hitung hari terlambat|
|Integrasi|Beberapa komponen bersama|Endpoint API dengan basis data uji|
|Sistem / E2E|Alur lengkap dari sudut pengguna|Login, pilih alat, ajukan, lihat status di browser|
|Penerimaan (UAT)|Pengguna nyata menilai apakah memenuhi kebutuhan|Petugas lab mencoba alur harian|

## 11.3 Jenis pengujian lain

1. **Fungsional**: sesuai kebutuhan fungsional.
2. **Nonfungsional**: kinerja (beban dan stres), keamanan, kegunaan, kompatibilitas.
3. **Regresi**: memastikan perubahan tidak merusak fitur lama. Idealnya otomatis.
4. **Smoke test**: pemeriksaan cepat bahwa fungsi paling dasar hidup setelah rilis.
5. **Eksploratori**: penguji bebas mencoba dan "mengakali" sistem untuk menemukan masalah tak terduga.

## 11.4 Teknik merancang kasus uji

1. **Partisi ekuivalen**: bagi masukan menjadi kelompok yang diperlakukan sama, uji satu wakil per kelompok.
2. **Analisis nilai batas (boundary value)**: kesalahan sering terjadi di batas. Jika stok maksimal 10, uji 0, 1, 9, 10, 11.
3. **Tabel keputusan**: untuk aturan bisnis dengan banyak kondisi.
4. **Uji status**: pastikan hanya transisi status yang sah yang diperbolehkan (lihat diagram status di Bab 6).
5. **Kasus negatif**: masukan kosong, format salah, nilai ekstrem, pengguna tanpa hak akses.

## 11.5 Format kasus uji

|ID|Tujuan|Prasyarat|Langkah|Hasil diharapkan|Hasil aktual|Status|
|---|---|---|---|---|---|---|
|TC-010|Ajukan alat tersedia|Mahasiswa login, stok 3|Pilih alat, tanggal valid, Ajukan|Pengajuan tersimpan dengan status Menunggu|(diisi saat uji)|Lulus/Gagal|
|TC-011|Ajukan dengan tanggal kembali sebelum tanggal pinjam|Mahasiswa login|Isi tanggal kembali lebih awal, Ajukan|Ditolak dengan pesan validasi|||
|TC-012|Ajukan alat stok 0|Stok 0|Pilih alat, Ajukan|Ditolak, pesan "Alat tidak tersedia"|||

## 11.6 Contoh pengujian unit (Python, pytest)

Kode yang diuji:

```python
# loans/rules.py
from datetime import date

def hitung_hari_terlambat(tanggal_kembali: date, tenggat: date) -> int:
    selisih = (tanggal_kembali - tenggat).days
    return max(selisih, 0)
```

Pengujian:

```python
# tests/test_rules.py
from datetime import date
from loans.rules import hitung_hari_terlambat

def test_tidak_terlambat_bila_kembali_sebelum_tenggat():
    assert hitung_hari_terlambat(date(2026, 11, 3), date(2026, 11, 5)) == 0

def test_tidak_terlambat_bila_kembali_tepat_tenggat():
    assert hitung_hari_terlambat(date(2026, 11, 5), date(2026, 11, 5)) == 0

def test_terlambat_dua_hari():
    assert hitung_hari_terlambat(date(2026, 11, 7), date(2026, 11, 5)) == 2
```

Jalankan dengan perintah `pytest`.

## 11.7 Contoh pengujian API (integrasi)

```python
from fastapi.testclient import TestClient
from main import app

client = TestClient(app)

def test_ajukan_peminjaman_berhasil():
    res = client.post("/api/loans", json={
        "equipment_id": 1,
        "start_date": "2030-01-10",
        "due_date": "2030-01-12",
    })
    assert res.status_code == 201
    assert res.json()["status"] == "Menunggu"

def test_tanggal_kembali_sebelum_pinjam_ditolak():
    res = client.post("/api/loans", json={
        "equipment_id": 1,
        "start_date": "2030-01-12",
        "due_date": "2030-01-10",
    })
    assert res.status_code == 422  # validasi gagal
```

## 11.8 Pola Arrange-Act-Assert

Susun setiap uji dalam tiga bagian: **Arrange** (siapkan data), **Act** (jalankan aksi), **Assert** (periksa hasil). Pola ini membuat uji mudah dibaca.

## 11.9 Cakupan pengujian dan metrik mutu

1. **Code coverage**: persentase baris atau cabang kode yang dijalankan oleh uji. Target realistis untuk capstone sekitar 60 sampai 80 persen pada logika inti. Cakupan tinggi tidak otomatis berarti uji berkualitas; periksa juga isi asersinya.
2. **Jumlah dan tingkat keparahan bug** yang ditemukan dan diperbaiki.
3. **Tingkat kelulusan uji**.
4. **Waktu respons** pada uji beban.

## 11.10 Pengujian kegunaan dan penerimaan pengguna (UAT)

Rancang UAT dengan 5 sampai 10 pengguna nyata:

1. Siapkan skenario tugas ("Pinjam osiloskop untuk tanggal 5 November").
2. Amati tanpa membantu; catat di mana mereka bingung.
3. Ukur: tingkat keberhasilan tugas, waktu, dan kepuasan.
4. Kuesioner standar seperti System Usability Scale (SUS) dapat dipakai untuk skor kegunaan.
5. Dokumentasikan temuan dan perbaikan yang dilakukan. Ini nilai tambah besar pada laporan.

## 11.11 Mengelola bug

Catat setiap bug dengan: judul, langkah mereproduksi, hasil diharapkan dan aktual, tingkat keparahan, dan tangkapan layar atau log. Gunakan pelacak isu (issue tracker) agar tidak ada bug yang hilang.

|Keparahan|Arti|Contoh|
|---|---|---|
|Kritis|Sistem tidak bisa dipakai atau data rusak|Login gagal untuk semua|
|Tinggi|Fitur utama gagal|Pengajuan tidak tersimpan|
|Sedang|Fitur sebagian bermasalah, ada jalan pintas|Filter tanggal salah|
|Rendah|Kosmetik|Salah ketik label|

## 11.12 Uji kinerja singkat

Gunakan alat uji beban (misalnya k6, JMeter, atau Locust) untuk mensimulasikan banyak pengguna dan mengukur waktu respons serta tingkat galat. Bandingkan dengan target kebutuhan nonfungsional pada Bab 5. Catat hasil sebelum dan sesudah optimasi.

## 11.13 Latihan Bab 11

1. Tulis 10 kasus uji dari kriteria penerimaan Bab 5, termasuk 3 kasus negatif dan 2 nilai batas.
2. Implementasikan minimal 5 pengujian unit otomatis.
3. Rancang skenario UAT untuk tiga tugas utama.

---

# Bab 12. Keamanan dan Privasi

## 12.1 Prinsip dasar keamanan informasi

Segitiga CIA:

1. **Confidentiality (kerahasiaan)**: hanya pihak berhak yang dapat mengakses data.
2. **Integrity (integritas)**: data tidak berubah tanpa izin.
3. **Availability (ketersediaan)**: sistem dapat dipakai saat dibutuhkan.

Prinsip lain:

- **Least privilege**: beri hak akses sekecil yang diperlukan.
- **Defense in depth**: banyak lapisan pertahanan.
- **Secure by default**: pengaturan awal harus aman.
- **Jangan percaya masukan**: validasi semua data dari luar.

## 12.2 Ancaman umum aplikasi web

OWASP Top 10 adalah daftar risiko keamanan aplikasi web yang diperbarui berkala oleh komunitas OWASP. Periksa versi terbaru di situs resmi owasp.org. Kategori yang secara konsisten muncul antara lain:

|Risiko|Penjelasan sederhana|Pencegahan dasar|
|---|---|---|
|Broken Access Control|Pengguna mengakses data atau fungsi yang bukan haknya|Periksa otorisasi di server untuk setiap permintaan|
|Cryptographic Failures|Data sensitif tidak dilindungi|HTTPS, hash kata sandi, jangan buat kriptografi sendiri|
|Injection|Masukan dieksekusi sebagai perintah (SQL, perintah sistem)|Kueri berparameter, validasi, escaping|
|Insecure Design|Kelemahan dari rancangan|Pemodelan ancaman sejak awal|
|Security Misconfiguration|Pengaturan bawaan tidak aman, fitur debug aktif|Hardening, tinjau konfigurasi|
|Vulnerable Components|Memakai library dengan celah diketahui|Pemindaian dependensi, perbarui rutin|
|Authentication Failures|Login lemah|Kata sandi kuat, batasi percobaan, autentikasi dua langkah|
|Integrity Failures|Pembaruan atau data tidak diverifikasi|Verifikasi sumber dan tanda tangan|
|Logging and Monitoring Failures|Serangan tidak terdeteksi|Catat dan pantau peristiwa keamanan|
|SSRF|Server dipaksa mengakses alamat internal|Validasi URL, daftar izin|

Selain itu waspadai **XSS (Cross-Site Scripting)** dan **CSRF (Cross-Site Request Forgery)**. Mitigasi XSS: escape keluaran, gunakan kerangka kerja yang melakukannya otomatis, terapkan Content Security Policy. Mitigasi CSRF: token CSRF, atribut cookie SameSite.

## 12.3 Pemodelan ancaman sederhana

Lakukan sesi 1 jam di fase desain dengan pertanyaan model STRIDE:

|Huruf|Ancaman|Contoh pertanyaan|
|---|---|---|
|S|Spoofing (menyamar)|Bisakah orang berpura-pura menjadi petugas?|
|T|Tampering (mengubah data)|Bisakah status peminjaman diubah tanpa hak?|
|R|Repudiation (menyangkal)|Apakah ada jejak audit siapa menyetujui apa?|
|I|Information disclosure (kebocoran)|Apakah data pengguna lain dapat terlihat?|
|D|Denial of service|Apakah satu pengguna bisa membuat sistem lumpuh?|
|E|Elevation of privilege|Bisakah mahasiswa mengakses menu admin?|

Catat ancaman beserta mitigasinya dan jadikan item backlog.

## 12.4 Kode aman: praktik harian

1. Validasi masukan di server (panjang, tipe, format, rentang).
2. Gunakan kueri berparameter.
3. Hash kata sandi; jangan simpan teks asli.
4. Jangan menaruh rahasia di kode atau repositori.
5. Pesan galat umum untuk pengguna, detail hanya di log internal.
6. Perbarui dependensi secara berkala dan pindai kerentanan dengan alat seperti dependency audit bawaan manajer paket, Dependabot, atau pemindai sejenis.
7. Batasi ukuran dan tipe berkas yang diunggah, simpan di luar direktori yang dapat dieksekusi.
8. Aktifkan header keamanan HTTP dan HTTPS.
9. Terapkan pembatasan laju pada login dan endpoint sensitif.

## 12.5 Pelindungan data pribadi

Di Indonesia, pemrosesan data pribadi diatur oleh Undang-Undang Nomor 27 Tahun 2022 tentang Pelindungan Data Pribadi (UU PDP). Sebagai pengembang, praktik yang selaras dengan prinsip-prinsipnya antara lain:

1. **Minimisasi data**: kumpulkan hanya data yang benar-benar dibutuhkan.
2. **Tujuan jelas**: beri tahu pengguna untuk apa data dipakai dan dapatkan persetujuan bila diperlukan.
3. **Keamanan**: lindungi data dengan enkripsi dan kontrol akses.
4. **Hak pengguna**: sediakan cara melihat, memperbaiki, atau menghapus data sesuai ketentuan.
5. **Retensi**: jangan menyimpan data lebih lama dari perlu.
6. **Anonimisasi data uji**: jangan memakai data pribadi nyata untuk pengembangan dan demo bila tidak perlu; gunakan data sintetis.

Catatan: ini ringkasan edukatif, bukan nasihat hukum. Untuk proyek dengan data pribadi sungguhan, konsultasikan dengan dosen pembimbing atau pihak berwenang di kampus atau mitra Anda dan rujuk teks resmi undang-undang beserta peraturan turunannya.

## 12.6 Pencadangan dan pemulihan

1. Cadangkan basis data secara berkala dan **uji pemulihannya** (cadangan yang belum pernah diuji belum bisa dipercaya).
2. Simpan salinan di lokasi terpisah dari server utama.
3. Dokumentasikan langkah pemulihan.

## 12.7 Latihan Bab 12

1. Lakukan sesi STRIDE untuk proyek Anda dan catat minimal 8 ancaman beserta mitigasi.
2. Jalankan pemindaian dependensi pada proyek Anda dan perbaiki temuan berisiko tinggi.
3. Periksa apakah ada rahasia yang pernah ter-commit di riwayat repositori Anda.

---

# Bab 13. CI/CD, Container, dan Deployment

## 13.1 Konsep

- **Continuous Integration (CI)**: setiap perubahan kode digabung sering dan otomatis dibangun serta diuji.
- **Continuous Delivery/Deployment (CD)**: hasil yang lolos uji otomatis disiapkan atau langsung dirilis ke lingkungan target.
- **Pipeline**: rangkaian langkah otomatis (build, lint, test, scan, deploy).

Manfaat: bug ketahuan cepat, rilis konsisten, dan mengurangi pekerjaan manual yang rawan salah.

## 13.2 Contoh pipeline CI (GitHub Actions)

```yaml
# .github/workflows/ci.yml
name: CI

on:
  pull_request:
  push:
    branches: [main]

jobs:
  backend-test:
    runs-on: ubuntu-latest
    services:
      postgres:
        image: postgres:16
        env:
          POSTGRES_PASSWORD: test
          POSTGRES_DB: sipinjam_test
        ports: ["5432:5432"]
        options: >-
          --health-cmd="pg_isready -U postgres"
          --health-interval=5s
          --health-timeout=5s
          --health-retries=10
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"
      - name: Install dependencies
        run: pip install -r backend/requirements.txt
      - name: Lint
        run: ruff check backend
      - name: Run tests
        env:
          DATABASE_URL: postgresql://postgres:test@localhost:5432/sipinjam_test
        run: pytest backend/tests --maxfail=1 -q
```

Versi action dan runtime di atas hanya contoh; periksa versi terbaru di dokumentasi resmi saat Anda mengimplementasikannya.

## 13.3 Container dengan Docker

Container membungkus aplikasi beserta dependensinya sehingga berjalan sama di laptop, server uji, dan produksi ("works on my machine" tidak lagi menjadi alasan).

Contoh `Dockerfile` untuk back-end Python:

```dockerfile
FROM python:3.12-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Jalankan sebagai pengguna non-root
RUN useradd -m appuser
USER appuser

EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

Contoh `docker-compose.yml` untuk menjalankan seluruh sistem lokal:

```yaml
services:
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: sipinjam
      POSTGRES_PASSWORD: ${DB_PASSWORD}
      POSTGRES_DB: sipinjam
    volumes:
      - dbdata:/var/lib/postgresql/data

  backend:
    build: ./backend
    environment:
      DATABASE_URL: postgresql://sipinjam:${DB_PASSWORD}@db:5432/sipinjam
    depends_on:
      - db
    ports:
      - "8000:8000"

  frontend:
    build: ./frontend
    ports:
      - "3000:80"
    depends_on:
      - backend

volumes:
  dbdata:
```

Jalankan dengan `docker compose up --build`.

## 13.4 Lingkungan (environment)

|Lingkungan|Fungsi|
|---|---|
|Development|Laptop pengembang|
|Staging / Test|Mirip produksi, untuk pengujian akhir dan UAT|
|Production|Dipakai pengguna nyata|

Untuk capstone, minimal sediakan satu lingkungan yang dapat diakses penguji agar demo tidak bergantung pada laptop Anda.

## 13.5 Strategi deployment

1. **Manual** (disalin ke server): paling mudah tetapi rawan salah.
2. **Otomatis lewat pipeline**: disarankan.
3. **Rolling, blue-green, canary**: strategi lanjutan untuk meminimalkan waktu henti, biasanya tidak diperlukan pada capstone.

Siapkan **rencana rollback**: bagaimana kembali ke versi sebelumnya jika rilis bermasalah.

## 13.6 Infrastructure as Code dan konfigurasi

Mendefinisikan infrastruktur lewat berkas (misalnya Docker Compose, Terraform, atau konfigurasi platform) membuat lingkungan dapat direproduksi dan diperiksa lewat kontrol versi. Untuk pemula, cukup mulai dari Docker Compose.

## 13.7 Pemantauan dan observabilitas

Setelah sistem berjalan, Anda perlu tahu kondisinya:

1. **Log**: catatan peristiwa.
2. **Metrik**: angka seperti jumlah permintaan, waktu respons, pemakaian memori.
3. **Trace**: jejak satu permintaan melewati beberapa komponen.
4. **Health check**: endpoint sederhana (misalnya `/health`) yang menunjukkan sistem hidup.
5. **Peringatan (alert)**: notifikasi ke tim bila ada masalah.

## 13.8 Biaya

Perhatikan biaya cloud sejak awal: pakai tingkat gratis atau kredit pelajar bila tersedia, matikan sumber daya yang tidak dipakai, dan atur batas anggaran serta peringatan tagihan. Jangan biarkan sumber daya berbayar menyala setelah proyek selesai.

## 13.9 Latihan Bab 13

1. Tulis Dockerfile untuk back-end dan front-end proyek Anda.
2. Buat pipeline CI yang menjalankan lint dan pengujian pada setiap pull request.
3. Tuliskan prosedur rollback dan uji sekali.

---

# Bab 14. Dokumentasi

## 14.1 Mengapa dokumentasi penting

Dokumentasi membuat proyek dapat dipahami, dipakai, dan dilanjutkan oleh orang lain, termasuk Anda sendiri enam bulan kemudian. Pada penilaian capstone, dokumentasi yang baik sering membedakan proyek rapi dari proyek yang hanya "bisa jalan di laptop pembuatnya".

## 14.2 Jenis dokumentasi

|Jenis|Pembaca|Isi|
|---|---|---|
|README|Pengembang dan penguji|Deskripsi, cara instalasi, cara menjalankan, cara uji|
|Dokumen kebutuhan (SRS)|Seluruh tim, mitra|Kebutuhan fungsional dan nonfungsional|
|Dokumen desain|Pengembang|Arsitektur, ERD, diagram, keputusan teknis|
|Dokumentasi API|Pengembang front-end/pihak ketiga|Endpoint, parameter, contoh respons|
|Rencana dan laporan pengujian|Penguji, dosen|Kasus uji, hasil, bug|
|Panduan pengguna|Pengguna akhir|Langkah memakai fitur dengan tangkapan layar|
|Panduan operasional|Administrator|Deployment, cadangan, pemantauan, pemecahan masalah|
|Catatan rilis (changelog)|Semua|Perubahan tiap versi|

## 14.3 README yang baik

Struktur yang disarankan:

```markdown
# Nama Proyek

Satu paragraf: apa yang dilakukan proyek ini dan untuk siapa.

## Fitur Utama
- ...

## Teknologi
- ...

## Prasyarat
- Docker 24+ atau Node/Python versi sekian

## Cara Menjalankan
1. Salin `.env.example` menjadi `.env` dan isi nilainya.
2. Jalankan `docker compose up --build`.
3. Buka http://localhost:3000.

## Akun Demo
- petugas@example.com / (sandi demo di dokumen terpisah)

## Menjalankan Pengujian
`pytest backend/tests`

## Struktur Proyek
Penjelasan singkat folder.

## Kontributor dan Lisensi
```

Uji README Anda: minta orang yang belum pernah melihat proyek mengikuti langkahnya dari nol. Jika gagal, perbaiki README.

## 14.4 Dokumentasi sebagai kode (docs as code)

Simpan dokumen dalam format teks (misalnya Markdown) di repositori yang sama dengan kode, dan lalui tinjauan seperti kode. Dengan begitu dokumen ikut berubah bersama kode dan riwayatnya tercatat. Diagram dapat ditulis dengan Mermaid atau PlantUML sehingga bisa disimpan sebagai teks.

## 14.5 Panduan pengguna

1. Tulis dari sudut pandang tugas: "Cara mengajukan peminjaman", bukan "Fungsi tombol X".
2. Gunakan langkah bernomor dan tangkapan layar.
3. Gunakan bahasa pengguna, bukan istilah teknis.
4. Sertakan bagian pemecahan masalah umum (FAQ).

## 14.6 Komentar kode dan dokumentasi inline

Gunakan docstring atau komentar dokumentasi untuk fungsi publik: tujuan, parameter, nilai kembalian, dan galat yang mungkin. Hindari komentar yang hanya mengulang kode.

## 14.7 Latihan Bab 14

1. Tulis README lengkap untuk proyek Anda dan minta rekan di luar tim mencobanya.
2. Buat panduan pengguna dengan minimal tiga tugas utama dan tangkapan layar.

---

# Bab 15. Laporan, Presentasi, dan Demo

## 15.1 Struktur laporan akhir

Format dapat berbeda antar kampus. Struktur umum:

1. Halaman judul, lembar pengesahan, kata pengantar, abstrak, daftar isi, daftar gambar dan tabel.
2. **Bab 1 Pendahuluan**: latar belakang, rumusan masalah, tujuan, manfaat, batasan.
3. **Bab 2 Tinjauan Pustaka dan Landasan Teori**: konsep dan teknologi yang dipakai, penelitian atau sistem terkait.
4. **Bab 3 Metodologi dan Perencanaan**: model proses (misalnya Scrum), jadwal, pembagian peran, manajemen risiko.
5. **Bab 4 Analisis Kebutuhan dan Perancangan**: kebutuhan, use case, arsitektur, ERD, antarmuka.
6. **Bab 5 Implementasi**: teknologi, struktur kode, potongan kode penting, antarmuka hasil.
7. **Bab 6 Pengujian dan Evaluasi**: rencana uji, hasil, UAT, analisis.
8. **Bab 7 Penutup**: kesimpulan, keterbatasan, saran pengembangan.
9. Daftar pustaka dan lampiran.

## 15.2 Tips menulis laporan teknis

1. Tulis sepanjang proyek berjalan, bukan sekaligus di akhir. Catatan dari tiap sprint menjadi bahan bab.
2. Satu paragraf, satu gagasan. Kalimat pendek dan jelas.
3. Setiap gambar dan tabel punya nomor, judul, dan dirujuk di teks.
4. Kesimpulan harus menjawab tujuan yang dirumuskan di Bab 1, dibuktikan dengan data pengujian.
5. Cantumkan keterbatasan dengan jujur; ini menunjukkan kematangan.
6. Kutip sumber dengan gaya sitasi yang diminta kampus (misalnya IEEE atau APA) dan hindari plagiarisme. Gunakan alat pengelola referensi seperti Zotero.

## 15.3 Presentasi

Struktur 15 menit yang umum:

|Menit|Isi|
|---|---|
|0-2|Masalah dan latar belakang: mengapa penting|
|2-4|Solusi dan tujuan|
|4-7|Desain dan arsitektur (singkat)|
|7-11|Demo langsung|
|11-13|Pengujian dan hasil (angka)|
|13-14|Kesimpulan dan pengembangan lanjutan|
|14-15|Penutup, siap tanya jawab|

Tips:

1. Satu slide, satu pesan. Sedikit teks, banyak visual.
2. Pembagian bicara merata di antara anggota dan tiap anggota paham seluruh sistem.
3. Latihan beberapa kali dengan pencatat waktu.
4. Antisipasi pertanyaan: mengapa memilih teknologi ini, bagaimana mengamankan data, apa yang terjadi bila X gagal, apa kontribusi Anda secara pribadi.

## 15.4 Demo langsung

Demo adalah momen paling berisiko dan paling meyakinkan.

1. Siapkan skenario demo tertulis (cerita pengguna dari awal sampai akhir) dan latih.
2. Siapkan data demo yang sudah terisi dan akun demo.
3. Siapkan **rencana cadangan**: rekaman video demo dan tangkapan layar jika internet atau server bermasalah.
4. Jalankan sistem di lingkungan yang sudah diuji, jangan mengubah kode beberapa jam sebelum sidang.
5. Siapkan juga koneksi cadangan (misalnya hotspot).
6. Bekukan kode (code freeze) beberapa hari sebelum sidang; hanya perbaikan bug kritis yang diperbolehkan.

## 15.5 Menjawab pertanyaan penguji

1. Dengarkan sampai selesai, ulangi pertanyaan bila perlu.
2. Jawab langsung, lalu jelaskan.
3. Jika tidak tahu, katakan jujur dan sampaikan bagaimana Anda akan mencari tahu. Jangan mengarang.
4. Terima kritik dengan tenang; catat sebagai masukan.

## 15.6 Poster dan video singkat

Jika diminta: poster memuat masalah, solusi, arsitektur, tangkapan layar, hasil, dan kode QR ke repositori atau demo. Video 2 sampai 3 menit menunjukkan alur utama dengan narasi singkat.

## 15.7 Latihan Bab 15

1. Buat kerangka laporan dengan perkiraan jumlah halaman per bab.
2. Susun slide 10 halaman dan latihan presentasi 15 menit di depan teman, lalu minta masukan.

---

# Bab 16. Penilaian dan Rubrik

Komponen dan bobot sebenarnya ditetapkan oleh prodi Anda. Contoh berikut hanya ilustrasi agar Anda tahu apa yang biasanya dinilai.

## 16.1 Contoh komponen penilaian

|Komponen|Bobot contoh|Yang dinilai|
|---|---|---|
|Proposal dan perencanaan|10%|Kejelasan masalah, tujuan, jadwal, risiko|
|Kebutuhan dan desain|15%|Kualitas dokumen, kesesuaian dengan masalah|
|Implementasi|25%|Fungsionalitas, kualitas kode, riwayat Git|
|Pengujian dan mutu|15%|Rencana, cakupan, bug, UAT|
|Dokumentasi dan laporan|15%|Kelengkapan dan kejelasan|
|Presentasi dan demo|10%|Penyampaian, penguasaan, demo|
|Proses dan kerja sama tim|10%|Konsistensi, kontribusi, laporan mingguan|

## 16.2 Contoh rubrik (empat level)

|Kriteria|Sangat baik (4)|Baik (3)|Cukup (2)|Kurang (1)|
|---|---|---|---|---|
|Perumusan masalah|Masalah nyata, spesifik, dukungan data|Jelas tetapi data terbatas|Umum|Tidak jelas|
|Kebutuhan|Terukur, dapat diuji, terlacak|Sebagian terukur|Banyak ambigu|Tidak ada|
|Desain|Konsisten, mendukung kebutuhan, ada alasan keputusan|Sesuai tetapi alasan minim|Tidak konsisten|Tidak ada|
|Kualitas kode|Rapi, teruji, ditinjau|Cukup rapi|Sulit dibaca|Berantakan|
|Pengujian|Berlapis dan otomatis, UAT terdokumentasi|Unit dan sebagian integrasi|Manual saja|Hampir tidak ada|
|Keamanan|Ancaman dianalisis dan dimitigasi|Praktik dasar diterapkan|Sebagian|Diabaikan|
|Dokumentasi|Lengkap dan teruji oleh orang luar|Lengkap|Kurang lengkap|Minim|
|Presentasi|Jelas, demo lancar, tanya jawab baik|Baik|Kurang terstruktur|Tidak siap|

## 16.3 Penilaian kontribusi individu

Pada proyek kelompok, nilai individu sering dipengaruhi oleh: riwayat commit dan pull request, tugas di papan kerja, penilaian rekan (peer assessment), dan penguasaan saat tanya jawab. Pastikan Anda memahami seluruh sistem walaupun hanya mengerjakan sebagian.

## 16.4 Latihan Bab 16

1. Nilai proyek Anda sendiri memakai rubrik 16.2 pada pertengahan proyek dan tentukan tiga perbaikan terbesar.

---

# Bab 17. Kesalahan Umum dan Cara Menghindarinya

|No|Kesalahan|Akibat|Cara menghindari|
|---|---|---|---|
|1|Topik terlalu besar|Tidak selesai|Tentukan MVP dan out of scope sejak awal|
|2|Topik terlalu mudah|Nilai rendah pada tantangan teknis|Tambahkan aspek teknis bermakna (keamanan, kinerja, analisis data)|
|3|Mulai coding tanpa memahami kebutuhan|Banyak pengerjaan ulang|Selesaikan kebutuhan dan desain dasar dulu|
|4|Tidak melibatkan pengguna|Produk tidak terpakai|Demo tiap sprint, UAT|
|5|Pembagian kerja tidak jelas|Tumpang tindih dan konflik|Papan tugas dengan penanggung jawab|
|6|Satu orang mengerjakan hampir semuanya|Beban tidak adil, risiko tinggi|Pair programming, rotasi, tinjauan kode|
|7|Menunda pengujian ke akhir|Bug menumpuk|Uji sejak awal, CI|
|8|Tidak memakai Git dengan disiplin|Kode hilang, konflik besar|Cabang kecil, commit sering, PR|
|9|Rahasia tertulis di repositori|Kebocoran|`.env`, pemindai rahasia, ganti kunci bila bocor|
|10|Mengabaikan keamanan|Celah mudah dieksploitasi|Bab 12, STRIDE, audit dependensi|
|11|Menyalin kode AI tanpa paham|Gagal saat tanya jawab, bug|Bab 9: pahami, uji, catat|
|12|Dokumentasi di menit terakhir|Dokumentasi buruk|Tulis sambil jalan|
|13|Demo hanya di laptop sendiri|Gagal saat sidang|Deploy ke lingkungan stabil, siapkan video cadangan|
|14|Mengubah kode sehari sebelum sidang|Sistem rusak|Code freeze|
|15|Mengabaikan data pribadi|Masalah etika dan hukum|Minimisasi dan anonimisasi, rujuk UU PDP|
|16|Tidak mencatat keputusan|Berdebat ulang, lupa alasan|ADR|
|17|Perfeksionisme pada fitur kecil|Fitur utama tertinggal|Prioritaskan Must have|
|18|Menyembunyikan masalah dari pembimbing|Terlambat ditangani|Laporkan hambatan lebih awal|

## Pola pikir yang membantu

1. **Selesai lebih baik daripada sempurna**, tetapi selesai harus memenuhi Definition of Done.
2. **Gagal lebih awal dan murah** lewat prototipe dan spike.
3. **Berkomunikasi berlebihan** lebih baik daripada kurang.
4. **Pelajari alasannya**, bukan hanya cara memakai alat.

---

# Bab 18. Studi Kasus Lengkap: SIPINJAM-LAB

Bab ini merangkum seluruh materi dalam satu contoh proyek fiktif agar Anda melihat bagaimana bagian-bagiannya terhubung. Ini adalah contoh ilustrasi; sesuaikan dengan proyek Anda.

## 18.1 Latar belakang dan masalah

Laboratorium Jaringan di sebuah program studi meminjamkan alat (osiloskop, router, kabel, mikrokontroler) kepada mahasiswa. Pencatatan memakai buku tulis. Akibatnya: petugas sulit mengetahui stok sebenarnya, alat sering terlambat dikembalikan tanpa terdeteksi, dan rekapitulasi bulanan memakan waktu berjam-jam.

**Problem statement**: Petugas dan mahasiswa mengalami kesulitan mengetahui ketersediaan dan status peminjaman alat karena pencatatan manual, sehingga terjadi alat hilang tanpa jejak, keterlambatan tidak terpantau, dan antrean panjang. Proyek ini bertujuan membangun sistem peminjaman berbasis web yang mencatat peminjaman dan pengembalian secara otomatis.

## 18.2 Tujuan SMART

1. Dalam 16 minggu, menyelesaikan sistem web dengan fitur katalog, pengajuan, persetujuan, pengembalian, dan laporan.
2. Mahasiswa dapat menyelesaikan pengajuan dalam kurang dari 2 menit (diuji pada 15 pengguna).
3. Rekapitulasi bulanan otomatis, menghemat pekerjaan manual petugas minimal 80 persen berdasarkan estimasi waktu sebelum dan sesudah.
4. Skor SUS minimal 70 pada UAT.

## 18.3 Stakeholder

|Stakeholder|Kebutuhan|
|---|---|
|Mahasiswa|Cek stok, ajukan, lihat status|
|Petugas lab|Setujui atau tolak, catat pengembalian, pantau keterlambatan|
|Kepala lab|Laporan ringkas|
|Admin|Kelola akun dan data alat|

## 18.4 Ruang lingkup

In scope: akun dan peran, katalog alat, pengajuan, persetujuan, pengembalian, notifikasi email tenggat, laporan bulanan.

Out of scope: aplikasi seluler asli, pembayaran denda, integrasi dengan sistem akademik kampus, pemindai barcode (ditunda ke pengembangan lanjutan).

## 18.5 Kebutuhan (cuplikan)

Fungsional:

|ID|Kebutuhan|Prioritas|
|---|---|---|
|KF-01|Sistem harus mengizinkan pengguna login dengan email dan kata sandi|Must|
|KF-02|Sistem harus menampilkan daftar alat beserta stok tersedia pada tanggal yang dipilih|Must|
|KF-03|Sistem harus mengizinkan mahasiswa mengajukan peminjaman dengan tanggal pinjam dan kembali|Must|
|KF-04|Sistem harus mengizinkan petugas menyetujui atau menolak pengajuan|Must|
|KF-05|Sistem harus mencatat pengembalian alat oleh petugas|Must|
|KF-06|Sistem harus mengirim email pengingat satu hari sebelum tenggat|Should|
|KF-07|Sistem harus menghasilkan laporan peminjaman bulanan yang dapat diunduh|Should|
|KF-08|Sistem harus menandai peminjaman yang melewati tenggat sebagai Terlambat|Must|

Nonfungsional:

|ID|Kebutuhan|
|---|---|
|KN-01|Halaman katalog harus tampil dalam kurang dari 2 detik untuk 95 persen permintaan pada 100 pengguna bersamaan|
|KN-02|Kata sandi harus disimpan sebagai hash dengan garam|
|KN-03|Akses menu petugas dan admin hanya untuk peran terkait, diperiksa di server|
|KN-04|Antarmuka harus dapat dipakai di layar lebar 360 piksel ke atas|
|KN-05|Cadangan basis data otomatis setiap hari, pemulihan diuji minimal sekali|

User story dan kriteria penerimaan contoh (KF-03):

> Sebagai mahasiswa, saya ingin mengajukan peminjaman alat untuk rentang tanggal tertentu agar saya dapat memakai alat itu untuk praktikum.

```gherkin
Skenario: Pengajuan berhasil
  Diberikan alat tersedia pada rentang tanggal yang dipilih
  Ketika mahasiswa menekan Ajukan
  Maka pengajuan tersimpan dengan status "Menunggu"

Skenario: Tanggal kembali sebelum tanggal pinjam
  Ketika mahasiswa memilih tanggal kembali sebelum tanggal pinjam
  Maka sistem menampilkan pesan validasi dan tidak menyimpan
```

## 18.6 Arsitektur dan teknologi

Keputusan (hasil matriks keputusan dan spike):

|Lapisan|Pilihan|Alasan|
|---|---|---|
|Front-end|React dengan TypeScript|Dikuasai 3 dari 4 anggota|
|Back-end|FastAPI (Python)|Cepat dikembangkan, validasi bawaan, dokumentasi OpenAPI otomatis|
|Basis data|PostgreSQL|Data relasional dan transaksi|
|Pengujian|pytest, Vitest, Playwright|Mencakup unit, integrasi, E2E|
|CI/CD|GitHub Actions|Repositori di GitHub|
|Deployment|Docker Compose di satu server virtual|Sederhana dan murah|

Gaya arsitektur: client-server dengan REST API (monolit berlapis di sisi back-end).

## 18.7 Pembagian peran (tim 4 orang)

|Anggota|Peran utama|Peran sekunder|
|---|---|---|
|A|Ketua, analis kebutuhan|Dokumentasi|
|B|Back-end|Basis data|
|C|Front-end|UI/UX|
|D|QA dan DevOps|Back-end pendukung|

## 18.8 Rencana sprint (sprint 2 minggu)

|Sprint|Sasaran|Item utama|
|---|---|---|
|0 (minggu 1-6)|Fondasi|Proposal, SRS, desain, repositori, CI dasar, prototipe|
|1 (minggu 7-8)|Autentikasi dan katalog|KF-01, KF-02|
|2 (minggu 9-10)|Peminjaman inti|KF-03, KF-04|
|3 (minggu 11-12)|Pengembalian dan status|KF-05, KF-08|
|4 (minggu 13-14)|Notifikasi dan laporan, keamanan, UAT|KF-06, KF-07, perbaikan|
|5 (minggu 15-16)|Stabilisasi, dokumentasi, sidang|Code freeze, latihan|

Tiap sprint diakhiri demo kepada petugas lab dan retrospektif tim.

## 18.9 Contoh daftar risiko aktual

|Risiko|Mitigasi|Hasil|
|---|---|---|
|Petugas sulit ditemui untuk wawancara|Jadwalkan wawancara tetap tiap Selasa, siapkan kuesioner daring|Tercapai|
|Tim baru mengenal TypeScript|Sesi belajar bersama, pair programming di sprint 1|Bug awal berkurang|
|Server uji kehabisan memori|Batasi sumber daya container, pantau metrik|Diperbaiki di sprint 3|

## 18.10 Contoh pengujian

|Level|Jumlah|Alat|Hasil contoh|
|---|---|---|---|
|Unit|64|pytest, Vitest|100% lulus, cakupan logika inti 78%|
|Integrasi API|28|pytest dengan basis data uji|Satu bug konflik tanggal ditemukan dan diperbaiki|
|E2E|6 alur utama|Playwright|Semua lulus pada lingkungan staging|
|Uji beban|100 pengguna bersamaan|k6|Persentil ke-95 waktu respons katalog 420 ms|
|UAT|12 pengguna|Skenario tugas dan SUS|Tingkat keberhasilan tugas 92%, skor SUS 78|

(Angka-angka di atas adalah contoh ilustrasi, bukan hasil nyata.)

## 18.11 Tantangan dan pelajaran yang dapat dilaporkan

1. Konflik penjadwalan alat ditangani dengan pemeriksaan ketersediaan di dalam transaksi basis data agar dua pengajuan tidak merebut stok terakhir secara bersamaan (race condition).
2. Perubahan permintaan dari petugas (misalnya status "Hilang") dikelola lewat proses perubahan kebutuhan dan ditunda ke sprint berikutnya.
3. Bagian yang paling banyak menyita waktu bukan kode, tetapi menyepakati aturan bisnis (misalnya batas maksimal hari pinjam).

## 18.12 Keterbatasan dan pengembangan lanjutan

1. Belum mendukung pemindaian barcode untuk pencatatan cepat.
2. Belum ada integrasi dengan sistem akademik untuk validasi status mahasiswa.
3. Laporan masih berbentuk berkas statis; dasbor interaktif dapat menjadi pengembangan lanjutan.

---

# Lampiran A. Template Proposal

```markdown
# Proposal Capstone Project

## 1. Identitas
- Judul proyek:
- Tim dan peran:
- Dosen pembimbing:
- Mitra/pengguna (jika ada):

## 2. Latar Belakang dan Masalah
(Problem statement: pengguna, masalah, dampak)

## 3. Tujuan dan Manfaat
(Tujuan SMART, manfaat bagi pengguna)

## 4. Ruang Lingkup
- In scope:
- Out of scope:
- Asumsi dan kendala:

## 5. Tinjauan Sistem Sejenis
(Tabel perbandingan, nilai tambah)

## 6. Rencana Solusi
- Gambaran arsitektur
- Teknologi yang diusulkan beserta alasan

## 7. Metodologi dan Jadwal
- Model proses (misalnya Scrum, sprint 2 minggu)
- Jadwal per minggu

## 8. Risiko dan Mitigasi
(Tabel risiko)

## 9. Rencana Pengujian dan Ukuran Keberhasilan
(Bagaimana keberhasilan diukur)

## 10. Pertimbangan Etika, Keamanan, dan Data Pribadi

## 11. Daftar Pustaka
```

# Lampiran B. Template Spesifikasi Kebutuhan (SRS) Ringkas

```markdown
# SRS - Nama Sistem

## 1. Pendahuluan
1.1 Tujuan dokumen
1.2 Ruang lingkup produk
1.3 Definisi, singkatan, istilah
1.4 Referensi

## 2. Deskripsi Umum
2.1 Perspektif produk (konteks sistem)
2.2 Fungsi produk (ringkasan)
2.3 Karakteristik pengguna
2.4 Batasan, asumsi, dan ketergantungan

## 3. Kebutuhan Spesifik
3.1 Kebutuhan fungsional (ID, deskripsi, prioritas, kriteria penerimaan)
3.2 Kebutuhan nonfungsional (kinerja, keamanan, ketersediaan, kegunaan, dll.)
3.3 Kebutuhan antarmuka (pengguna, perangkat lunak, perangkat keras, komunikasi)
3.4 Kebutuhan data

## 4. Model Sistem
4.1 Diagram use case
4.2 Deskripsi use case
4.3 Diagram aktivitas/alur utama

## 5. Matriks Keterlacakan

## 6. Lampiran
```

# Lampiran C. Template Laporan Mingguan

```markdown
# Laporan Mingguan - Minggu ke-__ (tanggal)

## Ringkasan
(2-3 kalimat kemajuan)

## Yang Diselesaikan
| Tugas | Penanggung jawab | Bukti (tautan PR/commit) |
|---|---|---|

## Rencana Minggu Depan
| Tugas | Penanggung jawab | Perkiraan selesai |
|---|---|---|

## Hambatan dan Bantuan yang Dibutuhkan

## Risiko Baru atau Perubahan Risiko

## Catatan Hasil Konsultasi dengan Pembimbing
```

# Lampiran D. Checklist Akhir Sebelum Sidang

Perencanaan dan kebutuhan

- [ ] Tujuan dalam proposal dapat dibuktikan dengan data dari pengujian.
- [ ] Semua kebutuhan Must memiliki implementasi dan kasus uji.
- [ ] Matriks keterlacakan diperbarui.

Kode dan repositori

- [ ] Cabang `main` stabil dan dapat dijalankan dari nol mengikuti README.
- [ ] Tidak ada rahasia di repositori maupun riwayatnya.
- [ ] Riwayat commit rapi dan mencerminkan kontribusi semua anggota.
- [ ] Linter bersih, CI hijau.

Pengujian dan keamanan

- [ ] Laporan pengujian (unit, integrasi, E2E, UAT) lengkap.
- [ ] Bug kritis dan tinggi sudah diperbaiki; sisanya terdokumentasi.
- [ ] Pemindaian dependensi dijalankan; temuan serius ditangani.
- [ ] Pencadangan dan pemulihan sudah diuji.
- [ ] Data pribadi diminimalkan; data demo bersifat sintetis.

Deployment dan demo

- [ ] Sistem berjalan di lingkungan stabil dan dapat diakses penguji.
- [ ] Akun dan data demo siap.
- [ ] Rekaman video demo dan tangkapan layar cadangan tersedia.
- [ ] Code freeze sudah diberlakukan.

Dokumentasi dan penyajian

- [ ] README, panduan pengguna, panduan operasional, dokumentasi API selesai.
- [ ] Laporan akhir lolos pemeriksaan kemiripan (plagiarisme) dan format.
- [ ] Penggunaan AI (jika ada) dicatat dan dilaporkan sesuai aturan.
- [ ] Presentasi sudah dilatih dengan waktu yang sesuai.
- [ ] Setiap anggota dapat menjelaskan seluruh sistem.

# Lampiran E. Glosarium

|Istilah|Arti|
|---|---|
|Acceptance criteria|Kriteria yang menentukan sebuah fitur dianggap diterima|
|ADR|Architecture Decision Record, catatan keputusan arsitektur|
|Agile|Pendekatan pengembangan iteratif dan adaptif|
|API|Antarmuka yang memungkinkan program berkomunikasi dengan program lain|
|Backlog|Daftar pekerjaan yang diprioritaskan|
|Branch|Cabang pengembangan dalam Git|
|CI/CD|Integrasi dan pengiriman berkelanjutan|
|Commit|Satu catatan perubahan kode di Git|
|Container|Paket terisolasi berisi aplikasi dan dependensinya|
|CRUD|Create, Read, Update, Delete|
|Definition of Done|Syarat sebuah pekerjaan dianggap selesai|
|DevOps|Budaya dan praktik yang menyatukan pengembangan dan operasi|
|ERD|Entity Relationship Diagram, diagram struktur data|
|Feasibility|Kelayakan|
|Front-end / Back-end|Bagian yang dilihat pengguna / bagian logika dan data di server|
|Git|Sistem kontrol versi|
|Hash|Hasil fungsi satu arah yang dipakai untuk menyimpan kata sandi dan memverifikasi integritas|
|JWT|JSON Web Token, token untuk autentikasi|
|Linter|Alat pemeriksa gaya dan kemungkinan kesalahan kode|
|Migrasi|Skrip perubahan skema basis data yang terkelola|
|MVP|Minimum Viable Product, versi paling sederhana yang sudah bernilai|
|ORM|Object-Relational Mapper|
|OWASP|Komunitas yang menerbitkan panduan keamanan aplikasi|
|Pipeline|Rangkaian langkah otomatis build, uji, dan rilis|
|Pull request|Permintaan menggabungkan cabang disertai tinjauan|
|RBAC|Role-Based Access Control, kontrol akses berbasis peran|
|Refactoring|Merapikan kode tanpa mengubah perilaku|
|REST|Gaya desain API berbasis HTTP|
|Scope creep|Perluasan ruang lingkup tanpa kendali|
|SRS|Software Requirements Specification|
|Sprint|Periode kerja tetap dalam Scrum|
|Stakeholder|Pihak yang berkepentingan atau terdampak|
|STRIDE|Model klasifikasi ancaman keamanan|
|SUS|System Usability Scale|
|UAT|User Acceptance Testing, pengujian penerimaan pengguna|
|UML|Unified Modeling Language|
|User story|Deskripsi kebutuhan dari sudut pandang pengguna|
|Velocity|Kecepatan tim menyelesaikan pekerjaan per sprint|
|WBS|Work Breakdown Structure|

# Lampiran F. Daftar Bacaan Lanjutan

Daftar ini berupa rujukan umum. Periksa edisi atau versi terbaru karena banyak di antaranya diperbarui berkala.

1. Sommerville, I. _Software Engineering_. Pearson. Buku teks rekayasa perangkat lunak yang luas dipakai.
2. Pressman, R. S. dan Maxim, B. R. _Software Engineering: A Practitioner's Approach_. McGraw-Hill.
3. Martin, R. C. _Clean Code_ dan _Clean Architecture_. Prentice Hall.
4. Hunt, A. dan Thomas, D. _The Pragmatic Programmer_. Addison-Wesley.
5. Schwaber, K. dan Sutherland, J. _The Scrum Guide_. Tersedia gratis di scrumguides.org.
6. Brown, S. _The C4 Model for Visualising Software Architecture_. c4model.com.
7. OWASP Foundation. _OWASP Top 10_ dan _OWASP Cheat Sheet Series_. owasp.org.
8. ISO/IEC/IEEE 29148. _Systems and software engineering - Life cycle processes - Requirements engineering_.
9. W3C. _Web Content Accessibility Guidelines (WCAG)_. w3.org.
10. Undang-Undang Republik Indonesia Nomor 27 Tahun 2022 tentang Pelindungan Data Pribadi.
11. Dokumentasi resmi alat yang Anda pakai (Git, Docker, GitHub Actions, kerangka kerja pilihan Anda). Selalu rujuk versi terbaru.
12. Pedoman capstone atau tugas akhir dari program studi Anda. Dokumen ini yang paling menentukan format dan penilaian.

---

## Penutup

Capstone Project bukan hanya tentang menghasilkan aplikasi. Ia melatih cara berpikir seorang insinyur perangkat lunak: memahami masalah sebelum membuat solusi, bekerja sama dalam tim, mengambil keputusan dengan alasan yang jelas, menguji dengan disiplin, menjaga keamanan dan privasi pengguna, serta menyampaikan hasil dengan jujur.

Tiga pesan terakhir untuk Anda:

1. **Mulailah kecil dan selesaikan.** Produk kecil yang bekerja dan teruji lebih berharga daripada rencana besar yang tidak terwujud.
2. **Libatkan pengguna dan pembimbing sejak awal.** Umpan balik dini adalah hal termurah yang bisa Anda dapatkan.
3. **Dokumentasikan perjalanan Anda.** Setiap keputusan, kesalahan, dan perbaikan adalah bahan belajar sekaligus bahan laporan.

Semoga sukses dengan proyek Anda.