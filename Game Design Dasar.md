# Game Design Dasar untuk Developer Indie

Panduan pemula untuk merancang game 2D dan 3D dengan fokus pada gameplay. Cerita dan lore tetap ada, tetapi melayani gameplay, dan tanpa voice actor.

Edisi: 2026 dan seterusnya Bahasa: Indonesia Target pembaca: pemula yang belum pernah merancang game secara serius

---

## Daftar Isi

1. Kata Pengantar dan Cara Memakai Buku Ini
2. Bab 1: Apa Itu Game Design
3. Bab 2: Anatomi Sebuah Game
4. Bab 3: Core Loop dan Gameplay Loop
5. Bab 4: Mekanik, Dinamika, dan Estetika (Kerangka MDA)
6. Bab 5: Memilih Genre, Perspektif, dan Dimensi (2D vs 3D)
7. Bab 6: Tantangan, Kesulitan, dan Kondisi Flow
8. Bab 7: Umpan Balik dan Game Feel
9. Bab 8: Kontrol dan Kamera
10. Bab 9: Progresi, Reward, dan Ekonomi Game
11. Bab 10: Level Design Dasar
12. Bab 11: Cerita dan Lore yang Melayani Gameplay (Tanpa Voice Actor)
13. Bab 12: UI, UX, Onboarding, dan Tutorial
14. Bab 13: Balancing
15. Bab 14: Prototyping dan Playtesting
16. Bab 15: Scope, Produksi, dan Bekerja Solo atau Tim Kecil
17. Bab 16: Dokumentasi Desain (One-Page Design dan GDD Ringan)
18. Bab 17: Memilih Engine dan Alur Kerja
19. Bab 18: Hal yang Perlu Diperhatikan Developer Indie di Era 2026 dan Seterusnya
20. Proyek Latihan: Roadmap 12 Minggu
21. Glosarium
22. Bacaan dan Sumber Belajar Lanjutan

---

## Kata Pengantar dan Cara Memakai Buku Ini

### Untuk siapa buku ini

Buku ini ditulis untuk Anda yang ingin membuat game sendiri atau bersama tim kecil (indie), tetapi belum tahu dari mana harus mulai mendesain. Anda tidak perlu bisa coding atau menggambar untuk memahami isinya. Game design adalah keterampilan berpikir, bukan keterampilan satu alat tertentu.

### Apa yang akan Anda pelajari

Setelah menyelesaikan buku ini, Anda diharapkan mampu:

- Menjelaskan apa itu game design dan membedakannya dari programming, seni, dan produksi.
- Menyusun core loop untuk game Anda sendiri.
- Merancang mekanik, tantangan, kurva kesulitan, dan sistem reward dasar.
- Membuat level sederhana yang mengajarkan pemain secara alami.
- Menulis cerita dan lore yang mendukung gameplay tanpa bergantung pada voice acting.
- Membuat prototipe, melakukan playtest, dan memperbaiki desain berdasarkan data.
- Menentukan scope (ruang lingkup) yang realistis untuk proyek indie.
- Menulis dokumen desain ringkas yang berguna, bukan sekadar formalitas.

### Fokus buku ini

Buku ini sengaja berfokus pada gameplay. Artinya, setiap konsep dinilai dari pertanyaan: "Apakah ini membuat pengalaman bermain lebih baik?" Cerita, lore, dunia, dan visual tetap dibahas, tetapi diposisikan sebagai pendukung gameplay.

Buku ini tidak membahas voice actor. Semua teknik penyampaian cerita di sini memakai teks, visual, lingkungan, suara efek (SFX), musik, dan gameplay itu sendiri. Pendekatan ini murah, realistis untuk indie, dan terbukti berhasil di banyak game.

### Cara membaca

Setiap bab memiliki struktur yang sama:

- Tujuan belajar: apa yang akan Anda kuasai setelah bab itu.
- Penjelasan: konsep dengan bahasa yang mudah.
- Contoh: penerapan nyata.
- Ringkasan: poin penting yang perlu diingat.
- Latihan: tugas kecil. Kerjakan, jangan hanya dibaca.

Saran: siapkan satu buku catatan atau satu file teks. Semua latihan ditulis di sana. Pada akhir buku, catatan itu menjadi dasar dokumen desain game pertama Anda.

### Catatan tentang contoh game

Buku ini menyebut beberapa game terkenal sebagai contoh, misalnya Celeste, Hades, Hollow Knight, Stardew Valley, Portal, dan seri Super Mario. Tujuannya sebagai bahan analisis desain. Disarankan Anda memainkan sebagian dari game tersebut sambil membaca, lalu mengamati: "Apa yang dilakukan game ini, dan mengapa itu berhasil?"

---

## Bab 1: Apa Itu Game Design

### Tujuan belajar

- Memahami definisi game design.
- Membedakan peran game designer dari peran lain dalam tim.
- Memahami mengapa game design penting bagi developer indie.

### 1.1 Definisi sederhana

Game design adalah proses menentukan aturan, tujuan, tantangan, dan pengalaman yang akan dialami pemain ketika bermain game.

Pertanyaan inti seorang game designer:

- Apa yang dilakukan pemain di game ini?
- Mengapa pemain mau melakukannya terus-menerus?
- Bagaimana pemain tahu bahwa mereka berhasil atau gagal?
- Apa yang dirasakan pemain saat bermain?

Bayangkan sepak bola. Game designer sepak bola (para pembuat aturan) menentukan: ada dua tim, ada gawang, tangan tidak boleh menyentuh bola, ada offside, ada waktu 2 x 45 menit. Aturan-aturan itu menciptakan pengalaman seru. Pemain tidak perlu membaca buku manual panjang, karena aturan dasarnya sederhana tetapi menghasilkan kemungkinan permainan yang sangat banyak.

### 1.2 Game design bukan sekadar "ide"

Kesalahan umum pemula: mengira game designer hanya orang yang punya ide game keren. Kenyataannya, ide murah. Yang bernilai adalah kemampuan mengubah ide menjadi sistem yang bisa dimainkan, diuji, dan diperbaiki.

Contoh ide: "Game tentang pahlawan yang mengalahkan naga."

Contoh desain: "Pemain bergerak dengan 4 arah, punya satu serangan jarak dekat dengan jeda 0,4 detik, dan satu gerakan menghindar yang memberi kekebalan 0,2 detik. Naga memiliki tiga pola serangan yang bisa dibaca dari animasi persiapannya. Setiap kali pemain kalah, ia belajar satu pola baru."

Perhatikan bedanya: ide bersifat umum, desain bersifat spesifik dan bisa diuji.

### 1.3 Peran dalam pengembangan game

|Peran|Fokus utama|
|---|---|
|Game designer|Aturan, mekanik, level, balancing, pengalaman pemain|
|Programmer|Mengimplementasikan sistem dalam kode|
|Artist (2D/3D)|Visual: karakter, lingkungan, animasi, UI|
|Sound designer / komposer|SFX dan musik|
|Narrative designer / penulis|Cerita, lore, dialog tertulis|
|Producer|Jadwal, prioritas, komunikasi|
|QA / tester|Mencari bug dan masalah pengalaman|

Pada tim indie, satu orang sering memegang banyak peran sekaligus. Anda mungkin menjadi designer, programmer, dan penulis dalam satu hari. Karena itu pemahaman dasar tiap peran sangat membantu.

### 1.4 Mengapa game design penting untuk indie

Developer indie biasanya memiliki sumber daya terbatas: waktu, uang, dan tenaga. Desain yang baik memungkinkan Anda:

- Membuat game yang menarik dengan konten sedikit (karena sistemnya dalam, bukan kontennya banyak).
- Menghindari pekerjaan yang terbuang karena fitur yang tidak jadi dipakai.
- Menentukan prioritas dengan jelas.

Contoh klasik: banyak game indie sukses dibangun dari satu mekanik inti yang diolah dalam-dalam, bukan dari puluhan fitur dangkal.

### Ringkasan

- Game design = merancang aturan, tantangan, dan pengalaman bermain.
- Ide umum belum desain; desain harus spesifik dan bisa diuji.
- Indie sering merangkap banyak peran, jadi pahami semuanya secara dasar.

### Latihan

1. Pilih satu game favorit Anda. Tulis dalam 5 kalimat: apa yang dilakukan pemain, apa tujuannya, apa tantangannya, bagaimana pemain tahu ia berhasil, dan apa yang membuat Anda terus bermain.
2. Ambil satu ide game dari kepala Anda dan ubah menjadi "desain spesifik" seperti contoh naga di atas.

---

## Bab 2: Anatomi Sebuah Game

### Tujuan belajar

- Mengenali elemen-elemen dasar yang membentuk game.
- Membedakan game dari mainan (toy) dan cerita interaktif murni.

### 2.1 Elemen formal game

Hampir semua game memiliki elemen berikut:

1. **Pemain (player)**: siapa yang bermain, dan berapa banyak (single player, co-op, versus).
2. **Tujuan (goal)**: apa yang ingin dicapai pemain. Contoh: sampai ke akhir level, mengumpulkan skor tertinggi, bertahan hidup.
3. **Aturan (rules)**: batasan dan kemungkinan tindakan. Contoh: karakter hanya bisa lompat dua kali di udara.
4. **Tantangan (challenge)**: hambatan antara pemain dan tujuan. Contoh: musuh, teka-teki, batas waktu, sumber daya terbatas.
5. **Umpan balik (feedback)**: informasi yang diterima pemain tentang hasil tindakannya, melalui visual, suara, angka, dan getaran kontroler.
6. **Sistem dan sumber daya (resources)**: hal yang dikelola pemain, seperti nyawa, mana, uang, amunisi, dan waktu.
7. **Konflik dan hasil (outcome)**: ada kondisi menang, kalah, atau kemajuan yang bisa diukur.

Jika salah satu elemen hilang, pengalaman biasanya terasa kurang "seperti game". Contoh: tanpa tujuan dan tantangan, sesuatu menjadi mainan (toy), seperti sandbox bebas tanpa target. Itu tidak salah, tetapi berbeda dengan game.

### 2.2 Verb: kata kerja inti

Cara cepat memahami game: tulis daftar kata kerja yang dilakukan pemain.

|Game|Kata kerja utama|
|---|---|
|Platformer (Super Mario)|berlari, melompat, menginjak, mengumpulkan|
|Game puzzle (Portal)|menembak portal, memindahkan objek, melompat lewat portal|
|Farming sim (Stardew Valley)|menanam, menyiram, memancing, berbicara, menambang|
|Roguelike aksi (Hades)|menyerang, menghindar, memilih berkah, menggunakan kemampuan|

Disarankan membatasi jumlah verb utama. Game dengan 3 sampai 5 verb yang dipoles jauh lebih kuat daripada game dengan 20 verb yang setengah matang.

### 2.3 Pilihan yang bermakna

Inti dari game yang menyenangkan adalah **pilihan yang bermakna (meaningful choice)**. Pilihan bermakna punya ciri:

- Ada lebih dari satu opsi yang masuk akal.
- Setiap opsi punya konsekuensi yang jelas dan berbeda.
- Pemain bisa memperkirakan konsekuensi itu (tidak sepenuhnya acak).

Contoh pilihan tidak bermakna: dua pintu, satu menuju hadiah, satu kosong, tanpa petunjuk apa pun. Itu hanya tebakan.

Contoh pilihan bermakna: pemain menemukan senjata yang kuat tetapi lambat, dan senjata lain yang lemah tetapi cepat. Musuh berikutnya terlihat gesit dari jauh. Pemain mempertimbangkan dan memutuskan.

### 2.4 Game versus mainan versus cerita interaktif

- **Mainan (toy)**: dimainkan karena menyenangkan itu sendiri, tidak ada tujuan eksplisit.
- **Game**: ada tujuan, aturan, tantangan, dan hasil.
- **Cerita interaktif / visual novel**: fokus pada narasi dengan sedikit atau tanpa tantangan mekanis. Pilihan memengaruhi alur, tetapi bukan keterampilan.

Buku ini berfokus pada game dengan gameplay, bukan visual novel.

### Ringkasan

- Elemen game: pemain, tujuan, aturan, tantangan, umpan balik, sumber daya, hasil.
- Kenali game lewat daftar kata kerja (verb) inti.
- Pilihan yang bermakna adalah jantung dari game yang seru.

### Latihan

1. Analisis dua game dengan tabel elemen formal (pemain, tujuan, aturan, tantangan, umpan balik, sumber daya, hasil).
2. Tulis daftar verb untuk ide game Anda. Coret hingga tersisa maksimal 5.

---

## Bab 3: Core Loop dan Gameplay Loop

### Tujuan belajar

- Memahami core loop dan mengapa itu fondasi desain.
- Membedakan loop mikro, makro, dan meta.
- Menyusun core loop untuk game sendiri.

### 3.1 Apa itu core loop

Core loop adalah rangkaian tindakan inti yang diulang-ulang pemain sepanjang game. Loop yang baik membuat setiap putaran terasa memuaskan sekaligus mendorong pemain untuk mengulanginya.

Pola umum core loop:

```
Tindakan  ->  Hasil  ->  Reward  ->  Peluang baru  ->  Tindakan berikutnya
```

Contoh pada game bertani:

```
Tanam bibit -> Siram dan tunggu -> Panen -> Jual hasil panen -> Beli bibit/alat baru -> Tanam lebih banyak
```

Contoh pada game aksi roguelike:

```
Masuk ruangan -> Bertarung -> Pilih hadiah -> Masuk ruangan berikutnya -> (kalah) -> Upgrade permanen -> Mulai lagi
```

### 3.2 Tiga lapis loop

Game biasanya memiliki loop berlapis:

|Lapis|Durasi|Contoh|
|---|---|---|
|Loop mikro|Detik sampai menit|Menyerang, menghindar, melompat, membidik|
|Loop makro|Menit sampai satu sesi|Menyelesaikan level, satu run, satu hari dalam game|
|Loop meta|Sesi ke sesi (jam sampai hari)|Upgrade permanen, membuka area, kemajuan cerita|

Cara menilai: apabila loop mikro membosankan, game tidak akan diselamatkan oleh loop makro atau meta. Selalu uji dan poles loop mikro lebih dulu.

### 3.3 Ciri core loop yang sehat

1. **Mudah dipahami**: pemain baru dapat menjelaskan "kita ngapain di sini" dalam satu kalimat.
2. **Memuaskan sendiri**: satu putaran sudah terasa menyenangkan tanpa reward besar.
3. **Memiliki variasi**: putaran ke-100 tidak terasa sama persis dengan putaran pertama.
4. **Memiliki kemajuan**: ada alasan untuk berputar lagi (kemampuan baru, tantangan lebih sulit, penemuan).
5. **Seimbang antara risiko dan reward**.

### 3.4 Cara menyusun core loop Anda

Langkah praktis:

1. Tulis verb utama (dari Bab 2).
2. Susun urutan verb menjadi satu putaran.
3. Tentukan reward pada setiap putaran (bisa berupa informasi, sumber daya, kemampuan, atau sekadar rasa puas).
4. Tentukan hal apa yang berubah setelah putaran selesai (supaya putaran berikutnya tidak identik).
5. Gambarkan sebagai diagram sederhana di kertas.

### Ringkasan

- Core loop = tindakan inti yang diulang pemain.
- Ada loop mikro, makro, dan meta; mulai dari mikro.
- Uji core loop sedini mungkin dengan prototipe kasar.

### Latihan

1. Gambar core loop dari tiga game yang Anda kenal. Tandai mana loop mikro, makro, dan meta.
2. Gambar core loop game Anda. Tunjukkan ke satu teman dan tanyakan apakah ia paham tanpa penjelasan tambahan.

---

## Bab 4: Mekanik, Dinamika, dan Estetika (Kerangka MDA)

### Tujuan belajar

- Memahami kerangka MDA (Mechanics, Dynamics, Aesthetics).
- Menggunakannya untuk merancang dari tujuan pengalaman.

### 4.1 Tiga tingkatan MDA

MDA adalah kerangka berpikir yang populer di dunia game design, dari makalah oleh Hunicke, LeBlanc, dan Zubek.

- **Mechanics (mekanik)**: aturan dan komponen dasar yang dibuat designer. Contoh: kecepatan gerak, jumlah nyawa, rumus kerusakan, jeda serangan.
- **Dynamics (dinamika)**: perilaku yang muncul ketika mekanik dijalankan bersama pemain. Contoh: pemain mulai bermain defensif, atau berkelompok, atau mencuri dari pemain lain.
- **Aesthetics (estetika)**: respons emosional pemain. Contoh: tegang, bangga, penasaran, santai, puas.

Arah pandang berbeda:

- Designer bekerja dari Mechanics ke Dynamics ke Aesthetics (mengatur aturan, berharap muncul perasaan).
- Pemain mengalami dari Aesthetics ke Dynamics ke Mechanics (merasakan dulu, baru lama-lama paham aturannya).

Karena itu, mulailah dari pertanyaan: "Perasaan apa yang ingin saya timbulkan pada pemain?", lalu rancang mekanik yang mengarah ke sana.

### 4.2 Delapan jenis kesenangan (estetika)

Makalah MDA menyebut beberapa jenis "kesenangan" (fun) yang bisa dijadikan tujuan:

1. Sensasi (sensation): kenikmatan indra, visual dan audio.
2. Fantasi: menjadi seseorang atau berada di dunia lain.
3. Narasi: alur cerita yang menarik.
4. Tantangan: mengatasi rintangan dan menguasai keterampilan.
5. Persahabatan / sosial: berinteraksi dengan pemain lain.
6. Penemuan (discovery): menjelajah dan menemukan hal baru.
7. Ekspresi: menyatakan diri, misalnya kustomisasi.
8. Pelepasan (submission): bermain santai untuk menghabiskan waktu.

Satu game biasanya menonjol di dua atau tiga jenis saja. Pilih sebagai "bintang utama" dan jangan mencoba menyenangkan semuanya.

### 4.3 Contoh penerapan MDA

Tujuan estetika: pemain merasa tegang tetapi adil ("sulit, tapi saya yang salah, bukan game-nya").

Mekanik yang mendukung:

- Musuh punya animasi persiapan serangan yang jelas (0,5 detik sebelum memukul).
- Pemain punya gerakan menghindar yang andal.
- Pemain kehilangan sedikit progres saat kalah, tetapi tidak semuanya.

Dinamika yang muncul:

- Pemain belajar membaca pola musuh.
- Pemain menunggu momen yang tepat untuk menyerang.
- Pemain merasa "kali ini saya pasti bisa" lalu mencoba lagi.

### 4.4 Menyusun "pernyataan pengalaman"

Tulis satu atau dua kalimat yang menggambarkan pengalaman yang Anda inginkan. Disebut juga experience statement atau pillar.

Contoh:

- "Pemain merasa seperti ninja yang cerdik: sabar, mengintai, lalu bergerak cepat dan tepat."
- "Pemain merasa tenang dan puas membangun kebun kecil secara perlahan."

Gunakan pernyataan ini sebagai filter. Setiap fitur baru ditanya: "Apakah ini mendukung pernyataan pengalaman?" Jika tidak, buang atau tunda.

### Ringkasan

- MDA: mekanik membentuk dinamika, dinamika membentuk estetika.
- Mulai dari perasaan yang diinginkan, lalu rancang mekaniknya.
- Pernyataan pengalaman adalah filter fitur yang efektif.

### Latihan

1. Tulis pernyataan pengalaman untuk game Anda (maksimal dua kalimat).
2. Tulis 5 mekanik yang mendukungnya dan 3 mekanik yang mungkin bertentangan dengannya.

---

## Bab 5: Memilih Genre, Perspektif, dan Dimensi (2D vs 3D)

### Tujuan belajar

- Memahami konsekuensi desain dari pilihan 2D atau 3D.
- Memilih genre dan perspektif yang realistis untuk indie.

### 5.1 Genre: bahasa bersama

Genre adalah label kelompok game dengan mekanik serupa. Contoh umum:

- Platformer: lompat dan navigasi ruang.
- Action / beat 'em up / hack and slash: pertarungan langsung.
- Roguelike / roguelite: run acak, kematian berarti mulai ulang dengan kemajuan terbatas.
- Metroidvania: dunia saling terhubung, area terbuka lewat kemampuan baru.
- Puzzle: pemecahan teka-teki logika.
- Simulasi / manajemen: mengelola sistem (kebun, kota, restoran).
- RPG: karakter berkembang lewat statistik, perlengkapan, dan pilihan.
- Strategi: perencanaan, sumber daya, posisi.
- Survival: bertahan dengan sumber daya terbatas.
- Horor: ketegangan dan rasa takut.

Genre membantu pemain berekspektasi dan membantu Anda belajar dari game sejenis. Anda boleh mencampur genre, tetapi mulai dari satu genre dominan.

### 5.2 Dimensi: 2D dan 3D

Perbedaan ini bukan sekadar soal "gambar datar atau tidak". Pilihan tersebut memengaruhi desain, produksi, dan biaya.

|Aspek|2D|3D|
|---|---|---|
|Ruang gerak|Bidang datar (kiri-kanan, atas-bawah)|Ruang penuh (x, y, z)|
|Kamera|Umumnya sederhana dan tetap|Rumit: bisa menabrak dinding, terhalang objek, membingungkan|
|Pembacaan visual|Mudah: jarak dan posisi jelas|Perlu perhatian: kedalaman, sudut pandang|
|Produksi aset|Sprite, tilemap, animasi frame-by-frame atau tulang 2D|Model 3D, rigging, tekstur, animasi, material, pencahayaan|
|Biaya dan waktu|Umumnya lebih rendah|Umumnya lebih tinggi|
|Level design|Layout cenderung linear atau berlapis|Perlu memikirkan ruang, ketinggian, navigasi, oklusi|
|Kinerja (performa)|Ringan|Perlu optimasi (poligon, draw call, pencahayaan)|

Penting: "3D itu lebih keren" adalah mitos. Banyak game 2D sangat sukses dan mendalam secara desain. Pilih berdasarkan kebutuhan gameplay dan kemampuan Anda.

### 5.3 Variasi perspektif

Di antara 2D dan 3D ada beberapa pendekatan campuran:

- **2D side-scroll**: pandangan dari samping. Cocok untuk platformer dan aksi.
- **2D top-down**: pandangan dari atas. Cocok untuk RPG, shooter, dan game bertani.
- **2.5D**: grafis 3D atau efek kedalaman, tetapi gerak dibatasi pada bidang 2D.
- **Isometrik**: sudut miring tetap, populer untuk strategi dan RPG.
- **3D orang ketiga (third-person)**: kamera di belakang karakter. Cocok untuk aksi dan petualangan.
- **3D orang pertama (first-person)**: kamera dari mata karakter. Cocok untuk eksplorasi, shooter, dan puzzle.

### 5.4 Cara memilih untuk proyek pertama

Panduan praktis:

1. Mulai dari gameplay: perspektif apa yang membuat mekanik inti paling jelas?
2. Pertimbangkan kemampuan: seberapa nyaman Anda membuat aset 2D atau 3D, atau membeli dan menggunakan aset berlisensi?
3. Pertimbangkan scope: proyek pertama sebaiknya kecil. 2D hampir selalu lebih mudah untuk dirampungkan.
4. Pertimbangkan pasar: apakah ada pemain untuk genre ini? Apakah terlalu padat?

Rekomendasi umum bagi pemula: game 2D dengan satu mekanik inti, selesai dalam 1 sampai 3 bulan. Setelah itu baru berkembang ke 3D atau proyek lebih besar.

### Ringkasan

- Genre adalah bahasa bersama dan alat belajar.
- 2D dan 3D berbeda dalam desain, biaya, dan kamera, bukan sekadar tampilan.
- Proyek pertama: kecil dan 2D biasanya pilihan paling aman.

### Latihan

1. Pilih satu genre dominan dan satu perspektif untuk game Anda. Tulis tiga alasan.
2. Cari dua game indie dengan genre sama dan catat apa yang membuatnya berbeda satu sama lain.

---

## Bab 6: Tantangan, Kesulitan, dan Kondisi Flow

### Tujuan belajar

- Memahami konsep flow dan mengapa kesulitan harus diatur.
- Merancang kurva kesulitan dasar.
- Mengenali perbedaan sulit yang adil dan sulit yang menjengkelkan.

### 6.1 Konsep flow

Flow adalah kondisi mental ketika seseorang sepenuhnya tenggelam dalam aktivitas. Konsep ini dipopulerkan oleh psikolog Mihaly Csikszentmihalyi. Dalam game, flow terjadi ketika **tantangan seimbang dengan keterampilan pemain**.

```
Tantangan
   ^
   |   Cemas (terlalu sulit)
   |        /
   |       /  <- zona flow
   |      /
   |     /
   |    /  Bosan (terlalu mudah)
   +-----------------------------> Keterampilan pemain
```

- Terlalu sulit: pemain frustrasi, cemas, lalu berhenti.
- Terlalu mudah: pemain bosan, lalu berhenti.
- Seimbang: pemain terus terlibat.

Keterampilan pemain bertambah seiring waktu, jadi tantangan juga harus naik secara bertahap.

### 6.2 Kurva kesulitan

Kurva kesulitan menggambarkan bagaimana tantangan berubah sepanjang game. Pola yang sehat bukan garis lurus naik terus, tetapi gelombang:

```
Kesulitan
   ^
   |            /\        /\
   |       /\  /  \  /\  /  \   (klimaks)
   |  /\  /  \/    \/  \/
   | /  \/
   +--------------------------------> Waktu
```

Prinsipnya: naik (tantangan baru), turun sebentar (istirahat dan penguasaan), naik lagi lebih tinggi. Fase turun sama pentingnya karena memberi pemain waktu menikmati keterampilan baru.

### 6.3 Pola pengenalan mekanik: Perkenalkan, Kembangkan, Uji, Putar

Pola yang sering dipakai pada level design (terkenal dari game platformer):

1. **Perkenalkan**: pemain bertemu mekanik baru di situasi aman, tanpa risiko besar.
2. **Kembangkan**: mekanik dipakai dalam situasi sedikit lebih sulit.
3. **Uji**: mekanik dikombinasikan dengan hal lain.
4. **Putar (twist)**: mekanik dipakai dengan cara tak terduga.

Setelah itu, pindah ke mekanik berikutnya. Pola ini mengajarkan tanpa teks panjang.

### 6.4 Sulit yang adil versus menjengkelkan

Kesulitan yang adil memiliki ciri:

- Pemain tahu mengapa ia gagal ("saya terlambat menghindar").
- Aturan konsisten, tidak berubah tiba-tiba.
- Ada petunjuk atau tanda peringatan sebelum bahaya.
- Mengulang tidak memakan waktu lama (checkpoint dekat, waktu muat singkat).

Kesulitan yang menjengkelkan biasanya karena:

- Kematian dari hal yang tidak terlihat atau tidak mungkin diprediksi.
- Kontrol tidak responsif.
- Hukuman terlalu berat dibanding kesalahan.
- Harus mengulang bagian panjang yang sudah dikuasai.

### 6.5 Opsi kesulitan dan bantuan

Cara umum mengakomodasi keterampilan berbeda:

- Mode kesulitan (mudah, normal, sulit).
- Opsi bantuan (assist mode) yang bisa diatur satu per satu, misalnya mengurangi kecepatan game atau memberi nyawa tambahan.
- Kesulitan adaptif, yaitu game menyesuaikan diri secara halus.

Banyak developer indie kini menyediakan opsi bantuan sebagai bagian dari aksesibilitas (lihat Bab 18).

### Ringkasan

- Flow = tantangan seimbang dengan keterampilan.
- Kurva kesulitan sebaiknya bergelombang, dengan jeda istirahat.
- Kesulitan yang adil membuat pemain merasa "itu salah saya, saya bisa memperbaikinya".

### Latihan

1. Gambar kurva kesulitan untuk game Anda (5 level atau 5 fase). Tandai titik istirahat dan titik klimaks.
2. Pilih satu mekanik di game Anda dan rancang urutan Perkenalkan, Kembangkan, Uji, Putar-nya.

---

## Bab 7: Umpan Balik dan Game Feel

### Tujuan belajar

- Memahami peran umpan balik dalam gameplay.
- Mengenal game feel dan teknik juice.
- Menerapkan prinsip responsivitas pada kontrol.

### 7.1 Mengapa umpan balik penting

Setiap tindakan pemain harus mendapat respons yang jelas dan cepat. Tanpa umpan balik, pemain tidak tahu apakah tindakannya berhasil, sehingga game terasa "mati" atau tidak adil.

Jenis umpan balik:

- **Visual**: animasi, partikel, perubahan warna, getaran layar, indikator kerusakan.
- **Audio**: efek suara, perubahan musik.
- **Haptik**: getaran kontroler.
- **Informasi**: angka, bar, ikon, teks.

### 7.2 Game feel

Game feel adalah sensasi fisik dan taktil ketika mengendalikan sesuatu dalam game. Istilah ini dipopulerkan oleh Steve Swink. Karakter yang "enak dikontrol" biasanya memiliki:

- **Respons cepat**: jeda antara tombol ditekan dan aksi terjadi sangat singkat.
- **Momentum dan akselerasi yang terasa nyata**: tidak langsung berhenti atau langsung berlari, kecuali memang disengaja.
- **Umpan balik kuat pada tindakan penting**: lompat, mendarat, memukul.

### 7.3 Juice

"Juice" adalah lapisan efek tambahan yang membuat tindakan terasa memuaskan tanpa mengubah aturan. Contoh teknik juice:

|Teknik|Efek|
|---|---|
|Screen shake (getar layar)|Memberi bobot pada tabrakan atau ledakan|
|Hit stop / freeze frame|Jeda 2 sampai 6 frame saat memukul agar dampaknya terasa kuat|
|Squash and stretch|Karakter memipih saat mendarat, memanjang saat melompat|
|Partikel|Debu saat mendarat, percikan saat memukul|
|Suara berlapis|Beberapa lapisan suara untuk satu aksi|
|Perubahan warna sesaat (flash)|Menandai musuh terkena serangan|
|Easing dan animasi bertahap|UI muncul dengan gerakan halus, bukan tiba-tiba|

Peringatan: juice yang berlebihan bisa mengganggu, bahkan membuat pusing. Beri opsi untuk mengurangi atau mematikan efek kuat seperti getaran layar (lihat Bab 18).

### 7.4 Teknik responsivitas yang dipakai banyak platformer

Dua teknik sederhana yang membuat kontrol terasa lebih adil:

- **Coyote time**: pemain masih bisa melompat dalam jeda sangat singkat (misalnya 0,1 detik) setelah meninggalkan tepi platform.
- **Input buffering**: jika pemain menekan tombol sedikit lebih awal dari waktu yang tepat, game menyimpan inputnya sebentar lalu menjalankannya saat memungkinkan.

Kedua teknik ini membuat game terasa "memaafkan kesalahan kecil" tanpa menghilangkan keterampilan.

### 7.5 Telegraphing

Telegraphing berarti memberi tanda peringatan sebelum sesuatu terjadi, misalnya musuh mengangkat senjata sebelum menyerang, atau lantai berkedip sebelum runtuh. Telegraphing adalah kunci kesulitan yang adil dan sangat penting untuk game tanpa teks atau voice yang menjelaskan bahaya.

### Ringkasan

- Setiap aksi pemain butuh umpan balik yang jelas.
- Game feel dibangun dari respons cepat, momentum, dan umpan balik kuat.
- Juice memperkuat rasa, tetapi harus bisa dikurangi demi kenyamanan.

### Latihan

1. Pilih satu aksi utama di game Anda (misalnya lompat atau serang). Tulis 5 lapis umpan balik yang akan Anda tambahkan.
2. Buat prototipe gerak karakter sederhana, lalu ubah satu parameter (kecepatan, percepatan, gravitasi) dan catat bagaimana rasanya berubah.

---

## Bab 8: Kontrol dan Kamera

### Tujuan belajar

- Merancang skema kontrol yang jelas.
- Memahami masalah kamera, terutama di 3D.

### 8.1 Prinsip desain kontrol

1. **Sederhana dan konsisten**: tombol yang sama punya fungsi yang konsisten.
2. **Sedikit tombol, banyak makna**: satu tombol bisa punya fungsi berbeda tergantung konteks, asal tetap jelas.
3. **Selaras dengan genre**: pemain berpengalaman berharap tata letak tertentu, misalnya WASD di PC atau analog kiri untuk bergerak di kontroler.
4. **Mendukung beberapa perangkat**: keyboard dan mouse, kontroler, layar sentuh jika relevan.
5. **Bisa dikonfigurasi ulang** (remapping): penting untuk aksesibilitas.

### 8.2 Jenis kontrol umum

- **Kontrol langsung (direct)**: pemain langsung menggerakkan karakter. Contoh: platformer.
- **Kontrol tidak langsung**: pemain memberi perintah, unit yang melakukan. Contoh: strategi.
- **Kontrol berbasis titik dan klik**: pemain menunjuk target. Contoh: game petualangan klasik.
- **Kontrol berbasis giliran**: pemain memilih aksi saat gilirannya.

### 8.3 Kamera 2D

Kamera 2D umumnya sederhana, tetapi tetap perlu keputusan desain:

- Apakah kamera mengikuti karakter dengan kaku atau halus (smoothing)?
- Apakah kamera "melihat ke depan" (look-ahead) ke arah gerak?
- Apakah ada batas (bounds) supaya tidak menampilkan ruang kosong di luar level?
- Apakah ada zona kamera tetap pada ruangan tertentu?

### 8.4 Kamera 3D

Kamera 3D sering menjadi sumber masalah terbesar. Pertanyaan yang perlu dijawab:

- Apakah kamera dikontrol pemain, otomatis, atau campuran?
- Bagaimana kamera menghindari tembok atau objek yang menghalangi?
- Apakah ada tombol untuk mengarahkan kamera kembali ke belakang karakter?
- Seberapa besar bidang pandang (field of view) agar nyaman dan tidak menyebabkan mual?

Untuk first-person, perhatikan efek goyang kepala (head bob) dan sensitivitas gerak. Berikan opsi pengaturan untuk kenyamanan.

### 8.5 Kejelasan dan keterbacaan

Terlepas dari 2D atau 3D, pemain harus selalu bisa membaca situasi:

- Karakter pemain mudah dibedakan dari latar.
- Bahaya dan musuh terlihat jelas.
- Objek interaktif memiliki penanda visual yang konsisten.

Gunakan kontras warna, siluet, dan pencahayaan untuk menuntun perhatian.

### Ringkasan

- Kontrol harus sederhana, konsisten, dan bisa dikonfigurasi.
- Kamera 3D membutuhkan perhatian khusus.
- Keterbacaan visual adalah bagian dari desain gameplay.

### Latihan

1. Tulis skema kontrol untuk game Anda dalam tabel (tombol, aksi, catatan).
2. Uji prototipe dengan satu orang yang belum pernah melihat game Anda. Catat tombol mana yang membingungkan.

---

## Bab 9: Progresi, Reward, dan Ekonomi Game

### Tujuan belajar

- Memahami jenis progresi dan reward.
- Merancang sistem sumber daya sederhana.
- Menghindari pola desain yang manipulatif.

### 9.1 Jenis progresi

- **Progresi keterampilan pemain**: pemain sendiri menjadi lebih mahir. Ini progresi yang paling murni.
- **Progresi karakter**: statistik, level, atau kemampuan karakter meningkat.
- **Progresi konten**: area, level, atau mekanik baru terbuka.
- **Progresi pengetahuan**: pemain mempelajari lore, kelemahan musuh, atau rahasia dunia.
- **Progresi koleksi**: pemain mengumpulkan item, kostum, atau pencapaian.

Game yang baik memadukan beberapa jenis progresi. Game aksi yang hanya mengandalkan statistik tanpa keterampilan terasa kosong, sedangkan game yang hanya mengandalkan keterampilan tanpa kemajuan terlihat bisa terasa kurang memberi imbalan.

### 9.2 Jenis reward

|Jenis|Contoh|Catatan|
|---|---|---|
|Reward fungsional|Senjata baru, kemampuan baru|Mengubah cara bermain|
|Reward informasi|Peta, petunjuk, lore|Memuaskan rasa ingin tahu|
|Reward estetika|Kostum, warna, dekorasi|Mendukung ekspresi|
|Reward sosial|Peringkat, pencapaian yang dibagikan|Mendukung rasa bangga|
|Reward kemajuan|Naik level, membuka area|Memberi rasa maju|

Prinsip: reward terbaik adalah reward yang membuat bermain lebih menarik, bukan sekadar angka yang bertambah.

### 9.3 Jadwal reward

Cara reward diberikan memengaruhi perilaku pemain:

- **Tetap**: reward setiap kali tindakan selesai. Mudah dipahami.
- **Acak (variabel)**: reward muncul tidak terduga (misalnya drop item). Menimbulkan antisipasi, namun bisa menjerumuskan ke pola kecanduan jika disalahgunakan.
- **Milestone**: reward pada titik kemajuan tertentu.

Perlakukan reward acak dengan hati-hati. Pertimbangkan etika dan dampaknya pada pemain.

### 9.4 Ekonomi game

Ekonomi game adalah sistem sumber daya yang masuk (source) dan keluar (sink).

- **Source (sumber)**: tempat sumber daya didapat (musuh menjatuhkan koin, panen menghasilkan uang).
- **Sink**: tempat sumber daya habis (membeli item, memperbaiki senjata, biaya upgrade).

Jika source jauh lebih besar dari sink, sumber daya menjadi tidak bernilai (inflasi). Jika sink terlalu besar, pemain merasa macet. Mulai dengan satu atau dua sumber daya saja.

Contoh sederhana (game bertani):

|Item|Biaya bibit|Harga jual|Waktu tumbuh|
|---|---|---|---|
|Wortel|20|50|3 hari|
|Tomat|40|110|5 hari|

Dari tabel, pemain dapat menghitung keuntungan per hari dan membuat keputusan. Itulah pilihan bermakna dalam bentuk ekonomi.

### 9.5 Pola yang perlu diwaspadai

Beberapa pola desain dianggap manipulatif jika disalahgunakan, misalnya timer yang sengaja dibuat lama agar pemain membayar, atau tekanan untuk bermain setiap hari. Sebagai developer indie, pertimbangkan reputasi dan etika. Game yang menghormati waktu pemain biasanya mendapat kepercayaan jangka panjang.

### Ringkasan

- Progresi dan reward harus memperkaya gameplay.
- Ekonomi game adalah soal keseimbangan source dan sink.
- Hindari pola manipulatif.

### Latihan

1. Daftar jenis progresi yang ada di game Anda dan beri bobot (rendah, sedang, tinggi).
2. Buat tabel ekonomi sederhana (minimal 3 item) dan hitung keuntungan per unit waktu untuk tiap item.

---

## Bab 10: Level Design Dasar

### Tujuan belajar

- Memahami fungsi level design.
- Menerapkan prinsip tata letak yang menuntun pemain.
- Merancang level pengenalan sederhana.

### 10.1 Fungsi level

Level adalah ruang tempat mekanik dimainkan. Level yang baik:

- Mengajarkan mekanik secara alami.
- Menciptakan tantangan yang bervariasi.
- Mengatur tempo (cepat, lambat, tegang, tenang).
- Menyampaikan dunia dan cerita lewat ruang.

### 10.2 Prinsip tata letak

1. **Ada tujuan yang jelas**: pemain tahu atau bisa menebak ke mana harus pergi.
2. **Penuntun visual**: cahaya, warna, garis, dan siluet mengarahkan perhatian.
3. **Ritme**: selang-seling antara aksi dan istirahat.
4. **Variasi**: ruang yang berbeda bentuk dan fungsi.
5. **Landmark**: ciri khas yang dapat dikenali agar pemain tidak tersesat, penting di 3D.

### 10.3 Struktur level umum

- **Linear**: satu jalur dari awal ke akhir. Mudah dikendalikan, cocok untuk cerita yang terarah.
- **Bercabang**: beberapa jalur yang bertemu kembali.
- **Hub and spoke**: satu area pusat dengan beberapa jalur keluar.
- **Terbuka**: pemain bebas menjelajah, perlu pengendalian tantangan yang lebih rumit.
- **Saling terhubung (interconnected)**: area terkunci hingga pemain mendapat kemampuan tertentu (gaya Metroidvania).

### 10.4 Mengajar tanpa kata

Level pengenalan yang baik membuat pemain belajar dengan mencoba, bukan membaca.

Contoh: ingin mengajarkan lompat melewati jurang.

1. Ruang pertama: jurang kecil dan aman, jika jatuh hanya turun sedikit dan bisa naik lagi.
2. Ruang kedua: jurang sedikit lebih lebar, jika jatuh kembali ke awal ruangan.
3. Ruang ketiga: jurang dengan musuh di seberang.
4. Ruang keempat: jurang dengan platform bergerak.

Tidak ada teks yang diperlukan. Pemain belajar melalui pola.

### 10.5 Proses level design praktis

1. **Tujuan**: apa yang ingin diajarkan atau dirasakan pemain pada level ini?
2. **Sketsa di kertas**: gambar denah kasar, tandai awal, akhir, bahaya, reward.
3. **Blockout (graybox)**: bangun level dengan bentuk dasar tanpa seni. Fokus pada ukuran, jarak, dan alur.
4. **Playtest**: biarkan orang lain bermain, amati tanpa membantu.
5. **Iterasi**: ubah berdasarkan pengamatan.
6. **Polesan seni dan audio**: dilakukan terakhir, setelah level terbukti seru.

Jangan membuat seni final sebelum level lolos tahap blockout.

### 10.6 Ruang sebagai penyampai cerita (environmental storytelling)

Penempatan objek dapat bercerita. Contoh: meja makan dengan piring berantakan dan kursi terjatuh menyiratkan kejadian mendadak. Ini dibahas lebih jauh pada Bab 11.

### Ringkasan

- Level mengajarkan, mengatur tempo, dan bercerita.
- Mulai dengan sketsa dan blockout sebelum seni.
- Pemain belajar paling baik dengan mencoba.

### Latihan

1. Rancang satu level pengenalan (4 sampai 5 ruangan) untuk mekanik utama Anda. Gambar denahnya.
2. Buat blockout level itu dan uji ke dua orang. Catat titik di mana mereka bingung.

---

## Bab 11: Cerita dan Lore yang Melayani Gameplay (Tanpa Voice Actor)

### Tujuan belajar

- Memahami peran cerita dan lore di game yang berfokus pada gameplay.
- Menggunakan teknik penceritaan tanpa voice acting.
- Menjaga keselarasan antara cerita dan mekanik (ludonarrative harmony).

### 11.1 Cerita versus lore

- **Cerita (story)**: urutan peristiwa yang dialami karakter dan pemain. Biasanya memiliki awal, konflik, dan akhir.
- **Lore**: latar belakang dunia, sejarah, budaya, dan aturan dunia yang tidak selalu ditampilkan langsung kepada pemain.

Analogi: cerita adalah film yang ditonton, lore adalah seluruh dunia yang ada di balik layar.

### 11.2 Prinsip: gameplay lebih dahulu

Pada game yang berfokus pada gameplay, cerita bertugas untuk:

1. **Memberi alasan (motivasi)**: mengapa pemain melakukan hal yang ia lakukan.
2. **Memberi konteks**: dunia seperti apa, apa taruhannya.
3. **Memberi emosi tambahan**: penghargaan terhadap kemajuan, rasa kehilangan, rasa penasaran.

Cerita tidak boleh menghentikan gameplay terlalu lama. Aturan praktis: jika pemain sering ingin melewati adegan (skip), mungkin adegan terlalu panjang atau tidak relevan.

### 11.3 Teknik bercerita tanpa voice actor

Tanpa voice actor, Anda tetap punya banyak alat:

1. **Teks dialog singkat**: kotak dialog dengan kalimat pendek. Tulis seperti pesan chat, bukan novel.
2. **Environmental storytelling**: cerita lewat lokasi, objek, dan kondisi lingkungan. Contoh: bangunan hancur, jejak kaki, tulisan di dinding.
3. **Item description dan catatan**: deskripsi item, surat, jurnal, papan pengumuman. Bersifat opsional sehingga pemain yang tertarik bisa membaca.
4. **Visual dan animasi**: ekspresi karakter, gerak tubuh, dan transisi sinematik sederhana.
5. **Musik dan SFX**: tema musik untuk lokasi atau karakter, suara lingkungan yang menggambarkan suasana.
6. **Gibberish atau suara simbolik**: karakter berbicara dengan bunyi tidak berbahasa (blip per huruf, nada, atau gumaman) yang cocok dengan teks. Cara ini sering dipakai game indie dan memberi ciri khas.
7. **Gameplay sebagai narasi (mechanical storytelling)**: mekanik itu sendiri menyampaikan makna. Contoh: karakter yang makin lambat melambangkan kelelahan, atau musuh yang menjadi teman dapat menggambarkan rekonsiliasi.

### 11.4 Menulis teks untuk game

Pedoman:

- **Singkat**: satu kotak dialog idealnya hanya satu atau dua kalimat.
- **Jelas**: pemain sering membaca sambil terburu-buru.
- **Berkarakter**: setiap tokoh punya gaya bicara khas (formal, kasar, ceria, ragu-ragu).
- **Hindari tembok teks (exposition dump)**: sebarkan informasi sedikit demi sedikit.
- **Beri pilihan membaca lebih dalam**: lore panjang diletakkan di tempat opsional.
- **Rancang agar mudah dilokalisasi**: hindari lelucon yang hanya masuk akal dalam satu bahasa, dan jangan menggabungkan potongan kalimat di kode secara langsung karena menyulitkan terjemahan.

### 11.5 Struktur cerita sederhana untuk indie

Struktur tiga babak yang ringkas:

1. **Awal**: tunjukkan dunia dan karakter pemain, lalu satu peristiwa yang memicu perjalanan.
2. **Tengah**: pemain menghadapi rintangan yang makin sulit, belajar, dan menemukan fakta penting. Di sinilah sebagian besar gameplay berlangsung.
3. **Akhir**: konflik utama diselesaikan, hasilnya mencerminkan perjalanan pemain.

Untuk game kecil, satu premis yang jelas lebih baik daripada cerita rumit.

Contoh premis sederhana:

- "Seorang tukang kebun terakhir di kota yang tertutup kabut harus menanam kembali pohon penjaga sebelum kabut menelan seluruh kota." Premis ini langsung menghubungkan cerita ke mekanik (menanam, mengelola kabut, menjelajah).

### 11.6 Ludonarrative harmony dan dissonance

- **Harmony**: cerita dan mekanik saling mendukung. Contoh: cerita tentang bertahan hidup dengan sumber daya langka, dan mekaniknya memang membuat sumber daya langka.
- **Dissonance**: cerita dan mekanik bertentangan. Contoh: tokoh digambarkan sebagai penyayang, tetapi gameplay menghargai pembantaian tanpa pertimbangan.

Selalu tanyakan: "Apakah yang pemain lakukan sesuai dengan yang cerita katakan?"

### 11.7 Membangun lore dengan hemat

Pendekatan hemat untuk indie:

1. Tulis **lembar lore satu halaman**: dunia, tokoh utama, konflik, aturan dunia.
2. Tentukan **tiga sampai lima fakta inti** yang perlu diketahui pemain.
3. Tentukan **rahasia** yang bisa ditemukan secara opsional.
4. Jangan menulis seluruh sejarah dunia sebelum game jadi. Tulis seperlunya, tambahkan ketika dibutuhkan.

Pengetahuan lore yang tidak terlihat di game hampir tidak menambah nilai bagi pemain.

### 11.8 Pilihan dan percabangan cerita

Percabangan cerita mahal karena jumlah konten berlipat. Alternatif murah:

- Pilihan yang memengaruhi dialog sebentar tetapi alur kembali bertemu.
- Pilihan yang memengaruhi akhir lewat beberapa variabel sederhana.
- Pilihan berbasis gameplay (misalnya siapa yang diselamatkan menentukan siapa yang muncul di adegan akhir).

### Ringkasan

- Pada game berfokus gameplay, cerita dan lore melayani motivasi, konteks, dan emosi.
- Tanpa voice actor, gunakan teks singkat, lingkungan, item, musik, SFX, dan mekanik.
- Jaga keselarasan antara cerita dan mekanik.

### Latihan

1. Tulis premis game Anda dalam dua kalimat, lalu tunjukkan bagaimana premis itu terhubung ke mekanik utama.
2. Tulis lembar lore satu halaman dan tentukan tiga cara menyampaikan fakta inti tanpa dialog suara.
3. Tulis lima kalimat dialog untuk satu karakter dengan gaya bicara khas.

---

## Bab 12: UI, UX, Onboarding, dan Tutorial

### Tujuan belajar

- Memahami perbedaan UI dan UX.
- Merancang HUD dan menu yang jelas.
- Merancang onboarding yang baik.

### 12.1 UI dan UX

- **UI (User Interface)**: tampilan yang dilihat pemain, seperti tombol, bar nyawa, ikon, dan menu.
- **UX (User Experience)**: pengalaman menyeluruh saat berinteraksi, termasuk kemudahan memahami dan menggunakan.

UI yang cantik tetapi membingungkan adalah UX yang buruk.

### 12.2 Jenis UI dalam game

- **HUD (Heads-Up Display)**: informasi selama bermain (nyawa, amunisi, peta mini).
- **Menu**: menu utama, jeda, pengaturan, inventaris.
- **Diegetic UI**: UI yang menjadi bagian dunia game. Contoh: indikator amunisi tampil di senjata karakter.
- **Non-diegetic UI**: UI yang berada di luar dunia game, seperti bar nyawa di pojok layar.

### 12.3 Prinsip UI game

1. **Tampilkan hanya yang perlu**: terlalu banyak informasi membuat layar penuh.
2. **Prioritaskan informasi**: yang kritis (nyawa) harus lebih terlihat daripada yang sekunder.
3. **Konsisten**: warna, ikon, dan tata letak sama di seluruh game.
4. **Mudah dibaca**: ukuran teks cukup besar dan kontras tinggi, termasuk pada layar kecil.
5. **Tidak bergantung pada warna saja**: gunakan bentuk atau ikon bersama warna, untuk membantu pemain dengan buta warna.
6. **Respons langsung**: tombol dan menu memberi umpan balik saat disentuh atau dipilih.

### 12.4 Onboarding: tiga tahap awal

Onboarding adalah proses memperkenalkan pemain baru pada game. Menit-menit pertama sangat menentukan.

Prinsip:

1. **Tunjukkan, jangan ceritakan**: biarkan pemain mencoba mekanik secepat mungkin.
2. **Satu hal pada satu waktu**: jangan menjejalkan semua kontrol di awal.
3. **Ajarkan pada saat dibutuhkan (just-in-time)**: petunjuk muncul saat konteksnya relevan.
4. **Beri ruang aman**: area latihan tanpa risiko besar.
5. **Beri kesempatan mengulang**: petunjuk bisa dilihat kembali melalui menu.

### 12.5 Bentuk tutorial yang baik

- **Tutorial berbasis level**: level pengenalan yang mengajar lewat desain (lihat Bab 10).
- **Petunjuk kontekstual singkat**: ikon tombol yang muncul saat dekat objek interaktif.
- **Tutorial opsional**: pemain berpengalaman dapat melewatinya.
- **Hindari layar teks panjang** di awal permainan.

### 12.6 Kesalahan umum pemula

- Menaruh semua instruksi di layar pertama.
- Tutorial yang tidak bisa dilewati.
- Menu pengaturan yang tidak memiliki opsi dasar (volume, kontrol, bahasa).
- Teks terlalu kecil.
- Tidak ada tombol jeda yang mudah ditemukan.

### Ringkasan

- UI membantu pemain memahami situasi, UX memastikan pengalaman nyaman.
- Onboarding terbaik mengajar lewat bermain.
- Sediakan pengaturan dasar sejak awal.

### Latihan

1. Buat sketsa HUD untuk game Anda. Tandai tiga informasi paling penting.
2. Tulis rencana onboarding untuk 5 menit pertama game Anda: apa yang diajarkan, urutannya, dan caranya.

---

## Bab 13: Balancing

### Tujuan belajar

- Memahami arti balancing.
- Menggunakan tabel dan angka sederhana untuk menyetel game.
- Mengenali masalah umum seperti opsi dominan.

### 13.1 Apa itu balancing

Balancing adalah proses menyetel angka dan aturan agar game terasa adil, menantang, dan menyenangkan. Balancing bukan sekadar membuat semuanya sama kuat, melainkan memastikan setiap pilihan punya kelebihan dan kekurangan yang berarti.

### 13.2 Angka dasar yang perlu ditetapkan

Contoh untuk game aksi:

|Parameter|Contoh nilai awal|
|---|---|
|Nyawa pemain|5|
|Kerusakan serangan dasar|10|
|Nyawa musuh biasa|30|
|Waktu jeda serangan pemain|0,4 detik|
|Kerusakan musuh biasa ke pemain|1 nyawa per serangan|
|Waktu persiapan serangan musuh|0,6 detik|

Dari angka sederhana ini, Anda dapat menghitung: pemain butuh 3 serangan untuk mengalahkan musuh biasa, sekitar 1,2 detik. Musuh butuh 5 serangan untuk mengalahkan pemain. Dari sini Anda menilai apakah tantangan terasa pas.

### 13.3 Tips praktis balancing

1. **Gunakan spreadsheet**: simpan semua angka di satu tabel agar mudah diubah dan dibandingkan.
2. **Ubah satu variabel pada satu waktu**: supaya Anda tahu pengaruh tiap perubahan.
3. **Gunakan data, bukan perasaan semata**: catat berapa kali pemain mati di tiap area, berapa lama menyelesaikan level.
4. **Pakai angka yang mudah dipahami**: kelipatan 5 atau 10 mudah dihitung pemain.
5. **Tentukan "unit nilai"**: misalnya, 1 koin sama dengan 1 menit bermain, lalu hitung item berdasarkan itu.

### 13.4 Masalah umum

- **Strategi dominan**: satu pilihan jauh lebih unggul sehingga pilihan lain tidak pernah dipakai. Solusi: beri kekurangan, atau perkuat pilihan lain.
- **Snowballing**: yang unggul semakin unggul, yang tertinggal tidak bisa mengejar. Solusi: mekanisme pemulihan (catch-up).
- **Lonjakan kesulitan**: satu titik tiba-tiba jauh lebih sulit. Solusi: perhalus kurva.
- **Ekonomi tidak seimbang**: pemain kebanjiran atau kekurangan sumber daya. Solusi: sesuaikan source dan sink.

### 13.5 Balancing untuk game acak

Jika game memiliki unsur acak (drop item, tata letak level), pastikan:

- Ada batas bawah kualitas hasil acak (tidak terlalu buruk).
- Pemain punya cara memengaruhi hasil (pilihan, strategi).
- Acak digunakan untuk variasi, bukan untuk menentukan menang atau kalah semata.

### Ringkasan

- Balancing adalah penyetelan angka dan aturan berbasis data.
- Ubah satu variabel pada satu waktu dan catat hasilnya.
- Waspadai strategi dominan dan lonjakan kesulitan.

### Latihan

1. Buat spreadsheet berisi parameter utama game Anda dan hitung durasi pertarungan dasar.
2. Buat dua opsi (misalnya dua senjata) dan tulis kelebihan serta kekurangan masing-masing agar tidak ada yang dominan.

---

## Bab 14: Prototyping dan Playtesting

### Tujuan belajar

- Memahami pentingnya prototipe cepat.
- Melakukan playtest dengan benar.
- Mengolah masukan menjadi perbaikan desain.

### 14.1 Prototipe

Prototipe adalah versi kasar game untuk menguji ide. Tujuannya belajar, bukan membuat produk bagus.

Jenis prototipe:

- **Prototipe kertas**: kartu, dadu, papan sederhana. Sangat berguna untuk menguji sistem dan ekonomi.
- **Prototipe digital cepat**: dibuat dengan bentuk dasar (kotak, lingkaran), tanpa seni.
- **Prototipe vertical slice**: satu potongan kecil game yang terlihat dan terasa seperti produk akhir. Dibuat setelah ide terbukti.

Prinsip: bangun prototipe terkecil yang dapat menjawab satu pertanyaan desain.

Contoh pertanyaan desain: "Apakah menghindar dan menyerang bergantian terasa seru?" Prototipe: kotak sebagai pemain, kotak lain sebagai musuh, dua tombol, tanpa seni.

### 14.2 Aturan prototipe

1. Tidak ada seni final.
2. Kode boleh berantakan, karena prototipe akan dibuang atau ditulis ulang.
3. Fokus pada satu pertanyaan.
4. Batas waktu ketat: misalnya 1 sampai 3 hari.
5. Siap membuang jika hasilnya tidak seru.

### 14.3 Playtesting

Playtest adalah mengamati orang lain bermain game Anda untuk menemukan masalah.

Cara melakukan playtest yang baik:

1. **Pilih penguji yang belum pernah melihat game Anda**: teman atau keluarga boleh, tetapi lebih baik yang mewakili target pemain.
2. **Jangan menjelaskan**: biarkan mereka mencari tahu sendiri. Jika mereka bingung, itu informasi berharga.
3. **Amati, jangan membela**: catat apa yang mereka lakukan, bukan hanya apa yang mereka katakan.
4. **Catat titik sulit**: di mana mereka mati berulang, berhenti, bingung, atau tertawa.
5. **Tanyakan setelah bermain**: "Apa bagian yang paling kamu suka?", "Apa yang membingungkan?", "Apa yang ingin kamu lakukan tetapi tidak bisa?"
6. **Perhatikan perilaku lebih dari opini**: pemain sering tidak tahu solusi terbaik, tetapi perilaku mereka jujur.

### 14.4 Mengolah masukan

- Cari **pola**: jika satu dari sepuluh orang mengeluh, mungkin itu selera. Jika enam dari sepuluh tersangkut di titik yang sama, itu masalah desain.
- Pisahkan **masalah** dari **solusi yang disarankan**: pemain jago mengenali masalah, tetapi belum tentu solusinya tepat.
- Prioritaskan perbaikan yang paling berdampak pada pengalaman inti.
- Catat setiap perubahan dan alasannya.

### 14.5 Iterasi

Siklus iterasi:

```
Bangun -> Uji -> Amati -> Pelajari -> Ubah -> Bangun lagi
```

Semakin cepat siklus ini, semakin cepat game Anda membaik.

### Ringkasan

- Prototipe adalah alat belajar, bukan produk.
- Playtest: amati perilaku, jangan menjelaskan, cari pola.
- Iterasi cepat adalah kunci kualitas.

### Latihan

1. Tentukan satu pertanyaan desain dan buat prototipe terkecil untuk menjawabnya dalam maksimal 3 hari.
2. Lakukan playtest dengan tiga orang. Catat tiga masalah terbesar dan satu perbaikan untuk tiap masalah.

---

## Bab 15: Scope, Produksi, dan Bekerja Solo atau Tim Kecil

### Tujuan belajar

- Memahami scope dan bahayanya.
- Menyusun rencana produksi realistis.
- Mengelola waktu dan motivasi.

### 15.1 Scope creep

Scope adalah seluruh pekerjaan yang diperlukan untuk menyelesaikan game. Scope creep adalah pembengkakan scope karena terus menambah fitur. Ini penyebab utama proyek indie tidak selesai.

Aturan praktis untuk pemula:

1. Perkirakan waktu, lalu kalikan 2 sampai 3. Hampir semua proyek memakan waktu lebih lama dari perkiraan.
2. Mulai dengan game yang bisa selesai dalam 1 sampai 3 bulan.
3. Selesaikan beberapa game kecil sebelum mengerjakan game besar.
4. Fitur baru hanya boleh masuk jika ada fitur lain yang dikeluarkan.

### 15.2 Prioritas fitur: Must, Should, Could, Won't

Gunakan metode kategori:

- **Must have**: tanpa ini game tidak bisa dimainkan atau tidak punya inti.
- **Should have**: penting, tetapi game masih bisa rilis tanpanya.
- **Could have**: bagus jika ada waktu.
- **Won't have (kali ini)**: sengaja ditunda atau dibuang.

Tulis daftar fitur Anda dan kelompokkan. Kerjakan Must terlebih dahulu.

### 15.3 Tahapan produksi

1. **Konsep**: ide, pernyataan pengalaman, core loop.
2. **Prototipe**: uji inti gameplay.
3. **Pra-produksi**: tetapkan gaya visual, kebutuhan aset, rencana.
4. **Produksi**: bangun konten dan fitur.
5. **Alpha**: semua fitur utama ada, masih banyak bug.
6. **Beta**: fitur lengkap, fokus perbaikan bug dan penyetelan.
7. **Rilis**: publikasi game.
8. **Pasca-rilis**: pembaruan, perbaikan, dukungan komunitas.

### 15.4 Mengelola tugas

Gunakan alat sederhana:

- Papan tugas (Kanban): kolom "Akan dikerjakan", "Sedang dikerjakan", "Selesai". Bisa dengan alat digital atau kertas tempel.
- Pecah tugas besar menjadi tugas kecil yang selesai dalam setengah hari sampai dua hari.
- Tetapkan target mingguan yang realistis.

### 15.5 Bekerja solo

Kelebihan: bebas, cepat memutuskan. Tantangan: motivasi, keterampilan terbatas, tidak ada yang mengoreksi.

Tips:

- Jadwalkan waktu rutin, walau singkat.
- Bagikan perkembangan ke komunitas atau teman untuk akuntabilitas.
- Gunakan aset berlisensi (dengan syarat lisensi yang jelas) untuk mempercepat, tetapi tetap jaga konsistensi gaya.
- Fokus pada satu keunggulan: gameplay unik, gaya visual, atau cerita, bukan semuanya sekaligus.

### 15.6 Bekerja dalam tim kecil

- Tentukan peran dan tanggung jawab sejak awal.
- Gunakan kontrol versi (misalnya Git) untuk kode dan aset.
- Sepakati satu sumber kebenaran untuk dokumen desain.
- Komunikasikan keputusan desain secara tertulis.
- Tentukan cara menyelesaikan perbedaan pendapat (misalnya satu orang memiliki keputusan akhir desain).
- Bicarakan sejak awal soal pembagian pendapatan dan kepemilikan, dan catat dalam kesepakatan tertulis.

### 15.7 Menghindari burnout

- Istirahat yang cukup.
- Hindari lembur terus-menerus; produktivitas turun.
- Rayakan kemajuan kecil.
- Boleh membatalkan atau menunda proyek yang tidak lagi masuk akal; itu keputusan dewasa, bukan kegagalan.

### Ringkasan

- Scope creep adalah musuh utama indie.
- Prioritaskan fitur dengan Must, Should, Could, Won't.
- Selesaikan game kecil dulu, belajar, baru naik ke proyek besar.

### Latihan

1. Daftar semua fitur game Anda, lalu kelompokkan ke Must, Should, Could, Won't.
2. Buat rencana mingguan 4 minggu untuk versi terkecil game Anda.

---

## Bab 16: Dokumentasi Desain (One-Page Design dan GDD Ringan)

### Tujuan belajar

- Menulis dokumen desain yang singkat dan berguna.
- Menggunakan template yang bisa dipakai langsung.

### 16.1 Mengapa dokumentasi

Dokumentasi membantu Anda:

- Menjernihkan pikiran.
- Mengingat keputusan yang sudah dibuat.
- Berkomunikasi dengan tim.
- Mengukur kemajuan dan mengendalikan scope.

Dokumen desain bukan karya tulis. Ia harus ringkas dan terus diperbarui. Dokumen panjang yang tidak pernah dibaca tidak berguna.

### 16.2 One-Page Design

Ringkasan satu halaman berisi:

- **Nama game dan genre**
- **Pernyataan pengalaman** (satu atau dua kalimat)
- **Platform dan perspektif** (misalnya PC, 2D side-scroll)
- **Target pemain**
- **Core loop** (diagram atau daftar)
- **Mekanik utama** (maksimal 5)
- **Tantangan utama**
- **Progresi dan reward**
- **Cerita dan dunia** (premis singkat)
- **Gaya visual dan audio** (satu paragraf)
- **Ruang lingkup** (perkiraan durasi bermain dan jumlah level)

### 16.3 Template One-Page Design

Salin dan isi:

```
NAMA GAME:
GENRE:
PLATFORM:
PERSPEKTIF (2D/3D, sudut kamera):

PERNYATAAN PENGALAMAN:
(Contoh: Pemain merasa seperti ...)

TARGET PEMAIN:

CORE LOOP:
1.
2.
3.
4.

MEKANIK UTAMA (maks. 5):
-
-

TANTANGAN UTAMA:

PROGRESI DAN REWARD:

PREMIS CERITA (2 kalimat):

DUNIA DAN LORE (3 sampai 5 fakta inti):

GAYA VISUAL DAN AUDIO:

RUANG LINGKUP:
- Jumlah level/area:
- Perkiraan durasi bermain:
- Perkiraan waktu pengerjaan:

FITUR:
Must:
Should:
Could:
Won't:

RISIKO TERBESAR:
```

### 16.4 GDD ringan (Game Design Document)

Jika proyek bertambah besar atau melibatkan tim, kembangkan one-page menjadi GDD ringan. Bagian yang umum:

1. Ringkasan dan visi
2. Gameplay (core loop, mekanik, kontrol, kamera)
3. Level dan progresi
4. Musuh dan tantangan (tabel parameter)
5. Item dan ekonomi (tabel)
6. Cerita, dunia, dan karakter
7. UI dan alur menu
8. Seni dan audio (panduan gaya, daftar aset)
9. Rencana produksi dan jadwal
10. Risiko dan pertanyaan terbuka

Prinsip penulisan:

- Gunakan tabel dan diagram daripada paragraf panjang.
- Beri tanggal dan versi.
- Tandai bagian yang masih dugaan.
- Gunakan alat yang mudah disunting (dokumen bersama, wiki sederhana, atau file Markdown).

### 16.5 Tabel parameter

Tabel adalah bentuk dokumentasi paling berguna untuk game. Contoh tabel musuh:

|Nama|Nyawa|Kerusakan|Kecepatan|Pola serangan|Kelemahan|
|---|---|---|---|---|---|
|Slime|20|1|Lambat|Melompat ke arah pemain|Serangan beruntun|
|Pemanah|15|2|Sedang|Menembak setiap 2 detik|Dekat dan cepat|
|Penjaga|60|3|Lambat|Menyapu dengan perisai|Serangan dari belakang|

### Ringkasan

- Dokumentasi ringkas lebih berguna daripada panjang.
- One-Page Design cukup untuk memulai.
- Tabel parameter memudahkan balancing dan komunikasi.

### Latihan

1. Isi template One-Page Design untuk game Anda.
2. Buat tabel musuh atau item dengan minimal tiga baris.

---

## Bab 17: Memilih Engine dan Alur Kerja

### Tujuan belajar

- Memahami peran game engine.
- Memilih engine berdasarkan kebutuhan.
- Menyusun alur kerja sederhana.

### 17.1 Apa itu game engine

Game engine adalah perangkat lunak yang menyediakan fondasi pembuatan game: grafis, fisika, input, suara, editor level, dan lainnya. Dengan engine, Anda tidak perlu menulis semuanya dari nol.

### 17.2 Engine populer untuk indie

Beberapa pilihan yang umum digunakan developer indie:

|Engine|Kekuatan umum|Catatan|
|---|---|---|
|Godot|Ringan, open source, kuat untuk 2D, mendukung 3D|Bahasa skrip utama GDScript (mirip Python), juga mendukung C#|
|Unity|Ekosistem besar, banyak tutorial dan aset, 2D dan 3D|Bahasa C#|
|Unreal Engine|Kualitas grafis 3D tinggi, sistem visual scripting (Blueprint)|Lebih berat, cocok untuk 3D|
|GameMaker|Fokus 2D, cepat untuk prototipe|Bahasa skrip khusus (GML)|
|Construct, dan sejenisnya|Berbasis visual tanpa kode, cocok untuk belajar dan prototipe|Fleksibilitas lebih terbatas|

Catatan: fitur, versi, dan syarat lisensi setiap engine bisa berubah. Sebelum memilih, selalu periksa situs resmi masing-masing untuk informasi terbaru, terutama soal biaya dan ketentuan lisensi.

### 17.3 Cara memilih

Pertanyaan penuntun:

1. 2D atau 3D? Banyak engine bagus untuk keduanya, tetapi ada yang lebih unggul di salah satunya.
2. Seberapa nyaman Anda dengan kode? Visual scripting bisa membantu pemula.
3. Perangkat Anda cukup kuat? Engine 3D berat membutuhkan komputer yang lebih mumpuni.
4. Platform tujuan? PC, konsol, seluler, web.
5. Komunitas dan materi belajar? Pilih yang punya banyak tutorial dan komunitas aktif dalam bahasa yang Anda pahami.
6. Lisensi dan biaya? Pahami syarat penggunaan komersial.

Saran umum untuk pemula: pilih satu engine dan bertahan setidaknya sampai menyelesaikan dua atau tiga proyek kecil. Berpindah-pindah engine terlalu sering menghambat belajar.

### 17.4 Alat pendukung

- **Kontrol versi**: Git untuk menyimpan riwayat perubahan dan membuat cadangan.
- **Penyunting gambar 2D**: untuk sprite dan UI.
- **Perangkat 3D**: untuk model dan animasi (jika membuat game 3D).
- **Perangkat audio**: untuk SFX dan musik, atau gunakan aset berlisensi yang jelas.
- **Spreadsheet**: untuk balancing dan data.
- **Alat catatan dan tugas**: untuk dokumen desain dan papan tugas.

### 17.5 Alur kerja sederhana untuk proyek pertama

1. Tulis One-Page Design (Bab 16).
2. Buat prototipe inti dengan bentuk dasar (Bab 14).
3. Playtest dan perbaiki.
4. Bangun satu level lengkap sebagai vertical slice.
5. Tambah konten secara bertahap sesuai prioritas Must.
6. Poles: umpan balik, juice, UI, audio.
7. Uji akhir dan perbaiki bug.
8. Siapkan halaman toko, materi promosi, dan rilis.

### 17.6 Aset: buat, beli, atau gunakan ulang

- **Buat sendiri**: konsisten dan unik, tetapi memakan waktu.
- **Beli atau gunakan aset berlisensi**: lebih cepat, tetapi baca lisensi dengan teliti (boleh komersial atau tidak, perlu atribusi atau tidak).
- **Placeholder**: gunakan aset sementara selama prototipe, ganti nanti.

Selalu simpan catatan sumber dan lisensi setiap aset yang Anda pakai.

### Ringkasan

- Pilih satu engine sesuai kebutuhan dan kenyamanan, lalu konsisten.
- Cek informasi resmi untuk versi dan lisensi terbaru.
- Gunakan kontrol versi dan catat lisensi aset sejak awal.

### Latihan

1. Buat tabel perbandingan dua engine berdasarkan enam pertanyaan penuntun di atas.
2. Pasang engine pilihan Anda dan selesaikan satu tutorial dasar sampai karakter bisa bergerak.

---

## Bab 18: Hal yang Perlu Diperhatikan Developer Indie di Era 2026 dan Seterusnya

### Tujuan belajar

- Memahami tren dan pertimbangan terkini bagi developer indie.
- Menerapkan aksesibilitas dan etika desain sejak awal.

Catatan: bagian ini berisi pertimbangan umum. Kebijakan platform, lisensi, dan regulasi dapat berubah, jadi selalu periksa ketentuan resmi sebelum mengambil keputusan.

### 18.1 Aksesibilitas

Aksesibilitas berarti membuat game dapat dimainkan oleh sebanyak mungkin orang, termasuk pemain dengan keterbatasan penglihatan, pendengaran, motorik, atau kognitif. Ini juga memperluas pasar Anda.

Langkah dasar yang realistis untuk indie:

- **Kontrol dapat dikonfigurasi ulang** (remapping) dan mendukung beberapa perangkat input.
- **Ukuran dan kontras teks** yang dapat diatur, serta subtitle untuk dialog dan suara penting.
- **Tidak bergantung pada warna saja** untuk menyampaikan informasi.
- **Opsi mengurangi efek**: getaran layar, kilatan cahaya, dan gerak kamera berlebih.
- **Opsi bantuan kesulitan**: kecepatan game, nyawa tambahan, bantuan bidik.
- **Pengaturan volume terpisah** untuk musik, SFX, dan suara lingkungan.
- **Hindari tindakan yang menuntut tahan tombol lama** tanpa opsi alternatif.

Karena game ini tanpa voice actor dan banyak memakai teks, perhatikan khusus: ukuran font, kecepatan teks (opsi percepat atau lewati), dan kemudahan membaca.

### 18.2 Lokalisasi

Menyediakan terjemahan memperluas pasar. Pertimbangan:

- Rancang UI dengan ruang yang cukup untuk teks yang lebih panjang.
- Pisahkan teks dari kode (gunakan file atau tabel string).
- Hindari menggabungkan kalimat dari potongan di kode.
- Mulailah dengan satu atau dua bahasa tambahan yang paling relevan dengan target pemain Anda.
- Pertimbangkan bahasa Indonesia sebagai nilai tambah untuk pasar lokal.

Karena game tanpa voice acting, biaya lokalisasi menjadi jauh lebih murah (hanya teks).

### 18.3 Platform dan distribusi

Pilihan umum distribusi: toko PC, konsol, seluler, dan web. Pertimbangkan:

- Perangkat dan kontrol yang sesuai genre.
- Kebijakan dan biaya platform.
- Persyaratan teknis dan sertifikasi.
- Kebutuhan halaman toko: deskripsi, tangkapan layar, trailer, tag genre.

Mulailah dengan satu platform, lalu perluas jika sudah stabil.

### 18.4 Penggunaan alat AI dalam pengembangan

Alat berbasis kecerdasan buatan semakin banyak dipakai untuk membantu pekerjaan seperti kode, ide, atau aset. Hal yang perlu dipertimbangkan:

- **Kepemilikan dan lisensi**: pahami syarat penggunaan alat dan status hak atas hasil yang dihasilkan.
- **Kebijakan platform**: beberapa toko mewajibkan pengungkapan penggunaan AI pada konten tertentu. Periksa ketentuan resmi saat akan rilis.
- **Kualitas dan konsistensi**: hasil perlu ditinjau, diedit, dan disesuaikan dengan visi game Anda.
- **Etika dan kepercayaan pemain**: pertimbangkan reaksi komunitas dan dampak pada seniman.
- **Keterampilan inti**: alat membantu, tetapi pemahaman desain tetap tanggung jawab Anda. Desain gameplay dan penilaian pengalaman pemain tetap menjadi inti pekerjaan Anda.

### 18.5 Pemasaran dan komunitas

Game bagus tidak selalu ditemukan dengan sendirinya. Mulailah membangun audiens lebih awal:

- Bagikan perkembangan (GIF, tangkapan layar, catatan pengembangan).
- Buat halaman toko sedini mungkin agar pemain dapat menambahkan ke daftar keinginan.
- Ikuti game jam dan acara komunitas untuk belajar dan bertemu orang.
- Gunakan demo untuk mendapat masukan dan perhatian.
- Dengarkan komunitas, tetapi tetap pegang visi desain.

### 18.6 Etika desain

- Hormati waktu dan uang pemain.
- Hindari mekanisme yang dirancang untuk memanipulasi (kecanduan buatan, tekanan palsu).
- Jelaskan dengan jujur apa yang ditawarkan game.
- Lindungi data pemain jika Anda mengumpulkannya, dan patuhi aturan privasi yang berlaku.

### 18.7 Kesehatan dan keberlanjutan

Menjadi developer indie adalah perjalanan panjang. Jaga:

- Kesehatan fisik dan mental.
- Keuangan: pertimbangkan sumber pendapatan lain selama game dikembangkan.
- Ekspektasi realistis: sebagian besar game indie tidak langsung laris. Anggap setiap proyek sebagai pembelajaran dan portofolio.

### Ringkasan

- Aksesibilitas dan lokalisasi memperluas jangkauan dengan biaya yang wajar, terutama untuk game berbasis teks.
- Periksa kebijakan platform, lisensi, dan aturan terkait alat AI sebelum rilis.
- Etika desain dan kesehatan pribadi sama pentingnya dengan fitur game.

### Latihan

1. Buat daftar periksa aksesibilitas (minimal 8 butir) untuk game Anda dan tandai yang akan dikerjakan pada versi pertama.
2. Tulis rencana pemasaran sederhana: tiga hal yang akan Anda bagikan setiap minggu dan di mana.

---

## Proyek Latihan: Roadmap 12 Minggu

Rencana ini membantu Anda menerapkan seluruh isi buku dengan membuat satu game kecil yang selesai. Jam kerja per minggu bersifat fleksibel; yang penting konsisten.

### Minggu 1 sampai 2: Fondasi

- Selesaikan Bab 1 sampai 4.
- Tentukan genre, perspektif, dan pernyataan pengalaman.
- Tulis verb utama dan core loop.
- Isi One-Page Design (versi awal).
- Pilih engine dan selesaikan tutorial dasar.

Hasil: One-Page Design v1 dan engine terpasang.

### Minggu 3 sampai 4: Prototipe inti

- Bangun prototipe tanpa seni: gerak karakter dan satu mekanik utama.
- Terapkan teknik responsivitas (Bab 7 dan 8).
- Lakukan playtest pertama dengan tiga orang.

Hasil: prototipe yang bisa dimainkan 5 menit.

### Minggu 5 sampai 6: Perluas gameplay

- Tambahkan musuh atau rintangan dengan telegraphing.
- Buat tabel parameter dan lakukan balancing awal (Bab 13).
- Rancang kurva kesulitan 5 level atau fase.
- Playtest kedua.

Hasil: gameplay lengkap dengan tantangan yang terukur.

### Minggu 7 sampai 8: Level dan progresi

- Bangun blockout seluruh level.
- Terapkan pola Perkenalkan, Kembangkan, Uji, Putar.
- Tambahkan progresi dan reward dasar.
- Tulis premis cerita dan lembar lore satu halaman.

Hasil: seluruh level dapat dimainkan dengan seni sementara.

### Minggu 9 sampai 10: Cerita, UI, dan onboarding

- Tambahkan dialog singkat, catatan, atau elemen lingkungan yang bercerita.
- Buat HUD, menu, dan pengaturan dasar.
- Rancang onboarding 5 menit pertama.
- Tambahkan opsi aksesibilitas dasar.
- Playtest ketiga, fokus pada pemain baru.

Hasil: game utuh dengan UI dan alur awal yang jelas.

### Minggu 11: Poles

- Tambahkan juice: efek, SFX, musik.
- Ganti aset sementara dengan aset akhir (buat sendiri atau berlisensi).
- Perbaiki bug dan lonjakan kesulitan.

Hasil: kandidat rilis.

### Minggu 12: Rilis dan refleksi

- Siapkan halaman publikasi (misalnya situs game kecil atau toko), deskripsi, dan tangkapan layar.
- Bagikan game ke komunitas.
- Tulis refleksi: apa yang berhasil, apa yang gagal, apa yang akan diubah pada proyek berikutnya.

Hasil: game pertama Anda dirilis dan satu catatan refleksi.

### Prinsip selama 12 minggu

- Jika terlambat, buang fitur (bukan memperpanjang waktu tanpa batas).
- Selalu ada versi yang bisa dimainkan setiap akhir minggu.
- Simpan cadangan dan gunakan kontrol versi.

---

## Glosarium

|Istilah|Penjelasan singkat|
|---|---|
|Aksesibilitas|Upaya membuat game dapat dimainkan oleh sebanyak mungkin orang|
|Balancing|Penyetelan angka dan aturan agar game adil dan seru|
|Blockout / graybox|Pembuatan level dengan bentuk dasar tanpa seni, untuk menguji tata letak|
|Core loop|Rangkaian tindakan inti yang diulang pemain|
|Coyote time|Jeda singkat setelah meninggalkan tepi platform saat pemain masih bisa melompat|
|Diegetic UI|UI yang menjadi bagian dari dunia game|
|Dinamika|Perilaku yang muncul dari interaksi antara mekanik dan pemain|
|Environmental storytelling|Bercerita lewat lingkungan dan objek|
|Estetika (MDA)|Respons emosional pemain terhadap game|
|Flow|Kondisi tenggelam dalam aktivitas saat tantangan seimbang dengan keterampilan|
|GDD|Game Design Document, dokumen yang menjelaskan desain game|
|Game feel|Sensasi taktil saat mengendalikan sesuatu dalam game|
|Graybox|Lihat blockout|
|HUD|Informasi yang tampil di layar selama bermain|
|Hit stop|Jeda sangat singkat saat serangan mengenai sasaran untuk memberi bobot|
|Input buffering|Menyimpan input sebentar agar dijalankan saat aksi memungkinkan|
|Juice|Lapisan efek yang memperkuat rasa memuaskan dari tindakan|
|Lore|Latar belakang dan sejarah dunia game|
|Lokalisasi|Penyesuaian game ke bahasa dan budaya lain|
|Ludonarrative harmony|Keselarasan antara cerita dan mekanik|
|MDA|Mechanics, Dynamics, Aesthetics; kerangka berpikir desain|
|Mekanik|Aturan dan komponen dasar dalam game|
|Onboarding|Proses memperkenalkan pemain baru pada game|
|Pilihan bermakna|Pilihan dengan konsekuensi jelas dan berbeda|
|Prototipe|Versi kasar game untuk menguji ide|
|Playtest|Mengamati orang bermain untuk menemukan masalah|
|Remapping|Mengubah pengaturan tombol kontrol|
|Scope|Seluruh lingkup pekerjaan sebuah proyek|
|Scope creep|Pembengkakan scope karena terus menambah fitur|
|Sink|Tempat sumber daya habis dalam ekonomi game|
|Source|Tempat sumber daya diperoleh dalam ekonomi game|
|Telegraphing|Memberi tanda peringatan sebelum suatu kejadian|
|UI|Tampilan antarmuka yang dilihat pemain|
|UX|Pengalaman menyeluruh pemain saat berinteraksi|
|Vertical slice|Potongan kecil game yang terlihat dan terasa seperti produk akhir|
|Verb|Kata kerja utama yang dilakukan pemain dalam game|

---

## Bacaan dan Sumber Belajar Lanjutan

Daftar berikut adalah rekomendasi umum. Ketersediaan, edisi, dan harga dapat berbeda; periksa sumber resminya.

### Buku

- Jesse Schell, "The Art of Game Design: A Book of Lenses". Pengantar luas dengan pendekatan "lensa" untuk menilai desain.
- Raph Koster, "A Theory of Fun for Game Design". Membahas mengapa game menyenangkan dari sudut pandang belajar.
- Steve Swink, "Game Feel". Membahas kontrol, respons, dan sensasi bermain secara mendalam.
- Katie Salen dan Eric Zimmerman, "Rules of Play". Buku teori game yang lebih akademis dan mendalam.
- Scott Rogers, "Level Up! The Guide to Great Video Game Design". Praktis, ramah pemula, kaya contoh level dan karakter.
- Robert Nystrom, "Game Programming Patterns". Berguna jika Anda juga ingin memahami sisi kode dengan rapi.

### Makalah dan ceramah

- Robin Hunicke, Marc LeBlanc, Robert Zubek, "MDA: A Formal Approach to Game Design and Game Research". Dasar kerangka MDA.
- Ceramah di Game Developers Conference (GDC), banyak yang tersedia gratis di kanal GDC di YouTube. Cari topik seperti game feel, level design, dan postmortem game indie.

### Cara belajar efektif

1. Mainkan banyak game dengan sudut pandang analitis: catat core loop, verb, kurva kesulitan, dan cara onboarding.
2. Baca postmortem (catatan pasca-proyek) dari developer indie untuk memahami keputusan dan kesalahan nyata.
3. Ikuti game jam: batas waktu singkat melatih Anda menyelesaikan proyek dan memangkas scope.
4. Bagikan karya Anda sejak dini dan terima masukan.
5. Selesaikan game kecil sebanyak mungkin. Pengalaman menyelesaikan proyek adalah guru terbaik.

---

## Penutup

Game design adalah keterampilan yang tumbuh lewat praktik. Tidak ada rumus tunggal untuk membuat game yang pasti disukai, tetapi ada kebiasaan yang membantu: berpikir dari pengalaman pemain, membuat prototipe kecil, menguji dengan orang lain, membuang yang tidak berhasil, dan menyelesaikan proyek.

Mulailah dari yang kecil. Satu mekanik yang dipoles lebih berharga daripada sepuluh fitur yang setengah jadi. Cerita dan lore memperkaya, tetapi gameplay adalah alasan pemain datang dan bertahan.

Selamat belajar dan selamat membuat game.