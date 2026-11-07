# Panduan Game Developer Indie 2026 dan Seterusnya

## Dari Ide sampai Game yang Laku, Adiktif, Unik, dan Dikenal

**Cakupan buku:** game indie 2D dan 3D, ada cerita dan lore tetapi fokus utama di gameplay, tanpa voice actor, dan fokus ke game offline (single player, bukan online).

**Untuk siapa:** pemula yang ingin membangun karier atau studio game indie, dengan target jual di Steam.

**Gaya penulisan:** bahasa Indonesia, istilah teknis dijelaskan dengan bahasa sederhana.

**Catatan waktu:** data pasar dan fitur Steam dalam buku ini dikumpulkan per November 2026. Platform berubah cepat. Setiap kali ada angka atau aturan Steam, cek ulang di dokumentasi resmi Steamworks sebelum mengambil keputusan.

---

## Daftar Isi

1. Bab 0: Baca Ini Dulu, Realitas yang Jujur
2. Bab 1: Peta Industri dan Steam di 2026
3. Bab 2: Fondasi Desain Gameplay
4. Bab 3: Membuat Game yang Membuat Orang Lupa Waktu
5. Bab 4: Keunikan dan Ciri Khas Game Anda
6. Bab 5: Cerita dan Lore yang Melayani Gameplay (Tanpa Voice Actor)
7. Bab 6: Memilih 2D atau 3D, Engine, dan Alat Kerja
8. Bab 7: Produksi: Scope, Prototype, dan Vertical Slice
9. Bab 8: Playtest, Balancing, dan Kualitas Teknis
10. Bab 9: Marketing di Steam Sebelum Rilis
11. Bab 10: Hari Peluncuran dan Dua Minggu Pertama
12. Bab 11: Setelah Rilis, Cara Bertahan di Daftar Teratas
13. Bab 12: Menuju Penghargaan dan Pengakuan
14. Bab 13: Bisnis, Uang, dan Legal
15. Bab 14: Roadmap 24 Bulan untuk Pemula
16. Bab 15: Checklist Ringkas dan Glosarium
17. Daftar Sumber

---

# Bab 0: Baca Ini Dulu, Realitas yang Jujur

Sebelum masuk teknik, ada beberapa hal yang harus Anda pahami supaya tidak salah arah. Bab ini penting karena banyak pemula gagal bukan karena kurang skill, tetapi karena target dan strateginya keliru.

## 0.1 Tujuan Anda dan apa yang benar-benar bisa dikendalikan

Tujuan yang Anda tulis adalah: banyak yang beli, banyak yang main, adiktif, masuk award, unik, dan selalu berada di Top Sellers serta Most Played Steam tanpa pernah hilang.

Enam tujuan pertama bisa dikejar dengan strategi yang jelas. Tujuan terakhir ("selalu ada, tidak pernah hilang") perlu diluruskan.

**Kenapa "tidak pernah hilang" tidak realistis sebagai janji:**

- Daftar Top Sellers dan Most Played di Steam bersifat persaingan langsung. Posisi Anda bergantung pada game lain, termasuk game dari studio besar dan game yang sedang viral.
- Most Played dihitung dari jumlah pemain bersamaan (concurrent players). Game offline single player cenderung punya puncak pemain yang tajam saat rilis dan diskon, lalu turun. Itu normal dan terjadi pada hampir semua game.
- Tidak ada developer di dunia yang bisa menjamin posisinya. Bahkan game besar keluar masuk daftar.

**Cara berpikir yang lebih sehat dan bisa dieksekusi:**

|Target awal (tidak terukur)|Target pengganti (terukur dan bisa dikejar)|
|---|---|
|Selalu masuk Top Sellers|Masuk Top Sellers saat rilis, saat diskon besar, dan saat update besar|
|Selalu masuk Most Played|Punya basis pemain setia yang main berulang kali (retensi tinggi)|
|Tidak pernah hilang|Punya jadwal momentum: rilis, update, diskon musiman, DLC, event komunitas|
|Game laku keras|Wishlist tinggi sebelum rilis, konversi toko bagus, ulasan positif|

Buku ini menyusun strategi untuk mendekati hasil terbaik secara realistis. Anda tetap bisa bermimpi besar, tetapi kerjakan dengan metrik.

## 0.2 Gambaran jujur tentang pasar

- Ribuan game masuk Steam setiap tahun. Sumber analisis 2026 menyebut angka di atas 14.000 game per tahun. Artinya game Anda bukan hanya harus bagus, tetapi harus bisa ditemukan.
- Banyak game yang ulasannya bagus tetap tidak balik modal karena tidak ditemukan pemain. Masalah ini sering disebut discovery problem.
- Data Steam Next Fest Februari 2026 menunjukkan bahwa game median hanya mendapat ratusan wishlist selama festival, sementara kelompok teratas bisa mendapat ribuan sampai puluhan ribu.

Pesan intinya: **membuat game bagus itu syarat minimum, bukan jaminan.** Marketing, ciri khas, dan jadwal kerja yang disiplin harus berjalan bersamaan sejak hari pertama, bukan setelah game selesai.

## 0.3 Tiga kunci yang dibahas sepanjang buku

1. **Game yang layak dimainkan berulang kali** (desain gameplay, retensi, replayability).
2. **Game yang mudah dibedakan** dari ribuan game lain (ciri khas dan positioning).
3. **Game yang bisa ditemukan** (store page, wishlist, demo, festival, komunitas, jadwal update).

Kalau salah satu hilang, hasilnya timpang. Game bagus tapi tidak unik akan tenggelam. Game unik tapi tidak punya halaman toko yang menarik tidak akan dilirik. Game dengan marketing besar tapi gameplay biasa akan mendapat ulasan buruk dan hilang cepat.

## 0.4 Cara membaca buku ini

- Jika Anda pemula total: baca berurutan, kerjakan latihan di akhir tiap bab.
- Jika sudah pernah membuat prototype: fokus ke Bab 3, 4, 9, 10, 11.
- Siapkan satu buku catatan (atau file teks) untuk mencatat ide, keputusan desain, dan hasil playtest.

---

# Bab 1: Peta Industri dan Steam di 2026

## 1.1 Mengapa Steam

Steam masih menjadi toko utama untuk game PC. Beberapa sumber menyebut pangsa pasarnya sekitar 75 persen untuk distribusi game PC. Angka ini perkiraan dan bisa bergeser, tetapi arahnya jelas: untuk game offline PC, Steam adalah target utama.

Platform lain tetap bisa dipakai sebagai tambahan:

- itch.io: bagus untuk prototype, demo, game jam, dan komunitas awal. Pembagian hasil fleksibel.
- Epic Games Store: bagi hasil lebih kecil untuk developer, tetapi seleksi lebih ketat.
- GOG: fokus game tanpa DRM.
- Konsol (Switch, PlayStation, Xbox): bisa jadi target porting setelah game sukses di PC.

## 1.2 Biaya dan bagi hasil Steam (per 2026)

Berdasarkan sumber yang memeriksa dokumentasi Steamworks di tahun 2026:

- **Biaya Steam Direct:** 100 dolar AS per game (per aplikasi, bukan per akun). Biaya ini dikembalikan (recoup) setelah game mencapai 1.000 dolar AS pendapatan kotor yang disesuaikan.
- **Bagi hasil:** Valve mengambil 30 persen untuk pendapatan sampai 10 juta dolar AS, lalu turun menjadi 25 persen sampai 50 juta dolar AS, lalu 20 persen di atasnya. Tarif ini berlaku per game.
- Demo, soundtrack, dan DLC tidak membutuhkan biaya Steam Direct tersendiri.
- Anda harus mengisi data pajak dan rekening bank di Steamworks sebelum bisa menerima pembayaran.

Contoh hitungan sederhana untuk game harga 20 dolar AS: Steam mengambil sekitar 6 dolar AS, Anda menerima sekitar 14 dolar AS, sebelum dikurangi pajak dan refund. Pajak di negara Anda berlaku lagi di atasnya (lihat Bab 13).

Selalu cek ulang angka ini di dokumentasi resmi Steamworks sebelum menyusun anggaran.

## 1.3 Cara Steam menampilkan game Anda

Steam tidak menampilkan semua game yang sama kepada semua orang. Tampilan toko dipersonalisasi. Ada dua jenis eksposur:

1. **Algoritmik dan personal:** Discovery Queue, rekomendasi untuk Anda, game serupa, hasil pencarian, dan sebagainya.
2. **Curated (dipilih manual):** halaman utama, event, dan sale khusus.

Hal penting yang sering disalahpahami pemula:

- Menurut pernyataan Valve yang dirangkum banyak analis, **jumlah wishlist saja bukan faktor visibilitas algoritmik umum**, dengan pengecualian seperti tab Popular Upcoming. Wishlist tetap sangat penting karena pemilik wishlist mendapat notifikasi saat rilis dan saat diskon, dan notifikasi itu membuat peluncuran Anda punya tenaga awal.
- Pembelian dan waktu bermain dalam dua minggu pertama setelah rilis disebut banyak analisis sebagai penentu besar visibilitas selanjutnya. Artinya awal peluncuran adalah momen kritis.
- Visibilitas tidak bisa dibeli di Steam. Yang bisa Anda lakukan adalah membuat game dan halaman toko yang memicu perilaku yang disukai algoritma: orang klik, menonton trailer, masuk wishlist, membeli, memainkan, dan tidak refund.

Sinyal yang diperkirakan dibaca Steam (bukan daftar resmi, tetapi arah yang konsisten dari berbagai analisis):

- Rasio klik terhadap tayangan (impression).
- Seberapa banyak orang menonton trailer dan menambah wishlist dari halaman toko.
- Rasio pembelian terhadap kunjungan halaman.
- Waktu bermain dan tingkat refund setelah rilis.
- Kecocokan tag dengan minat pemain.

## 1.4 Peran tag dan halaman toko

Tag adalah label genre dan fitur (misalnya Roguelite, Pixel Graphics, Cozy, Metroidvania). Steam memakai tag untuk memutuskan siapa yang diperlihatkan game Anda. Tag yang salah menarik pemain yang salah, lalu menghasilkan ulasan buruk dan refund tinggi.

Aturan praktis: pilih tag yang jujur menggambarkan game Anda, urutkan dari yang paling mewakili, dan bandingkan dengan game kompetitor yang sukses di niche yang sama.

## 1.5 Latihan Bab 1

1. Buka Steam, cari 10 game indie offline yang menurut Anda mirip dengan ide Anda. Catat tag teratas, harga, jumlah ulasan, dan persentase ulasan positif.
2. Hitung perkiraan: kalau game Anda harga 10 dolar AS dan terjual 5.000 kopi, berapa yang Anda terima setelah potongan Steam 30 persen?

---

# Bab 2: Fondasi Desain Gameplay

Karena fokus Anda gameplay, bab ini adalah inti pembelajaran. Semua teknik marketing tidak akan menolong kalau gameplay tidak enak dimainkan berulang kali.

## 2.1 Core loop

**Core loop** adalah siklus aksi terpendek yang diulang pemain sepanjang game. Contoh sederhana:

- Roguelite aksi: masuk ruangan, bertarung, ambil hadiah, pilih upgrade, masuk ruangan berikutnya.
- Game farming: tanam, rawat, panen, jual, beli bibit baru, tanam lagi.
- Game puzzle platformer: eksplorasi, lihat teka-teki, coba solusi, dapat akses area baru.

Core loop yang bagus punya tiga sifat:

1. **Jelas:** pemain paham apa yang harus dilakukan dalam 30 detik pertama.
2. **Memuaskan per ulangan:** satu putaran loop sudah terasa menyenangkan, bukan hanya hasil akhirnya.
3. **Bisa berkembang:** ada variasi dan kedalaman supaya putaran ke-100 tidak sama membosankan dengan putaran ke-1.

Cara menguji: bangun prototype tanpa grafis bagus (kotak dan lingkaran sudah cukup). Jika loop sudah menyenangkan dengan grafis jelek, loop itu kuat. Jika baru menyenangkan setelah dipoles, kemungkinan loop-nya lemah.

## 2.2 Hirarki loop

Game yang membuat orang bertahan lama biasanya punya beberapa lapis loop:

|Lapisan|Durasi|Contoh|
|---|---|---|
|Micro loop|detik|Gerak, lompat, tembak, pukul, rasakan "enak"|
|Core loop|menit|Satu pertempuran, satu ruangan, satu panen|
|Meta loop|puluhan menit sampai jam|Satu run, satu level, satu hari dalam game|
|Long-term loop|puluhan jam|Progres permanen, membuka area, build baru, ending berbeda|

Setiap lapisan memberi alasan berbeda untuk lanjut bermain. Banyak game gagal karena hanya kuat di satu lapisan.

## 2.3 Pilar desain

**Pilar desain** adalah 3 sampai 5 kalimat yang mendefinisikan game Anda dan dipakai untuk menolak ide yang tidak cocok. Contoh:

1. Setiap keputusan harus punya konsekuensi nyata.
2. Pemain selalu merasa kuat tetapi tidak pernah merasa aman.
3. Tidak ada teks tutorial panjang. Pemain belajar dengan melakukan.

Tulis pilar sebelum menulis kode. Setiap fitur baru ditanyai: apakah ini mendukung pilar? Jika tidak, jangan dibuat. Ini mencegah scope creep (fitur melebar tak terkendali).

## 2.4 Kerangka MDA

Kerangka MDA membantu memahami hubungan antara aturan dan perasaan pemain:

- **Mechanics (mekanik):** aturan dan sistem. Contoh: lompat dua kali, stamina, inventori.
- **Dynamics (dinamika):** perilaku yang muncul saat pemain berinteraksi dengan mekanik. Contoh: pemain mulai menghemat stamina untuk melarikan diri.
- **Aesthetics (estetika):** emosi yang dirasakan. Contoh: tegang, bangga, penasaran.

Anda mendesain dari mekanik, tetapi pemain mengalami dari estetika. Selalu tanyakan: perasaan apa yang ingin saya hadirkan, lalu mekanik apa yang menghasilkannya?

## 2.5 Flow: tantangan yang pas

Konsep **flow** menyatakan orang paling larut ketika tantangan sebanding dengan kemampuan. Terlalu mudah membuat bosan, terlalu sulit membuat frustrasi.

Cara menerapkan:

- Naikkan kesulitan bertahap (kurva kesulitan berbentuk gigi gergaji: naik, lalu jeda istirahat, naik lagi sedikit lebih tinggi).
- Beri umpan balik instan: suara, efek visual, getaran kamera saat pemain berhasil atau gagal.
- Berikan tujuan jangka pendek yang jelas: "kalahkan musuh ini", "capai pintu itu".
- Beri pilihan tingkat kesulitan atau opsi aksesibilitas supaya lebih banyak pemain bisa masuk.

## 2.6 Juice: rasa enak dari detail kecil

**Juice** adalah semua efek kecil yang membuat aksi terasa memuaskan. Dua game dengan mekanik identik bisa terasa sangat berbeda karena juice.

Contoh teknik juice yang murah dan efektif:

- Screen shake kecil saat pukulan mendarat.
- Hit stop: jeda 50 sampai 100 milidetik saat serangan kena, supaya terasa berbobot.
- Partikel kecil saat melompat atau mendarat.
- Suara bervariasi (jangan satu file suara yang diulang persis).
- Animasi squash and stretch pada karakter.
- Tampilan angka damage atau koin yang melonjak.

Contoh sederhana (pseudocode bergaya GDScript) untuk hit stop:

```gdscript
func apply_hit_stop(duration_ms: int) -> void:
    Engine.time_scale = 0.05
    await get_tree().create_timer(duration_ms / 1000.0, true, false, true).timeout
    Engine.time_scale = 1.0
```

Catatan: ini hanya ilustrasi. Pelajari fungsi yang tepat di dokumentasi engine yang Anda pakai.

Tips: kerjakan juice secara bertahap setelah mekanik inti stabil, tetapi jangan menunggu sampai akhir proyek.

## 2.7 Tutorial yang tidak terasa seperti tutorial

Tiga puluh menit pertama menentukan apakah pemain bertahan atau refund. Prinsipnya:

- Ajarkan satu hal pada satu waktu dalam situasi aman.
- Biarkan pemain melakukan, bukan membaca.
- Gunakan desain level untuk mengajar (misalnya satu celah yang hanya bisa dilewati dengan lompat ganda, pemain belajar tanpa teks).
- Jangan menghalangi pemain berpengalaman. Beri opsi lewati.

## 2.8 Latihan Bab 2

1. Tulis core loop game Anda dalam satu kalimat dan satu diagram sederhana.
2. Tulis tiga pilar desain.
3. Buat prototype kotak dan lingkaran selama 1 minggu. Minta 3 orang mencoba. Catat di menit ke berapa mereka mulai bosan atau bingung.

---

# Bab 3: Membuat Game yang Membuat Orang Lupa Waktu

Anda ingin game yang adiktif sampai pemain lupa waktu. Bab ini membahas psikologi di balik fenomena "satu giliran lagi" (one more turn). Ada juga garis etika yang perlu Anda pahami supaya game Anda dicintai, bukan dibenci.

## 3.1 Perbedaan engagement sehat dan manipulasi

Ada dua jenis "adiktif":

- **Engagement sehat:** pemain sangat menikmati, ingin kembali karena merasa puas, merasa berkembang, dan tidak menyesal setelah bermain.
- **Manipulasi (dark pattern):** game memanfaatkan kelemahan psikologis seperti rasa takut ketinggalan, timer yang menekan, atau mekanisme judi untuk memaksa pemain bermain atau membayar.

Untuk game offline premium (sekali beli), strategi manipulatif sebenarnya tidak perlu dan merugikan. Pemain yang merasa dimanipulasi menulis ulasan buruk dan refund. Fokus Anda adalah **engagement sehat**: game yang begitu menyenangkan sehingga orang rela bermain berjam-jam dan merekomendasikannya.

## 3.2 Mekanisme psikologi yang dipakai game hebat

### a. Tujuan jangka pendek yang bertumpuk

Pemain selalu punya beberapa tujuan kecil yang hampir selesai. Contoh: "tinggal satu level lagi untuk upgrade", "satu bos lagi untuk membuka area baru". Ketika satu tujuan selesai, tujuan baru sudah muncul. Inilah dasar dari "satu putaran lagi".

### b. Rasa kemajuan nyata

Pemain harus merasakan bahwa mereka menjadi lebih kuat atau lebih mahir. Dua jenis kemajuan:

- **Kemajuan karakter:** statistik naik, senjata baru, skill baru.
- **Kemajuan pemain (mastery):** pemain sendiri menjadi lebih jago. Ini yang paling kuat dan paling awet. Pemain yang merasa "saya makin jago" akan terus kembali.

### c. Hadiah yang bervariasi (variable reward)

Hadiah yang tidak selalu sama membuat pemain penasaran. Contoh: loot acak, kombinasi upgrade acak, ruangan prosedural. Perhatian: gunakan variasi untuk menambah rasa eksplorasi dan strategi, bukan mekanisme judi berbayar.

### d. Pilihan yang bermakna

Setiap kali pemain memilih (upgrade A atau B, jalur kiri atau kanan), pilihan itu harus terasa penting dan punya trade-off. Pilihan palsu (satu opsi jelas lebih baik) membosankan.

### e. Rasa hampir menang (near miss) dan belajar dari kegagalan

Kegagalan yang adil membuat pemain berpikir "kalau tadi saya lakukan begini, pasti bisa". Pastikan kematian atau kekalahan terasa karena kesalahan pemain, bukan karena sistem curang. Muat ulang cepat (restart dalam beberapa detik) sangat penting.

### f. Ritme: tegang lalu lega

Rancang gelombang ketegangan dan istirahat. Setelah pertarungan berat, beri ruang aman, hadiah, atau momen cerita. Ketegangan tanpa jeda melelahkan, jeda tanpa ketegangan membosankan.

### g. Rasa memiliki dan ekspresi diri

Pemain lebih lama bertahan di game yang memungkinkan mereka membuat sesuatu yang "milik mereka": base, build karakter unik, dekorasi, gaya bermain sendiri. Ini sering menjadi alasan game cozy dan sandbox sangat awet.

### h. Rasa penasaran dan misteri

Teka-teki, rahasia tersembunyi, dan potongan lore yang tersebar membuat pemain ingin tahu lebih banyak. Ini juga cara menyampaikan cerita tanpa mengganggu gameplay (Bab 5).

## 3.3 Struktur sesi bermain untuk game offline

Pikirkan seberapa panjang satu sesi dan bagaimana pemain kembali besok.

- **Sesi pendek yang bisa diulang:** roguelite dengan satu run 20 sampai 40 menit memudahkan "satu run lagi".
- **Titik berhenti alami:** simpan otomatis (autosave) yang sering supaya pemain tidak takut berhenti, namun tetap ingin lanjut.
- **Kait kembali (hook to return):** akhir sesi menyisakan tujuan yang menggantung ("besok saya coba bos itu dengan build berbeda").

## 3.4 Replayability: kunci retensi di game offline

Karena tidak ada multiplayer, retensi game offline dibangun dari **replayability** (nilai main ulang). Cara umum:

|Teknik|Penjelasan|Contoh genre|
|---|---|---|
|Generasi prosedural|Level atau isi game dibuat acak dengan aturan|Roguelike, roguelite|
|Build dan sinergi|Banyak kombinasi upgrade yang saling memperkuat|Deckbuilder, roguelite|
|Meta-progression|Progres permanen yang membuka opsi baru antar run|Roguelite|
|Banyak jalur dan ending|Pilihan membuat cerita dan gameplay berubah|RPG, game naratif|
|Mode tambahan|New Game Plus, mode tantangan, mode harian dengan seed tetap|Banyak genre|
|Sistem mastery|Skill ceiling tinggi, speedrun, tantangan sendiri|Platformer, aksi|
|Dukungan mod|Komunitas membuat konten tambahan|Simulasi, sandbox|

Untuk pemula, roguelite atau game berbasis run sering menjadi pilihan cerdas karena konten yang dibuat sedikit bisa dimainkan berkali-kali. Namun jangan memilih genre hanya karena populer. Pilih yang Anda mampu selesaikan dan yang cocok dengan ide Anda.

## 3.5 Onboarding dan pengalaman 10 menit pertama

Ulasan negatif paling sering datang dari kebingungan di awal atau pengalaman awal yang membosankan. Checklist:

- Dalam 60 detik pertama pemain sudah melakukan sesuatu yang menyenangkan.
- Dalam 10 menit pertama pemain sudah melihat "inti keunikan" game Anda.
- Dalam 30 menit pertama pemain sudah punya alasan kuat untuk lanjut (tujuan, misteri, atau kemajuan terasa).
- Tidak ada dinding teks panjang.

## 3.6 Hal yang membuat pemain berhenti

Kenali penyebab berhenti supaya bisa dihindari:

- Kontrol tidak responsif atau kamera mengganggu.
- Kesulitan melonjak tiba-tiba atau terasa tidak adil.
- Terlalu banyak pekerjaan berulang tanpa variasi (grinding membosankan).
- Bug yang menghilangkan progres (kehilangan save sangat fatal).
- Tidak jelas harus ke mana.
- Performa buruk (frame rate turun, loading lama).
- Konten habis terlalu cepat tanpa alasan main ulang.

## 3.7 Etika: pemain dan kesehatan

Game yang sangat menarik bisa membuat orang bermain berlebihan. Tanggung jawab developer yang baik:

- Jangan menambahkan mekanisme yang menghukum pemain karena berhenti bermain.
- Jangan memakai mekanisme berbayar acak (loot box) di game premium.
- Beri titik simpan yang ramah supaya pemain bisa berhenti kapan saja.
- Pertimbangkan pengingat istirahat opsional atau fitur aksesibilitas seperti pause kapan saja.

Ini bukan hanya soal moral. Reputasi baik membuat ulasan positif, dan ulasan positif adalah mesin marketing terbaik Anda.

## 3.8 Latihan Bab 3

1. Gambarkan empat lapis loop game Anda (micro, core, meta, long-term).
2. Daftar tiga alasan pemain kembali besok setelah bermain hari ini.
3. Mainkan satu game favorit Anda dan catat tiap momen Anda ingin "satu lagi". Apa pemicunya?

---

# Bab 4: Keunikan dan Ciri Khas Game Anda

Untuk menarik perhatian di tengah ribuan game, game Anda harus memiliki sesuatu yang bisa dijelaskan singkat dan langsung terasa berbeda. Bab ini membahas cara menemukan dan memvalidasi ciri khas tersebut.

## 4.1 USP dan hook

**USP (Unique Selling Point)** adalah alasan utama orang memilih game Anda daripada game lain. **Hook** adalah ide yang membuat orang langsung tertarik dalam satu kalimat.

Ujian satu kalimat: Anda harus bisa menjelaskan game dalam satu kalimat yang membuat orang berkata "oh, menarik".

Contoh format:

> "Sebuah [genre] di mana [mekanik unik], sehingga [pengalaman yang dirasakan pemain]."

Contoh latihan (fiktif): "Sebuah roguelite aksi di mana setiap senjata yang kamu pakai menghilang selamanya setelah satu pertarungan, sehingga kamu terus dipaksa beradaptasi."

Jika kalimat Anda terdengar seperti "game aksi petualangan dengan grafis bagus dan cerita menarik", itu belum unik. Hampir semua game mengaku seperti itu.

## 4.2 Cara menemukan ciri khas

### a. Kombinasi dua hal yang jarang disatukan

Banyak game unik lahir dari menggabungkan dua genre atau dua tema yang belum pernah dipasangkan. Contoh pola: genre A + tema B + satu aturan khusus. Latihan: tulis 10 genre dan 10 tema, lalu acak pasangannya, pilih yang paling membuat Anda penasaran.

### b. Memutar satu aturan yang dianggap pasti

Ambil game populer, lalu ubah satu asumsi dasarnya. Contoh: "bagaimana jika pemain tidak bisa menyerang langsung?", "bagaimana jika kematian adalah mekanik utama?", "bagaimana jika waktu hanya bergerak ketika pemain bergerak?". Satu aturan yang diputar bisa menghasilkan gameplay yang benar-benar segar.

### c. Mengambil sudut budaya yang spesifik

Latar budaya lokal yang diolah dengan baik bisa menjadi pembeda kuat karena jarang ada di pasar global. Anda bisa memanfaatkan mitologi, arsitektur, musik, atau kisah dari Nusantara. Syaratnya: jangan hanya tempelan visual. Biarkan budaya itu memengaruhi mekanik dan struktur game agar terasa autentik dan tidak dangkal. Lakukan riset dan hormati sumber budayanya.

### d. Gaya visual dan audio yang khas

Gaya seni yang konsisten dan mudah dikenali dari satu tangkapan layar adalah aset marketing besar. Dalam daftar toko Steam, gambar kecil (capsule) harus bisa dikenali dalam sepersekian detik. Pilih gaya yang bisa Anda produksi secara konsisten, bukan gaya yang terlalu mahal.

### e. Satu sistem yang diperdalam

Alih-alih membuat banyak fitur dangkal, pilih satu sistem inti dan gali sedalam mungkin. Kedalaman satu sistem sering terasa lebih unik daripada banyak fitur biasa.

## 4.3 Validasi: apakah ciri khas ini benar-benar menarik pasar

Ide yang Anda sukai belum tentu disukai pasar. Lakukan validasi lebih awal:

1. **Riset kompetitor:** cari game serupa di Steam. Lihat ulasan mereka: apa yang dipuji dan apa yang dikeluhkan. Keluhan berulang adalah peluang Anda.
2. **Cek apakah ada permintaan:** apakah ada game serupa yang laku? Jika tidak ada sama sekali, bisa berarti peluang besar atau pasar yang tidak ada. Jika terlalu banyak game identik, persaingan berat.
3. **Uji pesan:** buat satu gambar atau GIF 5 sampai 10 detik yang menunjukkan hook Anda. Unggah ke media sosial dan komunitas (misalnya subreddit game dev, Discord, X, TikTok, YouTube Shorts). Lihat apakah orang bereaksi.
4. **Uji prototipe:** beri prototype ke pemain target, bukan hanya teman dan keluarga yang cenderung memuji.
5. **Cek kesesuaian tag:** pastikan ada tag Steam yang mewakili game Anda sehingga pemain yang mencari genre itu bisa menemukan game Anda.

Prinsip penting: **kejelasan lebih penting daripada kebaruan murni.** Game yang terlalu aneh sehingga tidak bisa dijelaskan akan sulit dijual. Game yang cukup familiar (agar orang paham) dengan satu twist kuat biasanya paling efektif.

## 4.4 Sinyal bahwa ciri khas Anda berhasil

- Orang yang melihat 10 detik gameplay bisa menceritakannya kembali dengan kata-kata sendiri.
- Orang bertanya "kapan rilis?" atau "ada demo?" setelah melihat cuplikan.
- Tangkapan layar Anda bisa dikenali tanpa logo.
- Streamer atau pemain menyebut keunikan itu secara spontan di ulasan.

## 4.5 Latihan Bab 4

1. Tulis hook satu kalimat. Tunjukkan ke 10 orang asing (bukan teman dekat), catat berapa yang tertarik.
2. Buat GIF gameplay 8 detik dan unggah. Catat reaksi.
3. Daftar tiga game kompetitor dan tiga keluhan terbesar di ulasan negatif mereka.

---

# Bab 5: Cerita dan Lore yang Melayani Gameplay (Tanpa Voice Actor)

Anda memilih cerita dan lore yang ada tetapi fokus utama di gameplay. Itu pendekatan yang bagus untuk developer indie. Prinsipnya: **cerita harus memperkuat gameplay, bukan menghalanginya.**

## 5.1 Prinsip dasar

- Pemain datang untuk bermain. Setiap menit cerita yang menghentikan gameplay harus terasa layak.
- Cerita terbaik di game sering disampaikan melalui aksi dan lingkungan, bukan lewat cutscene panjang.
- Cerita yang bisa dilewati (skip) dan dibaca belakangan membuat pemain yang tidak peduli tidak terganggu, sementara pemain yang peduli tetap mendapat kedalaman.

## 5.2 Teknik bercerita tanpa voice actor

Tanpa dubbing, Anda punya banyak alternatif yang justru murah dan efektif:

|Teknik|Penjelasan|Keunggulan|
|---|---|---|
|Teks singkat|Dialog dalam kotak teks dengan gaya bahasa karakter|Murah, mudah dilokalisasi|
|Suara non-kata|Gumaman, nada, atau bunyi khas karakter (seperti gaya "bahasa fiktif")|Memberi kepribadian tanpa dubbing|
|Environmental storytelling|Cerita lewat desain dunia: reruntuhan, benda, grafiti, tata ruang|Pemain menemukan sendiri, terasa personal|
|Catatan dan dokumen dalam game|Surat, buku harian, catatan, poster|Lore bisa dibaca opsional|
|Deskripsi item|Teks pendek di item atau senjata yang menyiratkan sejarah dunia|Sangat efisien dan ringan|
|Visual dan animasi|Ekspresi karakter, adegan singkat tanpa kata|Universal, tidak butuh lokalisasi|
|Musik dan SFX|Tema musik karakter, suara ambient|Membangun suasana|

Catatan: teks butuh bahasa. Jika menargetkan pasar global, pertimbangkan lokalisasi (Inggris, Mandarin, Spanyol, Portugis Brasil, Rusia, dan lain-lain) karena pemain Steam berasal dari banyak negara. Teks yang singkat dan jelas jauh lebih mudah dilokalisasi daripada teks panjang.

## 5.3 Lore: seberapa banyak yang dibutuhkan

Lore adalah latar dan sejarah dunia game. Pemula sering tergoda menulis lore berhalaman-halaman sebelum membuat gameplay. Itu perangkap.

Pendekatan efisien:

1. Tulis **satu halaman** dasar lore: dunia ini apa, konflik utama apa, mengapa pemain ada di sini.
2. Tulis **sepuluh pertanyaan misterius** yang tidak langsung dijawab. Misteri membuat pemain penasaran.
3. Sebar lore dalam potongan kecil (item, catatan, lingkungan) sehingga pemain menyusun sendiri gambarannya.
4. Pastikan setiap potongan lore terhubung dengan sesuatu yang bisa dilakukan atau dilihat pemain.

## 5.4 Menghubungkan cerita dengan gameplay (ludonarrative harmony)

Kadang cerita mengatakan satu hal dan gameplay mengajarkan hal lain, misalnya tokoh digambarkan lemah lembut tetapi pemain membantai ratusan musuh tanpa konsekuensi. Ketidakselarasan ini disebut ludonarrative dissonance. Usahakan cerita dan mekanik saling menguatkan.

Contoh pendekatan: jika tema game adalah kehilangan, buat mekanik yang membuat pemain kehilangan sesuatu secara bermakna. Jika tema adalah bertahan hidup, buat sumber daya terbatas.

## 5.5 Struktur cerita sederhana untuk game kecil

Gunakan struktur tiga babak yang ringan:

1. **Pengantar (awal):** perkenalkan dunia dan tujuan sederhana.
2. **Konflik (tengah):** rintangan makin sulit, pemain menemukan rahasia, ada perubahan situasi.
3. **Penyelesaian (akhir):** klimaks yang menguji kemampuan pemain, kemudian resolusi.

Untuk game roguelite, cerita biasanya terungkap perlahan melalui run berulang. Pemain mendapat potongan cerita baru setiap kali kalah atau menang.

## 5.6 Latihan Bab 5

1. Tulis lore dalam satu halaman, lalu pangkas menjadi lima kalimat.
2. Tulis sepuluh pertanyaan misterius tentang dunia game Anda.
3. Rancang tiga cara menyampaikan satu fakta penting cerita tanpa dialog (misalnya lewat objek di lingkungan).

---

# Bab 6: Memilih 2D atau 3D, Engine, dan Alat Kerja

## 6.1 Memilih 2D atau 3D

Keputusan ini memengaruhi biaya, waktu, dan ukuran tim. Perbandingan umum:

|Aspek|2D|3D|
|---|---|---|
|Beban produksi seni|Lebih ringan, gambar dan animasi frame atau skeletal|Lebih berat: model, rig, tekstur, animasi, pencahayaan|
|Kamera dan desain level|Lebih sederhana|Lebih kompleks: kamera, navigasi, oklusi|
|Performa|Umumnya ringan|Butuh optimasi lebih serius|
|Kompetisi di Steam|Sangat padat di beberapa genre (pixel art, platformer)|Padat juga, tetapi kualitas seni sering lebih mahal|
|Cocok untuk pemula|Sangat cocok|Bisa, tetapi tentukan scope yang kecil|
|Ciri khas visual|Gaya tangan, pixel, vektor, kolase|Low poly, stylized, cel shaded|

Saran untuk pemula: **mulai dengan 2D** untuk game pertama yang dirilis. Setelah paham siklus produksi sampai rilis, baru lanjut ke 3D. Jika Anda sudah punya skill 3D, pilih 3D bergaya (stylized atau low poly) yang konsisten daripada realistis yang mahal.

Alternatif menarik: 2.5D (sprite 2D di dunia 3D, atau 3D dengan gerak 2D), yang sering memberi tampilan khas dengan biaya terkontrol.

## 6.2 Memilih engine

Engine adalah perangkat lunak dasar pembuat game. Tiga pilihan paling umum untuk indie:

|Engine|Kelebihan|Hal yang perlu dipertimbangkan|Cocok untuk|
|---|---|---|---|
|Godot|Gratis dan open source, ringan, sangat baik untuk 2D, bahasa GDScript mudah dipelajari, juga mendukung C#|Ekosistem aset dan beberapa fitur 3D tingkat lanjut lebih kecil dibanding yang besar|2D, 3D ringan sampai menengah, pemula|
|Unity|Ekosistem besar, banyak tutorial dan aset, bahasa C#|Periksa selalu syarat lisensi dan biaya terbaru karena kebijakan bisa berubah|2D dan 3D, mobile, PC|
|Unreal Engine|Kualitas grafis tinggi untuk 3D, Blueprint (visual scripting)|Lebih berat, butuh komputer kuat dan kurva belajar lebih curam|3D kelas atas, tim kecil berpengalaman|

Tren 2026: Godot semakin banyak dipakai. Salah satu analisis menyebut sekitar 9 persen demo di Steam Next Fest 2026 dibuat dengan Godot. Itu menunjukkan Godot sudah dipakai serius untuk game komersial.

**Rekomendasi untuk pemula yang ingin game 2D:** Godot. Untuk 3D dengan sumber belajar luas: Unity atau Godot. Untuk 3D dengan tampilan sinematik dan tim berpengalaman: Unreal.

Aturan penting: **jangan ganti engine di tengah proyek** hanya karena tergoda hal baru. Pilih satu, kuasai, selesaikan game.

## 6.3 Alat pendukung

|Kebutuhan|Contoh alat (cek ketersediaan dan lisensi terbaru)|
|---|---|
|Pixel art dan animasi 2D|Aseprite, Krita, LibreSprite|
|Gambar dan ilustrasi|Krita, Clip Studio Paint, Photoshop|
|Model 3D|Blender (gratis dan sangat kuat)|
|Audio dan musik|Reaper, Audacity, LMMS, FMOD atau Wwise (middleware audio)|
|Kontrol versi|Git (dengan GitHub atau GitLab)|
|Manajemen tugas|Trello, Notion, Jira, atau file teks sederhana|
|Peta level 2D|Tiled|
|Dokumentasi desain|Markdown, Notion, Obsidian|

Aturan emas: **kontrol versi (Git) wajib sejak hari pertama.** Banyak pemula kehilangan proyek karena komputer rusak atau file terhapus. Cadangkan juga ke tempat terpisah (cloud atau hard disk eksternal).

## 6.4 Aset: bikin sendiri, beli, atau pakai AI

- **Bikin sendiri:** paling unik dan konsisten, tetapi butuh waktu atau keahlian.
- **Beli aset (asset store):** hemat waktu. Risiko: game terlihat seperti game lain yang memakai aset sama (flipped asset look). Jika memakai aset beli, modifikasi agar punya identitas sendiri.
- **Kolaborasi atau outsourcing:** seniman lepas, komposer, sound designer. Buat kontrak tertulis yang jelas soal hak cipta dan lisensi.
- **Alat AI generatif:** Steam meminta developer mengungkapkan penggunaan konten buatan AI di formulir pengiriman game. Selain itu ada risiko hukum, hak cipta, dan reaksi komunitas. Jika Anda memakainya, baca kebijakan terbaru Steam, pahami lisensi alat yang dipakai, dan pastikan ciri khas visual game tetap konsisten dan milik Anda. Sebagai keputusan bisnis, pertimbangkan reaksi pemain di niche Anda.

## 6.5 Target perangkat

Tentukan target sejak awal:

- **PC Windows:** target utama.
- **Steam Deck:** perangkat genggam Valve. Mendapat status Verified atau Playable bisa membantu eksposur, dan banyak pemain game offline memakainya. Pastikan kontrol gamepad, ukuran teks terbaca, dan performa stabil.
- **Linux dan Mac:** opsional, tergantung engine dan sumber daya Anda.
- **Konsol:** pertimbangkan setelah PC sukses.

Pastikan dukungan controller dan keyboard-mouse sejak awal desain. Banyak pemain game offline suka memakai controller.

## 6.6 Latihan Bab 6

1. Pilih 2D atau 3D untuk game pertama beserta tiga alasan.
2. Pilih engine, instal, dan selesaikan satu tutorial resmi sampai selesai (misalnya membuat game kecil lengkap).
3. Buat repositori Git dan lakukan commit pertama.

---

# Bab 7: Produksi: Scope, Prototype, dan Vertical Slice

## 7.1 Musuh terbesar pemula: scope terlalu besar

Kebanyakan proyek indie gagal selesai karena scope (ruang lingkup) terlalu besar. Aturan praktis:

- Game pertama Anda harus bisa selesai dalam **6 sampai 12 bulan** oleh tim kecil atau perorangan.
- Perkirakan waktu kerja, lalu kalikan dua. Hampir selalu kurang.
- Potong fitur sampai game tinggal inti yang paling menyenangkan. Fitur tambahan masuk daftar "kalau ada waktu".
- Lebih baik game kecil yang polished (rapi dan lengkap) daripada game besar yang setengah jadi.

Pertimbangkan membuat satu atau dua game kecil (satu sampai tiga bulan) sebelum proyek utama. Belajar menyelesaikan proyek adalah skill tersendiri.

## 7.2 Tahapan produksi

|Tahap|Tujuan|Output|
|---|---|---|
|Konsep|Menentukan ide, hook, pilar|Dokumen satu halaman|
|Prototype|Membuktikan core loop menyenangkan|Versi kasar yang bisa dimainkan|
|Vertical slice|Satu potongan kecil dengan kualitas hampir final|10 sampai 20 menit gameplay yang dipoles|
|Pra-produksi akhir|Menetapkan sistem dan pipeline|Rencana konten, daftar fitur final|
|Produksi|Membuat seluruh konten|Game lengkap versi alpha|
|Polishing|Memperbaiki bug, balancing, juice|Versi beta lalu release candidate|
|Rilis|Meluncurkan di Steam|Versi 1.0|
|Live support|Patch dan update|Versi 1.x|

**Vertical slice** sangat penting. Itu adalah potongan kecil game yang sudah mewakili kualitas akhir (grafis, suara, gameplay, UI). Vertical slice dipakai untuk: halaman toko Steam, trailer, demo, pitch ke publisher, dan menilai apakah proyek layak diteruskan. Jika vertical slice tidak menarik, game utuhnya hampir pasti tidak menarik.

## 7.3 Mengelola tugas dan waktu

- Pecah pekerjaan menjadi tugas kecil (maksimal 1 sampai 2 hari kerja).
- Tetapkan milestone bulanan yang bisa dimainkan.
- Lakukan review mingguan: apa yang selesai, apa yang terlambat, apa yang dipotong.
- Catat semua keputusan desain agar tidak berputar-putar.
- Jaga kesehatan. Burnout menghentikan banyak proyek lebih sering daripada kendala teknis.

## 7.4 Arsitektur kode yang sehat (pengantar)

Anda tidak perlu menjadi programmer senior, tetapi beberapa kebiasaan menghemat banyak waktu:

- Pisahkan data (statistik musuh, item, dialog) dari kode. Simpan di file data (JSON, resource) agar mudah di-balance tanpa mengubah kode.
- Satu tanggung jawab per skrip atau komponen.
- Beri nama variabel dan fungsi yang jelas.
- Simpan sistem penyimpanan (save/load) sejak awal, bukan di akhir, karena menambahkannya belakangan sangat menyakitkan.
- Buat versi data save yang bisa di-migrasi agar update tidak merusak save lama pemain.

## 7.5 Latihan Bab 7

1. Daftar semua fitur game impian Anda, lalu coret sampai tersisa 5 fitur inti.
2. Tentukan tanggal target vertical slice (misalnya 3 bulan dari sekarang).
3. Buat papan tugas dengan kolom: Rencana, Dikerjakan, Selesai.

---

# Bab 8: Playtest, Balancing, dan Kualitas Teknis

## 8.1 Playtest: cermin yang jujur

Anda terlalu dekat dengan game sendiri untuk menilainya objektif. Playtest adalah cara melihat game dari mata orang lain.

**Aturan playtest:**

1. Gunakan **pemain yang belum pernah melihat game Anda**.
2. **Jangan menjelaskan** apa pun saat mereka bermain. Duduk diam dan amati.
3. Catat: di mana mereka bingung, kapan mereka tersenyum, kapan mereka bosan, kapan mereka berhenti.
4. Tanyakan setelah selesai: "bagian mana yang paling Anda ingat?", "apa yang membingungkan?", "apakah Anda mau main lagi?".
5. Perhatikan apa yang mereka lakukan, bukan hanya apa yang mereka katakan.

Lakukan playtest berkala: setiap milestone, bukan hanya di akhir.

## 8.2 Metrik yang dilacak

Walaupun game offline, Anda bisa mengumpulkan data dari playtest dan, jika pemain mengizinkan, dari telemetri anonim:

- Di titik mana pemain paling sering mati atau berhenti.
- Rata-rata durasi sesi.
- Persentase pemain yang menyelesaikan tutorial.
- Fitur yang paling jarang disentuh.
- Rata-rata waktu menyelesaikan level atau run.

Jika Anda memakai telemetri, wajib transparan dan mematuhi aturan privasi. Beri opsi opt-in dan jelaskan datanya di halaman toko.

Di Steam, setelah rilis, Anda juga dapat membaca ulasan dan data dari Steamworks (misalnya waktu bermain rata-rata dan pencapaian yang dibuka) untuk melihat perilaku pemain.

## 8.3 Balancing

Balancing adalah menyetel angka agar game terasa adil dan menantang.

- Mulai dari data yang bisa diubah mudah (spreadsheet, file data).
- Ubah satu hal pada satu waktu.
- Uji dengan pemain pemula dan pemain mahir.
- Pastikan tidak ada satu strategi yang jelas mengalahkan semua strategi lain (dominant strategy), kecuali itu disengaja.
- Pertimbangkan opsi tingkat kesulitan dan aksesibilitas (ukuran teks, mode buta warna, pengaturan ulang tombol, opsi mengurangi efek berkedip atau goncangan).

## 8.4 Kualitas teknis yang menentukan ulasan

Ulasan negatif karena masalah teknis sangat merugikan. Checklist minimal sebelum rilis:

- Tidak ada crash pada alur utama.
- Frame rate stabil di spesifikasi minimum yang Anda tulis di halaman toko.
- Waktu loading wajar.
- Sistem save andal, termasuk pengujian skenario keluar paksa saat menyimpan.
- Kontrol bisa diatur ulang.
- Resolusi dan rasio layar umum didukung, termasuk ultrawide jika memungkinkan.
- Uji di beberapa perangkat (PC spesifikasi rendah, menengah, dan Steam Deck jika menargetkan).
- Cadangan build dan proses rilis sudah diuji di Steamworks sebelum hari H.

## 8.5 Latihan Bab 8

1. Rekrut 5 pemain playtest yang belum pernah melihat game Anda. Rekam layar mereka (dengan izin) dan catat titik kebingungan.
2. Buat daftar 10 bug terparah dan prioritaskan perbaikannya.
3. Uji game di komputer berspesifikasi paling rendah yang Anda punya.

---

# Bab 9: Marketing di Steam Sebelum Rilis

Ini bagian yang paling sering diabaikan pemain baru, padahal menentukan banyak hal. Prinsip utamanya: **marketing dimulai saat game masih prototype, bukan setelah selesai.**

## 9.1 Jadwal pemasaran yang disarankan

Berdasarkan pola yang banyak dibahas analis Steam pada 2026:

|Waktu sebelum rilis|Kegiatan|
|---|---|
|Fase prototype|Tentukan USP, buat GIF dan cuplikan, mulai bangun akun sosial dan komunitas|
|9 sampai 12 bulan sebelum rilis|Buka halaman Steam (Coming Soon) secepat mungkin setelah ada materi layak, kumpulkan wishlist|
|6 sampai 9 bulan|Trailer pertama, tangkapan layar kuat, mulai kirim ke komunitas dan kreator|
|3 sampai 6 bulan|Demo yang dipoles, rencanakan Steam Next Fest, perbarui halaman toko|
|1 sampai 3 bulan|Ikut Next Fest, kirim kunci ke kreator dan media, finalisasi harga dan tanggal rilis|
|2 minggu|Pengingat ke komunitas, finalisasi trailer rilis, uji build rilis|
|Hari rilis|Peluncuran, interaksi aktif dengan komunitas|

Waktu di atas fleksibel. Intinya: halaman toko dan komunitas harus ada jauh sebelum rilis.

## 9.2 Wishlist: mengapa penting dan berapa angkanya

**Wishlist** adalah daftar keinginan pemain di Steam. Pemain yang wishlist game Anda akan mendapat notifikasi saat game rilis dan saat diskon. Wishlist adalah indikator minat dan bahan bakar peluncuran.

Hal penting dan jujur:

- Menurut Valve, jumlah wishlist bukan faktor algoritmik umum, kecuali di beberapa tempat seperti tab Popular Upcoming. Namun wishlist menghasilkan notifikasi, dan lonjakan pembelian di awal peluncuran sangat membantu visibilitas berikutnya.
- Angka acuan yang sering dikutip (perkiraan pihak luar, bisa berubah): sekitar 7.000 sampai 10.000 wishlist untuk mulai muncul di Popular Upcoming, dan puluhan ribu wishlist untuk punya peluang kuat muncul di bagian New and Trending saat rilis. Tab Popular Upcoming mengalami perubahan pada penyegaran toko Juni 2026, sehingga angka lama mungkin kurang akurat.
- Perkiraan kasar dari beberapa analisis: game dengan 50.000 wishlist bisa menghasilkan konversi pembelian sekitar 10 sampai 20 persen pada hari-hari awal peluncuran, bergantung genre dan harga. Ini bukan jaminan.
- Setelah rilis, total wishlist bisa terus bertambah karena eksposur di toko.

Cara menghitung realistis: jika Anda ingin 10.000 penjualan di minggu pertama, dengan konversi sekitar 10 sampai 20 persen, Anda butuh wishlist di kisaran 50.000 sampai 100.000. Jika target Anda lebih kecil, sesuaikan.

## 9.3 Halaman toko (Store Page) yang mengonversi

Halaman toko adalah etalase Anda. Beberapa analis menyebut tingkat konversi halaman (dari kunjungan menjadi wishlist) di kisaran 20 sampai 30 persen sebagai target sehat untuk game dengan basis wishlist di atas 1.000. Nilai ini perkiraan dan sangat bergantung genre.

Elemen yang harus dipoles:

1. **Capsule art (gambar kecil di daftar):** harus jelas dan menarik dalam ukuran sangat kecil. Gambar ini menentukan apakah orang klik. Uji beberapa versi.
2. **Trailer:** tampilkan gameplay nyata dalam 10 detik pertama. Jangan buka dengan logo panjang atau cerita yang lambat. Trailer yang efektif memperlihatkan hook, variasi, dan puncak aksi.
3. **Tangkapan layar:** urutkan dari yang paling kuat. Gunakan teks singkat jika perlu. Tunjukkan gameplay, bukan hanya menu.
4. **Deskripsi singkat:** satu atau dua kalimat pertama harus menjawab "game ini tentang apa dan apa uniknya". Banyak orang tidak membaca lebih jauh.
5. **GIF dan animasi di deskripsi panjang:** gunakan untuk menunjukkan fitur.
6. **Tag:** pilih jujur dan sesuai (lihat Bab 1.4).
7. **Persyaratan sistem, dukungan bahasa, dan fitur:** isi dengan lengkap dan akurat. Dukungan bahasa yang luas menaikkan potensi pasar global.
8. **Harga:** lihat Bab 10.

Gunakan data Steamworks (jumlah tayangan, klik, dan konversi) untuk menguji dan memperbaiki halaman.

## 9.4 Demo dan Steam Next Fest

**Demo** adalah versi gratis terbatas. **Steam Next Fest** adalah festival demo Valve yang berlangsung beberapa kali dalam setahun (pada 2026 berlangsung sekitar bulan Februari, Juni, dan Oktober). Sumber-sumber 2026 menyebut bahwa umumnya satu game hanya bisa ikut satu Next Fest, sehingga pemilihan waktu penting. Cek aturan terbaru di Steamworks.

Temuan data Next Fest 2026 yang berguna:

- Hasil sangat timpang: game median mendapat wishlist hanya ratusan selama festival, sedangkan kelompok teratas mendapat ribuan. Disebutkan bahwa sekitar 5 persen teratas mendapat sekitar 7.000 sampai 10.000 wishlist (perkiraan dari pengikut).
- Survei pengembang pada Februari 2026 menunjukkan korelasi sangat kuat antara jumlah wishlist sebelum festival dan jumlah wishlist yang diperoleh selama festival. Artinya Next Fest lebih sering memperbesar momentum yang sudah ada daripada menciptakan momentum dari nol.
- Karena itu, bangun dulu basis wishlist dan komunitas sebelum Next Fest, bukan berharap festival menyelamatkan.

Tips praktis demo:

1. Demo harus menunjukkan hook dalam 10 sampai 15 menit pertama.
2. Batasi panjang demo (sekitar 30 sampai 60 menit) agar pemain ingin lebih.
3. Akhiri demo dengan titik "ingin lanjut" yang jelas dan tombol wishlist yang mudah ditemukan.
4. Beberapa analis menyarankan memakai halaman Steam terpisah untuk demo agar bisa menerima ulasan demo, tetapi ini rekomendasi, bukan kewajiban.
5. Jangan rilis demo yang penuh bug. Demo yang jelek bisa mematikan peluang.
6. Beberapa analisis menyarankan tidak langsung rilis tepat setelah Next Fest, tetapi beberapa minggu kemudian, sambil memanfaatkan momentum untuk promosi.

## 9.5 Komunitas dan media sosial

Bangun audiens sedikit demi sedikit, terus menerus.

- **Discord:** wadah komunitas inti. Pemain awal yang setia, tempat uji coba, dan sumber saran.
- **Short video (TikTok, YouTube Shorts, Instagram Reels, X):** unggah klip gameplay 5 sampai 20 detik yang memperlihatkan "momen memuaskan". Konsistensi lebih penting daripada kesempurnaan.
- **Reddit dan forum:** ikut berpartisipasi secara tulus, bukan hanya promosi. Banyak subreddit punya aturan promosi diri, baca dulu.
- **Devlog:** catatan perkembangan di Steam, itch.io, atau YouTube. Menunjukkan proses membuat orang ikut merasa memiliki.
- **Game jam:** ikut jam kecil bisa menjadi cara cepat menguji ide dan mendapat audiens awal (misalnya lewat itch.io).

Prinsip: ceritakan prosesnya, tunjukkan momen terbaik gameplay, dan balas komentar. Orang mendukung developer yang terasa nyata.

## 9.6 Kreator konten (streamer dan YouTuber)

Streamer dan YouTuber adalah saluran eksposur yang sangat efektif untuk game dengan visual dan momen yang "enak ditonton".

- Rancang game dengan momen yang menarik ditonton (reaksi, kejutan, aksi besar).
- Kirim kunci (Steam key) ke kreator yang cocok dengan genre Anda, bukan sembarang kreator besar. Kreator kecil sampai menengah sering lebih responsif.
- Siapkan press kit: logo, tangkapan layar, trailer, deskripsi, tautan, dan kontak.
- Sertakan pesan pribadi yang singkat dan jelas, bukan pesan massal.
- Pastikan build yang dikirim stabil.
- Perhatikan aturan Steam tentang pembagian kunci dan jangan menjual kunci secara tidak wajar.

## 9.7 Media dan kurator

- Kirim siaran pers dan kunci ke situs game yang meliput genre Anda.
- Pertimbangkan Steam Curators (kurator) yang cocok dengan niche Anda.
- Ikut pameran dan festival (online maupun offline) yang sesuai skala Anda.

## 9.8 Iklan berbayar

Iklan berbayar bisa membantu, tetapi bukan jalan pintas. Jika halaman toko Anda belum bagus, iklan hanya membakar uang. Uji dulu halaman toko dengan trafik organik. Setelah konversi sehat, iklan skala kecil bisa dicoba dengan anggaran terkontrol. Ukur biaya per wishlist dan bandingkan dengan nilai wishlist menurut perkiraan Anda.

## 9.9 Kesalahan marketing yang sering terjadi

- Membuka halaman toko terlalu dekat dengan hari rilis.
- Menunggu game selesai baru mulai promosi.
- Trailer lambat dan tidak menunjukkan gameplay.
- Tag tidak sesuai game.
- Mengabaikan komunitas awal.
- Menganggap "game bagus pasti ketemu pemainnya".
- Menempatkan semua harapan pada satu momen (misalnya hanya Next Fest).

## 9.10 Latihan Bab 9

1. Buat daftar 5 hal yang bisa Anda posting minggu ini (GIF, devlog, dll.) dan jadwalkan.
2. Buat halaman Steam (Coming Soon) draft lengkap dan minta komentar dari 10 orang.
3. Buat press kit satu halaman.

---

# Bab 10: Hari Peluncuran dan Dua Minggu Pertama

## 10.1 Mengapa dua minggu pertama krusial

Banyak analisis menyebut bahwa pembelian dan waktu bermain dalam dua minggu pertama setelah rilis sangat membentuk visibilitas Steam berikutnya. Anda ingin momentum awal sebesar mungkin: banyak pembelian, banyak ulasan positif, banyak pemain aktif.

## 10.2 Memilih tanggal rilis

- Hindari bertabrakan langsung dengan rilis game besar di genre yang sama. Cek kalender rilis di Steam dan situs kalender game.
- Perhatikan periode sale besar Steam. Rilis tepat sebelum atau saat sale besar bisa membuat game Anda tenggelam. Beberapa developer memilih jendela yang lebih tenang, sebagian lain justru memanfaatkan keramaian trafik. Tidak ada jawaban pasti, tentukan berdasarkan data dan genre.
- Umumkan tanggal rilis jauh hari agar orang bisa bersiap (wishlist, ulasan, dan liputan).
- Hindari rilis di akhir pekan panjang saat tim Anda tidak bisa memperbaiki masalah mendesak.
- Pastikan Anda siap bekerja penuh selama 1 sampai 2 minggu setelah rilis untuk menangani bug dan masukan.

## 10.3 Harga

Harga adalah bagian dari positioning. Prinsip:

- Lihat game sejenis yang sukses: kisaran harga, durasi, dan kualitas.
- Harga terlalu murah bisa memberi kesan kualitas rendah. Harga terlalu mahal menurunkan konversi.
- Gunakan **harga regional** (regional pricing) yang disesuaikan dengan daya beli tiap negara. Steam menyediakan rekomendasi harga regional. Ini memperluas pasar.
- Diskon peluncuran (launch discount) biasanya diberikan beberapa persen untuk dua minggu pertama. Perhatikan aturan Steam tentang diskon dan jeda antar diskon.
- Hindari menurunkan harga terlalu cepat setelah rilis karena merugikan pembeli awal dan citra game.

## 10.4 Early Access atau rilis penuh

**Early Access** adalah merilis game yang belum selesai agar bisa dibeli sambil dikembangkan.

|Aspek|Early Access|Rilis penuh (1.0)|
|---|---|---|
|Pendapatan awal|Bisa lebih cepat|Setelah game selesai|
|Umpan balik|Terus-menerus dari pemain|Setelah rilis|
|Risiko|Ekspektasi dan tekanan update, ulasan negatif jika kualitas rendah|Satu kesempatan kesan pertama|
|Cocok untuk|Game sistemik, sandbox, roguelite yang bisa diperluas|Game naratif atau linear|

Untuk game offline dengan alur cerita dan konten yang terstruktur, rilis penuh biasanya lebih aman untuk pemula. Early Access butuh komitmen update berkelanjutan dan komunikasi jujur tentang peta jalan (roadmap).

## 10.5 Checklist peluncuran

Sebelum hari rilis:

- Build final sudah diunggah dan diuji lewat jalur rilis Steam.
- Halaman toko sudah final (teks, harga, bahasa, tag, trailer).
- Pencapaian (achievements) berfungsi.
- Cloud save berfungsi (jika dipakai).
- Dukungan controller diuji.
- Kunci untuk kreator dan media sudah dikirim.
- Pengumuman rilis dan trailer rilis siap.
- Server Discord dan kanal dukungan siap.
- Rencana patch hari pertama sudah ada.
- Anda sudah istirahat cukup.

Saat dan setelah rilis:

- Pantau ulasan, forum, dan Discord setiap beberapa jam.
- Perbaiki bug kritis secepatnya. Patch cepat sangat dihargai dan dapat mengubah ulasan negatif menjadi positif.
- Balas ulasan dan diskusi dengan sopan dan jujur.
- Jangan berdebat dengan ulasan negatif. Catat masukannya.
- Unggah klip momen terbaik dan hasil pemain ke media sosial.
- Terima kasih kepada komunitas.

## 10.6 Mengelola ulasan

Ulasan Steam memengaruhi konversi. Peringkat seperti "Very Positive" atau "Overwhelmingly Positive" meningkatkan penjualan. Cara menjaga ulasan sehat:

- Pastikan kualitas teknis dan gameplay inti sebelum rilis.
- Jangan menawarkan imbalan untuk ulasan positif (melanggar aturan).
- Tuliskan ekspektasi jujur di halaman toko supaya yang membeli memang segmen yang cocok.
- Perbaiki masalah yang sering disebut dalam ulasan, lalu umumkan perbaikannya.
- Di dalam game, beri pengingat halus dan tidak mengganggu agar pemain yang puas mau menulis ulasan (tanpa memaksa).

## 10.7 Latihan Bab 10

1. Tentukan tanggal rilis dan tiga alasannya, lalu cek rilis kompetitor di sekitar tanggal itu.
2. Buat tabel harga regional rencana Anda (cek rekomendasi Steam).
3. Tulis rencana 14 hari pertama: tugas harian setelah rilis.

---

# Bab 11: Setelah Rilis, Cara Bertahan di Daftar Teratas

Bab ini menjawab bagian "tidak pernah hilang" dari target Anda dengan cara yang realistis. Anda tidak bisa mengunci posisi, tetapi Anda bisa menciptakan **gelombang momentum berulang** sehingga game Anda sering muncul kembali.

## 11.1 Memahami cara kerja daftar

- **Top Sellers** pada dasarnya mencerminkan pendapatan dalam periode tertentu. Game muncul di sana ketika penjualannya tinggi, biasanya saat rilis, diskon, atau update besar.
- **Most Played** mencerminkan jumlah pemain bersamaan. Game dengan komunitas besar yang bermain bersamaan berada di atas. Untuk game offline, puncak biasanya muncul saat rilis, diskon besar, atau update besar.

Karena itu strategi Anda adalah **menciptakan puncak berulang**, bukan satu puncak tunggal.

## 11.2 Kalender momentum

Susun kalender 12 bulan setelah rilis dengan titik-titik momentum:

|Momentum|Tujuan|Contoh|
|---|---|---|
|Rilis|Puncak pertama|Peluncuran 1.0|
|Patch awal|Stabilitas dan ulasan|Perbaikan bug dan balancing|
|Update konten besar|Alasan kembali bermain|Area baru, mode baru, karakter baru|
|Diskon musiman|Puncak penjualan|Sale musiman Steam dan festival tematik|
|Event tematik|Menarik perhatian|Update bertema hari raya atau musim di dalam game|
|DLC|Pendapatan tambahan dan alasan kembali|Ekspansi cerita atau karakter|
|Dukungan perangkat baru|Pasar baru|Steam Deck Verified, dukungan bahasa baru|
|Porting konsol|Penjualan tambahan|Switch, PlayStation, Xbox|
|Bundel|Menjual ke audiens baru|Bundel dengan game Anda yang lain atau dengan developer lain|

Steam memiliki beberapa sale musiman dan festival tematik sepanjang tahun. Cek kalender resmi Steam dan daftarkan game Anda ke event yang relevan sesuai prosedur Steamworks. Ada aturan jeda antar diskon, jadi rencanakan dengan matang.

## 11.3 Update yang membuat pemain kembali

Update yang efektif:

- Memberi alasan baru untuk bermain (bukan hanya perbaikan).
- Diumumkan dengan jelas lewat Steam News, Discord, dan media sosial.
- Dibuat tematik dan punya "headline" yang mudah dibagikan.
- Menjawab permintaan komunitas yang paling sering disebut, selama sesuai pilar desain.
- Disertai trailer atau GIF singkat.

Gunakan fitur Steam untuk mengumumkan update dan mengumpulkan pemain lama.

## 11.4 Memperpanjang umur game offline

Beberapa cara memperpanjang umur game offline:

- **Mode tantangan, mode harian (daily seed), dan mode tantangan komunitas.** Mode harian dengan seed yang sama bisa dibagikan tanpa server (misalnya dengan membandingkan skor manual atau melalui fitur leaderboard Steam jika Anda memutuskan memakainya. Ingat bahwa leaderboard bersifat daring, jadi pertimbangkan apakah ini sesuai dengan keputusan "offline" Anda. Anda bisa menjadikannya fitur opsional).
- **Dukungan mod lewat Steam Workshop:** komunitas bisa membuat konten tanpa Anda harus membuatnya. Ini sangat efektif untuk game sandbox, simulasi, dan RPG.
- **Pencapaian (achievements) yang menarik:** pencapaian menantang memicu pemain mencoba gaya main berbeda. Hindari pencapaian yang hanya memaksa grinding.
- **New Game Plus, mode sulit, dan modifier:** pengaturan yang mengubah aturan permainan.
- **Editor level atau alat kreatif:** pemain membuat dan membagikan karya.
- **DLC yang bermakna:** perluasan dengan konten baru berkualitas, bukan pemotongan konten dari game utama.

## 11.5 Komunitas jangka panjang

- Perbarui Discord dan Steam Community secara rutin.
- Bagikan hasil kreasi pemain (screenshot, fanart, speedrun).
- Dengarkan komunitas, tetapi pertahankan visi desain Anda.
- Jaga tone yang ramah dan profesional.
- Beri kredit kepada kontributor komunitas.

## 11.6 Kapan membuat sekuel atau game berikutnya

Sering kali cara terbaik menjaga nama studio tetap hadir di daftar teratas adalah dengan membangun **katalog**: game kedua dan ketiga dengan identitas serupa. Pemain yang menyukai game pertama Anda lebih mudah membeli game kedua. Pemain yang menemukan game kedua akan membeli game pertama. Ikuti studio (follow) di Steam menjadi aset yang terkumpul dari waktu ke waktu.

## 11.7 Latihan Bab 11

1. Susun kalender momentum 12 bulan setelah rilis dengan minimal 6 titik momentum.
2. Rancang satu update besar (judul, fitur utama, pesan pengumuman).
3. Tentukan dua fitur yang membuat pemain ingin kembali ke game setelah selesai satu kali.

---

# Bab 12: Menuju Penghargaan dan Pengakuan

## 12.1 Realitas penghargaan

Penghargaan memberi kredibilitas dan eksposur, tetapi juga sangat kompetitif. Anda tidak bisa memastikan menang. Anda bisa meningkatkan peluang dengan:

1. Game yang benar-benar berbeda dan terasa matang.
2. Polesan tinggi (tidak ada bug mengganggu, UI jelas, audio baik).
3. Pengiriman tepat waktu dan lengkap ke festival dan penghargaan yang sesuai.
4. Narasi pengajuan yang kuat: apa yang membuat game ini baru dan penting.

## 12.2 Contoh festival dan penghargaan yang relevan untuk indie

(Cek jadwal, syarat, dan biaya terbaru di situs resmi masing-masing.)

- **Independent Games Festival (IGF)** yang berkaitan dengan Game Developers Conference (GDC).
- **The Game Awards**, termasuk kategori game independen.
- **BAFTA Games Awards**.
- **Steam Awards:** dipilih oleh pemain Steam. Kategori dan mekanismenya ditentukan Valve. Game dengan komunitas aktif punya peluang lebih baik.
- Festival regional dan internasional seperti pameran dan kompetisi indie (misalnya berbagai showcase di pameran game besar dunia).
- **Acara dan kompetisi lokal Indonesia**, misalnya yang diselenggarakan komunitas dan asosiasi game Indonesia (seperti Indonesia Game Developer Exchange dan program serupa). Cek kalender resmi dan komunitas lokal untuk info terbaru.
- **Game jam:** ajang cepat untuk eksposur awal dan portofolio.

## 12.3 Apa yang biasanya dihargai juri

Setiap penghargaan berbeda, tetapi pola umum yang dihargai:

- Inovasi dalam desain dan mekanik.
- Kohesi: seni, audio, mekanik, dan tema menyatu.
- Eksekusi: tidak setengah jadi.
- Kepekaan pada aksesibilitas dan pengalaman pemain.
- Dampak emosional atau gagasan yang diingat.
- Identitas unik sebuah studio dan budaya.

## 12.4 Strategi praktis

1. Tentukan 3 sampai 5 penghargaan atau festival yang realistis sesuai genre Anda.
2. Catat tanggal pendaftaran dan syarat, kerjakan mundur dari tenggat.
3. Siapkan materi pengajuan: build stabil, trailer pendek yang kuat, deskripsi singkat yang jelas, dan akses mudah bagi juri.
4. Mulai dari yang kecil (festival indie lokal, game jam) untuk membangun reputasi.
5. Hubungi komunitas dan developer lain untuk mendapat saran dan jaringan.
6. Rayakan nominasi dan penghargaan sekecil apa pun di media sosial untuk menambah eksposur.

## 12.5 Latihan Bab 12

1. Buat daftar 5 festival atau penghargaan, lengkap dengan tenggat dan syaratnya.
2. Tulis deskripsi pengajuan 100 kata tentang apa yang membuat game Anda berbeda.

---

# Bab 13: Bisnis, Uang, dan Legal

Informasi di bab ini bersifat umum, bukan nasihat hukum atau pajak. Konsultasikan dengan akuntan dan konsultan hukum di negara Anda.

## 13.1 Anggaran dan runway

- Hitung biaya hidup bulanan Anda dan lamanya Anda bisa bekerja tanpa penghasilan (runway).
- Hitung biaya proyek: perangkat keras, perangkat lunak, aset, outsourcing, marketing, biaya Steam, pajak.
- Siapkan cadangan untuk 6 sampai 12 bulan setelah rilis, karena pendapatan tidak langsung stabil.
- Pertimbangkan bekerja paruh waktu sambil mengembangkan game jika memungkinkan.

## 13.2 Sumber pendanaan

- Tabungan pribadi.
- Pendapatan dari pekerjaan lain atau proyek jasa.
- Hibah dan program pendanaan (dari pemerintah, lembaga, atau perusahaan) yang mendukung developer game. Cari program yang tersedia di Indonesia dan regional.
- Publisher indie: biasanya menyediakan dana, marketing, dan dukungan teknis dengan imbalan bagi hasil. Siapkan vertical slice, rencana anggaran, dan data pasar sebelum pitching. Baca kontrak dengan teliti, konsultasikan dengan ahli hukum.
- Crowdfunding (Kickstarter dan lainnya): membutuhkan komunitas dan materi kuat. Bisa juga menjadi alat validasi.
- Early Access sebagai pendapatan awal (lihat Bab 10.4).

## 13.3 Pembayaran dan pajak

- Anda perlu mengisi wawancara pajak dan data bank di Steamworks sebelum menerima pembayaran. Developer di luar Amerika Serikat biasanya mengisi formulir pajak yang sesuai (misalnya jenis formulir W-8). Ikuti instruksi resmi Steamworks.
- Steam mengirim pembayaran setelah periode tertentu dan ambang minimum. Cek dokumentasi resmi.
- Pendapatan dari Steam umumnya dalam dolar AS. Perhatikan nilai tukar dan biaya transfer bank.
- Catat semua pendapatan dan pengeluaran. Konsultasikan dengan akuntan tentang kewajiban pajak penghasilan di Indonesia dan apakah perlu mendirikan badan usaha.

## 13.4 Badan usaha dan hak kekayaan intelektual

- Pertimbangkan badan usaha (misalnya PT atau CV) jika bekerja dengan tim, menerima pendanaan, atau menandatangani kontrak dengan publisher.
- Daftarkan merek dagang untuk nama game dan studio jika memungkinkan.
- Simpan bukti kepemilikan aset: lisensi font, musik, efek suara, aset yang dibeli, dan kontrak dengan kontraktor.
- Jika memakai aset berlisensi, baca syarat penggunaan komersial.
- Hormati hak cipta. Jangan memakai musik, karakter, atau aset tanpa izin.

## 13.5 Kebijakan konten dan rating

- Steam memiliki aturan konten, termasuk pengungkapan konten dewasa dan penggunaan AI. Baca pedoman terbaru.
- Beberapa wilayah memiliki sistem klasifikasi usia. Cek persyaratan jika Anda menargetkan konsol atau wilayah tertentu.
- Sertakan peringatan konten (misalnya kekerasan, tema sensitif) di halaman toko agar ekspektasi pemain sesuai.

## 13.6 Latihan Bab 13

1. Hitung runway Anda dalam bulan.
2. Buat anggaran sederhana: biaya tetap, biaya proyek, dan cadangan.
3. Daftar tiga program pendanaan atau hibah yang bisa Anda teliti.

---

# Bab 14: Roadmap 24 Bulan untuk Pemula

Roadmap ini contoh untuk pemula yang bekerja sendiri atau dalam tim kecil. Sesuaikan dengan situasi Anda.

## Bulan 1 sampai 3: Belajar dan latihan

- Pilih engine dan selesaikan tutorial resmi.
- Buat 2 sampai 3 game mini (1 sampai 2 minggu per game). Selesaikan, jangan sempurnakan.
- Ikut satu game jam.
- Pelajari 20 game indie sukses di genre target: mekanik, tag, harga, ulasan.

## Bulan 4 sampai 6: Konsep dan prototype

- Tentukan hook, pilar desain, dan lore singkat.
- Bangun prototype core loop.
- Playtest dengan 10 sampai 20 orang.
- Mulai buat akun sosial dan Discord. Unggah GIF pertama.
- Putuskan lanjut atau ganti ide berdasarkan hasil playtest.

## Bulan 7 sampai 12: Vertical slice dan halaman toko

- Bangun vertical slice berkualitas tinggi.
- Buat trailer pertama dan capsule art.
- Buka halaman Steam (Coming Soon) dan mulai mengumpulkan wishlist.
- Posting rutin: setidaknya 3 kali seminggu.
- Hubungi kreator kecil yang cocok dengan genre Anda.

## Bulan 13 sampai 18: Produksi dan demo

- Produksi konten utama.
- Rilis demo yang dipoles.
- Ikut Steam Next Fest dengan basis wishlist yang sudah dibangun.
- Terus playtest dan balancing.
- Perbarui halaman toko berdasarkan data.

## Bulan 19 sampai 21: Polish dan persiapan rilis

- Perbaiki bug, optimasi, dan uji di berbagai perangkat.
- Finalisasi harga dan tanggal rilis.
- Kirim kunci ke kreator dan media.
- Siapkan komunikasi rilis dan rencana patch.

## Bulan 22 sampai 24: Rilis dan pasca rilis

- Rilis di Steam. Fokus penuh pada dua minggu pertama.
- Patch cepat dan komunikasi aktif.
- Rencanakan update pertama dan kalender momentum 12 bulan.
- Evaluasi: apa yang berhasil, apa yang tidak. Catat pelajaran untuk game berikutnya.

Catatan jujur: banyak proyek butuh lebih dari 24 bulan. Itu wajar. Yang penting adalah tidak berhenti dan terus menyelesaikan hal-hal kecil secara konsisten.

---

# Bab 15: Checklist Ringkas dan Glosarium

## 15.1 Checklist ringkas

**Gameplay**

- Core loop menyenangkan dengan grafis kasar.
- Ada micro, core, meta, dan long-term loop.
- Ada tujuan jangka pendek yang bertumpuk.
- Kemajuan terasa nyata.
- Restart cepat dan kekalahan terasa adil.
- Juice dan umpan balik jelas.
- Replayability terencana.

**Keunikan**

- Hook bisa dijelaskan dalam satu kalimat.
- Tangkapan layar bisa dikenali tanpa logo.
- Sudah dibandingkan dengan kompetitor.
- Sudah diuji ke orang asing.

**Cerita dan lore**

- Cerita tidak menghalangi gameplay.
- Lore tersebar dalam potongan kecil.
- Tidak butuh voice actor.

**Produksi**

- Scope realistis.
- Kontrol versi aktif dan ada cadangan.
- Vertical slice selesai sebelum produksi penuh.
- Playtest rutin.

**Marketing**

- Halaman Steam dibuka lebih awal.
- Capsule, trailer, dan tangkapan layar kuat.
- Komunitas (Discord, sosial) aktif.
- Demo dipoles dan siap Next Fest.
- Kunci untuk kreator dikirim.

**Peluncuran dan pasca rilis**

- Tanggal dan harga dipertimbangkan matang.
- Ada rencana 14 hari pertama.
- Ada kalender momentum 12 bulan.
- Komunitas dirawat.

## 15.2 Glosarium

|Istilah|Arti sederhana|
|---|---|
|Core loop|Siklus aksi utama yang diulang pemain|
|Meta-progression|Kemajuan permanen yang bertahan antar run|
|Roguelite|Genre dengan run berulang dan kemajuan permanen sebagian|
|Procedural generation|Pembuatan konten secara otomatis dengan aturan|
|Juice|Efek kecil yang membuat aksi terasa memuaskan|
|Hit stop|Jeda sangat singkat saat serangan kena untuk memberi kesan bobot|
|USP|Alasan utama orang memilih game Anda|
|Hook|Ide singkat yang langsung menarik perhatian|
|Vertical slice|Potongan kecil game dengan kualitas hampir final|
|Scope creep|Fitur bertambah tak terkendali|
|Playtest|Uji coba game oleh calon pemain|
|Wishlist|Daftar keinginan pemain di Steam|
|Capsule art|Gambar kecil game di toko Steam|
|Steam Next Fest|Festival demo Steam yang berlangsung beberapa kali setahun|
|Top Sellers|Daftar penjualan tertinggi Steam|
|Most Played|Daftar game dengan pemain bersamaan terbanyak|
|Concurrent players|Jumlah pemain yang bermain pada saat yang sama|
|Early Access|Menjual game yang belum selesai sambil terus dikembangkan|
|DLC|Konten tambahan berbayar atau gratis untuk game utama|
|Steamworks|Portal developer Steam untuk mengelola game|
|Retensi|Seberapa banyak pemain yang kembali bermain|
|Ludonarrative dissonance|Ketidakselarasan antara cerita dan mekanik|
|Regional pricing|Harga berbeda per negara sesuai daya beli|

---

# Daftar Sumber

Informasi pasar dan Steam dalam buku ini dirangkum dari sumber berikut (diakses November 2026). Sumber pihak ketiga bersifat analisis dan perkiraan, bukan angka resmi Valve. Verifikasi selalu di Steamworks.

- Analisis algoritma dan visibilitas Steam 2026: https://dev.to/linou518/steams-algorithm-isnt-magic-a-complete-breakdown-for-indie-games-in-2026-4hh4
- Tag, Discovery Queue, dan sinyal visibilitas: https://blog.playio.co/steam-tags-discovery-queue-visibility
- Popular Upcoming dan wishlist: https://games.gg/news/steam-popular-upcoming-wishlist-guide/ dan https://www.steampageanalyzer.com/blog/steam-popular-upcoming-list
- Penjelasan Valve tentang rekomendasi dan wishlist (GamesRadar): https://www.gamesradar.com/we-dont-think-steam-should-be-pay-to-win-valve-explains-how-games-we-wouldve-never-predicted-pop-off-so-hard
- Data Steam Next Fest Februari 2026: https://cinevva-site.pages.dev/signals/2026-03-11-steam-next-fest-discovery-data dan https://ziva.sh/blogs/steam-next-fest-2026
- Strategi Next Fest 2026: https://app.cinevva.com/guides/steam-next-fest-strategy
- Benchmark wishlist Next Fest (How To Market A Game): https://howtomarketagame.com/2025/03/26/archive-january-2026-benchmarks-how-many-wishlists-can-i-get-from-steam-next-fest/
- Taktik wishlist berdasarkan data: https://www.steampageanalyzer.com/blog/how-to-get-steam-wishlists
- Biaya Steam Direct: https://www.steampageanalyzer.com/blog/steam-direct-fee-explained
- Bagi hasil Steam: https://presskit.gg/field-guides/how-much-does-steam-take dan https://fungies.io/how-to-sell-a-game-on-steam-3/
- Masalah discovery di Steam: https://www.spieltimes.io/gaming/steam-s-discovery-problem-may-be-hurting-thousands-of-good-games/

**Catatan akhir:** angka seperti jumlah wishlist yang dibutuhkan, tingkat konversi, dan perkiraan jumlah game per tahun berasal dari analisis pihak ketiga dan bisa berubah. Gunakan sebagai gambaran arah, bukan jaminan.

Semoga buku ini membantu langkah pertama Anda. Mulailah kecil, selesaikan, pelajari, lalu ulangi dengan game yang lebih ambisius.