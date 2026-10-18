# Model Keamanan Komputasi Terdistribusi

**Buku Ajar Teknik Informatika untuk Pemula** Edisi Oktober 2026 (untuk tahun ajaran 2026/2027 dan seterusnya)

---

## Catatan tentang Kemutakhiran Buku

Dunia keamanan komputer bergerak cepat. Standar, versi protokol, dan tenggat waktu regulasi dapat berubah. Buku ini disusun berdasarkan pengetahuan hingga pertengahan 2026. Setiap kali Anda menemukan angka, tanggal, atau nama standar yang bersifat sementara (misalnya jadwal migrasi kriptografi pasca-kuantum atau masa berlaku sertifikat), buku ini akan memberi tanda **[verifikasi]**. Artinya, Anda perlu memeriksanya kembali ke sumber resmi (NIST, IETF, CA/Browser Forum, atau regulator) sebelum menjadikannya dasar keputusan.

---

## Daftar Isi

- Kata Pengantar dan Cara Menggunakan Buku
- Bab 1. Pengantar Sistem Terdistribusi dan Mengapa Keamanannya Sulit
- Bab 2. Konsep Dasar Keamanan Informasi
- Bab 3. Model Sistem, Model Kegagalan, dan Model Ancaman
- Bab 4. Dasar-Dasar Kriptografi untuk Sistem Terdistribusi
- Bab 5. Komunikasi Aman: TLS, mTLS, dan Serangan Ulang
- Bab 6. Identitas dan Autentikasi
- Bab 7. Otorisasi dan Model Kontrol Akses
- Bab 8. Model Kepercayaan dan Arsitektur Zero Trust
- Bab 9. Konsensus, Toleransi Kesalahan Bizantium, dan Blockchain
- Bab 10. Keamanan Data: Enkripsi, Manajemen Kunci, dan Komputasi Rahasia
- Bab 11. Keamanan Layanan Mikro, Kontainer, dan Rantai Pasok Perangkat Lunak
- Bab 12. Keamanan Komputasi Awan
- Bab 13. Pemantauan, Respons Insiden, dan Ketahanan
- Bab 14. Privasi dan Kepatuhan Hukum
- Bab 15. Tren 2026, 2027, dan Seterusnya
- Bab 16. Studi Kasus dan Proyek Akhir
- Lampiran A. Glosarium
- Lampiran B. Rencana Belajar 14 Minggu
- Lampiran C. Daftar Pustaka

---

## Kata Pengantar dan Cara Menggunakan Buku

### Untuk siapa buku ini

Buku ini ditulis untuk mahasiswa atau pembelajar mandiri yang baru pertama kali mempelajari keamanan pada sistem terdistribusi. Anda tidak perlu sudah mahir dalam kriptografi atau jaringan. Setiap istilah teknis akan dijelaskan saat pertama kali muncul, disertai padanan bahasa Inggrisnya dalam tanda kurung karena literatur dan dokumentasi di dunia kerja umumnya memakai istilah bahasa Inggris.

### Prasyarat

Anda sebaiknya sudah mengenal hal-hal berikut. Jika belum, tidak masalah, cukup pelajari secara paralel.

1. Dasar pemrograman (variabel, fungsi, percabangan, perulangan). Contoh kode di buku ini memakai Python.
2. Dasar jaringan komputer: alamat IP, port, TCP, HTTP.
3. Dasar sistem operasi: proses, berkas, dan pengguna (user).
4. Dasar penggunaan terminal Linux.

### Pola setiap bab

Setiap bab memiliki pola yang sama:

1. **Tujuan pembelajaran**: apa yang akan Anda kuasai.
2. **Penjelasan konsep**: dari analogi sederhana menuju penjelasan teknis.
3. **Contoh dan praktik**: kode atau perintah yang bisa dicoba.
4. **Ringkasan**: poin penting untuk diingat.
5. **Latihan**: pertanyaan untuk menguji pemahaman.

### Peringatan etika dan hukum

Seluruh praktik di buku ini harus dilakukan hanya pada sistem milik Anda sendiri atau lingkungan laboratorium yang diizinkan. Mencoba teknik serangan pada sistem orang lain tanpa izin tertulis adalah pelanggaran hukum, di Indonesia antara lain diatur dalam UU ITE. Pemahaman tentang serangan di buku ini bertujuan untuk membangun pertahanan, bukan untuk menyerang.

### Tujuan akhir

Setelah menyelesaikan buku ini, Anda diharapkan mampu:

1. Menjelaskan apa itu model keamanan dan mengapa sistem terdistribusi membutuhkan model yang berbeda dari sistem tunggal.
2. Menyusun model ancaman (threat model) untuk sebuah sistem terdistribusi sederhana.
3. Memilih mekanisme autentikasi, otorisasi, dan enkripsi yang tepat.
4. Menjelaskan cara sistem tetap benar walaupun sebagian komponennya rusak atau berbohong (toleransi kesalahan Bizantium).
5. Merancang arsitektur dasar yang menerapkan prinsip Zero Trust.
6. Mengenali tren yang akan memengaruhi pekerjaan Anda pada 2026, 2027, dan tahun-tahun berikutnya, termasuk migrasi ke kriptografi pasca-kuantum.

---

# Bab 1. Pengantar Sistem Terdistribusi dan Mengapa Keamanannya Sulit

## Tujuan pembelajaran

Setelah mempelajari bab ini, Anda mampu:

- Mendefinisikan sistem terdistribusi dan memberi contohnya.
- Menjelaskan karakteristik sistem terdistribusi yang membuat keamanannya lebih sulit.
- Membedakan keamanan sistem tunggal dan sistem terdistribusi.

## 1.1 Apa itu sistem terdistribusi

**Sistem terdistribusi (distributed system)** adalah kumpulan komputer independen yang bekerja sama melalui jaringan sehingga tampak bagi pengguna sebagai satu sistem yang koheren.

Contoh dalam kehidupan sehari-hari:

- Aplikasi dompet digital dan perbankan seluler. Satu transaksi melibatkan puluhan layanan: autentikasi, saldo, antifraud, notifikasi, dan pencatatan.
- Mesin pencari dan platform video. Data dan komputasi tersebar di ribuan server di banyak pusat data.
- Platform e-commerce saat promo besar. Katalog, keranjang, pembayaran, dan logistik berjalan sebagai layanan terpisah.
- Jaringan blockchain. Ribuan node yang tidak saling percaya menyepakati satu catatan transaksi.
- Klaster Kubernetes yang menjalankan aplikasi Anda.

## 1.2 Karakteristik yang memengaruhi keamanan

Ada beberapa sifat dasar sistem terdistribusi. Masing-masing membuka celah keamanan baru.

|Karakteristik|Penjelasan|Dampak pada keamanan|
|---|---|---|
|Komunikasi lewat jaringan|Komponen berbicara lewat pesan, bukan memori bersama|Pesan bisa disadap, diubah, diulang, atau dihapus oleh pihak ketiga|
|Tidak ada jam global|Setiap komputer punya jam sendiri yang bisa melenceng|Sulit menentukan urutan kejadian; token berbasis waktu bisa disalahgunakan|
|Kegagalan parsial|Sebagian komponen bisa gagal sementara yang lain tetap hidup|Sulit membedakan komponen yang lambat, mati, atau berbohong|
|Banyak titik masuk|Setiap layanan punya antarmuka (API)|Permukaan serangan (attack surface) membesar|
|Banyak domain administrasi|Komponen dikelola tim atau organisasi berbeda|Kebijakan keamanan tidak seragam|
|Skala besar dan dinamis|Komponen sering ditambah, dihapus, dipindah|Daftar komponen yang sah terus berubah|
|Heterogenitas|Beragam perangkat lunak, bahasa, dan sistem operasi|Banyak kemungkinan kerentanan dan konfigurasi salah|

## 1.3 Analogi: dari rumah menjadi kompleks perumahan

Bayangkan keamanan sistem tunggal seperti mengamankan satu rumah. Anda memasang kunci pada pintu depan dan selesai. Sistem terdistribusi seperti mengamankan sebuah kompleks dengan ratusan rumah, jalan, kurir, dan tamu. Anda harus menjawab pertanyaan baru:

- Bagaimana memastikan tamu yang datang benar-benar orang yang ia klaim (autentikasi)?
- Apa yang boleh dilakukan tamu itu di dalam kompleks (otorisasi)?
- Bagaimana memastikan surat yang dikirim antarrumah tidak dibuka atau dipalsukan di jalan (kerahasiaan dan integritas)?
- Bagaimana jika satu rumah dibobol, apakah pelaku bisa masuk ke semua rumah lain (isolasi dan batas kepercayaan)?
- Bagaimana jika satpam sendiri tidak jujur (kegagalan Bizantium)?

## 1.4 Dua pandangan lama dan baru

**Pandangan lama (model benteng dan parit, castle-and-moat):** semua yang berada di dalam jaringan internal dianggap tepercaya, sedangkan yang di luar dianggap berbahaya. Pengamanan difokuskan pada tembok luar seperti firewall.

**Pandangan modern:** jaringan internal pun tidak otomatis aman. Penyerang yang berhasil masuk lewat satu akun atau satu server bisa bergerak ke samping (lateral movement). Karena itu pengamanan harus ada di setiap komponen dan setiap komunikasi. Pendekatan ini dibahas di Bab 8 sebagai Zero Trust.

## 1.5 Apa itu model keamanan

**Model keamanan (security model)** adalah deskripsi terstruktur tentang:

1. **Apa yang dilindungi** (aset).
2. **Dari siapa** dan **dengan kemampuan apa** (model ancaman).
3. **Properti apa yang dijamin** (misalnya kerahasiaan, integritas).
4. **Dengan mekanisme apa** jaminan itu dipenuhi (kriptografi, kontrol akses, isolasi).
5. **Dengan asumsi apa** jaminan itu berlaku (misalnya "paling banyak satu dari empat node bisa dibajak").

Poin nomor 5 sangat penting. Tidak ada sistem yang aman tanpa asumsi. Model yang baik menyebutkan asumsinya secara eksplisit sehingga orang lain bisa memeriksanya.

## Ringkasan Bab 1

- Sistem terdistribusi bekerja lewat jaringan, tanpa jam global, dan dengan kegagalan parsial.
- Sifat-sifat itu memperluas permukaan serangan dan memperumit penalaran keamanan.
- Model keamanan menyatakan aset, ancaman, properti, mekanisme, dan asumsi.

## Latihan Bab 1

1. Sebutkan tiga contoh sistem terdistribusi yang Anda gunakan hari ini.
2. Mengapa tidak adanya jam global menyulitkan keamanan? Berikan satu contoh.
3. Jelaskan perbedaan pandangan "benteng dan parit" dengan pandangan modern.
4. Mengapa model keamanan harus menyebutkan asumsi secara eksplisit?

---

# Bab 2. Konsep Dasar Keamanan Informasi

## Tujuan pembelajaran

- Menjelaskan triad CIA dan properti keamanan tambahan.
- Membedakan identifikasi, autentikasi, otorisasi, dan akuntabilitas.
- Membedakan aset, ancaman, kerentanan, risiko, dan kontrol.
- Menerapkan prinsip desain keamanan yang klasik.

## 2.1 Triad CIA

Tiga properti utama keamanan informasi:

1. **Kerahasiaan (Confidentiality):** informasi hanya bisa dibaca oleh pihak yang berhak. Contoh pelanggaran: data kartu kredit pelanggan bocor.
2. **Integritas (Integrity):** informasi tidak diubah tanpa izin dan perubahan bisa terdeteksi. Contoh pelanggaran: penyerang mengubah nominal transfer dari 100 ribu menjadi 10 juta.
3. **Ketersediaan (Availability):** sistem dan data dapat diakses saat dibutuhkan. Contoh pelanggaran: serangan DDoS membuat layanan tidak bisa dibuka.

## 2.2 Properti tambahan yang penting pada sistem terdistribusi

- **Autentisitas (Authenticity):** pesan benar-benar berasal dari pengirim yang diklaim.
- **Nir-penyangkalan (Non-repudiation):** pengirim tidak bisa menyangkal telah mengirim pesan. Biasanya dicapai dengan tanda tangan digital.
- **Kesegaran (Freshness):** pesan bukan salinan lama yang dikirim ulang. Terkait serangan replay.
- **Akuntabilitas (Accountability):** tindakan dapat ditelusuri ke pelaku melalui catatan audit.
- **Privasi (Privacy):** data pribadi hanya dipakai sesuai tujuan yang sah. Dibahas di Bab 14.
- **Ketahanan (Resilience):** sistem tetap berfungsi, minimal sebagian, ketika diserang atau rusak.

## 2.3 Empat langkah akses: Identifikasi, Autentikasi, Otorisasi, Akuntabilitas

Sering disingkat AAA (Authentication, Authorization, Accounting) ditambah identifikasi.

|Langkah|Pertanyaan|Contoh|
|---|---|---|
|Identifikasi|Siapa Anda mengaku?|Memasukkan nama pengguna|
|Autentikasi|Buktikan klaim itu|Memasukkan kata sandi dan kode OTP|
|Otorisasi|Apa yang boleh Anda lakukan?|Boleh membaca laporan, tidak boleh menghapusnya|
|Akuntabilitas|Apa yang sudah Anda lakukan?|Log mencatat siapa mengakses apa dan kapan|

Kesalahan umum pemula adalah mencampuradukkan autentikasi dan otorisasi. Berhasil login (autentikasi) tidak berarti boleh melakukan semua hal (otorisasi).

## 2.4 Istilah risiko

- **Aset (asset):** sesuatu yang bernilai dan perlu dilindungi, misalnya basis data pelanggan, kunci enkripsi, atau reputasi.
- **Ancaman (threat):** hal yang berpotensi menimbulkan kerugian, misalnya penyerang eksternal atau pegawai yang tidak jujur.
- **Kerentanan (vulnerability):** kelemahan yang bisa dimanfaatkan, misalnya pustaka perangkat lunak yang belum ditambal.
- **Eksploitasi (exploit):** cara memanfaatkan kerentanan.
- **Risiko (risk):** kombinasi kemungkinan dan dampak. Secara kasar: risiko = kemungkinan x dampak.
- **Kontrol (control):** tindakan untuk mengurangi risiko, bisa bersifat pencegahan, pendeteksian, atau pemulihan.

## 2.5 Prinsip desain keamanan

Prinsip berikut berasal dari tulisan klasik Saltzer dan Schroeder (1975) dan tetap berlaku.

1. **Hak istimewa terkecil (least privilege):** beri setiap pengguna dan layanan hanya hak yang benar-benar dibutuhkan.
2. **Pertahanan berlapis (defense in depth):** jangan bergantung pada satu lapisan perlindungan.
3. **Gagal aman (fail-safe defaults):** jika terjadi kesalahan, sistem harus menolak akses, bukan membukanya.
4. **Mediasi lengkap (complete mediation):** setiap akses harus diperiksa, tidak boleh ada jalan pintas.
5. **Desain terbuka (open design):** keamanan tidak boleh bergantung pada kerahasiaan algoritma, hanya pada kerahasiaan kunci.
6. **Pemisahan tugas (separation of duties):** tindakan sensitif membutuhkan lebih dari satu pihak.
7. **Mekanisme ekonomis (economy of mechanism):** semakin sederhana, semakin mudah diaudit.
8. **Penerimaan psikologis (psychological acceptability):** kontrol yang terlalu menyulitkan akan dilewati pengguna.

## Ringkasan Bab 2

- CIA adalah dasar, tetapi sistem terdistribusi juga membutuhkan autentisitas, kesegaran, dan akuntabilitas.
- Autentikasi menjawab "siapa", otorisasi menjawab "boleh apa".
- Prinsip hak istimewa terkecil dan pertahanan berlapis adalah fondasi hampir semua desain yang baik.

## Latihan Bab 2

1. Pada kasus transfer bank yang nominalnya diubah di tengah jalan, properti apa yang dilanggar?
2. Mengapa tanda tangan digital memberi nir-penyangkalan sedangkan HMAC tidak? (Petunjuk: lihat siapa yang memegang kunci. Dibahas di Bab 4.)
3. Berikan contoh pelanggaran prinsip "gagal aman" pada sebuah layanan API.
4. Jelaskan perbedaan ancaman, kerentanan, dan risiko dengan contoh Anda sendiri.

---

# Bab 3. Model Sistem, Model Kegagalan, dan Model Ancaman

## Tujuan pembelajaran

- Membedakan model sistem sinkron, asinkron, dan sinkron parsial.
- Membedakan jenis kegagalan, dari crash hingga Bizantium.
- Memahami model penyerang, termasuk model Dolev-Yao.
- Menyusun model ancaman sederhana dengan STRIDE.

## 3.1 Model sistem: asumsi tentang waktu

Untuk bernalar tentang keamanan dan kebenaran, kita perlu mengasumsikan perilaku jaringan dan waktu.

- **Model sinkron:** ada batas atas yang diketahui untuk waktu pengiriman pesan dan kecepatan proses. Mudah dianalisis, tetapi jarang realistis di internet.
- **Model asinkron:** tidak ada batas waktu sama sekali. Pesan bisa tertunda sembarang lama. Sangat realistis, tetapi sangat sulit; misalnya hasil FLP (Fischer, Lynch, Paterson, 1985) menunjukkan konsensus deterministik tidak mungkin dijamin jika satu proses saja bisa crash.
- **Model sinkron parsial (partially synchronous):** sistem kadang tidak punya batas waktu, tetapi akhirnya (setelah suatu titik) berperilaku sinkron. Ini model yang dipakai kebanyakan protokol konsensus praktis seperti Raft dan PBFT.

Mengapa ini penting untuk keamanan? Karena penyerang dapat memperlambat jaringan dengan sengaja sehingga sulit membedakan komponen yang mati dari komponen yang hanya diperlambat.

## 3.2 Model kegagalan

Dari yang paling jinak hingga paling berbahaya:

|Jenis kegagalan|Perilaku|Contoh|
|---|---|---|
|Crash (fail-stop)|Komponen berhenti dan tidak melakukan apa pun lagi|Server mati karena listrik padam|
|Omission|Komponen gagal mengirim atau menerima sebagian pesan|Paket hilang, antrean penuh|
|Timing|Respons datang terlalu lambat atau terlalu cepat|Server kelebihan beban|
|Bizantium (Byzantine)|Komponen berperilaku sembarang, termasuk berbohong dan berkolusi|Server dibajak penyerang, perangkat lunak berbug, operator curang|

Kegagalan **Bizantium** adalah jembatan antara toleransi kesalahan (fault tolerance) dan keamanan. Server yang dibajak adalah contoh nyata komponen Bizantium. Nama ini berasal dari makalah Lamport, Shostak, dan Pease (1982) tentang "Masalah Jenderal Bizantium": beberapa jenderal harus menyepakati satu rencana serangan padahal sebagian jenderal bisa pengkhianat yang mengirim pesan berbeda ke jenderal berbeda.

## 3.3 Model penyerang

### Berdasarkan posisi

- **Penyerang eksternal:** tidak punya akses awal ke sistem.
- **Insider:** punya akses sah, misalnya pegawai atau kontraktor, lalu menyalahgunakannya.
- **Komponen terkompromi:** layanan atau perangkat yang awalnya sah, kemudian dikuasai penyerang.

### Berdasarkan perilaku

- **Pasif:** hanya menyadap lalu lintas (eavesdropping).
- **Aktif:** menyadap, mengubah, menyisipkan, menghapus, atau memutar ulang pesan.

### Berdasarkan kemampuan komputasi

- **Terbatas secara komputasi (computationally bounded):** tidak mampu memecahkan kriptografi dalam waktu wajar. Sebagian besar kriptografi praktis mengasumsikan ini.
- **Tak terbatas:** punya daya hitung tak hingga. Hanya skema tertentu seperti one-time pad dan secret sharing yang aman terhadapnya (information-theoretic security).
- **Penyerang kuantum:** punya komputer kuantum skala besar. Ini dasar kebutuhan kriptografi pasca-kuantum (Bab 4 dan 15).

## 3.4 Model Dolev-Yao

Model Dolev-Yao (1983) adalah model penyerang klasik dalam analisis protokol keamanan. Asumsinya:

1. Kriptografi dianggap sempurna. Penyerang tidak bisa memecahkan enkripsi atau memalsukan tanda tangan tanpa kunci.
2. Penyerang menguasai jaringan sepenuhnya. Ia dapat membaca, memblokir, mengubah, menyisipkan, dan memutar ulang pesan apa pun.
3. Penyerang dapat berpartisipasi sebagai peserta protokol yang sah (misalnya mendaftar sebagai pengguna).

Dengan model ini kita dapat bertanya: meskipun penyerang menguasai jaringan, apakah protokol tetap menjamin properti yang diinginkan? Jika tidak, protokol cacat secara logika, bukan karena kriptografinya lemah. Alat verifikasi formal seperti Tamarin dan ProVerif memakai model ini untuk memeriksa protokol seperti TLS 1.3.

## 3.5 Ancaman klasik pada jaringan terdistribusi

- **Penyadapan (eavesdropping):** membaca lalu lintas.
- **Man-in-the-middle (MITM):** penyerang berada di tengah dan meneruskan serta mengubah pesan.
- **Replay:** merekam pesan sah lalu mengirim ulang. Contoh: mengulang pesan "transfer 1 juta".
- **Spoofing:** memalsukan identitas atau alamat.
- **Penolakan layanan (DoS/DDoS):** membanjiri sistem agar tidak tersedia.
- **Sybil attack:** satu pelaku membuat banyak identitas palsu untuk menguasai suara dalam sistem terbuka seperti jaringan peer-to-peer.
- **Eclipse attack:** mengisolasi satu node dari jaringan sebenarnya sehingga hanya menerima informasi dari penyerang.
- **Serangan pergerakan lateral:** setelah satu node jatuh, penyerang berpindah ke node lain.
- **Serangan rantai pasok:** menyusupkan kode berbahaya lewat pustaka atau pembaruan sah.

## 3.6 Menyusun model ancaman dengan STRIDE

STRIDE adalah kerangka dari Microsoft untuk mengelompokkan ancaman. Setiap huruf mewakili satu jenis ancaman dan satu properti yang dilanggar.

|Huruf|Ancaman|Properti yang dilanggar|Contoh|Kontrol umum|
|---|---|---|---|---|
|S|Spoofing (pemalsuan identitas)|Autentisitas|Layanan palsu menyamar sebagai layanan pembayaran|Autentikasi, mTLS, tanda tangan|
|T|Tampering (pengubahan data)|Integritas|Mengubah isi pesan di antrean|MAC, tanda tangan, hash|
|R|Repudiation (penyangkalan)|Nir-penyangkalan|Pengguna menyangkal melakukan transaksi|Log audit, tanda tangan digital|
|I|Information disclosure (kebocoran)|Kerahasiaan|Data bocor lewat log yang berisi kata sandi|Enkripsi, kontrol akses|
|D|Denial of service|Ketersediaan|Banjir permintaan ke API|Rate limiting, redundansi, CDN|
|E|Elevation of privilege|Otorisasi|Pengguna biasa memperoleh hak admin|Least privilege, validasi input|

### Langkah praktis

1. **Gambar diagram arus data (data flow diagram).** Tunjukkan komponen, penyimpanan data, dan arus data.
2. **Tandai batas kepercayaan (trust boundary).** Batas ini adalah garis tempat tingkat kepercayaan berubah, misalnya antara internet dan jaringan internal, atau antara layanan milik tim A dan tim B.
3. **Terapkan STRIDE** pada setiap elemen dan setiap arus yang melewati batas kepercayaan.
4. **Nilai risiko** dan prioritaskan.
5. **Tentukan kontrol**, lalu catat ancaman yang diterima (risiko residu).

### Contoh diagram sederhana

```
  [Pengguna] --HTTPS--> [API Gateway] --mTLS--> [Layanan Pesanan] --> [Basis Data]
      |                       |                         |
  (Internet)          ====== Batas kepercayaan ======   |
                                              Layanan Pembayaran (tim lain)
```

Pada diagram ini, panah yang melewati batas kepercayaan (Internet ke Gateway, Layanan Pesanan ke Layanan Pembayaran) harus dianalisis paling teliti.

## Ringkasan Bab 3

- Asumsi tentang waktu (sinkron, asinkron, sinkron parsial) memengaruhi apa yang mungkin dijamin.
- Kegagalan Bizantium adalah model terburuk dan paling relevan untuk keamanan.
- Model Dolev-Yao mengasumsikan penyerang menguasai jaringan tetapi tidak memecahkan kriptografi.
- STRIDE membantu menyusun model ancaman secara sistematis.

## Latihan Bab 3

1. Jelaskan perbedaan kegagalan crash dan kegagalan Bizantium dengan contoh.
2. Mengapa model sinkron parsial dianggap kompromi yang masuk akal?
3. Gambarlah diagram arus data untuk aplikasi pemesanan makanan dan tandai batas kepercayaannya.
4. Terapkan STRIDE pada satu arus data dari soal nomor 3.

---

# Bab 4. Dasar-Dasar Kriptografi untuk Sistem Terdistribusi

## Tujuan pembelajaran

- Menjelaskan fungsi hash, MAC, enkripsi simetris, enkripsi asimetris, dan tanda tangan digital.
- Memilih primitif kriptografi yang tepat untuk kebutuhan tertentu.
- Memahami PKI dan sertifikat.
- Memahami ancaman kuantum dan kriptografi pasca-kuantum.

## 4.0 Aturan emas

> Jangan pernah merancang algoritma kriptografi sendiri. Gunakan pustaka yang terkenal dan teruji (misalnya libsodium, pustaka kriptografi bawaan bahasa pemrograman, atau OpenSSL), dengan parameter yang direkomendasikan.

Kesalahan penggunaan (misalnya salah memakai mode atau mengulang nonce) jauh lebih sering menyebabkan pembobolan dibandingkan kelemahan algoritmanya.

## 4.1 Fungsi hash

**Fungsi hash kriptografis** memetakan data berukuran sembarang menjadi keluaran berukuran tetap (disebut digest atau sidik jari). Contoh: SHA-256, SHA-3.

Sifat yang diharapkan:

1. **Deterministik:** masukan sama menghasilkan keluaran sama.
2. **Efek longsor (avalanche):** perubahan 1 bit pada masukan mengubah keluaran secara drastis.
3. **Tahan pra-citra (preimage resistance):** dari hash tidak bisa ditemukan masukannya.
4. **Tahan tabrakan (collision resistance):** sulit menemukan dua masukan berbeda yang menghasilkan hash sama.

Kegunaan: memeriksa integritas berkas, mengidentifikasi data (content addressing), membangun pohon Merkle dan blockchain, dan menjadi komponen tanda tangan digital.

Catatan: MD5 dan SHA-1 sudah dianggap tidak aman untuk tujuan yang memerlukan tahan tabrakan. Jangan dipakai pada desain baru.

## 4.2 MAC dan HMAC

Hash biasa tidak membuktikan siapa pengirimnya, karena siapa pun bisa menghitung hash. **Message Authentication Code (MAC)** adalah hash yang melibatkan kunci rahasia bersama. Hanya pihak yang memegang kunci yang dapat membuat MAC yang valid. **HMAC** adalah konstruksi standar (RFC 2104) yang membangun MAC dari fungsi hash.

MAC menjamin **integritas** dan **autentisitas** (pesan berasal dari pemegang kunci), tetapi **tidak** menjamin nir-penyangkalan, karena kedua pihak yang memegang kunci sama-sama bisa membuat MAC.

### Contoh kode: HMAC dengan Python

```python
import hmac
import hashlib
import secrets

kunci = secrets.token_bytes(32)          # kunci rahasia bersama, 256 bit
pesan = b"transfer:rekening=123;nominal=100000"

# Pengirim menghitung tag
tag = hmac.new(kunci, pesan, hashlib.sha256).digest()

# Penerima memverifikasi dengan perbandingan waktu-konstan
tag_hitung = hmac.new(kunci, pesan, hashlib.sha256).digest()
if hmac.compare_digest(tag, tag_hitung):
    print("Pesan asli dan utuh")
else:
    print("Pesan ditolak")
```

Perhatikan pemakaian `hmac.compare_digest`. Perbandingan biasa (`==`) dapat membocorkan informasi lewat perbedaan waktu eksekusi (timing attack).

## 4.3 Enkripsi simetris

Pada **enkripsi simetris**, satu kunci yang sama dipakai untuk mengenkripsi dan mendekripsi. Cepat dan efisien untuk data besar.

Standar yang dipakai saat ini:

- **AES** (kunci 128 atau 256 bit), umumnya dalam mode **GCM**.
- **ChaCha20-Poly1305**, populer di perangkat tanpa akselerasi perangkat keras AES.

Keduanya adalah **AEAD (Authenticated Encryption with Associated Data)**: sekaligus menjamin kerahasiaan dan integritas. Gunakan AEAD, jangan enkripsi tanpa autentikasi.

Peringatan penting tentang **nonce**: pada AES-GCM, nonce (bilangan yang dipakai sekali) tidak boleh diulang untuk kunci yang sama. Pengulangan nonce dapat membocorkan kunci autentikasi dan memungkinkan pemalsuan. Pada sistem terdistribusi, ini sering terjadi karena beberapa server memakai kunci yang sama tanpa koordinasi pembuatan nonce. Solusinya: nonce acak yang cukup panjang dengan batas jumlah pesan per kunci, atau skema nonce yang dikoordinasikan, atau mode yang tahan penyalahgunaan nonce (misalnya AES-GCM-SIV).

Masalah utama enkripsi simetris adalah **distribusi kunci**: bagaimana dua pihak yang belum pernah bertemu bisa menyepakati kunci rahasia lewat jaringan yang tidak aman? Jawabannya adalah kriptografi asimetris.

## 4.4 Kriptografi asimetris (kunci publik)

Setiap pihak memiliki sepasang kunci:

- **Kunci publik**: boleh disebarkan ke siapa saja.
- **Kunci privat**: dirahasiakan oleh pemiliknya.

Ada dua penggunaan utama:

1. **Pertukaran kunci (key exchange / key encapsulation):** dua pihak menyepakati kunci rahasia bersama lewat saluran terbuka. Contoh: **ECDH** dengan kurva **X25519**. Hasilnya dipakai sebagai kunci simetris.
2. **Tanda tangan digital:** pemilik kunci privat menandatangani pesan; siapa pun dengan kunci publik dapat memverifikasi. Contoh: **Ed25519**, **ECDSA**, **RSA-PSS**.

### Tanda tangan digital vs MAC

|Aspek|MAC / HMAC|Tanda tangan digital|
|---|---|---|
|Kunci|Satu kunci rahasia bersama|Pasangan kunci privat dan publik|
|Siapa bisa membuat|Semua pemegang kunci|Hanya pemilik kunci privat|
|Siapa bisa memverifikasi|Semua pemegang kunci|Siapa pun dengan kunci publik|
|Nir-penyangkalan|Tidak|Ya|
|Kecepatan|Sangat cepat|Lebih lambat|

### Enkripsi hibrida

Kriptografi asimetris lambat. Praktik umum adalah **enkripsi hibrida**: gunakan kriptografi asimetris untuk menyepakati kunci sesi, lalu gunakan enkripsi simetris (AEAD) untuk data. Inilah cara kerja TLS.

## 4.5 Fungsi turunan kunci dan penyimpanan kata sandi

- **KDF (Key Derivation Function)** seperti **HKDF** mengubah satu rahasia menjadi beberapa kunci yang independen (misalnya kunci enkripsi dan kunci MAC terpisah).
- **Hash kata sandi** harus memakai fungsi yang sengaja lambat dan boros memori: **Argon2id** (pilihan modern), scrypt, atau bcrypt. Jangan menyimpan kata sandi dengan SHA-256 polos. Selalu tambahkan **salt** unik per pengguna.

## 4.6 PKI dan sertifikat

Masalah: jika Anda menerima kunci publik, bagaimana yakin bahwa itu memang milik pihak yang dituju, bukan milik penyerang? Jawabannya adalah **Public Key Infrastructure (PKI)**.

- **Sertifikat digital (X.509):** dokumen yang mengikat identitas (misalnya nama domain) dengan kunci publik, ditandatangani oleh pihak tepercaya.
- **Certificate Authority (CA):** pihak yang menerbitkan dan menandatangani sertifikat.
- **Root CA:** CA puncak yang sertifikatnya sudah tertanam di sistem operasi atau peramban sebagai "jangkar kepercayaan" (trust anchor).
- **Intermediate CA:** CA perantara. Root CA jarang dipakai langsung agar kunci privatnya aman.
- **Rantai sertifikat (certificate chain):** sertifikat server, ditandatangani intermediate CA, ditandatangani root CA.

```
  Root CA (trust anchor, offline)
        |
        v  menandatangani
  Intermediate CA
        |
        v  menandatangani
  Sertifikat server (nama: api.contoh.id, kunci publik server)
```

### Pencabutan dan masa berlaku

Jika kunci privat bocor, sertifikat harus dicabut. Mekanisme pencabutan (CRL dan OCSP) memiliki keterbatasan dalam praktik. Karena itu tren industri adalah **sertifikat berumur pendek** dan otomatisasi penerbitan (misalnya protokol ACME). Kebocoran kunci menjadi kurang berbahaya jika sertifikat toh kedaluwarsa dalam hitungan hari atau minggu.

Catatan kemutakhiran **[verifikasi]**: CA/Browser Forum telah menyetujui pengurangan bertahap masa berlaku maksimum sertifikat TLS publik, dengan jadwal yang mencapai sekitar 200 hari pada Maret 2026, sekitar 100 hari pada Maret 2027, dan sekitar 47 hari pada Maret 2029. Konsekuensinya, otomatisasi pembaruan sertifikat bukan lagi pilihan, melainkan keharusan operasional.

### Model kepercayaan alternatif

- **PKI hierarkis** (di atas): terpusat, dipakai di web.
- **Web of trust**: pengguna saling menandatangani kunci (contoh: PGP).
- **Trust on first use (TOFU)**: kunci diterima saat pertama kali bertemu lalu diingat (contoh: SSH).
- **Transparansi sertifikat (Certificate Transparency):** semua sertifikat publik dicatat pada log publik yang hanya bisa ditambah, sehingga penerbitan sertifikat palsu terdeteksi.

## 4.7 Ancaman kuantum dan kriptografi pasca-kuantum

**Komputer kuantum** yang cukup besar dapat menjalankan algoritma Shor untuk memecahkan RSA dan kriptografi kurva eliptik (ECC) dengan efisien. Akibatnya, pertukaran kunci dan tanda tangan yang ada hari ini akan rapuh. Untuk kriptografi simetris dan hash, dampaknya lebih ringan (algoritma Grover memberi percepatan kuadratik), sehingga cukup menaikkan ukuran, misalnya memakai AES-256.

Ancaman yang sudah berlaku sekarang adalah **harvest now, decrypt later**: penyerang merekam lalu lintas terenkripsi hari ini untuk didekripsi nanti ketika komputer kuantum tersedia. Data yang harus tetap rahasia selama puluhan tahun (data kesehatan, rahasia negara, arsip hukum) sudah berisiko.

**Kriptografi pasca-kuantum (Post-Quantum Cryptography, PQC)** adalah algoritma yang dirancang tahan terhadap komputer kuantum, namun tetap berjalan di komputer biasa. NIST menerbitkan standar pertamanya pada Agustus 2024:

|Standar|Nama algoritma|Fungsi|
|---|---|---|
|FIPS 203|ML-KEM (berbasis CRYSTALS-Kyber)|Pertukaran kunci (KEM)|
|FIPS 204|ML-DSA (berbasis CRYSTALS-Dilithium)|Tanda tangan digital|
|FIPS 205|SLH-DSA (berbasis SPHINCS+)|Tanda tangan berbasis hash (cadangan)|

NIST juga telah memilih algoritma tambahan (misalnya HQC untuk KEM cadangan) dan menyiapkan standar tanda tangan berbasis Falcon **[verifikasi status terbaru]**.

Praktik migrasi yang umum disarankan adalah **mode hibrida**: menggabungkan algoritma klasik (misalnya X25519) dengan algoritma pasca-kuantum (misalnya ML-KEM) sehingga keamanan tetap terjaga selama salah satu algoritma masih kuat. Implementasi hibrida X25519 dengan ML-KEM sudah tersedia pada banyak peramban dan pustaka TLS.

Rencana penghentian algoritma lama oleh NIST (draf dokumen NIST IR 8547 menyebut target pelemahan RSA dan ECC sekitar 2030 dan pelarangan sekitar 2035) perlu dicek ulang pada sumber resmi **[verifikasi]**. Intinya bagi praktisi: mulai dari sekarang buatlah **inventaris kriptografi** (di mana sistem Anda memakai RSA, ECC, dan sertifikat) dan rancang **crypto agility**, yaitu kemampuan mengganti algoritma tanpa membongkar seluruh sistem.

## Ringkasan Bab 4

- Hash untuk sidik jari data, HMAC untuk integritas dan autentisitas dengan kunci bersama, AEAD untuk kerahasiaan dan integritas, tanda tangan digital untuk autentisitas dan nir-penyangkalan.
- Enkripsi hibrida menggabungkan kriptografi asimetris (kesepakatan kunci) dan simetris (data).
- PKI mengikat identitas ke kunci publik lewat sertifikat; sertifikat berumur pendek dan otomatisasi adalah arah industri.
- Ancaman kuantum nyata; mulailah dengan inventaris kriptografi dan mode hibrida.

## Latihan Bab 4

1. Mengapa menyimpan kata sandi dengan SHA-256 polos adalah praktik buruk?
2. Apa yang terjadi jika nonce AES-GCM dipakai dua kali dengan kunci yang sama?
3. Jelaskan mengapa HMAC tidak memberi nir-penyangkalan.
4. Apa arti "harvest now, decrypt later" dan mengapa relevan sebelum komputer kuantum besar ada?
5. Modifikasi kode HMAC di atas agar pesan yang diubah satu karakter ditolak. Tunjukkan hasilnya.

---

# Bab 5. Komunikasi Aman: TLS, mTLS, dan Serangan Ulang

## Tujuan pembelajaran

- Menjelaskan cara kerja TLS 1.3 secara garis besar.
- Membedakan TLS dan mTLS.
- Memahami serangan replay dan cara menangkalnya.
- Mempraktikkan pembuatan CA mini untuk eksperimen mTLS.

## 5.1 Apa yang dijamin oleh TLS

**Transport Layer Security (TLS)** adalah protokol yang mengamankan komunikasi di atas TCP. HTTPS adalah HTTP di atas TLS. TLS memberikan:

1. **Kerahasiaan:** data dienkripsi sehingga penyadap tidak bisa membacanya.
2. **Integritas:** perubahan data terdeteksi.
3. **Autentikasi server:** klien yakin ia berbicara dengan server yang benar (lewat sertifikat).
4. **Autentikasi klien (opsional):** pada mTLS, server juga memverifikasi klien.

Versi yang direkomendasikan adalah **TLS 1.3** (RFC 8446). Versi lama (SSL, TLS 1.0, TLS 1.1) sudah usang dan tidak boleh dipakai. TLS 1.2 masih banyak dipakai tetapi harus dikonfigurasi dengan hati-hati.

## 5.2 Alur TLS 1.3 yang disederhanakan

```
  Klien                                           Server
    |                                               |
    |--- ClientHello (versi, daftar sandi, -------->|
    |     bagian kunci publik ECDH)                 |
    |                                               |
    |<-- ServerHello (pilihan sandi, bagian --------|
    |     kunci publik ECDH server)                 |
    |                                               |
    |   [Mulai di sini semua pesan dienkripsi]      |
    |<-- Sertifikat server ------------------------ |
    |<-- CertificateVerify (tanda tangan) ----------|
    |<-- Finished (bukti seluruh percakapan) -------|
    |                                               |
    |--- Finished --------------------------------->|
    |                                               |
    |=========== Data aplikasi terenkripsi =========|
```

Penjelasan langkah penting:

1. **ClientHello:** klien menyebut kemampuan dan langsung mengirim bagian pertukaran kunci ECDH sementara (ephemeral).
2. **ServerHello:** server memilih parameter dan mengirim bagian ECDH miliknya. Kedua pihak kini bisa menghitung rahasia bersama dan menurunkan kunci sesi.
3. **Sertifikat dan CertificateVerify:** server membuktikan identitasnya dengan sertifikat, dan menandatangani transkrip percakapan dengan kunci privatnya sehingga klien yakin pihak di seberang memegang kunci privat itu.
4. **Finished:** kedua pihak saling membuktikan bahwa mereka melihat percakapan yang sama sehingga tidak ada pengubahan di tengah jalan.

### Forward secrecy

Karena memakai kunci ECDH **sementara** (ephemeral) untuk setiap sesi, kebocoran kunci privat server di masa depan tidak membuka sesi lama. Sifat ini disebut **forward secrecy** (kerahasiaan ke depan). Pada TLS 1.3 sifat ini selalu ada.

### 0-RTT dan risikonya

TLS 1.3 menyediakan mode **0-RTT** (early data) untuk melanjutkan sesi dengan lebih cepat. Data 0-RTT **rentan terhadap serangan replay**. Karena itu 0-RTT hanya aman untuk operasi yang idempoten (misalnya membaca data), dan jangan dipakai untuk operasi yang mengubah keadaan seperti pembayaran.

## 5.3 mTLS (mutual TLS)

Pada TLS biasa, hanya server yang membuktikan identitasnya. Pada **mTLS**, klien juga menyerahkan sertifikat sehingga server dapat memverifikasi klien. mTLS populer untuk komunikasi antarlayanan (service-to-service) di dalam sistem terdistribusi, karena setiap layanan punya identitas kriptografis yang dapat diverifikasi, bukan sekadar alamat IP.

Manfaat mTLS:

- Layanan dapat menolak koneksi dari pihak yang tidak punya sertifikat sah.
- Identitas (misalnya nama layanan di sertifikat) dapat dipakai dalam keputusan otorisasi.
- Lalu lintas internal terenkripsi.

Tantangan operasionalnya: menerbitkan, mendistribusikan, dan merotasi sertifikat untuk ratusan atau ribuan layanan. Di sinilah service mesh dan SPIFFE/SPIRE berperan (Bab 11).

## 5.4 Serangan replay dan penangkalnya

**Replay attack**: penyerang merekam pesan sah, lalu mengirim ulang. Meskipun pesan terenkripsi dan terautentikasi, pengulangan bisa menimbulkan efek ganda.

Penangkal umum:

1. **Nonce:** bilangan acak sekali pakai yang disertakan dalam pesan; penerima menolak nonce yang sudah pernah dilihat.
2. **Nomor urut (sequence number):** pesan dengan nomor lama ditolak.
3. **Stempel waktu (timestamp) dan jendela waktu:** pesan yang terlalu lama ditolak. Memerlukan sinkronisasi jam yang wajar.
4. **Idempotency key:** pada API, klien mengirim kunci unik per operasi sehingga operasi yang sama tidak diproses dua kali.
5. **Tantangan-respons (challenge-response):** server mengirim tantangan acak yang harus dijawab klien, sehingga jawaban lama tidak berguna.

## 5.5 Alternatif dan pelengkap TLS

- **SSH:** akses shell dan transfer berkas aman; memakai TOFU atau sertifikat SSH.
- **IPsec dan WireGuard:** terowongan VPN di lapisan jaringan.
- **QUIC dan HTTP/3:** memakai TLS 1.3 di dalam protokol transportnya.
- **Enkripsi ujung ke ujung (end-to-end encryption):** data dienkripsi oleh pengirim dan hanya didekripsi oleh penerima akhir, bahkan perantara (server) tidak bisa membacanya. Contoh: aplikasi pesan dengan protokol Signal.

## 5.6 Praktik: CA mini dan mTLS dengan OpenSSL

**Hanya untuk laboratorium.** Kita membuat CA sendiri, sertifikat server, dan sertifikat klien.

```bash
# 1. Buat CA (root) untuk laboratorium
openssl ecparam -name prime256v1 -genkey -noout -out ca.key
openssl req -x509 -new -key ca.key -sha256 -days 365 \
  -subj "/CN=Lab Root CA" -out ca.crt

# 2. Buat sertifikat server (dengan SAN, wajib pada klien modern)
openssl ecparam -name prime256v1 -genkey -noout -out server.key
openssl req -new -key server.key -subj "/CN=server.lab.local" -out server.csr
printf "subjectAltName=DNS:server.lab.local\n" > san.cnf
openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -CAcreateserial \
  -days 90 -sha256 -extfile san.cnf -out server.crt

# 3. Buat sertifikat klien
openssl ecparam -name prime256v1 -genkey -noout -out client.key
openssl req -new -key client.key -subj "/CN=klien-pesanan" -out client.csr
openssl x509 -req -in client.csr -CA ca.crt -CAkey ca.key -CAcreateserial \
  -days 90 -sha256 -out client.crt

# 4. Jalankan server yang mewajibkan sertifikat klien (terminal 1)
openssl s_server -accept 8443 -tls1_3 \
  -cert server.crt -key server.key -CAfile ca.crt -Verify 1

# 5. Sambungkan klien (terminal 2)
openssl s_client -connect localhost:8443 -tls1_3 \
  -CAfile ca.crt -cert client.crt -key client.key \
  -verify_hostname server.lab.local
```

Eksperimen yang disarankan:

1. Sambungkan klien **tanpa** `-cert` dan `-key`. Amati bahwa server menolak koneksi.
2. Buat CA kedua, terbitkan sertifikat klien dari CA itu, lalu coba sambungkan. Amati penolakan karena CA tidak dikenal server.
3. Ubah `-verify_hostname` menjadi nama lain dan amati kegagalan verifikasi nama.

## Ringkasan Bab 5

- TLS 1.3 memberi kerahasiaan, integritas, dan autentikasi server, dengan forward secrecy.
- mTLS menambahkan autentikasi klien dan cocok untuk komunikasi antarlayanan.
- Replay ditangkal dengan nonce, nomor urut, jendela waktu, idempotency key, atau challenge-response.
- Hati-hati dengan 0-RTT untuk operasi yang mengubah keadaan.

## Latihan Bab 5

1. Apa itu forward secrecy dan bagaimana TLS 1.3 mencapainya?
2. Mengapa mTLS lebih kuat daripada membatasi akses hanya berdasarkan alamat IP?
3. Rancang mekanisme agar permintaan "buat pembayaran" tidak diproses dua kali walaupun dikirim ulang oleh penyerang.
4. Apa akibatnya jika sertifikat klien dan CA yang menerbitkannya tidak dikelola dengan rotasi?

---

# Bab 6. Identitas dan Autentikasi

## Tujuan pembelajaran

- Memahami faktor autentikasi dan autentikasi multi-faktor.
- Menjelaskan cara kerja Kerberos secara garis besar.
- Memahami OAuth 2.0, OpenID Connect, dan JWT beserta jebakannya.
- Memahami identitas beban kerja (workload identity).

## 6.1 Identitas pada sistem terdistribusi

Di sistem terdistribusi ada dua kelompok identitas:

1. **Identitas manusia:** pegawai, pelanggan, administrator.
2. **Identitas mesin atau beban kerja (workload):** layanan, kontainer, fungsi serverless, perangkat IoT.

Pada sistem modern, jumlah identitas mesin biasanya jauh lebih banyak daripada identitas manusia, dan sering lebih lemah pengamanannya (misalnya kunci API statis yang tertanam di kode).

## 6.2 Faktor autentikasi

1. **Sesuatu yang Anda ketahui:** kata sandi, PIN.
2. **Sesuatu yang Anda miliki:** ponsel, kunci keamanan perangkat keras.
3. **Sesuatu yang Anda adalah:** sidik jari, wajah (biometrik).

**Autentikasi multi-faktor (MFA)** mengombinasikan faktor dari kategori berbeda. Dua kata sandi bukan MFA.

Tidak semua MFA setara. Kode OTP lewat SMS rentan terhadap pembajakan nomor (SIM swap) dan phishing. Pendekatan yang lebih kuat adalah **FIDO2/WebAuthn** dan **passkey**: perangkat menyimpan kunci privat dan menandatangani tantangan dari situs. Kunci terikat pada domain situs sehingga **tahan phishing**: situs palsu tidak bisa memperoleh tanda tangan yang valid untuk domain aslinya. Passkey semakin luas dipakai sehingga pada 2026 dan seterusnya layak dijadikan pilihan utama untuk pengguna manusia.

## 6.3 Kerberos

**Kerberos** adalah protokol autentikasi jaringan berbasis tiket yang banyak dipakai di lingkungan korporat (misalnya Active Directory). Gagasan utamanya: pengguna membuktikan identitas sekali ke pihak tepercaya, lalu memperoleh tiket untuk mengakses layanan tanpa mengirim kata sandi berulang kali.

Pihak yang terlibat:

- **Klien** (pengguna).
- **KDC (Key Distribution Center)**, terdiri dari **AS (Authentication Server)** dan **TGS (Ticket Granting Server)**.
- **Layanan** yang ingin diakses.

```
  Klien                      KDC (AS + TGS)                 Layanan
    |                              |                           |
    |-- 1. Permintaan TGT -------->|                           |
    |<- 2. TGT + kunci sesi -------|  (dienkripsi dgn kunci    |
    |      (terenkripsi kunci      |   turunan kata sandi)     |
    |       pengguna)              |                           |
    |-- 3. Minta tiket layanan --->|  (menyertakan TGT)        |
    |<- 4. Tiket layanan ----------|                           |
    |-- 5. Tiket layanan + autentikator ---------------------->|
    |<- 6. (opsional) bukti dari layanan ----------------------|
```

Poin penting:

- **TGT (Ticket Granting Ticket)** adalah "tiket untuk meminta tiket", berlaku terbatas waktu.
- **Autentikator** berisi stempel waktu terenkripsi untuk mencegah replay. Karena itu Kerberos **bergantung pada sinkronisasi jam**, secara umum toleransi default sekitar lima menit.
- KDC adalah **titik kepercayaan tunggal**. Jika KDC jatuh, seluruh domain terdampak. Karena itu KDC harus dijaga ketat dan direplikasi.

## 6.4 Single Sign-On, OAuth 2.0, dan OpenID Connect

Masalah yang diselesaikan: pengguna ingin login sekali lalu mengakses banyak layanan, atau memberi aplikasi pihak ketiga akses terbatas ke datanya tanpa menyerahkan kata sandi.

### Membedakan dua hal yang sering tertukar

- **OAuth 2.0** adalah kerangka **otorisasi** (delegasi akses): "izinkan aplikasi X membaca kalender saya".
- **OpenID Connect (OIDC)** adalah lapisan **autentikasi** di atas OAuth 2.0: "siapa pengguna yang baru saja login".
- **SAML** adalah standar SSO lebih tua berbasis XML yang masih umum di lingkungan perusahaan.

### Peran dalam OAuth 2.0

- **Resource owner:** pengguna pemilik data.
- **Client:** aplikasi yang meminta akses.
- **Authorization server:** pihak yang mengautentikasi pengguna dan menerbitkan token.
- **Resource server:** API yang menyimpan data dan memeriksa token.

### Alur Authorization Code dengan PKCE

Alur ini adalah yang direkomendasikan untuk aplikasi web, seluler, dan aplikasi satu halaman. **PKCE (Proof Key for Code Exchange, RFC 7636)** melindungi dari pencurian kode otorisasi.

```
  Pengguna/Aplikasi (Client)       Authorization Server        Resource Server (API)
        |                                   |                          |
 1. Buat code_verifier acak,                |                          |
    hitung code_challenge = hash(verifier)  |                          |
        |-- 2. Arahkan pengguna + challenge->|                         |
        |        (pengguna login, setuju)   |                          |
        |<- 3. kode otorisasi (authorization code) ------              |
        |-- 4. Tukar kode + code_verifier -->|                         |
        |<- 5. access token (+ refresh token, id token) --             |
        |-- 6. Panggil API dengan access token -------------------->   |
```

Server memeriksa bahwa hash dari `code_verifier` sama dengan `code_challenge` di langkah 2. Penyerang yang hanya mencuri kode di langkah 3 tidak punya `code_verifier` sehingga tidak bisa menukarnya.

Praktik yang dianjurkan:

- Hindari alur lama yang berisiko seperti _implicit flow_ dan _password grant_. Pembaruan standar (OAuth 2.1) menggabungkan praktik terbaik ini.
- Gunakan token akses berumur pendek (menit), dan refresh token yang dirotasi.
- Batasi **scope** token seminimal mungkin.

## 6.5 JSON Web Token (JWT)

**JWT** (RFC 7519) adalah format token yang berisi klaim (misalnya identitas pengguna, penerbit, waktu kedaluwarsa), biasanya ditandatangani sehingga penerima dapat memverifikasi tanpa menghubungi penerbit setiap kali.

Struktur: `header.payload.signature`, masing-masing dikodekan Base64URL.

Perlu diingat: **JWT yang ditandatangani tidak dienkripsi.** Siapa pun bisa membaca isinya. Jangan menaruh data rahasia di payload.

### Jebakan umum JWT

1. **Tidak memverifikasi tanda tangan**, atau memercayai algoritma yang tertulis di header. Serangan klasik: mengganti `alg` menjadi `none`. Selalu tetapkan daftar algoritma yang diizinkan di sisi server.
2. **Mencampur kunci:** menggunakan kunci publik RSA sebagai kunci HMAC (kebingungan algoritma).
3. **Tidak memeriksa klaim:** `exp` (kedaluwarsa), `iss` (penerbit), `aud` (audiens yang dituju), dan `nbf`.
4. **Token berumur panjang tanpa mekanisme pencabutan.** JWT sulit dicabut sebelum kedaluwarsa. Gunakan umur pendek, daftar pencabutan, atau token buram (opaque) dengan introspeksi.
5. **Menyimpan token di tempat yang rentan** (misalnya local storage yang bisa dibaca skrip XSS).

### Contoh verifikasi JWT yang benar (pseudokode Python)

```python
import jwt  # pustaka PyJWT

def verifikasi(token: str, kunci_publik: str) -> dict:
    return jwt.decode(
        token,
        kunci_publik,
        algorithms=["ES256"],          # daftar algoritma eksplisit
        audience="api.contoh.id",      # wajib cocok dengan audiens
        issuer="https://auth.contoh.id",
        options={"require": ["exp", "iss", "aud"]},
    )
```

## 6.6 Identitas beban kerja

Untuk layanan, kata sandi dan kunci API statis yang berumur panjang adalah sumber kebocoran. Pendekatan modern:

- **SPIFFE (Secure Production Identity Framework For Everyone)** mendefinisikan format identitas layanan (SPIFFE ID, misalnya `spiffe://contoh.id/layanan/pesanan`) dan dokumen identitas (SVID) berupa sertifikat X.509 atau JWT.
- **SPIRE** adalah implementasi acuan yang menerbitkan dan merotasi SVID secara otomatis setelah memverifikasi (attestation) bahwa beban kerja memang berjalan di tempat yang diharapkan.
- Penyedia awan menawarkan identitas beban kerja serupa sehingga kode tidak perlu menyimpan kunci statis.

Prinsipnya: identitas layanan harus **berumur pendek, dirotasi otomatis, dan diikat pada bukti tentang di mana dan bagaimana layanan itu berjalan**.

## Ringkasan Bab 6

- Gunakan MFA yang tahan phishing (FIDO2, passkey) untuk manusia.
- Kerberos memakai tiket dan bergantung pada jam serta KDC yang tepercaya.
- OAuth 2.0 untuk otorisasi, OIDC untuk autentikasi; gunakan Authorization Code dengan PKCE.
- JWT harus diverifikasi dengan ketat; jangan menaruh rahasia di dalamnya.
- Untuk layanan, gunakan identitas berumur pendek yang dirotasi otomatis.

## Latihan Bab 6

1. Mengapa SMS OTP dianggap kurang kuat dibandingkan passkey?
2. Apa fungsi autentikator berstempel waktu pada Kerberos dan apa konsekuensinya bagi sinkronisasi jam?
3. Jelaskan bagaimana PKCE mencegah pencurian kode otorisasi.
4. Sebutkan tiga klaim JWT yang harus selalu diperiksa dan alasannya.
5. Mengapa kunci API statis di dalam kode sumber berbahaya?

---

# Bab 7. Otorisasi dan Model Kontrol Akses

## Tujuan pembelajaran

- Membedakan model DAC, MAC, RBAC, ABAC, dan ReBAC.
- Memahami konsep Policy Decision Point dan Policy Enforcement Point.
- Mengenali masalah confused deputy dan solusi berbasis capability.
- Membaca contoh kebijakan sederhana dalam bahasa kebijakan.

## 7.1 Pertanyaan inti otorisasi

Otorisasi menjawab: apakah **subjek** (pengguna atau layanan) boleh melakukan **aksi** terhadap **objek** (sumber daya) dalam **konteks** tertentu?

## 7.2 Model kontrol akses

### DAC (Discretionary Access Control)

Pemilik sumber daya menentukan siapa yang boleh mengaksesnya. Contoh: izin berkas Linux (pemilik, grup, lainnya) dan ACL. Fleksibel, tetapi bergantung pada kehati-hatian pemilik.

### MAC (Mandatory Access Control)

Kebijakan ditetapkan secara terpusat oleh sistem dan tidak bisa diubah oleh pemilik. Contoh: tingkat klasifikasi (Rahasia, Terbatas, Umum), SELinux. Cocok untuk lingkungan dengan persyaratan ketat.

### RBAC (Role-Based Access Control)

Hak diberikan ke **peran** (role), pengguna diberi peran. Contoh: peran "kasir" boleh membuat transaksi, peran "auditor" boleh membaca laporan. Mudah dikelola dan umum dipakai (misalnya RBAC di Kubernetes). Kelemahan: dapat mengalami "ledakan peran" ketika kebutuhan sangat bervariasi.

### ABAC (Attribute-Based Access Control)

Keputusan berdasarkan **atribut** subjek, objek, aksi, dan lingkungan. Contoh: "dokter boleh membaca rekam medis pasien jika dokter itu bertugas di bangsal yang sama dan akses dilakukan pada jam dinas". Sangat ekspresif, tetapi kebijakan lebih rumit.

### ReBAC (Relationship-Based Access Control)

Keputusan berdasarkan **hubungan** antarentitas dalam graf. Contoh: "pengguna boleh mengedit dokumen jika ia anggota tim yang memiliki folder induk dokumen itu". Dipakai oleh sistem berskala besar untuk berbagi dokumen.

### Perbandingan singkat

|Model|Dasar keputusan|Kelebihan|Kekurangan|
|---|---|---|---|
|DAC|Izin yang ditentukan pemilik|Sederhana, fleksibel|Rawan salah konfigurasi|
|MAC|Label dan kebijakan pusat|Kuat, konsisten|Kaku|
|RBAC|Peran|Mudah dikelola|Ledakan peran|
|ABAC|Atribut dan konteks|Halus dan fleksibel|Kebijakan kompleks|
|ReBAC|Hubungan dalam graf|Cocok untuk berbagi|Perlu penyimpanan graf yang konsisten|

## 7.3 Arsitektur kebijakan: PEP, PDP, PAP, PIP

Pada sistem terdistribusi, otorisasi sebaiknya dipisah dari kode bisnis.

- **PEP (Policy Enforcement Point):** titik yang menegakkan keputusan, misalnya API gateway atau proxy sidecar.
- **PDP (Policy Decision Point):** komponen yang mengevaluasi kebijakan dan menjawab izinkan atau tolak.
- **PAP (Policy Administration Point):** tempat kebijakan ditulis dan dikelola.
- **PIP (Policy Information Point):** sumber atribut tambahan (misalnya direktori pengguna).

```
  Permintaan --> [PEP] --tanya--> [PDP] <--atribut-- [PIP]
                   |                ^
                   | izin/tolak     |
                   v                +---- kebijakan dari [PAP]
              [Layanan]
```

Keuntungan pemisahan: kebijakan konsisten di seluruh layanan, dapat diaudit, dan dapat diubah tanpa membangun ulang aplikasi. **Open Policy Agent (OPA)** dengan bahasa kebijakan **Rego** adalah contoh populer.

### Contoh kebijakan Rego sederhana

```rego
package pesanan.authz

default allow := false

# Pengguna boleh membaca pesanan miliknya sendiri
allow if {
    input.aksi == "baca"
    input.pengguna.id == input.pesanan.pemilik_id
}

# Petugas dukungan boleh membaca semua pesanan pada jam kerja
allow if {
    input.aksi == "baca"
    "dukungan" in input.pengguna.peran
    input.konteks.jam >= 8
    input.konteks.jam < 17
}
```

Perhatikan `default allow := false`. Ini penerapan prinsip **gagal aman**: jika tidak ada aturan yang mengizinkan, hasilnya adalah tolak.

## 7.4 Masalah confused deputy dan capability

**Confused deputy problem:** layanan A (yang punya hak besar) dapat diperdaya oleh pihak yang berhak kecil untuk melakukan tindakan atas namanya. Contoh: layanan pemrosesan berkas yang bisa menulis ke seluruh penyimpanan diminta pengguna biasa untuk menyimpan hasil ke jalur yang seharusnya tidak boleh ia sentuh.

Solusi umum:

- **Meneruskan identitas dan hak pemanggil asli** (misalnya token turunan dengan cakupan terbatas), sehingga layanan bertindak dengan hak pemanggil, bukan haknya sendiri.
- **Model capability:** hak diwakili oleh **token yang tidak dapat dipalsukan** (capability) yang mengikat sumber daya dan aksi tertentu. Siapa yang memegang token itu boleh melakukan aksi tersebut, dan token dapat dibatasi atau diteruskan dengan hak yang lebih sempit. Contoh: URL bertanda tangan sementara untuk mengunduh satu berkas, dan **macaroon** yang dapat diperkecil haknya oleh pemegangnya.

## 7.5 Otorisasi pada skala terdistribusi

Beberapa tantangan khas:

1. **Konsistensi:** jika pencabutan hak butuh waktu untuk merambat ke semua replika, ada jendela waktu saat pengguna yang sudah dicabut masih bisa mengakses. Tentukan batas yang dapat diterima (misalnya token berumur pendek).
2. **Latensi:** memanggil PDP terpusat pada setiap permintaan menambah latensi dan menjadi titik kegagalan. Solusi: sebarkan PDP sebagai pustaka atau sidecar lokal dengan kebijakan yang disinkronkan.
3. **Propagasi identitas:** pada rantai panggilan A ke B ke C, siapa subjek yang dipakai di C? Putuskan dan dokumentasikan.
4. **Audit:** catat setiap keputusan otorisasi penting beserta alasannya.

## Ringkasan Bab 7

- Otorisasi menjawab apakah subjek boleh melakukan aksi pada objek dalam konteks tertentu.
- RBAC mudah, ABAC fleksibel, ReBAC cocok untuk relasi; pilih sesuai kebutuhan.
- Pisahkan penegakan (PEP) dari keputusan (PDP) agar kebijakan konsisten.
- Waspadai confused deputy; capability membantu menyempitkan hak.

## Latihan Bab 7

1. Pilih model kontrol akses yang cocok untuk (a) sistem berbagi dokumen, (b) sistem rekam medis rumah sakit, (c) klaster Kubernetes. Jelaskan alasannya.
2. Apa arti `default allow := false` pada contoh kebijakan di atas?
3. Berikan contoh confused deputy pada sistem yang Anda kenal.
4. Mengapa pencabutan hak pada sistem terdistribusi tidak selalu instan?
5. Tambahkan aturan Rego yang mengizinkan peran "auditor" membaca semua pesanan tetapi tidak boleh mengubahnya.

---

# Bab 8. Model Kepercayaan dan Arsitektur Zero Trust

## Tujuan pembelajaran

- Menjelaskan konsep kepercayaan (trust) dan batas kepercayaan.
- Menjelaskan prinsip Zero Trust dan komponen arsitekturnya.
- Menerapkan segmentasi dan mikrosegmentasi.

## 8.1 Apa itu kepercayaan dalam keamanan

Dalam keamanan, **mempercayai** sebuah komponen berarti sistem bergantung pada komponen itu untuk berperilaku benar. Jika komponen yang dipercaya ternyata berbahaya atau rusak, jaminan keamanan runtuh. Karena itu praktik yang baik adalah **meminimalkan basis komputasi tepercaya (Trusted Computing Base, TCB)**: semakin sedikit hal yang harus dipercaya, semakin kecil peluang kegagalan.

Contoh hal yang dipercaya dalam sebuah sistem: sistem operasi, hipervisor, root CA, penyedia awan, administrator basis data, pustaka pihak ketiga.

## 8.2 Dari model perimeter ke Zero Trust

Model perimeter menganggap jaringan internal aman. Kelemahannya nyata:

- Pekerjaan jarak jauh, awan, dan SaaS membuat perimeter kabur.
- Penyerang yang menembus satu titik dapat bergerak leluasa.
- Ancaman dari dalam (insider) tidak dibendung oleh firewall luar.

**Zero Trust** adalah pendekatan yang berasumsi bahwa jaringan sudah atau akan dikompromikan. Slogannya: **"jangan pernah percaya, selalu verifikasi" (never trust, always verify)**. NIST SP 800-207 merumuskan arsitekturnya.

## 8.3 Prinsip Zero Trust

1. **Verifikasi eksplisit:** setiap permintaan diautentikasi dan diotorisasi berdasarkan semua data yang tersedia (identitas, perangkat, lokasi, perilaku).
2. **Hak istimewa terkecil:** akses secukupnya dan sesingkat mungkin (just-in-time, just-enough-access).
3. **Asumsikan pelanggaran (assume breach):** rancang agar dampak kompromi satu komponen terbatas, dan siapkan deteksi.
4. **Tidak ada kepercayaan berdasarkan lokasi jaringan:** alamat IP internal bukan bukti identitas.
5. **Keputusan akses dinamis:** per sesi atau per permintaan, bukan sekali di awal untuk selamanya.

## 8.4 Komponen arsitektur Zero Trust

Merujuk pada NIST SP 800-207:

- **Policy Engine** dan **Policy Administrator** (digabung sebagai Policy Decision Point): memutuskan apakah akses diberikan, memakai masukan dari sumber seperti inventaris perangkat, intelijen ancaman, dan log.
- **Policy Enforcement Point:** membuka atau menutup jalur komunikasi sesuai keputusan.
- Sumber data pendukung: manajemen identitas, kondisi keamanan perangkat, log aktivitas, kebijakan data.

```
  Subjek (pengguna + perangkat)
        |
        v
  [Policy Enforcement Point] <---- keputusan ---- [Policy Decision Point]
        |                                              ^
        v                                              | masukan: identitas,
  [Sumber daya / Layanan]                              | postur perangkat, log,
                                                       | intelijen ancaman
```

## 8.5 Segmentasi dan mikrosegmentasi

- **Segmentasi jaringan:** memecah jaringan menjadi zona (misalnya web, aplikasi, basis data) dengan aturan antarzona.
- **Mikrosegmentasi:** isolasi pada tingkat beban kerja individual. Setiap layanan hanya boleh berbicara dengan layanan yang memang perlu. Pada Kubernetes diwujudkan antara lain dengan NetworkPolicy dan mTLS (Bab 11).

Tujuannya: jika satu layanan dibobol, penyerang tidak otomatis dapat menjangkau layanan lain.

## 8.6 Zero Trust bukan produk

Zero Trust adalah strategi dan arsitektur, bukan satu produk yang bisa dibeli. Penerapannya bertahap:

1. Inventarisasi aset, identitas, dan arus data.
2. Perkuat identitas (MFA tahan phishing, identitas layanan).
3. Terapkan akses hak terkecil dan segmentasi.
4. Aktifkan pemantauan dan deteksi menyeluruh.
5. Otomatisasi respons dan perbaiki terus-menerus.

## Ringkasan Bab 8

- Kurangi hal yang harus dipercaya (TCB).
- Zero Trust: verifikasi eksplisit, hak terkecil, asumsikan pelanggaran.
- Keputusan akses dinamis, dipisah antara PDP dan PEP.
- Mikrosegmentasi membatasi dampak kompromi.

## Latihan Bab 8

1. Mengapa alamat IP internal tidak boleh dijadikan satu-satunya dasar kepercayaan?
2. Jelaskan perbedaan segmentasi dan mikrosegmentasi.
3. Sebutkan lima hal yang dipercaya oleh aplikasi web sederhana yang berjalan di awan.
4. Mengapa dikatakan Zero Trust bukan produk?

---

# Bab 9. Konsensus, Toleransi Kesalahan Bizantium, dan Blockchain

## Tujuan pembelajaran

- Menjelaskan masalah konsensus dan mengapa ia sulit.
- Membedakan toleransi crash dan toleransi Bizantium.
- Menjelaskan mengapa BFT membutuhkan paling sedikit 3f+1 replika.
- Memahami garis besar PBFT, Raft, dan konsensus blockchain.
- Memahami struktur data tahan-ubah: rantai hash dan pohon Merkle.

## 9.1 Mengapa konsensus penting untuk keamanan

Banyak sistem terdistribusi perlu beberapa komputer menyepakati satu nilai atau satu urutan operasi, misalnya urutan transaksi pada basis data atau siapa pemimpin saat ini. Jika sebagian komputer rusak atau berbohong, kesepakatan harus tetap benar. Inilah masalah **konsensus**.

Sebuah protokol konsensus yang benar menjamin:

1. **Kesepakatan (agreement):** semua node yang jujur memutuskan nilai yang sama.
2. **Validitas (validity):** nilai yang diputuskan pernah diusulkan oleh node yang sah.
3. **Terminasi (termination/liveness):** akhirnya keputusan tercapai.

Properti pertama dan kedua adalah **safety** (tidak ada hal buruk terjadi); yang ketiga adalah **liveness** (hal baik akhirnya terjadi).

## 9.2 Batas teoretis penting

- **FLP impossibility (1985):** pada sistem asinkron murni, tidak ada protokol deterministik yang menjamin konsensus jika satu proses saja bisa crash. Dalam praktik, protokol memakai asumsi sinkron parsial, pengacakan, atau penghitung waktu (timeout) untuk keluar dari batas ini.
- **Teorema CAP:** pada saat jaringan terpartisi (P), sistem harus memilih antara konsistensi (C) dan ketersediaan (A). Pilihan ini berdampak pada keamanan: misalnya apakah saat partisi sistem tetap menerima transaksi (risiko saldo ganda) atau menolaknya (risiko layanan tidak tersedia).

## 9.3 Konsensus toleran crash: Raft

**Raft** (Ongaro dan Ousterhout, 2014) dan **Paxos** menoleransi kegagalan crash. Mereka bekerja bila **mayoritas** node hidup dan jujur.

- Dengan **n** node, Raft menoleransi **f** crash selama **n >= 2f + 1**. Contoh: 5 node menoleransi 2 crash.
- Raft memilih satu **pemimpin (leader)** yang mengurutkan operasi dan mereplikasi log ke pengikut (follower). Operasi dianggap tetap (committed) setelah disimpan oleh mayoritas.

Raft **tidak** melindungi dari node yang berbohong. Jika pemimpin dibajak, ia bisa mengirim data berbeda ke pengikut berbeda. Untuk lingkungan yang semua node dikelola satu organisasi dan dianggap jujur tetapi bisa mati, Raft cukup dan lebih sederhana serta cepat.

## 9.4 Konsensus toleran Bizantium (BFT)

BFT diperlukan jika sebagian node mungkin berperilaku sembarang, misalnya antarorganisasi yang tidak saling percaya, atau lingkungan berisiko tinggi.

### Batas 3f + 1

Untuk menoleransi **f** node Bizantium, dibutuhkan **n >= 3f + 1** node.

**Intuisi dengan contoh:** misalkan f = 1 dan kita hanya punya n = 3 node (A, B, C), dengan C jahat. Jenderal pengirim (A) mengirim "serang". C memberi tahu B bahwa A mengirim "mundur". B menerima "serang" dari A dan "mundur" dari C, dan tidak bisa menentukan siapa yang berbohong. B tidak dapat memutuskan dengan aman. Dengan n = 4, node jujur (3 dari 4) selalu menjadi mayoritas yang cukup besar untuk mengalahkan satu pembohong sehingga keputusan benar masih dapat ditarik.

Ringkasan batas:

|Jenis kegagalan|Jumlah node minimal untuk f kegagalan|Contoh protokol|
|---|---|---|
|Crash|2f + 1|Raft, Paxos|
|Bizantium|3f + 1|PBFT, Tendermint, HotStuff dan turunannya|

### Garis besar PBFT

**PBFT (Practical Byzantine Fault Tolerance, Castro dan Liskov, 1999)** menunjukkan bahwa BFT bisa praktis. Operasi berlangsung dalam tiga fase utama dengan pemimpin (primary):

1. **Pre-prepare:** primary memberi nomor urut pada permintaan klien dan mengirim ke semua replika.
2. **Prepare:** replika menyiarkan bahwa mereka menerima usulan; setelah menerima cukup banyak pesan yang cocok (kuorum 2f + 1), replika menjadi "prepared".
3. **Commit:** replika menyiarkan komitmen; setelah kuorum 2f + 1, operasi dieksekusi dan dijawab ke klien. Klien menunggu **f + 1** jawaban yang sama.

Jika primary mencurigakan atau lambat, replika menjalankan **view change** untuk memilih primary baru. Semua pesan ditandatangani atau diautentikasi (MAC) sehingga pembohong sulit memalsukan pesan jujur.

Kekurangan BFT klasik: jumlah pesan besar (kompleksitas komunikasi tinggi) sehingga sulit diskalakan ke ribuan node. Protokol lebih baru seperti HotStuff mengurangi biaya komunikasi.

## 9.5 Blockchain dan konsensus pada lingkungan terbuka

Pada jaringan **terbuka** (siapa pun boleh bergabung), ada risiko **Sybil attack**: penyerang membuat banyak identitas palsu. Konsensus klasik berbasis hitung suara per identitas tidak cukup. Blockchain mengikat hak suara pada sumber daya yang mahal dipalsukan:

- **Proof of Work (PoW):** hak menambah blok diperoleh dengan menyelesaikan teka-teki komputasi. Penyerang butuh mayoritas daya hitung (serangan 51%) untuk menulis ulang sejarah.
- **Proof of Stake (PoS):** hak menambah blok bergantung pada jumlah aset yang dikunci sebagai jaminan (stake). Perilaku curang dapat dihukum dengan memotong jaminan (slashing).

Pada jaringan **berizin (permissioned)**, peserta teridentifikasi dan lebih sedikit. Di sini protokol BFT dapat dipakai, misalnya pada beberapa platform blockchain korporat.

Perbedaan model keamanan: blockchain terbuka memberikan jaminan **probabilistik** (semakin banyak blok di atas transaksi, semakin sulit dibalik), sedangkan BFT klasik memberikan **finalitas** (setelah di-commit, tidak dibalik) selama asumsi f terpenuhi.

## 9.6 Struktur data tahan-ubah

### Rantai hash

Setiap blok memuat hash blok sebelumnya. Mengubah satu blok lama mengubah hash-nya dan membuat semua blok sesudahnya tidak cocok, sehingga perubahan terdeteksi.

```python
import hashlib, json

def hash_blok(blok: dict) -> str:
    isi = json.dumps(blok, sort_keys=True).encode()
    return hashlib.sha256(isi).hexdigest()

rantai = []
hash_sebelumnya = "0" * 64
for data in ["A kirim 10 ke B", "B kirim 5 ke C", "C kirim 2 ke A"]:
    blok = {"data": data, "hash_sebelumnya": hash_sebelumnya}
    blok["hash"] = hash_blok({"data": blok["data"],
                              "hash_sebelumnya": blok["hash_sebelumnya"]})
    rantai.append(blok)
    hash_sebelumnya = blok["hash"]

def valid(rantai) -> bool:
    prev = "0" * 64
    for b in rantai:
        h = hash_blok({"data": b["data"], "hash_sebelumnya": b["hash_sebelumnya"]})
        if b["hash_sebelumnya"] != prev or b["hash"] != h:
            return False
        prev = b["hash"]
    return True

print(valid(rantai))                 # True
rantai[0]["data"] = "A kirim 1000 ke B"
print(valid(rantai))                 # False, perubahan terdeteksi
```

Rantai hash saja menjamin **deteksi pengubahan**, bukan pencegahan. Pencegahan datang dari konsensus dan replikasi di banyak pihak.

### Pohon Merkle

**Pohon Merkle** menyusun hash secara hierarkis: daun adalah hash data, setiap simpul induk adalah hash gabungan dua anaknya, dan puncaknya (root) mewakili seluruh kumpulan data. Manfaat: membuktikan bahwa satu data ada dalam kumpulan hanya dengan sejumlah hash yang jumlahnya logaritmik terhadap ukuran data (proof of inclusion). Dipakai pada blockchain, sistem berkas terdistribusi, dan **Certificate Transparency**.

## 9.7 Kapan memakai apa

|Situasi|Pilihan wajar|
|---|---|
|Semua node milik satu organisasi, risiko utama mati listrik atau jaringan|Raft atau Paxos|
|Beberapa organisasi yang tidak saling percaya, peserta terdaftar|BFT (PBFT, HotStuff, dan sejenisnya)|
|Jaringan terbuka tanpa izin|Blockchain PoW atau PoS|
|Hanya butuh bukti tidak diubah (audit)|Rantai hash atau log transparansi dengan pohon Merkle|

Pertimbangkan juga apakah Anda benar-benar membutuhkan konsensus. Basis data terkelola dengan replikasi sering menyelesaikan masalah dengan lebih sederhana.

## Ringkasan Bab 9

- Konsensus menjamin safety dan liveness; FLP dan CAP mengingatkan keterbatasan.
- Raft: n >= 2f + 1 untuk crash. BFT: n >= 3f + 1 untuk Bizantium.
- Blockchain menyelesaikan masalah Sybil dengan PoW atau PoS pada jaringan terbuka.
- Rantai hash dan pohon Merkle memungkinkan deteksi pengubahan dan bukti inklusi.

## Latihan Bab 9

1. Berapa node minimal agar sistem menoleransi 2 node Bizantium? Berapa untuk 2 node crash?
2. Mengapa Raft tidak aman jika pemimpin dibajak?
3. Jelaskan Sybil attack dan bagaimana PoW membatasinya.
4. Jalankan kode rantai hash, ubah data blok kedua, dan jelaskan mengapa `valid` bernilai False.
5. Mengapa pohon Merkle efisien untuk membuktikan bahwa sebuah sertifikat tercatat dalam log?

---

# Bab 10. Keamanan Data: Enkripsi, Manajemen Kunci, dan Komputasi Rahasia

## Tujuan pembelajaran

- Membedakan data saat diam (at rest), saat bergerak (in transit), dan saat dipakai (in use).
- Menjelaskan enkripsi amplop (envelope encryption) dan peran KMS dan HSM.
- Menjelaskan berbagi rahasia Shamir.
- Menjelaskan konsep komputasi rahasia dan attestation jarak jauh.

## 10.1 Tiga keadaan data

|Keadaan|Contoh|Perlindungan umum|
|---|---|---|
|Saat diam (at rest)|Basis data, disk, cadangan|Enkripsi disk dan basis data, enkripsi tingkat aplikasi|
|Saat bergerak (in transit)|Lalu lintas antarlayanan|TLS, mTLS, VPN|
|Saat dipakai (in use)|Data di memori saat diproses|Komputasi rahasia (TEE), enkripsi homomorfik, MPC|

Celah klasik: data aman saat diam dan saat bergerak, tetapi terbuka di memori saat diproses. Bagian akhir bab ini membahas bagaimana menutupnya.

## 10.2 Manajemen kunci

Kekuatan enkripsi sepenuhnya bergantung pada keamanan kunci. Siklus hidup kunci mencakup pembuatan, distribusi, penyimpanan, penggunaan, rotasi, pencabutan, dan penghancuran.

Aturan praktis:

1. Buat kunci dengan generator acak yang aman secara kriptografis.
2. **Jangan menyimpan kunci di kode sumber, repositori, atau berkas konfigurasi biasa.**
3. Simpan di **KMS (Key Management Service)**, **HSM (Hardware Security Module)**, atau pengelola rahasia (secret manager).
4. **Rotasi** kunci secara berkala dan saat dicurigai bocor.
5. Pisahkan kunci berdasarkan fungsi dan tenant.
6. Batasi dan audit setiap penggunaan kunci.

### Enkripsi amplop (envelope encryption)

Mengenkripsi semua data besar langsung dengan kunci utama yang disimpan di HSM tidak efisien. Solusinya memakai dua tingkat kunci:

- **DEK (Data Encryption Key):** kunci yang mengenkripsi data, dibuat per objek atau per berkas.
- **KEK (Key Encryption Key):** kunci utama di KMS atau HSM yang mengenkripsi (membungkus) DEK.

```
  Data  --[enkripsi dengan DEK]--> Data terenkripsi
  DEK   --[dibungkus dengan KEK di KMS]--> DEK terbungkus
  Simpan: Data terenkripsi + DEK terbungkus
  KEK tidak pernah meninggalkan KMS/HSM
```

Manfaat: rotasi KEK cukup membungkus ulang DEK (kecil), tidak perlu mengenkripsi ulang seluruh data; dan akses ke KEK dapat diaudit di satu tempat.

### HSM

**HSM** adalah perangkat keras tahan-ubah yang membuat, menyimpan, dan memakai kunci tanpa pernah membocorkan kunci mentahnya. Operasi kriptografi dikirim ke HSM, hasilnya yang dikembalikan. Dipakai untuk kunci root CA, kunci penandatanganan, dan kunci penting lain.

## 10.3 Berbagi rahasia Shamir (Shamir's Secret Sharing)

Bagaimana melindungi kunci yang sangat penting agar tidak ada satu orang pun yang bisa menyalahgunakannya, dan tetap aman jika sebagian orang kehilangan bagiannya? Jawabannya: **skema ambang (t, n)**.

Rahasia dipecah menjadi **n** bagian (share). Gabungan **t** atau lebih bagian dapat merekonstruksi rahasia, sedangkan **t - 1** bagian atau kurang tidak memberi informasi apa pun tentang rahasia itu (keamanan teoretis informasi).

Intuisi: dua titik menentukan satu garis lurus, tiga titik menentukan satu parabola. Rahasia dijadikan titik potong pada sumbu tertentu dari suatu polinomial berderajat t - 1; setiap bagian adalah satu titik pada kurva itu. Dengan t titik, polinomial dapat direkonstruksi (interpolasi Lagrange).

### Contoh kode sederhana (hanya untuk belajar)

```python
import random

P = 2**127 - 1  # bilangan prima besar (medan hingga)

def pecah(rahasia: int, t: int, n: int):
    koef = [rahasia] + [random.randrange(P) for _ in range(t - 1)]
    def f(x):
        return sum(c * pow(x, i, P) for i, c in enumerate(koef)) % P
    return [(x, f(x)) for x in range(1, n + 1)]

def gabung(bagian):
    hasil = 0
    for i, (xi, yi) in enumerate(bagian):
        num, den = 1, 1
        for j, (xj, _) in enumerate(bagian):
            if i != j:
                num = (num * -xj) % P
                den = (den * (xi - xj)) % P
        hasil = (hasil + yi * num * pow(den, -1, P)) % P
    return hasil

rahasia = 123456789
bagian = pecah(rahasia, t=3, n=5)
print(gabung(bagian[:3]) == rahasia)   # True
print(gabung(bagian[1:4]) == rahasia)  # True
```

Catatan: kode ini edukatif. Untuk produksi, gunakan pustaka teruji dan generator acak kriptografis (`secrets`, bukan `random`). Contoh pemakaian nyata: kunci utama KMS atau "upacara kunci" (key ceremony) yang membutuhkan kehadiran beberapa pemegang bagian.

## 10.4 Melindungi data saat dipakai

### Komputasi rahasia (Confidential Computing)

Komputasi rahasia memakai **Trusted Execution Environment (TEE)**, yaitu area terisolasi yang dilindungi perangkat keras prosesor. Memori di dalam TEE dienkripsi dan tidak dapat dibaca oleh sistem operasi, hipervisor, atau administrator awan. Contoh teknologi: Intel SGX dan TDX, AMD SEV-SNP, ARM CCA. Beberapa penyedia awan menyediakan mesin virtual rahasia.

Konsep kunci: **attestation jarak jauh (remote attestation)**. Sebelum mengirim data sensitif atau kunci ke sebuah TEE, pihak lain meminta bukti kriptografis yang ditandatangani perangkat keras tentang (a) perangkat keras asli, dan (b) perangkat lunak persis apa yang berjalan (lewat pengukuran hash). Hanya jika bukti cocok dengan yang diharapkan, rahasia dilepas.

Batasan yang perlu dipahami: TEE memindahkan kepercayaan ke produsen prosesor dan implementasinya; serangan kanal samping (side-channel) dan kerentanan mikroarsitektur pernah ditemukan. Jadi TEE adalah satu lapisan pertahanan, bukan jaminan mutlak.

### Teknik lain

- **Enkripsi homomorfik (HE):** menghitung langsung pada data terenkripsi. Sangat aman secara konsep, tetapi masih mahal secara komputasi.
- **Komputasi multipihak aman (Secure Multi-Party Computation, MPC):** beberapa pihak menghitung fungsi bersama tanpa saling membuka masukan masing-masing.
- **Zero-knowledge proof (ZKP):** membuktikan suatu pernyataan benar tanpa membuka datanya, misalnya membuktikan usia di atas 18 tanpa menunjukkan tanggal lahir.

## 10.5 Cadangan, pemusnahan, dan retensi

- Terapkan kaidah cadangan **3-2-1**: tiga salinan data, pada dua jenis media berbeda, satu salinan di lokasi terpisah. Tambahkan salinan yang **tidak dapat diubah (immutable)** atau terputus (air-gapped) untuk menghadapi ransomware.
- Enkripsi cadangan dan lindungi kuncinya terpisah dari data.
- Uji pemulihan secara berkala; cadangan yang tidak pernah diuji belum tentu bisa dipakai.
- **Crypto-shredding:** menghapus kunci enkripsi sama dengan menghapus data terenkripsi secara efektif, berguna ketika menghapus data dari banyak replika sulit dilakukan.

## Ringkasan Bab 10

- Lindungi data saat diam, bergerak, dan dipakai.
- Kunci adalah titik terlemah; gunakan KMS, HSM, enkripsi amplop, rotasi, dan audit.
- Shamir memungkinkan kendali bersama atas rahasia penting.
- TEE dan attestation jarak jauh melindungi data saat diproses, dengan batasan.

## Latihan Bab 10

1. Mengapa enkripsi amplop mempermudah rotasi kunci?
2. Pada skema Shamir (3, 5), apa yang terjadi jika hanya 2 bagian yang terkumpul?
3. Apa fungsi attestation jarak jauh dalam komputasi rahasia?
4. Mengapa cadangan yang tidak pernah diuji pemulihannya berisiko?
5. Jelaskan konsep crypto-shredding dan satu situasi pemakaiannya.

---

# Bab 11. Keamanan Layanan Mikro, Kontainer, dan Rantai Pasok Perangkat Lunak

## Tujuan pembelajaran

- Mengenali permukaan serangan pada arsitektur layanan mikro.
- Menerapkan kontrol dasar pada Kubernetes.
- Memahami service mesh dan mTLS otomatis.
- Memahami keamanan rantai pasok perangkat lunak.

## 11.1 Permukaan serangan layanan mikro

Memecah aplikasi monolit menjadi layanan mikro memberi fleksibilitas, tetapi:

- Jumlah API meningkat, setiap API adalah pintu masuk.
- Komunikasi internal bertambah sehingga perlu diamankan, bukan hanya komunikasi ke internet.
- Rahasia (kredensial basis data, kunci API) tersebar di banyak tempat.
- Konfigurasi salah menjadi lebih mungkin karena banyaknya komponen.

Praktik inti:

1. **Gerbang API (API gateway)** sebagai pintu masuk tunggal untuk autentikasi, pembatasan laju (rate limiting), dan validasi dasar.
2. **Validasi masukan** di setiap layanan; jangan hanya percaya pada gateway.
3. **mTLS antarlayanan** dengan identitas layanan.
4. **Otorisasi per layanan**, bukan hanya di gerbang.
5. **Rahasia dikelola terpusat**, bukan di kode atau variabel lingkungan statis.

Referensi berguna: **OWASP API Security Top 10**, yang mencantumkan kelemahan umum seperti otorisasi tingkat objek yang rusak (BOLA), autentikasi yang lemah, dan konsumsi sumber daya tanpa batas.

## 11.2 Keamanan kontainer dan Kubernetes

**Kontainer** berbagi kernel dengan host, sehingga isolasinya lebih lemah daripada mesin virtual. Praktik dasar:

1. **Jangan jalankan sebagai root** di dalam kontainer; gunakan pengguna non-root.
2. **Sistem berkas root hanya-baca** bila memungkinkan.
3. **Cabut kapabilitas Linux** yang tidak perlu dan hindari mode `privileged`.
4. **Gunakan citra (image) minimal** dari sumber tepercaya dan pindai kerentanannya.
5. **Batasi sumber daya** (CPU dan memori) agar satu kontainer tidak menghabiskan semuanya.

Pada **Kubernetes**:

- **RBAC:** batasi siapa yang bisa melakukan apa pada API server. Hindari pemberian peran `cluster-admin` secara luas.
- **Pod Security Standards:** profil keamanan (privileged, baseline, restricted) yang ditegakkan pada namespace.
- **Secret:** secara default hanya dikodekan Base64, bukan dienkripsi. Aktifkan enkripsi at rest dan pertimbangkan integrasi dengan KMS atau pengelola rahasia eksternal.
- **NetworkPolicy:** mengatur komunikasi antarpod (mikrosegmentasi).

### Contoh: tolak semua lalu izinkan seperlunya

```yaml
# 1. Tolak semua lalu lintas masuk ke semua pod di namespace "toko"
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: tolak-semua-masuk
  namespace: toko
spec:
  podSelector: {}
  policyTypes:
    - Ingress
---
# 2. Izinkan hanya layanan "pesanan" menghubungi "pembayaran" di port 8443
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: izinkan-pesanan-ke-pembayaran
  namespace: toko
spec:
  podSelector:
    matchLabels:
      app: pembayaran
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: pesanan
      ports:
        - protocol: TCP
          port: 8443
```

Catatan: NetworkPolicy hanya berfungsi bila plugin jaringan (CNI) di klaster mendukungnya.

## 11.3 Service mesh

**Service mesh** (misalnya Istio, Linkerd, Cilium) menambahkan lapisan infrastruktur untuk komunikasi antarlayanan. Biasanya melalui proxy sampingan (sidecar) atau mekanisme tanpa sidecar. Manfaat keamanan:

- **mTLS otomatis** antarlayanan, dengan penerbitan dan rotasi sertifikat otomatis.
- **Kebijakan otorisasi** berdasarkan identitas layanan (misalnya "layanan pesanan boleh memanggil metode POST /bayar pada layanan pembayaran").
- **Telemetri:** metrik dan jejak terpusat untuk deteksi.

Kompromi: kompleksitas operasional tambahan dan sedikit beban latensi. Pertimbangkan apakah skala sistem Anda membenarkannya.

## 11.4 Keamanan rantai pasok perangkat lunak

Sebagian besar kode dalam aplikasi modern berasal dari pustaka pihak ketiga. Penyerang menargetkan rantai pasok karena satu titik kompromi dapat memengaruhi ribuan korban.

Ancaman umum:

- Dependensi berisi kerentanan (contoh: Log4Shell pada pustaka Log4j, 2021).
- Paket berbahaya dengan nama menyerupai paket populer (typosquatting).
- Kompromi sistem build atau distribusi pembaruan (contoh: insiden SolarWinds, 2020).
- Citra kontainer yang dimodifikasi.

Kontrol:

1. **SBOM (Software Bill of Materials):** daftar komponen penyusun perangkat lunak (format SPDX atau CycloneDX) sehingga ketika kerentanan baru diumumkan Anda tahu apakah terdampak.
2. **Pemindaian dependensi** dan pembaruan teratur.
3. **Penguncian versi** dan verifikasi hash dependensi.
4. **Penandatanganan artefak dan citra** (misalnya dengan Sigstore/cosign) serta verifikasi tanda tangan saat deploy.
5. **Build yang dapat direproduksi dan terisolasi**, dengan provenans (rekaman asal-usul build). Kerangka **SLSA** memberi tingkatan kematangan.
6. **Kebijakan admisi** di klaster: hanya citra bertanda tangan dari registri tepercaya yang boleh berjalan.

## Ringkasan Bab 11

- Layanan mikro memperbesar permukaan serangan; amankan gateway, antarlayanan, dan rahasia.
- Kontainer: non-root, minimal, hak terbatas; Kubernetes: RBAC, Pod Security, NetworkPolicy.
- Service mesh memberi mTLS dan otorisasi berbasis identitas secara otomatis.
- Rantai pasok: SBOM, pemindaian, tanda tangan, provenans.

## Latihan Bab 11

1. Mengapa Secret Kubernetes tidak otomatis aman?
2. Tuliskan NetworkPolicy yang mengizinkan hanya layanan "pesanan" menghubungi basis data "db-pesanan" di port 5432.
3. Apa manfaat SBOM ketika kerentanan seperti Log4Shell diumumkan?
4. Jelaskan perbedaan keamanan isolasi kontainer dan mesin virtual.

---

# Bab 12. Keamanan Komputasi Awan

## Tujuan pembelajaran

- Memahami model tanggung jawab bersama.
- Mengenali risiko khas awan: salah konfigurasi, IAM berlebih, multi-tenancy.
- Menerapkan prinsip dasar keamanan awan.

## 12.1 Model tanggung jawab bersama (Shared Responsibility Model)

Penyedia awan dan pelanggan membagi tanggung jawab keamanan. Garis pembagiannya bergantung pada model layanan.

|Lapisan|IaaS (mesin virtual)|PaaS (platform)|SaaS (aplikasi jadi)|
|---|---|---|---|
|Data dan klasifikasinya|Pelanggan|Pelanggan|Pelanggan|
|Identitas dan akses pelanggan|Pelanggan|Pelanggan|Pelanggan|
|Aplikasi|Pelanggan|Pelanggan|Penyedia|
|Sistem operasi|Pelanggan|Penyedia|Penyedia|
|Jaringan virtual dan hipervisor|Penyedia|Penyedia|Penyedia|
|Fasilitas fisik|Penyedia|Penyedia|Penyedia|

Kesalahan kronis: mengira penyedia mengamankan segalanya. Data, identitas, dan konfigurasi hampir selalu menjadi tanggung jawab pelanggan.

## 12.2 Risiko utama di awan

1. **Salah konfigurasi:** bucket penyimpanan terbuka ke publik, basis data terpapar ke internet, port administrasi terbuka. Ini penyebab terbesar kebocoran data di awan.
2. **IAM berlebihan:** peran dan kebijakan terlalu longgar (misalnya izin `*` pada semua sumber daya).
3. **Kunci akses statis berumur panjang** yang bocor di repositori kode.
4. **Multi-tenancy:** banyak pelanggan berbagi perangkat keras. Isolasi bergantung pada hipervisor dan kontrol penyedia; serangan kanal samping antartenant menjadi perhatian.
5. **Ketergantungan pada penyedia (lock-in) dan konsentrasi risiko:** gangguan besar pada satu wilayah atau penyedia berdampak luas.
6. **Visibilitas terbatas:** pelanggan hanya melihat apa yang disediakan penyedia lewat log dan API.

## 12.3 Praktik dasar yang dianjurkan

1. **Aktifkan MFA tahan phishing** pada akun root/administrator dan jangan gunakan akun root untuk pekerjaan harian.
2. **IAM hak terkecil** dan peran sementara (temporary credentials), bukan kunci statis.
3. **Pisahkan akun atau proyek** berdasarkan lingkungan (produksi, pengembangan) untuk membatasi dampak.
4. **Enkripsi secara default**, dengan kunci pelanggan (CMK) untuk data sensitif.
5. **Postur keamanan sebagai kode (infrastructure as code) dan pemindaian konfigurasi** (CSPM) untuk mendeteksi salah konfigurasi lebih awal.
6. **Aktifkan log audit** (log aktivitas API) dan kirim ke penyimpanan terpisah yang tidak bisa diubah.
7. **Desain lintas zona ketersediaan atau wilayah** untuk ketahanan.

## 12.4 Kedaulatan data dan lokasi

Data yang disimpan di awan tunduk pada hukum yurisdiksi tempat data berada dan, sering kali, hukum negara penyedia. Pertimbangkan **residensi data** (di wilayah mana data disimpan), persyaratan regulator sektor (misalnya keuangan dan kesehatan), dan opsi seperti **kunci yang dikelola pelanggan di luar penyedia (external key management)** agar penyedia tidak memegang kunci Anda. Bab 14 membahas aspek hukum di Indonesia.

## Ringkasan Bab 12

- Pahami garis tanggung jawab bersama; data dan identitas hampir selalu urusan Anda.
- Salah konfigurasi dan IAM berlebih adalah penyebab terbanyak insiden.
- Gunakan kredensial sementara, pemisahan akun, enkripsi, dan log audit.

## Latihan Bab 12

1. Pada layanan SaaS, siapa yang bertanggung jawab atas pengelolaan akun pengguna Anda?
2. Sebutkan tiga salah konfigurasi awan yang dapat menyebabkan kebocoran data.
3. Mengapa kredensial sementara lebih aman daripada kunci akses statis?
4. Mengapa log audit sebaiknya dikirim ke akun terpisah?

---

# Bab 13. Pemantauan, Respons Insiden, dan Ketahanan

## Tujuan pembelajaran

- Menjelaskan peran logging, metrik, dan jejak dalam keamanan.
- Memahami tantangan log pada sistem terdistribusi.
- Mengenali tahap-tahap respons insiden.
- Menjelaskan ketahanan terhadap DDoS dan rekayasa kekacauan.

## 13.1 Mengapa deteksi penting

Tidak ada pencegahan yang sempurna. Prinsip **asumsikan pelanggaran** berarti Anda harus mampu **mendeteksi** dan **merespons**. Dua ukuran penting: **MTTD** (Mean Time To Detect, rata-rata waktu mendeteksi) dan **MTTR** (Mean Time To Respond/Recover). Semakin cepat keduanya, semakin kecil kerugian.

## 13.2 Tiga pilar observabilitas

1. **Log:** catatan kejadian diskret (login gagal, perubahan konfigurasi).
2. **Metrik:** ukuran numerik berkala (jumlah permintaan per detik, tingkat galat).
3. **Jejak (trace):** perjalanan satu permintaan melintasi banyak layanan, dengan **ID korelasi** yang sama.

Untuk keamanan, ketiganya membantu menelusuri apa yang terjadi, mendeteksi anomali, dan merekonstruksi serangan.

## 13.3 Praktik log yang aman

1. **Kumpulkan log secara terpusat** (misalnya ke SIEM, Security Information and Event Management) sehingga penyerang yang membobol satu server tidak bisa menghapus jejaknya.
2. **Lindungi integritas log:** penyimpanan hanya-tambah (append-only), pemisahan akses, atau rantai hash/log transparansi.
3. **Sinkronkan jam** (misalnya dengan NTP yang aman atau NTS) agar urutan kejadian antarserver dapat direkonstruksi.
4. **Jangan mencatat data rahasia:** kata sandi, token, kunci, dan data pribadi sensitif tidak boleh muncul di log.
5. **Catat peristiwa penting:** autentikasi (berhasil dan gagal), keputusan otorisasi, perubahan hak, akses ke data sensitif, perubahan konfigurasi, dan penggunaan kunci.
6. **Tentukan masa retensi** sesuai kebutuhan investigasi dan regulasi.

## 13.4 Deteksi

- **Berbasis aturan:** misalnya peringatan jika ada 50 login gagal dari satu sumber dalam semenit.
- **Berbasis anomali:** mendeteksi perilaku yang menyimpang dari pola biasa (misalnya layanan yang tiba-tiba mengirim data dalam jumlah besar ke luar).
- **Honeypot dan honeytoken:** umpan yang tidak seharusnya disentuh siapa pun; setiap akses adalah sinyal serangan dengan sedikit hasil positif palsu.
- Gabungkan sumber: log aplikasi, jaringan, identitas, awan, dan titik akhir (EDR).

## 13.5 Respons insiden

Kerangka umum (selaras dengan NIST SP 800-61):

1. **Persiapan:** rencana, peran, alat, dan latihan (tabletop exercise).
2. **Deteksi dan analisis:** memastikan insiden nyata, menilai cakupan dan dampak.
3. **Penahanan, pemberantasan, dan pemulihan:** isolasi sistem terdampak, hilangkan penyebab (misalnya cabut kredensial, tambal kerentanan), pulihkan layanan dari sumber yang bersih.
4. **Pasca-insiden:** tinjauan tanpa menyalahkan (blameless postmortem), perbaiki akar masalah, perbarui kontrol dan rencana.

Pada sistem terdistribusi, isolasi cepat (memutus jaringan satu segmen, mencabut identitas layanan, merotasi kunci) sangat bergantung pada persiapan sebelumnya, misalnya otomatisasi rotasi kunci dan inventaris layanan yang akurat.

Pertimbangkan juga kewajiban pelaporan insiden ke regulator dan pihak terdampak sesuai hukum yang berlaku (lihat Bab 14).

## 13.6 Ketahanan terhadap penolakan layanan

**DDoS (Distributed Denial of Service)** memakai banyak sumber untuk membanjiri target. Contoh terkenal: botnet Mirai (2016) yang memakai perangkat IoT berkata sandi bawaan.

Pertahanan berlapis:

- **Jaringan pengiriman konten (CDN) dan layanan mitigasi DDoS** untuk menyerap lalu lintas volumetrik.
- **Rate limiting dan kuota** per klien di gerbang API.
- **Autoscaling** dengan batas biaya.
- **Desain degradasi anggun (graceful degradation):** fitur non-esensial dimatikan saat beban tinggi.
- **Pemutus sirkuit (circuit breaker)** dan **backpressure** agar kegagalan satu layanan tidak merambat.
- **Redundansi** lintas zona atau wilayah.

## 13.7 Rekayasa kekacauan dan latihan keamanan

**Chaos engineering** adalah praktik sengaja menyuntikkan kegagalan (mematikan instance, memutus jaringan) di lingkungan terkendali untuk menguji ketahanan. Versi keamanannya: **red team**, **purple team**, dan latihan simulasi insiden. Tujuannya menemukan kelemahan sebelum penyerang menemukannya.

## Ringkasan Bab 13

- Pencegahan tidak cukup; deteksi dan respons cepat sama pentingnya.
- Log terpusat, terlindungi integritasnya, dan berjam tersinkron.
- Respons insiden: persiapan, deteksi, penahanan dan pemulihan, pasca-insiden.
- Ketahanan DDoS dibangun berlapis: CDN, rate limiting, redundansi, degradasi anggun.

## Latihan Bab 13

1. Mengapa log harus dikirim ke penyimpanan terpusat?
2. Mengapa jam yang tidak sinkron menyulitkan investigasi insiden?
3. Rancang tiga aturan deteksi untuk layanan login.
4. Apa itu blameless postmortem dan mengapa bermanfaat?
5. Jelaskan perbedaan rate limiting dan circuit breaker.

---

# Bab 14. Privasi dan Kepatuhan Hukum

## Tujuan pembelajaran

- Membedakan keamanan dan privasi.
- Mengenal prinsip perlindungan data pribadi dan UU PDP di Indonesia.
- Memahami teknik privasi: pseudonimisasi, anonimisasi, differential privacy, federated learning.

## 14.1 Keamanan bukan privasi

- **Keamanan** melindungi data dari akses dan perubahan yang tidak sah.
- **Privasi** mengatur bagaimana data pribadi dikumpulkan, dipakai, dan dibagikan, termasuk oleh pihak yang sah.

Sebuah sistem bisa sangat aman tetapi melanggar privasi (misalnya menyimpan data pribadi yang tidak perlu secara aman). Sebaliknya, privasi tidak mungkin terjaga tanpa keamanan.

## 14.2 Prinsip perlindungan data

Prinsip yang umum ditemukan dalam regulasi modern (termasuk GDPR dan UU PDP):

1. **Pembatasan tujuan:** data dipakai hanya untuk tujuan yang disampaikan.
2. **Minimisasi data:** kumpulkan hanya yang diperlukan.
3. **Akurasi.**
4. **Pembatasan penyimpanan:** hapus ketika tidak lagi diperlukan.
5. **Integritas dan kerahasiaan:** amankan dengan kontrol teknis dan organisasi.
6. **Akuntabilitas dan transparansi.**
7. **Hak subjek data:** akses, koreksi, penghapusan, penarikan persetujuan, dan lain-lain.

**Privacy by design:** privasi dipertimbangkan sejak perancangan sistem, bukan ditambahkan belakangan.

## 14.3 Kerangka hukum di Indonesia

Beberapa rujukan yang relevan (periksa versi dan peraturan turunan terbaru **[verifikasi]**):

- **UU No. 27 Tahun 2022 tentang Pelindungan Data Pribadi (UU PDP):** mengatur hak subjek data serta kewajiban pengendali dan prosesor data pribadi, termasuk dasar pemrosesan, keamanan data, dan pemberitahuan kegagalan pelindungan data. Masa transisi dua tahun setelah pengundangan berakhir pada Oktober 2024, sehingga ketentuan sanksinya berlaku penuh.
- **UU ITE** dan perubahannya: mengatur transaksi elektronik dan perbuatan yang dilarang.
- **PP No. 71 Tahun 2019 tentang Penyelenggaraan Sistem dan Transaksi Elektronik:** kewajiban penyelenggara sistem elektronik, termasuk aspek keamanan dan lokasi data.
- Regulasi sektoral, misalnya dari OJK dan Bank Indonesia untuk sektor keuangan, serta Kementerian Kesehatan untuk data kesehatan.

Bagi perancang sistem, konsekuensi praktisnya: petakan data pribadi yang diproses, tentukan dasar hukumnya, terapkan kontrol keamanan yang proporsional, siapkan prosedur pelaporan insiden dan pemenuhan hak subjek data, dan dokumentasikan semuanya. Untuk nasihat hukum yang mengikat, konsultasikan dengan ahli hukum.

## 14.4 Teknik peningkat privasi

### Pseudonimisasi dan anonimisasi

- **Pseudonimisasi:** mengganti pengenal langsung (nama, NIK) dengan pengenal semu. Data masih dapat dihubungkan kembali dengan informasi tambahan yang disimpan terpisah, sehingga tetap tergolong data pribadi.
- **Anonimisasi:** data tidak lagi dapat dikaitkan dengan individu. Sulit dicapai dengan benar; menghapus nama saja sering tidak cukup karena kombinasi atribut (misalnya kode pos, tanggal lahir, jenis kelamin) dapat mengidentifikasi seseorang (serangan re-identifikasi).

### Differential privacy

**Differential privacy** menambahkan derau (noise) terkalibrasi pada hasil agregat sehingga keberadaan atau ketidakberadaan satu individu dalam data hampir tidak memengaruhi hasil. Parameter **epsilon** mengatur kompromi antara privasi dan akurasi: epsilon kecil berarti privasi lebih kuat tetapi hasil kurang akurat. Dipakai oleh beberapa perusahaan teknologi dan lembaga statistik.

### Federated learning

**Federated learning** melatih model pembelajaran mesin secara terdistribusi: data tetap di perangkat atau organisasi pemilik, hanya pembaruan model yang dikirim ke server untuk digabungkan. Mengurangi pemusatan data, tetapi **bukan jaminan privasi penuh** karena pembaruan model dapat membocorkan informasi; sering dikombinasikan dengan differential privacy dan agregasi aman.

### Teknik kriptografis

Komputasi multipihak aman, enkripsi homomorfik, dan zero-knowledge proof (Bab 10) memungkinkan komputasi atau verifikasi tanpa membuka data mentah.

## Ringkasan Bab 14

- Keamanan melindungi data; privasi mengatur penggunaannya yang sah.
- UU PDP menetapkan kewajiban dan sanksi; rancang sistem dengan privacy by design.
- Pseudonimisasi bukan anonimisasi; differential privacy dan federated learning adalah teknik penguat privasi dengan batasannya.

## Latihan Bab 14

1. Mengapa data yang hanya dihapus namanya belum tentu anonim?
2. Jelaskan peran parameter epsilon pada differential privacy.
3. Sebutkan tiga kewajiban teknis yang harus dipikirkan perancang sistem terkait UU PDP.
4. Mengapa federated learning belum otomatis menjamin privasi?

---

# Bab 15. Tren 2026, 2027, dan Seterusnya

## Tujuan pembelajaran

- Mengenali tren yang membentuk keamanan sistem terdistribusi ke depan.
- Menyusun daftar kesiapan (readiness) untuk menghadapinya.

Catatan: bab ini bersifat arah umum. Periksa perkembangan terbaru sebelum mengambil keputusan.

## 15.1 Migrasi ke kriptografi pasca-kuantum

- Standar NIST FIPS 203, 204, dan 205 sudah tersedia; implementasi hibrida pada TLS sudah dipakai luas pada peramban dan pustaka utama.
- Langkah yang layak dikerjakan pada 2026 dan 2027: **inventarisasi kriptografi** (CBOM, Cryptographic Bill of Materials), **prioritaskan data berumur panjang**, **uji mode hibrida di lingkungan non-produksi**, dan **rancang crypto agility**.
- Waspadai ukuran kunci dan tanda tangan yang lebih besar, yang memengaruhi latensi, ukuran sertifikat, dan batas protokol.
- Jadwal penghentian algoritma lama dari NIST dan lembaga lain perlu dipantau **[verifikasi]**.

## 15.2 Otomatisasi sertifikat dan identitas berumur pendek

Dengan masa berlaku sertifikat publik yang terus dipendekkan (Bab 4), pembaruan manual tidak lagi layak. Otomatisasi (ACME, SPIFFE/SPIRE, manajer sertifikat) menjadi kompetensi dasar. Sertifikat dan token yang berumur pendek mengurangi dampak kebocoran.

## 15.3 Autentikasi tanpa kata sandi

Passkey dan FIDO2 semakin menjadi standar untuk pengguna manusia. Fokus berikutnya adalah mengurangi ketergantungan pada rahasia statis untuk mesin: identitas beban kerja dan federasi identitas antarawan.

## 15.4 Komputasi rahasia dan data saat dipakai

Penyedia awan memperluas dukungan mesin virtual dan kontainer rahasia. Pemakaian meningkat untuk kolaborasi data antarorganisasi dan beban kerja pembelajaran mesin yang sensitif. Pahami batasan TEE dan manfaatkan attestation dengan benar.

## 15.5 Keamanan sistem berbasis agen AI

Semakin banyak sistem terdistribusi yang melibatkan **agen AI**, yaitu program berbasis model bahasa yang dapat memanggil alat, API, dan layanan atas nama pengguna. Ini memunculkan pertimbangan keamanan khas:

- **Prompt injection:** instruksi berbahaya yang disisipkan di dalam data (halaman web, dokumen, email) yang dibaca agen, sehingga agen melakukan tindakan yang tidak diinginkan. Pada dasarnya ini versi baru dari masalah **confused deputy** (Bab 7).
- **Hak istimewa terkecil untuk agen:** beri agen hanya alat dan cakupan akses yang diperlukan, dengan token berumur pendek.
- **Identitas dan akuntabilitas agen:** setiap tindakan agen harus dapat ditelusuri ke identitas agen dan pengguna yang mendelegasikannya.
- **Persetujuan manusia** untuk tindakan berdampak tinggi atau tidak dapat dibatalkan.
- **Isolasi dan pembatasan keluaran:** jalankan alat dalam lingkungan terisolasi; saring data yang boleh keluar.
- **Keamanan rantai pasok alat dan konektor:** konektor dan server alat pihak ketiga adalah bagian dari permukaan serangan.

Prinsip lama (autentikasi, otorisasi, hak terkecil, audit) tetap menjadi jawaban, hanya diterapkan pada jenis aktor baru.

## 15.6 Regulasi keamanan produk dan rantai pasok

Regulasi seperti **EU Cyber Resilience Act (CRA)** menuntut produsen produk digital memenuhi persyaratan keamanan, mengelola kerentanan, dan melaporkan insiden, dengan tahapan penerapan hingga akhir 2027 **[verifikasi jadwal]**. Meskipun regulasi ini berasal dari Uni Eropa, perusahaan Indonesia yang menjual produk atau layanan ke pasar Eropa dapat terdampak. SBOM dan proses penanganan kerentanan menjadi praktik standar.

## 15.7 Bahasa pemrograman aman memori dan desain aman sejak awal

Sebagian besar kerentanan serius berasal dari kesalahan memori pada bahasa seperti C dan C++. Dorongan industri dan pemerintah untuk memakai bahasa aman memori (misalnya Rust, Go, atau Java) pada komponen baru semakin kuat. Konsep **secure by design** dan **secure by default**: produk dikirim dalam konfigurasi paling aman, bukan membebankan pengamanan kepada pengguna.

## 15.8 Daftar periksa kesiapan

Gunakan daftar berikut untuk menilai sistem Anda. Jawab dengan ya atau tidak, lalu tindak lanjuti yang belum.

1. Apakah kami memiliki inventaris aset, layanan, dan identitas yang mutakhir?
2. Apakah semua komunikasi antarlayanan dienkripsi dan diautentikasi (mTLS)?
3. Apakah pengguna manusia memakai MFA tahan phishing?
4. Apakah tidak ada kredensial statis berumur panjang di kode atau konfigurasi?
5. Apakah pembaruan dan rotasi sertifikat serta kunci sepenuhnya otomatis?
6. Apakah kami punya inventaris kriptografi dan rencana migrasi pasca-kuantum?
7. Apakah ada SBOM dan pemindaian dependensi pada pipeline?
8. Apakah log terpusat, tahan-ubah, dan dipantau?
9. Apakah rencana respons insiden pernah dilatih dalam setahun terakhir?
10. Apakah cadangan diuji pemulihannya dan ada salinan immutable?
11. Apakah pemrosesan data pribadi terpetakan dan sesuai UU PDP?
12. Apakah hak akses agen otomatis (termasuk agen AI) dibatasi dan diaudit?

---

# Bab 16. Studi Kasus dan Proyek Akhir

## Tujuan pembelajaran

- Menganalisis insiden nyata dengan kerangka model keamanan.
- Menyusun proyek akhir yang mengintegrasikan materi buku.

## 16.1 Cara menganalisis sebuah insiden

Untuk setiap studi kasus, jawab pertanyaan berikut:

1. **Aset** apa yang menjadi sasaran?
2. **Penyerang** siapa dan dengan kemampuan apa (model ancaman)?
3. **Kerentanan** apa yang dimanfaatkan?
4. **Properti** apa yang dilanggar (kerahasiaan, integritas, ketersediaan, dan lain-lain)?
5. **Kontrol** apa yang gagal atau tidak ada?
6. **Pelajaran** apa untuk model keamanan dan arsitektur?

## 16.2 Studi kasus 1: Heartbleed (2014)

**Ringkasan:** kerentanan pada pustaka OpenSSL memungkinkan penyerang meminta server mengirim potongan memori yang tidak seharusnya, berpotensi membocorkan kunci privat, kata sandi, dan data sesi. Penyebabnya kesalahan validasi panjang pada fitur heartbeat (pembacaan di luar batas buffer).

**Analisis:**

- Aset: kunci privat server, data pengguna.
- Properti: kerahasiaan.
- Pelajaran: satu pustaka bersama yang dipakai jutaan sistem adalah titik kegagalan tunggal; pentingnya bahasa aman memori, audit kode, forward secrecy (membatasi dampak kebocoran kunci), serta kemampuan **merotasi kunci dan sertifikat dengan cepat** setelah insiden.

## 16.3 Studi kasus 2: SolarWinds (2020)

**Ringkasan:** penyerang menyusupkan kode berbahaya ke dalam proses build perangkat lunak manajemen jaringan, sehingga pembaruan resmi bertanda tangan yang didistribusikan ke ribuan pelanggan membawa pintu belakang.

**Analisis:**

- Aset: integritas rantai pasok pembaruan perangkat lunak.
- Properti: integritas dan autentisitas (tanda tangan valid tetapi atas kode yang sudah tercemar).
- Pelajaran: tanda tangan digital membuktikan asal, bukan niat baik; perlu pengamanan sistem build, build yang dapat direproduksi, provenans (SLSA), segmentasi, serta deteksi perilaku anomali pasca-instalasi (prinsip asumsikan pelanggaran).

## 16.4 Studi kasus 3: Log4Shell (2021)

**Ringkasan:** kerentanan eksekusi kode jarak jauh pada pustaka logging Java Log4j, dapat dipicu hanya dengan membuat aplikasi mencatat string tertentu, yang sering berasal dari masukan pengguna.

**Analisis:**

- Aset: seluruh sistem yang memakai pustaka itu.
- Properti: kerahasiaan, integritas, ketersediaan.
- Pelajaran: dependensi transitif sulit dilacak sehingga SBOM sangat bernilai; masukan tak tepercaya tidak boleh dievaluasi sebagai kode atau pencarian; pembatasan lalu lintas keluar (egress filtering) dan hak terkecil mengurangi dampak; pentingnya kemampuan menambal cepat di ribuan layanan.

## 16.5 Studi kasus 4: Botnet Mirai (2016)

**Ringkasan:** malware menginfeksi perangkat IoT (kamera, router) yang memakai kata sandi bawaan, membentuk botnet untuk serangan DDoS besar terhadap penyedia infrastruktur.

**Analisis:**

- Aset: ketersediaan layanan target.
- Properti: ketersediaan.
- Pelajaran: kredensial bawaan adalah kerentanan sistemik; prinsip **secure by default**; perlunya mitigasi DDoS berlapis; skala serangan terdistribusi menuntut pertahanan terdistribusi.

## 16.6 Proyek akhir: Sistem Pesan Terdistribusi yang Aman

### Deskripsi

Rancang dan bangun (atau rancang saja, jika waktu terbatas) sebuah sistem pemesanan sederhana yang terdiri dari minimal tiga layanan:

1. **Layanan Gerbang (API Gateway)** yang menerima permintaan pengguna.
2. **Layanan Pesanan** yang membuat dan membaca pesanan.
3. **Layanan Pembayaran** yang memproses pembayaran (boleh disimulasikan).

### Persyaratan keamanan

Dokumen dan implementasi harus memuat:

1. **Model ancaman:** diagram arus data, batas kepercayaan, dan analisis STRIDE dengan minimal 10 ancaman beserta kontrolnya (Bab 3).
2. **Komunikasi aman:** TLS pada sisi pengguna dan mTLS antarlayanan; gunakan CA laboratorium dari Bab 5.
3. **Autentikasi:** login pengguna dengan token berumur pendek (OIDC atau JWT yang diverifikasi benar sesuai Bab 6).
4. **Otorisasi:** kebijakan yang memastikan pengguna hanya membaca pesanannya sendiri, dan layanan hanya memanggil layanan yang diizinkan (Bab 7).
5. **Perlindungan replay:** idempotency key pada pembuatan pesanan dan pembayaran (Bab 5).
6. **Perlindungan data:** enkripsi data sensitif saat diam dengan enkripsi amplop; kunci tidak disimpan di kode (Bab 10).
7. **Mikrosegmentasi:** NetworkPolicy atau aturan jaringan setara (Bab 11).
8. **Log audit:** log terpusat tahan-ubah (minimal rantai hash) yang mencatat autentikasi, otorisasi, dan pembayaran (Bab 9 dan 13).
9. **Rantai pasok:** SBOM dan pemindaian dependensi (Bab 11).
10. **Privasi:** pemetaan data pribadi, minimisasi, dan rencana pemenuhan UU PDP (Bab 14).
11. **Rencana respons insiden** satu halaman: siapa melakukan apa jika kunci layanan pembayaran bocor (Bab 13).
12. **Rencana migrasi pasca-kuantum:** inventaris kriptografi dan langkah migrasi (Bab 4 dan 15).

### Rubrik penilaian

|Komponen|Bobot|
|---|---|
|Model ancaman dan analisis STRIDE|20 persen|
|Implementasi komunikasi dan identitas (TLS/mTLS, token)|20 persen|
|Otorisasi dan perlindungan replay|15 persen|
|Perlindungan data dan manajemen kunci|15 persen|
|Pemantauan, log, dan respons insiden|10 persen|
|Rantai pasok, privasi, dan rencana pasca-kuantum|10 persen|
|Kualitas dokumentasi dan presentasi|10 persen|

### Saran pengerjaan bertahap

1. Minggu 1: gambar arsitektur, diagram arus data, dan model ancaman.
2. Minggu 2: bangun tiga layanan dasar tanpa keamanan lalu uji fungsi.
3. Minggu 3: tambahkan TLS, mTLS, dan autentikasi.
4. Minggu 4: tambahkan otorisasi, idempotency, enkripsi data, dan log audit.
5. Minggu 5: pengujian keamanan (percobaan serangan di lingkungan lab), perbaikan, dan dokumentasi akhir.

---

# Lampiran A. Glosarium

|Istilah|Arti singkat|
|---|---|
|ABAC|Kontrol akses berbasis atribut|
|ACME|Protokol otomatisasi penerbitan sertifikat|
|AEAD|Enkripsi terautentikasi dengan data tambahan; memberi kerahasiaan dan integritas|
|Attestation|Bukti kriptografis tentang perangkat keras dan perangkat lunak yang berjalan|
|Autentikasi|Membuktikan identitas|
|Otorisasi|Menentukan hak akses|
|BFT|Toleransi kesalahan Bizantium|
|CA|Certificate Authority, penerbit sertifikat|
|CAP|Teorema tentang konsistensi, ketersediaan, dan toleransi partisi|
|Confused deputy|Layanan berhak besar diperdaya melakukan tindakan atas nama pihak berhak kecil|
|Crypto agility|Kemampuan mengganti algoritma kriptografi dengan mudah|
|DEK|Kunci yang mengenkripsi data|
|Dolev-Yao|Model penyerang yang menguasai jaringan tetapi tidak memecahkan kriptografi|
|ECDH|Pertukaran kunci Diffie-Hellman kurva eliptik|
|Envelope encryption|Enkripsi dua tingkat dengan DEK dan KEK|
|Forward secrecy|Kebocoran kunci jangka panjang tidak membuka sesi lama|
|HMAC|MAC berbasis fungsi hash|
|HSM|Modul perangkat keras untuk menyimpan dan memakai kunci|
|IAM|Manajemen identitas dan akses|
|JWT|Token berformat JSON yang umumnya ditandatangani|
|KDC|Pusat distribusi kunci pada Kerberos|
|KEK|Kunci yang membungkus kunci lain|
|KMS|Layanan manajemen kunci|
|MAC|Kode autentikasi pesan|
|MFA|Autentikasi multi-faktor|
|ML-KEM, ML-DSA, SLH-DSA|Algoritma pasca-kuantum standar NIST|
|mTLS|TLS dengan autentikasi dua arah|
|Nonce|Bilangan yang dipakai sekali|
|OAuth 2.0|Kerangka delegasi otorisasi|
|OIDC|Lapisan autentikasi di atas OAuth 2.0|
|PBFT|Protokol BFT praktis|
|PDP, PEP|Titik keputusan dan titik penegakan kebijakan|
|PKCE|Perlindungan kode otorisasi pada OAuth|
|PKI|Infrastruktur kunci publik|
|PQC|Kriptografi pasca-kuantum|
|RBAC|Kontrol akses berbasis peran|
|Replay|Serangan pengiriman ulang pesan sah|
|SBOM|Daftar komponen perangkat lunak|
|Service mesh|Lapisan infrastruktur komunikasi antarlayanan|
|Shamir|Skema berbagi rahasia ambang|
|SIEM|Sistem pengumpulan dan analisis peristiwa keamanan|
|SPIFFE/SPIRE|Standar dan implementasi identitas beban kerja|
|STRIDE|Kerangka klasifikasi ancaman|
|Sybil attack|Pemalsuan banyak identitas|
|TCB|Basis komputasi tepercaya|
|TEE|Lingkungan eksekusi tepercaya|
|TLS|Protokol keamanan lapisan transport|
|Zero Trust|Arsitektur "jangan percaya, selalu verifikasi"|

---

# Lampiran B. Rencana Belajar 14 Minggu

|Minggu|Topik|Aktivitas|
|---|---|---|
|1|Bab 1 dan 2|Baca, kerjakan latihan, buat peta konsep|
|2|Bab 3|Buat diagram arus data dan analisis STRIDE sederhana|
|3|Bab 4 (bagian 1)|Praktik hash, HMAC, dan AEAD dengan Python|
|4|Bab 4 (bagian 2)|Pahami PKI dan PQC; buat ringkasan satu halaman|
|5|Bab 5|Praktik CA mini dan mTLS dengan OpenSSL|
|6|Bab 6|Praktik OAuth/OIDC dengan penyedia identitas uji; verifikasi JWT|
|7|Bab 7|Tulis kebijakan Rego dan uji dengan OPA|
|8|Ujian tengah|Ujian dan tinjauan|
|9|Bab 8 dan 9|Kode rantai hash; bandingkan Raft dan PBFT secara konsep|
|10|Bab 10|Praktik enkripsi amplop dan Shamir|
|11|Bab 11|Praktik NetworkPolicy dan pemindaian dependensi|
|12|Bab 12 dan 13|Simulasi tabletop respons insiden|
|13|Bab 14 dan 15|Pemetaan data pribadi dan rencana migrasi PQC|
|14|Bab 16|Presentasi proyek akhir|

---

# Lampiran C. Daftar Pustaka

## Buku

1. Andrew S. Tanenbaum dan Maarten van Steen. _Distributed Systems: Principles and Paradigms_ (atau edisi terbaru _Distributed Systems_).
2. Ross Anderson. _Security Engineering: A Guide to Building Dependable Distributed Systems_.
3. Martin Kleppmann. _Designing Data-Intensive Applications_.
4. Jean-Philippe Aumasson. _Serious Cryptography_.
5. Adam Shostack. _Threat Modeling: Designing for Security_.
6. Christian Cachin, Rachid Guerraoui, dan Luis Rodrigues. _Introduction to Reliable and Secure Distributed Programming_.

## Makalah klasik

1. J. Saltzer dan M. Schroeder. "The Protection of Information in Computer Systems" (1975).
2. D. Dolev dan A. Yao. "On the Security of Public Key Protocols" (1983).
3. L. Lamport, R. Shostak, dan M. Pease. "The Byzantine Generals Problem" (1982).
4. M. Fischer, N. Lynch, dan M. Paterson. "Impossibility of Distributed Consensus with One Faulty Process" (1985).
5. A. Shamir. "How to Share a Secret" (1979).
6. M. Castro dan B. Liskov. "Practical Byzantine Fault Tolerance" (1999).
7. D. Ongaro dan J. Ousterhout. "In Search of an Understandable Consensus Algorithm (Raft)" (2014).

## Standar dan dokumen resmi

1. RFC 8446: The Transport Layer Security (TLS) Protocol Version 1.3.
2. RFC 2104: HMAC: Keyed-Hashing for Message Authentication.
3. RFC 6749 dan RFC 7636: OAuth 2.0 dan PKCE.
4. RFC 7519: JSON Web Token (JWT).
5. NIST SP 800-207: Zero Trust Architecture.
6. NIST SP 800-61: Computer Security Incident Handling Guide.
7. NIST FIPS 203, 204, 205: standar kriptografi pasca-kuantum.
8. OWASP Top 10 dan OWASP API Security Top 10.
9. SLSA (Supply-chain Levels for Software Artifacts) dan SPDX/CycloneDX untuk SBOM.
10. Undang-Undang No. 27 Tahun 2022 tentang Pelindungan Data Pribadi.

---

_Akhir buku. Selamat belajar. Keamanan adalah disiplin yang berkembang terus; kebiasaan memeriksa sumber resmi dan mencoba langsung di laboratorium akan jauh lebih berharga daripada menghafal._