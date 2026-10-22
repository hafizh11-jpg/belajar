# Interaksi Manusia dan Komputer

### Buku Pembelajaran untuk Pemula, Program Studi Teknik Informatika

Edisi Oktober 2026 (disusun untuk pembelajaran tahun 2026, 2027, dan seterusnya)

---

## Kata Pengantar

Buku ini ditulis untuk Anda yang baru pertama kali belajar Interaksi Manusia dan Komputer (IMK). Anda tidak perlu latar belakang desain atau psikologi. Cukup kemampuan dasar menggunakan komputer dan ponsel, serta rasa ingin tahu mengapa sebuah aplikasi terasa mudah dipakai sementara aplikasi lain terasa membingungkan.

Cara penulisan buku ini:

- Istilah teknis ditulis dengan padanan bahasa Inggrisnya pada saat pertama kali muncul, misalnya _usabilitas_ (_usability_), karena di dunia kerja dan literatur, istilah Inggris lebih sering dipakai.
- Setiap konsep dijelaskan dengan bahasa sehari-hari terlebih dahulu, lalu diberi definisi teknis.
- Setiap bab diakhiri dengan ringkasan dan latihan. Jawaban latihan ada di Lampiran B.
- Contoh kode memakai HTML, CSS, JavaScript, dan Python karena paling mudah dibaca pemula.

### Catatan tentang Waktu dan Pembaruan

Buku ini disusun pada Oktober 2026. Sebagian isi bersifat **tahan lama** (cara kerja persepsi manusia, prinsip desain, metode evaluasi) dan sebagian lagi bersifat **cepat berubah** (fitur produk AI, standar aksesibilitas, perangkat spasial). Untuk membantu Anda, bagian yang cepat berubah diberi label **Catatan Versi**. Jika Anda membaca buku ini pada 2027 atau sesudahnya, periksa ulang bagian berlabel tersebut ke sumber resmi yang tercantum di Daftar Pustaka.

### Cara Menggunakan Buku Ini

|Jika Anda...|Saran jalur belajar|
|---|---|
|Mahasiswa semester awal|Baca berurutan Bab 1 sampai Bab 12, kerjakan semua latihan|
|Ingin cepat praktik|Baca Bab 1, 4, 5, 7, 9, 10, lalu kerjakan Bab 16|
|Developer yang ingin lebih peka UX|Fokus Bab 4, 5, 8, 11, 12, 13|
|Mempersiapkan skripsi atau tugas akhir|Fokus Bab 6, 7, 10, 15|

---

## Daftar Isi

- Bab 1. Pengantar IMK
- Bab 2. Manusia sebagai Pengguna
- Bab 3. Komputer, Perangkat, dan Gaya Interaksi
- Bab 4. Model Mental dan Prinsip Dasar Norman
- Bab 5. Heuristik dan Pedoman Desain
- Bab 6. Proses Desain Berpusat pada Pengguna
- Bab 7. Riset Pengguna
- Bab 8. Desain Visual dan Tata Letak
- Bab 9. Prototipe dan Arsitektur Informasi
- Bab 10. Evaluasi Usabilitas
- Bab 11. Aksesibilitas dan Inklusivitas
- Bab 12. Desain untuk Berbagai Platform
- Bab 13. IMK di Era Kecerdasan Buatan
- Bab 14. Komputasi Spasial dan Antarmuka Masa Depan
- Bab 15. Etika, Privasi, dan Dampak Sosial
- Bab 16. Proyek Akhir dan Peta Jalan Belajar
- Lampiran A. Glosarium
- Lampiran B. Jawaban Latihan
- Lampiran C. Daftar Periksa Desain
- Lampiran D. Templat Dokumen
- Daftar Pustaka

---

## Bab 1. Pengantar IMK

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjelaskan apa itu IMK dan mengapa penting bagi seorang informatikawan.
2. Membedakan istilah UI, UX, usabilitas, dan aksesibilitas.
3. Menyebutkan tonggak sejarah utama IMK.
4. Menjelaskan tiga komponen usabilitas menurut ISO 9241-11.

### 1.1 Apa Itu IMK?

**Interaksi Manusia dan Komputer (IMK)**, dalam bahasa Inggris _Human-Computer Interaction_ (HCI), adalah bidang ilmu yang mempelajari bagaimana manusia berinteraksi dengan sistem komputasi, dan bagaimana merancang sistem tersebut agar sesuai dengan kemampuan, kebutuhan, dan keterbatasan manusia.

Perhatikan bahwa definisi ini mengandung dua arah:

- **Memahami manusia**: bagaimana orang melihat, berpikir, mengingat, dan bertindak.
- **Merancang sistem**: bagaimana tampilan, alur, dan perilaku perangkat lunak dibuat supaya manusia berhasil mencapai tujuannya.

Contoh sederhana: tombol "Bayar" pada aplikasi belanja. Dari sudut pandang pemrograman, tombol itu hanya elemen yang memicu fungsi. Dari sudut pandang IMK, kita bertanya:

- Apakah pengguna menyadari tombol itu bisa ditekan?
- Apakah posisinya mudah dijangkau jempol?
- Apakah setelah ditekan, pengguna tahu bahwa sistem sedang memproses?
- Apa yang terjadi jika pengguna salah menekan?
- Apakah pengguna dengan gangguan penglihatan bisa menemukannya dengan pembaca layar?

Semua pertanyaan itu adalah pertanyaan IMK.

### 1.2 Mengapa IMK Penting bagi Teknik Informatika?

Anda bisa menulis program yang benar secara teknis, tetapi tetap gagal sebagai produk bila pengguna tidak bisa atau tidak mau memakainya. Alasan IMK penting:

1. **Biaya kesalahan manusia**. Antarmuka yang membingungkan menyebabkan salah input, salah transfer, atau salah diagnosis pada sistem kritis seperti perangkat medis.
2. **Adopsi produk**. Pengguna yang bingung pada dua menit pertama cenderung meninggalkan aplikasi.
3. **Biaya pengembangan**. Memperbaiki masalah desain pada tahap rancangan jauh lebih murah daripada memperbaikinya setelah kode selesai dan dirilis.
4. **Kewajiban hukum dan sosial**. Banyak negara mengatur aksesibilitas layanan digital. Di Indonesia, hak penyandang disabilitas diatur antara lain dalam Undang-Undang Nomor 8 Tahun 2016.
5. **Daya saing karier**. Perusahaan mencari engineer yang memahami pengguna, bukan hanya sintaks.

### 1.3 Istilah yang Sering Tertukar

|Istilah|Singkatan|Penjelasan singkat|Contoh|
|---|---|---|---|
|Antarmuka pengguna (_User Interface_)|UI|Apa yang dilihat dan disentuh pengguna: layar, tombol, menu, suara|Warna tombol, tata letak halaman|
|Pengalaman pengguna (_User Experience_)|UX|Keseluruhan pengalaman sebelum, selama, dan sesudah memakai produk|Dari mendaftar sampai mendapat bantuan saat ada masalah|
|Usabilitas (_Usability_)|-|Seberapa mudah, efisien, dan memuaskan sebuah produk dipakai untuk tujuan tertentu|Waktu yang dibutuhkan untuk menyelesaikan checkout|
|Aksesibilitas (_Accessibility_)|a11y|Seberapa baik produk dapat dipakai oleh orang dengan beragam kemampuan|Dukungan pembaca layar, kontras warna|
|Desain interaksi (_Interaction Design_)|IxD|Merancang perilaku produk: respons terhadap aksi pengguna|Animasi saat item dihapus beserta tombol urungkan|
|Arsitektur informasi (_Information Architecture_)|IA|Cara mengorganisasi dan memberi label pada konten|Struktur menu dan kategori|
|Desain berpusat pada manusia (_Human-Centered Design_)|HCD|Pendekatan proses yang menempatkan kebutuhan pengguna sebagai pusat|Riset, prototipe, uji, ulangi|

> Catatan: UI adalah bagian dari UX, tetapi UX lebih luas. Antarmuka yang indah tidak otomatis menghasilkan pengalaman yang baik.

### 1.4 Sejarah Singkat IMK

|Tahun|Peristiwa|Mengapa penting|
|---|---|---|
|1945|Vannevar Bush mengusulkan konsep _Memex_|Gagasan awal tentang penyimpanan dan penelusuran informasi yang terhubung, cikal bakal hiperteks|
|1963|Ivan Sutherland membuat _Sketchpad_|Awal grafika komputer interaktif dan manipulasi langsung|
|1968|Douglas Engelbart mendemonstrasikan mouse, jendela, dan hiperteks|Demonstrasi yang kemudian dijuluki "Mother of All Demos"|
|1973|Xerox Alto|Komputer dengan antarmuka grafis bertenaga bitmap dan mouse|
|1984|Apple Macintosh|Antarmuka grafis menjadi produk massal|
|1990-an|World Wide Web dan peramban|Antarmuka berbasis halaman, tautan, dan formulir|
|2007|Ponsel layar sentuh multisentuh populer|Gestur sentuh menjadi cara utama berinteraksi|
|2010-an|Asisten suara, aplikasi seluler masif|Interaksi suara dan antarmuka seluler menjadi arus utama|
|2020-an|Model bahasa generatif|Bahasa alami menjadi antarmuka; muncul pola copilot dan agen|
|2024 dan sesudahnya|Perangkat komputasi spasial dan agen AI lebih matang|Interaksi bergeser dari mengoperasikan layar ke menyampaikan tujuan dan mengawasi sistem|

Pola besarnya: setiap generasi mengurangi jarak antara niat manusia dan tindakan pada mesin. Dari kartu berlubang, baris perintah, antarmuka grafis, sentuh, suara, hingga bahasa alami dan agen.

### 1.5 Usabilitas Menurut ISO 9241-11

Standar internasional ISO 9241-11 mendefinisikan usabilitas sebagai sejauh mana sebuah produk dapat dipakai oleh pengguna tertentu untuk mencapai tujuan tertentu dengan tiga ukuran dalam konteks pemakaian yang spesifik:

1. **Efektivitas** (_effectiveness_): apakah pengguna berhasil mencapai tujuan dengan akurat dan lengkap?
2. **Efisiensi** (_efficiency_): berapa sumber daya (waktu, langkah, usaha mental) yang dibutuhkan?
3. **Kepuasan** (_satisfaction_): apakah pengalamannya nyaman dan dapat diterima?

Kata kunci: **pengguna tertentu**, **tujuan tertentu**, **konteks tertentu**. Aplikasi yang mudah bagi mahasiswa informatika belum tentu mudah bagi lansia. Aplikasi yang nyaman dipakai di kantor ber-Wi-Fi belum tentu nyaman di angkot dengan sinyal lemah.

Jakob Nielsen merinci usabilitas menjadi lima atribut mutu:

|Atribut|Pertanyaan kunci|
|---|---|
|Kemudahan dipelajari (_learnability_)|Seberapa mudah pengguna baru menyelesaikan tugas pertamanya?|
|Efisiensi (_efficiency_)|Setelah mahir, seberapa cepat tugas diselesaikan?|
|Kemudahan diingat (_memorability_)|Jika lama tidak memakai, seberapa mudah mengingat cara pakainya?|
|Galat (_errors_)|Seberapa sering dan seberapa parah kesalahan? Seberapa mudah pulih?|
|Kepuasan (_satisfaction_)|Seberapa menyenangkan dipakai?|

### 1.6 Bidang yang Berkontribusi pada IMK

IMK bersifat multidisiplin:

- **Informatika**: pemrograman, sistem, basis data, kecerdasan buatan
- **Psikologi kognitif**: persepsi, memori, perhatian, pengambilan keputusan
- **Desain**: grafis, industri, interaksi
- **Ergonomi dan faktor manusia** (_human factors_): kenyamanan fisik dan keselamatan
- **Ilmu sosial dan antropologi**: konteks budaya dan kerja
- **Linguistik**: bahasa, percakapan, mikroteks

### Ringkasan Bab 1

- IMK mempelajari bagaimana manusia berinteraksi dengan komputer dan bagaimana merancang interaksi itu agar baik.
- UI adalah bagian dari UX; usabilitas dan aksesibilitas adalah kualitas yang ingin dicapai.
- Usabilitas diukur dari efektivitas, efisiensi, dan kepuasan pada pengguna, tujuan, dan konteks tertentu.

### Latihan Bab 1

1. Jelaskan dengan kalimat Anda sendiri perbedaan UI dan UX. Beri satu contoh produk yang UI-nya menarik tetapi UX-nya buruk.
2. Pilih satu aplikasi yang Anda pakai setiap hari. Tuliskan satu contoh masing-masing untuk efektivitas, efisiensi, dan kepuasan pada aplikasi itu.
3. Mengapa definisi usabilitas selalu menyebut "pengguna tertentu" dan "konteks tertentu"?
4. Sebutkan tiga bidang ilmu yang berkontribusi pada IMK dan satu hal yang disumbangkan masing-masing.

---

## Bab 2. Manusia sebagai Pengguna

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjelaskan cara kerja persepsi, memori, dan perhatian secara garis besar.
2. Menggunakan Hukum Fitts dan Hukum Hick untuk mengambil keputusan desain.
3. Menjelaskan beban kognitif dan cara menguranginya.
4. Menyadari keragaman pengguna: usia, budaya, kemampuan, dan kondisi perangkat.

### 2.1 Model Pemroses Manusia

Untuk merancang sistem, kita perlu model sederhana tentang cara manusia memproses informasi. Salah satu model klasik adalah _Model Human Processor_ (Card, Moran, dan Newell, 1983) yang membagi manusia menjadi tiga subsistem:

```
   Lingkungan / Layar
          |
          v
 +--------------------+     +--------------------+     +--------------------+
 |  Sistem Perseptual | --> |  Sistem Kognitif   | --> |  Sistem Motorik    |
 |  (melihat, dengar) |     |  (berpikir, putus) |     |  (gerak tangan,    |
 |                    |     |                    |     |   jari, suara)     |
 +--------------------+     +--------------------+     +--------------------+
          ^                          |                          |
          |                          v                          |
          |                 Memori kerja &                      |
          |                 memori jangka panjang               |
          +-------------------- umpan balik <-------------------+
```

Setiap tahap memakan waktu. Total waktu reaksi dalam tugas sederhana berada pada orde ratusan milidetik. Artinya, sistem yang lambat merespons akan terasa jelas bagi pengguna.

### 2.2 Persepsi

**Penglihatan.** Mata kita hanya melihat tajam pada area kecil di tengah pandangan yang disebut _fovea_. Sisanya (penglihatan tepi) peka terhadap gerakan dan kontras tetapi tidak tajam. Konsekuensi desain:

- Letakkan elemen terpenting di tempat mata cenderung melihat lebih dulu.
- Gerakan atau kedipan di tepi layar menarik perhatian, sehingga animasi yang berlebihan mengganggu.
- Teks kecil dengan kontras rendah sulit dibaca, terlebih di bawah sinar matahari.

**Warna.** Sekitar 1 dari 12 pria dan sekitar 1 dari 200 wanita memiliki buta warna merah-hijau (angka bervariasi menurut populasi). Jangan pernah hanya memakai warna sebagai satu-satunya pembeda, misalnya status "berhasil" hijau dan "gagal" merah tanpa ikon atau teks.

**Pendengaran.** Suara efektif untuk notifikasi, tetapi tidak boleh menjadi satu-satunya kanal karena pengguna mungkin berada di tempat bising, memakai mode senyap, atau memiliki gangguan pendengaran.

**Sentuhan** (_haptic_). Getaran dan umpan balik taktil mengonfirmasi tindakan tanpa perlu melihat, misalnya getar halus saat kode berhasil dimasukkan.

### 2.3 Memori

|Jenis memori|Kapasitas dan durasi|Implikasi desain|
|---|---|---|
|Sensori|Sangat singkat (sekitar detik)|Informasi yang muncul sekejap, seperti notifikasi hilang cepat, mudah terlewat|
|Kerja (_working memory_)|Terbatas; sekitar 4 "kepingan" (_chunk_) informasi menurut riset modern, tahan puluhan detik|Jangan paksa pengguna mengingat informasi dari satu layar ke layar lain|
|Jangka panjang|Sangat besar dan tahan lama, tetapi pengambilan tidak selalu mudah|Manfaatkan pola yang sudah dikenal pengguna dari aplikasi lain|

Angka terkenal "7 plus minus 2" dari George Miller (1956) sering dikutip, tetapi riset kemudian (misalnya Nelson Cowan) menunjukkan kapasitas efektif memori kerja lebih mendekati 3 sampai 5 kepingan. Pelajaran praktisnya sama: **kurangi beban ingatan**. Gunakan _chunking_, yaitu mengelompokkan informasi. Nomor telepon `081234567890` lebih mudah dibaca sebagai `0812-3456-7890`.

Prinsip turunannya, **kenali lebih mudah daripada ingat** (_recognition over recall_): menampilkan daftar pilihan lebih mudah daripada meminta pengguna mengetik perintah dari ingatan.

### 2.4 Perhatian

Perhatian manusia terbatas dan selektif.

- **Perhatian selektif**: kita hanya memproses sebagian kecil rangsangan.
- **Kebutaan banner** (_banner blindness_): pengguna cenderung mengabaikan area yang tampak seperti iklan, termasuk konten penting yang kebetulan berdesain seperti iklan.
- **Kebutaan perubahan** (_change blindness_): perubahan kecil pada layar sering tidak disadari jika tidak ada penanda yang jelas.
- **Gangguan** (_interruption_): notifikasi dan pop-up memecah fokus dan memperbesar peluang kesalahan.

Desain yang baik menarik perhatian hanya pada hal yang memang penting, misalnya peringatan sebelum menghapus data.

### 2.5 Beban Kognitif

**Beban kognitif** (_cognitive load_) adalah total usaha mental yang dibutuhkan untuk menyelesaikan tugas. Teori yang dikembangkan John Sweller membaginya menjadi tiga:

1. **Intrinsik**: kesulitan bawaan tugas itu sendiri (misalnya mengisi pajak memang rumit).
2. **Ekstraneus** (_extraneous_): kesulitan yang timbul karena desain yang buruk (menu berantakan, istilah asing, langkah berulang).
3. **Germane**: usaha yang berguna untuk belajar dan memahami.

Tugas desainer dan developer: **memperkecil beban ekstraneus** agar usaha mental pengguna dipakai untuk tujuan mereka, bukan untuk melawan antarmuka.

Cara praktis menguranginya:

- Pecah formulir panjang menjadi langkah-langkah pendek.
- Beri nilai bawaan (_default_) yang masuk akal.
- Gunakan kata yang dipahami pengguna, bukan istilah internal tim.
- Tampilkan hanya informasi yang relevan pada saat itu (_progressive disclosure_).
- Hindari meminta data yang sama dua kali.

### 2.6 Hukum-Hukum yang Berguna

Bagian ini berisi hukum empiris yang sering dipakai dalam IMK. Anda tidak perlu menghafal angkanya, tetapi pahami logikanya.

#### Hukum Fitts (_Fitts's Law_)

Waktu untuk menjangkau sebuah target bergantung pada **jarak** ke target dan **ukuran** target. Target yang lebih besar dan lebih dekat lebih cepat dicapai. Rumus (bentuk Shannon):

```
MT = a + b * log2( D / W + 1 )
```

- `MT` : waktu gerak (_movement time_)
- `D` : jarak ke target
- `W` : lebar target pada arah gerak
- `a`, `b` : konstanta empiris yang bergantung perangkat dan pengguna

Contoh perhitungan dengan Python:

```python
import math

def waktu_fitts(a, b, jarak, lebar):
    """Perkiraan waktu menjangkau target (detik)."""
    indeks_kesulitan = math.log2(jarak / lebar + 1)  # dalam bit
    return a + b * indeks_kesulitan

a, b = 0.10, 0.15  # nilai contoh, bukan hasil pengukuran nyata

print(round(waktu_fitts(a, b, jarak=400, lebar=40), 3))  # tombol kecil
print(round(waktu_fitts(a, b, jarak=400, lebar=80), 3))  # tombol besar
```

Hasil: sekitar 0,619 detik untuk tombol kecil dan 0,488 detik untuk tombol besar. Menggandakan lebar tombol menurunkan waktu jangkauan.

Implikasi desain:

- Tombol penting dibuat cukup besar, terutama pada layar sentuh.
- Letakkan aksi yang sering dipakai dekat dengan lokasi jari atau kursor pengguna.
- Tepi dan sudut layar pada komputer desktop mudah dijangkau karena kursor tertahan di tepi (itulah alasan bilah menu macOS menempel di tepi atas).
- Jangan tempatkan tombol berbahaya (misalnya "Hapus Akun") berdekatan dengan tombol yang sering ditekan.

#### Hukum Hick (_Hick's Law_)

Waktu untuk mengambil keputusan bertambah seiring jumlah pilihan. Bentuk umumnya:

```
T = b * log2( n + 1 )
```

dengan `n` jumlah pilihan yang sama probabilitasnya. Implikasi: menu dengan 30 item membuat pengguna lebih lama memilih daripada menu dengan 7 item yang dikelompokkan. Namun hati-hati: jangan menyembunyikan terlalu banyak sehingga pengguna harus menelusuri level yang dalam.

#### Hukum Jakob (_Jakob's Law_)

Pengguna menghabiskan sebagian besar waktunya di situs dan aplikasi lain. Mereka berharap produk Anda bekerja seperti produk yang sudah mereka kenal. Ikon keranjang di pojok kanan atas pada toko daring dikenali karena hampir semua toko daring memakainya.

#### Hukum Tesler (_Law of Conservation of Complexity_)

Setiap sistem memiliki kompleksitas minimum yang tidak bisa dihilangkan, hanya dipindahkan. Pertanyaannya: apakah kompleksitas ditanggung pengguna atau oleh sistem dan pengembang? Misalnya, mendeteksi lokasi pengguna otomatis memindahkan kerumitan dari pengguna ke sistem.

#### Ambang Doherty (_Doherty Threshold_) dan Batas Waktu Respons

Menurut riset yang dipopulerkan Jakob Nielsen, kesan pengguna terhadap kecepatan sistem kira-kira:

|Waktu respons|Kesan pengguna|Apa yang sebaiknya dilakukan|
|---|---|---|
|Sampai sekitar 0,1 detik|Terasa instan|Tidak perlu indikator khusus|
|Sampai sekitar 1 detik|Pengguna masih merasa alur berpikirnya tidak terputus|Beri umpan balik ringan|
|Sampai sekitar 10 detik|Batas perhatian pengguna tertahan|Tampilkan indikator kemajuan|
|Lebih dari 10 detik|Pengguna cenderung berpindah tugas|Beri progres jelas, estimasi, atau proses di latar belakang|

#### Aturan Puncak-Akhir (_Peak-End Rule_)

Orang menilai pengalaman terutama dari momen paling intens (puncak) dan bagian akhirnya, bukan rata-rata seluruh pengalaman. Karena itu pesan sukses setelah pembayaran dan penanganan kesalahan punya pengaruh besar pada kesan keseluruhan.

#### Efek Von Restorff

Elemen yang berbeda dari sekitarnya lebih mudah diingat. Gunakan untuk satu aksi utama per layar (_primary action_). Jika semua tombol dibuat mencolok, tidak ada yang menonjol.

### 2.7 Bias Kognitif dalam Antarmuka

Manusia tidak selalu rasional. Beberapa kecenderungan yang perlu dipahami:

- **Efek bawaan** (_default effect_): kebanyakan orang tidak mengubah nilai bawaan. Karena itu nilai bawaan mengandung tanggung jawab etis (lihat Bab 15).
- **Penjangkaran** (_anchoring_): angka pertama yang dilihat memengaruhi penilaian berikutnya (harga coret).
- **Keengganan rugi** (_loss aversion_): kerugian terasa lebih berat daripada keuntungan setara.
- **Bias otomatisasi** (_automation bias_): kecenderungan terlalu percaya pada keluaran sistem otomatis, topik penting pada era AI (Bab 13).

### 2.8 Keragaman Pengguna

Jangan merancang untuk "pengguna rata-rata" karena ia tidak ada. Pertimbangkan:

|Dimensi|Contoh|
|---|---|
|Usia|Anak, remaja, dewasa, lansia dengan kemampuan motorik dan penglihatan berbeda|
|Kemampuan|Penglihatan, pendengaran, motorik, kognitif; permanen, sementara (tangan patah), atau situasional (membawa bayi)|
|Literasi digital|Dari pengguna ahli sampai orang yang baru pertama kali memakai ponsel pintar|
|Bahasa dan budaya|Bahasa daerah, bahasa campuran, makna warna dan simbol yang berbeda, format tanggal dan mata uang|
|Perangkat|Ponsel dengan memori kecil, layar retak, baterai lemah|
|Konektivitas|Sinyal tidak stabil, kuota terbatas|

Untuk konteks Indonesia, pertimbangan perangkat murah, jaringan yang tidak merata, dan penggunaan campuran bahasa Indonesia dan bahasa daerah sering menjadi faktor penentu kualitas pengalaman.

### Ringkasan Bab 2

- Manusia memproses informasi melalui persepsi, kognisi, dan gerak, dan setiap tahap memiliki batas.
- Memori kerja sangat terbatas, sehingga desain harus mengurangi beban ingatan.
- Hukum Fitts, Hick, Jakob, dan Tesler, serta batas waktu respons, adalah alat bantu keputusan desain.
- Pengguna sangat beragam; rancang untuk rentang kemampuan, bukan satu orang rata-rata.

### Latihan Bab 2

1. Gunakan fungsi `waktu_fitts` dengan `a=0.1`, `b=0.15`. Hitung waktu untuk `jarak=600`, `lebar=30`, lalu `lebar=60`. Apa kesimpulan Anda?
2. Mengapa menampilkan status "Berhasil" hanya dengan warna hijau bermasalah bagi sebagian pengguna? Apa perbaikannya?
3. Sebuah halaman formulir meminta pengguna menyalin kode dari satu layar lalu mengetiknya di layar berikutnya. Prinsip memori mana yang dilanggar? Usulkan perbaikannya.
4. Jelaskan beda beban kognitif intrinsik dan ekstraneus dengan contoh dari aplikasi perbankan seluler.
5. Sebutkan tiga kondisi situasional (bukan disabilitas permanen) yang memengaruhi cara orang memakai ponsel.

---

## Bab 3. Komputer, Perangkat, dan Gaya Interaksi

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menyebutkan perangkat masukan dan keluaran beserta kelebihan dan keterbatasannya.
2. Membedakan gaya interaksi: baris perintah, menu, formulir, manipulasi langsung, sentuh, suara, dan percakapan.
3. Menjelaskan siklus dasar interaksi pada perangkat lunak berbasis peristiwa (_event_).

### 3.1 Perangkat Masukan (_Input_)

|Perangkat|Kelebihan|Keterbatasan|
|---|---|---|
|Papan ketik|Cepat dan presisi untuk teks, pintasan|Butuh keterampilan; kurang cocok untuk gerak spasial|
|Mouse dan trackpad|Presisi untuk penunjukan|Butuh permukaan datar; tidak ada di ponsel|
|Layar sentuh|Langsung dan intuitif|Jari menutupi layar; target harus cukup besar; tidak ada "hover"|
|Pena digital (_stylus_)|Menulis dan menggambar presisi|Perlu perangkat tambahan|
|Suara|Bebas tangan, cepat untuk perintah sederhana|Terganggu bising; isu privasi; sulit untuk koreksi presisi|
|Gestur dan kamera|Tanpa kontak|Kelelahan lengan, deteksi tidak sempurna|
|Pelacak mata (_eye tracking_)|Cepat menunjuk objek yang dilihat|Perlu kalibrasi; masalah privasi data biometrik|
|Sensor (akselerometer, giroskop, lokasi)|Konteks otomatis|Pengguna mungkin tidak sadar sedang dilacak|
|Pengendali khusus (_game controller_, joystick)|Sesuai tugas tertentu|Tidak umum|

### 3.2 Perangkat Keluaran (_Output_)

- **Layar**: diukur dengan resolusi, kerapatan piksel (PPI), kecerahan, laju penyegaran (_refresh rate_), dan akurasi warna.
- **Audio**: musik, suara sistem, pembacaan teks (_text-to-speech_), audio spasial.
- **Haptik**: getaran, tekanan, dan sensasi lain.
- **Pencetak dan perangkat fisik lain**: tampilan braille, perangkat IoT.
- **Tampilan imersif**: kacamata AR dan headset VR (Bab 14).

### 3.3 Gaya Interaksi

#### 1. Antarmuka baris perintah (_Command Line Interface_, CLI)

Pengguna mengetik perintah. Kuat dan efisien bagi ahli, tetapi sulit dipelajari karena tidak ada petunjuk visual. Contoh:

```bash
git commit -m "Perbaiki validasi formulir"
```

#### 2. Antarmuka berbasis menu

Pengguna memilih dari daftar pilihan. Mudah dipelajari karena prinsip _recognition over recall_.

#### 3. Isian formulir (_form-fill_)

Pengguna mengisi kolom data. Umum pada sistem informasi, pendaftaran, dan transaksi.

#### 4. Manipulasi langsung (_Direct Manipulation_)

Istilah dari Ben Shneiderman. Pengguna bertindak langsung pada representasi objek, dengan umpan balik segera dan aksi yang dapat dibalik. Contoh: menyeret berkas ke tempat sampah, mencubit untuk memperbesar foto.

Ciri utamanya:

- Objek dan aksi terlihat terus-menerus.
- Tindakan fisik menggantikan sintaks yang rumit.
- Aksi bersifat cepat, bertahap, dan dapat dibalik.

#### 5. WIMP

_Windows, Icons, Menus, Pointer_: paradigma antarmuka grafis desktop.

#### 6. Sentuh dan gestur

Mengetuk, menggeser, mencubit, menekan lama. Masalah umum: gestur yang tersembunyi (tidak terlihat) sehingga sulit ditemukan (_discoverability_).

#### 7. Antarmuka suara (_Voice User Interface_, VUI)

Pengguna berbicara. Cocok untuk situasi tangan sibuk, tetapi tidak memberi petunjuk visual tentang apa yang bisa dikatakan.

#### 8. Antarmuka percakapan dan berbasis bahasa alami

Pengguna mengetik atau berbicara dalam bahasa sehari-hari kepada sistem, termasuk chatbot dan asisten AI. Fleksibel, tetapi menghadirkan masalah baru: apa yang bisa saya minta? seberapa benar jawabannya? (Bab 13).

#### 9. Multimodal dan spasial

Menggabungkan beberapa kanal (suara, sentuh, pandangan, gestur) dan ruang tiga dimensi (Bab 14).

### 3.4 Perbandingan Gaya Interaksi

|Gaya|Kemudahan dipelajari|Efisiensi untuk ahli|Fleksibilitas|Risiko utama|
|---|---|---|---|---|
|Baris perintah|Rendah|Sangat tinggi|Sangat tinggi|Salah ketik, tidak ada petunjuk|
|Menu|Tinggi|Sedang|Sedang|Menu terlalu dalam|
|Formulir|Tinggi|Sedang|Rendah|Formulir panjang dan melelahkan|
|Manipulasi langsung|Tinggi|Tinggi|Sedang|Presisi sulit pada layar kecil|
|Suara|Tinggi|Sedang|Tinggi|Salah pengenalan, privasi|
|Percakapan AI|Tinggi pada awal|Bervariasi|Sangat tinggi|Jawaban salah, kontrol rendah|

### 3.5 Siklus Interaksi dalam Perangkat Lunak

Hampir semua antarmuka modern berbasis peristiwa (_event-driven_). Siklus dasarnya:

```
 Pengguna beraksi
        |
        v
  Peristiwa (event) dibuat oleh sistem: click, keydown, touchstart, ...
        |
        v
  Penangan peristiwa (event handler) dijalankan
        |
        v
  Status (state) aplikasi berubah
        |
        v
  Tampilan dirender ulang  --->  Umpan balik (feedback) dilihat pengguna
        |
        v
  Pengguna menilai hasil dan beraksi lagi
```

Contoh paling sederhana dengan JavaScript:

```html
<button id="simpan">Simpan</button>
<p id="status" role="status"></p>

<script>
  const tombol = document.getElementById("simpan");
  const status = document.getElementById("status");

  tombol.addEventListener("click", async () => {
    tombol.disabled = true;                 // cegah klik ganda
    status.textContent = "Menyimpan...";    // umpan balik segera

    try {
      await simpanKeServer();               // misalnya memanggil API
      status.textContent = "Tersimpan.";    // umpan balik hasil
    } catch (err) {
      status.textContent =
        "Gagal menyimpan. Periksa koneksi Anda lalu coba lagi.";
    } finally {
      tombol.disabled = false;
    }
  });
</script>
```

Perhatikan keputusan IMK di dalam kode: mencegah klik ganda, memberi umpan balik saat proses dan setelah hasil, serta pesan kesalahan yang menyarankan tindakan. Atribut `role="status"` membuat pembaca layar mengumumkan perubahan teks.

### 3.6 Latensi dan Kinerja sebagai Bagian dari UX

Kecepatan adalah fitur. Kinerja yang buruk dirasakan sebagai desain yang buruk. Teknik yang membantu:

- **Umpan balik optimistis** (_optimistic UI_): tampilkan hasil segera lalu sinkronkan dengan server, dan tangani kegagalan dengan jelas.
- **Kerangka pemuatan** (_skeleton screen_): menampilkan bentuk konten sementara data dimuat.
- **Pemuatan bertahap** (_lazy loading_) untuk gambar dan komponen berat.
- **Pemrosesan di latar belakang** untuk tugas panjang, disertai notifikasi saat selesai.

### Ringkasan Bab 3

- Perangkat masukan dan keluaran memiliki kelebihan dan batasan; pilih sesuai pengguna dan konteks.
- Gaya interaksi berkembang dari baris perintah hingga percakapan dan spasial, tanpa saling menggantikan sepenuhnya.
- Antarmuka modern bersifat berbasis peristiwa, dan setiap tindakan pengguna perlu mendapat umpan balik.

### Latihan Bab 3

1. Pilih gaya interaksi yang paling cocok untuk (a) pengemudi yang ingin menelepon, (b) administrator server yang mengelola ratusan mesin, (c) nenek yang ingin mengirim foto ke cucu. Jelaskan alasannya.
2. Mengapa pada layar sentuh tidak bisa mengandalkan efek _hover_ untuk menampilkan informasi penting?
3. Pada contoh kode 3.5, apa yang terjadi jika baris `tombol.disabled = true` dihapus? Dampaknya bagi pengguna?
4. Sebutkan dua contoh antarmuka manipulasi langsung selain yang disebutkan di buku ini.

---

## Bab 4. Model Mental dan Prinsip Dasar Norman

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjelaskan model mental, model konseptual, dan citra sistem.
2. Menjelaskan _gulf of execution_ dan _gulf of evaluation_.
3. Menerapkan konsep _affordance_, _signifier_, _mapping_, _feedback_, dan _constraint_.
4. Membedakan _slip_ dan _mistake_ serta merancang pencegahannya.

Bab ini bersandar pada gagasan Don Norman dalam bukunya _The Design of Everyday Things_.

### 4.1 Tiga Model dalam Satu Interaksi

```
 Model konseptual           Citra sistem              Model mental
 (rancangan desainer)  -->  (apa yang tampak     -->  (pemahaman pengguna
                             dan terasa)                tentang cara kerja)
```

- **Model konseptual** (_conceptual model_): cara desainer dan pengembang membayangkan sistem bekerja.
- **Citra sistem** (_system image_): semua yang pengguna lihat dan alami: tampilan, label, perilaku, dokumentasi.
- **Model mental** (_mental model_): bayangan di kepala pengguna tentang bagaimana sistem bekerja.

Masalah timbul ketika model mental pengguna tidak cocok dengan cara sistem benar-benar bekerja. Contoh: pengguna mengira tombol "Tutup" pada aplikasi catatan akan menyimpan, padahal tidak. Pengguna bukan "bodoh"; citra sistem gagal membangun model mental yang benar.

### 4.2 Dua Jurang Interaksi

Norman menggambarkan dua kesenjangan yang harus dijembatani desain:

|Jurang|Pertanyaan pengguna|Cara menjembatani|
|---|---|---|
|**Jurang pelaksanaan** (_gulf of execution_)|Bagaimana cara saya melakukan ini? Aksi apa yang tersedia?|Petunjuk yang jelas, kontrol yang terlihat, pola yang sudah dikenal|
|**Jurang evaluasi** (_gulf of evaluation_)|Apa yang terjadi? Apakah berhasil?|Umpan balik jelas, status terlihat, hasil mudah dipahami|

Desain yang baik membuat kedua jurang itu sempit.

### 4.3 Tujuh Tahap Aksi

Norman membagi satu siklus aksi pengguna menjadi tujuh tahap:

1. Membentuk **tujuan** ("saya ingin mengirim foto").
2. Membentuk **niat** ("saya akan memakai aplikasi pesan").
3. Menyusun **urutan aksi** ("buka obrolan, tekan ikon klip, pilih foto, kirim").
4. **Melakukan** aksi.
5. **Mempersepsi** keadaan dunia (apa yang tampak di layar).
6. **Menafsirkan** apa artinya.
7. **Mengevaluasi** apakah tujuan tercapai.

Tahap 1 sampai 4 adalah sisi pelaksanaan, tahap 5 sampai 7 sisi evaluasi. Saat pengguna macet, tanyakan di tahap mana ia macet.

### 4.4 Konsep Kunci

#### Affordance dan Signifier

- **Affordance** adalah hubungan antara sifat sebuah objek dan kemampuan pelaku: apa yang _mungkin dilakukan_. Kursi memberi affordance untuk duduk. Layar sentuh memberi affordance untuk disentuh.
- **Signifier** adalah **petunjuk** yang menunjukkan di mana dan bagaimana aksi dilakukan. Tombol berbayangan, ikon tarik pada sudut jendela, atau teks "Seret berkas ke sini" adalah signifier.

Pada layar, affordance sering ada (semua piksel bisa disentuh), sehingga yang menentukan adalah signifier. Teks biru bergaris bawah dikenali sebagai tautan karena signifier.

Contoh buruk: gestur geser (_swipe_) untuk menghapus item tanpa petunjuk apa pun. Perbaikan: tampilkan ikon atau animasi singkat sebagai petunjuk, dan sediakan juga cara alternatif (menu "Hapus").

#### Pemetaan (_Mapping_)

Hubungan antara kontrol dan efeknya. Pemetaan alami memanfaatkan analogi ruang. Contoh: kompor dengan empat tungku dan empat kenop yang disusun sama persis dengan susunan tungku. Pada antarmuka: penggeser (_slider_) volume ke kanan menaikkan volume; tombol panah sesuai arah geseran konten.

#### Umpan Balik (_Feedback_)

Setiap tindakan pengguna perlu respons yang jelas dan segera: perubahan visual, suara, atau getaran. Tanpa umpan balik, pengguna mengulang aksi (menekan tombol bayar dua kali) atau ragu apakah sistem bekerja.

Umpan balik yang baik bersifat: segera, informatif, sesuai skala (aksi kecil, umpan balik kecil), dan tidak mengganggu.

#### Batasan (_Constraints_)

Pembatas yang mencegah aksi yang keliru:

- **Fisik**: colokan USB-C bisa dimasukkan dari dua arah, sedangkan colokan lama hanya satu arah.
- **Logis**: tidak bisa memilih tanggal pulang sebelum tanggal berangkat.
- **Semantik dan budaya**: konvensi (merah berarti berhenti atau bahaya).
- **Pemaksa** (_forcing function_): sistem tidak mengizinkan lanjut sampai syarat dipenuhi, misalnya dialog konfirmasi sebelum menghapus.

#### Kemudahan Ditemukan (_Discoverability_)

Apakah pengguna bisa menemukan aksi apa yang tersedia dan bagaimana melakukannya? Fitur yang tersembunyi di balik gestur atau menu dalam bernilai nol bagi pengguna yang tidak pernah menemukannya.

### 4.5 Kesalahan Manusia: Slip dan Mistake

Norman membedakan dua jenis kesalahan:

|Jenis|Penyebab|Contoh|Pencegahan|
|---|---|---|---|
|**Slip**|Niat benar, pelaksanaan salah (kurang perhatian)|Menekan tombol yang salah karena berdekatan; salah ketik|Jarak antar tombol, konfirmasi, fitur urungkan (_undo_), validasi masukan|
|**Mistake**|Niat atau rencana salah (pemahaman salah)|Mengira "Arsipkan" sama dengan "Simpan"|Label jelas, model mental yang benar, pratinjau, bantuan kontekstual|

Prinsip praktis: **jangan menyalahkan pengguna**. Anggap setiap kesalahan sebagai informasi bahwa desain belum cukup membantu. Rancang agar kesalahan **sulit dibuat dan mudah dipulihkan**.

### 4.6 Studi Kasus Mini: Pesan Kesalahan

**Versi buruk:**

```
Error 4002: Invalid input.
```

**Versi lebih baik:**

```
Nomor ponsel belum lengkap. Masukkan 10 sampai 13 digit,
contoh: 0812 3456 7890.
```

Perbandingan:

|Aspek|Buruk|Baik|
|---|---|---|
|Bahasa|Kode teknis, istilah internal|Bahasa sehari-hari|
|Diagnosis|Tidak jelas apa yang salah|Menyebut persis masalahnya|
|Solusi|Tidak ada|Memberi contoh format benar|
|Nada|Menyalahkan|Netral dan membantu|

### Ringkasan Bab 4

- Pengguna bertindak berdasarkan model mental mereka; tugas desain adalah membentuk model mental yang benar melalui citra sistem.
- Jurang pelaksanaan dan jurang evaluasi harus dijembatani dengan petunjuk dan umpan balik.
- Affordance, signifier, mapping, feedback, dan constraint adalah perangkat utama desain interaksi.
- Rancang agar kesalahan sulit terjadi dan mudah dipulihkan.

### Latihan Bab 4

1. Jelaskan perbedaan affordance dan signifier dengan contoh pada antarmuka web.
2. Sebuah aplikasi menghapus data tanpa konfirmasi dan tanpa tombol urungkan. Klasifikasikan risikonya (slip atau mistake) dan usulkan dua perbaikan.
3. Tulis ulang pesan kesalahan berikut agar lebih baik: "Gagal. Kode 500."
4. Ambil satu aplikasi yang Anda pakai. Identifikasi satu contoh pemetaan yang baik dan satu yang buruk.
5. Dalam tujuh tahap aksi, pada tahap mana pengguna paling mungkin macet jika tombol tidak tampak seperti tombol?

---

## Bab 5. Heuristik dan Pedoman Desain

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menerapkan sepuluh heuristik usabilitas Nielsen.
2. Menerapkan delapan aturan emas Shneiderman.
3. Mengenali pola antarmuka umum dan pedoman platform.
4. Menulis mikroteks (teks antarmuka) yang jelas.

### 5.1 Sepuluh Heuristik Usabilitas Nielsen

_Heuristik_ adalah aturan praktis berdasarkan pengalaman, bukan hukum yang kaku. Sepuluh heuristik Jakob Nielsen (1994) masih dipakai luas sebagai daftar periksa evaluasi.

|No.|Heuristik|Penjelasan|Contoh baik|Contoh buruk|
|---|---|---|---|---|
|1|**Visibilitas status sistem**|Pengguna selalu tahu apa yang terjadi|Bilah kemajuan saat mengunggah berkas|Tombol ditekan tetapi layar diam|
|2|**Kesesuaian sistem dengan dunia nyata**|Pakai bahasa dan konsep yang dikenal pengguna|Ikon keranjang untuk belanja|Istilah teknis internal pada label|
|3|**Kontrol dan kebebasan pengguna**|Sediakan "pintu darurat": urungkan, batal, kembali|Tombol "Urungkan" setelah menghapus pesan|Tidak bisa keluar dari alur pendaftaran|
|4|**Konsistensi dan standar**|Hal sama tampak dan bekerja sama; ikuti konvensi platform|Tombol "Simpan" selalu di posisi sama|Satu halaman memakai "Kirim", halaman lain "Submit", halaman lain "Oke" untuk aksi sama|
|5|**Pencegahan galat**|Cegah masalah sebelum terjadi|Memblokir tanggal yang tidak valid pada kalender|Membiarkan pengguna mengirim formulir lalu menolak seluruhnya|
|6|**Mengenali daripada mengingat**|Kurangi beban ingatan; tampilkan pilihan|Riwayat pencarian dan saran otomatis|Meminta pengguna mengingat kode dari layar sebelumnya|
|7|**Fleksibilitas dan efisiensi pemakaian**|Melayani pemula dan ahli|Pintasan papan ketik, aksi cepat|Hanya ada jalur panjang untuk semua pengguna|
|8|**Desain estetis dan minimalis**|Hilangkan informasi yang tidak perlu|Halaman fokus pada satu aksi utama|Halaman penuh banner dan pop-up|
|9|**Bantu pengguna mengenali, mendiagnosis, dan pulih dari galat**|Pesan galat jelas dan membantu|"Kata sandi minimal 8 karakter"|"Terjadi kesalahan"|
|10|**Bantuan dan dokumentasi**|Bantuan mudah dicari, singkat, dan kontekstual|Teks bantuan di samping kolom yang rumit|Panduan PDF 100 halaman terpisah|

### 5.2 Delapan Aturan Emas Shneiderman

Ben Shneiderman merumuskan delapan aturan yang beririsan dengan heuristik Nielsen:

1. **Berusaha konsisten** pada urutan aksi, istilah, dan tampilan.
2. **Kejar kegunaan universal**: layani pemula dan ahli, beragam usia dan kemampuan.
3. **Beri umpan balik yang informatif** untuk setiap aksi.
4. **Rancang dialog yang berujung penutupan** (_closure_): urutan aksi punya awal, tengah, dan akhir yang jelas.
5. **Cegah galat**; jika terjadi, beri penanganan sederhana.
6. **Izinkan pembalikan aksi dengan mudah**.
7. **Beri pengguna rasa kendali** (_internal locus of control_).
8. **Kurangi beban ingatan jangka pendek**.

Perhatikan kesamaannya dengan Nielsen. Dua pakar dari dua jalur berbeda sampai pada kesimpulan yang mirip, yang menunjukkan prinsip-prinsip ini kuat.

### 5.3 Pedoman Platform

Platform besar menerbitkan pedoman desain resmi yang membantu konsistensi dengan ekosistemnya:

|Pedoman|Pemilik|Fokus|
|---|---|---|
|Material Design|Google|Android dan web|
|Human Interface Guidelines|Apple|iOS, iPadOS, macOS, dan platform Apple lain|
|Fluent Design|Microsoft|Windows dan aplikasi Microsoft|

Mengikuti pedoman platform memanfaatkan **Hukum Jakob**: pengguna sudah tahu cara kerjanya. Pedoman ini diperbarui berkala, jadi selalu rujuk versi terbaru di situs resminya.

### 5.4 Pola Antarmuka Umum

|Pola|Fungsi|Hal yang perlu diperhatikan|
|---|---|---|
|Navigasi utama|Berpindah antar bagian|Maksimal sekitar 5 sampai 7 tujuan utama; label jelas; posisi konsisten|
|Pencarian|Menemukan konten cepat|Toleran salah ketik, beri saran, tangani "tidak ada hasil"|
|Formulir|Mengumpulkan data|Label di atas kolom, validasi bertahap, tunjukkan kolom wajib|
|Daftar dan tabel|Menampilkan banyak data|Urut, saring, paginasi atau gulir tak berujung dengan hati-hati|
|Modal (dialog)|Meminta keputusan penting|Jangan berlebihan; fokus keyboard pindah ke dialog dan kembali ketika ditutup|
|Notifikasi|Memberi kabar|Jangan membanjiri; beri kontrol kepada pengguna|
|Keadaan kosong (_empty state_)|Layar tanpa data|Jelaskan dan beri ajakan aksi, bukan layar kosong|
|Onboarding|Memperkenalkan produk|Singkat, bisa dilewati, ajarkan dengan melakukan|

### 5.5 Menulis Mikroteks yang Baik

Teks kecil pada antarmuka (_microcopy_) sangat memengaruhi usabilitas.

Panduan:

- Pakai **kata kerja yang spesifik** pada tombol: "Simpan perubahan", bukan "Oke".
- Pakai bahasa pengguna, bukan bahasa sistem: "Kata sandi salah", bukan "Autentikasi gagal".
- Jelaskan **apa yang terjadi** dan **apa yang bisa dilakukan**.
- Jaga nada konsisten: sopan, jelas, tidak menyalahkan, tidak berlebihan.
- Perhatikan bahasa: tentukan apakah memakai "Anda" atau "kamu" lalu konsisten.

Contoh:

|Kurang baik|Lebih baik|
|---|---|
|"Anda yakin?"|"Hapus 3 foto ini secara permanen?" dengan tombol "Hapus" dan "Batal"|
|"Submit"|"Kirim pesanan"|
|"Terjadi kesalahan."|"Pesanan belum terkirim karena koneksi terputus. Coba lagi."|

### Ringkasan Bab 5

- Heuristik Nielsen dan aturan emas Shneiderman adalah alat evaluasi dan desain yang praktis dan tahan lama.
- Pedoman platform membantu menjaga konsistensi dengan harapan pengguna.
- Mikroteks yang spesifik, manusiawi, dan membantu sering menjadi perbaikan UX termurah dengan dampak besar.

### Latihan Bab 5

1. Pilih tiga heuristik Nielsen, lalu cari satu pelanggarannya pada aplikasi atau situs yang Anda kenal.
2. Perbaiki mikroteks: tombol "Yes" dan "No" pada dialog "Apakah Anda ingin keluar tanpa menyimpan?"
3. Mengapa konsistensi dengan aplikasi lain (konsistensi eksternal) penting, dan kapan boleh melanggarnya?
4. Rancang desain _empty state_ untuk halaman "Riwayat Pesanan" pada aplikasi belanja yang pengguna barunya belum punya pesanan.

---

## Bab 6. Proses Desain Berpusat pada Pengguna

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjelaskan siklus desain berpusat pada pengguna.
2. Membedakan beberapa kerangka kerja: Double Diamond, Design Thinking, Lean UX, Design Sprint.
3. Mengaitkan proses IMK dengan pengembangan perangkat lunak agile.
4. Menulis _user story_ dan kriteria penerimaan sederhana.

### 6.1 Desain Berpusat pada Pengguna

Standar ISO 9241-210 menggambarkan proses desain berpusat pada manusia sebagai siklus yang berulang:

```
   +---------------------------------+
   | 1. Pahami konteks pemakaian     |
   +---------------------------------+
                  |
                  v
   +---------------------------------+
   | 2. Tentukan kebutuhan pengguna  |
   +---------------------------------+
                  |
                  v
   +---------------------------------+
   | 3. Hasilkan solusi desain       |
   +---------------------------------+
                  |
                  v
   +---------------------------------+
   | 4. Evaluasi terhadap kebutuhan  |-----+
   +---------------------------------+     |
                  ^                         |
                  +---- ulangi sampai ------+
                        memenuhi kebutuhan
```

Kuncinya ada pada tiga kata: **berpusat pada pengguna**, **iteratif**, dan **berbasis bukti**.

### 6.2 Kerangka Kerja Populer

#### Double Diamond

Dari Design Council (Inggris). Dua "berlian": satu untuk memahami masalah yang tepat, satu lagi untuk membangun solusi yang tepat. Setiap berlian melebar (diverge: mengeksplorasi banyak kemungkinan) lalu menyempit (converge: memilih).

```
  Temukan      Definisikan      Kembangkan      Hantarkan
 (Discover)      (Define)       (Develop)       (Deliver)
   /\    \      /    \/\           /\    \         /    \/
  /  \    \    /       \         /  \    \       /
 /    \    \  /         \       /    \    \     /
 melebar      menyempit         melebar     menyempit
 (riset)      (masalah)         (ide)       (solusi)
```

#### Design Thinking

Lima tahap yang populer dari d.school Stanford: _empathize_ (berempati), _define_ (mendefinisikan), _ideate_ (menggagas), _prototype_ (membuat prototipe), _test_ (menguji). Tahapnya tidak harus linear dan bisa kembali ke tahap sebelumnya.

#### Lean UX

Mengurangi dokumentasi berat dan lebih fokus pada hipotesis, eksperimen cepat, dan pembelajaran. Kerangkanya: _Think, Make, Check_.

#### Design Sprint

Proses lima hari dari Google Ventures untuk menjawab pertanyaan penting lewat prototipe dan uji pengguna: Peta, Sketsa, Putuskan, Prototipe, Uji.

### 6.3 IMK dalam Tim Agile

Dalam pengembangan agile, desain dan riset tidak berhenti sebelum coding. Pola yang umum:

- **Riset dan desain terus-menerus** di depan sprint pengembangan (_dual-track agile_).
- **Desainer dan developer** berdiskusi sejak awal tentang kelayakan teknis.
- **Sistem desain** (_design system_) membantu konsistensi dan kecepatan.
- **Uji usabilitas ringan** pada tiap sprint atau dua sprint.

Peran dalam tim produk digital:

|Peran|Tanggung jawab utama|
|---|---|
|Peneliti pengguna (_UX researcher_)|Memahami pengguna, merancang dan menjalankan riset|
|Desainer UX/produk|Alur, struktur, interaksi, prototipe|
|Desainer visual/UI|Tampilan, komponen, sistem desain|
|Penulis UX (_UX writer_)|Mikroteks dan konsistensi bahasa|
|Manajer produk|Prioritas, tujuan bisnis|
|Engineer (frontend dan backend)|Implementasi, kinerja, aksesibilitas pada kode|
|Pakar aksesibilitas|Memastikan kepatuhan dan kegunaan bagi semua|

Di perusahaan kecil, satu orang bisa memegang beberapa peran.

### 6.4 Dari Kebutuhan ke Cerita Pengguna

**Cerita pengguna** (_user story_) menuliskan kebutuhan dari sudut pandang pengguna:

```
Sebagai [jenis pengguna],
saya ingin [melakukan sesuatu],
agar [mendapat manfaat tertentu].
```

Contoh:

```
Sebagai mahasiswa,
saya ingin memperpanjang peminjaman buku dari ponsel,
agar tidak terkena denda keterlambatan.
```

**Kriteria penerimaan** (_acceptance criteria_) membuat cerita itu dapat diuji:

```
Diberikan saya memiliki buku yang masih dipinjam dan belum melewati tenggat,
Ketika saya menekan "Perpanjang",
Maka tenggat bertambah 7 hari dan saya melihat konfirmasi
     dengan tanggal baru.

Diberikan buku sudah ditandai dipesan orang lain,
Ketika saya menekan "Perpanjang",
Maka saya melihat pesan yang menjelaskan alasan penolakan
     dan alternatif tindakan.
```

Perhatikan kriteria kedua yang menangani kasus tepi, tempat banyak masalah UX tersembunyi.

### 6.5 Kesalahan Proses yang Sering Terjadi

- Langsung membuat solusi tanpa memahami masalah.
- Mendesain untuk diri sendiri ("saya suka, berarti pengguna suka").
- Riset hanya untuk membenarkan keputusan yang sudah dibuat.
- Menguji terlalu terlambat, saat perubahan sudah mahal.
- Menganggap desain selesai begitu dirilis.

### Ringkasan Bab 6

- Desain berpusat pada pengguna bersifat iteratif: pahami, tentukan, rancang, evaluasi, ulangi.
- Double Diamond, Design Thinking, Lean UX, dan Design Sprint adalah kerangka kerja berbeda dengan semangat sama.
- Dalam tim agile, riset dan desain berjalan bersama pengembangan, bukan sebelum atau sesudahnya.

### Latihan Bab 6

1. Gambarkan siklus desain berpusat pada pengguna untuk proyek "aplikasi antrean klinik kampus". Tuliskan satu kegiatan pada tiap tahap.
2. Tulis dua _user story_ beserta kriteria penerimaannya untuk fitur "Reset kata sandi".
3. Apa perbedaan tahap "diverge" dan "converge"? Mengapa keduanya diperlukan?
4. Sebutkan tiga alasan mengapa pengujian dini lebih murah daripada pengujian setelah rilis.

---

## Bab 7. Riset Pengguna

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Membedakan riset kualitatif dan kuantitatif, generatif dan evaluatif.
2. Merencanakan dan menjalankan wawancara pengguna dasar.
3. Menyusun persona, peta empati, dan peta perjalanan pengguna.
4. Menjalankan riset secara etis.

### 7.1 Jenis-Jenis Riset

|Dimensi|Penjelasan|Contoh pertanyaan|
|---|---|---|
|**Kualitatif**|Menjawab "mengapa" dan "bagaimana"; data berupa cerita, perilaku|Mengapa pengguna berhenti di langkah pembayaran?|
|**Kuantitatif**|Menjawab "berapa banyak"; data berupa angka|Berapa persen pengguna menyelesaikan pembayaran?|
|**Generatif** (_discovery_)|Menggali kebutuhan sebelum atau saat merancang|Apa yang sulit saat mahasiswa mencari ruang belajar?|
|**Evaluatif**|Menguji solusi yang sudah ada atau prototipe|Apakah pengguna bisa memesan ruang dengan prototipe ini?|

Kedua jenis data saling melengkapi. Analitik menunjukkan **apa** yang terjadi; wawancara dan pengamatan menjelaskan **mengapa**.

### 7.2 Metode Riset Umum

|Metode|Apa itu|Kapan dipakai|
|---|---|---|
|Wawancara|Percakapan terarah satu per satu|Memahami motivasi, kebiasaan, masalah|
|Pengamatan lapangan / _contextual inquiry_|Mengamati pengguna di lingkungan sebenarnya|Memahami alur kerja nyata|
|Survei (kuesioner)|Pertanyaan terstruktur ke banyak orang|Mengukur sikap atau preferensi dalam skala besar|
|Studi diari (_diary study_)|Pengguna mencatat pengalaman selama beberapa hari|Memahami pengalaman jangka panjang|
|_Card sorting_|Pengguna mengelompokkan kartu topik|Merancang struktur menu dan kategori|
|Analisis kompetitor|Menelaah produk pesaing|Memahami standar pasar dan peluang|
|Analitik produk|Menganalisis data perilaku|Menemukan titik pengguna berhenti|
|Uji usabilitas|Pengguna mencoba tugas di produk atau prototipe|Mengevaluasi desain (Bab 10)|

### 7.3 Wawancara Pengguna: Panduan Praktis

**Persiapan**

1. Tentukan tujuan riset dalam satu atau dua kalimat. Contoh: "Memahami bagaimana mahasiswa mencari dan memesan ruang belajar."
2. Tentukan siapa yang diwawancarai (kriteria rekrutmen).
3. Siapkan panduan wawancara (maksimal sekitar 8 sampai 10 pertanyaan utama).
4. Siapkan lembar persetujuan (_informed consent_).

**Saat wawancara**

- Mulai dengan perkenalan dan pertanyaan ringan.
- Gunakan pertanyaan terbuka: "Ceritakan terakhir kali Anda mencari ruang belajar."
- Minta cerita tentang **perilaku nyata di masa lalu**, bukan opini hipotetis.
- Gunakan pertanyaan lanjutan: "Bisa ceritakan lebih lanjut?", "Apa yang terjadi setelah itu?", "Mengapa begitu?"
- Diam sejenak setelah jawaban; sering kali pengguna menambah informasi berharga.
- Jangan menggiring.

**Pertanyaan menggiring vs netral**

|Menggiring (hindari)|Netral (gunakan)|
|---|---|
|"Apakah aplikasi ini mudah dipakai?"|"Bagaimana pengalaman Anda memakai aplikasi ini?"|
|"Anda pasti suka fitur ini, kan?"|"Apa pendapat Anda tentang fitur ini?"|
|"Apakah Anda akan memakai fitur ini?"|"Kapan terakhir kali Anda melakukan hal serupa? Ceritakan."|

Orang cenderung terlalu optimis memprediksi perilaku mereka sendiri dan bersikap sopan. Karena itu, perilaku masa lalu lebih dapat dipercaya daripada janji masa depan.

### 7.4 Berapa Banyak Partisipan?

- Untuk riset kualitatif, pola dan tema baru sering mulai berulang setelah sekitar 5 sampai 10 wawancara dari kelompok pengguna yang serupa. Jumlah pastinya bergantung pada keragaman pengguna dan tujuan riset.
- Untuk survei, jumlah responden mengikuti kebutuhan statistik, biasanya puluhan sampai ratusan atau lebih.

### 7.5 Sintesis: Dari Data ke Wawasan

Data mentah perlu diolah menjadi wawasan (_insight_).

**Diagram afinitas** (_affinity diagram_): tulis setiap temuan pada satu catatan, kelompokkan yang serupa, beri nama tiap kelompok. Tema yang muncul menjadi dasar wawasan.

**Peta empati** (_empathy map_): ringkasan apa yang pengguna _katakan_, _pikirkan_, _lakukan_, dan _rasakan_.

**Persona**: representasi fiktif tetapi berbasis data dari kelompok pengguna.

Contoh persona singkat:

```
Nama        : Rani, 20 tahun, mahasiswa semester 4
Tujuan      : Mendapat ruang belajar tenang menjelang ujian
Hambatan    : Ruang cepat penuh; tidak tahu ketersediaan real-time
Perangkat   : Ponsel Android kelas menengah, kuota terbatas
Perilaku    : Mengecek ketersediaan sambil berjalan ke perpustakaan
Kutipan     : "Aku sering sudah sampai ternyata penuh."
```

Persona harus berbasis data riset, bukan karangan. Persona tanpa dasar data berbahaya karena memberi rasa pasti yang palsu.

**Peta perjalanan pengguna** (_user journey map_): menguraikan langkah, pikiran, emosi, dan titik masalah pengguna sepanjang mencapai tujuan.

|Tahap|Mencari ruang|Memesan|Datang|Memakai|Selesai|
|---|---|---|---|---|---|
|Tindakan|Membuka aplikasi|Memilih jam dan ruang|Menunjukkan kode pesanan|Belajar|Meninggalkan ruang|
|Pikiran|"Ada yang kosong tidak ya?"|"Semoga tidak gagal"|"Kodenya bisa dibaca petugas?"|"Tenang juga"|"Perlu dibersihkan dulu?"|
|Emosi|Cemas|Ragu|Lega|Puas|Netral|
|Masalah|Informasi tidak real-time|Formulir panjang|Kode tidak tampil saat offline|-|Tidak ada pengingat batas waktu|
|Peluang|Tampilkan status real-time|Sederhanakan langkah|Simpan kode untuk akses offline|-|Kirim pengingat|

### 7.6 Etika Riset

- **Persetujuan yang diinformasikan**: jelaskan tujuan, apa yang direkam, bagaimana data dipakai, dan bahwa partisipan boleh berhenti kapan saja.
- **Privasi dan data pribadi**: kumpulkan seperlunya, simpan aman, anonimkan. Di Indonesia, perlindungan data pribadi diatur dalam Undang-Undang Nomor 27 Tahun 2022 tentang Pelindungan Data Pribadi.
- **Tidak merugikan**: jangan menekan partisipan; hati-hati pada topik sensitif.
- **Kompensasi yang pantas** bila memungkinkan.
- **Keterbukaan**: jangan menipu partisipan tentang tujuan riset tanpa alasan yang sah dan pemberitahuan sesudahnya.

### Ringkasan Bab 7

- Riset menggabungkan metode kualitatif dan kuantitatif, generatif dan evaluatif.
- Wawancara yang baik menggali perilaku nyata dengan pertanyaan terbuka dan tidak menggiring.
- Sintesis mengubah data menjadi wawasan melalui diagram afinitas, persona, dan peta perjalanan.
- Etika dan perlindungan data pribadi adalah syarat, bukan tambahan.

### Latihan Bab 7

1. Ubah pertanyaan menggiring berikut menjadi netral: "Bukankah fitur favorit lebih memudahkan Anda?"
2. Rancang lima pertanyaan wawancara untuk memahami bagaimana mahasiswa mengatur jadwal kuliah.
3. Mengapa persona harus berbasis data? Apa risikonya bila tidak?
4. Buat peta perjalanan singkat (lima tahap) untuk "mengurus surat keterangan aktif kuliah secara daring".

---

## Bab 8. Desain Visual dan Tata Letak

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menerapkan hierarki visual dan prinsip Gestalt.
2. Memilih tipografi, warna, dan jarak secara sistematis.
3. Merancang tata letak yang responsif.
4. Memahami sistem desain dan token desain.

### 8.1 Hierarki Visual

**Hierarki visual** mengarahkan mata pengguna pada hal yang paling penting terlebih dahulu. Alat utamanya:

- **Ukuran**: lebih besar tampak lebih penting.
- **Kontras**: warna dan ketebalan yang kontras menarik perhatian.
- **Posisi**: atas dan kiri biasanya dibaca lebih dahulu pada bahasa dengan arah baca kiri ke kanan.
- **Jarak kosong** (_white space_): ruang di sekitar elemen memberinya penekanan dan memudahkan membaca.
- **Pengelompokan**: elemen berdekatan dianggap berhubungan.

Uji sederhana: **uji menyipitkan mata** (_squint test_). Buramkan pandangan Anda pada layar. Apa yang masih menonjol? Itu seharusnya hal terpenting.

### 8.2 Prinsip Gestalt

Psikologi Gestalt menjelaskan bagaimana otak mengelompokkan elemen visual:

|Prinsip|Penjelasan|Penerapan|
|---|---|---|
|Kedekatan (_proximity_)|Elemen berdekatan dianggap satu kelompok|Label dekat kolomnya, jauh dari kolom lain|
|Kemiripan (_similarity_)|Elemen serupa dianggap sejenis|Semua tautan memakai gaya sama|
|Kesinambungan (_continuity_)|Mata mengikuti garis atau alur|Penyelarasan elemen dalam baris atau kolom|
|Penutupan (_closure_)|Otak melengkapi bentuk tidak utuh|Ikon sederhana tetap dikenali|
|Figur dan latar (_figure-ground_)|Memisahkan objek utama dari latar|Modal dengan latar redup|
|Wilayah bersama (_common region_)|Elemen dalam satu kotak dianggap satu kelompok|Kartu (_card_)|
|Keterhubungan (_connectedness_)|Elemen yang terhubung garis dianggap berkaitan|Langkah-langkah yang dihubungkan garis|

### 8.3 Tata Letak dan Jarak

- Gunakan **grid** (misalnya 12 kolom) agar rapi dan konsisten.
- Gunakan **skala jarak** yang konsisten, misalnya kelipatan 4 atau 8 piksel: 4, 8, 16, 24, 32, 48. Konsistensi lebih penting daripada angka tertentu.
- Beri **margin dan padding** yang cukup.
- Pola membaca: pengguna sering memindai (_scan_) halaman, bukan membaca kata demi kata. Gunakan judul, subjudul, dan poin-poin.

### 8.4 Tipografi

Teks adalah komponen terbesar sebagian besar antarmuka.

Panduan praktis untuk web:

|Aspek|Saran umum|
|---|---|
|Ukuran teks isi|Sekitar 16 piksel (1rem) atau lebih|
|Tinggi baris (_line-height_)|Sekitar 1,4 sampai 1,6 kali ukuran huruf untuk paragraf|
|Panjang baris|Sekitar 45 sampai 75 karakter agar nyaman dibaca|
|Jumlah jenis huruf|1 sampai 2 keluarga huruf|
|Penekanan|Gunakan ketebalan, bukan huruf kapital semua atau garis bawah (tautan memakai garis bawah)|
|Perataan|Rata kiri untuk paragraf pada bahasa dengan arah kiri ke kanan|

Gunakan satuan relatif (`rem`, `em`) agar teks mengikuti pengaturan ukuran huruf pengguna, bukan satuan tetap yang mengabaikannya.

### 8.5 Warna

Warna menyampaikan makna, menciptakan hierarki, dan membangun merek, tetapi harus dipakai dengan hati-hati.

- **Kontras**: pastikan rasio kontras teks terhadap latar memenuhi standar aksesibilitas (Bab 11).
- **Jangan mengandalkan warna saja** untuk menyampaikan informasi.
- **Makna budaya**: warna bisa bermakna berbeda antar budaya. Putih dikaitkan dengan duka di sebagian budaya dan dengan kesucian di budaya lain. Uji dengan pengguna lokal.
- **Palet terbatas**: satu warna utama, satu atau dua warna aksen, warna netral, dan warna status (sukses, peringatan, galat, informasi).
- **Mode gelap** (_dark mode_): bukan sekadar membalik warna. Kontras, saturasi, dan bayangan perlu diatur ulang. Sediakan sebagai pilihan dan hormati preferensi sistem pengguna.

### 8.6 Ikon dan Gambar

- Ikon yang universal (rumah, cari, tutup) dapat dikenali tanpa label. Ikon yang kurang umum membutuhkan **label teks**.
- Gunakan gaya ikon yang konsisten (ketebalan garis, sudut, ukuran).
- Gambar yang bermakna perlu **teks alternatif** (Bab 11). Gambar dekoratif ditandai agar diabaikan pembaca layar.
- Optimalkan ukuran gambar agar halaman cepat dimuat, penting bagi pengguna dengan kuota dan jaringan terbatas.

### 8.7 Desain Responsif

**Desain responsif** (_responsive design_) membuat tampilan menyesuaikan ukuran layar. Pendekatan _mobile-first_ mulai dari layar kecil lalu menambah kompleksitas untuk layar besar.

Contoh CSS dasar:

```css
/* Dasar: berlaku untuk semua ukuran, mulai dari layar kecil */
.kartu-daftar {
  display: grid;
  grid-template-columns: 1fr;
  gap: 16px;
  padding: 16px;
}

/* Layar menengah ke atas */
@media (min-width: 768px) {
  .kartu-daftar {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Layar lebar */
@media (min-width: 1100px) {
  .kartu-daftar {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

Hal lain yang perlu diperhatikan: orientasi layar, lipat layar (_foldable_), mode terpisah (_split view_), zoom teks sampai 200 persen tanpa konten terpotong.

### 8.8 Gerak dan Animasi

Animasi yang baik menjelaskan perubahan, memberi umpan balik, dan menjaga kesinambungan. Animasi yang berlebihan mengganggu dan bisa memicu pusing pada sebagian orang.

- Durasi umum untuk transisi antarmuka: sekitar 100 sampai 500 milidetik, tergantung jarak dan kompleksitas.
- Hormati preferensi **kurangi gerak** (_reduce motion_) di sistem operasi:

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

### 8.9 Sistem Desain dan Token Desain

**Sistem desain** (_design system_) adalah kumpulan komponen yang dapat dipakai ulang, aturan, dan pedoman yang menjaga konsistensi produk. Isinya biasanya: prinsip, token, komponen, pola, dan panduan penulisan.

**Token desain** (_design tokens_) adalah nilai desain bernama, seperti warna dan jarak, yang menjadi satu sumber kebenaran. Contoh dengan variabel CSS:

```css
:root {
  /* Warna */
  --warna-utama: #1a5fb4;
  --warna-teks: #1f2328;
  --warna-latar: #ffffff;
  --warna-galat: #b42318;

  /* Jarak */
  --jarak-1: 4px;
  --jarak-2: 8px;
  --jarak-3: 16px;
  --jarak-4: 24px;

  /* Tipografi */
  --ukuran-dasar: 1rem;
  --tinggi-baris: 1.5;
}

@media (prefers-color-scheme: dark) {
  :root {
    --warna-teks: #e6edf3;
    --warna-latar: #0d1117;
    --warna-utama: #79b8ff;
    --warna-galat: #ff7b72;
  }
}

.tombol-utama {
  background: var(--warna-utama);
  color: var(--warna-latar);
  padding: var(--jarak-2) var(--jarak-3);
  border-radius: 8px;
  font-size: var(--ukuran-dasar);
}
```

Manfaat: mengubah satu nilai memperbarui seluruh antarmuka, memudahkan mode gelap dan tema, serta menjembatani desainer dan developer.

### Ringkasan Bab 8

- Hierarki visual dan prinsip Gestalt membantu pengguna memahami struktur halaman dengan cepat.
- Tipografi, warna, dan jarak sebaiknya sistematis dan konsisten.
- Desain responsif dan hormat pada preferensi pengguna (mode gelap, kurangi gerak) adalah standar modern.
- Sistem desain dan token desain menjaga konsistensi dan mempercepat kerja tim.

### Latihan Bab 8

1. Lakukan uji menyipitkan mata pada satu halaman situs favorit Anda. Apa yang paling menonjol? Apakah sesuai tujuan halaman?
2. Tulis CSS untuk kartu yang menampilkan 1 kolom di ponsel dan 2 kolom di layar 768 piksel ke atas.
3. Tentukan dua alasan mengapa memakai `rem` untuk ukuran huruf lebih baik daripada `px`.
4. Jelaskan dua prinsip Gestalt pada formulir pendaftaran dan bagaimana menerapkannya.

---

## Bab 9. Prototipe dan Arsitektur Informasi

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjelaskan tingkat kerincian (_fidelity_) prototipe dan kapan memakainya.
2. Membuat sketsa, wireframe, dan alur pengguna dasar.
3. Menyusun arsitektur informasi sederhana.

### 9.1 Mengapa Membuat Prototipe?

**Prototipe** adalah representasi awal dari desain yang dapat dicoba untuk mengumpulkan umpan balik sebelum investasi besar pada kode. Tujuannya belajar, bukan membuat produk jadi. Prototipe memungkinkan Anda gagal murah dan cepat.

### 9.2 Tingkat Kerincian

|Tingkat|Contoh|Kecepatan|Kegunaan|
|---|---|---|---|
|Rendah (_low-fidelity_)|Sketsa kertas, kotak dan garis|Sangat cepat|Menjajaki ide, struktur, dan alur|
|Menengah|Wireframe digital abu-abu|Cepat|Menguji tata letak dan alur tanpa pengalih visual|
|Tinggi (_high-fidelity_)|Desain visual lengkap dan prototipe interaktif|Lebih lambat|Menguji detail interaksi, tampilan, dan kesan|
|Prototipe kode|Halaman HTML/JS yang berfungsi|Bergantung|Menguji perilaku nyata, animasi, kinerja|

Prinsipnya: **mulai dari yang paling murah untuk menjawab pertanyaan Anda**. Jika pertanyaannya "apakah alurnya masuk akal?", sketsa sudah cukup.

### 9.3 Teknik Prototipe

- **Prototipe kertas** (_paper prototype_): kertas dan pena, tiap layar satu lembar; fasilitator mengganti lembar sesuai aksi partisipan.
- **Wizard of Oz**: pengguna merasa berinteraksi dengan sistem nyata, padahal manusia bekerja di belakang layar. Berguna untuk menguji ide sebelum teknologi ada, misalnya antarmuka percakapan.
- **Prototipe klik** (_clickable prototype_): layar digital yang terhubung dengan tautan.
- **Prototipe kode**: dibuat dengan HTML, CSS, dan JavaScript, atau kerangka kerja antarmuka.

### 9.4 Perangkat

Perangkat desain dan prototipe terus berubah, jadi pilih yang sesuai kebutuhan tim:

- **Figma**: desain dan prototipe kolaboratif berbasis web, banyak dipakai industri.
- **Penpot**: alat desain sumber terbuka (_open source_).
- **Balsamiq** dan alat wireframe cepat lain.
- **Kertas dan papan tulis**: tetap tak tergantikan untuk tahap awal.

Sejak 2023 banyak alat menawarkan fitur pembuatan desain atau kode dengan bantuan AI. Perlakukan keluarannya sebagai **draf awal**: periksa kualitas, konsistensi, aksesibilitas, dan kesesuaian dengan kebutuhan pengguna nyata. AI mempercepat pembuatan, tetapi tidak menggantikan riset dan evaluasi.

### 9.5 Arsitektur Informasi

**Arsitektur informasi** (_information architecture_) adalah seni dan ilmu mengatur konten agar mudah ditemukan dan dipahami. Elemennya:

- **Sistem organisasi**: bagaimana konten dikelompokkan (topik, tugas, audiens, kronologi, abjad).
- **Sistem pelabelan**: nama untuk kategori dan tautan.
- **Sistem navigasi**: bagaimana pengguna berpindah.
- **Sistem pencarian**: bagaimana pengguna mencari langsung.

**Peta situs** (_sitemap_) contoh untuk aplikasi perpustakaan kampus:

```
Beranda
|-- Cari Buku
|   |-- Hasil Pencarian
|   |-- Detail Buku
|-- Pinjaman Saya
|   |-- Aktif
|   |-- Riwayat
|   |-- Perpanjang
|-- Pesan Ruang
|   |-- Pilih Ruang
|   |-- Konfirmasi
|-- Akun
    |-- Profil
    |-- Pengaturan
    |-- Bantuan
```

**Alur pengguna** (_user flow_) menggambarkan langkah pengguna mencapai tujuan, termasuk keputusan dan kasus gagal:

```
[Mulai] -> [Buka "Pesan Ruang"] -> [Pilih tanggal dan jam]
                                          |
                                          v
                              <Ada ruang kosong?>
                               /               \
                            Ya                  Tidak
                             |                   |
                             v                   v
                      [Pilih ruang]      [Tampilkan jam lain / daftar tunggu]
                             |
                             v
                      [Konfirmasi] -> [Kode pesanan] -> [Selesai]
```

Selalu rancang **jalur bahagia** (_happy path_) dan **jalur gagal** (kehabisan stok, koneksi putus, sesi habis, izin ditolak).

### Ringkasan Bab 9

- Prototipe adalah alat belajar; mulai dari kerincian terendah yang cukup menjawab pertanyaan.
- Teknik seperti prototipe kertas dan Wizard of Oz memungkinkan pengujian awal yang murah.
- Arsitektur informasi dan alur pengguna menyusun struktur sebelum tampilan.

### Latihan Bab 9

1. Buat sketsa tiga layar untuk fitur "Pesan Ruang" pada aplikasi perpustakaan.
2. Gambarkan alur pengguna untuk "Pemesanan gagal karena koneksi terputus". Apa yang sebaiknya terjadi?
3. Kapan Anda akan memilih prototipe Wizard of Oz? Beri satu contoh.
4. Lakukan _card sorting_ dengan 10 kartu topik dan 3 orang teman. Catat pengelompokan yang berbeda dan alasannya.

---

## Bab 10. Evaluasi Usabilitas

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Melakukan evaluasi heuristik dengan tingkat keparahan.
2. Merencanakan dan menjalankan uji usabilitas dasar.
3. Menghitung dan menafsirkan skor SUS.
4. Memahami dasar pengujian A/B dan analitik.

### 10.1 Dua Keluarga Evaluasi

|Keluarga|Siapa yang menilai|Contoh metode|Kelebihan|Keterbatasan|
|---|---|---|---|---|
|Inspeksi|Pakar|Evaluasi heuristik, _cognitive walkthrough_|Cepat dan murah|Bukan pengguna nyata; bisa melewatkan masalah|
|Uji dengan pengguna|Pengguna nyata|Uji usabilitas, pengujian A/B, survei|Bukti perilaku nyata|Lebih mahal dan butuh rekrutmen|

Praktik terbaik: **gabungkan keduanya**.

### 10.2 Evaluasi Heuristik

Beberapa evaluator (idealnya 3 sampai 5) memeriksa antarmuka secara terpisah terhadap daftar heuristik (misalnya sepuluh heuristik Nielsen), mencatat masalah, lalu menggabungkan temuan.

Tingkat keparahan (skala Nielsen):

|Skor|Arti|
|---|---|
|0|Bukan masalah usabilitas|
|1|Masalah kosmetik; perbaiki bila ada waktu|
|2|Masalah kecil; prioritas rendah|
|3|Masalah besar; prioritas tinggi|
|4|Bencana usabilitas; harus diperbaiki sebelum rilis|

Contoh catatan temuan:

|ID|Layar|Masalah|Heuristik|Keparahan|Saran|
|---|---|---|---|---|---|
|T-01|Pembayaran|Tombol "Bayar" tidak memberi umpan balik setelah ditekan|1. Visibilitas status|4|Tampilkan indikator dan nonaktifkan tombol sementara|
|T-02|Profil|Label "Submit" dan "Simpan" dipakai bergantian|4. Konsistensi|2|Samakan menjadi "Simpan"|
|T-03|Pencarian|Hasil kosong hanya menampilkan layar putih|9. Pemulihan galat|3|Beri pesan dan saran pencarian alternatif|

### 10.3 Cognitive Walkthrough

Evaluator menelusuri tugas langkah demi langkah dan bertanya pada setiap langkah:

1. Apakah pengguna akan mencoba melakukan efek yang benar?
2. Apakah pengguna akan melihat bahwa kontrol yang benar tersedia?
3. Apakah pengguna akan mengaitkan kontrol itu dengan efek yang diinginkan?
4. Setelah aksi, apakah pengguna memahami umpan baliknya dan tahu bahwa mereka maju?

Sangat berguna untuk menilai kemudahan dipelajari bagi pengguna baru.

### 10.4 Uji Usabilitas

**Uji usabilitas** meminta pengguna nyata mencoba menyelesaikan tugas realistis sementara tim mengamati.

**Langkah-langkah:**

1. **Tentukan tujuan dan pertanyaan riset**. Contoh: "Apakah mahasiswa dapat memesan ruang dalam waktu kurang dari 2 menit tanpa bantuan?"
2. **Susun skenario tugas** yang realistis dan tidak memberi petunjuk cara.
3. **Rekrut partisipan** yang mewakili pengguna sasaran.
4. **Siapkan lingkungan**: prototipe atau produk, perekam layar dan suara (dengan izin), catatan.
5. **Jalankan sesi**: sambutan, persetujuan, _think-aloud_ (berpikir keras), tugas, tanya jawab akhir.
6. **Analisis dan laporkan**: kumpulkan masalah, beri keparahan, usulkan perbaikan.

**Skenario tugas yang baik vs buruk**

|Buruk (memberi petunjuk)|Baik (berbasis tujuan)|
|---|---|
|"Klik menu Pesan Ruang, lalu pilih ruang dan tekan Konfirmasi."|"Besok sore Anda perlu tempat tenang untuk belajar kelompok 4 orang selama 2 jam. Pesankan ruang melalui aplikasi ini."|

**Peran fasilitator**:

- Jangan membantu atau membela desain.
- Dorong partisipan terus bicara: "Apa yang sedang Anda pikirkan?"
- Jika pengguna bertanya "Apakah ini benar?", balas dengan "Menurut Anda bagaimana?"

**Jumlah partisipan.** Penelitian Nielsen dan Landauer menunjukkan bahwa sekitar 5 pengguna dapat menemukan sebagian besar masalah usabilitas utama dalam satu putaran pengujian untuk satu kelompok pengguna serupa. Karena itu, lebih baik menguji 5 orang, memperbaiki, lalu menguji lagi, daripada sekali dengan 15 orang. Bila ada kelompok pengguna berbeda, uji tiap kelompok.

### 10.5 Metrik Usabilitas

|Metrik|Cara mengukur|Contoh|
|---|---|---|
|Tingkat keberhasilan tugas|Persentase tugas yang selesai|7 dari 8 partisipan berhasil memesan ruang|
|Waktu penyelesaian tugas|Detik atau menit untuk selesai|Median 95 detik|
|Tingkat galat|Jumlah kesalahan per tugas|Rata-rata 1,2 salah ketuk|
|Kepuasan|Kuesioner baku|SUS, SEQ|
|Kemudahan tugas|Satu pertanyaan setelah tugas|_Single Ease Question_ (SEQ) skala 1 sampai 7|

### 10.6 System Usability Scale (SUS)

SUS adalah kuesioner 10 pernyataan dengan skala 1 (sangat tidak setuju) sampai 5 (sangat setuju), dikembangkan John Brooke (1986, dipublikasikan 1996). Pernyataan ganjil bernada positif, genap bernada negatif.

Contoh pernyataan:

1. Saya kira saya ingin sering memakai sistem ini.
2. Saya merasa sistem ini terlalu rumit tanpa alasan.
3. Saya merasa sistem ini mudah dipakai.
4. Saya kira saya butuh bantuan teknisi untuk bisa memakai sistem ini.
5. Saya merasa fungsi-fungsi dalam sistem ini terintegrasi dengan baik.
6. Saya merasa terlalu banyak ketidakkonsistenan pada sistem ini.
7. Saya kira kebanyakan orang akan belajar memakai sistem ini dengan cepat.
8. Saya merasa sistem ini sangat merepotkan untuk dipakai.
9. Saya merasa sangat percaya diri memakai sistem ini.
10. Saya perlu belajar banyak hal dulu sebelum bisa memakai sistem ini.

**Cara menghitung skor satu responden:**

- Pernyataan ganjil: skor kontribusi = jawaban dikurangi 1.
- Pernyataan genap: skor kontribusi = 5 dikurangi jawaban.
- Jumlahkan seluruh kontribusi, lalu kalikan 2,5. Hasilnya 0 sampai 100.

```python
def hitung_sus(jawaban):
    """jawaban: daftar 10 angka (1 sampai 5) sesuai urutan pernyataan."""
    if len(jawaban) != 10:
        raise ValueError("SUS membutuhkan tepat 10 jawaban.")
    total = 0
    for i, nilai in enumerate(jawaban, start=1):
        if i % 2 == 1:        # nomor ganjil: pernyataan positif
            total += nilai - 1
        else:                 # nomor genap: pernyataan negatif
            total += 5 - nilai
    return total * 2.5

contoh = [4, 2, 4, 1, 4, 2, 5, 2, 4, 1]
print(hitung_sus(contoh))  # 85.0
```

**Menafsirkan skor.** Rata-rata SUS dari banyak penelitian sekitar 68. Skor di atas 68 umumnya dianggap di atas rata-rata, dan skor di atas sekitar 80 dianggap sangat baik. Skor SUS **bukan persentase** meskipun rentangnya 0 sampai 100. Skor ini baik dipakai untuk membandingkan versi atau produk, bukan sebagai satu-satunya ukuran.

### 10.7 Pengujian A/B dan Analitik

**Pengujian A/B** membandingkan dua versi (A dan B) dengan membagi pengguna secara acak, lalu mengukur metrik seperti tingkat konversi. Hal yang perlu diperhatikan:

- Tentukan hipotesis dan metrik **sebelum** menguji.
- Pastikan ukuran sampel cukup dan jalankan cukup lama (mencakup siklus mingguan).
- Pahami signifikansi statistik; jangan menghentikan uji hanya karena angka awal tampak bagus.
- Uji A/B menunjukkan **versi mana yang lebih baik**, bukan **mengapa**. Kombinasikan dengan riset kualitatif.
- Hati-hati terhadap metrik yang mendorong perilaku merugikan pengguna (misalnya maksimalkan klik dengan cara menyesatkan).

**Analitik** (misalnya corong konversi, peta panas, rekaman sesi, kejadian kesalahan) membantu menemukan **di mana** pengguna bermasalah. Patuhi persetujuan dan perlindungan data pribadi.

### 10.8 Melaporkan Temuan

Laporan yang berguna bersifat ringkas, berbukti, dan dapat ditindaklanjuti:

1. Ringkasan eksekutif: temuan utama dan rekomendasi teratas.
2. Metode dan partisipan singkat.
3. Temuan, diurutkan menurut keparahan, dengan bukti (kutipan, rekaman, tangkapan layar).
4. Rekomendasi spesifik.
5. Hal-hal yang berjalan baik (agar tidak hilang saat redesain).

### Ringkasan Bab 10

- Evaluasi terbagi menjadi inspeksi pakar dan pengujian dengan pengguna; gabungkan keduanya.
- Uji usabilitas dengan sekitar 5 pengguna per kelompok berulang kali sangat efektif menemukan masalah utama.
- SUS memberi ukuran kepuasan baku; skor dihitung dengan aturan khusus.
- A/B testing menjawab "mana yang lebih baik", riset kualitatif menjawab "mengapa".

### Latihan Bab 10

1. Hitung skor SUS untuk jawaban `[5, 1, 5, 2, 4, 1, 5, 2, 5, 1]`.
2. Ubah instruksi tugas "Klik ikon keranjang lalu tekan Bayar" menjadi skenario berbasis tujuan.
3. Lakukan evaluasi heuristik singkat pada halaman login suatu situs. Catat tiga temuan dengan tingkat keparahan.
4. Mengapa menghentikan pengujian A/B begitu salah satu versi tampak unggul pada hari pertama berisiko menyesatkan?

---

## Bab 11. Aksesibilitas dan Inklusivitas

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjelaskan aksesibilitas dan mengapa penting.
2. Menjelaskan empat prinsip POUR dan struktur level WCAG.
3. Menerapkan praktik aksesibilitas dasar pada HTML dan CSS.
4. Menguji aksesibilitas dengan alat dan secara manual.

### 11.1 Mengapa Aksesibilitas?

**Aksesibilitas** (_accessibility_, sering disingkat a11y karena ada 11 huruf di antara a dan y) berarti produk dapat dipakai oleh orang dengan beragam kemampuan, termasuk penyandang disabilitas.

Alasan penting:

- **Etika dan keadilan**: akses informasi dan layanan adalah hak.
- **Hukum dan kebijakan**: banyak yurisdiksi mewajibkan atau mendorong aksesibilitas. Di Indonesia, Undang-Undang Nomor 8 Tahun 2016 tentang Penyandang Disabilitas mengatur hak, termasuk akses terhadap informasi dan komunikasi. Di Uni Eropa, _European Accessibility Act_ mulai berlaku bagi banyak produk dan layanan digital sejak Juni 2025. Aturan berubah dan bergantung wilayah, jadi periksa peraturan terbaru.
- **Jangkauan pengguna**: disabilitas bukan hanya kondisi permanen. Ada kondisi sementara (tangan patah) dan situasional (silau matahari, ruang bising).
- **Manfaat bagi semua** (_curb-cut effect_): fitur yang dirancang untuk disabilitas sering bermanfaat luas. Teks bantuan (_caption_) berguna juga bagi orang yang menonton video tanpa suara.

Spektrum persona inklusif (dari praktik Microsoft Inclusive Design):

|Kemampuan|Permanen|Sementara|Situasional|
|---|---|---|---|
|Penglihatan|Tunanetra|Cedera mata|Silau matahari|
|Pendengaran|Tunarungu|Infeksi telinga|Tempat bising|
|Gerak tangan|Satu lengan|Tangan patah|Menggendong bayi|
|Bicara|Gangguan bicara|Radang tenggorokan|Aksen asing|
|Kognitif|Disleksia, ADHD|Kurang tidur|Terburu-buru, stres|

### 11.2 WCAG dan Prinsip POUR

**Web Content Accessibility Guidelines (WCAG)** dari W3C adalah standar teknis aksesibilitas yang paling banyak dirujuk di dunia. Empat prinsipnya disingkat **POUR**:

|Prinsip|Arti|Contoh|
|---|---|---|
|**Perceivable** (Dapat dipersepsi)|Informasi dapat ditangkap lewat indra yang tersedia|Teks alternatif untuk gambar, takarir video, kontras cukup|
|**Operable** (Dapat dioperasikan)|Komponen dapat dioperasikan dengan berbagai cara|Seluruh fungsi bisa lewat papan ketik, target cukup besar, waktu cukup|
|**Understandable** (Dapat dipahami)|Konten dan operasi mudah dipahami|Bahasa jelas, perilaku dapat diprediksi, bantuan saat salah input|
|**Robust** (Tangguh)|Konten dapat ditafsirkan oleh beragam teknologi, termasuk teknologi bantu|HTML semantik, nama dan peran komponen yang benar|

WCAG memiliki tiga level kesesuaian: **A** (minimum), **AA** (target umum dan paling sering diwajibkan oleh peraturan), dan **AAA** (tertinggi, tidak selalu mungkin untuk seluruh konten).

> **Catatan Versi (per Oktober 2026).** Versi WCAG yang berlaku sebagai Rekomendasi W3C adalah **WCAG 2.2**. Pada Maret 2026 W3C menerbitkan pembaruan Rancangan Kerja (_Working Draft_) **WCAG 3.0**, yang menyusun ulang pedoman menjadi persyaratan berbasis hasil dengan model penilaian baru. Dokumen tersebut masih berstatus rancangan, belum standar final, dan W3C menyatakan WCAG 3 tidak menggantikan atau mencabut WCAG 2. Peraturan dan kontrak saat ini umumnya merujuk WCAG 2.x, jadi untuk praktik saat ini targetkan **WCAG 2.2 level AA**. Jika Anda membaca ini setelah 2026, periksa status terbaru di situs W3C WAI.

### 11.3 Praktik Dasar

#### 1. Gunakan HTML semantik

Elemen HTML bawaan sudah membawa peran, fokus papan ketik, dan perilaku yang dipahami teknologi bantu. **Aturan pertama ARIA: jika ada elemen HTML bawaan yang sesuai, pakai itu, jangan membuat ulang dengan `div` dan ARIA.**

Buruk:

```html
<div class="tombol" onclick="kirim()">Kirim</div>
```

Baik:

```html
<button type="button" onclick="kirim()">Kirim</button>
```

Elemen `<button>` otomatis bisa difokuskan dengan Tab, diaktifkan dengan Enter atau Spasi, dan diumumkan sebagai "tombol" oleh pembaca layar. Pada `div` semuanya hilang kecuali Anda menambahkannya manual.

#### 2. Struktur dokumen dan landmark

```html
<body>
  <a class="lompat" href="#isi">Lompat ke konten utama</a>
  <header>...</header>
  <nav aria-label="Navigasi utama">...</nav>
  <main id="isi">
    <h1>Judul Halaman</h1>
    <section>
      <h2>Bagian Pertama</h2>
    </section>
  </main>
  <footer>...</footer>
</body>
```

- Satu `<h1>` per halaman, tingkat judul berurutan (jangan melompat dari `h1` ke `h4` hanya demi ukuran).
- _Skip link_ membantu pengguna papan ketik melewati navigasi berulang.
- Ukuran visual diatur dengan CSS, bukan dengan memilih tingkat judul.

#### 3. Teks alternatif untuk gambar

```html
<!-- Gambar bermakna: jelaskan fungsi atau isi -->
<img src="grafik-penjualan.png"
     alt="Grafik batang: penjualan naik dari 120 unit pada Januari menjadi 210 unit pada Juni">

<!-- Gambar dekoratif: alt kosong agar dilewati pembaca layar -->
<img src="hiasan.svg" alt="">
```

Tips menulis `alt`: jelaskan **tujuan** gambar dalam konteksnya, bukan sekadar "gambar" atau nama berkas. Untuk gambar kompleks, beri penjelasan panjang di dekatnya.

#### 4. Formulir yang dapat dipakai

```html
<form>
  <div>
    <label for="email">Alamat email</label>
    <input id="email" name="email" type="email"
           autocomplete="email" required
           aria-describedby="email-bantuan email-galat">
    <p id="email-bantuan">Contoh: nama@contoh.ac.id</p>
    <p id="email-galat" role="alert"></p>
  </div>

  <fieldset>
    <legend>Pilih metode pengiriman</legend>
    <label><input type="radio" name="kirim" value="reguler"> Reguler</label>
    <label><input type="radio" name="kirim" value="kilat"> Kilat</label>
  </fieldset>

  <button type="submit">Kirim</button>
</form>
```

Poin penting:

- Setiap kolom punya `<label>` yang terhubung (`for` dan `id`). `placeholder` **bukan** pengganti label karena menghilang saat mengetik dan biasanya berkontras rendah.
- `autocomplete` membantu pengguna dan pengelola kata sandi.
- Pesan galat menyebut kolom, penyebab, dan cara memperbaiki; dikaitkan dengan kolomnya.
- Kelompok pilihan dibungkus `fieldset` dan `legend`.

#### 5. Keyboard dan fokus

- Seluruh fungsi harus bisa dipakai tanpa mouse: Tab, Shift+Tab, Enter, Spasi, panah, Esc.
- **Fokus harus selalu terlihat**. Jangan menghapus garis fokus tanpa pengganti:

```css
/* Buruk: menghapus indikator fokus */
button:focus { outline: none; }

/* Baik: indikator jelas dan konsisten */
:focus-visible {
  outline: 3px solid #1a5fb4;
  outline-offset: 2px;
}
```

- Urutan fokus mengikuti urutan logis.
- Pada dialog modal, fokus berpindah ke dalam dialog, terkurung di dalamnya, dan kembali ke pemicu setelah ditutup.

#### 6. Kontras warna

Rasio kontras minimum WCAG 2.x level AA:

|Elemen|Rasio minimum AA|Level AAA|
|---|---|---|
|Teks biasa|4,5 : 1|7 : 1|
|Teks besar (sekitar 24 px atau 19 px tebal)|3 : 1|4,5 : 1|
|Komponen antarmuka dan grafik bermakna (batas kolom, ikon)|3 : 1|-|

Berikut kode Python untuk menghitung rasio kontras sesuai rumus WCAG:

```python
def _linier(c):
    c = c / 255
    return c / 12.92 if c <= 0.03928 else ((c + 0.055) / 1.055) ** 2.4

def luminans(hex_warna):
    hex_warna = hex_warna.lstrip("#")
    r, g, b = (int(hex_warna[i:i + 2], 16) for i in (0, 2, 4))
    return 0.2126 * _linier(r) + 0.7152 * _linier(g) + 0.0722 * _linier(b)

def rasio_kontras(warna1, warna2):
    l1, l2 = luminans(warna1), luminans(warna2)
    terang, gelap = max(l1, l2), min(l1, l2)
    return (terang + 0.05) / (gelap + 0.05)

print(round(rasio_kontras("#000000", "#ffffff"), 2))  # 21.0
print(round(rasio_kontras("#767676", "#ffffff"), 2))  # sekitar 4.54, lolos AA
print(round(rasio_kontras("#777777", "#ffffff"), 2))  # sekitar 4.48, tidak lolos AA
```

#### 7. Jangan hanya mengandalkan warna

Tambahkan ikon, teks, atau pola. Contoh status galat: ikon tanda seru, teks "Galat:", dan warna merah, bukan merah saja.

#### 8. Ukuran target sentuh

WCAG 2.2 menambahkan kriteria **Target Size (Minimum)** pada level AA: target interaktif minimal 24 x 24 piksel CSS (dengan beberapa pengecualian). Pedoman platform menyarankan lebih besar: sekitar 44 poin pada iOS dan 48 dp pada Android. Beri jarak antar target agar tidak salah ketuk.

#### 9. Media berbasis waktu dan gerak

- Video: takarir (_captions_) dan, bila perlu, deskripsi audio.
- Audio: transkrip.
- Jangan memutar otomatis media bersuara.
- Hindari kilatan lebih dari tiga kali per detik (risiko memicu kejang pada penderita epilepsi fotosensitif).
- Hormati preferensi _reduce motion_ (Bab 8).

#### 10. Zoom dan reflow

Halaman harus tetap dapat dipakai pada pembesaran 200 persen dan pada lebar sekitar 320 piksel CSS tanpa gulir horizontal untuk konten teks (kriteria _Reflow_).

#### 11. Bahasa dan keterbacaan

```html
<html lang="id">
```

Atribut `lang` membantu pembaca layar memilih pelafalan yang benar. Tandai bagian berbahasa lain dengan `lang` terpisah, misalnya `<span lang="en">dashboard</span>`.

### 11.4 Kriteria Baru WCAG 2.2 yang Perlu Dikenal

WCAG 2.2 menambahkan sejumlah kriteria untuk membantu pengguna dengan disabilitas kognitif, penglihatan rendah, dan motorik. Contohnya:

- **Focus Not Obscured**: elemen yang sedang fokus tidak boleh tertutup sepenuhnya oleh konten lain (misalnya spanduk lengket).
- **Dragging Movements**: aksi seret harus punya alternatif tanpa seret.
- **Target Size (Minimum)**: ukuran target minimum.
- **Consistent Help**: bantuan berada di tempat yang konsisten antar halaman.
- **Redundant Entry**: jangan meminta pengguna memasukkan ulang informasi yang sudah diberikan dalam proses yang sama.
- **Accessible Authentication (Minimum)**: proses masuk tidak boleh bergantung pada tes fungsi kognitif (misalnya mengingat atau menyalin kata sandi) tanpa alternatif; izinkan pengelola kata sandi dan tempel (_paste_).

Daftar lengkap dan terbaru ada di dokumen resmi W3C.

### 11.5 Menguji Aksesibilitas

Pengujian aksesibilitas bersifat berlapis:

|Lapis|Alat atau cara|Yang ditemukan|
|---|---|---|
|Otomatis|Lighthouse, axe, WAVE|Sebagian masalah teknis (kontras, label hilang, alt hilang). Alat otomatis hanya menemukan sebagian masalah|
|Papan ketik|Coba seluruh alur hanya dengan Tab, Enter, Spasi, Esc|Perangkap fokus, urutan salah, kontrol yang tak bisa dijangkau|
|Pembaca layar|NVDA atau JAWS (Windows), VoiceOver (macOS dan iOS), TalkBack (Android)|Nama, peran, dan urutan pembacaan|
|Pembesaran dan tampilan|Zoom 200 persen, mode kontras tinggi, mode gelap|Teks terpotong, kontras hilang|
|Pengguna nyata|Uji dengan penyandang disabilitas|Masalah yang tidak terdeteksi cara lain|

### 11.6 Aksesibilitas dan AI

Teknologi AI membantu (misalnya teks alternatif otomatis, takarir otomatis, ringkasan) tetapi memiliki batas:

- Teks alternatif otomatis bisa keliru atau tidak sesuai konteks. Tinjau oleh manusia untuk konten penting.
- Takarir otomatis bisa salah pada istilah teknis, nama, atau aksen.
- Antarmuka percakapan harus tetap dapat dipakai oleh pembaca layar, papan ketik, dan input suara.
- Keluaran AI yang berubah-ubah perlu diumumkan dengan benar ke teknologi bantu (misalnya memakai wilayah langsung/_live region_) dan tidak boleh merebut fokus.

### 11.7 Inklusivitas Lebih Luas

Aksesibilitas adalah bagian dari inklusivitas yang lebih luas:

- **Bahasa**: pertimbangkan bahasa daerah, bahasa sederhana, dan penerjemahan yang baik.
- **Literasi**: gunakan kalimat pendek dan ikon pendukung.
- **Perangkat dan jaringan**: dukung perangkat lama, mode hemat data, dan fungsi dasar saat offline.
- **Gender, usia, dan budaya**: hindari stereotip pada ilustrasi, formulir (misalnya pilihan gender dan nama), dan contoh.

### Ringkasan Bab 11

- Aksesibilitas memastikan produk dapat dipakai oleh orang dengan beragam kemampuan; ini juga menguntungkan semua pengguna.
- Prinsip POUR dan WCAG 2.2 level AA adalah acuan teknis utama saat ini; WCAG 3.0 masih berupa rancangan.
- HTML semantik, label formulir, fokus terlihat, kontras cukup, dan teks alternatif adalah dasar yang berdampak besar.
- Pengujian aksesibilitas membutuhkan alat otomatis, uji manual, pembaca layar, dan pengguna nyata.

### Latihan Bab 11

1. Ubah `div` tombol pada contoh 11.3 menjadi versi yang dapat dipakai dengan papan ketik. Sebutkan tiga hal yang kini otomatis tersedia.
2. Hitung rasio kontras `#2a6fdb` terhadap putih menggunakan kode Python di buku ini, lalu tentukan apakah lolos AA untuk teks biasa.
3. Tulis `alt` yang baik untuk foto grafik batang yang menunjukkan jumlah pengunjung perpustakaan per bulan.
4. Jelaskan mengapa `placeholder` tidak boleh menggantikan `label`.
5. Lakukan uji papan ketik pada satu situs: apakah semua fungsi dapat dijangkau dan fokus terlihat jelas? Catat temuan.

---

## Bab 12. Desain untuk Berbagai Platform

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjelaskan pertimbangan desain pada web, seluler, desktop, dan platform lain.
2. Memahami kinerja web sebagai bagian dari pengalaman pengguna.
3. Menimbang konsistensi lintas platform dan kesesuaian dengan platform asli.

### 12.1 Web

Kekuatan web: dapat diakses lewat tautan, tanpa pemasangan, lintas perangkat. Tantangan: beragam peramban, ukuran layar, dan kualitas jaringan.

Pertimbangan:

- Desain responsif dan _progressive enhancement_ (fungsi inti bekerja di mana-mana, fitur canggih ditambahkan bila didukung).
- Tautan yang bermakna, tombol "kembali" yang berfungsi, URL yang dapat dibagikan.
- Kinerja (lihat 12.6).
- Dukungan aksesibilitas (Bab 11).

### 12.2 Seluler (_Mobile_)

Karakteristik: layar kecil, sentuh, konteks bergerak, gangguan tinggi, jaringan tidak stabil, baterai terbatas.

Pertimbangan:

- **Zona jempol** (_thumb zone_): bagian bawah layar lebih mudah dijangkau pada pemakaian satu tangan. Letakkan aksi sering di sana.
- **Ukuran target**: sekitar 44 poin (iOS) atau 48 dp (Android) minimal.
- **Gestur**: sediakan alternatif yang terlihat untuk gestur tersembunyi.
- **Konteks**: izinkan pemakaian singkat; simpan kemajuan; antisipasi gangguan dan panggilan masuk.
- **Offline dan jaringan lemah**: simpan data sementara, sinkronisasi saat tersambung, beri status jelas.
- **Izin** (_permissions_): minta izin kamera, lokasi, dan notifikasi pada saat relevan dan jelaskan alasannya, bukan saat aplikasi pertama dibuka.
- **Keyboard layar**: pilih tipe keyboard yang sesuai (angka, email), hindari menutup kolom yang sedang diisi.

### 12.3 Desktop

Karakteristik: layar lebar, papan ketik dan mouse, banyak jendela, pengguna ahli.

Pertimbangan:

- **Pintasan papan ketik** dan palet perintah untuk pengguna mahir.
- **Menu konteks**, klik kanan, seret dan lepas.
- Berbagai ukuran dan pemisahan jendela.
- Kepadatan informasi lebih tinggi untuk alat kerja profesional.
- Konsistensi dengan sistem operasi (Windows, macOS, Linux).

### 12.4 Perangkat Lain

|Platform|Pertimbangan utama|
|---|---|
|Jam tangan pintar (_wearable_)|Interaksi sangat singkat (hitungan detik), informasi ringkas, notifikasi bermakna|
|TV dan layar jauh|Jarak pandang jauh, navigasi pengendali jarak jauh (arah, pilih), teks besar|
|Otomotif|Meminimalkan gangguan pengemudi; suara dan kontrol fisik; aturan keselamatan|
|Kios, ATM, mesin layanan mandiri|Pengguna umum tanpa pelatihan, privasi layar, waktu habis, aksesibilitas fisik|
|Asisten suara dan speaker pintar|Tanpa layar atau layar minimal; perintah ringkas; konfirmasi verbal|
|IoT dan perangkat rumah pintar|Pengaturan awal sederhana, umpan balik fisik, keamanan|
|Permainan (_game_)|Antarmuka tampilan kepala (HUD), keseimbangan tantangan, alur (_flow_), opsi aksesibilitas (pemetaan ulang tombol, mode warna)|

### 12.5 Konsistensi Lintas Platform

Anda sering harus memilih:

- **Konsistensi lintas platform**: pengalaman serupa di semua platform. Menguntungkan pengguna yang berpindah perangkat dan menghemat biaya.
- **Kesesuaian platform asli** (_platform-native_): mengikuti konvensi tiap platform. Menguntungkan pengguna yang mengharapkan perilaku familier di perangkatnya.

Praktik yang umum: samakan **struktur, istilah, dan merek**, sesuaikan **kontrol dan perilaku** dengan platform.

### 12.6 Kinerja sebagai UX

Kinerja web diukur antara lain dengan _Core Web Vitals_ dari Google:

|Metrik|Mengukur|Ambang "baik" (umum dirujuk)|
|---|---|---|
|LCP (_Largest Contentful Paint_)|Kecepatan konten utama tampil|2,5 detik atau kurang|
|INP (_Interaction to Next Paint_)|Daya tanggap terhadap interaksi|200 milidetik atau kurang|
|CLS (_Cumulative Layout Shift_)|Stabilitas tata letak (tidak melompat)|0,1 atau kurang|

INP menggantikan metrik sebelumnya (FID) pada 2024. Ambang dan metrik dapat diperbarui, jadi cek dokumentasi resmi.

Praktik: kompres dan ukur gambar dengan tepat, tunda pemuatan skrip yang tidak kritis, tentukan dimensi gambar agar layout tidak melompat, dan uji pada perangkat dan jaringan yang realistis, bukan hanya laptop cepat di jaringan kantor.

### Ringkasan Bab 12

- Tiap platform memiliki kekuatan, batasan, dan konvensi sendiri.
- Seluler menuntut perhatian pada target sentuh, konteks bergerak, dan jaringan tidak stabil.
- Seimbangkan konsistensi lintas platform dengan kesesuaian platform asli.
- Kinerja adalah bagian dari pengalaman pengguna dan perlu diukur.

### Latihan Bab 12

1. Pilih satu aplikasi seluler. Tandai aksi mana yang berada pada zona jempol dan mana yang sulit dijangkau. Apa saran Anda?
2. Mengapa meminta izin lokasi saat aplikasi pertama dibuka sering menurunkan penerimaan pengguna? Apa alternatifnya?
3. Jelaskan perbedaan prioritas desain antara aplikasi di jam tangan pintar dan aplikasi desktop untuk analis data.
4. Mengapa CLS yang buruk (halaman "melompat") merusak pengalaman pengguna?

---

## Bab 13. IMK di Era Kecerdasan Buatan

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjelaskan pergeseran paradigma interaksi menuju antarmuka percakapan, copilot, dan agen.
2. Menerapkan pedoman interaksi manusia-AI.
3. Merancang kontrol, transparansi, dan pemulihan galat untuk sistem berbasis AI.
4. Mengenali risiko seperti kepercayaan berlebihan, halusinasi, dan dampak pada privasi.

> **Catatan Versi.** Bab ini membahas bidang yang berubah sangat cepat. Nama produk dan fitur tertentu sengaja tidak dibahas. Fokusnya pada **prinsip dan pola** yang lebih tahan lama. Gunakan sumber terbaru untuk perkembangan produk.

### 13.1 Dari Antarmuka Grafis ke Antarmuka Berbasis Tujuan

Pergeseran besar yang diamati dalam beberapa tahun terakhir:

|Era|Pengguna menyampaikan|Sistem merespons|Beban pengguna|
|---|---|---|---|
|Baris perintah|Perintah tepat|Hasil perintah|Menghafal sintaks|
|Antarmuka grafis dan sentuh|Aksi langkah demi langkah|Perubahan tampilan|Menavigasi menu dan alur|
|Percakapan dan asisten AI|Permintaan dalam bahasa alami|Jawaban atau konten|Merumuskan permintaan, memeriksa hasil|
|Agen AI|Tujuan tingkat tinggi|Rangkaian tindakan multi-langkah|Menetapkan batas, mengawasi, menyetujui|

Laporan tren HCI 2026 dari IEEE Computer Society menggambarkan agen AI yang makin menjadi lapisan interaksi utama: pengguna menyatakan tujuan, bukan menavigasi antarmuka satu per satu. Analis industri lain juga menggambarkan peran antarmuka yang bergeser dari alat yang dioperasikan menjadi tempat untuk **memberi arahan, mengawasi, dan mengoreksi** agen. Anggap ini sebagai arah umum, bukan kepastian; kecepatan dan bentuk adopsinya berbeda-beda antar produk.

Konsekuensinya bagi IMK:

- Pekerjaan desain bergeser dari merancang layar ke merancang **hubungan dan pembagian kerja** antara manusia dan sistem.
- Pertanyaan baru: seberapa otonom sistem? kapan harus bertanya? bagaimana pengguna tahu apa yang dilakukan sistem dan dapat menghentikannya?
- Prinsip lama tetap berlaku: visibilitas status, kontrol pengguna, pencegahan galat, pemulihan galat.

### 13.2 Pola Interaksi Manusia dengan AI

|Pola|Deskripsi|Contoh penggunaan|
|---|---|---|
|Percakapan (_chat_)|Dialog bebas dengan sistem|Tanya jawab, curah gagasan|
|Copilot / asisten sebaris|AI menawarkan saran di dalam alur kerja yang sudah ada|Saran penyelesaian kode, saran penulisan ulang teks|
|Palet perintah dengan bahasa alami|Mengetik tujuan, sistem memetakan ke fungsi|"Buat grafik penjualan bulan lalu"|
|Antarmuka generatif (_generative UI_)|Tampilan dibentuk atau disesuaikan oleh AI menurut konteks|Dasbor yang menyesuaikan pertanyaan pengguna|
|Agen otonom bertugas|AI merencanakan dan menjalankan rangkaian tindakan|Memesan perjalanan, merapikan berkas|
|Multimodal|Gabungan teks, suara, gambar, video|Memotret objek lalu bertanya tentangnya|

### 13.3 Pedoman Interaksi Manusia dan AI

Dua rujukan penting:

1. **Guidelines for Human-AI Interaction** (Amershi dan kolega, Microsoft Research, CHI 2019): 18 pedoman yang dikelompokkan menjadi empat fase: **di awal**, **saat interaksi**, **saat sistem salah**, dan **seiring waktu**.
2. **People + AI Guidebook** dari Google PAIR (_People + AI Research_): panduan praktis untuk merancang produk AI yang berpusat pada manusia.

Ringkasan semangat pedoman tersebut:

|Fase|Prinsip|Penerapan|
|---|---|---|
|Di awal|Jelaskan apa yang bisa dan tidak bisa dilakukan sistem; jelaskan seberapa baik ia melakukannya|Tampilkan contoh dan batasan; hindari klaim berlebihan|
|Saat interaksi|Beri saran pada waktu yang tepat; sesuaikan dengan konteks; hindari bias sosial|Jangan membanjiri dengan saran; jaga kesopanan dan kesetaraan|
|Saat sistem salah|Mudah mengabaikan, mengoreksi, atau menolak; jelaskan mengapa sistem melakukan itu|Tombol "Tolak", "Edit", "Urungkan"; sebutkan alasan atau sumber|
|Seiring waktu|Ingat interaksi terdahulu; belajar dari perilaku; beri tahu perubahan; beri kontrol global|Pengaturan personalisasi, riwayat yang dapat dihapus, pemberitahuan pembaruan perilaku|

### 13.4 Prinsip Desain untuk Sistem AI

**1. Atur ekspektasi dan komunikasikan batasan.** Pengguna perlu model mental yang tepat: AI bukan mesin pencari yang pasti benar, dan bukan manusia. Jelaskan bahwa hasil dapat keliru dan apa yang perlu diperiksa.

**2. Transparansi yang berguna.** Tunjukkan apa yang sedang dikerjakan sistem, data apa yang dipakai, dan sumber yang dirujuk. Penjelasan yang terlalu teknis tidak membantu; berikan yang relevan untuk keputusan pengguna.

**3. Kalibrasi kepercayaan.** Tujuannya **kepercayaan yang tepat**: tidak terlalu percaya (_over-trust_, terkait bias otomatisasi) dan tidak terlalu curiga (_under-trust_). Tunjukkan tingkat keyakinan atau bukti bila bermakna, dan rancang agar pengguna terdorong memverifikasi hal penting.

**4. Kontrol dan kemampuan membalik.** Pengguna harus bisa menghentikan, mengubah, dan mengurungkan. Makin berdampak suatu aksi, makin penting persetujuan dan pembalikan.

**5. Konfirmasi untuk aksi berisiko.** Aksi yang mahal, tidak dapat dibalik, atau melibatkan pihak lain (membayar, mengirim email, menghapus data) sebaiknya memerlukan persetujuan eksplisit atau tinjauan.

**6. Umpan balik dan perbaikan.** Sediakan cara mudah memberi tahu bahwa jawaban salah atau baik, serta cara memperbaiki arah ("buat lebih singkat", "pakai sumber lain").

**7. Gagal dengan anggun** (_graceful failure_). Saat AI tidak yakin atau tidak mampu, katakan terus terang, tawarkan alternatif, dan sediakan jalur manusia.

**8. Privasi dan kendali data.** Jelaskan data apa yang dikumpulkan, disimpan berapa lama, dan bagaimana menghapusnya. Minimalkan data yang dikirim.

### 13.5 Merancang untuk Agen: Tingkat Otonomi

Ketika sistem bertindak atas nama pengguna, tentukan tingkat otonominya per jenis tugas:

|Tingkat|Perilaku sistem|Peran pengguna|Cocok untuk|
|---|---|---|---|
|1. Saran saja|Memberi usulan, pengguna melakukan|Pelaku|Tugas berisiko tinggi atau baru|
|2. Tanya dulu|Menyiapkan tindakan lalu meminta persetujuan setiap kali|Pemberi persetujuan|Aksi berdampak sedang|
|3. Bertindak dengan batas|Bertindak otomatis dalam batas yang ditetapkan, meminta persetujuan di luar batas|Penetap kebijakan|Tugas rutin berisiko rendah|
|4. Bertindak dan melapor|Bertindak lalu melaporkan hasil; dapat diurungkan|Pengawas|Tugas rutin dan dapat dibalik|
|5. Otonom penuh|Bertindak tanpa pelaporan rinci|Hampir tidak ada|Jarang cocok; hanya untuk tugas yang sangat aman|

Pola desain untuk agen yang baik:

- **Pratinjau rencana**: tunjukkan rencana sebelum menjalankan.
- **Kemajuan terlihat**: tampilkan langkah yang sedang dikerjakan.
- **Dapat diinterupsi**: tombol berhenti yang selalu tersedia.
- **Izin bertingkat dan berbatas**: akses minimum yang diperlukan (_least privilege_), terutama untuk data dan akun.
- **Jejak audit** (_audit trail_): catatan apa yang dilakukan agen dan alasannya.
- **Pembalikan**: sebisa mungkin sediakan urungkan atau pemulihan.
- **Serah terima ke manusia** bila situasi di luar kemampuan atau risikonya tinggi.

Contoh pola konfirmasi aksi berisiko dalam TypeScript sederhana (konseptual):

```typescript
type Risiko = "rendah" | "sedang" | "tinggi";

interface AksiAgen {
  deskripsi: string;      // apa yang akan dilakukan, dalam bahasa pengguna
  risiko: Risiko;
  dapatDibalik: boolean;
  jalankan: () => Promise<void>;
  urungkan?: () => Promise<void>;
}

async function eksekusiDenganKontrol(
  aksi: AksiAgen,
  mintaPersetujuan: (teks: string) => Promise<boolean>
) {
  // Aksi berisiko tinggi atau tidak dapat dibalik selalu butuh persetujuan.
  const perluPersetujuan =
    aksi.risiko === "tinggi" || !aksi.dapatDibalik;

  if (perluPersetujuan) {
    const setuju = await mintaPersetujuan(
      `Agen akan: ${aksi.deskripsi}. Lanjutkan?`
    );
    if (!setuju) return { status: "dibatalkan" as const };
  }

  await aksi.jalankan();
  catatAudit(aksi.deskripsi);   // jejak audit untuk transparansi
  return { status: "selesai" as const, dapatDiurungkan: !!aksi.urungkan };
}
```

Kode ini hanya memperlihatkan gagasan: keputusan UX (kapan meminta persetujuan, apa yang dicatat, apakah bisa diurungkan) tertanam dalam logika program.

### 13.6 Masalah Khas Antarmuka AI

|Masalah|Penjelasan|Mitigasi|
|---|---|---|
|**Halusinasi**|Model menghasilkan informasi yang meyakinkan tetapi salah|Sumber yang dapat dicek, penolakan jujur, tinjauan manusia untuk hal penting|
|**Bias otomatisasi**|Pengguna terlalu percaya keluaran sistem|Dorong verifikasi, tunjukkan ketidakpastian, buat tinjauan mudah|
|**Masalah halaman kosong**|Kotak input kosong tidak memberi petunjuk apa yang bisa diminta|Contoh permintaan, saran, templat|
|**Penemuan kemampuan** (_discoverability_)|Pengguna tidak tahu apa yang mampu dilakukan sistem|Petunjuk kontekstual, daftar kemampuan|
|**Tidak deterministik**|Masukan sama bisa menghasilkan keluaran berbeda|Beri opsi regenerasi, simpan versi, jelaskan variasi|
|**Latensi**|Respons butuh waktu|Streaming bertahap, indikator kemajuan, kerangka|
|**Kehilangan kendali**|Pengguna tidak tahu apa yang dilakukan agen|Pratinjau, log, tombol berhenti|
|**Privasi dan kebocoran data**|Data sensitif terkirim atau tersimpan|Minimalkan data, kontrol pengguna, kebijakan jelas|
|**Akuntabilitas**|Siapa yang bertanggung jawab saat salah?|Kejelasan peran, jejak audit, jalur banding|
|**Bias dan keadilan**|Hasil merugikan kelompok tertentu|Evaluasi pada kelompok beragam, pemantauan|
|**Ketergantungan dan penurunan keterampilan**|Pengguna berhenti melatih kemampuan sendiri|Dorong pemahaman, bukan hanya jawaban, pada konteks belajar|

### 13.7 Mengevaluasi Pengalaman AI

Metode IMK klasik masih berlaku, dengan penyesuaian:

- **Uji usabilitas** dengan tugas nyata, termasuk saat AI salah. Amati: apakah pengguna sadar, bagaimana ia pulih?
- **Skenario kegagalan** (_failure modes_): rancang dan uji secara sengaja kasus sulit, ambigu, dan berisiko.
- **Rubrik kualitas** untuk keluaran: akurasi, kelengkapan, nada, keamanan.
- **Evaluasi berkelanjutan**: perilaku model dan data berubah, jadi pantau setelah rilis.
- **Ukur kepercayaan dan ketergantungan**, bukan hanya kepuasan dan kecepatan.
- **Uji dengan beragam pengguna**, termasuk bahasa daerah, aksen, dan kebutuhan aksesibilitas.

### 13.8 AI sebagai Alat Kerja bagi Praktisi IMK

AI dapat membantu: merangkum transkrip wawancara, menyusun draf mikroteks, menghasilkan variasi desain, membuat kode prototipe, menyiapkan data uji. Batasannya:

- **Periksa keluaran**: AI bisa keliru, bias, atau generik.
- **Jangan menggantikan pengguna nyata**: persona sintetis dari AI bukan pengganti riset dengan manusia. Ia bisa menggemakan stereotip.
- **Jaga data**: jangan memasukkan data pribadi partisipan ke layanan tanpa dasar hukum dan persetujuan yang jelas.
- **Tanggung jawab tetap pada Anda** sebagai desainer atau engineer.

### Ringkasan Bab 13

- Interaksi bergeser dari mengoperasikan layar menuju menyampaikan tujuan dan mengawasi sistem, tetapi prinsip IMK klasik tetap relevan.
- Pedoman interaksi manusia-AI menekankan ekspektasi yang tepat, transparansi, kontrol, pemulihan galat, dan pembelajaran seiring waktu.
- Merancang agen berarti menentukan tingkat otonomi, persetujuan, batas, jejak audit, dan pembalikan.
- Risiko khas: halusinasi, kepercayaan berlebihan, kehilangan kendali, privasi, dan bias.

### Latihan Bab 13

1. Pilih fitur AI yang pernah Anda pakai. Nilai dengan empat fase pedoman interaksi manusia-AI. Mana yang sudah baik dan mana yang kurang?
2. Rancang antarmuka konfirmasi untuk agen AI yang akan mengirim email ke 50 penerima. Apa saja yang ditampilkan sebelum pengguna menyetujui?
3. Tentukan tingkat otonomi (1 sampai 5) yang sesuai untuk: (a) mengatur ulang label folder, (b) mentransfer dana, (c) menjadwalkan rapat. Beri alasan.
4. Jelaskan apa itu bias otomatisasi dan dua cara desain dapat menguranginya.
5. Mengapa persona sintetis dari AI tidak dapat menggantikan wawancara dengan pengguna nyata?

---

## Bab 14. Komputasi Spasial dan Antarmuka Masa Depan

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Membedakan VR, AR, MR, dan XR serta komputasi spasial.
2. Menjelaskan prinsip desain dasar untuk antarmuka 3D dan imersif.
3. Mengenali tren antarmuka masa depan: multimodal, tanpa antarmuka, dan antarmuka otak-komputer.
4. Menilai tren secara kritis.

> **Catatan Versi.** Perangkat dan produk spasial berkembang cepat dan pasarnya berubah. Bab ini menekankan konsep dan prinsip. Periksa perkembangan terbaru dari sumber riset dan industri.

### 14.1 Istilah

|Istilah|Penjelasan|
|---|---|
|Realitas virtual (_Virtual Reality_, VR)|Pengguna sepenuhnya masuk ke lingkungan digital buatan|
|Realitas tertambah (_Augmented Reality_, AR)|Konten digital ditumpangkan pada dunia nyata|
|Realitas campuran (_Mixed Reality_, MR)|Objek digital dan nyata berinteraksi satu sama lain secara spasial|
|XR (_Extended Reality_)|Istilah payung untuk VR, AR, dan MR|
|Komputasi spasial (_Spatial Computing_)|Komputasi yang memahami dan memakai ruang fisik tiga dimensi sebagai bagian dari antarmuka|

### 14.2 Cara Berinteraksi di Ruang 3D

Modalitas masukan yang umum pada perangkat spasial:

- **Pandangan** (_gaze_) untuk menunjuk, sering dikombinasikan dengan **gestur tangan** (misalnya mencubit) untuk memilih.
- **Pelacakan tangan** untuk manipulasi langsung objek 3D.
- **Pengendali** (_controller_) untuk presisi dan permainan.
- **Suara** untuk perintah dan dikte.
- **Tubuh dan gerakan** (berjalan, menoleh, menunduk).

Prinsip penting: **manipulasi langsung** menjadi kuat di 3D, karena pengguna menyentuh objek, bukan menunjuk lewat perantara.

### 14.3 Prinsip Desain untuk Antarmuka Imersif

1. **Kenyamanan fisik adalah syarat utama.**
    - **Mabuk gerak** (_cybersickness_) dapat terjadi bila ada ketidaksesuaian antara gerakan yang dilihat dan dirasakan tubuh atau latensi tinggi. Jaga laju bingkai tinggi dan latensi gerak-ke-tampilan sangat rendah (target umum di bawah sekitar 20 milidetik).
    - Hindari gerakan kamera paksa. Beri pengguna kendali gerak dan opsi kenyamanan.
2. **Ergonomi.** Hindari menuntut lengan terangkat lama (_gorilla arm_). Letakkan konten pada jarak dan sudut pandang yang nyaman; hindari terlalu dekat atau terlalu jauh dari mata.
3. **Skala dan jarak.** Ukuran objek harus masuk akal; teks harus terbaca pada jarak yang diperkirakan.
4. **Kedalaman dan isyarat spasial.** Bayangan, oklusi (objek menutupi objek lain), dan audio spasial membantu pengguna memahami posisi.
5. **Umpan balik multisensori.** Visual, suara, dan haptik memperkuat kepastian bahwa interaksi berhasil, terutama karena tidak ada permukaan fisik untuk disentuh.
6. **Hormati ruang dan lingkungan nyata.** Pada AR/MR, perhatikan keselamatan (rintangan nyata), privasi (orang di sekitar), dan konteks sosial.
7. **Kemudahan ditemukan.** Tanpa konvensi mapan, pengguna perlu petunjuk jelas dan pengantar singkat.
8. **Aksesibilitas.** Tidak semua orang bisa berdiri, menggerakkan tangan, atau melihat dalam 3D. Sediakan alternatif (duduk, suara, kontrol sederhana, teks lebih besar, deskripsi audio).
9. **Privasi biometrik.** Pelacakan mata, tangan, dan lingkungan menghasilkan data sensitif yang perlu perlindungan khusus.

### 14.4 Antarmuka Multimodal dan Tanpa Layar

**Multimodal**: sistem menerima dan memberi informasi lewat beberapa kanal (suara, sentuh, pandangan, gestur, teks, gambar) dan memilih yang paling sesuai konteks. Contoh: mengemudi memakai suara, mengetik di rapat, atau memotret sambil bertanya.

**Zero UI / antarmuka tak terlihat**: tren di mana sistem bertindak berdasarkan konteks dan tujuan dengan interaksi visual minimal. Contoh: rumah pintar yang menyesuaikan suhu otomatis. Tantangannya:

- **Visibilitas dan kontrol**: bagaimana pengguna tahu apa yang dilakukan sistem dan menggantinya?
- **Kemudahan ditemukan**: bagaimana pengguna tahu apa yang dapat dilakukan?
- **Kepercayaan dan privasi**: sistem yang selalu mendengar atau melihat menimbulkan risiko.
- **Kesalahan senyap**: kesalahan tanpa antarmuka sulit disadari.

Prinsip _Calm Technology_ (teknologi tenang) dari Mark Weiser dan John Seely Brown: teknologi sebaiknya berada di pinggiran perhatian, memberi informasi tanpa menuntut perhatian penuh, dan masuk ke pusat perhatian hanya saat perlu.

### 14.5 Antarmuka Otak-Komputer dan Teknologi Saraf

**Antarmuka otak-komputer** (_Brain-Computer Interface_, BCI) membaca sinyal otak untuk mengendalikan perangkat. Penelitian klinis telah menunjukkan pemanfaatan untuk membantu orang dengan kelumpuhan berat berkomunikasi atau mengendalikan perangkat. Pengembangan untuk pengguna umum masih sangat awal.

Isu etika yang menonjol: **privasi data saraf**, persetujuan, keamanan, kesetaraan akses, dan siapa yang memiliki data. Laporan tren HCI menyebut bentuk awal antarmuka manusia-sistem langsung sebagai arah jangka lebih panjang, tetapi ini perlu dilihat sebagai prospek, bukan kenyataan umum.

### 14.6 Perangkat Pakai, Ruang Cerdas, dan Robot

- **Perangkat pakai** (_wearables_) dan kacamata pintar: informasi sekilas, interaksi suara, konteks.
- **Komputasi ambient dan IoT**: banyak perangkat kecil terhubung. Tantangan: interoperabilitas, keamanan, pengaturan sederhana.
- **Robot sosial dan asisten fisik**: aspek tambahan seperti bahasa tubuh, jarak sosial, dan keselamatan.

### 14.7 Menilai Tren Secara Kritis

Setiap beberapa tahun muncul gelombang "teknologi masa depan". Beberapa tumbuh, sebagian meredup. Untuk menilainya, ajukan pertanyaan IMK yang sama:

1. **Masalah apa yang diselesaikan** dan untuk siapa?
2. Apakah **lebih baik daripada alternatif** yang ada pada konteks nyata (bukan demonstrasi)?
3. Apa **biayanya**: uang, kenyamanan fisik, privasi, kerumitan?
4. Siapa yang **terkecualikan**?
5. Apa **dampak jangka panjangnya** bagi perilaku dan masyarakat?

Prinsip abadi: **teknologi berubah, manusia relatif tetap**. Kapasitas perhatian, memori, dan fisik kita berubah sangat lambat, sehingga pengetahuan tentang manusia (Bab 2 dan 4) tetap berguna di era apa pun.

### Ringkasan Bab 14

- Komputasi spasial memakai ruang 3D sebagai antarmuka dengan masukan pandangan, tangan, dan suara.
- Kenyamanan fisik, ergonomi, aksesibilitas, dan privasi biometrik adalah prioritas.
- Multimodal dan antarmuka tak terlihat mengurangi beban interaksi tetapi menantang visibilitas, kontrol, dan kepercayaan.
- Nilai tren secara kritis dengan pertanyaan masalah, alternatif, biaya, dan keadilan.

### Latihan Bab 14

1. Sebutkan tiga penyebab ketidaknyamanan fisik pada perangkat imersif dan satu mitigasi untuk masing-masing.
2. Rancang cara agar pengguna tahu "apa yang dapat dilakukan" pada antarmuka suara tanpa layar.
3. Pilih satu tren (misalnya kacamata pintar). Jawab lima pertanyaan penilaian kritis pada 14.7.
4. Mengapa data pelacakan mata dianggap sensitif?

---

## Bab 15. Etika, Privasi, dan Dampak Sosial

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Mengenali pola gelap (_dark patterns_) dan menghindarinya.
2. Menerapkan prinsip privasi sejak desain.
3. Mempertimbangkan kesejahteraan digital, keadilan, dan keberlanjutan.
4. Menggunakan kerangka sederhana untuk keputusan desain etis.

### 15.1 Mengapa Etika Penting dalam IMK?

Desainer dan developer memengaruhi perilaku jutaan orang dengan keputusan kecil: nilai bawaan, posisi tombol, kata pada dialog. Pengaruh ini membawa tanggung jawab. Kode etik profesi seperti **ACM Code of Ethics and Professional Conduct** menegaskan prinsip menghindari bahaya, jujur, menghormati privasi, dan menyumbang bagi kesejahteraan masyarakat.

### 15.2 Pola Gelap (_Dark Patterns_)

**Pola gelap** adalah desain yang menipu atau memanipulasi pengguna agar melakukan hal yang tidak mereka inginkan atau tidak mereka pahami.

|Pola|Penjelasan|Contoh|Alternatif etis|
|---|---|---|---|
|_Confirmshaming_|Pilihan menolak ditulis memalukan|"Tidak, saya tidak mau hemat"|Pilihan setara: "Tidak, terima kasih"|
|_Roach motel_|Mudah masuk, sulit keluar|Berlangganan satu klik, berhenti harus menelepon|Berhenti semudah berlangganan|
|_Hidden costs_|Biaya muncul di akhir proses|Biaya layanan baru terlihat saat bayar|Tampilkan total sejak awal|
|_Forced continuity_|Uji coba gratis berubah jadi bayar tanpa pengingat jelas|Penagihan otomatis tanpa notifikasi|Pengingat sebelum penagihan|
|_Misdirection_|Mengalihkan perhatian dari opsi tertentu|Tombol "Terima" besar, "Tolak" tersembunyi|Visual setara untuk pilihan penting|
|_Fake urgency/scarcity_|Hitung mundur atau stok palsu|"Tersisa 1!" padahal tidak benar|Informasi jujur|
|_Nagging_|Terus-menerus mengganggu|Pop-up berulang minta aktifkan notifikasi|Hormati jawaban, tanyakan seperlunya|
|_Preselected options_|Opsi merugikan sudah dicentang|Persetujuan pemasaran tercentang otomatis|Biarkan kosong, pengguna memilih aktif|
|_Privacy zuckering_|Menggiring pengguna berbagi data lebih banyak|Pengaturan privasi rumit dan menyesatkan|Pengaturan jelas, bawaan menjaga privasi|

Pola gelap sering meningkatkan metrik jangka pendek (konversi, pendapatan) tetapi merusak kepercayaan jangka panjang, dan semakin mendapat sorotan regulator di berbagai negara. Metrik yang Anda optimalkan membentuk produk Anda, jadi pilih metrik yang mencerminkan nilai nyata bagi pengguna.

### 15.3 Privasi Sejak Desain

_Privacy by design_ berarti perlindungan data menjadi bagian dari rancangan sejak awal, bukan tambahan di akhir. Prinsip praktis:

1. **Minimalisasi data**: kumpulkan hanya yang benar-benar diperlukan.
2. **Pembatasan tujuan**: pakai data hanya untuk tujuan yang dijelaskan.
3. **Transparansi**: jelaskan dengan bahasa sederhana apa yang dikumpulkan dan mengapa.
4. **Persetujuan bermakna**: bebas, spesifik, dan dapat ditarik; bukan dialog yang dirancang untuk disetujui tanpa dibaca.
5. **Kendali pengguna**: akses, koreksi, unduh, dan hapus data mudah dilakukan.
6. **Bawaan yang melindungi**: pengaturan awal paling ramah privasi.
7. **Keamanan**: enkripsi, pembatasan akses, penyimpanan secukupnya.

Di Indonesia, pelindungan data pribadi diatur dalam **Undang-Undang Nomor 27 Tahun 2022 tentang Pelindungan Data Pribadi**. Sebagai developer, kenali kewajiban dasar seperti dasar pemrosesan, hak subjek data, dan kewajiban menjaga keamanan. Karena regulasi dan peraturan turunannya dapat berkembang, rujuk teks dan panduan resmi terbaru serta konsultasikan ahli hukum untuk produk nyata.

### 15.4 Kesejahteraan Digital

Beberapa mekanisme desain dapat mendorong penggunaan kompulsif: gulir tanpa akhir, putar otomatis, notifikasi pemantik, hadiah variabel (seperti mesin slot), dan "streak" yang menimbulkan kecemasan.

Pertimbangan:

- Beri **kontrol** kepada pengguna: batas waktu, mode senyap, pengaturan notifikasi yang rinci.
- Hindari mengeksploitasi kerentanan psikologis, terutama pada **anak-anak dan remaja**.
- Ukur keberhasilan dari **nilai yang diterima pengguna**, bukan hanya waktu layar.
- Beri jeda alami (titik berhenti) pada alur yang berpotensi tak berujung.

### 15.5 Keadilan dan Bias

- **Bias data dan algoritma**: sistem berbasis data dapat merugikan kelompok yang kurang terwakili dalam data (misalnya pengenalan suara atau wajah yang kurang akurat bagi kelompok tertentu).
- **Bias desain**: asumsi tentang nama (satu nama depan dan satu nama belakang), alamat, gender, atau keluarga dapat mengecualikan banyak orang.
- **Representasi**: ilustrasi dan contoh perlu mencerminkan keberagaman nyata.

Mitigasi: uji pada kelompok beragam, libatkan komunitas terdampak, dokumentasikan keputusan dan batasan, dan sediakan jalur koreksi.

### 15.6 Keberlanjutan

Antarmuka juga berdampak lingkungan:

- Halaman dan aplikasi yang berat meningkatkan konsumsi energi dan data.
- Dorongan ganti perangkat karena aplikasi tidak lagi mendukung perangkat lama menambah limbah elektronik.
- Fitur AI yang berat memerlukan banyak energi komputasi di pusat data.

Praktik: optimalkan ukuran aset, dukung perangkat lama sewajarnya, pakai AI hanya bila bernilai, dan pertimbangkan pengaturan hemat data.

### 15.7 Anak-Anak, Lansia, dan Kelompok Rentan

- **Anak-anak**: perlu perlindungan tambahan atas data dan konten, serta desain sesuai tahap perkembangan.
- **Lansia**: pertimbangkan penglihatan, pendengaran, ketangkasan, dan kecepatan belajar; jangan mengasumsikan ketidakmampuan.
- **Kelompok rentan** (korban kekerasan, orang dengan kondisi kesehatan sensitif): pertimbangkan skenario penyalahgunaan, misalnya fitur pelacakan lokasi yang bisa dipakai untuk menguntit.

### 15.8 Kerangka Pertanyaan Etis

Sebelum merilis fitur, tanyakan:

1. **Manfaat**: siapa yang diuntungkan dan bagaimana?
2. **Bahaya**: siapa yang bisa dirugikan, termasuk lewat penyalahgunaan?
3. **Kejujuran**: apakah pengguna memahami apa yang terjadi?
4. **Persetujuan dan kendali**: apakah pengguna dapat memilih dan membatalkan?
5. **Keadilan**: apakah semua kelompok diperlakukan adil?
6. **Akuntabilitas**: siapa yang bertanggung jawab dan bagaimana pengguna dapat mengajukan keberatan?
7. **Uji "halaman depan"**: jika keputusan ini diberitakan secara terbuka, apakah kami nyaman?

### Ringkasan Bab 15

- Pola gelap menyesatkan pengguna; hindari dan sediakan alternatif jujur.
- Privasi sejak desain dan kepatuhan pada hukum pelindungan data adalah dasar kepercayaan.
- Pertimbangkan kesejahteraan, keadilan, kelompok rentan, dan keberlanjutan dalam setiap keputusan.

### Latihan Bab 15

1. Temukan dua contoh pola gelap pada aplikasi atau situs yang pernah Anda pakai. Jelaskan dan usulkan perbaikan.
2. Tulis ulang dialog persetujuan data agar jujur dan jelas (maksimal 60 kata).
3. Mengapa nilai bawaan (_default_) membawa tanggung jawab etis?
4. Rancang tiga fitur yang membantu kesejahteraan digital pada aplikasi media sosial.
5. Gunakan kerangka 15.8 untuk menilai fitur "bagikan lokasi real-time ke teman".

---

## Bab 16. Proyek Akhir dan Peta Jalan Belajar

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

1. Menjalankan proyek IMK dari awal sampai akhir dengan jadwal terstruktur.
2. Mengukur hasil proyek dengan rubrik.
3. Menyusun peta jalan belajar dan portofolio.

### 16.1 Proyek Akhir: Redesain Layanan Digital

**Tujuan:** mengidentifikasi masalah usabilitas pada satu layanan digital nyata (misalnya aplikasi akademik kampus, aplikasi perpustakaan, layanan kesehatan, atau layanan publik) lalu merancang, mengujicoba, dan mengevaluasi perbaikannya.

**Ketentuan:** kerja individu atau kelompok 2 sampai 4 orang. Pilih layanan yang bisa Anda akses dan pengguna sasarannya bisa Anda temui.

**Jadwal contoh (8 minggu):**

|Minggu|Kegiatan|Keluaran|
|---|---|---|
|1|Pilih layanan, tentukan pengguna sasaran, rumuskan pertanyaan riset|Proposal singkat (1 halaman)|
|2|Analisis awal: evaluasi heuristik dan analisis kompetitor|Daftar masalah dan peluang|
|3|Riset pengguna: 5 sampai 8 wawancara dan/atau observasi|Catatan dan rekaman (dengan persetujuan)|
|4|Sintesis: diagram afinitas, persona, peta perjalanan, pernyataan masalah|Dokumen sintesis|
|5|Ideasi dan struktur: sketsa, alur pengguna, arsitektur informasi|Sketsa dan alur|
|6|Prototipe resolusi menengah atau tinggi, mempertimbangkan aksesibilitas|Prototipe interaktif|
|7|Uji usabilitas: 5 partisipan, tugas berbasis skenario, SUS|Data uji dan temuan|
|8|Iterasi, laporan akhir, dan presentasi|Laporan dan presentasi|

### 16.2 Struktur Laporan

1. Latar belakang dan tujuan
2. Pengguna sasaran dan konteks pemakaian
3. Metode riset dan temuan
4. Persona dan peta perjalanan
5. Pernyataan masalah dan kebutuhan
6. Proses desain: sketsa, alur, keputusan, alasan
7. Prototipe akhir
8. Hasil evaluasi: metrik, SUS, temuan, perbaikan
9. Pertimbangan aksesibilitas, privasi, dan etika
10. Keterbatasan dan rencana lanjutan
11. Lampiran: panduan wawancara, skenario tugas, data mentah ringkas

### 16.3 Rubrik Penilaian

|Aspek|Bobot|Kriteria unggul|
|---|---|---|
|Pemahaman pengguna|20 persen|Riset dengan pengguna nyata, temuan mendalam, persona berbasis data|
|Proses dan penalaran desain|20 persen|Keputusan dijelaskan dengan bukti dan prinsip IMK|
|Kualitas solusi|20 persen|Menjawab masalah; konsisten; heuristik terpenuhi|
|Aksesibilitas dan etika|15 persen|Memenuhi dasar WCAG 2.2 AA pada prototipe; pertimbangan privasi dan pola gelap|
|Evaluasi|15 persen|Uji sesuai metode; data analisis jujur; iterasi nyata|
|Komunikasi|10 persen|Laporan jelas dan presentasi efektif|

### 16.4 Peta Jalan Belajar Lanjutan

**Bulan 1 sampai 2: Dasar**

- Pahami Bab 1 sampai 5.
- Bedah 5 aplikasi: tulis temuan heuristik.
- Latihan menulis mikroteks.

**Bulan 3 sampai 4: Riset dan Proses**

- Lakukan 5 wawancara pengguna.
- Latih sintesis dan pembuatan persona dan peta perjalanan.
- Pelajari alat prototipe.

**Bulan 5 sampai 6: Evaluasi dan Aksesibilitas**

- Jalankan uji usabilitas dan hitung SUS.
- Audit aksesibilitas pada situs nyata dengan alat otomatis, papan ketik, dan pembaca layar.
- Pelajari WCAG 2.2.

**Bulan 7 sampai 9: Implementasi**

- Bangun antarmuka dengan HTML, CSS, JavaScript atau kerangka kerja seperti React; terapkan sistem desain.
- Belajar kinerja web dan pengukuran.

**Bulan 10 sampai 12: Spesialisasi**

- Pilih arah: riset UX, desain interaksi, rekayasa frontend yang berfokus aksesibilitas, desain produk AI, desain spasial, atau riset IMK akademik.
- Buat satu studi kasus portofolio mendalam.

### 16.5 Keterampilan yang Dicari

|Kategori|Contoh|
|---|---|
|Teknis|HTML, CSS, JavaScript, kerangka kerja antarmuka, dasar basis data dan API, dasar AI/ML untuk produk|
|Desain|Alur, struktur, tipografi, warna, sistem desain, prototipe|
|Riset|Wawancara, survei, uji usabilitas, analisis data|
|Aksesibilitas|WCAG, teknologi bantu, pengujian|
|Komunikasi|Menulis, presentasi, bercerita dengan data|
|Kolaborasi|Bekerja dengan produk, engineer, bisnis|
|Etika|Privasi, keadilan, pertimbangan dampak|
|Literasi AI|Merancang dan mengevaluasi pengalaman berbasis AI|

### 16.6 Membangun Portofolio

Portofolio yang baik menunjukkan **proses berpikir**, bukan hanya gambar akhir:

- Masalah dan konteks
- Peran Anda
- Riset dan bukti
- Alternatif yang dipertimbangkan dan alasan memilih
- Hasil dan metrik
- Pelajaran dan hal yang akan diubah

Pilih 2 sampai 3 studi kasus mendalam daripada 10 yang dangkal.

### 16.7 Menjaga Pengetahuan Tetap Relevan

Karena teknologi berubah, biasakan:

- Mengikuti sumber utama: **W3C WAI** (aksesibilitas), dokumentasi pedoman platform (Material Design, Apple HIG, Fluent), **Nielsen Norman Group**, makalah **ACM CHI** dan konferensi IMK lain.
- Mengikuti perkembangan peraturan: pelindungan data, aksesibilitas, dan tata kelola AI di Indonesia dan negara tujuan pasar Anda.
- Mencoba produk dan perangkat baru secara kritis dengan pertanyaan di 14.7.
- Membaca laporan tren tahunan, sambil membedakan fakta dan promosi.
- Menulis ulang catatan Anda setiap tahun: apa yang berubah, apa yang bertahan.

### Ringkasan Bab 16

- Proyek akhir menggabungkan seluruh siklus: riset, desain, prototipe, evaluasi, aksesibilitas, dan etika.
- Peta jalan belajar bertahap membantu membangun keterampilan nyata.
- Relevansi jangka panjang berasal dari memahami prinsip, bukan menghafal alat.

---

## Lampiran A. Glosarium

|Istilah|Padanan Inggris|Arti singkat|
|---|---|---|
|Aksesibilitas|_Accessibility_ (a11y)|Kemampuan produk dipakai oleh orang dengan beragam kemampuan|
|Affordance|_Affordance_|Kemungkinan aksi yang ditawarkan oleh sebuah objek kepada pelaku|
|Agen AI|_AI agent_|Sistem AI yang merencanakan dan melakukan rangkaian tindakan untuk mencapai tujuan|
|Arsitektur informasi|_Information architecture_|Pengorganisasian dan pelabelan konten agar mudah ditemukan|
|Beban kognitif|_Cognitive load_|Total usaha mental yang diperlukan untuk suatu tugas|
|Bias otomatisasi|_Automation bias_|Kecenderungan terlalu percaya pada keluaran sistem otomatis|
|Desain berpusat pada pengguna|_User-centered design_|Pendekatan desain yang menempatkan kebutuhan pengguna sebagai pusat proses|
|Desain responsif|_Responsive design_|Tampilan yang menyesuaikan ukuran dan kemampuan perangkat|
|Diagram afinitas|_Affinity diagram_|Pengelompokan catatan temuan untuk menemukan tema|
|Evaluasi heuristik|_Heuristic evaluation_|Pemeriksaan antarmuka oleh pakar terhadap daftar prinsip|
|Fokus|_Focus_|Elemen yang sedang menerima masukan papan ketik|
|Heuristik|_Heuristic_|Aturan praktis berdasarkan pengalaman|
|Hierarki visual|_Visual hierarchy_|Pengaturan elemen agar urutan pentingnya jelas|
|Jurang evaluasi|_Gulf of evaluation_|Kesenjangan antara keadaan sistem dan pemahaman pengguna|
|Jurang pelaksanaan|_Gulf of execution_|Kesenjangan antara niat pengguna dan aksi yang tersedia|
|Kemudahan ditemukan|_Discoverability_|Seberapa mudah pengguna menemukan aksi yang tersedia|
|Kriteria penerimaan|_Acceptance criteria_|Syarat agar sebuah fitur dianggap selesai dan benar|
|Manipulasi langsung|_Direct manipulation_|Bertindak langsung pada representasi objek dengan umpan balik segera|
|Mikroteks|_Microcopy_|Teks kecil pada antarmuka seperti label dan pesan galat|
|Model mental|_Mental model_|Pemahaman pengguna tentang cara kerja sebuah sistem|
|Pemetaan|_Mapping_|Hubungan antara kontrol dan efeknya|
|Persona|_Persona_|Representasi fiktif berbasis data dari kelompok pengguna|
|Pola gelap|_Dark pattern_|Desain yang menipu atau memanipulasi pengguna|
|Prototipe|_Prototype_|Representasi awal desain yang dapat dicoba|
|Pembaca layar|_Screen reader_|Perangkat lunak yang membacakan isi layar|
|Signifier|_Signifier_|Petunjuk yang menunjukkan di mana dan bagaimana aksi dilakukan|
|Sistem desain|_Design system_|Kumpulan komponen, token, dan pedoman yang dapat dipakai ulang|
|Slip|_Slip_|Kesalahan pelaksanaan padahal niat benar|
|Mistake|_Mistake_|Kesalahan karena niat atau rencana yang salah|
|SUS|_System Usability Scale_|Kuesioner 10 butir untuk mengukur kegunaan yang dirasakan|
|Teknologi bantu|_Assistive technology_|Perangkat atau perangkat lunak yang membantu penyandang disabilitas|
|Token desain|_Design token_|Nilai desain bernama (warna, jarak) sebagai satu sumber kebenaran|
|Uji usabilitas|_Usability testing_|Mengamati pengguna menyelesaikan tugas pada produk atau prototipe|
|Umpan balik|_Feedback_|Respons sistem terhadap aksi pengguna|
|Usabilitas|_Usability_|Kemudahan, efisiensi, dan kepuasan pemakaian untuk tujuan tertentu|
|Wizard of Oz|_Wizard of Oz_|Teknik prototipe di mana manusia berperan sebagai sistem di belakang layar|
|WCAG|_Web Content Accessibility Guidelines_|Pedoman aksesibilitas dari W3C|
|XR|_Extended Reality_|Payung untuk VR, AR, dan MR|

---

## Lampiran B. Jawaban Latihan

Jawaban berikut bersifat ringkas. Untuk latihan terbuka, jawaban Anda bisa berbeda selama didukung alasan yang kuat.

### Bab 1

1. UI adalah tampilan dan elemen yang dilihat dan disentuh pengguna; UX adalah keseluruhan pengalaman. Contoh: aplikasi dengan tampilan indah tetapi proses pembayaran berbelit sehingga pengguna gagal menyelesaikan pembelian.
2. Jawaban bebas. Contoh pada aplikasi transportasi daring: efektivitas (berhasil memesan kendaraan sampai tujuan), efisiensi (memesan dengan beberapa ketukan), kepuasan (merasa nyaman dan aman).
3. Karena kemudahan bergantung pada siapa yang memakai (kemampuan, pengalaman), untuk apa (tujuan), dan di mana atau kapan (konteks); produk yang baik untuk satu kelompok belum tentu baik bagi yang lain.
4. Contoh: informatika (membangun sistem), psikologi kognitif (memahami perhatian dan memori), desain (tata letak dan estetika).

### Bab 2

1. `jarak=600, lebar=30`: ID = log2(600/30 + 1) = log2(21) ≈ 4,392; MT ≈ 0,1 + 0,15 x 4,392 ≈ 0,759 detik. `lebar=60`: ID = log2(11) ≈ 3,459; MT ≈ 0,619 detik. Kesimpulan: memperbesar target mempercepat penjangkauan.
2. Pengguna dengan buta warna merah-hijau mungkin tidak membedakannya, dan pada kondisi layar silau pun kontras warna bisa hilang. Tambahkan ikon (centang) dan teks "Berhasil".
3. Melanggar prinsip mengurangi beban memori kerja (_recognition over recall_). Perbaikan: izinkan tempel (_paste_), isi otomatis, atau tampilkan kode pada layar yang sama.
4. Intrinsik: kerumitan bawaan, misalnya memahami konsep bunga atau biaya transfer antar bank. Ekstraneus: istilah asing, menu berantakan, atau langkah berulang yang ditambahkan desain.
5. Contoh: tangan sedang membawa barang, silau matahari, ruang bising, tergesa-gesa, jaringan lambat.

### Bab 3

1. (a) Suara, karena tangan dan mata sibuk. (b) Baris perintah, karena efisien, dapat diotomatisasi, dan fleksibel. (c) Manipulasi langsung berbasis sentuh dengan ikon dan label jelas.
2. Layar sentuh tidak memiliki kursor yang melayang sehingga tidak ada keadaan hover; informasi penting harus tersedia lewat ketukan.
3. Pengguna dapat menekan tombol berulang kali sehingga data tersimpan ganda atau terjadi permintaan ganda; juga tidak ada petunjuk bahwa proses berjalan.
4. Contoh: menyeret elemen pada kanvas desain, memutar peta dengan jari, mengubah ukuran jendela dengan menarik tepi.

### Bab 4

1. Affordance: apa yang mungkin dilakukan (elemen dapat diklik). Signifier: petunjuk yang menunjukkan (teks biru bergaris bawah, tombol berbayang).
2. Risiko slip (salah ketuk). Perbaikan: konfirmasi untuk penghapusan dan tombol urungkan atau tempat sampah sementara.
3. Contoh: "Pesanan belum dapat diproses karena ada gangguan pada server kami. Coba lagi sebentar lagi. Jika tetap gagal, hubungi bantuan dengan kode 500."
4. Jawaban bebas. Contoh baik: penggeser kecerahan yang bergerak ke kanan untuk lebih terang. Contoh buruk: dua tombol dengan tata letak horizontal tetapi urutannya tidak sesuai urutan langkah.
5. Pada tahap "menyusun urutan aksi" atau "melakukan aksi" (sisi pelaksanaan), karena pengguna tidak tahu bahwa elemen itu bisa ditekan (jurang pelaksanaan).

### Bab 5

1. Jawaban bebas. Contoh: (1) tidak ada indikator saat pencarian dijalankan; (4) label tombol tidak konsisten; (9) pesan galat tidak jelas.
2. Misal: tombol "Keluar tanpa menyimpan" dan "Kembali dan simpan", dengan judul "Perubahan Anda belum disimpan".
3. Konsistensi eksternal memanfaatkan pengetahuan pengguna dari produk lain. Boleh melanggar bila ada alasan kuat dan teruji, misalnya inovasi yang terbukti lebih mudah, dengan petunjuk jelas.
4. Contoh: ilustrasi sederhana, teks "Anda belum punya pesanan. Mulai belanja untuk melihat riwayat di sini.", dan tombol "Mulai belanja".

### Bab 6

1. Jawaban bebas. Contoh: (1) mengamati antrean di klinik dan mewawancarai mahasiswa, (2) menetapkan kebutuhan "mengetahui estimasi giliran", (3) membuat sketsa dan prototipe, (4) menguji dengan 5 mahasiswa lalu memperbaiki.
2. Contoh: "Sebagai pengguna yang lupa kata sandi, saya ingin menerima tautan reset ke email saya agar dapat masuk kembali." Kriteria: tautan kedaluwarsa dalam waktu tertentu; pesan konsisten walau email tidak terdaftar (untuk keamanan); kata sandi baru harus memenuhi aturan dan ditampilkan aturannya.
3. Diverge: memperluas pilihan dan ide; converge: menyaring dan memilih. Keduanya diperlukan agar tidak terpaku pada solusi pertama dan tidak berhenti pada kumpulan ide tanpa keputusan.
4. Contoh: biaya perubahan kecil pada tahap awal, risiko lebih rendah, belum ada ketergantungan kode, dan tim belum terikat emosional pada solusi tertentu.

### Bab 7

1. "Bagaimana pendapat Anda tentang fitur favorit? Ceritakan bagaimana Anda memakainya."
2. Contoh: (1) Ceritakan bagaimana Anda mengatur jadwal kuliah semester ini. (2) Apa yang terakhir kali Anda lakukan ketika jadwal bentrok? (3) Alat apa yang Anda pakai? (4) Apa bagian yang paling merepotkan? (5) Apa yang Anda lakukan untuk mengatasinya?
3. Persona berbasis data mencerminkan pengguna nyata; tanpa data, persona hanya asumsi dan membuat tim merasa yakin pada hal yang belum tentu benar.
4. Contoh tahap: menyadari kebutuhan, mencari tahu prosedur, mengajukan, menunggu, menerima surat.

### Bab 8

1. Jawaban bebas. Periksa apakah elemen yang menonjol adalah aksi atau informasi utama halaman.
2. Lihat kode pada 8.7, gunakan `grid-template-columns: 1fr;` dasar dan `repeat(2, 1fr)` pada `min-width: 768px`.
3. Menghormati pengaturan ukuran huruf pengguna dan membuat penskalaan lebih konsisten serta mudah disesuaikan.
4. Contoh: kedekatan (label dekat kolomnya, jarak antar kelompok kolom lebih besar) dan kemiripan (semua kolom bergaya sama; tombol utama berbeda).

### Bab 9

1. Jawaban bebas (sketsa).
2. Contoh: setelah koneksi terputus, tampilkan pesan jelas, simpan isian pengguna, tombol "Coba lagi" otomatis atau manual, dan jangan kehilangan data yang sudah diisi.
3. Saat teknologi belum ada atau mahal, misalnya menguji asisten percakapan: seorang rekan membalas secara manual di belakang layar.
4. Jawaban bebas. Perhatikan perbedaan label dan struktur yang dibuat peserta.

### Bab 10

1. Ganjil: (5-1)+(5-1)+(4-1)+(5-1)+(5-1) = 4+4+3+4+4 = 19. Genap: (5-1)+(5-2)+(5-1)+(5-2)+(5-1) = 4+3+4+3+4 = 18. Total 37 x 2,5 = 92,5.
2. Contoh: "Anda ingin membeli sebuah buku dan membayarnya dengan dompet digital. Lakukan pembelian ini."
3. Jawaban bebas dengan tiga temuan, heuristik terkait, dan skor keparahan.
4. Hasil awal dipengaruhi variasi acak dan efek kebaruan; belum mencakup siklus perilaku (hari kerja vs akhir pekan) dan berisiko memberi kesimpulan keliru.

### Bab 11

1. `<button type="button" onclick="kirim()">Kirim</button>`. Tersedia otomatis: dapat difokuskan dengan Tab, dapat diaktifkan dengan Enter dan Spasi, diumumkan sebagai tombol oleh pembaca layar.
2. Jalankan fungsi `rasio_kontras("#2a6fdb", "#ffffff")`. Bandingkan hasil dengan 4,5 untuk teks biasa. Bila di bawah 4,5, tidak lolos AA dan perlu warna lebih gelap.
3. Contoh: "Grafik batang jumlah pengunjung perpustakaan per bulan; tertinggi pada Mei dengan sekitar 3.200 pengunjung, terendah pada Desember sekitar 1.100." (angka contoh)
4. Placeholder hilang saat mengetik, sering berkontras rendah, dan tidak selalu dibaca teknologi bantu; label tetap terlihat dan terhubung dengan kolom.
5. Jawaban bebas.

### Bab 12

1. Jawaban bebas; aksi sering sebaiknya berada di bagian bawah atau tengah layar.
2. Pengguna belum paham manfaatnya sehingga menolak; alternatifnya meminta izin saat fitur yang memerlukan lokasi dipakai, dengan penjelasan singkat.
3. Jam tangan: interaksi singkat dan informasi ringkas; desktop analis data: informasi padat, banyak jendela, pintasan dan analisis mendalam.
4. Elemen bergeser saat dimuat dapat membuat pengguna salah mengetuk, kehilangan posisi baca, dan frustrasi.

### Bab 13

1. Jawaban bebas, gunakan empat fase di 13.3 sebagai kerangka penilaian.
2. Tampilkan: daftar penerima (atau ringkasan dan akses ke daftar lengkap), isi email, waktu kirim, tombol "Kirim", "Edit", "Batal"; peringatan karena aksi tidak bisa ditarik kembali; bila bisa, opsi kirim ke diri sendiri dulu.
3. (a) Tingkat 3 atau 4 (rendah risiko, dapat dibalik); (b) tingkat 1 atau 2 (berisiko tinggi, perlu persetujuan eksplisit); (c) tingkat 2 atau 3 (menyiapkan lalu meminta persetujuan, melibatkan pihak lain).
4. Bias otomatisasi: terlalu mempercayai keluaran sistem. Dikurangi dengan menampilkan sumber atau bukti yang dapat dicek, dan merancang langkah tinjauan yang mudah untuk keputusan penting.
5. AI dapat menggemakan stereotip dan rata-rata data pelatihan, tidak memiliki pengalaman nyata, konteks, dan emosi pengguna spesifik; wawancara nyata mengungkap perilaku dan kebutuhan yang tidak terduga.

### Bab 14

1. Contoh: latensi tinggi (tingkatkan laju bingkai, turunkan latensi), gerakan kamera paksa (beri kendali pengguna), lengan terangkat lama (letakkan konten pada posisi nyaman, izinkan duduk).
2. Contoh: sapaan awal yang menyebut beberapa kemampuan utama, perintah "Apa yang bisa kamu lakukan?", saran contoh perintah setelah beberapa saat diam, dan pesan yang menawarkan opsi saat perintah tidak dikenali.
3. Jawaban bebas.
4. Karena dapat mengungkap perhatian, minat, kondisi kesehatan, atau keadaan emosi seseorang, termasuk hal yang tidak mereka sadari.

### Bab 15

1. Jawaban bebas; rujuk tabel 15.2.
2. Contoh: "Kami meminta lokasi Anda hanya untuk menampilkan toko terdekat. Lokasi tidak dijual dan dihapus setelah 24 jam. Anda dapat mengubah pilihan ini kapan saja di Pengaturan." Pilihan: "Izinkan" dan "Tidak sekarang" bertampilan setara.
3. Karena kebanyakan orang tidak mengubah nilai bawaan, sehingga pembuat desain secara efektif menentukan pilihan bagi mayoritas pengguna.
4. Contoh: batas waktu harian dengan pengingat, jeda "Sudah waktunya istirahat" setelah gulir panjang, pengaturan notifikasi rinci dan mode fokus.
5. Manfaat: koordinasi dan keselamatan. Bahaya: penguntitan, kekerasan, pelacakan tanpa persetujuan. Persetujuan dan kendali: izin eksplisit, durasi terbatas, indikator jelas ketika berbagi aktif, mudah dihentikan. Keadilan dan akuntabilitas: pertimbangkan kelompok rentan; sediakan jalur pelaporan dan penyalahgunaan.

---

## Lampiran C. Daftar Periksa Desain

### Daftar Periksa Usabilitas Cepat

- Apakah pengguna tahu di mana mereka berada dan apa yang bisa dilakukan?
- Apakah setiap aksi memberi umpan balik yang jelas?
- Apakah aksi penting dapat dibatalkan atau diurungkan?
- Apakah istilah dan label memakai bahasa pengguna dan konsisten?
- Apakah kesalahan dicegah, dan bila terjadi, dijelaskan beserta solusinya?
- Apakah pengguna tidak dipaksa mengingat informasi dari layar lain?
- Apakah ada satu aksi utama yang jelas pada setiap layar?
- Apakah alur penting dapat diselesaikan dengan sedikit langkah?
- Apakah halaman cepat dan tetap berguna pada koneksi lambat?

### Daftar Periksa Aksesibilitas Cepat

- Apakah seluruh fungsi dapat dipakai dengan papan ketik saja?
- Apakah fokus selalu terlihat jelas dan urutannya logis?
- Apakah kontras teks minimal 4,5 : 1 (teks besar 3 : 1)?
- Apakah informasi tidak hanya disampaikan lewat warna?
- Apakah gambar bermakna punya teks alternatif dan gambar dekoratif ditandai?
- Apakah setiap kolom formulir punya label terhubung dan pesan galat yang jelas?
- Apakah judul dan landmark terstruktur, dan `lang` diatur?
- Apakah video punya takarir dan audio punya transkrip?
- Apakah halaman tetap terbaca pada zoom 200 persen dan lebar sempit?
- Apakah target sentuh cukup besar dan berjarak?
- Apakah animasi menghormati preferensi kurangi gerak?
- Apakah sudah diuji dengan alat otomatis, papan ketik, dan pembaca layar?

### Daftar Periksa Fitur AI

- Apakah pengguna paham apa yang bisa dan tidak bisa dilakukan fitur ini?
- Apakah ada cara mudah untuk menolak, mengedit, atau mengurungkan hasil?
- Apakah aksi berisiko memerlukan persetujuan eksplisit?
- Apakah sumber atau alasan ditampilkan bila relevan?
- Apakah ada penanganan ketika AI tidak yakin atau salah?
- Apakah data pengguna diminimalkan dan pengguna bisa mengendalikannya?
- Apakah fitur dapat dipakai dengan teknologi bantu?
- Apakah sudah diuji pada kasus gagal dan pada beragam pengguna?

### Daftar Periksa Etika

- Apakah ada pola gelap?
- Apakah nilai bawaan melindungi kepentingan pengguna?
- Apakah persetujuan data jelas dan dapat ditarik?
- Siapa yang mungkin dirugikan atau terkecualikan?
- Apakah kami nyaman jika keputusan ini diberitakan terbuka?

---

## Lampiran D. Templat Dokumen

### D.1 Panduan Wawancara Pengguna

```
Judul riset     :
Tujuan          :
Partisipan      : (kriteria dan jumlah)
Durasi          : (misal 45 menit)

1. Pembukaan (5 menit)
   - Perkenalan, tujuan, izin merekam, hak berhenti kapan saja

2. Latar belakang (5 menit)
   - Ceritakan kegiatan Anda sehari-hari terkait [topik].

3. Pengalaman terakhir (15 menit)
   - Ceritakan terakhir kali Anda [melakukan aktivitas].
   - Apa yang Anda lakukan pertama? lalu apa?
   - Apa yang mudah? apa yang menyulitkan?

4. Alat dan solusi saat ini (10 menit)
   - Alat apa yang dipakai? Mengapa?
   - Apa yang dilakukan ketika terjadi masalah?

5. Penutup (5 menit)
   - Adakah hal lain yang ingin Anda sampaikan?
   - Terima kasih, penjelasan penggunaan data
```

### D.2 Lembar Persetujuan Partisipan (Ringkas)

```
Saya memahami bahwa:
- Tujuan riset ini adalah ...
- Sesi ini berlangsung sekitar ... menit dan akan direkam (suara/layar).
- Data saya hanya dipakai untuk ... dan dijaga kerahasiaannya.
- Partisipasi bersifat sukarela dan saya boleh berhenti kapan saja
  tanpa konsekuensi.
- Hasil riset akan dilaporkan tanpa mengungkap identitas saya.

Nama      :
Tanggal   :
Tanda tangan / persetujuan lisan terekam:
```

### D.3 Skenario Tugas Uji Usabilitas

```
Tugas     : T1
Skenario  : (konteks dan tujuan, tanpa memberi petunjuk cara)
Kondisi sukses  : (apa yang dianggap berhasil)
Metrik    : berhasil/gagal, waktu, jumlah galat, SEQ (1 sampai 7)
Catatan pengamat :
```

### D.4 Catatan Temuan Usabilitas

|ID|Tugas|Masalah (apa yang terjadi)|Bukti (kutipan/rekaman)|Keparahan (0 sampai 4)|Rekomendasi|
|---|---|---|---|---|---|
|||||||

### D.5 Format Pernyataan Masalah

```
[Pengguna] membutuhkan cara untuk [kebutuhan]
karena [wawasan/hambatan yang ditemukan].

Contoh:
Mahasiswa membutuhkan cara untuk mengetahui ketersediaan ruang belajar
secara langsung karena mereka sering datang ke perpustakaan
dan mendapati semua ruang penuh.
```

---

## Daftar Pustaka

### Buku

1. Norman, D. A. _The Design of Everyday Things_ (edisi revisi dan perluasan). Basic Books.
2. Nielsen, J. _Usability Engineering_. Morgan Kaufmann, 1993.
3. Shneiderman, B., Plaisant, C., Cohen, M., Jacobs, S., dan Elmqvist, N. _Designing the User Interface: Strategies for Effective Human-Computer Interaction_. Pearson (edisi terbaru).
4. Preece, J., Rogers, Y., dan Sharp, H. _Interaction Design: Beyond Human-Computer Interaction_. Wiley (edisi terbaru).
5. Dix, A., Finlay, J., Abowd, G. D., dan Beale, R. _Human-Computer Interaction_. Pearson.
6. Krug, S. _Don't Make Me Think, Revisited_. New Riders.
7. Cooper, A., Reimann, R., Cronin, D., dan Noessel, C. _About Face: The Essentials of Interaction Design_. Wiley.
8. Card, S. K., Moran, T. P., dan Newell, A. _The Psychology of Human-Computer Interaction_. Lawrence Erlbaum, 1983.

### Artikel dan Standar

9. Brooke, J. "SUS: A 'Quick and Dirty' Usability Scale." Dalam _Usability Evaluation in Industry_, 1996.
10. Nielsen, J. dan Landauer, T. K. "A Mathematical Model of the Finding of Usability Problems." Prosiding INTERCHI, 1993.
11. Amershi, S. dkk. "Guidelines for Human-AI Interaction." Prosiding ACM CHI, 2019.
12. Miller, G. A. "The Magical Number Seven, Plus or Minus Two." _Psychological Review_, 1956.
13. Cowan, N. "The Magical Number 4 in Short-Term Memory." _Behavioral and Brain Sciences_, 2001.
14. Fitts, P. M. "The Information Capacity of the Human Motor System in Controlling the Amplitude of Movement." _Journal of Experimental Psychology_, 1954.
15. ISO 9241-11 (usabilitas) dan ISO 9241-210 (proses desain berpusat pada manusia).
16. ACM Code of Ethics and Professional Conduct.

### Sumber Daring (periksa versi terbaru)

17. W3C. _Web Content Accessibility Guidelines (WCAG) 2.2_. https://www.w3.org/TR/WCAG22/
18. W3C. _W3C Accessibility Guidelines (WCAG) 3.0, Working Draft_. https://www.w3.org/TR/wcag-3.0/ (status rancangan per Maret 2026)
19. W3C Web Accessibility Initiative (WAI). https://www.w3.org/WAI/
20. IEEE Computer Society. "Top HCI Trends in 2026: The Rise of AI Agents and Invisible Interfaces" (28 April 2026). https://www.computer.org/publications/tech-news/trends/hci-trends-2026
21. Google PAIR. _People + AI Guidebook_. https://pair.withgoogle.com/guidebook/
22. Nielsen Norman Group. Artikel dan riset usabilitas. https://www.nngroup.com/
23. Google. Dokumentasi _Core Web Vitals_. https://web.dev/vitals/
24. Material Design (Google), Human Interface Guidelines (Apple), dan Fluent Design (Microsoft): dokumentasi resmi masing-masing.

### Peraturan (Indonesia)

25. Undang-Undang Republik Indonesia Nomor 8 Tahun 2016 tentang Penyandang Disabilitas.
26. Undang-Undang Republik Indonesia Nomor 27 Tahun 2022 tentang Pelindungan Data Pribadi.

> Catatan: peraturan dan standar dapat berubah. Untuk keperluan profesional atau hukum, selalu rujuk teks resmi terbaru dan konsultasikan dengan ahli yang berwenang.

---

_Akhir buku._