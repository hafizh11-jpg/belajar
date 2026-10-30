# Game Design Lanjutan untuk Developer Indie

**Subjudul:** Panduan Praktis Merancang Game Offline 2D dan 3D yang Berfokus pada Gameplay, dengan Cerita dan Lore Tanpa Voice Actor

**Edisi:** Era 2026/2027 dan seterusnya

**Bahasa:** Indonesia

**Target pembaca:** Pemula yang sudah mengenal dasar game development dan ingin naik ke tingkat game design lanjutan

---

## Daftar Isi

- [Bab 0. Cara Memakai Buku Ini dan Peta Lanskap 2026/2027+](#bab-0-cara-memakai-buku-ini-dan-peta-lanskap-20262027)
- [Bab 1. Pola Pikir Desainer Tingkat Lanjut](#bab-1-pola-pikir-desainer-tingkat-lanjut)
- [Bab 2. Arsitektur Loop: Core Loop, Secondary Loop, dan Meta Loop](#bab-2-arsitektur-loop-core-loop-secondary-loop-dan-meta-loop)
- [Bab 3. Game Feel dan Juice](#bab-3-game-feel-dan-juice)
- [Bab 4. Desain Sistem dan Emergent Gameplay](#bab-4-desain-sistem-dan-emergent-gameplay)
- [Bab 5. Matematika dan Balancing](#bab-5-matematika-dan-balancing)
- [Bab 6. Ekonomi Game dan Desain Randomness](#bab-6-ekonomi-game-dan-desain-randomness)
- [Bab 7. Desain Combat 2D dan 3D](#bab-7-desain-combat-2d-dan-3d)
- [Bab 8. Desain AI Musuh dan Companion](#bab-8-desain-ai-musuh-dan-companion)
- [Bab 9. Level Design Lanjutan](#bab-9-level-design-lanjutan)
- [Bab 10. Progression, Kurva Kesulitan, dan Aksesibilitas](#bab-10-progression-kurva-kesulitan-dan-aksesibilitas)
- [Bab 11. Procedural Generation dan Desain Roguelite](#bab-11-procedural-generation-dan-desain-roguelite)
- [Bab 12. Narrative Design Gameplay-First Tanpa Voice Actor](#bab-12-narrative-design-gameplay-first-tanpa-voice-actor)
- [Bab 13. UX, Onboarding, HUD, Kamera, dan Input](#bab-13-ux-onboarding-hud-kamera-dan-input)
- [Bab 14. Desain Khusus Game Offline](#bab-14-desain-khusus-game-offline)
- [Bab 15. Playtesting dan Iterasi Berbasis Data](#bab-15-playtesting-dan-iterasi-berbasis-data)
- [Bab 16. Produksi Indie: Scope, Prototipe, dan Dokumentasi](#bab-16-produksi-indie-scope-prototipe-dan-dokumentasi)
- [Bab 17. Studi Kasus Analisis Genre](#bab-17-studi-kasus-analisis-genre)
- [Bab 18. Proyek Akhir 12 Minggu](#bab-18-proyek-akhir-12-minggu)
- [Lampiran A. Template GDD Ringkas](#lampiran-a-template-gdd-ringkas)
- [Lampiran B. Template Laporan Playtest](#lampiran-b-template-laporan-playtest)
- [Lampiran C. Checklist Desain](#lampiran-c-checklist-desain)
- [Lampiran D. Glosarium](#lampiran-d-glosarium)
- [Lampiran E. Bahan Bacaan dan Sumber Belajar](#lampiran-e-bahan-bacaan-dan-sumber-belajar)

---

## Bab 0. Cara Memakai Buku Ini dan Peta Lanskap 2026/2027+

### 0.1 Untuk siapa buku ini

Buku ini ditulis untuk Anda yang sudah pernah, atau setidaknya paham konsep, membuat game sederhana (misalnya membuat karakter bergerak, melompat, dan menembak di sebuah engine). Sekarang Anda ingin naik level: bukan sekadar "game jalan", tetapi "game yang enak dimainkan, seimbang, dan membuat pemain bertahan bermain".

Isi buku ini adalah **Game Design tingkat lanjut**. Artinya kita tidak membahas cara memasang engine atau cara membuat sprite. Kita membahas **keputusan desain**: mengapa sebuah mekanik terasa memuaskan, bagaimana menyeimbangkan angka, bagaimana menyusun level agar pemain belajar tanpa dipaksa membaca tutorial, dan bagaimana menyampaikan cerita tanpa voice actor.

### 0.2 Batasan dan fokus buku

|Aspek|Keputusan dalam buku ini|
|---|---|
|Dimensi|2D dan 3D, dengan catatan perbedaan tiap bab|
|Mode|Offline, single-player. Tidak membahas multiplayer, matchmaking, atau live service|
|Fokus utama|Gameplay. Cerita dan lore adalah pendukung, bukan pusat|
|Suara|Tanpa voice actor. Narasi lewat teks, UI, desain level, SFX, musik, dan animasi|
|Skala|Tim kecil atau solo developer|
|Engine|Netral. Contoh kode berupa pseudocode agar bisa diterapkan di engine apa pun|

### 0.3 Cara membaca

Setiap bab memiliki pola yang sama:

1. **Tujuan bab**: apa yang akan Anda kuasai.
2. **Konsep inti**: penjelasan teknis dengan bahasa sederhana.
3. **Contoh dan rumus**: penerapan konkret.
4. **Kesalahan umum**: jebakan yang sering menimpa developer indie.
5. **Latihan**: tugas kecil. Kerjakan, jangan hanya dibaca.
6. **Ringkasan**: poin yang perlu diingat.

Saran urutan belajar: baca satu bab, kerjakan latihannya pada **satu proyek prototipe yang sama** sepanjang buku ini. Dengan begitu pada akhir buku Anda memiliki sebuah vertical slice (potongan game yang lengkap dan layak diuji) sebagai bukti kemampuan.

### 0.4 Lanskap industri 2026/2027+ yang relevan bagi desainer indie

Berikut tren umum yang memengaruhi keputusan desain. Anggap ini sebagai arah, bukan kepastian. Selalu cek kondisi terkini sebelum memutuskan.

1. **Pasar sangat ramai.** Jumlah game yang dirilis per tahun di platform PC besar sangat banyak. Konsekuensinya: game Anda harus bisa dijelaskan dalam satu kalimat dan terlihat menarik dalam beberapa detik (hook yang jelas).
2. **Perangkat handheld PC dan kontroler-first.** Banyak pemain memainkan game PC di perangkat genggam. Desain input, ukuran teks, dan UI sebaiknya nyaman untuk kontroler dan layar kecil sejak awal.
3. **Pemain menghargai respect for time.** Game yang pendek tetapi padat (sekitar 4 sampai 12 jam) dan tidak membuang waktu pemain cenderung diterima baik.
4. **Subgenre populer yang ramah indie:** roguelite, metroidvania, cozy game, puzzle, survival ringan, tactics ringkas, dan platformer presisi. Genre ini kuat pada gameplay dan efisien pada produksi.
5. **Aksesibilitas semakin menjadi ekspektasi dasar.** Opsi remap kontrol, ukuran teks, mode warna, dan opsi kesulitan bukan lagi fitur tambahan.
6. **Alat bantu AI dalam produksi.** Banyak developer memakai alat AI untuk brainstorming, prototyping, atau aset sementara. Dari sisi desain, ingat dua hal: keputusan desain tetap tanggung jawab Anda, dan periksa kebijakan platform serta aspek lisensi sebelum memakai aset hasil AI dalam rilis komersial.
7. **Demo dan wishlist sebagai strategi.** Demo yang menunjukkan inti gameplay dalam 20 sampai 30 menit sering dipakai untuk membangun minat. Artinya, desain Anda harus mampu menampilkan "momen terbaik" dengan cepat.

> Catatan: Buku ini sengaja tidak menyebut nomor versi engine. Versi berubah cepat. Prinsip desain di sini bertahan jauh lebih lama daripada versi perangkat lunak.

---

## Bab 1. Pola Pikir Desainer Tingkat Lanjut

### Tujuan bab

- Memahami kerangka MDA dan memakainya untuk menganalisis game.
- Menyusun design pillars dan player fantasy.
- Membedakan masalah desain dari masalah implementasi.

### 1.1 Desainer merancang pengalaman, bukan fitur

Pemula sering bertanya, "Fitur apa yang harus saya tambah?" Desainer tingkat lanjut bertanya, "Pengalaman apa yang ingin dirasakan pemain, dan keputusan apa yang harus mereka ambil untuk merasakannya?"

Game adalah serangkaian **keputusan bermakna** (meaningful decisions). Sebuah keputusan bermakna jika:

1. Pemain punya lebih dari satu pilihan yang masuk akal.
2. Pemain bisa memperkirakan konsekuensi, setidaknya sebagian.
3. Konsekuensi benar-benar memengaruhi kondisi game.

Contoh keputusan tidak bermakna: dua senjata yang identik kecuali nama. Contoh keputusan bermakna: senjata A kuat tetapi lambat (berisiko saat dikepung), senjata B lemah tetapi cepat (aman, tetapi musuh berlapis baja jadi sulit).

### 1.2 Kerangka MDA

MDA adalah singkatan dari **Mechanics, Dynamics, Aesthetics**.

|Lapisan|Pertanyaan|Contoh pada platformer|
|---|---|---|
|Mechanics (mekanik)|Aturan dan sistem apa yang ada?|Lompat, dash, gravitasi, damage duri|
|Dynamics (dinamika)|Perilaku apa yang muncul saat pemain berinteraksi dengan mekanik?|Pemain merencanakan rute, mengambil risiko di platform sempit|
|Aesthetics (estetika pengalaman)|Emosi apa yang dirasakan pemain?|Tantangan, penguasaan, kebebasan bergerak|

**Penting:** Desainer bekerja dari sisi mekanik, tetapi pemain mengalaminya dari sisi estetika. Anda tidak bisa langsung "memasang" emosi. Anda hanya bisa mengatur mekanik, lalu menguji apakah dinamika dan emosi yang muncul sesuai harapan.

**Latihan cepat:** Ambil game favorit Anda. Tulis tiga mekanik, dua dinamika yang muncul darinya, dan satu emosi utama. Contohnya: mekanik "stamina terbatas saat menghindar" menghasilkan dinamika "pemain menyerang dengan sabar" dan emosi "ketegangan terkendali".

### 1.3 Design pillars

**Design pillars** adalah 3 sampai 5 pernyataan pendek yang menjadi kompas keputusan. Setiap fitur baru harus lolos uji: "Apakah ini mendukung pilar kita?"

Contoh pilar untuk sebuah action-adventure 3D indie:

1. **Gerakan adalah hadiah.** Bergerak harus selalu terasa enak, bahkan tanpa musuh.
2. **Eksplorasi mengalahkan instruksi.** Pemain menemukan, bukan diberi tahu.
3. **Risiko yang adil.** Kematian selalu bisa dijelaskan oleh pemain.
4. **Cerita lewat dunia.** Lore ditemukan di lingkungan, bukan di cutscene panjang.

Kriteria pilar yang baik:

- **Spesifik.** "Seru" bukan pilar. "Pertarungan berbasis timing, bukan tombol spam" adalah pilar.
- **Bisa menolak ide.** Pilar yang baik membuat Anda mengatakan "tidak" pada ide bagus yang tidak cocok.
- **Bisa diuji.** Anda dapat menanyai pemain apakah pilar itu terasa.

### 1.4 Player fantasy

**Player fantasy** adalah peran atau kekuatan yang ingin dirasakan pemain. Contoh: "Saya penjelajah gua yang cerdik", "Saya pedagang kecil yang membangun toko dari nol", "Saya pendekar yang makin lincah".

Setiap mekanik utama sebaiknya memperkuat player fantasy. Jika fantasinya "penjelajah yang cerdik", maka mekanik berupa kait tali (grappling) dan pembacaan lingkungan cocok, sedangkan menu manajemen inventori yang rumit kurang cocok.

### 1.5 Memisahkan masalah desain dari masalah implementasi

Saat playtest menemukan masalah, tanyakan dulu: ini masalah **desain** atau **implementasi**?

|Gejala|Kemungkinan masalah desain|Kemungkinan masalah implementasi|
|---|---|---|
|Pemain mati terus di satu boss|Boss terlalu sulit, telegraph kurang jelas|Hitbox boss tidak sesuai animasi, bug kolisi|
|Pemain tidak tahu harus ke mana|Level tidak memberi petunjuk visual|Kamera menutupi jalan, marker tidak muncul|
|Lompat terasa "licin"|Parameter gerak tidak cocok dengan tujuan|Input terlambat satu frame|

Memperbaiki desain dengan menambah kode, atau memperbaiki kode padahal masalahnya desain, adalah sumber utama pemborosan waktu.

### Kesalahan umum

- Menambah fitur untuk menutupi inti gameplay yang membosankan.
- Mengutamakan ide "keren" di atas pilar yang sudah disepakati.
- Mendesain untuk diri sendiri saja tanpa memikirkan pemain baru.

### Latihan

1. Tulis satu kalimat konsep game Anda: "Game [genre] di mana pemain [peran] untuk [tujuan] dengan cara [mekanik khas]".
2. Tulis 3 sampai 4 design pillars.
3. Tulis player fantasy dalam satu kalimat.

### Ringkasan

- Desain adalah merancang keputusan bermakna.
- MDA: Anda mengatur Mechanics, pemain merasakan Aesthetics.
- Pilar dan player fantasy menjaga arah proyek.

---

## Bab 2. Arsitektur Loop: Core Loop, Secondary Loop, dan Meta Loop

### Tujuan bab

- Menyusun loop gameplay berlapis.
- Mengidentifikasi sumber motivasi pemain pada tiap lapisan.
- Memeriksa apakah loop Anda utuh dan tidak bocor.

### 2.1 Apa itu loop

**Loop** adalah siklus aksi yang diulang pemain: aksi, hasil, umpan balik, imbalan, lalu kembali ke aksi. Game yang bertahan lama biasanya punya beberapa loop yang bersarang (nested).

### 2.2 Tiga lapisan loop

|Lapisan|Durasi tipikal|Pertanyaan pemain|Contoh|
|---|---|---|---|
|Core loop (inti)|Detik sampai satu menit|"Apa yang saya lakukan sekarang?"|Menghindar, menyerang, mengambil jeda|
|Secondary loop (sekunder)|Beberapa menit sampai satu jam|"Apa tujuan saya di area ini?"|Membersihkan ruangan, memecahkan puzzle, mengumpulkan sumber daya|
|Meta loop (meta)|Beberapa jam sampai seluruh game|"Mengapa saya terus bermain?"|Membuka kemampuan baru, membuka area baru, memajukan cerita|

Diagram teks:

```
META LOOP: Jelajahi -> Dapatkan kemampuan baru -> Buka area baru -> Cerita maju
    |
    +-- SECONDARY LOOP: Masuk area -> Selesaikan tantangan -> Kumpulkan sumber daya -> Perkuat karakter
            |
            +-- CORE LOOP: Amati -> Putuskan -> Eksekusi -> Umpan balik -> Amati
```

### 2.3 Uji kualitas core loop

Core loop harus menyenangkan **tanpa** hadiah dari lapisan lain. Ujinya: matikan semua progression, upgrade, dan cerita. Apakah mengulang aksi inti selama 5 menit masih terasa menyenangkan? Jika tidak, hiasan di atasnya tidak akan menyelamatkan game Anda.

Pertanyaan pemeriksaan core loop:

1. Apakah ada **tantangan** yang jelas dan bisa dipelajari?
2. Apakah ada **umpan balik** instan (suara, animasi, getaran layar)?
3. Apakah ada **variasi** agar tidak monoton (musuh, tata letak, situasi)?
4. Apakah ada **penguasaan** (skill ceiling) yang membuat pemain merasa makin mahir?

### 2.4 Loop yang bocor

Loop bocor (leaky loop) terjadi ketika sebuah imbalan tidak terhubung kembali ke aksi pemain.

Contoh bocor: pemain mengumpulkan koin, tetapi tidak ada tempat membelanjakannya. Koin menjadi tidak bermakna.

Contoh utuh: pemain mengumpulkan koin, membeli upgrade lompat ganda, lalu bisa mencapai area baru yang berisi koin lebih banyak.

Gambarkan loop Anda sebagai diagram. Setiap panah harus mengarah kembali ke aksi. Jika ada panah yang berakhir "menggantung", itu kebocoran.

### 2.5 Pacing antar-loop

Pemain butuh ritme: tegang, lega, tegang, lega. Pola umum:

```
Tegang (tantangan) -> Lega (hadiah/jeda) -> Eksplorasi tenang -> Tegang lebih tinggi
```

Jika tantangan terus naik tanpa jeda, pemain lelah. Jika jeda terlalu panjang, pemain bosan. Atur "napas" dalam game Anda sebagaimana napas dalam musik.

### 2.6 Motivasi pemain: intrinsik dan ekstrinsik

- **Intrinsik:** aksi itu sendiri menyenangkan (bergerak, menguasai teknik, penasaran).
- **Ekstrinsik:** hadiah dari luar aksi (item, skor, achievement).

Prinsip desain lanjutan: **bangun di atas motivasi intrinsik, lalu perkuat dengan ekstrinsik**. Hadiah ekstrinsik yang berlebihan dapat membuat aksi inti terasa seperti pekerjaan.

### Kesalahan umum

- Mengandalkan meta loop (progres) untuk menutupi core loop lemah.
- Menambah mata uang baru tanpa fungsi jelas.
- Tidak punya "momen jeda" setelah tantangan berat.

### Latihan

1. Gambar tiga lapisan loop game Anda dalam bentuk diagram teks.
2. Cari satu kebocoran dan perbaiki.
3. Lakukan uji "matikan progression" pada prototipe Anda dan catat hasilnya.

### Ringkasan

- Loop berlapis: inti, sekunder, meta.
- Core loop harus menyenangkan secara mandiri.
- Setiap imbalan harus terhubung kembali ke aksi.

---

## Bab 3. Game Feel dan Juice

### Tujuan bab

- Memahami komponen game feel.
- Menerapkan teknik kontrol responsif (input buffer, coyote time, dan lainnya).
- Menambah juice secara terukur, bukan berlebihan.

### 3.1 Definisi

**Game feel** adalah sensasi taktil saat pemain mengendalikan game: seberapa responsif, bertenaga, dan memuaskan aksi terasa. **Juice** adalah lapisan umpan balik audio-visual yang memperkuat game feel (efek partikel, getaran layar, suara, animasi pegas).

Tiga komponen utama game feel:

1. **Input**: seberapa cepat dan akurat game merespons tombol.
2. **Response (respons)**: bagaimana objek bergerak (akselerasi, gravitasi, kurva gerak).
3. **Context (konteks)**: lingkungan tempat gerakan terjadi (platform, musuh, ruang).

### 3.2 Kontrol responsif: teknik wajib

**a. Input buffering.** Simpan input pemain selama beberapa frame agar aksi tetap berjalan meski ditekan sedikit lebih awal dari yang valid.

```
BUFFER_WINDOW = 0.12 detik

saat tombol_lompat ditekan:
    waktu_buffer_lompat = BUFFER_WINDOW

setiap frame:
    waktu_buffer_lompat -= delta_waktu
    jika waktu_buffer_lompat > 0 DAN bisa_lompat:
        lompat()
        waktu_buffer_lompat = 0
```

**b. Coyote time.** Beri pemain jeda singkat untuk melompat setelah meninggalkan tepi platform.

```
COYOTE_WINDOW = 0.10 detik

setiap frame:
    jika di_tanah:
        waktu_coyote = COYOTE_WINDOW
    kalau tidak:
        waktu_coyote -= delta_waktu

bisa_lompat = (waktu_coyote > 0)
```

**c. Variable jump height.** Lompat lebih tinggi jika tombol ditahan, lebih pendek jika dilepas cepat. Teknik: saat tombol dilepas dan karakter masih naik, kurangi kecepatan vertikal.

**d. Gravitasi asimetris.** Gravitasi lebih besar saat turun daripada saat naik agar lompatan terasa tegas, bukan melayang.

**e. Corner correction.** Jika karakter nyaris menabrak sudut platform, dorong sedikit agar tetap lolos.

**f. Akselerasi dan deselerasi.** Gerakan tanpa akselerasi terasa kaku. Gerakan dengan akselerasi terlalu lambat terasa licin. Sediakan parameter yang dapat disetel (tuning).

### 3.3 Prinsip "tuning di luar kode"

Jangan menulis angka gerak langsung di dalam logika. Letakkan di data (file konfigurasi, resource, atau ScriptableObject-sejenis) agar bisa diubah cepat saat bermain.

```
karakter_data:
    kecepatan_maks      = 8.0
    akselerasi          = 60.0
    deselerasi          = 80.0
    gaya_lompat         = 14.0
    gravitasi_naik      = 30.0
    gravitasi_turun     = 45.0
    coyote_time         = 0.10
    buffer_lompat       = 0.12
```

Fitur yang sangat membantu: **tombol reload parameter saat game berjalan** (hot reload) sehingga Anda dapat bermain sambil mengubah angka.

### 3.4 Juice: lapisan umpan balik

Daftar elemen juice dan fungsinya:

|Elemen|Fungsi|Peringatan|
|---|---|---|
|Hitstop (jeda beberapa frame saat serangan mengenai)|Memberi bobot pada serangan|Jangan terlalu lama, cukup 2 sampai 6 frame|
|Screen shake|Menekankan dampak|Sediakan opsi mematikan atau mengurangi, demi kenyamanan pemain|
|Squash and stretch|Memberi kesan lentur dan hidup|Pakai halus pada karakter yang butuh keterbacaan|
|Partikel|Menunjukkan hasil aksi|Jangan menutupi bahaya yang penting|
|Suara berlapis|Menguatkan identitas aksi|Variasikan pitch sedikit agar tidak monoton|
|Flash warna|Menandai hit atau damage|Perhatikan pemain sensitif cahaya|
|Easing (kurva gerak)|Gerakan UI dan kamera terasa organik|Hindari linear untuk gerak yang terlihat|

**Aturan emas juice:** umpan balik harus **proporsional** terhadap pentingnya aksi. Lompat biasa cukup debu kecil. Serangan akhir pada boss boleh mendapat hitstop, shake, dan partikel besar. Jika semuanya heboh, tidak ada yang terasa istimewa.

### 3.5 Perbedaan 2D dan 3D

|Aspek|2D|3D|
|---|---|---|
|Presisi gerak|Mudah dibuat presisi (grid piksel, bidang datar)|Lebih sulit: kamera, kedalaman, sudut|
|Teknik kunci|Coyote time, buffer, corner correction|Kamera adaptif, ledge assist, target lock, snap ke permukaan|
|Risiko utama|Kontrol terlalu kaku|Kontrol "melayang", kamera melawan pemain|
|Pembacaan jarak|Mudah|Perlu bayangan, indikator, atau marker|

Pada 3D, bantu pemain memperkirakan kedalaman: bayangan bulat di tanah di bawah karakter, garis panduan lompat, atau indikator pendaratan.

### 3.6 Uji game feel

Uji "tanpa musuh": taruh karakter di ruang kosong. Apakah hanya berlari, melompat, dan menghindar sudah terasa menyenangkan? Jika ya, fondasi Anda kuat.

### Kesalahan umum

- Menambah juice berlebihan hingga gameplay tidak terbaca.
- Mengabaikan opsi pengurangan efek (screen shake, flash).
- Mengunci angka tuning di dalam kode.

### Latihan

1. Implementasikan coyote time dan input buffer pada prototipe Anda. Rekam sebelum dan sesudah.
2. Pilih satu aksi utama, tambahkan 3 elemen juice, lalu minta teman membandingkannya.
3. Tambahkan menu opsi untuk mengurangi screen shake.

### Ringkasan

- Game feel dibangun dari input, respons, dan konteks.
- Teknik kunci: buffer, coyote time, gravitasi asimetris.
- Juice harus proporsional dan bisa dikurangi pemain.

---

## Bab 4. Desain Sistem dan Emergent Gameplay

### Tujuan bab

- Memahami perbedaan fitur dan sistem.
- Merancang interaksi antar-sistem untuk menciptakan emergent gameplay.
- Memakai matriks interaksi untuk mengelola kompleksitas.

### 4.1 Fitur versus sistem

- **Fitur** adalah satu kemampuan: "pemain bisa membakar rumput".
- **Sistem** adalah sekumpulan aturan yang berinteraksi: "api menyebar ke bahan mudah terbakar, air memadamkannya, angin mengubah arah sebarannya".

Sistem yang bagus memungkinkan **emergent gameplay**: situasi dan solusi yang tidak Anda rancang satu per satu, tetapi muncul dari kombinasi aturan.

### 4.2 Verbs dan objek

Cara praktis merancang sistem adalah mendaftar **verbs** (kata kerja yang bisa dilakukan pemain) dan **objects** (benda yang bisa dikenai kata kerja).

Contoh:

- Verbs: mendorong, membakar, membekukan, menarik, melempar, memecahkan.
- Objects: kotak kayu, genangan air, musuh, tali, pintu.

Kekuatan desain muncul dari **jumlah kombinasi yang bermakna** (verb x object), bukan dari jumlah verb semata. Lebih baik 5 verb yang berinteraksi dengan 20 objek daripada 20 verb yang hanya berlaku pada 2 objek.

### 4.3 Matriks interaksi

Untuk menghindari kekacauan, susun tabel interaksi.

|Aksi / Objek|Kayu|Air|Es|Logam|Musuh|
|---|---|---|---|---|---|
|Api|Terbakar, menyebar|Menguap|Mencair|Memanas|Damage berkelanjutan|
|Es|Tidak ada efek|Membeku|(sudah es)|Tidak ada efek|Melambat|
|Listrik|Tidak ada efek|Menyebar, damage area|Tidak ada efek|Menghantar|Stun singkat|

Manfaat matriks:

1. Menemukan sel kosong yang membingungkan pemain (hasil tak terduga yang tidak adil).
2. Menemukan kombinasi eksploitatif (terlalu kuat).
3. Menjadi dokumentasi untuk programmer, level designer, dan penguji.

### 4.4 Rule of three untuk elemen

Satu elemen interaktif sebaiknya bisa dipakai pada tiga konteks berbeda: untuk **bertarung**, untuk **menjelajah**, dan untuk **memecahkan teka-teki**. Contoh kait tali: menarik musuh (pertarungan), berayun melewati jurang (eksplorasi), menarik tuas jauh (puzzle). Ini membuat satu fitur menghasilkan nilai besar dan menghemat produksi.

### 4.5 Konsistensi aturan

Pemain bisa bermain kreatif hanya jika dunia **konsisten**. Jika api membakar kayu di satu ruangan tetapi tidak di ruangan lain tanpa alasan terlihat, pemain berhenti bereksperimen karena tidak bisa mempercayai aturan.

Kalau memang ada pengecualian, berikan **tanda visual** (misalnya kayu berlapis logam yang jelas terlihat tahan api).

### 4.6 Mengelola kompleksitas

Sistem yang saling terhubung dengan cepat menjadi sulit diuji. Panduan:

1. Mulai dari 2 sampai 3 sistem inti, uji sampai matang, baru tambah.
2. Beri setiap sistem **satu tanggung jawab** yang jelas.
3. Hindari ketergantungan melingkar (sistem A butuh B, B butuh A).
4. Siapkan **ruang uji** (sandbox) untuk mencoba semua kombinasi.

### 4.5b Kapan membatasi emergent gameplay

Emergent gameplay bisa merusak desain level, misalnya pemain melewati puzzle dengan cara tak terduga. Pilihan desain:

- **Terima** jika memberi rasa cerdas bagi pemain dan tidak merusak progres (bonus kreativitas).
- **Cegah** jika membuat pemain terjebak atau melompati hal yang wajib (lakukan dengan pagar halus, bukan tembok tak terlihat).

### Kesalahan umum

- Membuat banyak sistem dangkal tanpa interaksi.
- Pengecualian aturan tanpa petunjuk visual.
- Tidak memiliki ruang uji kombinasi.

### Latihan

1. Susun matriks interaksi minimal 4 aksi x 5 objek untuk game Anda.
2. Tandai sel yang berpotensi eksploit dan putuskan bagaimana menanganinya.
3. Pilih satu mekanik, tulis bagaimana ia dipakai untuk bertarung, menjelajah, dan puzzle.

### Ringkasan

- Sistem berinteraksi, fitur berdiri sendiri.
- Matriks interaksi menjaga kompleksitas tetap terkendali.
- Konsistensi aturan memicu eksperimen pemain.

---

## Bab 5. Matematika dan Balancing

### Tujuan bab

- Memahami kurva progres dan pemilihan rumus.
- Menghitung damage, health, dan time-to-kill (TTK).
- Memakai spreadsheet untuk balancing sebelum mengubah game.
- Mendeteksi strategi dominan.

### 5.1 Mengapa balancing butuh matematika

Balancing adalah mengatur angka agar tantangan terasa adil dan pilihan pemain tetap berarti. Tanpa struktur, Anda hanya "mencoba angka" tanpa henti. Dengan struktur, Anda bisa memprediksi dan memperbaiki.

### 5.2 Jenis kurva progres

|Kurva|Rumus umum|Perilaku|Cocok untuk|
|---|---|---|---|
|Linear|y = a * x + b|Naik konstan|Damage senjata dasar, biaya sederhana|
|Eksponensial|y = a * r^x|Naik makin cepat|Biaya upgrade, XP yang dibutuhkan|
|Polinomial (kuadratik)|y = a * x^2 + b|Naik bertahap makin tajam|Kekuatan musuh, biaya menengah|
|Logaritmik|y = a * log(x) + b|Naik cepat lalu melandai|Diminishing returns (efek makin kecil)|
|Kurva S (sigmoid)|y = L / (1 + e^(-k(x - x0)))|Lambat, cepat, lalu melandai|Peluang, keseimbangan "batas"|

**Contoh XP per level (eksponensial ringan):**

```
xp_dibutuhkan(level) = dasar * (level ^ 1.5)
dasar = 100

level 1  -> 100
level 5  -> sekitar 1118
level 10 -> sekitar 3162
level 20 -> sekitar 8944
```

Mengapa eksponen 1.5 dan bukan 2 atau 3? Pilih eksponen sesuai **lama** yang Anda inginkan di tiap level. Gunakan spreadsheet untuk melihat kurvanya sebelum memutuskan.

### 5.3 Time-to-Kill (TTK) dan Hits-to-Kill (HTK)

Dua ukuran paling berguna untuk combat:

- **HTK** = jumlah serangan untuk menjatuhkan musuh = ceil(HP musuh / damage per serangan).
- **TTK** = HTK x jeda antar serangan.

Contoh:

```
HP musuh = 100
Damage serangan = 18
HTK = ceil(100 / 18) = 6
Jeda serangan = 0.5 detik
TTK = 6 * 0.5 = 3.0 detik
```

Gunakan TTK untuk menentukan "rasa" pertarungan:

|TTK musuh biasa|Rasa yang dihasilkan|
|---|---|
|Kurang dari 1 detik|Cepat, memuaskan, cocok untuk horde|
|2 sampai 5 detik|Seimbang, ada ruang taktik|
|Lebih dari 8 detik|Berat, deliberate, risiko membosankan jika kurang variasi|

### 5.4 Rumus damage

Ada beberapa pendekatan umum:

**Pengurangan datar (flat):**

```
damage_akhir = max(1, serangan - pertahanan)
```

Masalah: pertahanan tinggi bisa membuat damage nol dan stagnan. Maka dipakai `max(1, ...)`.

**Persentase (proporsional):**

```
damage_akhir = serangan * (100 / (100 + pertahanan))
```

Keunggulan: pertahanan tinggi tidak pernah membuat damage menjadi nol, dan ada diminishing returns.

**Kombinasi:**

```
damage_akhir = max(1, (serangan - pertahanan_datar)) * (100 / (100 + pertahanan_persen))
```

Pakai hanya jika memang butuh dan jelaskan dengan jelas di UI. Rumus rumit sulit dipahami pemain.

**Prinsip keterbacaan:** pemain harus bisa memperkirakan efek keputusan mereka. Jika Anda butuh kalkulator untuk memahami, tampilkan angka pratinjau di UI (misalnya "Damage: 24, naik 4 jika memakai item ini").

### 5.5 Power curve: pemain versus musuh

Rancang dua kurva dan bandingkan:

- **Kurva kekuatan pemain** (dari level, item, kemampuan).
- **Kurva kekuatan musuh** (dari HP, damage, jumlah, pola).

Tujuan: jarak keduanya membentuk pola gelombang tantangan, bukan garis datar. Bila pemain selalu jauh lebih kuat, bosan. Bila selalu jauh lebih lemah, frustrasi.

```
Tantangan relatif
    ^
    |        /\        /\
    |   /\  /  \  /\  /  \
    |  /  \/    \/  \/    \  -> naik bertahap dengan puncak boss dan lembah jeda
    +------------------------------> waktu / progres
```

### 5.6 Strategi dominan dan degenerate strategy

**Strategi dominan** adalah pilihan yang selalu lebih baik daripada semua alternatif. Ketika ada, pilihan lain menjadi sia-sia dan keputusan menjadi tidak bermakna.

Cara mendeteksi:

1. Buat tabel pilihan (senjata, build, taktik) dan hitung metrik seperti damage per detik, risiko, dan biaya.
2. Cari pilihan yang unggul di semua kolom.
3. Dengarkan pemain: "Semua orang memakai X" adalah tanda bahaya.

Cara memperbaiki:

- **Trade-off:** beri kelemahan nyata (jangkauan pendek, lambat, mahal, berisiko).
- **Counter:** pastikan ada situasi di mana pilihan lain unggul.
- **Konteks:** buat nilai pilihan bergantung pada situasi (musuh berlapis baja, ruang sempit, dan seterusnya).

### 5.7 Payoff matrix sederhana

Untuk membandingkan dua pilihan, buat tabel hasil pada situasi berbeda.

|Situasi|Senjata A (jarak dekat)|Senjata B (jarak jauh)|
|---|---|---|
|Ruang sempit|Sangat baik|Cukup|
|Ruang terbuka|Cukup|Sangat baik|
|Musuh berlapis baja|Baik|Buruk|
|Banyak musuh kecil|Buruk|Baik|

Jika satu kolom unggul di setiap baris, desain perlu diperbaiki.

### 5.8 Balancing dengan spreadsheet

Langkah kerja:

1. Pindahkan semua angka ke satu spreadsheet (HP, damage, biaya, XP).
2. Tulis rumus, bukan angka mati.
3. Buat grafik kurva untuk melihat bentuknya.
4. Tentukan **target** (misalnya TTK musuh level 5 adalah 3 detik).
5. Ubah parameter sampai target tercapai.
6. Impor data ke game melalui file data (CSV, JSON).
7. Uji bermain, kembali ke spreadsheet bila perlu.

Dengan pola ini, perubahan balancing bisa dilakukan tanpa mengubah kode.

### 5.9 Simulasi cepat

Untuk sistem rumit (misalnya build berbeda), tulis skrip kecil yang mensimulasikan ribuan pertarungan dan melaporkan rata-rata hasil.

```
untuk build di semua_build:
    kemenangan = 0
    ulangi 10000 kali:
        jika simulasi_pertarungan(build, musuh_standar) menang:
            kemenangan += 1
    cetak(build, kemenangan / 10000)
```

Simulasi tidak menggantikan playtest, tetapi sangat berguna untuk menangkap ketimpangan ekstrem.

### Kesalahan umum

- Mengubah angka tanpa target jelas.
- Rumus damage terlalu rumit untuk dipahami pemain.
- Tidak mencatat perubahan balancing sehingga tidak bisa dibatalkan.
- Menyeimbangkan hanya untuk satu gaya bermain (misalnya yang Anda sukai).

### Latihan

1. Buat spreadsheet kurva XP dan pilih eksponen yang cocok dengan durasi game Anda.
2. Hitung HTK dan TTK untuk 3 jenis musuh.
3. Buat payoff matrix untuk 3 senjata atau kemampuan dan cari strategi dominan.

### Ringkasan

- Kurva dan rumus yang tepat membuat progres terukur.
- TTK dan HTK adalah alat ukur utama combat.
- Waspadai strategi dominan, perbaiki lewat trade-off dan konteks.

---

## Bab 6. Ekonomi Game dan Desain Randomness

### Tujuan bab

- Memahami faucet dan sink dalam ekonomi game offline.
- Merancang loot table dan drop rate yang adil.
- Mengelola randomness agar terasa adil dan tidak menjengkelkan.

### 6.1 Ekonomi dalam game single-player

Pada game offline, tidak ada pemain lain yang memengaruhi harga. Ekonomi Anda sepenuhnya terkontrol, sehingga lebih mudah diseimbangkan. Tetapi tetap ada risiko: terlalu banyak sumber daya membuat pilihan kehilangan makna, terlalu sedikit membuat pemain frustrasi.

Istilah penting:

- **Faucet (keran):** sumber yang menambah sumber daya (musuh, peti, hadiah quest).
- **Sink (pembuangan):** pengurang sumber daya (toko, upgrade, perbaikan, konsumsi).
- **Currency (mata uang):** sumber daya yang bisa ditukar.
- **Hoarding:** pemain menumpuk sumber daya tanpa memakainya.

Keseimbangan: laju faucet harus cukup agar pemain merasa maju, tetapi sink harus memberi keputusan menarik tentang pengeluaran.

### 6.2 Mendesain faucet dan sink

Tabel contoh:

|Sumber (faucet)|Perkiraan per jam|Pengeluaran (sink)|Biaya|
|---|---|---|---|
|Musuh biasa|120 koin|Ramuan|30 koin|
|Peti|80 koin|Upgrade senjata tingkat 1|200 koin|
|Quest sampingan|150 koin|Upgrade senjata tingkat 2|600 koin|

Pertanyaan evaluasi:

1. Dalam satu jam, berapa upgrade yang mampu dibeli pemain?
2. Apakah pemain harus **memilih** (tidak bisa membeli semua)?
3. Apakah ada sink untuk koin yang sudah berlebih di akhir game (misalnya kosmetik, tantangan opsional)?

### 6.3 Mengurangi jumlah mata uang

Banyak pemula menambah banyak mata uang (koin, permata, token, kristal). Setiap mata uang baru membebani ingatan dan UI pemain. Pedoman: **mulai dengan satu mata uang**, tambah hanya jika memberi keputusan baru yang tidak bisa dicapai lewat satu mata uang.

### 6.4 Loot table dan drop rate

**Loot table** adalah daftar kemungkinan hadiah beserta bobot (peluang).

```
loot_table_peti_biasa:
    ramuan_kecil   bobot 50
    koin_banyak    bobot 30
    bahan_upgrade  bobot 15
    item_langka    bobot  5
total_bobot = 100
```

Peluang item_langka = 5 / 100 = 5 persen.

**Roll berbobot (weighted random):**

```
fungsi pilih_hadiah(tabel):
    total = jumlah semua bobot
    angka = acak(0, total)
    untuk entri di tabel:
        angka -= entri.bobot
        jika angka < 0:
            kembalikan entri
```

### 6.5 Randomness yang terasa adil

Manusia buruk dalam intuisi probabilitas. Peluang 5 persen berarti pada rata-rata 20 percobaan, tetapi pemain bisa saja gagal 60 kali berturut-turut dan merasa "dikerjai".

Teknik untuk membuat randomness terasa adil:

|Teknik|Cara kerja|Kapan dipakai|
|---|---|---|
|Pity timer (bad luck protection)|Peluang naik setiap kegagalan, direset setelah berhasil|Item penting yang ingin Anda pastikan akan didapat|
|Pseudo-random distribution (PRD)|Peluang efektif dibuat lebih merata|Efek kritikal, proc, drop kecil|
|Shuffle bag|Hadiah dikocok dalam "kantong", diambil tanpa pengembalian|Distribusi merata, misalnya urutan musuh|
|Guaranteed drop|Hadiah tertentu dijamin di titik tertentu|Item progres wajib|

**Contoh pity timer:**

```
peluang_dasar = 0.05
kenaikan_per_gagal = 0.02

peluang = peluang_dasar + (jumlah_gagal * kenaikan_per_gagal)
jika acak(0,1) < peluang:
    beri_item()
    jumlah_gagal = 0
kalau tidak:
    jumlah_gagal += 1
```

**Contoh shuffle bag:**

```
kantong = [A, A, A, B, B, C]   // rasio 3:2:1
acak_urutan(kantong)
ambil satu per satu; jika kosong, isi ulang dan acak lagi
```

### 6.4b Input randomness vs output randomness

- **Input randomness:** keacakan terjadi **sebelum** pemain memutuskan (misalnya peta acak, kartu yang ditarik). Pemain bisa merencanakan berdasarkan hasilnya. Umumnya terasa adil.
- **Output randomness:** keacakan terjadi **setelah** pemain memutuskan (misalnya serangan meleset 20 persen). Bisa terasa tidak adil jika terlalu besar.

Prinsip: gunakan input randomness sebanyak mungkin untuk menciptakan variasi, dan batasi output randomness pada aksi yang berisiko rendah atau kecil dampaknya.

### 6.6 Seed

**Seed** adalah angka awal pembangkit bilangan acak. Dengan seed yang sama, hasil acak berulang sama. Manfaat: reproduksi bug, fitur "bagikan seed", dan tantangan harian offline (berdasarkan tanggal pada perangkat).

### 6.7 Ekonomi item dan inventori

Inventori adalah bagian ekonomi: batas kapasitas menciptakan keputusan ("bawa apa?"). Tetapi batas yang terlalu ketat membuat repot. Opsi desain:

- Batas jumlah slot dengan penyimpanan di basecamp.
- Item bertumpuk (stack) untuk barang kecil.
- Sistem "bawa sedikit, mudah pulang" untuk pemain yang tidak suka mengatur inventori.

### Kesalahan umum

- Menambah mata uang tanpa keperluan.
- Drop rate sangat kecil tanpa perlindungan kesialan.
- Hadiah acak untuk item wajib progres.
- Tidak ada sink di akhir game sehingga uang menumpuk tanpa makna.

### Latihan

1. Buat tabel faucet dan sink untuk satu jam gameplay.
2. Rancang loot table untuk satu jenis peti dan terapkan pity timer.
3. Identifikasi dua tempat di game Anda yang memakai input randomness dan dua yang memakai output randomness.

### Ringkasan

- Ekonomi offline mudah dikontrol, tetapi tetap butuh keseimbangan faucet dan sink.
- Randomness harus terasa adil: pity timer, shuffle bag, dan input randomness.
- Sedikit mata uang lebih jelas bagi pemain.

---

## Bab 7. Desain Combat 2D dan 3D

### Tujuan bab

- Memahami anatomi serangan (anticipation, active, recovery).
- Merancang telegraph yang adil dan musuh dengan peran berbeda.
- Merancang boss dengan fase dan pola yang dapat dipelajari.

### 7.1 Anatomi sebuah serangan

Setiap serangan, baik milik pemain maupun musuh, bisa dipecah menjadi tiga fase:

|Fase|Fungsi|Pengaruh pada desain|
|---|---|---|
|Startup / Anticipation|Persiapan sebelum damage|Memberi pemain waktu bereaksi (telegraph)|
|Active|Saat hitbox aktif dan damage terjadi|Durasi singkat, fokus pada dampak|
|Recovery|Pemulihan setelah serangan|Memberi celah untuk dibalas (punish window)|

Hubungan penting: **startup panjang** berarti serangan lebih mudah dihindari tetapi biasanya bisa lebih kuat. **Recovery panjang** berarti serangan berisiko bagi yang melakukannya. Ini adalah alat utama balancing combat.

**Frame data** adalah catatan durasi tiap fase dalam frame. Contoh pada 60 frame per detik:

```
Serangan pedang berat:
    startup  = 24 frame (0.40 detik)
    active   = 6  frame (0.10 detik)
    recovery = 30 frame (0.50 detik)
```

Menyimpan frame data di tabel memudahkan penyetelan dan perbandingan antar-serangan.

### 7.2 Telegraph yang adil

**Telegraph** adalah isyarat bahwa serangan akan datang. Prinsip keadilan:

1. **Terlihat:** gerakan, warna, atau efek yang jelas (misalnya musuh mengangkat senjata, mata bersinar).
2. **Terdengar:** suara khas sebelum serangan.
3. **Cukup lama:** waktu telegraph lebih panjang dari waktu reaksi manusia (sekitar 0,2 sampai 0,3 detik untuk reaksi sederhana, lebih lama untuk keputusan).
4. **Konsisten:** isyarat yang sama selalu berarti serangan yang sama.

Jika pemain mati dan merasa "tidak ada cara tahu", telegraph gagal.

### 7.3 Peran musuh (enemy archetypes)

Merancang variasi musuh berdasarkan **peran** membuat pertarungan lebih kaya daripada sekadar menambah HP.

|Peran|Tujuan desain|Cara pemain meresponsnya|
|---|---|---|
|Grunt (prajurit biasa)|Mengajarkan dasar, mengisi ruang|Serangan dasar dan menghindar|
|Brute (tank)|Menekan pemain secara fisik|Menghindari serangan berat, mencari celah|
|Ranged (penembak)|Memaksa pemain bergerak|Menutup jarak atau berlindung|
|Swarmer (gerombolan)|Menguji kontrol area|Serangan area, posisi|
|Support (pendukung)|Mengubah prioritas target|Menyingkirkan lebih dulu|
|Assassin (cepat, rapuh)|Menguji reaksi|Timing dan pertahanan|
|Mini-boss|Ujian keterampilan|Menggabungkan semua yang dipelajari|

Kombinasi peran memicu keputusan: Ranged di belakang Brute memaksa pemain memilih antara menembus pertahanan atau menghindari tembakan.

### 7.4 Ruang pertarungan (arena)

Level dan combat saling bergantung. Pertimbangkan:

- **Ukuran arena:** terlalu sempit membatasi menghindar, terlalu luas membuat musuh sulit ditemukan.
- **Elemen medan:** penghalang untuk berlindung, platform tinggi, jebakan lingkungan.
- **Jalan keluar:** pemain harus bisa mundur dan mengatur ulang posisi.

### 7.5 Sumber daya combat

Sumber daya mengatur ritme dan risiko.

|Sumber daya|Efek pada ritme|Catatan|
|---|---|---|
|Stamina|Membatasi spam, mendorong sabar|Tampilkan jelas, jangan terlalu menghukum|
|Mana/energi|Membatasi kemampuan kuat|Atur isi ulang agar tidak menunggu terlalu lama|
|Amunisi|Membuat pilihan senjata bermakna|Pastikan ada senjata cadangan|
|Cooldown|Memberi jeda strategis|Cooldown panjang pada kemampuan tidak menarik terasa membosankan|
|Risk/reward (misalnya combo meter)|Menghargai agresi|Pastikan risiko terlihat|

### 7.6 Desain boss

Boss adalah puncak ujian keterampilan. Prinsip desain:

1. **Pola yang bisa dipelajari.** Boss memiliki satu set serangan dengan isyarat jelas. Pemain menang karena belajar, bukan karena beruntung.
2. **Fase.** Perubahan perilaku pada ambang HP (misalnya 66 persen dan 33 persen) menjaga kesegaran. Fase baru memperkenalkan variasi atau kombinasi, bukan hanya angka lebih besar.
3. **Celah (opening).** Setiap serangan boss menciptakan peluang balasan. Tanpa celah, boss terasa tidak adil.
4. **Ujian terhadap yang diajarkan.** Boss ideal menguji kemampuan yang sudah dipelajari di level sebelumnya, bukan mekanik baru.
5. **Checkpoint adil.** Jika boss sulit, jarak dari checkpoint ke boss harus pendek.

Contoh kerangka boss tiga fase:

```
Boss "Penjaga Gerbang"

Fase 1 (100% sampai 66% HP):
    - Tebasan horizontal (telegraph: mengangkat pedang, 0.6 dtk)
    - Hentak tanah (telegraph: melompat, 0.8 dtk)
    Celah: setelah tebasan, 1.0 dtk recovery

Fase 2 (66% sampai 33% HP):
    - Semua serangan fase 1, lebih cepat 15%
    - Tambah: serangan proyektil dari jauh (ajarkan lewat musuh ranged sebelumnya)

Fase 3 (33% sampai 0% HP):
    - Gabungan: hentak tanah diikuti proyektil
    - Arena menyempit (hazard di tepi)
    Celah tetap ada, lebih pendek (0.7 dtk)
```

### 7.7 Combat 2D vs 3D

|Aspek|2D|3D|
|---|---|---|
|Keterbacaan|Mudah: bidang datar, siluet jelas|Perlu perhatian kamera dan kedalaman|
|Hitbox|Persegi/lingkaran, mudah diperkirakan|Volume, bisa terasa tidak sesuai visual|
|Target|Seringkali otomatis dari arah|Lock-on, auto-aim, snap target|
|Menghindar|Arah terbatas|Ruang bebas, perlu indikator area|
|Risiko khas|Spam serangan|Kamera menutupi serangan, musuh di luar layar|

**Tips 3D:**

- Sediakan **lock-on** atau bantuan target agar pemain tidak kehilangan musuh.
- Jaga musuh agar tidak menyerang dari luar layar tanpa peringatan (gunakan indikator arah).
- Buat **hitbox sedikit lebih ramah pemain** (hitbox pemain kecil, hitbox musuh lebih jelas dan sesuai visual).

### 7.8 Prinsip keadilan combat

- Kematian harus **bisa dijelaskan** pemain.
- Hukuman harus **proporsional**.
- Variasi tantangan harus **bertambah**, bukan hanya nilai angka.
- Berikan **alat** untuk memperbaiki diri (belajar pola, memilih build, memakai item).

### Kesalahan umum

- Telegraph terlalu singkat atau tidak konsisten.
- Boss yang menang dengan HP besar saja.
- Musuh yang menyerang tanpa recovery.
- Kamera 3D menutupi pertarungan.

### Latihan

1. Buat tabel frame data untuk 4 serangan musuh dan 3 serangan pemain.
2. Rancang tiga peran musuh dan satu kombinasi yang memaksa keputusan.
3. Tulis kerangka boss tiga fase seperti contoh di atas.

### Ringkasan

- Serangan memiliki startup, active, recovery.
- Telegraph yang adil menjadi dasar combat yang menyenangkan.
- Musuh dirancang berdasarkan peran, boss berdasarkan fase dan pola.

---

## Bab 8. Desain AI Musuh dan Companion

### Tujuan bab

- Memilih teknik AI yang tepat (FSM, behavior tree, utility AI).
- Merancang AI yang "terasa cerdas" tanpa menjadi tidak adil.
- Merancang companion yang membantu tanpa mengganggu.

### 8.1 Prinsip dasar: AI untuk pemain, bukan untuk menang

Tujuan AI musuh di game bukan mengalahkan pemain, melainkan **menciptakan tantangan yang menyenangkan**. AI yang terlalu pintar membuat frustrasi. AI yang terlalu bodoh membuat bosan. Target: AI yang **terbaca dan bisa dimanfaatkan** oleh pemain yang cerdik.

### 8.2 Finite State Machine (FSM)

**FSM** adalah model paling sederhana: musuh berada di satu **state** pada satu waktu, dan berpindah state berdasarkan **kondisi**.

```
State: Patroli
    -> jika melihat_pemain: ke Kejar

State: Kejar
    -> jika jarak < jangkauan_serang: ke Serang
    -> jika kehilangan_pemain > 3 detik: ke Cari

State: Serang
    -> setelah serangan selesai: ke Pemulihan

State: Pemulihan
    -> setelah 1 detik: ke Kejar

State: Cari
    -> jika melihat_pemain: ke Kejar
    -> jika waktu_cari > 5 detik: ke Patroli
```

Kelebihan FSM: mudah dipahami dan di-debug. Kekurangan: jika state bertambah banyak, transisi menjadi rumit ("state explosion").

### 8.3 Behavior Tree (BT)

**Behavior tree** menyusun perilaku sebagai pohon keputusan. Node utama:

- **Selector:** coba anak satu per satu sampai ada yang berhasil (seperti "atau").
- **Sequence:** jalankan semua anak berurutan, berhenti jika ada yang gagal (seperti "dan").
- **Condition:** memeriksa kondisi.
- **Action:** melakukan sesuatu.

```
Selector
 |- Sequence (Menyerang)
 |    |- Condition: pemain dalam jangkauan?
 |    |- Action: serang
 |- Sequence (Mengejar)
 |    |- Condition: melihat pemain?
 |    |- Action: bergerak ke pemain
 |- Action: patroli
```

Kelebihan BT: modular dan lebih mudah diperluas daripada FSM besar. Banyak engine sudah menyediakan dukungan BT bawaan atau lewat addon.

### 8.4 Utility AI

**Utility AI** menilai setiap aksi dengan skor lalu memilih skor tertinggi. Cocok untuk perilaku yang tampak lebih alami dan kontekstual.

```
skor_serang = (kedekatan_pemain * 0.6) + (hp_sendiri * 0.2) - (bahaya_sekitar * 0.4)
skor_mundur = ((1 - hp_sendiri) * 0.7) + (bahaya_sekitar * 0.5)
skor_beri_bantuan = (rekan_terluka * 0.8)

pilih aksi dengan skor tertinggi
```

Kekuatan: perilaku terasa fleksibel. Tantangan: harus disetel (tuning) dengan teliti dan lebih sulit diprediksi saat debugging.

### 8.5 Memilih teknik

|Kebutuhan|Rekomendasi|
|---|---|
|Musuh sederhana, sedikit perilaku|FSM|
|Musuh dengan banyak perilaku modular|Behavior tree|
|Perilaku bergantung pada banyak faktor|Utility AI|
|Boss dengan pola terjadwal|FSM berbasis fase atau skrip pola|

### 8.6 Persepsi AI yang adil

AI tidak boleh "tahu segalanya". Berikan batas persepsi:

- **Penglihatan:** kerucut pandang dan jarak (sight cone).
- **Pendengaran:** radius suara (misalnya lari lebih berisik daripada berjalan).
- **Ingatan:** AI mengingat posisi terakhir pemain, bukan posisi aktual.
- **Waktu reaksi:** jeda sebelum bereaksi (misalnya 0,3 detik).

Pemain mengeksploitasi batas ini dengan strategi (bersembunyi, memancing). Itu bagian dari kesenangan.

### 8.7 Pathfinding dan navigasi

- **2D grid:** algoritma A* pada grid sudah umum dan cukup.
- **3D:** gunakan **navigation mesh (navmesh)** yang disediakan engine. Atur agar musuh tidak tersangkut di sudut dan bisa menangani tangga, lompatan, atau celah bila relevan.
- **Steering behaviors:** seek, flee, separation (menjaga jarak antar musuh), dan avoidance membuat gerakan kelompok tampak alami.

**Penting:** musuh yang bergerombol harus punya mekanisme **menjaga jarak** agar tidak menumpuk di satu titik.

### 8.8 Pengaturan token serangan

Jika banyak musuh menyerang bersamaan, pemain tidak punya peluang. Gunakan **attack token**: hanya N musuh (misalnya 2 sampai 3) yang boleh menyerang aktif, sisanya mengitari atau menunggu.

```
token_serangan_tersedia = 2

musuh meminta token sebelum menyerang
jika token ada: serang, tahan token sampai selesai, lalu kembalikan
jika tidak: bergerak mengitari
```

Hasilnya: pertarungan terasa seperti "tarian" yang adil, bukan kerumunan acak.

### 8.9 Companion AI

Companion (rekan) yang membantu pemain harus mengikuti prinsip:

1. **Tidak menghalangi.** Jangan blokir jalan atau mengganggu kamera.
2. **Tidak mencuri sorotan.** Companion tidak menyelesaikan puzzle untuk pemain.
3. **Membantu secara bermakna.** Misalnya mengalihkan musuh, membuka jalan, atau memberi petunjuk halus.
4. **Mudah diabaikan.** Pemain boleh menyuruh companion diam atau menonaktifkannya.
5. **Tidak bisa mati secara menjengkelkan.** Jika companion kalah, buat pulih otomatis atau tak mudah tewas.

### 8.10 Director offline (pengatur tempo)

Pada game offline, Anda dapat memakai sistem **director** sederhana yang mengatur intensitas: jika pemain sedang tertekan (HP rendah, banyak musuh), kurangi spawn berikutnya. Jika terlalu santai, naikkan tekanan. Ini membantu pacing tanpa multiplayer.

### Kesalahan umum

- AI memiliki informasi sempurna tentang posisi pemain.
- Banyak musuh menyerang sekaligus tanpa batas.
- FSM raksasa tanpa struktur.
- Companion yang menyelesaikan semua tantangan.

### Latihan

1. Gambar FSM untuk satu musuh (minimal 4 state).
2. Terapkan batas persepsi (sight cone dan ingatan posisi terakhir).
3. Terapkan attack token pada kelompok 4 musuh.

### Ringkasan

- Pilih FSM, BT, atau utility AI sesuai kebutuhan.
- AI yang baik adil, terbaca, dan dapat dimanfaatkan.
- Companion harus membantu tanpa mengganggu.

---

## Bab 9. Level Design Lanjutan

### Tujuan bab

- Merancang level yang mengajar tanpa tutorial panjang.
- Mengarahkan pemain dengan bahasa visual.
- Merancang tata letak (graph) dunia yang saling terhubung.
- Mengatur pacing dan tantangan.

### 9.1 Level sebagai guru

Level terbaik mengajar lewat **pengalaman**, bukan teks. Pola klasik untuk memperkenalkan mekanik:

1. **Introduce (Perkenalan):** pemain bertemu mekanik di tempat aman, tanpa risiko besar.
2. **Develop (Pengembangan):** mekanik dipakai dalam situasi yang sedikit lebih menantang.
3. **Twist (Putaran):** mekanik dipakai dengan cara tak terduga atau digabung dengan mekanik lain.
4. **Conclude (Penutup):** ujian akhir yang menggabungkan semuanya.

Contoh: mekanik "lompat dinding".

- Introduce: dinding tinggi di ruang aman, hanya cara untuk naik.
- Develop: dinding berseling dengan duri, perlu timing.
- Twist: dinding bergerak atau musuh menyerang saat memanjat.
- Conclude: sirkuit memanjat dengan musuh dan jebakan.

### 9.2 Bahasa visual pemandu

Pemain mengikuti isyarat tanpa sadar. Alat panduan:

|Alat|Cara kerja|
|---|---|
|Cahaya|Pemain tertarik ke area yang lebih terang|
|Warna|Warna kontras menandai interaksi (misalnya kuning untuk bisa dipanjat)|
|Landmark|Objek besar dan khas yang terlihat dari jauh|
|Garis arah (leading lines)|Jalan, rel, sungai yang mengarahkan mata|
|Pergerakan|Objek bergerak menarik perhatian|
|Suara|Musik dan efek lingkungan memberi arah|
|NPC atau hewan|Berjalan atau menunjuk ke arah tertentu|

**Konsistensi:** jika kuning berarti "bisa dipanjat", pakai kuning hanya untuk itu. Konsistensi membangun bahasa visual game Anda.

### 9.3 Blockout atau greybox

Sebelum membuat seni final, buat level dari bentuk dasar (kotak, silinder). Tujuannya menguji:

- Ritme dan ukuran ruang.
- Jalur dan jarak lompat.
- Tantangan dan penempatan musuh.

Uji dulu di greybox. Jika sudah menyenangkan tanpa seni, seni akan mempercantiknya. Jika belum, seni tidak akan menyelamatkannya.

### 9.4 Critical path dan jalur opsional

- **Critical path:** jalur wajib dari awal sampai akhir. Harus jelas dan tidak membuat pemain tersesat.
- **Jalur opsional:** cabang yang memberi hadiah tambahan (item, lore, shortcut). Cabang ini memenuhi kebutuhan pemain eksplorer.

Pastikan hadiah cabang sepadan dengan risikonya, dan beri petunjuk visual bahwa cabang itu ada ("cukup menarik untuk dikunjungi").

### 9.5 Struktur dunia sebagai graph (metroidvania dan semi-open)

Dunia yang saling terhubung dapat digambarkan sebagai **graph**: titik (area) dan garis (koneksi), dengan **gerbang** (gate) berupa kemampuan atau kunci.

```
[Awal] --- [Hutan] --- [Gua Es] --- [Menara]
              |            |
          [Rawa]       [Ruang Rahasia]

Gerbang:
    Hutan -> Gua Es: butuh Dash
    Gua Es -> Menara: butuh Lompat Ganda
    Rawa: butuh Tali Kait
```

Langkah merancang:

1. Tentukan **kemampuan kunci** (Dash, Lompat Ganda, Kait) dan urutan perolehan.
2. Tempatkan **gerbang** yang hanya bisa dilewati dengan kemampuan tersebut.
3. Pastikan ada **jalur menuju kemampuan** tanpa kemampuan itu sendiri (hindari soft-lock).
4. Tambahkan **shortcut** yang menghubungkan area jauh, memberi rasa penguasaan.
5. Tambahkan **backtracking yang bermakna**: pemain kembali karena punya kemampuan baru, bukan karena dipaksa mengulang.

### 9.6 Pengelolaan soft-lock dan jalan buntu

**Soft-lock** terjadi saat pemain terjebak tanpa jalan maju dan tanpa cara keluar. Pencegahan:

- Uji semua urutan pengambilan kemampuan.
- Sediakan cara kembali (teleport, pintu satu arah yang kemudian membuka).
- Hindari jebakan yang tidak bisa dibatalkan tanpa peringatan.
- Sediakan opsi "kembali ke checkpoint terakhir" di menu.

### 9.7 Pacing level

Gunakan **grafik intensitas** per bagian level:

```
Intensitas
    ^
    |             /\
    |      /\    /  \      /\/\ (klimaks)
    |  /\ /  \  /    \    /
    | /  V    \/      \__/
    +--------------------------------> posisi di level
      Intro  Eksplorasi  Tantangan  Jeda  Boss
```

Tandai titik: tantangan, pertemuan musuh, puzzle, jeda tenang, hadiah, dan cerita. Pastikan ada pola naik-turun.

### 9.8 Perbedaan level design 2D dan 3D

|Aspek|2D|3D|
|---|---|---|
|Orientasi|Mudah, sumbu kiri-kanan atau empat arah|Pemain bisa tersesat, butuh landmark dan peta|
|Keterbacaan|Siluet dan layering|Kamera dan sudut pandang|
|Verticality|Platform bertumpuk|Ruang volume nyata|
|Jalur|Biasanya satu arah utama|Banyak sudut pandang dan jalur|
|Alat bantu|Parallax, kontras|Sightline, signposting, minimap atau kompas|

**Tips 3D:** gunakan **sightline** (garis pandang) untuk menunjukkan tujuan dari jauh. Pemain yang melihat tujuan jauh termotivasi menuju ke sana dan menemukan hal lain di perjalanan.

### 9.9 Level untuk berbagai gaya bermain

Rancang beberapa jalur menyelesaikan tantangan: jalur agresif, jalur sembunyi-sembunyi, jalur kreatif. Ini meningkatkan replayability dan menghormati preferensi pemain.

### 9.10 Anti-kebosanan dan variasi

- Jangan ulang pola yang sama lebih dari tiga kali tanpa perubahan.
- Perubahan **tema, mekanik, atau ritme** menyegarkan pengalaman.
- Sisipkan **set piece** (momen khusus yang unik, misalnya runtuhnya jembatan) di titik penting.

### Kesalahan umum

- Level dibuat langsung dengan seni final.
- Tutorial berupa teks panjang di awal.
- Jalan wajib tidak jelas, jalur opsional terlalu tersembunyi.
- Soft-lock yang tidak diuji.

### Latihan

1. Rancang satu level kecil dengan pola Introduce, Develop, Twist, Conclude untuk satu mekanik.
2. Gambar graph dunia game Anda dengan minimal 6 area dan 3 gerbang.
3. Buat greybox satu ruangan combat dan uji dengan 3 orang.

### Ringkasan

- Level adalah guru: perkenalkan, kembangkan, putar, tutup.
- Bahasa visual dan landmark mengarahkan pemain tanpa teks.
- Graph dunia, gerbang, dan shortcut membuat eksplorasi bermakna.

---

## Bab 10. Progression, Kurva Kesulitan, dan Aksesibilitas

### Tujuan bab

- Merancang progression (kemajuan) yang memuaskan.
- Memahami flow state dan mengatur kurva kesulitan.
- Merancang opsi kesulitan dan aksesibilitas.

### 10.1 Jenis progression

|Jenis|Penjelasan|Contoh|
|---|---|---|
|Progres keterampilan pemain|Pemain makin mahir|Belajar timing boss|
|Progres karakter (statistik)|Angka naik|Level, HP, damage|
|Progres kemampuan (ability)|Mekanik baru terbuka|Dash, lompat ganda|
|Progres konten|Area dan cerita baru|Membuka dunia baru|
|Progres koleksi|Mengumpulkan item|Lore, kosmetik|

Pedoman desain: **progres kemampuan dan keterampilan** lebih bermakna daripada sekadar angka. Peningkatan angka (misalnya +5 persen damage) terasa hambar dibanding kemampuan baru yang mengubah cara bermain.

### 10.2 Skill tree dan upgrade

Prinsip merancang skill tree:

1. **Pilihan nyata:** pemain tidak bisa mengambil semua. Pilihan menciptakan identitas build.
2. **Perubahan perilaku, bukan hanya angka:** upgrade yang memberi mekanik baru lebih menarik daripada +3 persen.
3. **Keterbacaan:** pemain dapat memahami efek sebelum memilih.
4. **Respec yang ramah:** izinkan mengubah pilihan dengan biaya rendah, agar pemain berani bereksperimen.
5. **Hindari upgrade wajib:** jika semua pemain memilih jalur yang sama, tree tidak berfungsi.

Contoh upgrade bermakna versus hambar:

|Hambar|Bermakna|
|---|---|
|Damage +5 persen|Serangan ketiga dalam kombo memicu gelombang kejut|
|HP maksimal +10|Setelah menghindar sempurna, pulihkan sedikit HP|
|Kecepatan +3 persen|Dash meninggalkan jejak api yang melukai musuh|

### 10.3 Flow state dan kurva kesulitan

**Flow** adalah keadaan terserap penuh saat tantangan seimbang dengan kemampuan. Jika tantangan jauh di atas kemampuan terjadi kecemasan. Jika jauh di bawah terjadi kebosanan.

```
Tantangan
    ^
    |   Kecemasan        /
    |               /  /
    |          /  FLOW
    |      /  /
    |   /  Kebosanan
    +--------------------------> Kemampuan
```

Kurva kesulitan ideal berbentuk **gigi gergaji naik** (sawtooth): tantangan naik, pemain belajar, ada jeda, lalu tantangan baru yang sedikit lebih tinggi dari sebelumnya.

### 10.4 Memberi pemain kendali atas kesulitan

Pemain berbeda-beda. Opsi pendekatan:

|Pendekatan|Penjelasan|Catatan|
|---|---|---|
|Pilihan kesulitan di awal|Mudah, Normal, Sulit|Beri deskripsi jelas apa yang berubah|
|Parameter terpisah|Atur HP musuh, damage musuh, timing secara terpisah|Fleksibel, cocok untuk assist mode|
|Dynamic difficulty adjustment (DDA)|Game menyesuaikan diam-diam|Pakai hati-hati: pemain bisa merasa dipermainkan|
|Tantangan opsional|Tantangan ekstra untuk yang mahir|Menghormati semua tingkat keterampilan|

**Catatan DDA:** penyesuaian halus (misalnya menambah item pemulihan setelah banyak kematian) umumnya diterima. Penyesuaian yang mengubah aturan drastis tanpa sepengetahuan pemain bisa merusak kepercayaan. Jika memakainya, sebaiknya transparan atau bisa dimatikan.

### 10.5 Kegagalan sebagai bagian desain

Kematian dan kegagalan harus **cepat, informatif, dan murah**:

- **Cepat:** reload atau respawn singkat.
- **Informatif:** pemain tahu mengapa gagal (replay kematian singkat, indikator penyebab).
- **Murah:** kehilangan progres sedikit sehingga mau mencoba lagi.

Hukuman tinggi harus dibayar dengan tantangan yang adil dan sinyal yang jelas.

### 10.6 Aksesibilitas sebagai prinsip desain

Aksesibilitas memperluas jumlah orang yang dapat menikmati game Anda. Banyak fitur juga membantu semua pemain.

Daftar fitur dasar yang layak masuk sejak awal:

|Kategori|Fitur|
|---|---|
|Visual|Ukuran teks dapat diatur, kontras tinggi, mode buta warna, jangan mengandalkan warna saja|
|Audio|Subtitle dan caption (termasuk keterangan efek suara penting), kontrol volume terpisah|
|Motorik|Remap kontrol, opsi tahan atau toggle, kurangi tombol cepat berulang (QTE)|
|Kognitif|Pengingat tujuan, tutorial dapat diulang, kecepatan game dapat diatur|
|Kenyamanan|Kurangi screen shake, kurangi flash, opsi motion blur dan head bob|

Prinsip praktis: **jangan mengkomunikasikan informasi penting hanya lewat satu kanal**. Jika bahaya ditandai hanya dengan warna merah, tambahkan bentuk atau suara. Jika petunjuk hanya lewat suara, tambahkan visual.

### 10.7 Assist mode

Assist mode menyediakan penyesuaian opsional (misalnya mengurangi damage, memperlambat game, kebal sementara) tanpa memberi stigma. Beri nama netral dan jangan mengunci achievement tanpa alasan jelas.

### Kesalahan umum

- Progres hanya berupa angka naik.
- Skill tree dengan upgrade wajib.
- Satu pilihan kesulitan yang tidak menjelaskan perubahannya.
- Aksesibilitas ditambahkan di akhir produksi (jauh lebih sulit).

### Latihan

1. Rancang 6 upgrade, tiga di antaranya mengubah perilaku, bukan sekadar angka.
2. Gambar kurva kesulitan game Anda dengan pola gigi gergaji.
3. Tambahkan minimal lima opsi aksesibilitas dasar pada prototipe.

### Ringkasan

- Progres bermakna mengubah cara bermain, bukan sekadar angka.
- Flow lahir dari tantangan yang sepadan dengan kemampuan.
- Aksesibilitas dirancang sejak awal dan menguntungkan semua pemain.

---

## Bab 11. Procedural Generation dan Desain Roguelite

### Tujuan bab

- Memahami kapan procedural generation berguna.
- Merancang level acak yang tetap terkurasi.
- Merancang loop roguelite dengan meta progression.

### 11.1 Apa itu procedural generation (PCG)

**Procedural content generation (PCG)** adalah pembuatan konten (level, item, musuh) berdasarkan aturan dan keacakan, bukan dibuat manual satu per satu.

Manfaat:

- **Replayability:** setiap permainan berbeda.
- **Efisiensi konten:** satu sistem menghasilkan banyak variasi.

Risiko:

- Konten terasa **generik** dan berulang.
- Sulit menjamin **kualitas** dan **keadilan**.
- Banyak waktu habis untuk membangun sistem generasi, bukan gameplay.

**Aturan praktis:** PCG berguna jika inti kesenangan game berasal dari **sistem dan keputusan**, bukan dari alur cerita yang tetap.

### 11.2 Pendekatan PCG yang ramah indie

|Pendekatan|Cara kerja|Kelebihan|Kekurangan|
|---|---|---|---|
|Room-based (ruang prefabrikasi)|Menyusun ruang buatan tangan secara acak|Kualitas ruang terjaga|Variasi terbatas pada jumlah ruang|
|Grid dan aturan (misalnya wave function collapse atau aturan tetangga)|Menyusun tile berdasarkan aturan|Variasi tinggi|Lebih sulit dikendalikan|
|Noise (Perlin, Simplex)|Medan alami dengan noise|Cocok untuk terrain|Perlu penyaringan untuk gameplay|
|Random walk dan automata seluler|Menggali gua atau jalur|Mudah dibuat|Perlu dibersihkan agar bisa dilalui|

Untuk pemula: mulai dengan **room-based**. Anda tetap mengendalikan kualitas tiap ruang.

### 11.3 Terkurasi, bukan murni acak

Level acak yang baik memiliki **aturan struktur**:

1. **Garansi:** jalur dari awal ke akhir selalu ada.
2. **Pacing terjadwal:** misalnya ruang aman setelah dua ruang tempur.
3. **Tema dan komposisi:** musuh dipilih berdasarkan "anggaran kesulitan" (difficulty budget).
4. **Validasi:** setelah generasi, periksa apakah level bisa diselesaikan, apakah ada musuh yang tumpang tindih dengan dinding, dan seterusnya.

**Anggaran kesulitan:**

```
anggaran_ruang = dasar + (nomor_ruang * kenaikan)

biaya_musuh = { grunt: 1, brute: 3, ranged: 2, mini_boss: 8 }

selama anggaran > 0:
    pilih musuh acak yang biayanya <= anggaran
    tambahkan ke ruang
    anggaran -= biaya musuh
```

Dengan cara ini tingkat tantangan terkendali walau komposisinya acak.

### 11.4 Loop roguelite

Roguelike menekankan ketahanan satu "run" dengan kematian permanen. **Roguelite** menambahkan meta progression: sesuatu tetap terbawa antar-run.

Struktur umum:

```
RUN LOOP:
    Mulai run -> Jelajah ruang -> Ambil upgrade acak -> Hadapi boss -> Mati/Menang

META LOOP:
    Hasil run (sumber daya) -> Belanja di base -> Buka opsi baru/kemampuan awal -> Run berikutnya
```

### 11.5 Prinsip desain roguelite

1. **Run harus selalu terasa berbeda,** tetapi tetap berpola agar pemain dapat belajar.
2. **Keputusan pada upgrade acak:** tawarkan 3 pilihan, bukan 1, agar pemain tetap memiliki kendali.
3. **Sinergi antar-upgrade:** upgrade yang saling memperkuat menciptakan build unik dan momen "wow".
4. **Meta progression tidak boleh menghapus tantangan:** jika meta upgrade membuat run pertama otomatis menang, tantangan hilang. Sebaiknya meta progression memperluas **opsi**, bukan hanya angka.
5. **Run harus bermakna walau gagal:** pemain pulang membawa sesuatu (sumber daya, pengetahuan, kemajuan cerita).
6. **Durasi run:** sesuaikan dengan target sesi bermain (misalnya 20 sampai 45 menit).

### 11.6 Menyampaikan cerita di game roguelite

Cerita bisa maju **antar-run**: setiap kematian membuka potongan dialog atau lore baru. Pemain mendapat alasan untuk mencoba lagi. Teknik ini sangat cocok dengan format **tanpa voice actor** karena dapat berupa teks pendek dan pemain yang menemukan potongan demi potongan.

### 11.7 Menguji konten acak

- Gunakan **seed** untuk mereproduksi level bermasalah.
- Jalankan generator ratusan kali dan **log** hasil: tingkat gagal validasi, distribusi ruang, rata-rata musuh.
- Uji bot sederhana yang berjalan melalui level untuk memastikan jalur dapat diselesaikan.

### Kesalahan umum

- Membangun generator rumit sebelum inti gameplay menyenangkan.
- Level acak tanpa validasi sehingga ada jalan buntu.
- Meta progression yang membuat game terlalu mudah.
- Upgrade acak yang tidak bersinergi.

### Latihan

1. Buat 8 ruang prefabrikasi dan susun menjadi satu run dengan aturan pacing.
2. Implementasikan anggaran kesulitan untuk pemilihan musuh.
3. Rancang 10 upgrade dengan setidaknya 3 sinergi.

### Ringkasan

- PCG efektif bila sistem menjadi pusat kesenangan.
- Konten acak harus terkurasi dan divalidasi.
- Roguelite menggabungkan run loop dan meta loop dengan keputusan bermakna.

---

## Bab 12. Narrative Design Gameplay-First Tanpa Voice Actor

### Tujuan bab

- Merancang cerita dan lore yang mendukung gameplay.
- Menyampaikan narasi tanpa voice actor secara efektif.
- Menyatukan cerita dengan mekanik (ludonarrative harmony).

### 12.1 Posisi cerita dalam game gameplay-first

Pada game yang berfokus pada gameplay, cerita bertugas sebagai:

1. **Konteks:** alasan mengapa pemain melakukan aksi.
2. **Motivasi:** tujuan yang menarik pemain maju.
3. **Atmosfer:** nada dan identitas dunia.
4. **Hadiah:** potongan informasi sebagai imbalan eksplorasi.

Cerita **tidak boleh** menghalangi gameplay. Pemain yang ingin bermain harus bisa melewati cerita tanpa kehilangan kejelasan tujuan.

### 12.2 Aturan emas: cerita bisa dilewati, lore bisa digali

Bedakan dua lapisan:

|Lapisan|Fungsi|Cara penyampaian|Wajib?|
|---|---|---|---|
|Cerita utama (plot)|Alur dasar, tujuan, klimaks|Singkat, jelas, terintegrasi|Ya, tetapi ringkas|
|Lore (latar dunia)|Kedalaman dunia|Opsional: item, dokumen, lingkungan|Tidak|

Dengan pembagian ini, pemain kasual mendapat cerita yang cukup, pemain penasaran mendapat kedalaman.

### 12.3 Menyampaikan cerita tanpa voice actor

Ketiadaan voice actor adalah keputusan produksi yang sah dan memiliki banyak teknik kuat.

**a. Teks.**

- Dialog pendek (satu sampai tiga kalimat per kotak).
- Ritme baca nyaman (opsi kecepatan teks).
- Pemisahan nada karakter lewat gaya bahasa, bukan lewat banyak kata.
- Opsi lewati atau percepat dialog.

**b. Suara non-verbal.**

- **Voice blips:** bunyi pendek per karakter (seperti gumam) yang berbeda tiap karakter memberi identitas tanpa suara aktor.
- **Bahasa rekaan (gibberish):** suara tak terbaca yang menunjukkan nada emosi.
- **Efek suara dan musik:** leitmotif (tema musik) untuk karakter atau lokasi.

**c. Visual.**

- **Ekspresi dan potret karakter** yang berubah sesuai emosi.
- **Animasi bahasa tubuh:** gestur menunjukkan sikap tanpa kata.
- **Ikon dan simbol:** gelembung ikon (misalnya tanda tanya, hati) menunjukkan reaksi.
- **Cutscene pantomim:** adegan tanpa dialog, mengandalkan gambar dan musik.

**d. Lingkungan (environmental storytelling).**

- Ruangan yang menceritakan kejadian lewat objek dan kondisi (kursi terguling, jejak darah, surat yang ditinggalkan).
- Pola cuaca, tingkat kerusakan, dan evolusi lokasi seiring cerita.

**e. Dokumen dan item.**

- Surat, catatan, deskripsi item, papan pengumuman.
- Deskripsi item adalah media lore yang murah dan efektif.

**f. Interaksi.**

- Pilihan pemain yang menunjukkan karakter (memilih menolong atau tidak).
- Mekanik yang menyampaikan tema (misalnya karakter melemah ketika sedih secara naratif).

### 12.4 Menulis teks game yang efektif

Prinsip penulisan:

1. **Singkat dan jelas.** Pemain membaca sambil bermain.
2. **Fokus pada tindakan dan emosi.** Hindari eksposisi panjang.
3. **Satu ide per kotak dialog.**
4. **Suara karakter berbeda.** Tentukan kosa kata, ritme, dan kebiasaan tiap karakter.
5. **Beri informasi sesuai konteks.** Berikan tepat saat dibutuhkan, bukan semua di awal.
6. **Hormati waktu pemain.** Dialog opsional diberi penanda.

Contoh perbandingan:

```
Kurang efektif:
"Wahai petualang, dahulu kala kerajaan ini dipimpin oleh raja bijak yang
memiliki tiga putra, dan salah satu dari mereka mengkhianati ayahnya..."
(terlalu panjang, menghentikan permainan)

Lebih efektif:
Penjaga: "Jangan masuk. Terakhir kali ada yang masuk, hanya suaranya yang kembali."
(singkat, menimbulkan rasa penasaran)
```

### 12.5 Ludonarrative harmony

**Ludonarrative harmony** berarti mekanik (ludo) dan cerita (narrative) sejalan. **Dissonance** terjadi saat keduanya bertentangan, misalnya cerita menyatakan karakter pasifis tetapi gameplay mendorongnya membunuh ratusan musuh tanpa konsekuensi.

Cara menjaga keselarasan:

- Tema cerita tercermin dalam mekanik (misalnya tema "bertahan hidup" tercermin dalam sumber daya terbatas).
- Kemajuan cerita berkaitan dengan kemampuan baru (mekanik baru muncul bersama momen cerita).
- Konsekuensi dalam game mencerminkan nilai cerita.

### 12.6 Struktur cerita ringan untuk game

Gunakan **struktur tiga babak yang sangat ringkas** dan kaitkan dengan progres gameplay:

|Babak|Cerita|Gameplay|
|---|---|---|
|Awal|Pengenalan dunia dan tujuan|Tutorial terintegrasi, mekanik dasar|
|Tengah|Kendala dan pengungkapan|Mekanik berkembang, area bervariasi, boss tengah|
|Akhir|Klimaks dan resolusi|Ujian semua mekanik, boss akhir|

Catat **story beats** (momen penting) dan pasangkan dengan **gameplay beats** (momen mekanik penting).

### 12.7 Quest design untuk game gameplay-first

Quest yang baik adalah **gameplay dengan konteks**, bukan daftar tugas membosankan.

Jenis quest dan kelemahannya:

|Jenis|Risiko|Perbaikan|
|---|---|---|
|Fetch (ambil barang)|Monoton|Bangun rintangan menarik pada jalur, beri twist|
|Kill (bunuh N musuh)|Repetitif|Variasikan musuh dan konteks, beri alasan cerita|
|Escort (kawal)|Menjengkelkan|Buat NPC tangguh dan mandiri|
|Eksplorasi|Pemain tersesat|Beri petunjuk dan penanda halus|
|Puzzle|Kesulitan tidak sesuai|Beri petunjuk bertahap|

**Quest yang ideal** memperkenalkan mekanik atau area baru, mengungkap lore, dan memberi hadiah yang berguna.

### 12.8 Karakter dan pemain

- **Protagonis diam (silent protagonist):** pemain memproyeksikan diri. Murah dan cocok tanpa voice actor, tetapi hindari kesan kosong dengan memberi reaksi lewat animasi.
- **Protagonis berkarakter:** punya kepribadian lewat teks pilihan dan animasi. Perlu penulisan lebih kuat.
- **Karakter pendamping:** membantu menyampaikan eksposisi secara alami lewat percakapan singkat.

### 12.9 Lokalisasi (terjemahan)

Tanpa voice actor, lokalisasi jauh lebih murah dan menjangkau pasar lebih luas. Tips:

1. **Pisahkan teks dari kode.** Simpan semua teks dalam tabel atau file bahasa (misalnya CSV atau JSON).
2. **Jangan menyatukan kalimat di kode.** Urutan kata antar-bahasa berbeda.
3. **Sisakan ruang UI.** Terjemahan bisa lebih panjang dari aslinya.
4. **Gunakan font yang mendukung banyak karakter** bila menargetkan bahasa tertentu.
5. **Beri konteks penerjemah.** Catatan tentang siapa berbicara dan nuansanya.

### 12.10 Pacing cerita dalam gameplay

- Hindari **info dump**: jangan memberi banyak teks sekaligus.
- Selipkan cerita di **momen tenang**, bukan di tengah tekanan combat.
- Biarkan pemain **mengendalikan kecepatan** (lewati, ulangi, jurnal).
- Sediakan **jurnal atau codex** berisi ringkasan agar pemain yang lupa bisa membaca ulang.

### Kesalahan umum

- Cutscene dan dialog panjang yang tidak bisa dilewati.
- Lore sebagai syarat memahami gameplay.
- Mekanik yang bertentangan dengan tema cerita.
- Teks tersebar di kode sehingga sulit diterjemahkan.

### Latihan

1. Tulis sinopsis cerita utama Anda dalam maksimal 5 kalimat.
2. Tulis 3 potongan lore dalam bentuk deskripsi item, masing-masing maksimal 3 kalimat.
3. Rancang satu lokasi dengan environmental storytelling (daftar 5 objek yang menceritakan kejadian).
4. Pasangkan 5 story beats dengan gameplay beats.

### Ringkasan

- Cerita mendukung gameplay, lore opsional untuk digali.
- Tanpa voice actor, gunakan teks, voice blips, visual, lingkungan, dan musik.
- Jaga keselarasan mekanik dan tema.

---

## Bab 13. UX, Onboarding, HUD, Kamera, dan Input

### Tujuan bab

- Merancang onboarding yang efektif.
- Merancang HUD dan menu yang jelas.
- Mengatur kamera dan input untuk kenyamanan.

### 13.1 Onboarding

**Onboarding** adalah proses mengajarkan pemain cara bermain. Prinsip:

1. **Learn by doing:** pemain mempelajari dengan melakukan, bukan membaca.
2. **Satu hal sekaligus:** jangan mengenalkan banyak mekanik bersamaan.
3. **Aman untuk gagal:** area belajar tanpa hukuman berat.
4. **Beri umpan balik instan:** pemain tahu bahwa aksinya benar.
5. **Ajarkan saat relevan (just-in-time):** petunjuk muncul ketika dibutuhkan.
6. **Dapat diulang:** sediakan menu panduan atau latihan ulang.

Cara mengajar tanpa teks panjang:

- Ruang aman dengan satu rintangan tunggal yang memaksa mencoba mekanik.
- Visual sederhana (ikon tombol yang muncul dekat objek yang bisa diinteraksi).
- Contoh dari NPC atau animasi demonstrasi singkat.
- Gating alami: area berikutnya baru terbuka setelah mekanik dipakai.

### 13.2 Tutorial yang baik dan buruk

|Buruk|Baik|
|---|---|
|Dinding teks di awal|Petunjuk singkat saat diperlukan|
|Memaksa mengikuti urutan yang tidak bisa dilewati|Opsi lewati untuk pemain berpengalaman|
|Memberi semua mekanik dalam 5 menit pertama|Memperkenalkan bertahap sepanjang game|
|Tidak mengajarkan kondisi kegagalan|Menunjukkan mengapa gagal dan cara memperbaiki|

### 13.3 Prinsip HUD

**HUD (Heads-Up Display)** menampilkan informasi saat bermain. Prinsip:

1. **Tampilkan hanya yang penting.** Setiap elemen bersaing mendapat perhatian.
2. **Hierarki visual:** informasi kritis (HP) lebih menonjol daripada informasi sekunder.
3. **Posisi konsisten** dan sesuai kebiasaan (HP di pojok, peta di pojok lain).
4. **Keterbacaan:** kontras tinggi, ukuran cukup untuk layar kecil.
5. **Bisa dikonfigurasi:** skala HUD dan opsi sembunyikan sebagian elemen.
6. **Diegetic bila memungkinkan:** informasi ditampilkan dalam dunia game (misalnya HP terlihat dari kondisi pakaian) untuk imersi, tetapi hati-hati agar tetap terbaca.

Jenis HUD:

|Jenis|Penjelasan|
|---|---|
|Non-diegetic|Overlay di layar, tidak ada di dunia (bar HP biasa)|
|Diegetic|Ada di dunia game (layar di senjata)|
|Spatial|Muncul di dunia 3D tetapi bukan objek dunia (penanda di atas musuh)|
|Meta|Efek layar (tepi memerah saat terluka)|

### 13.4 Desain menu dan navigasi

- Semua menu harus bisa dioperasikan dengan **kontroler, keyboard, dan mouse**.
- Sediakan **fokus yang jelas** (elemen terpilih terlihat nyata).
- Hindari menu bersarang terlalu dalam.
- Beri **konfirmasi** untuk aksi destruktif (hapus save).
- Pause harus bisa diakses kapan saja, dengan akses cepat ke opsi.

### 13.5 Kamera

Kamera adalah "mata" pemain dan salah satu sumber masalah terbesar pada game 3D.

**Kamera 2D:**

- **Look-ahead:** kamera sedikit bergerak ke arah gerakan agar pemain melihat lebih jauh.
- **Smoothing:** pergerakan halus dengan damping.
- **Zona kamera:** batasi area kamera per ruangan.
- **Kamera dinamis:** zoom saat boss atau area luas.

**Kamera 3D:**

- **Third person:** hindari kamera menembus dinding (collision kamera), beri opsi sensitivitas dan invert.
- **Lock-on:** kamera mengikuti target.
- **Auto-recenter:** kamera menyesuaikan di belakang pemain saat bergerak (opsional).
- **Occlusion:** objek yang menutupi karakter dibuat transparan.
- **Opsi kenyamanan:** field of view (FOV), motion blur, head bob dapat diatur.

**Aturan:** kamera yang baik hampir tidak disadari. Jika pemain mengeluhkan kamera, itu masalah serius.

### 13.6 Input dan kontrol

Prinsip:

1. **Desain untuk kontroler terlebih dahulu**, lalu sesuaikan untuk keyboard dan mouse (atau sebaliknya sesuai genre), karena banyak pemain memakai kontroler atau perangkat genggam.
2. **Pemetaan konsisten:** tombol yang sama untuk fungsi yang mirip.
3. **Remap kontrol:** izinkan pemain menyesuaikan.
4. **Dead zone:** atur ambang stik agar tidak ada drift.
5. **Umpan balik haptik:** getaran kontroler untuk dampak (sediakan opsi mematikan).
6. **Kurangi beban tombol:** terlalu banyak aksi pada satu tombol membuat menu "kontekstual" membingungkan.

Tabel pertimbangan kontrol:

|Hal|Pertanyaan evaluasi|
|---|---|
|Jumlah tombol|Apakah semua aksi muat dalam skema kontroler standar?|
|Aksi kritis|Apakah bisa dilakukan tanpa melepas stik kamera?|
|Hold vs toggle|Apakah pemain boleh memilih?|
|Kombinasi|Apakah ada kombinasi tombol yang menyulitkan secara fisik?|

### 13.7 Petunjuk interaksi

- Tampilkan **prompt** (misalnya ikon tombol) saat dekat objek interaktif.
- Ikon menyesuaikan perangkat input yang sedang dipakai (kontroler atau keyboard).
- Beri **umpan balik** setelah interaksi (suara, animasi).

### Kesalahan umum

- Tutorial berupa layar teks panjang.
- HUD penuh angka yang tidak berguna.
- Kamera menembus dinding dan menutupi aksi.
- Tidak mendukung remap kontrol.

### Latihan

1. Rancang onboarding 5 menit pertama game Anda tanpa dialog tutorial.
2. Buat sketsa HUD yang hanya menampilkan 4 elemen penting.
3. Uji kamera di ruang sempit dan catat masalah.

### Ringkasan

- Onboarding terbaik adalah belajar sambil melakukan.
- HUD fokus pada informasi penting, konfigurable.
- Kamera dan input yang baik hampir tak terasa tetapi sangat memengaruhi pengalaman.

---

## Bab 14. Desain Khusus Game Offline

### Tujuan bab

- Memanfaatkan keunggulan game offline.
- Merancang save system dan checkpoint yang ramah.
- Merancang replayability tanpa fitur online.

### 14.1 Keunggulan game offline bagi desainer

|Keunggulan|Implikasi desain|
|---|---|
|Tidak ada pemain lain yang memengaruhi|Anda bebas mengatur kesulitan, tempo, dan cerita|
|Tidak perlu menjaga keseimbangan kompetitif|Fokus pada pengalaman, bukan "adil terhadap pemain lain"|
|Tidak butuh server|Biaya operasional rendah, game tetap bisa dimainkan bertahun-tahun|
|Pemain mengendalikan sesi|Pause kapan saja, tidak ada tekanan waktu eksternal|
|Cheat tidak merugikan orang lain|Anda dapat mengizinkan mode bebas atau debug untuk pemain|

Karena game dapat dimainkan selamanya tanpa server, **stabilitas dan kualitas rilis** menjadi penting. Patch tetap mungkin, tetapi jangan bergantung padanya.

### 14.2 Save system

Prinsip:

1. **Auto-save di titik yang adil:** setelah pencapaian penting, bukan di tengah pertarungan.
2. **Beberapa slot** dan opsi **backup otomatis** (simpan 2 sampai 3 versi terakhir).
3. **Save cepat saat keluar:** jangan memaksa pemain menyelesaikan bagian panjang.
4. **Versi save:** sertakan nomor versi agar update game tidak merusak save lama.
5. **Validasi data:** tangani save rusak dengan pesan jelas dan opsi pulihkan.
6. **Indikator menyimpan:** ikon kecil agar pemain tidak menutup game saat proses simpan.

Pilihan model save:

|Model|Penjelasan|Cocok untuk|
|---|---|---|
|Save bebas (kapan saja)|Pemain simpan di mana saja|Game bertempo santai, puzzle, strategi|
|Checkpoint|Titik simpan otomatis|Aksi, platformer|
|Save di lokasi khusus|Hanya di titik tertentu|Game dengan ketegangan dan sumber daya|
|Save di akhir sesi|Progres tersimpan setelah selesai|Roguelite|

**Pertimbangan keadilan:** semakin keras hukuman kematian, semakin dekat checkpoint seharusnya.

### 14.3 Replayability

Cara meningkatkan nilai ulang tanpa online:

1. **Build dan pilihan berbeda:** kelas, kemampuan, atau jalur.
2. **New Game Plus:** mengulang dengan kemampuan sebelumnya dan tantangan lebih berat.
3. **Konten acak terkurasi** (Bab 11).
4. **Mode tantangan:** run cepat (speedrun), batasan khusus, kesulitan tinggi.
5. **Banyak akhir:** cabang yang dipengaruhi pilihan.
6. **Koleksi:** item, lore, achievement.
7. **Seed harian offline:** tantangan berdasarkan tanggal.
8. **Mod support:** komunitas dapat memperluas konten (butuh perencanaan sejak awal).

### 14.4 Durasi dan pacing keseluruhan

Tentukan target durasi dan **jaga setiap jamnya**. Lebih baik 6 jam yang padat daripada 20 jam yang diregangkan. Tanyakan pada setiap segmen: "Apa yang baru di sini?" Jika jawabannya "tidak ada", potong atau ubah.

### 14.5 Mode foto, galeri, dan fitur pendamping

Fitur kecil yang menambah nilai di game offline:

- Galeri koleksi (lore, monster, item).
- Mode foto.
- Statistik permainan (waktu bermain, kematian, pencapaian).
- Mode latihan untuk boss yang sudah dikalahkan (boss rush).

### 14.6 Perangkat dan performa

Karena banyak pemain memakai perangkat bervariasi (termasuk handheld), pertimbangkan:

- **Opsi grafis** yang jelas (resolusi, kualitas, batas FPS).
- **Frame rate stabil** lebih penting daripada efek visual berat.
- **Penggunaan baterai** untuk perangkat genggam: sediakan batas FPS.
- **Waktu loading singkat** atau tersamarkan (misalnya lewat transisi desain).
- **Game dapat di-pause dan dilanjutkan** (suspend) dengan aman.

### 14.7 Anti-frustrasi di game offline

Karena tidak ada pemain lain, frustrasi hampir selalu berasal dari desain. Daftar periksa:

- Apakah ada situasi yang tidak adil atau tak bisa dijelaskan?
- Apakah pemain kehilangan waktu terlalu banyak saat gagal?
- Apakah ada bagian yang membosankan tetapi wajib diulang?
- Apakah ada jalan buntu atau bug progres?

### Kesalahan umum

- Save di titik yang bisa membuat pemain terjebak.
- Save lama tidak kompatibel dengan update.
- Menggelembungkan durasi dengan pengulangan.
- Mengabaikan performa di perangkat kelas bawah.

### Latihan

1. Tentukan model save untuk game Anda dan alasannya.
2. Rancang 3 fitur replayability yang realistis untuk skala tim Anda.
3. Tulis target durasi dan daftar "apa yang baru" tiap jam.

### Ringkasan

- Offline memberi kebebasan desain, tetapi menuntut kualitas rilis.
- Save system yang adil dan aman adalah bagian dari desain.
- Replayability dibangun dari pilihan, variasi, dan tantangan.

---

## Bab 15. Playtesting dan Iterasi Berbasis Data

### Tujuan bab

- Menjalankan playtest yang menghasilkan wawasan.
- Mengumpulkan data kualitatif dan kuantitatif.
- Memprioritaskan perbaikan.

### 15.1 Mengapa playtest

Anda sebagai pembuat sudah terlalu dekat dengan game. Anda tahu cara bermain dan "melihat" apa yang pemain tidak lihat. Playtest dengan orang baru adalah satu-satunya cara jujur menguji desain.

### 15.2 Jenis playtest

|Jenis|Tujuan|Kapan|
|---|---|---|
|Playtest pribadi|Cek dasar, bug jelas|Terus-menerus|
|Teman dan keluarga|Umpan balik awal|Prototipe awal|
|Pemain target (orang asing)|Uji daya tarik dan kejelasan|Vertical slice dan seterusnya|
|Playtest terarah|Menguji hal spesifik (misalnya tutorial)|Setelah perubahan besar|
|Beta terbuka atau demo|Skala lebih besar, data lebih banyak|Menjelang rilis|

### 15.3 Protokol playtest

Langkah praktis:

1. **Tentukan pertanyaan:** misalnya "Apakah pemain memahami cara dash tanpa petunjuk?"
2. **Siapkan build stabil** dan lingkungan tenang.
3. **Jangan membantu.** Amati diam-diam. Catat di mana pemain bingung.
4. **Minta pemain berpikir keras (think aloud)** bila cocok.
5. **Rekam layar dan suara** (dengan izin).
6. **Catat perilaku, bukan hanya komentar.** Pemain sering tidak tepat menjelaskan alasan, tetapi tindakan mereka jujur.
7. **Wawancara singkat setelahnya.**

### 15.4 Pertanyaan pasca-playtest

Contoh pertanyaan netral:

- "Bagian mana yang paling Anda ingat?"
- "Apa yang membuat Anda bingung?"
- "Kalau menjelaskan game ini ke teman, apa katanya?"
- "Pada titik mana Anda ingin berhenti, jika ada?"
- "Apa yang ingin Anda lakukan tetapi tidak bisa?"

Hindari pertanyaan menggiring ("Bukankah boss itu seru?").

### 15.5 Data telemetri lokal

Pada game offline, Anda dapat mencatat data **lokal** selama playtest (dengan izin) tanpa server. Contoh data:

|Data|Manfaat|
|---|---|
|Lokasi kematian|Menemukan titik tersulit|
|Waktu per area|Menemukan area membosankan atau membingungkan|
|Penggunaan item dan senjata|Menemukan strategi dominan atau item tak terpakai|
|Titik berhenti bermain|Menemukan kapan pemain menyerah|
|Jumlah percobaan boss|Mengukur kesulitan|

Visualisasikan dengan **heatmap kematian** pada peta level. Titik panas menunjukkan masalah.

> Etika: beri tahu pemain data apa yang dicatat, minta persetujuan, dan jangan mengumpulkan data pribadi. Patuhi aturan privasi yang berlaku di wilayah pemain dan kebijakan platform.

### 15.6 Menafsirkan umpan balik

- **Pola lebih penting daripada satu komentar.** Jika 3 dari 5 orang bingung di titik yang sama, itu masalah nyata.
- **Pisahkan gejala dari penyebab.** "Boss terlalu sulit" mungkin berarti telegraph buruk, bukan HP terlalu besar.
- **Jangan mengikuti solusi pemain secara harfiah.** Dengar masalahnya, rancang solusinya sendiri.
- **Waspadai bias:** teman cenderung terlalu sopan, pemain ahli tidak mewakili pemula.

### 15.7 Prioritas perbaikan

Gunakan matriks dampak dan usaha:

||Usaha kecil|Usaha besar|
|---|---|---|
|Dampak besar|Kerjakan segera|Rencanakan|
|Dampak kecil|Kerjakan bila sempat|Tunda atau batalkan|

Prioritaskan masalah yang membuat pemain **berhenti bermain** (blocker) daripada masalah kosmetik.

### 15.8 Siklus iterasi

```
Hipotesis -> Ubah -> Uji -> Ukur -> Pelajari -> (ulang)
```

Ubah **satu variabel pada satu waktu** agar tahu penyebab perubahan. Catat setiap eksperimen dan hasilnya (jurnal desain).

### Kesalahan umum

- Membantu pemain saat playtest sehingga masalah tersembunyi.
- Hanya menguji dengan teman dekat.
- Mengubah banyak hal sekaligus.
- Mengabaikan data karena "sudah merasa tahu".

### Latihan

1. Jalankan playtest 3 orang dan catat perilaku (bukan hanya komentar).
2. Buat heatmap kematian sederhana (bisa manual).
3. Susun daftar 10 temuan dan prioritaskan dengan matriks dampak-usaha.

### Ringkasan

- Amati perilaku pemain, jangan membantu.
- Telemetri lokal dan heatmap menemukan masalah objektif.
- Iterasi satu variabel per waktu.

---

## Bab 16. Produksi Indie: Scope, Prototipe, dan Dokumentasi

### Tujuan bab

- Mengelola scope agar proyek selesai.
- Membangun prototipe dan vertical slice.
- Menulis dokumentasi desain yang ringkas dan berguna.

### 16.1 Musuh utama: scope creep

**Scope creep** adalah pembengkakan lingkup proyek karena penambahan fitur terus-menerus. Penyebab utama proyek indie gagal selesai.

Strategi menjaga scope:

1. **Mulai kecil.** Game pertama sebaiknya jauh lebih kecil dari mimpi Anda.
2. **Potong tanpa ampun.** Daftar "must have", "should have", "nice to have". Kerjakan must have dulu.
3. **Gunakan pilar** untuk menolak fitur.
4. **Hitung biaya konten.** Setiap level, musuh, dan item membutuhkan desain, seni, suara, uji. Hitung total.
5. **Tambahkan buffer.** Perkiraan waktu sebaiknya dikalikan 1,5 sampai 2.

### 16.2 Tahapan produksi

|Tahap|Tujuan|Hasil|
|---|---|---|
|Konsep|Ide, pilar, target pemain|Dokumen satu halaman|
|Prototipe|Menguji inti gameplay|Prototipe kasar, greybox|
|Vertical slice|Satu potongan lengkap dengan kualitas hampir final|Demo singkat (10 sampai 30 menit)|
|Produksi|Membuat seluruh konten|Konten lengkap versi alfa|
|Polish dan beta|Memperbaiki, menguji, menyempurnakan|Versi kandidat rilis|
|Rilis dan pasca-rilis|Peluncuran dan perbaikan|Game dirilis, patch jika perlu|

### 16.3 Prototipe

Tujuan prototipe adalah **menjawab pertanyaan desain** secepat mungkin, bukan membuat produk indah.

Aturan prototipe:

1. Tentukan **satu pertanyaan** ("Apakah mekanik kait tali menyenangkan?").
2. Pakai bentuk sederhana (kotak, placeholder).
3. Batasi waktu (misalnya 1 sampai 2 minggu).
4. Siap **dibuang**. Prototipe bukan kode produksi.
5. Catat hasil: lanjut, ubah, atau batalkan.

### 16.4 Vertical slice

**Vertical slice** adalah potongan game yang mewakili seluruh pengalaman akhir: gameplay inti, seni, suara, UI, dan sedikit cerita dalam kualitas hampir final. Manfaat:

- Membuktikan bahwa game benar-benar menyenangkan.
- Menjadi dasar demo dan materi promosi.
- Memperkirakan biaya produksi sisa dengan lebih akurat.

Jika vertical slice tidak menyenangkan, memperbanyak konten tidak akan memperbaikinya.

### 16.5 Dokumentasi desain yang ringkas

Hindari dokumen desain raksasa yang tak pernah dibaca. Pilih dokumen **hidup dan ringkas**:

1. **Halaman satu (one-pager):** konsep, pilar, target pemain, fitur utama.
2. **Dokumen mekanik:** aturan, parameter, interaksi (matriks).
3. **Dokumen konten:** daftar musuh, item, level (spreadsheet).
4. **Dokumen cerita dan lore:** ringkasan alur, karakter, glosarium dunia.
5. **Jurnal desain:** catatan keputusan dan alasannya.

Gunakan wiki atau repositori catatan. Perbarui setiap ada perubahan penting.

### 16.6 Manajemen tugas

Gunakan papan sederhana (Todo, Doing, Done) atau metode sprint satu sampai dua minggu. Prinsip:

- Tugas kecil dan jelas (selesai dalam 1 sampai 2 hari).
- Batasi pekerjaan yang berjalan bersamaan.
- Tinjau mingguan: apa yang selesai, apa yang menghambat.

### 16.7 Risiko dan strategi

|Risiko|Pencegahan|
|---|---|
|Fitur terlalu ambisius|Prototipe cepat, potong lebih awal|
|Kelelahan (burnout)|Jadwal realistis, jeda, tujuan kecil|
|Ketergantungan satu orang|Dokumentasi, kode terstruktur|
|Kehilangan data|Version control dan backup otomatis|
|Tidak ada audiens|Bangun komunitas sejak awal, bagikan perkembangan|

**Wajib:** gunakan **version control** (misalnya Git) sejak hari pertama dan lakukan backup di lokasi terpisah.

### 16.8 Komponen jangka panjang: polish

Polish adalah banyak perbaikan kecil yang membuat game terasa profesional: transisi halus, suara responsif, animasi mulus, teks bebas typo, pesan error jelas. Sisihkan waktu khusus (misalnya 15 sampai 25 persen) untuk polish.

### 16.9 Menentukan kapan berhenti menambah fitur

Terapkan **feature freeze**: setelah titik tertentu, tidak ada fitur baru, hanya perbaikan dan polish. Ini sering memisahkan proyek yang selesai dari yang tidak.

### Kesalahan umum

- Memulai dengan game raksasa sebagai proyek pertama.
- Tidak menguji inti gameplay sebelum membuat konten.
- Tidak memakai version control.
- Tidak ada feature freeze.

### Latihan

1. Tulis one-pager game Anda.
2. Buat daftar fitur dan kelompokkan menjadi must, should, nice.
3. Rencanakan vertical slice dengan daftar isi dan perkiraan waktu.

### Ringkasan

- Scope adalah faktor penentu keberhasilan proyek indie.
- Prototipe menjawab pertanyaan, vertical slice membuktikan kualitas.
- Dokumentasi ringkas dan hidup lebih berguna daripada dokumen panjang.

---

## Bab 17. Studi Kasus Analisis Genre

Bab ini melatih cara berpikir **menganalisis** game lewat kerangka yang sama. Anda tidak perlu menyalin game tertentu. Gunakan polanya untuk menganalisis game yang Anda sukai. Contoh di bawah bersifat generik agar tidak bergantung pada satu judul.

### 17.1 Kerangka analisis

Untuk setiap game, jawab:

1. **Pilar:** apa 3 hal inti yang dijanjikan?
2. **Core loop:** apa aksi yang diulang dan imbalannya?
3. **Sistem:** mekanik apa yang berinteraksi?
4. **Kesulitan:** bagaimana kurva dan opsi kesulitan?
5. **Level dan pacing:** bagaimana pemain diajari dan diarahkan?
6. **Narasi:** bagaimana cerita disampaikan?
7. **Kelemahan:** apa yang bisa diperbaiki?

### 17.2 Studi 1: Platformer 2D presisi

|Aspek|Analisis tipikal|
|---|---|
|Pilar|Kontrol presisi, kegagalan cepat, penguasaan|
|Core loop|Melompati rintangan, mati, ulang cepat, berhasil|
|Teknik kunci|Coyote time, buffer, respawn instan, checkpoint rapat|
|Level design|Tiap ruang mengajarkan satu ide, pola Introduce-Develop-Twist-Conclude|
|Narasi|Minimal: teks singkat, simbol, atmosfer|
|Risiko|Kesulitan terlalu tinggi, kelelahan|
|Solusi|Assist mode, jalur opsional, checkpoint murah|

**Pelajaran:** game yang sulit tetap terasa adil bila kegagalan cepat dan informatif.

### 17.3 Studi 2: Action RPG 3D berbasis eksplorasi

|Aspek|Analisis tipikal|
|---|---|
|Pilar|Eksplorasi bebas, combat bermakna, dunia bercerita|
|Core loop|Jelajah, temukan musuh dan harta, bertarung, perkuat karakter|
|Sistem|Stamina, lock-on, build karakter|
|Level design|Landmark, sightline, shortcut, area terbuka dan ruang rahasia|
|Narasi|Lore lewat deskripsi item, lingkungan, NPC bersuara teks|
|Risiko|Kamera, musuh berkelompok, inventori rumit|
|Solusi|Attack token, kamera adaptif, UI sederhana|

**Pelajaran:** kebebasan butuh struktur halus (landmark dan shortcut) agar pemain tidak tersesat.

### 17.4 Studi 3: Metroidvania

|Aspek|Analisis tipikal|
|---|---|
|Pilar|Eksplorasi, kemampuan baru, penguasaan peta|
|Core loop|Temukan kemampuan, buka area lama, temukan lebih banyak|
|Sistem|Gerbang kemampuan, peta, shortcut|
|Level design|Graph dunia saling terhubung|
|Narasi|Fragmen lore, lingkungan, boss bersimbol|
|Risiko|Pemain tersesat, backtracking membosankan|
|Solusi|Peta berguna, fast travel, penanda "ruang belum selesai"|

**Pelajaran:** kemampuan baru harus mengubah cara pemain melihat dunia lama.

### 17.5 Studi 4: Roguelite aksi

|Aspek|Analisis tipikal|
|---|---|
|Pilar|Variasi run, pembuatan build, penguasaan lewat pengulangan|
|Core loop|Masuk ruang, bertarung, pilih upgrade, lanjut|
|Sistem|Upgrade bersinergi, meta progression|
|Level design|Ruang prefabrikasi, anggaran kesulitan|
|Narasi|Cerita maju antar-run|
|Risiko|Run terasa seragam, meta membuat terlalu mudah|
|Solusi|Sinergi besar, tantangan opsional, opsi baru (bukan hanya angka)|

**Pelajaran:** kematian harus menjadi bahan bakar motivasi, bukan hukuman.

### 17.6 Studi 5: Puzzle dan eksplorasi tenang

|Aspek|Analisis tipikal|
|---|---|
|Pilar|Rasa penasaran, momen "aha", suasana|
|Core loop|Amati, bereksperimen, pahami aturan, selesaikan|
|Sistem|Aturan sederhana dengan kombinasi dalam|
|Level design|Kurva pengenalan aturan bertahap|
|Narasi|Lingkungan dan simbol, tanpa dialog panjang|
|Risiko|Puzzle terlalu sulit atau tidak adil|
|Solusi|Petunjuk bertahap, puzzle opsional, tombol lewati|

**Pelajaran:** puzzle terbaik mengajarkan aturan lewat contoh, bukan teks.

### 17.7 Studi 6: Survival dan crafting ringan

|Aspek|Analisis tipikal|
|---|---|
|Pilar|Bertahan hidup, penguasaan sumber daya, kemandirian|
|Core loop|Kumpulkan sumber daya, buat alat, bertahan, perluas|
|Sistem|Sumber daya, crafting, cuaca atau waktu|
|Ekonomi|Faucet (lingkungan), sink (konsumsi dan pembuatan)|
|Risiko|Grind berlebihan, inventori menyebalkan|
|Solusi|Batas jelas, resep sederhana, kualitas hidup (auto-sort, bawa lebih banyak)|

**Pelajaran:** crafting harus menciptakan keputusan, bukan sekadar pekerjaan.

### 17.8 Latihan analisis

Pilih satu game yang pernah Anda mainkan. Isi tabel kerangka analisis (17.1). Tulis juga:

1. Satu hal yang akan Anda tiru prinsipnya (bukan salin konten).
2. Satu hal yang akan Anda perbaiki.
3. Satu hal yang akan Anda hindari.

---

## Bab 18. Proyek Akhir 12 Minggu

Proyek ini menyatukan seluruh bab menjadi **satu vertical slice** yang dapat dimainkan 15 sampai 30 menit.

### 18.1 Aturan proyek

- **Skala:** satu mekanik inti, 3 musuh, 1 boss, 3 sampai 5 area atau ruang.
- **Dimensi:** pilih 2D atau 3D (2D lebih disarankan untuk pemula).
- **Mode:** offline.
- **Cerita:** singkat, tanpa voice actor, lewat teks dan lingkungan.
- **Tujuan:** menyenangkan, bukan lengkap.

### 18.2 Jadwal mingguan

|Minggu|Fokus|Output|
|---|---|---|
|1|Konsep dan pilar (Bab 1)|One-pager, pilar, player fantasy|
|2|Core loop dan prototipe (Bab 2)|Prototipe gerakan dan aksi inti|
|3|Game feel (Bab 3)|Kontrol responsif, juice dasar|
|4|Sistem dan combat (Bab 4, 7)|Matriks interaksi, 3 musuh dasar|
|5|Balancing dan ekonomi (Bab 5, 6)|Spreadsheet angka, loot sederhana|
|6|AI dan boss (Bab 8)|AI musuh, desain boss tiga fase|
|7|Level design (Bab 9)|Greybox level dan pola pengenalan mekanik|
|8|Progression dan kesulitan (Bab 10)|Upgrade, opsi kesulitan dan aksesibilitas|
|9|Narasi dan lore (Bab 12)|Dialog, item lore, environmental storytelling|
|10|UX dan kamera (Bab 13, 14)|Onboarding, HUD, save system|
|11|Playtest dan iterasi (Bab 15)|Laporan playtest, perbaikan prioritas|
|12|Polish dan rilis demo (Bab 16)|Build final, halaman proyek, video singkat|

### 18.3 Kriteria penilaian mandiri

Beri nilai 1 sampai 5 pada tiap kriteria:

|Kriteria|Pertanyaan|
|---|---|
|Core loop|Menyenangkan tanpa progression?|
|Game feel|Kontrol responsif dan memuaskan?|
|Keterbacaan|Telegraph dan HUD jelas?|
|Keadilan|Kematian bisa dijelaskan?|
|Onboarding|Pemain baru paham tanpa bantuan?|
|Pacing|Ada jeda dan variasi?|
|Narasi|Cerita mendukung tanpa mengganggu?|
|Aksesibilitas|Opsi dasar tersedia?|
|Stabilitas|Bebas bug blocker?|
|Polish|Terasa rapi?|

Nilai rata-rata di bawah 3 pada kriteria tertentu menjadi prioritas perbaikan.

### 18.4 Setelah proyek selesai

1. Tulis **post-mortem**: apa yang berhasil, apa yang gagal, apa yang dipelajari.
2. Putuskan: kembangkan menjadi game penuh, atau mulai proyek baru dengan pelajaran tersebut.
3. Bagikan demo kepada komunitas dan kumpulkan umpan balik.

---

## Lampiran A. Template GDD Ringkas

Salin dan isi untuk proyek Anda.

```markdown
# [Judul Game]

## 1. Ringkasan
- Genre:
- Dimensi (2D/3D):
- Platform target:
- Target pemain:
- Satu kalimat konsep:

## 2. Pilar Desain
1.
2.
3.

## 3. Player Fantasy
-

## 4. Core Loop
- Aksi:
- Umpan balik:
- Imbalan:

## 5. Meta Loop dan Progression
-

## 6. Mekanik Utama
| Mekanik | Deskripsi | Parameter penting |
|---|---|---|

## 7. Musuh dan Boss
| Nama | Peran | HP | Serangan | Telegraph | Celah |
|---|---|---|---|---|---|

## 8. Level dan Dunia
- Daftar area:
- Graph/gerbang:
- Pola pengenalan mekanik:

## 9. Ekonomi dan Item
- Mata uang:
- Faucet:
- Sink:
- Loot:

## 10. Kesulitan dan Aksesibilitas
- Opsi kesulitan:
- Fitur aksesibilitas:

## 11. Cerita dan Lore
- Sinopsis (maks. 5 kalimat):
- Cara penyampaian (teks, lingkungan, item):
- Karakter utama:

## 12. UI, Kamera, dan Kontrol
- HUD:
- Kamera:
- Skema kontrol (kontroler):
- Skema kontrol (keyboard dan mouse):

## 13. Save dan Replayability
-

## 14. Rencana Produksi
- Must have:
- Should have:
- Nice to have:
- Jadwal:

## 15. Risiko
-
```

---

## Lampiran B. Template Laporan Playtest

```markdown
# Laporan Playtest

- Tanggal:
- Versi build:
- Jumlah pemain:
- Profil pemain (pemula/menengah/ahli):
- Tujuan playtest (pertanyaan yang diuji):

## Temuan Utama
| No | Temuan | Berapa pemain mengalami | Tingkat keparahan (blocker/besar/kecil) | Dugaan penyebab |
|---|---|---|---|---|

## Titik Bingung
-

## Titik Menyenangkan
-

## Kutipan Penting (paraphrase)
-

## Rekomendasi Perbaikan
| No | Tindakan | Dampak | Usaha | Prioritas |
|---|---|---|---|---|

## Hipotesis untuk Tes Berikutnya
-
```

---

## Lampiran C. Checklist Desain

### C.1 Checklist core loop dan feel

- [ ] Aksi inti menyenangkan tanpa progression.
- [ ] Kontrol responsif (buffer, coyote time, dan sebagainya).
- [ ] Umpan balik jelas dan proporsional.
- [ ] Opsi mengurangi efek (shake, flash) tersedia.

### C.2 Checklist combat

- [ ] Telegraph terlihat, terdengar, dan cukup lama.
- [ ] Setiap serangan ada recovery atau celah.
- [ ] Musuh punya peran yang berbeda.
- [ ] Boss memiliki fase dan pola yang dapat dipelajari.
- [ ] Attack token atau batas serangan serentak diterapkan.

### C.3 Checklist level

- [ ] Mekanik baru diperkenalkan di tempat aman.
- [ ] Jalur wajib jelas, jalur opsional bermakna.
- [ ] Tidak ada soft-lock.
- [ ] Ada jeda dan variasi.
- [ ] Greybox sudah menyenangkan sebelum seni final.

### C.4 Checklist balancing dan ekonomi

- [ ] Target TTK ditentukan.
- [ ] Tidak ada strategi dominan yang jelas.
- [ ] Faucet dan sink seimbang.
- [ ] Randomness dilengkapi pity timer atau shuffle bag bila perlu.
- [ ] Angka berada di data, bukan dikunci di kode.

### C.5 Checklist narasi

- [ ] Cerita bisa dilewati tanpa kehilangan arah.
- [ ] Lore opsional dan mudah digali.
- [ ] Mekanik selaras dengan tema.
- [ ] Teks terpisah dari kode (siap lokalisasi).
- [ ] Dialog singkat dan memiliki opsi percepat.

### C.6 Checklist UX dan aksesibilitas

- [ ] Onboarding tanpa teks panjang.
- [ ] HUD ringkas dan dapat diatur.
- [ ] Kamera tidak menembus dinding dan tidak menutupi aksi.
- [ ] Remap kontrol tersedia.
- [ ] Informasi penting tidak hanya lewat warna atau suara.
- [ ] Opsi ukuran teks dan subtitle tersedia.

### C.7 Checklist rilis game offline

- [ ] Save system aman, ada versi dan backup.
- [ ] Performa stabil di perangkat target.
- [ ] Tidak ada bug blocker progres.
- [ ] Demo atau cuplikan menunjukkan gameplay inti.
- [ ] Version control dan backup aktif.

---

## Lampiran D. Glosarium

|Istilah|Arti|
|---|---|
|Aesthetics (MDA)|Emosi atau pengalaman yang dirasakan pemain|
|Anticipation / Startup|Fase persiapan serangan sebelum damage|
|Attack token|Batas jumlah musuh yang boleh menyerang bersamaan|
|Behavior Tree|Struktur pohon untuk mengatur keputusan AI|
|Blockout / Greybox|Pembuatan level awal dari bentuk dasar tanpa seni final|
|Core loop|Siklus aksi inti yang diulang pemain|
|Coyote time|Jeda singkat untuk melompat setelah meninggalkan tepi|
|Critical path|Jalur wajib dari awal sampai akhir|
|DDA|Dynamic Difficulty Adjustment, penyesuaian kesulitan otomatis|
|Diegetic|Elemen UI yang ada di dalam dunia game|
|Emergent gameplay|Situasi yang muncul dari interaksi aturan, bukan dirancang satu per satu|
|Faucet|Sumber penambah sumber daya dalam ekonomi game|
|Flow|Keadaan terserap penuh saat tantangan setara kemampuan|
|FSM|Finite State Machine, model AI berbasis state|
|Game feel|Sensasi taktil saat mengendalikan game|
|GDD|Game Design Document, dokumen desain game|
|Hitbox|Area yang menentukan kena atau tidaknya serangan|
|Hitstop|Jeda singkat saat serangan mengenai untuk memberi bobot|
|HTK|Hits-to-Kill, jumlah serangan untuk menjatuhkan musuh|
|HUD|Heads-Up Display, informasi di layar saat bermain|
|Input buffering|Menyimpan input beberapa frame agar tetap dieksekusi|
|Juice|Lapisan umpan balik audio-visual yang memperkuat aksi|
|Leitmotif|Tema musik yang terkait karakter atau lokasi|
|Loot table|Daftar hadiah beserta peluang|
|Ludonarrative harmony|Keselarasan antara mekanik dan cerita|
|MDA|Mechanics, Dynamics, Aesthetics|
|Mechanics (MDA)|Aturan dan sistem dasar game|
|Meta loop|Siklus jangka panjang yang memotivasi pemain kembali|
|Navmesh|Mesh navigasi untuk pathfinding 3D|
|PCG|Procedural Content Generation|
|Pity timer|Mekanisme peluang naik tiap gagal untuk menghindari kesialan ekstrem|
|Player fantasy|Peran atau kekuatan yang ingin dirasakan pemain|
|Polish|Penyempurnaan detail kecil agar game terasa profesional|
|Prefab / Prefabrikasi|Aset atau ruang yang dibuat sebelumnya dan dipakai ulang|
|Recovery|Fase pemulihan setelah serangan|
|Respec|Mengatur ulang pilihan skill atau upgrade|
|Roguelite|Genre dengan run acak dan meta progression|
|Scope creep|Pembengkakan lingkup proyek|
|Seed|Angka awal pembangkit bilangan acak|
|Shuffle bag|Teknik acak tanpa pengembalian untuk distribusi merata|
|Sink|Pengurang sumber daya dalam ekonomi game|
|Soft-lock|Keadaan pemain terjebak tanpa jalan maju atau keluar|
|Telegraph|Isyarat bahwa serangan akan datang|
|TTK|Time-to-Kill, waktu menjatuhkan musuh|
|Utility AI|AI yang memilih aksi berdasarkan skor kegunaan|
|Vertical slice|Potongan game lengkap berkualitas hampir final|
|Voice blips|Bunyi pendek per karakter sebagai pengganti suara aktor|

---

## Lampiran E. Bahan Bacaan dan Sumber Belajar

Daftar berikut adalah rekomendasi kategori sumber belajar. Judul dan ketersediaan dapat berubah, jadi cari versi terbaru dan periksa apakah masih relevan.

### E.1 Buku (cari edisi terbaru)

- Buku tentang dasar teori desain game dan kerangka MDA (cari "A Book of Lenses" oleh Jesse Schell, "Rules of Play" oleh Katie Salen dan Eric Zimmerman).
- Buku tentang game feel (cari "Game Feel" oleh Steve Swink).
- Buku tentang level design dan pacing (cari buku dan artikel tentang level design dari berbagai praktisi).
- Buku tentang AI game (cari "Artificial Intelligence for Games" dan sumber tentang behavior tree).
- Buku tentang narrative design untuk game (cari karya praktisi narrative design).

### E.2 Sumber daring

- Kanal video dan seri analisis desain game (cari pembahasan "level design analysis", "game feel", "enemy design").
- Konferensi desain game: banyak presentasi lama tersedia gratis di arsip daring (cari arsip talk dari konferensi pengembang game).
- Artikel postmortem pengembang indie di blog dan portal berita industri game.
- Dokumentasi resmi engine pilihan Anda tentang navigasi, animasi, dan sistem input.
- Komunitas pengembang game Indonesia dan regional untuk umpan balik dan kolaborasi.

### E.3 Praktik belajar yang disarankan

1. **Mainkan dengan mata desainer.** Berhenti sejenak dan tanya: mengapa ini terasa baik atau buruk?
2. **Bongkar game favorit.** Isi kerangka analisis Bab 17.
3. **Ikuti game jam.** Batas waktu singkat melatih scope, prototipe, dan menyelesaikan.
4. **Tulis jurnal desain.** Catat keputusan dan alasannya.
5. **Bagikan karya Anda.** Umpan balik nyata adalah guru terbaik.

---

## Penutup

Game design tingkat lanjut bukan tentang menghafal teori, melainkan tentang **membuat keputusan yang bisa Anda jelaskan, uji, dan perbaiki**. Prinsip yang berulang di seluruh buku ini:

1. Inti gameplay harus menyenangkan secara mandiri.
2. Setiap sistem harus menghasilkan keputusan bermakna.
3. Keadilan dan keterbacaan lebih penting daripada kerumitan.
4. Cerita mendukung gameplay, bukan menghalanginya.
5. Uji dengan pemain nyata, ukur, lalu iterasi.
6. Jaga scope agar proyek benar-benar selesai.

Mulailah dari yang kecil, selesaikan, lalu belajar dari hasilnya. Proyek kecil yang selesai jauh lebih berharga daripada proyek besar yang tidak pernah rilis.

Selamat berkarya.