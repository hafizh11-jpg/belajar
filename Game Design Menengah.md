# Game Design Tingkat Menengah untuk Game Developer Indie

## Fokus Game 2D dan 3D, Ada Story dan Lore tetapi Gameplay Tetap Raja, Tanpa Voice Actor

Edisi untuk praktik di tahun 2026, 2027, dan seterusnya.

---

## Daftar Isi

1. Kata Pengantar dan Cara Memakai Buku Ini
2. Bab 1 - Realitas Indie Developer di Era 2026 dan Seterusnya
3. Bab 2 - Fondasi yang Harus Kuat: Core Loop, Pillars, dan Kerangka MDA
4. Bab 3 - Sistem Loop Berlapis: Micro, Core, Meta, dan Progression
5. Bab 4 - Mekanik, Dinamika, dan Emergent Gameplay
6. Bab 5 - Psikologi Pemain: Motivasi, Flow, dan Feedback
7. Bab 6 - Game Feel dan Juice: Membuat Aksi Terasa Enak
8. Bab 7 - Desain Kontrol dan Kamera (2D dan 3D)
9. Bab 8 - Level Design: Mengajar, Menantang, dan Mengatur Tempo
10. Bab 9 - Balancing, Ekonomi Game, dan Kurva Kesulitan
11. Bab 10 - Desain Musuh dan AI Gameplay
12. Bab 11 - Narrative Design dan Lore yang Melayani Gameplay (Tanpa Voice Actor)
13. Bab 12 - UI/UX, Onboarding, dan Aksesibilitas
14. Bab 13 - Prototyping, Playtesting, dan Iterasi
15. Bab 14 - Dokumentasi Desain yang Ringan tapi Berguna
16. Bab 15 - Manajemen Scope dan Produksi untuk Tim Kecil
17. Bab 16 - Memilih 2D atau 3D, dan Studi Kasus Genre
18. Bab 17 - Dari Desain ke Rilis: Demo, Wishlist, dan Monetisasi dari Sisi Desain
19. Bab 18 - Proyek Capstone dan Roadmap Belajar
20. Lampiran A - Glosarium
21. Lampiran B - Template Siap Pakai
22. Lampiran C - Bacaan dan Sumber Belajar Lanjutan

---

## Kata Pengantar dan Cara Memakai Buku Ini

### Untuk siapa buku ini

Buku ini ditulis untuk Anda yang:

- Sudah tahu konsep dasar membuat game (misalnya pernah mencoba engine seperti Godot, Unity, Unreal, atau GameMaker), atau minimal sudah memainkan banyak game dan penasaran bagaimana game dirancang.
- Ingin naik dari level "pemula" ke level "menengah" dalam hal **game design**, yaitu ilmu merancang pengalaman bermain, bukan ilmu menulis kode.
- Bekerja sendiri atau dalam tim kecil (1 sampai 5 orang), sehingga setiap keputusan desain harus realistis terhadap waktu dan tenaga.

### Apa yang membedakan buku ini

1. **Fokus pada gameplay.** Story dan lore tetap dibahas (Bab 11), tetapi posisinya melayani gameplay, bukan sebaliknya.
2. **Tanpa voice actor.** Semua teknik penceritaan di buku ini menggunakan teks, visual, level, musik, dan efek suara. Ini juga keputusan produksi yang hemat biaya dan mempermudah lokalisasi.
3. **Mencakup 2D dan 3D.** Prinsip desain dibahas secara umum, lalu perbedaan khusus 2D dan 3D ditandai dengan jelas.
4. **Bebas dari ketergantungan pada satu engine.** Contoh kode ditulis sebagai pseudocode (kode bayangan) agar bisa Anda terjemahkan ke engine apa pun.

### Catatan tentang tahun 2026 dan seterusnya

Engine, tools, dan kebijakan platform distribusi berubah cepat. Karena itu buku ini sengaja menekankan **prinsip yang tahan lama** (misalnya core loop, flow, balancing, playtesting) dan tidak mengikatkan diri pada nomor versi tertentu. Setiap kali buku ini menyebut tool atau kebijakan platform, anggap itu sebagai contoh dan **selalu cek dokumentasi resmi terbaru** sebelum mengambil keputusan produksi.

### Cara membaca

- Setiap bab memiliki: tujuan belajar, penjelasan konsep, contoh, kesalahan umum, dan latihan.
- Istilah bahasa Inggris dipertahankan karena itulah istilah yang dipakai di industri dan di dokumentasi engine. Setiap istilah dijelaskan saat pertama kali muncul, dan semuanya ada di Lampiran A.
- Kerjakan latihan. Game design adalah keterampilan praktik; membaca saja tidak cukup.

### Prasyarat yang disarankan

- Pernah menyelesaikan minimal satu prototipe sederhana (misalnya Pong, platformer satu level, atau game top-down kecil).
- Mampu memakai spreadsheet dasar (Google Sheets atau Excel) untuk Bab 9.
- Mau memainkan game orang lain secara analitis, yaitu bertanya "kenapa ini terasa seru atau membosankan?".

---

# Bab 1 - Realitas Indie Developer di Era 2026 dan Seterusnya

## Tujuan belajar

- Memahami posisi dan tantangan nyata game indie saat ini.
- Menentukan ukuran proyek yang realistis.
- Memahami peran game designer dalam tim kecil.

## 1.1 Lanskap singkat

Membuat game kini lebih mudah secara teknis dibanding satu atau dua dekade lalu: engine gratis atau murah, aset siap pakai, dan tool berbantuan AI untuk berbagai pekerjaan pendukung. Namun **jumlah game yang dirilis juga sangat besar**, sehingga bersaing untuk perhatian pemain justru lebih sulit. Artinya:

- Game yang hanya "jadi" tidak cukup. Game harus **punya alasan jelas untuk dimainkan** (hook).
- Desain yang tajam lebih berharga daripada grafis mewah. Banyak game indie sukses memiliki satu ide mekanik yang kuat dan dieksekusi dengan rapi.
- Kemampuan menyelesaikan proyek (finishing) adalah keunggulan kompetitif utama.

## 1.2 Peran AI dan tool otomatis dengan sikap yang sehat

Tool berbantuan AI dapat membantu pekerjaan seperti brainstorming, membuat placeholder, menulis kode boilerplate, atau merapikan dokumentasi. Beberapa catatan praktis:

- **Desain tetap keputusan Anda.** AI tidak memainkan game Anda dan tidak merasakan frustrasi pemain. Playtesting manusia tidak tergantikan.
- **Perhatikan hak cipta dan lisensi** aset yang dihasilkan. Kebijakan hukum dan platform berbeda-beda dan berubah. Beberapa platform distribusi mewajibkan pengungkapan penggunaan AI. Cek aturan terbaru platform tempat Anda merilis.
- **Konsistensi gaya** lebih penting daripada kecepatan. Aset campur aduk dari banyak sumber membuat game terasa murahan.
- Gunakan AI untuk mempercepat, bukan untuk menggantikan proses berpikir desain.

## 1.3 Skala proyek: tiga kategori realistis

|Kategori|Durasi pengerjaan (perkiraan)|Durasi bermain|Cocok untuk|
|---|---|---|---|
|Micro game|1 sampai 3 bulan|15 sampai 60 menit|Belajar, portofolio, game jam|
|Small indie|6 sampai 18 bulan|3 sampai 8 jam|Proyek komersial pertama|
|Mid indie|2 sampai 4 tahun|10 sampai 30 jam|Tim berpengalaman, 3+ orang|

Aturan praktis: **kebanyakan estimasi waktu pemula meleset 2 sampai 4 kali lipat.** Jika Anda berpikir proyek memakan 6 bulan, rencanakan 12 bulan.

## 1.4 Peran game designer di tim kecil

Di studio besar, game designer terbagi menjadi spesialis (system designer, level designer, narrative designer, economy designer). Di tim indie, Anda biasanya memakai **semua topi** sekaligus. Karena itu buku ini membahas semuanya, tetapi dengan prioritas pada yang paling berdampak pada gameplay.

## 1.5 Kesalahan umum

- Memulai dengan proyek raksasa (open world, MMO, game dengan crafting plus base building plus multiplayer).
- Menghabiskan berbulan-bulan membuat lore dan dunia sebelum ada satu mekanik yang menyenangkan.
- Menganggap grafis bagus menutupi gameplay yang membosankan.

## Latihan Bab 1

1. Tuliskan tiga game indie favorit Anda. Untuk masing-masing, tulis satu kalimat: "Yang membuat game ini berbeda adalah ...".
2. Tentukan kategori proyek Anda (micro, small, mid) dan alasannya.
3. Tuliskan berapa jam per minggu yang realistis bisa Anda alokasikan, lalu hitung estimasi kasar total jam yang tersedia dalam 12 bulan.

---

# Bab 2 - Fondasi yang Harus Kuat: Core Loop, Pillars, dan Kerangka MDA

## Tujuan belajar

- Mampu mendefinisikan core loop game Anda.
- Menyusun design pillars sebagai kompas keputusan.
- Memahami dan memakai kerangka MDA untuk menganalisis desain.

## 2.1 Apa itu game, secara desain

Definisi kerja yang berguna: **game adalah sistem aturan di mana pemain mengambil keputusan untuk mencapai tujuan, dan sistem memberi respons yang bermakna terhadap keputusan itu.**

Tiga kata kunci:

- **Keputusan** (decision): pemain memilih sesuatu.
- **Respons** (feedback): game menunjukkan akibat pilihan itu.
- **Bermakna** (meaningful): pilihan berpengaruh pada hasil, bukan dekorasi.

Jika pemain tidak punya keputusan menarik, itu bukan game yang baik, melainkan hanya interaksi.

## 2.2 Core loop

**Core loop** adalah siklus aksi yang diulang pemain paling sering. Biasanya berbentuk:

```
Aksi  ->  Hasil/Feedback  ->  Reward  ->  Keputusan baru  ->  Aksi
```

Contoh:

|Game (genre)|Core loop|
|---|---|
|Platformer|Lompat dan bergerak -> hindari bahaya -> capai checkpoint -> level berikutnya lebih sulit|
|Roguelike|Masuk ruangan -> bertarung -> pilih upgrade -> ruangan lebih sulit -> mati atau menang -> mulai lagi dengan pengetahuan baru|
|Farming sim|Tanam -> rawat -> panen -> jual -> beli benih/alat lebih baik|
|Metroidvania|Jelajah -> temukan hambatan -> dapat kemampuan baru -> buka area lama -> jelajah lagi|

### Uji kualitas core loop

Satu putaran core loop idealnya:

1. **Menyenangkan walau tanpa reward besar.** Jika bergerak dan menyerang saja sudah enak, fondasinya bagus.
2. **Punya keputusan.** Ada pilihan yang berbeda dengan konsekuensi berbeda.
3. **Cukup pendek untuk diulang**, cukup dalam untuk tidak membosankan.
4. **Bisa dijelaskan dalam satu kalimat.**

Tulis core loop Anda dalam satu kalimat. Jika tidak bisa, desain Anda belum jelas.

## 2.3 Design pillars

**Design pillars** adalah 3 sampai 5 pernyataan pendek tentang pengalaman inti game Anda. Pillars bertugas sebagai **filter keputusan**: setiap fitur harus mendukung minimal satu pillar.

Contoh pillars untuk game aksi 2D bertema reruntuhan kuno:

1. **Gerakan presisi**: kontrol ketat dan adil; kematian selalu terasa salah pemain, bukan salah game.
2. **Eksplorasi dengan rasa ingin tahu**: dunia menyembunyikan rahasia yang layak dicari.
3. **Pertarungan yang terbaca**: setiap musuh punya pola yang bisa dipelajari.

Contoh penggunaan: Anda tergoda menambah sistem memancing. Tanya: mendukung pillar yang mana? Jika tidak ada, tunda atau buang.

### Cara menulis pillar yang baik

- Spesifik dan bisa diuji ("pertarungan yang terbaca" lebih baik daripada "pertarungan seru").
- Bisa dipakai menolak ide.
- Jumlahnya sedikit. Lebih dari lima biasanya berarti belum memilih.

## 2.4 Kerangka MDA

MDA adalah kerangka klasik untuk memahami hubungan antara desainer dan pemain:

- **Mechanics (Mekanik)**: aturan dan komponen dasar, misalnya lompat, tembak, inventori, stamina.
- **Dynamics (Dinamika)**: perilaku yang muncul saat mekanik dijalankan bersama pemain, misalnya pemain mulai memakai taktik kiting (menyerang sambil mundur).
- **Aesthetics (Estetika)**: respons emosional pemain, misalnya tantangan, penemuan, ekspresi diri, kebersamaan, rasa penasaran.

Arah pandang berbeda:

```
Desainer:   Mechanics  ->  Dynamics  ->  Aesthetics
Pemain:     Aesthetics <-  Dynamics  <-  Mechanics
```

Desainer membangun dari mekanik, tetapi **pemain mengalami dari estetika**. Maka langkah praktisnya:

1. Tentukan dulu estetika yang Anda inginkan (misalnya "rasa tegang dan lega").
2. Cari dinamika yang menghasilkannya (misalnya "sumber daya terbatas dan musuh agresif").
3. Rancang mekanik yang memunculkan dinamika itu (misalnya "amunisi terbatas dan tidak ada regenerasi darah").

## 2.5 Kesalahan umum

- Menumpuk mekanik tanpa tahu estetika yang dituju.
- Core loop yang hanya menyenangkan karena reward, bukan karena aksinya.
- Pillars terlalu umum ("game harus seru").

## Latihan Bab 2

1. Tuliskan core loop game Anda dalam satu kalimat dan dalam diagram panah.
2. Tulis 3 design pillars. Untuk masing-masing, berikan satu ide fitur yang akan Anda tolak karena melanggarnya.
3. Ambil satu game favorit. Analisis dengan MDA: sebutkan 3 mekanik, 2 dinamika yang muncul, dan 2 estetika yang Anda rasakan.

---

# Bab 3 - Sistem Loop Berlapis: Micro, Core, Meta, dan Progression

## Tujuan belajar

- Memahami loop pada beberapa skala waktu.
- Merancang progression yang membuat pemain ingin lanjut.
- Menghindari progression palsu yang hanya memperpanjang durasi.

## 3.1 Tiga skala waktu

Game yang matang memiliki loop pada beberapa skala:

|Loop|Skala waktu|Contoh|
|---|---|---|
|Micro loop|Detik|Satu serangan: bidik, tembak, lihat hasil|
|Core loop|Menit|Satu pertarungan atau satu ruangan|
|Meta loop|Jam|Satu run, satu area, satu chapter, upgrade permanen|

Semua lapisan harus **saling mendukung**. Jika micro loop tidak enak, meta loop sebagus apa pun tidak menyelamatkan game.

## 3.2 Progression: empat jenis

1. **Progression kemampuan pemain (skill)**: pemain menjadi lebih mahir. Ini progression terbaik karena tidak butuh konten baru.
2. **Progression kekuatan karakter (power)**: level, stat, senjata.
3. **Progression kemampuan (ability/unlock)**: lompat ganda, dash, kunci baru yang membuka mekanik baru.
4. **Progression pengetahuan (knowledge)**: pemain tahu pola musuh, rahasia dunia, interaksi antar sistem.

Game yang kuat biasanya memakai kombinasi, dengan **skill dan knowledge sebagai fondasi**.

## 3.3 Prinsip progression yang sehat

- **Unlock yang mengubah cara bermain** lebih berharga daripada angka yang membesar. "Kini bisa dash menembus musuh" lebih menarik daripada "serangan +5%".
- **Beri tujuan jangka pendek, menengah, dan panjang.** Pemain perlu tahu apa yang dikejar dalam 5 menit, dalam 1 jam, dan sampai akhir game.
- **Hindari "grind palsu"**: mengulang aktivitas yang sama hanya untuk menaikkan angka, tanpa keputusan baru.
- **Perkenalkan elemen baru secara bertahap** agar pemain tidak kewalahan.

## 3.4 Contoh perancangan: roguelike 2D kecil

```
Micro loop : gerak, serang, hindar (kontrol dan feel)
Core loop  : bersihkan ruangan -> pilih 1 dari 3 upgrade
Meta loop  : selesai/mati -> dapat mata uang meta -> buka kelas karakter atau item baru
```

Pertanyaan desain:

- Apakah pilihan 1 dari 3 upgrade benar-benar membuat dilema (bukan satu opsi jelas terbaik)?
- Apakah meta upgrade membuka **variasi** (cara main baru) atau hanya **kekuatan** (membuat game gampang)?
- Apakah pemain yang mati tetap merasa maju (belajar atau membuka sesuatu)?

## 3.5 Kesalahan umum

- Meta progression yang terlalu kuat sehingga run pertama dan run ke-50 terasa seperti game berbeda tingkat kesulitan secara tidak adil.
- Terlalu banyak mata uang berbeda yang membingungkan.
- Menambah progression untuk menutupi core loop lemah.

## Latihan Bab 3

1. Gambar tiga lapis loop untuk game Anda.
2. Daftar semua progression dalam game Anda dan kelompokkan ke empat jenis di atas. Jenis mana yang paling dominan?
3. Tulis 3 unlock yang **mengubah cara bermain**, bukan hanya menambah angka.

---

# Bab 4 - Mekanik, Dinamika, dan Emergent Gameplay

## Tujuan belajar

- Merancang mekanik yang saling berinteraksi.
- Memahami emergent gameplay dan cara memancingnya.
- Mengukur kedalaman (depth) desain tanpa kompleksitas berlebihan.

## 4.1 Kompleksitas versus kedalaman

Dua istilah yang sering tertukar:

- **Kompleksitas (complexity)**: banyaknya aturan yang harus dipelajari.
- **Kedalaman (depth)**: banyaknya strategi menarik yang muncul dari aturan.

Target desain indie: **aturan sedikit, kedalaman besar**. Contoh klasik: catur punya aturan relatif sedikit, tetapi kedalamannya luar biasa.

## 4.2 Resep: sedikit mekanik, banyak interaksi

Jika Anda memiliki N mekanik independen, Anda mendapat N hal untuk dipelajari. Jika mekanik **saling berinteraksi**, jumlah kemungkinan meningkat tajam.

Contoh sistem sederhana dengan interaksi:

- Api membakar rumput.
- Air memadamkan api.
- Listrik menyambar pada air (menyetrum musuh di dalamnya).
- Angin menyebarkan api.

Empat aturan kecil, tetapi pemain bisa menemukan banyak taktik. Inilah **emergent gameplay**: perilaku menarik yang muncul dari interaksi aturan, tidak dirancang satu per satu.

### Aturan untuk sistem interaksi

1. **Konsisten.** Aturan berlaku sama di mana saja agar pemain bisa menarik kesimpulan.
2. **Terbaca.** Pemain bisa melihat penyebab dan akibat (visual dan audio jelas).
3. **Terbatas dan terkontrol.** Setiap aturan baru menambah kasus pengujian. Uji semua kombinasi penting.
4. **Aman dari exploit yang merusak.** Tentukan mana exploit yang dibiarkan (menyenangkan) dan mana yang ditutup (merusak game).

## 4.3 Verba (kata kerja) sebagai alat desain

Cara praktis merancang mekanik: daftar **verba** yang bisa dilakukan pemain.

Contoh: lompat, dash, serang, tangkis, lempar, tarik, bakar, sembunyi.

Lalu tanya untuk tiap verba:

- Apa **tantangan** yang menguji verba ini?
- Apa **verba lain** yang berinteraksi dengannya?
- Apakah verba ini tetap menarik setelah 5 jam?

Metode ini membantu menghindari fitur kosong. Sebuah verba yang tidak diuji oleh level atau musuh adalah verba yang sia-sia.

## 4.4 Risiko dan imbalan (risk and reward)

Keputusan menarik biasanya punya trade-off:

|Pilihan|Risiko|Imbalan|
|---|---|---|
|Serang musuh dari dekat|Mudah terkena balasan|Damage besar|
|Serang dari jauh|Aman|Damage kecil|
|Ambil jalur rahasia|Mungkin jebakan|Item langka|

Jika satu pilihan selalu lebih baik, itu disebut **dominant strategy** dan membuat pilihan lain tidak relevan. Tugas Anda adalah memastikan tidak ada dominant strategy yang terlalu jelas (kecuali memang disengaja untuk onboarding).

## 4.5 Mekanik yang "mengajar" dirinya sendiri

Mekanik bagus bisa dipahami tanpa teks panjang:

- Visual memberi petunjuk (platform yang retak terlihat rapuh).
- Konsekuensi ringan di awal (jatuh ke lubang yang aman).
- Pengulangan dengan variasi.

Kita bahas lebih dalam di Bab 8 dan 12.

## 4.6 Kesalahan umum

- Menambah mekanik baru setiap kali game terasa kurang, padahal masalahnya di eksekusi.
- Interaksi sistem yang tidak terbaca sehingga pemain merasa "dicurangi".
- Tidak menguji kombinasi mekanik.

## Latihan Bab 4

1. Daftar semua verba dalam game Anda. Coret yang tidak punya tantangan di level atau musuh.
2. Rancang tabel interaksi 4x4 untuk empat elemen atau mekanik dan tuliskan hasil tiap kombinasi.
3. Cari satu dominant strategy dalam game yang pernah Anda mainkan, lalu usulkan perubahan aturan untuk memperbaikinya.

---

# Bab 5 - Psikologi Pemain: Motivasi, Flow, dan Feedback

## Tujuan belajar

- Memahami apa yang memotivasi pemain.
- Menjaga pemain dalam kondisi flow.
- Merancang feedback yang jelas dan memuaskan.

## 5.1 Mengapa pemain bermain

Beberapa kerangka berguna:

### Self-Determination Theory (SDT)

Menurut teori ini, orang termotivasi secara intrinsik ketika tiga kebutuhan terpenuhi:

1. **Autonomy (otonomi)**: pemain merasa punya kendali dan pilihan.
2. **Competence (kompetensi)**: pemain merasa semakin mahir.
3. **Relatedness (keterhubungan)**: pemain merasa terhubung dengan sesuatu (karakter, dunia, orang lain).

Untuk game single-player berfokus gameplay, **autonomy dan competence** adalah dua yang paling bisa Anda kendalikan melalui desain.

### Tipe pemain (Bartle, dan variasinya)

Klasifikasi klasik: **Achiever** (mengejar target), **Explorer** (menjelajah), **Socializer** (berinteraksi), **Killer** (mendominasi). Anggap ini alat berpikir, bukan label kaku. Satu pemain bisa berganti gaya. Gunakan untuk bertanya: "Apakah game saya melayani minimal dua gaya?"

## 5.2 Flow

**Flow** adalah keadaan fokus penuh ketika tantangan seimbang dengan kemampuan.

```
Tantangan
   ^
   |        Cemas (terlalu sulit)
   |      /
   |    /   <- zona flow
   |  /
   |/   Bosan (terlalu mudah)
   +-----------------------------> Kemampuan
```

Karena kemampuan pemain naik seiring waktu, **tantangan juga harus naik** agar pemain tetap di zona flow. Tantangan yang naik tanpa jeda juga melelahkan, maka kita memakai **tempo** (naik, turun, naik) yang dibahas di Bab 8.

## 5.3 Feedback: empat sifat penting

Feedback yang baik adalah:

1. **Segera**: terjadi hampir saat aksi (idealnya dalam 100 milidetik).
2. **Jelas**: pemain paham apa yang terjadi dan kenapa.
3. **Proporsional**: aksi kecil, respons kecil; aksi besar, respons besar.
4. **Multi-sensorik**: visual, audio, dan (bila ada) getaran controller bekerja bersama.

Contoh serangan mengenai musuh: musuh berkedip putih singkat, terlempar sedikit, ada suara benturan, angka damage muncul, kamera bergetar tipis. Itu lima kanal feedback pada satu momen.

## 5.4 Kejelasan informasi (readability)

Pemain harus bisa menjawab tiga pertanyaan kapan saja:

1. Di mana saya dan apa yang terjadi?
2. Apa yang bisa saya lakukan sekarang?
3. Apa akibat dari pilihan saya?

Dalam pertarungan, kejelasan musuh yang akan menyerang (telegraphing, Bab 10) sangat menentukan rasa adil.

## 5.5 Rasa adil (fairness)

Pemain menerima kegagalan jika merasa **itu salah mereka dan bisa diperbaiki**. Pemain marah jika merasa:

- Dihukum untuk hal yang tidak bisa mereka lihat atau prediksi.
- Kontrol tidak responsif.
- Kehilangan progres besar tanpa alasan jelas.

Aturan emas: **kematian harus mengajarkan sesuatu.**

## 5.6 Rasa ingin tahu dan rasa penemuan

Rasa penasaran bisa dirancang melalui **celah informasi**: tunjukkan sebagian, sembunyikan sebagian. Contoh: pintu terkunci yang terlihat dari awal tetapi baru terbuka berjam-jam kemudian. Pemain mengingatnya dan merasa pintar saat kembali.

## 5.7 Kesalahan umum

- Menganggap semua pemain sama.
- Feedback yang terlalu berlebihan sehingga layar kacau dan sulit dibaca.
- Reward acak tanpa rasa kontrol yang justru membuat pemain merasa dimanipulasi.

## Latihan Bab 5

1. Pilih satu aksi utama dalam game Anda. Tuliskan 5 kanal feedback-nya (visual, audio, dan lainnya).
2. Mainkan sebuah game selama 20 menit dan catat tiga momen ketika Anda masuk flow dan tiga momen ketika Anda keluar. Apa penyebabnya?
3. Evaluasi game Anda terhadap tiga kebutuhan SDT. Mana yang paling lemah?

---

# Bab 6 - Game Feel dan Juice: Membuat Aksi Terasa Enak

## Tujuan belajar

- Memahami komponen game feel.
- Menerapkan teknik juice secara terukur.
- Mampu menyetel parameter kontrol (misalnya akselerasi, gravitasi) dengan sengaja.

## 6.1 Apa itu game feel

**Game feel** adalah sensasi taktil saat pemain mengendalikan sesuatu di layar. Tiga unsur menurut Steve Swink (dalam bukunya _Game Feel_):

1. **Input real-time**: kontrol langsung dan responsif.
2. **Ruang yang disimulasikan**: ada dunia dengan aturan fisik (walau sederhana).
3. **Polish**: efek yang menegaskan interaksi.

Game dengan konsep biasa tetapi feel luar biasa sering lebih disukai daripada game dengan konsep hebat tetapi feel kaku.

## 6.2 Parameter kontrol yang perlu Anda pahami

Untuk karakter yang bergerak, ada beberapa parameter inti:

|Parameter|Arti|Efek jika terlalu kecil|Efek jika terlalu besar|
|---|---|---|---|
|Kecepatan maksimum|Batas laju|Lambat, membosankan|Sulit dikendalikan|
|Akselerasi|Seberapa cepat mencapai laju maksimum|Terasa berat, licin|Terasa kaku, instan|
|Deselerasi (friksi)|Seberapa cepat berhenti|Seperti es, tergelincir|Terasa menempel|
|Gravitasi|Tarikan ke bawah|Mengambang|Berat dan cepat jatuh|
|Kekuatan lompat|Tinggi lompatan|Tidak bisa melewati rintangan|Terlalu mudah melompati semuanya|

### Contoh pseudocode gerak horizontal dengan akselerasi

```
// dijalankan setiap frame fisika
input = ambilInputHorizontal()           // -1, 0, atau 1

jika input != 0:
    kecepatan.x = mendekati(kecepatan.x, input * KECEPATAN_MAKS, AKSELERASI * delta)
selain itu:
    kecepatan.x = mendekati(kecepatan.x, 0, FRIKSI * delta)
```

Fungsi `mendekati(nilai, target, langkah)` menggeser nilai ke arah target tanpa melewatinya. Dengan mengubah `AKSELERASI` dan `FRIKSI`, Anda mengubah karakter gerakan dari licin menjadi presisi.

## 6.3 Teknik pemaaf (forgiveness) untuk platformer dan aksi

Teknik ini membuat kontrol terasa **adil dan responsif**. Banyak diterapkan tanpa disadari pemain:

- **Coyote time**: pemain tetap boleh melompat dalam jeda singkat (sekitar 0,08 sampai 0,15 detik) setelah meninggalkan tepi platform.
- **Jump buffering**: jika pemain menekan lompat sedikit sebelum mendarat, lompatan tetap dijalankan saat mendarat.
- **Variable jump height**: menahan tombol lebih lama menghasilkan lompatan lebih tinggi.
- **Corner correction**: jika kepala hampir mengenai sudut langit-langit, karakter digeser sedikit agar tidak tersangkut.
- **Input buffering untuk serangan**: serangan yang ditekan di akhir animasi sebelumnya tetap diproses.

Angka di atas hanya titik awal. Selalu uji dengan pemain nyata.

```
// coyote time dan jump buffer
jika sedangDiTanah:
    timerCoyote = WAKTU_COYOTE
selain itu:
    timerCoyote -= delta

jika tombolLompatDitekan:
    timerBuffer = WAKTU_BUFFER
selain itu:
    timerBuffer -= delta

jika timerBuffer > 0 dan timerCoyote > 0:
    lompat()
    timerBuffer = 0
    timerCoyote = 0
```

## 6.4 Juice: bumbu yang menegaskan aksi

**Juice** adalah efek tambahan yang tidak mengubah aturan game, tetapi membuat aksi terasa kuat. Daftar teknik:

|Teknik|Fungsi|
|---|---|
|Screen shake|Menegaskan benturan atau ledakan|
|Hit stop (hit pause/freeze frame)|Membekukan game 30 sampai 100 milidetik saat serangan kena, menambah bobot|
|Squash and stretch|Karakter memipih saat mendarat, memanjang saat lompat|
|Partikel|Debu saat mendarat, percikan saat tebasan|
|Flash|Objek berkedip putih saat terkena|
|Knockback|Musuh terdorong saat terkena|
|Variasi suara|Beberapa varian SFX agar tidak monoton|
|Easing animasi|Gerakan UI melambat atau menjepit alami, tidak linear|
|Kamera dinamis|Zoom ringan, look-ahead mengikuti arah gerak|

### Prinsip memakai juice

1. **Proporsional**: serangan ringan berefek ringan.
2. **Berfungsi, bukan hanya hiasan**: efek harus membantu pemain membaca situasi.
3. **Bisa dimatikan atau dikurangi**: sediakan opsi untuk screen shake dan efek berkedip (aksesibilitas, Bab 12).
4. **Jangan menutupi gameplay**: efek tidak boleh mengaburkan musuh atau proyektil.

## 6.5 Perbedaan 2D dan 3D untuk game feel

- **2D**: kontrol lebih mudah dibuat presisi karena hanya dua sumbu. Animasi frame-by-frame memberi kendali penuh atas timing (frame data serangan).
- **3D**: ada masalah tambahan: kamera, lock-on, kedalaman (sulit menilai jarak lompatan), dan animasi blending. Sediakan **bayangan karakter** di tanah dan indikator bidikan untuk membantu persepsi kedalaman.

## 6.6 Kesalahan umum

- Menambah juice sebelum kontrol dasar nyaman.
- Terlalu banyak screen shake sehingga mual.
- Mengubah parameter tanpa mencatat nilai sebelumnya. Simpan versi parameter agar bisa kembali.

## Latihan Bab 6

1. Buat prototipe karakter bergerak. Setel akselerasi dan friksi menjadi tiga karakter berbeda: licin, seimbang, kaku. Minta tiga orang mencoba dan memilih yang paling enak.
2. Terapkan coyote time dan jump buffer. Bandingkan rasa sebelum dan sesudah.
3. Tambahkan lima juice pada satu serangan dan lakukan A/B test (dengan dan tanpa juice) pada teman.

---

# Bab 7 - Desain Kontrol dan Kamera (2D dan 3D)

## Tujuan belajar

- Merancang skema kontrol yang nyaman dan konsisten.
- Memilih kamera yang sesuai gameplay.
- Menghindari masalah umum kamera 3D.

## 7.1 Prinsip desain kontrol

1. **Konsistensi**: tombol yang sama punya arti yang sama di semua situasi.
2. **Beban kognitif rendah**: pemain tidak perlu menghafal belasan kombinasi.
3. **Ergonomi**: perhatikan jari mana yang dipakai. Aksi yang sering dipakai harus di tombol yang mudah dijangkau.
4. **Dukungan beberapa perangkat**: keyboard dan mouse, gamepad, dan (bila relevan) layar sentuh. Rencanakan dari awal agar tidak perlu rombak besar.
5. **Remapping**: izinkan pemain mengubah tombol. Ini juga masuk aksesibilitas.

### Jumlah aksi per tombol

Aturan praktis: jangan membebani satu tombol dengan terlalu banyak fungsi bergantung konteks. Konteks yang tidak jelas membuat pemain salah menekan.

## 7.2 Kontrol langsung versus tidak langsung

- **Langsung**: tombol langsung menghasilkan aksi pada karakter (platformer, action).
- **Tidak langsung**: pemain memberi perintah, karakter atau unit yang menjalankan (strategi, simulasi).

Kontrol langsung menuntut responsivitas sangat tinggi (Bab 6). Kontrol tidak langsung menuntut antarmuka yang jelas (Bab 12).

## 7.3 Kamera 2D

Pilihan umum:

|Jenis|Contoh penggunaan|Catatan|
|---|---|---|
|Kamera tetap per layar|Platformer klasik, puzzle|Mudah, desain level berbasis "satu layar"|
|Mengikuti karakter|Platformer modern|Perlu smoothing dan batas area|
|Look-ahead|Aksi cepat|Kamera sedikit mendahului arah gerak|
|Top-down|RPG, roguelike|Perlu keputusan soal sudut (lurus atas atau miring)|

Tips: gunakan **dead zone** (area di tengah layar tempat karakter bergerak tanpa menggeser kamera) agar kamera tidak bergoyang terus.

## 7.4 Kamera 3D

|Jenis|Ciri|Tantangan|
|---|---|---|
|Orang pertama (FPS)|Imersif, bidikan natural|Rawan mual (motion sickness), persepsi lompat sulit|
|Orang ketiga di belakang bahu|Fleksibel untuk aksi|Kamera menembus dinding, terhalang objek|
|Isometrik atau fixed angle|Pandangan strategis|Objek bisa menutupi pemain|
|Top-down 3D|Jelas untuk pertarungan|Hati-hati tinggi rendah dunia|

### Masalah kamera 3D yang sering terjadi

1. **Kamera menembus geometri**: gunakan collision untuk kamera dan dorong kamera maju saat terhalang.
2. **Objek menutup pandangan**: buat objek menjadi transparan atau gunakan occlusion handling.
3. **Kecepatan putar kamera tidak nyaman**: sediakan pengaturan sensitivitas.
4. **Motion sickness**: sediakan opsi mengurangi head bob, FOV (field of view) yang dapat diatur, dan titik fokus tetap di layar.

## 7.5 Perbedaan aiming 2D dan 3D

- 2D: bidikan biasanya 8 arah atau bebas 360 derajat dengan mouse atau stik analog.
- 3D: ada bidikan bebas, aim assist, atau lock-on. Lock-on menyederhanakan pertarungan tetapi memerlukan kamera yang pintar dalam memilih target.

## 7.6 Kesalahan umum

- Memilih kamera berdasarkan gaya visual, bukan kebutuhan gameplay.
- Mengabaikan perbedaan sensitivitas keyboard dan gamepad.
- Tidak menguji di layar atau perangkat target.

## Latihan Bab 7

1. Gambar skema tombol untuk game Anda (gamepad dan keyboard). Hitung jumlah aksi per tombol.
2. Jika game Anda 3D, uji kamera di ruang sempit dan catat masalahnya.
3. Rancang dead zone dan smoothing kamera, lalu tes dengan tiga kecepatan gerak berbeda.

---

# Bab 8 - Level Design: Mengajar, Menantang, dan Mengatur Tempo

## Tujuan belajar

- Memahami level sebagai alat mengajar.
- Menyusun struktur level dan kurva intensitas.
- Menerapkan blockout dan metrik level di 2D dan 3D.

## 8.1 Level adalah guru yang diam

Level yang baik **mengajarkan mekanik tanpa teks panjang**. Pola pengajaran yang terbukti:

1. **Perkenalan (Introduce)**: mekanik ditemui di situasi aman. Contoh: ruang kosong dengan satu lubang kecil untuk belajar lompat.
2. **Pengembangan (Develop)**: mekanik dipakai dalam situasi sedikit berbeda dan sedikit lebih sulit.
3. **Kombinasi (Combine)**: mekanik digabung dengan mekanik lain.
4. **Ujian (Test)**: mekanik diuji penuh, sering sebagai tantangan atau bos.
5. **Variasi atau twist**: kejutan yang membalikkan harapan.

Pola ini sering disebut pendekatan "empat langkah" (perkenalan, pengembangan, twist, kesimpulan) atau variasinya. Intinya: **aman dulu, lalu menantang**.

## 8.2 Kurva intensitas dan tempo (pacing)

Jangan membuat tantangan naik lurus tanpa jeda. Gunakan gelombang:

```
Intensitas
   ^
   |            /\            /\/\
   |      /\   /  \     /\   /    \  <- klimaks
   |  /\ /  \_/    \___/  \_/
   | /
   +--------------------------------> Waktu
      aman  tegang  istirahat  tegang  puncak
```

Momen rendah (ruang aman, eksplorasi, toko, checkpoint) memberi pemain waktu bernapas dan mencerna pelajaran. Tanpanya, tantangan tinggi terasa melelahkan.

## 8.3 Struktur level

Beberapa struktur umum:

|Struktur|Ciri|Contoh|
|---|---|---|
|Linear|Satu jalur dari awal ke akhir|Platformer klasik|
|Linear dengan cabang|Jalur utama dengan jalan samping opsional|Banyak game aksi|
|Hub and spoke|Pusat dengan beberapa level terpisah|Game dengan area dunia|
|Interconnected (terhubung)|Area saling terhubung dengan pintas|Metroidvania|
|Open atau sandbox|Bebas jelajah|Game dunia terbuka (butuh sumber daya besar)|

Untuk indie, **linear dengan cabang** dan **hub and spoke** adalah titik awal paling realistis.

## 8.4 Tools desain level

### Blockout (greybox)

Bangun level kasar dari bentuk dasar (kotak, silinder) tanpa tekstur. Tujuannya menguji **gameplay dan skala** sebelum seni. Jika blockout sudah seru, seni akan memperkuat. Jika blockout membosankan, seni tidak akan menyelamatkannya.

### Metrik level

Tentukan ukuran yang konsisten dan catat dalam dokumen:

- **2D**: tinggi lompat maksimum, jarak lompat maksimum, lebar platform minimum, tinggi karakter dalam tile.
- **3D**: tinggi lompat, lebar koridor minimum, tinggi langit-langit, jarak pandang, lebar jalur.

Contoh: jika lompat maksimum karakter adalah 4 tile, jangan membuat celah 4 tile yang menuntut presisi sempurna sebagai tantangan awal. Gunakan **margin keamanan** (misalnya celah 3 tile untuk lompatan biasa, 4 tile untuk tantangan lanjutan).

### Pengarahan pemain (guiding)

Tanpa teks, arahkan pemain dengan:

- **Cahaya**: area terang menarik perhatian.
- **Warna kontras**: jalur penting berwarna berbeda.
- **Garis pandang**: tunjukkan tujuan dari jauh.
- **Komposisi dan landmark**: bangunan tinggi atau objek unik sebagai penanda.
- **Audio**: suara dari arah tujuan.
- **Gerakan**: objek bergerak menarik mata.

## 8.5 Encounter design: ruangan pertarungan

Satu ruangan pertarungan dapat dirancang dengan memperhatikan:

1. **Ruang**: ada tempat berlindung, ruang menghindar, ketinggian.
2. **Komposisi musuh**: kombinasi musuh yang saling melengkapi (satu jarak jauh, satu pendekar jarak dekat, satu penghalang).
3. **Gelombang**: satu atau beberapa fase untuk membangun tempo.
4. **Pembelajaran**: apakah ruangan menguji hal yang baru dipelajari?

## 8.6 Perbedaan khusus 2D dan 3D

**2D**

- Layar adalah kanvas utama. Atur komposisi agar bahaya terbaca.
- Layering (latar depan, tengah, belakang) memberi kedalaman visual tanpa membingungkan area bermain.
- Setiap piksel penting: pastikan platform yang bisa dipijak terbaca jelas dari dekorasi.

**3D**

- Kedalaman menambah kompleksitas navigasi. Pemain mudah tersesat.
- Gunakan **landmark** dan peta mini atau kompas bila perlu.
- Pengoptimalan performa (jumlah objek, occlusion culling, level of detail) memengaruhi desain ruang.
- Vertikalitas (ketinggian) memberi dimensi desain tambahan, tetapi juga membuat pengarahan lebih sulit.

## 8.7 Proses membuat satu level (langkah praktis)

1. Tulis **tujuan level** (apa yang diajarkan atau diuji, emosi yang dituju).
2. Buat **sketsa alur** (diagram sederhana, titik awal, titik tantangan, titik istirahat, titik akhir).
3. **Blockout** dan uji metrik.
4. **Playtest** blockout. Perbaiki masalah tempo dan keterbacaan.
5. Tambahkan **musuh dan objek**.
6. Playtest lagi.
7. Barulah **seni dan efek**.
8. Playtest final dan polish.

## 8.8 Kesalahan umum

- Level terlalu besar dan kosong.
- Tantangan sulit di awal tanpa pelajaran.
- Tidak ada checkpoint yang adil.
- Lompat buta (blind jump): pemain harus melompat tanpa melihat tujuan, lalu dihukum.

## Latihan Bab 8

1. Rancang satu level 5 menit yang mengajar satu mekanik baru dengan empat langkah (perkenalan, pengembangan, kombinasi, ujian). Gambar sketsa alurnya.
2. Gambar kurva intensitas level tersebut dan tandai ruang istirahatnya.
3. Buat blockout dan minta dua orang memainkannya tanpa penjelasan. Catat titik di mana mereka bingung.

---

# Bab 9 - Balancing, Ekonomi Game, dan Kurva Kesulitan

## Tujuan belajar

- Mengatur angka game secara sistematis dengan spreadsheet.
- Memahami kurva pertumbuhan (linear, eksponensial, dan sebagainya).
- Merancang ekonomi sumber daya yang sehat.
- Menyetel kesulitan yang adil.

## 9.1 Apa itu balancing

**Balancing** adalah proses menyesuaikan angka dan aturan agar pengalaman bermain adil, menantang, dan menyenangkan. Tujuan balancing bukan membuat semua opsi sama kuat, melainkan membuat **semua pilihan yang disengaja terasa layak dipilih**.

Jenis balance:

- **Balance kesulitan**: tantangan vs kemampuan pemain.
- **Balance antar pilihan**: senjata A vs senjata B.
- **Balance ekonomi**: pemasukan vs pengeluaran sumber daya.
- **Balance progression**: kecepatan pemain menjadi kuat.

## 9.2 Spreadsheet sebagai alat desain

Gunakan spreadsheet (Google Sheets atau Excel) untuk **memodelkan** angka sebelum dikodekan. Keuntungan: cepat diubah, bisa dibuat grafik, bisa dibagikan.

Struktur sederhana tabel musuh:

|Nama|HP|Damage|Kecepatan|Reward XP|Level muncul|
|---|---|---|---|---|---|
|Slime|20|3|1,0|5|1|
|Goblin|35|6|1,4|9|3|
|Ogre|120|18|0,7|40|6|

Dari tabel ini Anda bisa menghitung **time to kill** (TTK): berapa lama pemain membunuh musuh, dan **time to die** (TTD): berapa lama musuh membunuh pemain. Rasio keduanya menentukan rasa pertarungan.

```
TTK  = HP_musuh / DPS_pemain
TTD  = HP_pemain / DPS_musuh
```

Jika TTK jauh lebih besar dari TTD, pertarungan terasa mustahil. Jika sebaliknya, terasa trivial. Target tergantung genre dan tempo yang Anda inginkan.

## 9.3 Kurva pertumbuhan

Cara angka naik menentukan karakter progression.

|Kurva|Rumus contoh|Efek|
|---|---|---|
|Linear|`nilai = dasar + a * level`|Naik stabil, mudah diprediksi|
|Polinomial|`nilai = dasar * level^k` (k antara 1,5 dan 3)|Naik makin cepat secara moderat|
|Eksponensial|`nilai = dasar * (r ^ level)` (r > 1)|Naik sangat cepat, cocok untuk genre idle atau incremental|
|Logaritmik|`nilai = dasar * log(level)`|Naik cepat di awal lalu melandai|

Contoh XP yang dibutuhkan untuk naik level (polinomial):

```
xpDibutuhkan(level) = 100 * level ^ 1.5
```

|Level|XP dibutuhkan (kira-kira)|
|---|---|
|1|100|
|5|1.118|
|10|3.162|
|20|8.944|

Uji kurva di spreadsheet: berapa lama pemain mencapai level 10 pada kecepatan membunuh normal? Jika terlalu lama atau terlalu cepat, ubah eksponen.

## 9.4 Rumus damage dan pertahanan

Dua rumus populer:

**Pengurangan datar (flat)**

```
damageAkhir = maks(1, serangan - pertahanan)
```

Sederhana, tetapi pertahanan bisa membuat damage menjadi 1 atau 0 sehingga musuh atau pemain kebal. Hati-hati.

**Pengurangan proporsional**

```
damageAkhir = serangan * (100 / (100 + pertahanan))
```

Pertahanan memberi pengurangan yang makin melandai (diminishing returns), sehingga tidak ada kekebalan total. Contoh: pertahanan 100 mengurangi damage 50 persen, pertahanan 300 mengurangi 75 persen.

## 9.5 Diminishing returns dan soft cap

Agar satu stat tidak mendominasi, gunakan **diminishing returns**: setiap tambahan memberi manfaat lebih kecil. Alternatifnya **hard cap** (batas keras), misalnya cooldown reduction maksimum 40 persen.

## 9.6 Ekonomi game: sumber (source) dan penyerap (sink)

Dalam game dengan mata uang atau sumber daya (emas, material, energi), pikirkan:

- **Source**: dari mana sumber daya masuk (hadiah, drop musuh, hasil panen).
- **Sink**: ke mana sumber daya keluar (belanja, perbaikan, biaya upgrade).

Jika source terlalu besar dibanding sink, terjadi **inflasi**: pemain menumpuk sumber daya dan kehilangan makna keputusan belanja. Jika sink terlalu besar, pemain merasa miskin dan terjebak.

Cara menguji: buat model sederhana di spreadsheet untuk pemain "rata-rata" dalam satu jam: berapa penghasilan, berapa pengeluaran tipikal, berapa sisa.

### Kelangkaan yang bermakna

Sumber daya yang terbatas memaksa **pilihan**. Jika pemain bisa membeli semuanya, tidak ada dilema. Pastikan setiap mata uang punya keputusan menarik dalam pemakaiannya.

## 9.7 Kurva kesulitan dan opsi kesulitan

Pendekatan umum:

1. **Kesulitan tetap** dengan kurva dirancang matang (bagus untuk pengalaman terarah).
2. **Tingkat kesulitan pilihan pemain** (Mudah, Normal, Sulit).
3. **Dynamic difficulty adjustment (DDA)**: game menyesuaikan diri diam-diam. Bermanfaat, tetapi hati-hati: pemain yang merasa "dibantu diam-diam" kadang merasa ditipu. Pertimbangkan membuatnya transparan atau opsional.
4. **Assist mode**: opsi aksesibilitas seperti kebal, memperlambat game, melewati bagian. Mulai banyak dipakai dan sangat disukai pemain yang butuh.

Parameter yang bisa dipakai untuk kesulitan (selain sekadar HP musuh):

- Frekuensi serangan musuh.
- Jendela waktu untuk parry atau dodge.
- Jumlah checkpoint.
- Jumlah sumber daya yang dijatuhkan.

Mengubah **perilaku** lebih menyenangkan daripada hanya mengubah **angka**. Musuh dengan HP dua kali lipat terasa membosankan; musuh dengan pola serangan tambahan terasa menantang.

## 9.8 Proses balancing yang sehat

1. **Tetapkan target pengalaman** (misalnya "satu pertarungan biasa berlangsung 20 sampai 40 detik").
2. **Modelkan** di spreadsheet.
3. **Implementasi** dan **instrumentasi** (catat data: waktu per level, jumlah kematian, item yang dipilih).
4. **Playtest** dan lihat data.
5. **Ubah satu hal pada satu waktu** agar penyebab perubahan jelas.
6. **Catat** semua perubahan dan alasannya.

## 9.9 Kesalahan umum

- Mengubah banyak angka sekaligus.
- Mengandalkan intuisi tanpa data.
- Mengejar "balance sempurna" terlalu dini sebelum fitur stabil.
- Membuat satu opsi jelas terbaik tanpa disadari.

## Latihan Bab 9

1. Buat tabel di spreadsheet untuk 5 musuh. Hitung TTK dan TTD terhadap karakter awal dan karakter setelah 5 upgrade.
2. Rancang kurva XP dengan tiga eksponen berbeda dan buat grafiknya. Pilih satu dan jelaskan alasannya.
3. Gambarkan model source dan sink untuk satu mata uang dalam game Anda. Ada risiko inflasi atau kelangkaan berlebih?

---

# Bab 10 - Desain Musuh dan AI Gameplay

## Tujuan belajar

- Merancang musuh yang adil, menarik, dan mudah dibaca.
- Memahami teknik AI praktis: finite state machine dan behavior tree.
- Menyusun komposisi musuh dalam pertarungan.

## 10.1 Prinsip desain musuh

Musuh adalah **soal** yang harus dipecahkan pemain. Musuh yang baik:

1. **Punya identitas jelas**: dari siluet dan gerakan, pemain tahu perannya.
2. **Menguji keterampilan tertentu**: menghindar, menangkis, prioritas target, posisi.
3. **Terbaca (readable)**: pola serangan dapat dipelajari.
4. **Adil**: ada jendela waktu untuk bereaksi.

## 10.2 Telegraphing: memberi peringatan

**Telegraphing** adalah isyarat sebelum serangan agar pemain bisa bereaksi. Tiga fase serangan musuh:

```
Anticipation (persiapan)  ->  Action (serangan)  ->  Recovery (pemulihan)
```

- **Anticipation**: musuh menarik senjata, berkedip, mengeluarkan suara. Durasi harus cukup untuk bereaksi.
- **Action**: serangan nyata dengan hitbox aktif.
- **Recovery**: musuh rentan; di sinilah pemain punya jendela balasan.

Durasi anticipation tergantung tingkat kesulitan. Musuh dasar bisa 0,5 detik, musuh cepat 0,25 detik. Gunakan nilai itu sebagai titik awal dan uji.

## 10.3 Peran musuh (archetype)

Satu cara praktis merancang variasi:

|Peran|Fungsi dalam pertarungan|Contoh|
|---|---|---|
|Grunt (prajurit biasa)|Pengisi, dasar pertarungan|Prajurit pedang|
|Ranged (jarak jauh)|Menekan pemain agar bergerak|Pemanah|
|Tank|Menyerap damage, memaksa strategi|Prajurit perisai|
|Swarmer|Banyak dan lemah, menguji area attack|Kelelawar|
|Support|Memperkuat musuh lain, prioritas target|Penyembuh|
|Assassin|Menyerang cepat dari samping atau belakang|Ninja|
|Elite atau mini-boss|Ujian besar|Ksatria besar|

Kombinasi peran menciptakan teka-teki: misalnya pemanah di belakang tank memaksa pemain memilih prioritas.

## 10.4 Boss design

Boss idealnya **ujian akhir** dari mekanik yang diajarkan sepanjang area:

1. **Fase**: ubah pola di fase berikutnya (misalnya HP 66 persen dan 33 persen).
2. **Pola yang bisa dipelajari**: serangan berulang dalam urutan tertentu dengan variasi.
3. **Jendela balasan** yang jelas.
4. **Arena yang mendukung**: ruang, platform, atau elemen lingkungan.
5. **Tidak terlalu panjang**: kematian dekat akhir yang berulang terasa menyiksa. Pertimbangkan checkpoint dekat bos.

## 10.5 AI praktis: Finite State Machine (FSM)

FSM adalah cara sederhana mengatur perilaku: musuh berada pada satu **state** (keadaan) pada satu waktu, berpindah state berdasarkan **kondisi**.

```
Idle ----(lihat pemain)----> Kejar ----(dekat)----> Serang
  ^                            |                       |
  |                            v                       v
  +------(kehilangan jejak)--- Cari <----(pemain kabur)+
```

Contoh pseudocode:

```
state = IDLE

setiap frame:
    ganti state:
        IDLE:
            jika pemainTerlihat(): state = KEJAR
        KEJAR:
            bergerakMenujuPemain()
            jika jarak < JARAK_SERANG: state = SERANG
            jika pemainHilang(): state = CARI
        SERANG:
            jalankanSerangan()
            jika selesai: state = KEJAR
        CARI:
            periksaTerakhirDilihat()
            jika waktuHabis(): state = IDLE
```

Kelebihan: mudah dipahami dan di-debug. Kekurangan: bisa menjadi rumit jika state terlalu banyak.

## 10.6 Behavior Tree (untuk AI lebih kompleks)

Behavior tree menyusun keputusan dalam pohon dengan node seperti **Selector** (coba anak sampai ada yang berhasil), **Sequence** (jalankan anak berurutan sampai ada yang gagal), serta node kondisi dan aksi.

```
Selector
 |- Sequence (jika HP rendah)
 |    |- Kondisi: HP < 30 persen
 |    '- Aksi: kabur dan minum ramuan
 |- Sequence (jika pemain dekat)
 |    |- Kondisi: jarak < 2
 |    '- Aksi: serang jarak dekat
 '- Aksi: patroli
```

Gunakan FSM untuk musuh sederhana dan behavior tree jika perilaku bercabang banyak.

## 10.7 AI yang terasa cerdas tanpa benar-benar cerdas

Pemain menilai kecerdasan dari **perilaku yang terlihat**, bukan algoritma. Trik:

- Reaksi yang masuk akal (menoleh saat ada suara).
- Variasi (tidak mengulang pola persis sama setiap saat).
- Koordinasi sederhana (musuh tidak menumpuk di satu titik; ada "tiket serangan" yang membatasi berapa musuh menyerang bersamaan).
- Kesalahan yang disengaja agar pemain punya peluang.

**Attack token** (tiket serangan) sangat berguna: hanya N musuh yang boleh menyerang bersamaan, sisanya mengitari atau menunggu. Ini membuat pertarungan terasa adil dan terbaca.

## 10.8 Pathfinding

Untuk bergerak menuju target di dunia dengan rintangan, engine biasanya menyediakan **navigation mesh** (3D) atau **navigation grid atau tilemap navigation** (2D), memakai algoritma seperti A*. Anda cukup memahami konsep: dunia dibagi menjadi area yang bisa dilalui, lalu algoritma mencari jalur terpendek.

Aspek desain: hindari musuh yang tersangkut. Uji sudut tajam dan ruang sempit.

## 10.9 Kesalahan umum

- Musuh menyerang tanpa telegraph.
- Hitbox dan hurtbox tidak sesuai tampilan (pemain merasa terkena padahal tidak).
- Semua musuh mengejar dan menyerang bersamaan.
- Menaikkan kesulitan hanya lewat HP dan damage.

## Latihan Bab 10

1. Rancang tiga musuh dengan peran berbeda. Tulis pola anticipation, action, recovery masing-masing dengan durasi.
2. Gambar FSM untuk satu musuh Anda.
3. Rancang satu boss tiga fase dan tulis apa yang diuji pada tiap fase.

---

# Bab 11 - Narrative Design dan Lore yang Melayani Gameplay (Tanpa Voice Actor)

## Tujuan belajar

- Menempatkan cerita dan lore sebagai pendukung gameplay.
- Menguasai teknik bercerita tanpa voice actor.
- Menjaga keselarasan antara cerita dan mekanik (ludonarrative harmony).
- Menulis teks game yang singkat dan efektif.

## 11.1 Prinsip utama: cerita melayani gameplay

Dalam game yang fokus gameplay, cerita ibarat **bumbu**, bukan hidangan utama. Pertanyaan filter:

1. Apakah cerita ini membuat pemain **ingin** melakukan aksi berikutnya?
2. Apakah cerita ini **menjelaskan** mengapa aturan dunia berlaku?
3. Apakah pemain bisa **melewati** cerita tanpa kehilangan kemampuan bermain?

Jika sebuah adegan panjang menghentikan gameplay tanpa alasan kuat, pertimbangkan memendekkan, mengubah menjadi pengalaman bermain, atau membuatnya opsional.

## 11.2 Perbedaan story, lore, dan narrative

|Istilah|Arti|Contoh|
|---|---|---|
|Story (cerita)|Rangkaian peristiwa yang dialami pemain|Pahlawan mencari artefak untuk menyelamatkan desa|
|Lore|Latar belakang dunia: sejarah, mitologi, tokoh, hukum dunia|Mengapa kerajaan runtuh, siapa dewa-dewanya|
|Narrative (narasi)|Cara cerita dan lore disampaikan kepada pemain|Lewat teks, visual, level, item, musik|

Lore boleh sangat luas, tetapi **yang dibagikan ke pemain harus sedikit dan terpilih**. Pemain tidak butuh buku sejarah lengkap; mereka butuh potongan yang memancing rasa penasaran.

## 11.3 Mengapa tanpa voice actor itu baik untuk indie

- **Biaya dan waktu**: rekaman, penyuntingan, dan koordinasi aktor suara mahal dan memakan waktu.
- **Fleksibilitas revisi**: mengubah dialog hanya mengedit teks.
- **Lokalisasi lebih mudah**: cukup menerjemahkan teks, tidak merekam ulang di tiap bahasa.
- **Aksesibilitas**: teks dapat disesuaikan ukurannya dan dibaca oleh pemain dengan gangguan pendengaran.
- **Tidak ada ketidakcocokan suara** dengan imajinasi pemain.

Kekurangan yang perlu diimbangi: emosi harus dibangun lewat **teks yang kuat, musik, SFX, animasi, dan komposisi visual**.

## 11.4 Teknik bercerita tanpa voice actor

### 1. Environmental storytelling (bercerita lewat lingkungan)

Dunia sendiri menceritakan sesuatu:

- Ruangan berantakan dengan dua cangkir teh di meja dan satu kursi terbalik.
- Reruntuhan benteng dengan bekas pertempuran.
- Tulisan di dinding, poster, papan pengumuman.

Pemain menyimpulkan cerita sendiri. Ini kuat, murah, dan memberi rasa penemuan.

### 2. Teks dan dialog singkat

- Gunakan **kotak dialog** dengan teks yang pendek (satu sampai dua kalimat per kotak).
- Gunakan **gaya berbicara** yang berbeda per karakter (formal, kasar, puitis) agar identitas terasa tanpa suara.
- Sediakan **tombol lewati** dan **kecepatan teks** yang bisa diatur.
- Pertimbangkan **bunyi teks** (misalnya suara "blip" ringan per karakter, atau bunyi khas per tokoh) sebagai pengganti suara bicara, ala game klasik. Ini memberi karakter audio tanpa merekam aktor.

### 3. Deskripsi item dan codex

Setiap item bisa membawa potongan lore:

> Pedang Berkarat. Dahulu milik penjaga gerbang. Bilahnya masih menyimpan bekas api.

Dua kalimat sudah memunculkan pertanyaan: siapa penjaga itu, api apa. Item opsional ini memberi pemain Explorer sesuatu untuk dikumpulkan.

### 4. Catatan, surat, dan log yang ditemukan

Bentuk umum: catatan harian, rekaman teks, prasasti. Aturan praktis:

- Pendek (kurang dari 60 sampai 100 kata).
- Setiap catatan punya **satu ide**.
- Jangan memaksa pemain membaca untuk bisa maju. Jadikan bonus.

### 5. Visual dan desain karakter

Siluet, warna, pakaian, ekspresi, animasi idle. Contoh: tokoh yang selalu menunduk dan gerakannya lambat menyampaikan kelelahan tanpa kata.

### 6. Musik dan sound design

Tema musik untuk tokoh atau area (leitmotif), perubahan musik saat kondisi berubah, keheningan sebelum momen penting. Suara lingkungan menceritakan suasana (angin kosong, tetesan air di gua).

### 7. Cutscene tanpa dialog

Gunakan pantomim, kamera, musik, dan teks pendek. Alternatif: **cutscene dalam engine** yang singkat dan bisa dilewati. Batasi durasi.

### 8. Gameplay itu sendiri sebagai narasi

Mekanik yang menceritakan sesuatu: karakter yang melemah seiring waktu (mekanik menyampaikan penyakit), area yang berubah setelah peristiwa (level berubah). Ini bentuk bercerita terbaik untuk game karena **dialami**, bukan dibaca.

## 11.5 Ludonarrative harmony

**Ludonarrative harmony** artinya mekanik dan cerita saling mendukung. **Ludonarrative dissonance** artinya bertentangan.

Contoh disonansi: cerita mengatakan tokoh utama pasifis yang benci kekerasan, tetapi gameplay mengharuskan membantai ratusan musuh tanpa konsekuensi.

Cara menjaga harmoni:

- Pastikan **motivasi tokoh** sejalan dengan **aksi yang dilakukan pemain**.
- Jika mekanik inti adalah pertarungan, buat cerita yang menjelaskan mengapa bertarung (dunia penuh ancaman, tugas penjaga).
- Gunakan cerita untuk **memperkuat** mekanik: kekuatan baru diberi konteks naratif.

## 11.6 Struktur cerita sederhana untuk game indie

Struktur tiga babak yang disesuaikan untuk game:

1. **Babak 1 - Pengenalan**: dunia, tokoh, tujuan awal. Sekaligus tutorial mekanik dasar.
2. **Babak 2 - Pengembangan**: konflik meningkat, mekanik berkembang, kejutan (twist), kehilangan atau kekalahan sementara.
3. **Babak 3 - Klimaks dan resolusi**: ujian terakhir (boss), konsekuensi, penutup.

Untuk micro dan small indie, **cukup satu garis cerita utama** dengan beberapa karakter pendukung. Hindari alur bercabang besar kecuali itu inti game.

### Kerangka satu halaman

```
Premis      : satu kalimat tentang situasi awal
Tujuan      : apa yang dikejar tokoh utama
Hambatan    : siapa atau apa yang menghalangi
Twist       : informasi yang mengubah pemahaman pemain
Penutup     : konsekuensi dan perasaan akhir
Tema        : satu ide yang mengikat seluruh cerita
```

## 11.7 Menulis lore yang efektif

1. **Mulai dari pertanyaan, bukan jawaban.** Lore yang baik membuat pemain bertanya.
2. **Iceberg principle**: pemain hanya melihat 10 persen; Anda tahu 100 persen, tetapi tidak menyampaikan semuanya.
3. **Konsisten**: buat dokumen lore internal berisi fakta kunci agar tidak saling bertentangan.
4. **Kaitkan lore dengan gameplay**: tiap area punya identitas lore yang tercermin di musuh, visual, dan mekanik.
5. **Biarkan misteri**: tidak semua pertanyaan perlu dijawab.

### Dokumen lore internal (bible) ringkas

Isi minimal:

- Garis waktu singkat dunia.
- Faksi atau kelompok utama dan tujuan mereka.
- Daftar tokoh penting dan hubungan antar tokoh.
- Aturan dunia (sihir, teknologi, hukum alam).
- Daftar istilah khusus dan ejaan baku (untuk konsistensi).

## 11.8 Menulis teks game yang baik

- **Singkat dan konkret.** Hindari paragraf panjang di kotak dialog.
- **Suara tokoh** berbeda dalam pilihan kata dan panjang kalimat.
- **Tunjukkan, jangan ceritakan.** "Tangannya gemetar saat memegang surat itu" lebih kuat daripada "Dia gugup".
- **Hemat kata dalam UI**: label tombol dan tooltip harus langsung.
- **Hindari eksposisi berat (info dump).** Sebarkan informasi sepanjang permainan.
- **Gunakan variabel teks dengan hati-hati** (nama pemain, angka) dan uji untuk bahasa dengan tata bahasa berbeda saat lokalisasi.

### Tips lokalisasi sejak awal

- Simpan semua teks di **file terpisah** (misalnya tabel CSV atau JSON), bukan di dalam kode.
- Beri **ID unik** pada setiap string.
- Beri ruang tambahan di UI karena beberapa bahasa lebih panjang.
- Hindari menyisipkan teks ke dalam gambar.
- Jangan menggabung kalimat dari potongan-potongan karena urutan kata berbeda di tiap bahasa.

Contoh tabel teks:

|id|indonesia|english|
|---|---|---|
|ui.menu.start|Mulai|Start|
|npc.guard.greet|Berhenti. Gerbang ini ditutup.|Halt. This gate is closed.|

## 11.9 Pacing cerita dalam game fokus gameplay

Aturan ritme: **cerita muncul di jeda gameplay, bukan memotongnya.** Tempat alami untuk narasi:

- Ruang aman atau hub.
- Setelah mengalahkan boss.
- Saat memuat atau transisi level.
- Lewat objek opsional di sepanjang level.

Hindari cutscene panjang tepat setelah kematian berulang atau sebelum boss yang sering diulang. Sediakan tombol lewati.

## 11.10 Kesalahan umum

- Menghabiskan berbulan-bulan menulis lore sebelum gameplay jadi.
- Dialog panjang dan sulit dilewati.
- Cerita yang bertentangan dengan mekanik.
- Terlalu banyak nama dan istilah baru di awal sehingga membingungkan.
- Tidak menyiapkan teks untuk lokalisasi.

## Latihan Bab 11

1. Tulis kerangka cerita satu halaman untuk game Anda.
2. Tulis 5 deskripsi item (masing-masing maksimal 25 kata) yang menyiratkan lore tanpa menjelaskannya.
3. Rancang satu ruangan dengan environmental storytelling. Sketsa dan tulis 3 objek yang menceritakan sesuatu.
4. Periksa ludonarrative harmony game Anda: apakah tindakan utama pemain sejalan dengan motivasi tokoh?

---

# Bab 12 - UI/UX, Onboarding, dan Aksesibilitas

## Tujuan belajar

- Merancang antarmuka yang jelas dan tidak mengganggu.
- Menyusun onboarding (tutorial) yang efektif.
- Menerapkan aksesibilitas dasar yang berdampak besar.

## 12.1 Prinsip UI game

1. **Hirarki informasi**: hal terpenting paling menonjol (HP, tujuan, peringatan).
2. **Konsistensi**: ikon, warna, dan posisi elemen sama di seluruh game.
3. **Keterbacaan**: ukuran teks cukup besar, kontras memadai, font jelas.
4. **Minimalis kontekstual**: tampilkan informasi saat dibutuhkan; sembunyikan yang tidak relevan.
5. **Respons**: setiap aksi UI memberi feedback (suara klik, animasi hover).

### HUD (Heads-Up Display)

Jenis HUD:

- **Diegetic**: ada di dunia game (layar di dinding, meteran di senjata).
- **Non-diegetic**: overlay klasik (bar HP, minimap).
- **Spatial**: elemen UI menempel pada objek di dunia (bar HP di atas musuh).
- **Meta**: efek layar (layar merah saat HP rendah).

Pilih sesuai gaya. Diegetic lebih imersif tetapi kadang kurang jelas. Selalu cek keterbacaannya.

## 12.2 Onboarding: mengajar tanpa membosankan

Prinsip:

1. **Ajar lewat bermain, bukan membaca.** Beri pemain situasi aman untuk mencoba.
2. **Satu konsep pada satu waktu.**
3. **Ajar saat dibutuhkan (just-in-time).** Petunjuk tombol muncul saat pertama kali relevan.
4. **Beri ruang gagal yang aman.**
5. **Izinkan melewati** bagi pemain berpengalaman.
6. **Ulangi petunjuk penting** untuk yang lupa (misalnya lewat menu bantuan).

Contoh alur tutorial dalam level pertama:

```
1. Ruang kosong       -> pemain belajar bergerak
2. Lubang kecil       -> pemain belajar melompat
3. Musuh lemah diam   -> pemain belajar menyerang
4. Musuh lemah bergerak -> pemain belajar mengatur jarak
5. Hadiah di ujung    -> pemain merasa berhasil
```

Teks bantuan hanya muncul singkat ("Tekan A untuk melompat") dan hilang setelah dipakai.

## 12.3 Menu dan alur navigasi

- Menu utama sederhana: Mulai/Lanjutkan, Pengaturan, Keluar.
- Pengaturan lengkap: audio, grafis, kontrol, aksesibilitas, bahasa.
- Layar jeda (pause) yang cepat diakses dan bisa dilanjutkan dengan satu tombol.
- Simpan otomatis (autosave) dengan indikator jelas agar pemain tahu progres aman.

## 12.4 Aksesibilitas

Aksesibilitas bukan sekadar kewajiban moral; ia memperluas jumlah pemain dan sering menaikkan kenyamanan semua orang. Fitur dasar yang berdampak besar:

|Area|Fitur|
|---|---|
|Visual|Ukuran teks dapat diubah, mode buta warna atau tidak bergantung warna saja, kontras tinggi, opsi mengurangi efek berkedip dan screen shake|
|Audio|Subtitle atau teks untuk bunyi penting, kontrol volume terpisah (musik, SFX, UI), indikator visual untuk bunyi penting|
|Kontrol|Remapping tombol, opsi tahan atau tekan (toggle), sensitivitas bisa diatur, dukungan satu tangan bila memungkinkan|
|Kognitif|Tutorial dapat diulang, tujuan jelas dan bisa dilihat ulang, opsi kecepatan game, assist mode|
|Fotosensitivitas|Hindari kedipan cepat berkontras tinggi, beri peringatan dan opsi|

Karena game Anda **tanpa voice actor**, semua informasi dialog sudah berbasis teks, sehingga satu hambatan aksesibilitas besar sudah terhindari. Pastikan **bunyi penting** (misalnya peringatan musuh di luar layar) juga punya isyarat visual.

### Jangan hanya mengandalkan warna

Contoh: musuh yang akan menyerang ditandai merah. Pemain dengan buta warna merah-hijau mungkin sulit membedakan. Tambahkan **bentuk** atau **ikon** selain warna.

## 12.5 Kesalahan umum

- Tutorial berupa dinding teks.
- HUD terlalu penuh.
- Mengabaikan opsi dasar (volume, remap) hingga akhir proyek.
- Teks kecil yang tidak terbaca di layar kecil atau handheld.

## Latihan Bab 12

1. Rancang alur onboarding 5 langkah untuk game Anda dan tulis apa yang diajarkan pada tiap langkah.
2. Buat checklist aksesibilitas untuk game Anda dan tandai mana yang akan dimasukkan di versi pertama.
3. Minta teman yang belum pernah bermain mencoba menu dan tutorial tanpa bantuan. Catat semua titik bingung.

---

# Bab 13 - Prototyping, Playtesting, dan Iterasi

## Tujuan belajar

- Membuat prototipe cepat untuk menguji ide.
- Menjalankan playtest yang menghasilkan data berguna.
- Mengelola iterasi tanpa tersesat.

## 13.1 Prototipe: tujuan dan jenis

**Prototipe** adalah versi cepat dan kasar untuk menjawab **satu pertanyaan desain**. Contoh pertanyaan: "Apakah mekanik dash ini seru?" atau "Apakah pemain paham cara memakai kait?"

Jenis prototipe:

|Jenis|Kegunaan|Cara|
|---|---|---|
|Kertas atau papan|Menguji aturan dan keputusan|Kartu, dadu, token|
|Greybox digital|Menguji kontrol dan level|Bentuk sederhana di engine|
|Vertical slice|Menguji kualitas akhir satu bagian|Satu level lengkap dengan seni, audio, UI|
|Horizontal prototype|Menguji cakupan fitur|Semua fitur ada tetapi dangkal|

Aturan: **buat sekecil dan secepat mungkin untuk menjawab pertanyaan.** Kualitas kode prototipe boleh jelek; yang penting jawaban cepat. Namun jangan menjadikan prototipe sebagai fondasi game final tanpa dirapikan.

## 13.2 Prototipe kertas

Untuk game dengan sistem (kartu, ekonomi, strategi), prototipe kertas sangat murah. Contoh: uji roguelike deck-builder dengan kartu kertas sebelum menulis kode. Anda bisa menemukan masalah keseimbangan dalam beberapa jam.

## 13.3 Playtesting

**Playtest** adalah mengamati orang lain memainkan game Anda. Aturan emas:

1. **Diam dan amati.** Jangan menjelaskan atau membela game saat mereka bermain.
2. **Lihat apa yang dilakukan**, bukan hanya apa yang dikatakan. Perilaku lebih jujur daripada opini.
3. **Gunakan pemain baru** yang belum pernah melihat game Anda.
4. **Rekam** (dengan izin): layar, dan bila memungkinkan wajah atau suara.
5. **Catat titik** di mana pemain bingung, frustrasi, tertawa, atau berhenti.

### Pertanyaan setelah bermain

- "Apa yang Anda pikir tujuan game ini?"
- "Bagian mana yang paling menyenangkan? Paling membosankan?"
- "Apakah ada saat Anda tidak tahu harus berbuat apa?"
- "Apa yang Anda ingin lakukan tetapi tidak bisa?"

Hindari pertanyaan pengarah seperti "Bukankah level ini seru?"

### Berapa banyak penguji

Untuk menemukan masalah besar (kebingungan, bug fatal), **5 sampai 8 penguji** pertama biasanya sudah memunculkan sebagian besar masalah. Ulangi setelah perbaikan dengan penguji baru.

## 13.4 Mengukur dengan data (telemetri sederhana)

Bila memungkinkan, catat data anonim di build uji (dengan persetujuan pemain):

- Waktu menyelesaikan tiap level.
- Jumlah kematian per lokasi (peta panas kematian).
- Pilihan upgrade yang diambil.
- Titik pemain berhenti bermain.

Data membantu menemukan **di mana**, playtest membantu memahami **kenapa**.

## 13.5 Memilah masukan

Tidak semua masukan harus diikuti. Cara memilah:

1. **Pisahkan masalah dari solusi.** Pemain bilang "tambahkan peta". Masalah sebenarnya: "tersesat". Solusinya mungkin landmark lebih jelas.
2. **Cari pola.** Satu orang mengatakan sesuatu = anekdot; lima orang mengatakan hal serupa = masalah.
3. **Cek terhadap design pillars.** Masukan yang bertentangan dengan visi bisa ditolak dengan sopan.
4. **Prioritaskan** berdasarkan dampak dan biaya.

Matriks prioritas sederhana:

||Biaya rendah|Biaya tinggi|
|---|---|---|
|Dampak tinggi|Kerjakan sekarang|Rencanakan|
|Dampak rendah|Kerjakan jika sempat|Abaikan|

## 13.6 Siklus iterasi

```
Hipotesis -> Bangun -> Uji -> Pelajari -> Ubah -> (ulang)
```

Setiap siklus tulis catatan singkat: apa yang diuji, apa hasilnya, apa keputusannya. Catatan ini mencegah Anda mengulang kesalahan yang sama dan membantu menjelaskan keputusan kepada anggota tim.

## 13.7 Kapan membuang ide

Tanda sebuah fitur sebaiknya dibuang atau dirombak:

- Setelah beberapa iterasi tetap tidak menyenangkan.
- Membutuhkan banyak penjelasan tetapi tidak memberi banyak nilai.
- Tidak mendukung design pillars.
- Biayanya jauh lebih besar dari manfaatnya.

Menghapus fitur adalah keterampilan desain, bukan kegagalan. Ingat prinsip: **kill your darlings** (relakan ide kesayangan yang tidak berhasil).

## 13.8 Kesalahan umum

- Memperbaiki masalah yang diceritakan pemain tanpa memahami akar masalah.
- Hanya menguji dengan teman dekat yang sungkan jujur.
- Menunggu terlalu lama sebelum playtest pertama.
- Mengubah terlalu banyak hal antar playtest sehingga tidak tahu perubahan mana yang bekerja.

## Latihan Bab 13

1. Tulis satu pertanyaan desain dan rancang prototipe paling murah untuk menjawabnya.
2. Siapkan lembar observasi playtest berisi kolom: waktu, apa yang pemain lakukan, apa yang pemain katakan, interpretasi saya.
3. Lakukan playtest dengan 3 orang dan ringkas tiga masalah teratas serta solusi usulan.

---

# Bab 14 - Dokumentasi Desain yang Ringan tapi Berguna

## Tujuan belajar

- Menulis dokumen desain yang benar-benar dipakai.
- Memakai format satu halaman dan GDD hidup.
- Menyimpan keputusan dan catatan perubahan.

## 14.1 Mengapa mendokumentasikan

Dokumentasi:

- Memaksa Anda berpikir jernih.
- Menjaga konsistensi antar anggota tim (dan Anda di masa depan, yang akan lupa).
- Memudahkan pencarian pendanaan atau penerbit jika suatu saat diperlukan.

Namun dokumen tebal yang tak pernah dibaca adalah pemborosan. Prinsipnya: **ringan, singkat, hidup (selalu diperbarui).**

## 14.2 Satu halaman desain (One-Page Design)

Berisi:

```
Judul game        :
Genre dan platform:
Premis (1 kalimat):
Core loop         :
Design pillars    : (3 sampai 5)
Fitur utama       : (5 sampai 7)
Target pemain     :
Gaya visual dan audio:
Ruang lingkup (scope): ukuran proyek dan durasi bermain
Pembeda (hook)    : apa yang membuat game ini unik
```

Jika Anda tidak dapat mengisi satu halaman, ide Anda belum matang.

## 14.3 Game Design Document (GDD) yang hidup

GDD bukan kitab suci, tetapi **dokumen kerja**. Struktur yang disarankan:

1. **Gambaran umum**: premis, pillars, target pemain.
2. **Gameplay**: core loop, mekanik, kontrol, kamera.
3. **Progression**: unlock, kurva kesulitan, ekonomi.
4. **Konten**: daftar level, musuh, item (tabel).
5. **Cerita dan lore ringkas**: kerangka, tokoh, daftar lore penting.
6. **UI dan UX**: layar, alur menu, HUD.
7. **Seni dan audio**: gaya, referensi, daftar kebutuhan aset.
8. **Teknis**: platform, spesifikasi minimum, catatan engine.
9. **Jadwal dan milestone**.
10. **Risiko dan keputusan terbuka**.

### Tips

- Gunakan **tabel** dan **diagram** daripada paragraf panjang.
- Simpan di tempat yang mudah dicari (wiki, dokumen bersama).
- Beri **tanggal dan versi** pada perubahan penting.
- Tandai bagian yang **belum diputuskan** secara eksplisit.

## 14.4 Log keputusan (decision log)

Catat keputusan penting dengan format singkat:

```
Tanggal   : 2026-11-03
Keputusan : Dash tidak dapat dipakai di udara lebih dari sekali sebelum mendarat
Alasan    : Playtest menunjukkan dash tak terbatas melewati hampir semua tantangan
Alternatif yang ditolak: cooldown waktu (terasa tidak intuitif)
```

Log ini menghemat waktu saat Anda lupa kenapa sesuatu diputuskan.

## 14.5 Backlog dan penugasan

Pisahkan **ide** (daftar keinginan) dari **tugas** (pekerjaan yang dijadwalkan). Gunakan papan sederhana (Kanban): Rencana, Dikerjakan, Diuji, Selesai. Tentukan prioritas berdasarkan:

1. Apakah mendukung pillars?
2. Apakah menghambat pekerjaan lain?
3. Berapa biaya (waktu)?

## 14.6 Kesalahan umum

- GDD 100 halaman di awal yang tidak pernah diperbarui.
- Tidak mencatat perubahan keputusan.
- Mencampur ide liar dengan rencana kerja.

## Latihan Bab 14

1. Isi template satu halaman untuk game Anda (Lampiran B).
2. Tulis tiga entri decision log dari keputusan desain yang pernah Anda ambil.
3. Buat papan Kanban sederhana untuk dua minggu ke depan.

---

# Bab 15 - Manajemen Scope dan Produksi untuk Tim Kecil

## Tujuan belajar

- Memperkirakan dan mengendalikan ruang lingkup proyek.
- Membagi pekerjaan menjadi milestone yang realistis.
- Menghindari feature creep dan kelelahan (burnout).

## 15.1 Scope: musuh utama indie

**Scope** adalah seluruh pekerjaan yang dibutuhkan untuk menyelesaikan game. **Scope creep** adalah pertumbuhan scope tanpa kendali: "tambah satu fitur lagi" berkali-kali.

Cara mengendalikan:

1. **Tetapkan batas** di awal (durasi bermain, jumlah level, jumlah musuh).
2. **Pakai pillars** sebagai filter.
3. **Pisahkan** fitur menjadi: **Wajib** (must have), **Sebaiknya** (should have), **Bagus jika ada** (nice to have).
4. **Siapkan cut list** (daftar fitur yang akan dipotong jika waktu mepet), dan urutkan dari yang paling mudah dipotong.

## 15.2 Menghitung biaya sebuah fitur

Satu fitur bukan hanya kode. Hitung juga:

- Desain dan dokumentasi
- Kode dan integrasi
- Seni dan animasi
- Audio
- UI
- Pengujian dan perbaikan bug
- Lokalisasi

Contoh "sistem memancing" tampak murah (satu minigame), tetapi butuh: aset ikan, UI, animasi, suara, ekonomi hasil, tutorial, dan pengujian. Total bisa berminggu-minggu.

Aturan praktis: **kalikan estimasi pertama Anda dengan 2 sampai 3**, lalu tambahkan waktu untuk polish.

## 15.3 Tahap produksi

|Tahap|Tujuan|Output|
|---|---|---|
|Konsep|Menentukan ide dan pillars|Satu halaman desain|
|Prototipe|Membuktikan core loop menyenangkan|Prototipe greybox|
|Vertical slice|Membuktikan kualitas akhir dan pipeline|Satu level lengkap|
|Produksi|Membuat seluruh konten|Konten level, musuh, UI|
|Alpha|Semua fitur ada tetapi kasar|Build lengkap fitur|
|Beta|Fokus perbaikan bug dan polish|Build hampir final|
|Rilis|Peluncuran|Game final|
|Pasca rilis|Pembaruan, perbaikan|Patch|

**Vertical slice** adalah titik kritis: jika satu level lengkap saja belum menyenangkan, memperbanyak level hanya memperbanyak masalah.

## 15.4 Milestone dan buffer

- Bagi proyek menjadi milestone 4 sampai 8 minggu.
- Setiap milestone punya hasil yang **bisa dimainkan**.
- Sisihkan **buffer waktu** (sekitar 20 sampai 30 persen) untuk hal tak terduga.
- Evaluasi di akhir milestone: apakah jadwal masih realistis? Apa yang harus dipotong?

## 15.5 Aset dan pipeline

Untuk tim kecil, strategi aset yang realistis:

- **Gaya visual yang efisien**: pixel art, low-poly, stylized, atau gaya dengan palet terbatas. Pilih yang bisa Anda hasilkan konsisten.
- **Modular**: gunakan tile atau modul yang dapat dirakit ulang menjadi banyak variasi.
- **Gunakan ulang** aset dengan variasi (recolor, skala, kombinasi).
- **Aset berlisensi** harus dicek lisensinya (komersial atau tidak, atribusi).
- **Konsistensi** lebih penting daripada kualitas individual aset.

Jika memakai tool AI untuk aset sementara atau final, perhatikan konsistensi gaya, lisensi, dan aturan platform (Bab 1).

## 15.6 Kontrol versi dan cadangan

Pakai **version control** (misalnya Git dengan layanan hosting). Aturan dasar:

- Commit kecil dan sering dengan pesan jelas.
- Cadangan di lebih dari satu tempat.
- Untuk aset besar (seni, audio), gunakan mekanisme yang cocok (misalnya Git LFS atau tool khusus).
- Bagi branch untuk fitur eksperimen agar build utama tetap stabil.

## 15.7 Menjaga diri: burnout dan motivasi

- Tetapkan jam kerja realistis.
- Rayakan milestone kecil.
- Tampilkan progres ke orang lain secara berkala (media sosial, komunitas) agar termotivasi, tanpa berlebihan.
- Istirahat adalah bagian dari produksi.
- Jika proyek terasa mati, kembali ke core loop dan ingat kenapa Anda memulai.

## 15.8 Kesalahan umum

- Tidak punya definisi "selesai".
- Polish terlalu awal pada konten yang mungkin dibuang.
- Mengabaikan bug hingga akhir.
- Mengerjakan semua hal sekaligus tanpa prioritas.

## Latihan Bab 15

1. Buat daftar fitur dan kelompokkan Wajib, Sebaiknya, Bagus jika ada.
2. Buat cut list dengan urutan pemotongan.
3. Rancang 4 milestone untuk proyek Anda dengan hasil yang bisa dimainkan di tiap milestone.

---

# Bab 16 - Memilih 2D atau 3D, dan Studi Kasus Genre

## Tujuan belajar

- Memutuskan 2D atau 3D berdasarkan kebutuhan, bukan tren.
- Memahami konsekuensi desain dan produksi dari tiap pilihan.
- Menganalisis pola desain pada beberapa genre populer.

## 16.1 Perbandingan 2D dan 3D untuk tim kecil

|Aspek|2D|3D|
|---|---|---|
|Biaya aset|Umumnya lebih terkendali (sprite, tilemap)|Model, rigging, animasi, tekstur, material: biasanya lebih berat|
|Animasi|Frame-by-frame atau skeletal 2D|Skeletal, blending, retargeting|
|Kamera|Sederhana|Kompleks (collision, occlusion, lock-on)|
|Level design|Layar adalah kanvas, mudah dibaca|Navigasi dan vertikalitas lebih kompleks|
|Performa|Umumnya ringan|Perlu optimasi (LOD, culling, bayangan)|
|Imersi|Gaya dan seni bisa sangat ekspresif|Ruang dan kedalaman alami|
|Pengujian|Lebih sedikit kasus tepi|Banyak kasus tepi (tersangkut, jatuh dari dunia)|
|Risiko scope|Sedang|Lebih tinggi|

**Rekomendasi untuk proyek pertama komersial:** 2D atau 3D sederhana dengan gaya stylized dan jumlah aset terbatas. 3D bisa dikerjakan solo, tetapi **pilih gaya dan genre yang mengurangi kebutuhan animasi kompleks**.

### Variasi di antara keduanya

- **2.5D**: dunia 3D dengan gameplay bidang 2D, atau sprite 2D di dunia 3D.
- **Low-poly 3D**: model sederhana, tekstur minimalis.
- **Pixel art 3D (hybrid)**: model 3D dengan filter pikselasi.

## 16.2 Kriteria memilih

Tanyakan:

1. Apakah gameplay inti **membutuhkan** dimensi ketiga? (Misalnya eksplorasi vertikal, tembak orang pertama, parkour.)
2. Apakah saya dan tim punya **kemampuan seni** untuk menghasilkan aset konsisten pada dimensi itu?
3. Berapa **waktu** yang tersedia?
4. Platform target dan **performa** perangkat target.
5. Referensi: game sukses sejenis dikerjakan oleh tim sebesar apa?

## 16.3 Studi kasus pola genre

Analisis berikut adalah pola desain umum, bukan resep baku.

### Platformer (2D, kadang 3D)

- **Inti**: kontrol presisi dan level yang mengajar.
- **Fokus desain**: game feel (Bab 6), metrik level (Bab 8), coyote time dan buffering.
- **Risiko**: level desain butuh banyak iterasi.
- **Cerita**: lewat environmental storytelling dan teks singkat.

### Roguelike atau roguelite

- **Inti**: variasi tiap run, keputusan upgrade, kematian sebagai pembelajaran.
- **Fokus desain**: sistem modular (item yang saling berinteraksi), balancing (Bab 9), meta progression (Bab 3).
- **Risiko**: konten acak bisa terasa hambar; kombinasi item butuh banyak pengujian.
- **Cerita**: fragmen lore yang terbuka seiring run, cocok untuk tanpa voice actor.

### Metroidvania

- **Inti**: eksplorasi dan kemampuan yang membuka area lama.
- **Fokus desain**: peta terhubung, gerbang kemampuan (ability gating), peta dan navigasi.
- **Risiko**: desain dunia kompleks dan rawan "pemain buntu".
- **Cerita**: lore tersebar, cocok untuk Explorer.

### Action RPG atau action-adventure

- **Inti**: pertarungan, progression karakter, eksplorasi.
- **Fokus desain**: sistem combat (hitbox, telegraph, stamina), build karakter.
- **Risiko**: scope cepat membengkak (banyak sistem sekaligus).
- **Cerita**: dibangun lewat dunia dan tokoh; batasi dialog panjang.

### Puzzle dan puzzle-platformer

- **Inti**: aturan sederhana, kombinasi cerdas.
- **Fokus desain**: kurva pengajaran, momen "aha", validasi solusi (tidak ada jalan pintas yang merusak).
- **Risiko**: butuh banyak level dan pengujian solusi.
- **Cerita**: minimal, sering lewat suasana.

### Survival atau crafting (skala kecil)

- **Inti**: manajemen sumber daya, bertahan, membangun.
- **Fokus desain**: ekonomi (source dan sink), tempo siang malam, ancaman bertahap.
- **Risiko**: sistem banyak yang saling bergantung; sulit di-balance.
- **Cerita**: sering lewat catatan dan lingkungan.

### Strategi atau taktik (turn-based kecil)

- **Inti**: keputusan berbobot dengan informasi jelas.
- **Fokus desain**: keterbacaan, UI, AI lawan.
- **Risiko**: AI dan balancing membutuhkan banyak iterasi.
- **Cerita**: bisa lewat kampanye ringan.

### Farming atau life sim ringan

- **Inti**: rutinitas yang menenangkan dan progres jangka panjang.
- **Fokus desain**: loop harian, ekonomi, kemajuan terasa.
- **Risiko**: konten dalam jumlah besar dibutuhkan agar tidak repetitif.
- **Cerita**: hubungan dengan tokoh, teks dialog (tanpa suara) sangat cocok.

## 16.4 Menggabungkan genre dengan hati-hati

Menggabung genre (misalnya roguelike plus deck-builder) menciptakan pembeda, tetapi **menggandakan sistem yang harus Anda desain dan seimbangkan**. Mulai dari satu genre sebagai fondasi dan tambahkan satu "twist" yang jelas.

## 16.5 Kesalahan umum

- Memilih 3D karena terlihat lebih "profesional", tanpa kemampuan atau waktu.
- Menjiplak genre tanpa memahami apa yang membuat inti genre itu berhasil.
- Menggabungkan terlalu banyak genre.

## Latihan Bab 16

1. Isi tabel keputusan 2D vs 3D untuk proyek Anda dengan skor 1 sampai 5 per aspek, lalu tentukan pilihan.
2. Pilih satu genre dan tulis tiga "aturan emas" genre itu beserta satu twist unik Anda.
3. Analisis satu game indie dari genre pilihan Anda: sebutkan core loop, pillars (tebakan Anda), dan satu keputusan desain yang cerdas.

---

# Bab 17 - Dari Desain ke Rilis: Demo, Wishlist, dan Monetisasi dari Sisi Desain

## Tujuan belajar

- Memahami bagaimana keputusan desain memengaruhi pemasaran dan penjualan.
- Merancang demo dan trailer yang efektif.
- Mempertimbangkan model monetisasi etis.

Catatan: aturan platform, persentase bagi hasil, dan fitur toko berubah seiring waktu. Cek dokumentasi resmi platform terbaru sebelum mengambil keputusan.

## 17.1 Desain yang "bisa dijual"

Game dengan gameplay bagus tetap perlu **mudah dikomunikasikan**. Uji:

1. **Hook dalam satu kalimat**: "Platformer di mana waktu mundur setiap kali Anda mati."
2. **Terlihat menarik dalam 5 detik trailer atau gambar**: aksi inti harus terlihat jelas.
3. **Pembeda**: apa yang tidak dimiliki game sejenis?
4. **Target pemain jelas**: siapa yang menyukai game seperti ini?

## 17.2 Demo

Demo adalah alat pemasaran dan alat playtest sekaligus. Prinsip:

- **Mulai bagus cepat**: 5 menit pertama harus memikat.
- **Tunjukkan core loop**, bukan hanya tutorial.
- **Beri kesan ada lebih banyak** (misalnya teaser konten lanjutan).
- **Ajak pemain melakukan tindakan** (misalnya masukkan ke wishlist) di akhir demo.
- **Jaga demo tetap stabil**: bug fatal di demo sangat merugikan.
- Kumpulkan umpan balik dari demo untuk memperbaiki game final.

## 17.3 Trailer dan materi promosi

- Tunjukkan **gameplay sejak detik-detik awal**, bukan hanya logo.
- Tampilkan variasi aksi, kejutan, dan pembeda.
- Hindari terlalu banyak teks.
- Sertakan **GIF atau klip pendek** yang bisa dibagikan untuk media sosial.
- Gambar toko (capsule art) harus terbaca saat kecil.

## 17.4 Komunitas dan umpan balik berkelanjutan

- Bagikan proses pengembangan (devlog) secara berkala.
- Bangun komunitas kecil yang peduli sejak awal.
- Terima umpan balik dengan kepala dingin; filter dengan pillars (Bab 13).

## 17.5 Monetisasi dari sisi desain

Model umum:

|Model|Ciri|Pertimbangan desain|
|---|---|---|
|Beli sekali (premium)|Pemain membeli game penuh|Fokus pada nilai: pengalaman lengkap, replayability|
|Demo gratis plus beli|Pemain coba dulu|Demo harus mewakili kualitas|
|DLC atau ekspansi|Konten tambahan berbayar|Desain agar game dasar tetap utuh|
|Gratis dengan pembelian dalam game|Basis pemain besar|Perlu desain ekonomi sangat hati-hati|
|Langganan atau paket platform|Distribusi lewat layanan|Syarat dan skema bagi hasil bervariasi|

Untuk indie single-player berfokus gameplay, **beli sekali** biasanya paling selaras dengan desain yang bersih.

### Prinsip monetisasi yang etis

- Jangan mengorbankan **keadilan gameplay** demi penjualan.
- Hindari mekanik yang memanfaatkan psikologi secara manipulatif (misalnya tekanan waktu palsu).
- Jelaskan dengan jujur apa yang dibeli pemain.
- Harga mencerminkan durasi dan kualitas, serta kondisi pasar target.

## 17.6 Pasca rilis

- Siapkan rencana perbaikan bug cepat setelah rilis.
- Pantau ulasan dan cari pola keluhan.
- Putuskan apakah update konten layak, berdasarkan sumber daya dan permintaan.
- Pelajari data (penjualan, retensi) untuk proyek berikutnya.

## 17.7 Kesalahan umum

- Memikirkan pemasaran hanya setelah game selesai.
- Demo tidak stabil atau tidak mewakili game.
- Harga tanpa riset pasar.
- Tidak menyiapkan rencana pasca rilis.

## Latihan Bab 17

1. Tulis hook game Anda dalam satu kalimat dan uji pada lima orang: apakah mereka paham?
2. Rancang alur demo 10 menit: apa yang ditunjukkan pada menit 0 sampai 2, 2 sampai 5, 5 sampai 10, dan ajakan di akhir.
3. Buat daftar lima klip pendek (3 sampai 5 detik) yang menampilkan hal paling menarik dari game Anda.

---

# Bab 18 - Proyek Capstone dan Roadmap Belajar

## Tujuan belajar

- Menerapkan seluruh materi dalam satu proyek terarah.
- Menyusun rencana belajar berkelanjutan.

## 18.1 Proyek capstone: "Game 1 Level Lengkap" dalam 8 minggu

Tujuan: menghasilkan **vertical slice** berkualitas dari game Anda, dengan semua unsur di buku ini.

### Spesifikasi minimal

- 1 core loop yang jelas dan menyenangkan.
- 1 level utama (10 sampai 15 menit bermain) plus 1 area tutorial singkat.
- 3 jenis musuh dengan peran berbeda dan 1 boss atau tantangan puncak.
- 1 sistem progression sederhana (misalnya satu kemampuan baru dan 3 upgrade).
- Cerita dan lore: kerangka satu halaman, 5 item atau catatan lore, satu momen environmental storytelling, tanpa voice actor.
- UI dasar: menu, HUD, layar jeda, pengaturan audio dan kontrol.
- Aksesibilitas dasar (remap, ukuran teks, opsi efek).
- Dokumen: satu halaman desain, decision log, cut list.

### Jadwal 8 minggu

|Minggu|Fokus|Hasil|
|---|---|---|
|1|Konsep: pillars, core loop, satu halaman desain|Dokumen satu halaman|
|2|Prototipe kontrol dan game feel|Karakter yang enak digerakkan|
|3|Prototipe musuh dan pertarungan atau tantangan inti|Satu pertarungan seru|
|4|Blockout level dan playtest pertama|Level greybox dapat dimainkan|
|5|Progression, balancing, dan UI dasar|Sistem lengkap kasar|
|6|Narasi, lore, dan seni pengganti (kualitas rendah)|Cerita terintegrasi|
|7|Polish: juice, audio, perbaikan dari playtest kedua|Vertical slice|
|8|Playtest akhir, perbaikan bug, rekam trailer singkat|Build final capstone|

Jika waktu Anda terbatas, **kurangi isi, bukan kualitas**. Lebih baik satu level yang sangat baik daripada tiga level setengah matang.

### Kriteria penilaian mandiri

Nilai 1 sampai 5 untuk tiap poin:

1. Kontrol dan game feel terasa enak.
2. Core loop jelas dan menyenangkan diulang.
3. Pemain baru paham tanpa dijelaskan.
4. Tempo level (naik turun) baik.
5. Musuh adil dan terbaca.
6. Cerita dan lore mendukung gameplay dan mudah dilewati.
7. UI jelas dan aksesibel.
8. Stabil (tidak ada bug fatal).

## 18.2 Roadmap belajar berkelanjutan

### Tahap A - Memperkuat dasar (1 sampai 3 bulan)

- Selesaikan 3 prototipe kecil dengan genre berbeda.
- Analisis 10 game dengan kerangka MDA dan core loop.
- Ikuti satu game jam (game jam) untuk melatih menyelesaikan proyek cepat.

### Tahap B - Menengah (3 sampai 9 bulan)

- Selesaikan capstone.
- Pelajari satu spesialisasi lebih dalam: level design, system design, atau narrative design.
- Rilis demo atau game kecil gratis (misalnya di platform game indie).

### Tahap C - Lanjutan (9 bulan ke atas)

- Rilis game komersial kecil.
- Pelajari pemasaran, analitik, dan manajemen komunitas.
- Pertimbangkan kolaborasi (artis, komposer, penulis) untuk proyek berikutnya.

### Kebiasaan yang membangun kemampuan

- **Bermain secara analitis**: setelah bermain, tulis tiga hal yang berhasil dan tiga hal yang tidak.
- **Bongkar game**: gambar ulang level game favorit, hitung metriknya.
- **Buat jurnal desain**: catat ide, kegagalan, dan pelajaran.
- **Ikut komunitas**: forum, Discord, pertemuan lokal developer.
- **Beri dan terima kritik** secara konstruktif.

## 18.3 Menjaga kesehatan karier jangka panjang

- Bangun portofolio dari proyek selesai, bukan proyek tak berujung.
- Dokumentasikan proses (devlog, studi kasus) karena menunjukkan cara berpikir.
- Diversifikasi pendapatan bila game belum menghasilkan (kerja lepas, pekerjaan terkait).
- Ingat bahwa kebanyakan game pertama tidak menjadi hit; yang penting adalah **belajar dan menyelesaikan**.

---

# Lampiran A - Glosarium

|Istilah|Arti singkat|
|---|---|
|Accessibility (aksesibilitas)|Kemudahan game dimainkan oleh beragam kemampuan|
|AI (gameplay)|Logika perilaku musuh atau karakter non-pemain|
|Anticipation|Fase persiapan sebelum serangan|
|Assist mode|Opsi untuk memudahkan game bagi pemain yang membutuhkan|
|Balancing|Penyesuaian angka agar adil dan menyenangkan|
|Behavior tree|Struktur pohon untuk keputusan AI|
|Blockout / greybox|Level kasar dari bentuk dasar untuk menguji gameplay|
|Core loop|Siklus aksi inti yang paling sering diulang|
|Coyote time|Jeda pendek setelah meninggalkan tepi, pemain masih boleh melompat|
|Cut list|Daftar fitur yang akan dipotong bila waktu mepet|
|DDA|Dynamic Difficulty Adjustment, kesulitan menyesuaikan otomatis|
|Diegetic|Elemen UI yang ada di dalam dunia game|
|Diminishing returns|Manfaat tambahan yang semakin kecil|
|Dominant strategy|Strategi yang selalu terbaik sehingga menyingkirkan pilihan lain|
|Emergent gameplay|Perilaku menarik yang muncul dari interaksi aturan|
|Environmental storytelling|Bercerita lewat lingkungan|
|Feature creep / scope creep|Pertumbuhan lingkup tanpa kendali|
|Flow|Keadaan fokus ketika tantangan seimbang dengan kemampuan|
|FSM|Finite State Machine, mesin keadaan terbatas|
|Game feel|Sensasi taktil saat mengendalikan|
|GDD|Game Design Document|
|Hit stop|Pembekuan singkat saat serangan kena|
|Hitbox / hurtbox|Area yang menimbulkan atau menerima damage|
|HUD|Heads-Up Display, informasi di layar|
|Juice|Efek tambahan yang membuat aksi terasa kuat|
|Lore|Latar belakang dunia game|
|Ludonarrative harmony|Keselarasan antara mekanik dan cerita|
|MDA|Mechanics, Dynamics, Aesthetics|
|Meta loop / meta progression|Siklus dan kemajuan jangka panjang|
|Navmesh|Navigation mesh, peta area yang bisa dilalui di 3D|
|Onboarding|Proses memperkenalkan pemain pada game|
|Pacing|Tempo dan ritme intensitas|
|Pillars|Pernyataan inti pengalaman game|
|Playtest|Pengujian dengan pemain nyata|
|Prototipe|Versi cepat untuk menguji ide|
|Risk and reward|Pertukaran antara risiko dan imbalan|
|Scope|Ruang lingkup pekerjaan|
|Sink / source|Penyerap dan sumber sumber daya dalam ekonomi game|
|Telegraphing|Isyarat sebelum serangan|
|TTK / TTD|Time to Kill / Time to Die|
|Vertical slice|Potongan kecil game dengan kualitas hampir akhir|

---

# Lampiran B - Template Siap Pakai

## B.1 Template Satu Halaman Desain

```
JUDUL           :
GENRE / PLATFORM:
PREMIS (1 KALIMAT):
CORE LOOP       :
DESIGN PILLARS  :
  1.
  2.
  3.
FITUR UTAMA     :
  -
  -
  -
TARGET PEMAIN   :
GAYA VISUAL & AUDIO:
SCOPE           : (durasi bermain, jumlah level, jumlah musuh)
HOOK / PEMBEDA  :
RISIKO UTAMA    :
```

## B.2 Template Desain Musuh

```
NAMA           :
PERAN          : (grunt / ranged / tank / swarmer / support / assassin / elite)
HP / DAMAGE / KECEPATAN:
POLA SERANGAN  :
  Serangan 1: anticipation (detik) / action (detik) / recovery (detik)
  Serangan 2:
KELEMAHAN      :
TELEGRAPH      : (isyarat visual dan audio)
LORE SINGKAT   : (satu kalimat)
KOMBINASI IDEAL: (musuh lain yang berpasangan baik)
```

## B.3 Template Desain Level

```
NAMA LEVEL     :
TUJUAN PEMBELAJARAN/PENGALAMAN:
DURASI TARGET  :
MEKANIK YANG DIPERKENALKAN / DIUJI:
STRUKTUR       : (linear / cabang / hub / terhubung)
KURVA INTENSITAS: (sketsa)
RUANG ISTIRAHAT: (lokasi)
ENCOUNTER      : (daftar pertarungan, musuh, ruang)
RAHASIA / OPSIONAL:
ELEMEN NARASI  : (lore, environmental storytelling)
CHECKPOINT     :
CATATAN PLAYTEST:
```

## B.4 Template Lembar Observasi Playtest

```
Tanggal / Versi build :
Penguji (kode)        :
Pengalaman bermain sebelumnya:

Waktu | Aksi pemain | Ucapan pemain | Interpretasi saya | Prioritas

Pertanyaan akhir:
1. Tujuan game menurut Anda?
2. Paling menyenangkan?
3. Paling membingungkan atau membosankan?
4. Hal yang ingin dilakukan tetapi tidak bisa?
```

## B.5 Template Decision Log

```
Tanggal   :
Keputusan :
Alasan    :
Alternatif yang ditolak:
Dampak yang diharapkan:
Tinjau ulang pada:
```

## B.6 Checklist Sebelum Rilis Demo

```
- Core loop terasa menyenangkan dalam 5 menit pertama
- Tutorial jelas tanpa dinding teks
- Tidak ada bug fatal (crash, progres hilang)
- Opsi dasar tersedia (volume, remap, kualitas grafis)
- Aksesibilitas dasar sudah ada
- Autosave dan checkpoint adil
- Teks tanpa typo penting dan siap lokalisasi
- Tombol lewati untuk teks dan cutscene
- Ajakan di akhir demo (wishlist atau tautan)
- Diuji pada perangkat target minimum
```

---

# Lampiran C - Bacaan dan Sumber Belajar Lanjutan

Buku (judul bahasa Inggris, bisa dicari edisi terbaru):

1. _The Art of Game Design: A Book of Lenses_ - Jesse Schell. Kumpulan sudut pandang untuk memeriksa desain.
2. _A Theory of Fun for Game Design_ - Raph Koster. Mengapa permainan menyenangkan dan bagaimana belajar bekerja.
3. _Game Feel_ - Steve Swink. Dasar kontrol dan sensasi.
4. _Level Up! The Guide to Great Video Game Design_ - Scott Rogers. Praktis, mencakup level, musuh, dan kontrol.
5. _Designing Games_ - Tynan Sylvester. Desain pengalaman, emosi, dan narasi yang muncul dari sistem.
6. _Rules of Play_ - Katie Salen dan Eric Zimmerman. Fondasi teori desain permainan.
7. _Game Programming Patterns_ - Robert Nystrom. Pola kode yang berguna untuk game (tersedia gratis di situs penulis).
8. _The Design of Everyday Things_ - Don Norman. Prinsip desain pengalaman pengguna yang berlaku untuk UI game.

Sumber lain:

- Seri video analisis desain game dari kanal-kanal edukatif di platform video (cari "game design analysis").
- Rekaman presentasi Game Developers Conference (GDC) yang tersedia di kanal resmi.
- Dokumentasi resmi engine pilihan Anda (selalu cek versi terbaru).
- Komunitas developer lokal dan daring untuk umpan balik dan kolaborasi.
- Game jam daring: latihan menyelesaikan proyek dalam batas waktu.

---

## Penutup

Game design adalah keterampilan yang diasah lewat siklus: **rancang, bangun, uji, pelajari, ulangi.** Buku ini memberi Anda peta dan alat, tetapi kemampuan sesungguhnya tumbuh saat Anda menyelesaikan proyek, menerima kritik, dan memperbaiki desain berkali-kali.

Ingat tiga pegangan utama:

1. **Gameplay adalah raja.** Cerita, lore, seni, dan musik memperkuat gameplay; semuanya melayani pengalaman bermain.
2. **Scope kecil, eksekusi tajam.** Game kecil yang selesai dan dipoles mengalahkan game besar yang tak pernah rampung.
3. **Uji dengan manusia nyata.** Intuisi Anda berharga, tetapi pemain adalah hakim akhir.

Selamat berkarya, dan semoga game pertama Anda segera bisa dimainkan orang lain.