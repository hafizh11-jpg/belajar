# Game Developer Indie dengan Godot Engine

## Panduan Dasar untuk Pemula: Game 2D dan 3D, Fokus Gameplay, Offline, Tanpa Voice Actor

Versi dokumen: November 2026 Acuan engine: Godot 4.7.x (rilis stabil terbaru saat buku ini ditulis adalah 4.7.2). Seluruh konsep inti di buku ini berlaku untuk seluruh seri Godot 4.x, sehingga tetap relevan jika kamu memakai versi yang lebih baru di tahun 2027 dan seterusnya.

---

## Daftar Isi

- Bab 0 - Cara Memakai Buku Ini
- Bab 1 - Memahami Dunia Game Developer Indie
- Bab 2 - Mengenal Godot Engine dan Instalasi
- Bab 3 - Tur Antarmuka Editor Godot
- Bab 4 - Konsep Inti: Node, Scene, Scene Tree, dan Resource
- Bab 5 - Dasar Pemrograman GDScript
- Bab 6 - Siklus Hidup Node, Delta Time, dan Input
- Bab 7 - Menyiapkan Project dengan Benar
- Bab 8 - Game 2D Pertama: Player yang Bisa Bergerak
- Bab 9 - Fisika dan Collision 2D
- Bab 10 - Membangun Level dengan TileMapLayer
- Bab 11 - Animasi 2D
- Bab 12 - Signal, Group, dan Komunikasi Antar Node
- Bab 13 - User Interface (UI)
- Bab 14 - Audio: Musik dan Efek Suara
- Bab 15 - Pengenalan Game 3D
- Bab 16 - Karakter, Interaksi, dan Fisika 3D
- Bab 17 - Story dan Lore Tanpa Voice Actor
- Bab 18 - Autoload, Pergantian Scene, dan Game State
- Bab 19 - Save, Load, dan Pengaturan (Offline)
- Bab 20 - Sistem Gameplay Dasar: Health, State Machine, Musuh, dan Game Feel
- Bab 21 - Debugging dan Optimasi Dasar
- Bab 22 - Export, Distribusi, dan Version Control
- Bab 23 - Mini Proyek: Game Petualangan Kecil
- Bab 24 - Roadmap Belajar, Kesalahan Umum, Glosarium, dan Cheat Sheet

---

# Bab 0 - Cara Memakai Buku Ini

## 0.1 Untuk siapa buku ini

Buku ini ditujukan untuk pemula yang ingin menjadi game developer indie (pengembang game independen, biasanya sendirian atau tim kecil) dengan Godot Engine. Kamu tidak perlu pengalaman membuat game. Pengalaman pemrograman sedikit akan membantu, tetapi buku ini mengajarkan dasar pemrograman yang kamu butuhkan.

## 0.2 Batasan dan fokus buku

Agar belajar lebih terarah, buku ini sengaja membatasi ruang lingkup:

|Aspek|Keputusan di buku ini|Alasan|
|---|---|---|
|Dimensi|2D dan 3D (dasar keduanya)|Kamu perlu paham konsep di kedua dimensi, tetapi 2D dipakai sebagai fondasi karena lebih sederhana|
|Fokus desain|Gameplay terlebih dahulu|Game yang menyenangkan dimainkan lebih penting daripada cerita yang panjang|
|Story dan lore|Ada, tetapi sebagai pendukung|Cerita disampaikan lewat teks, objek di dunia game, dan level|
|Voice actor|Tidak ada|Menghemat biaya dan waktu. Dialog memakai teks, suara hanya musik dan efek suara (SFX)|
|Mode|Offline, single player|Tidak perlu server, jaringan, atau akun. Data disimpan di komputer pemain|
|Bahasa pemrograman|GDScript|Paling terintegrasi dengan editor dan paling mudah untuk pemula|

## 0.3 Cara belajar yang disarankan

1. Ketik kodenya sendiri. Jangan hanya menyalin dan menempel. Mengetik membuat otak memproses detailnya.
2. Jalankan setelah setiap perubahan kecil. Tekan F5 sesering mungkin.
3. Kerjakan latihan di akhir tiap bab.
4. Jika error, baca pesan errornya dengan tenang. Error di Godot biasanya menyebut nama file dan nomor baris.
5. Simpan project di folder yang rapi dan buat cadangan secara rutin (lihat Bab 22).

## 0.4 Konvensi penulisan

- Kode ditulis dalam blok kode dengan label bahasa, misalnya `gdscript`.
- Nama node, properti, atau menu ditulis dengan `huruf monospasi`.
- Menu ditulis dengan tanda panah, misalnya `Project > Project Settings`.
- Path `res://` menunjuk ke folder project kamu. Path `user://` menunjuk ke folder data pengguna (dipakai untuk save game).

## 0.5 Perangkat yang dibutuhkan

- Komputer dengan Windows, macOS, atau Linux. Godot sangat ringan sehingga laptop sederhana pun cukup untuk game 2D dan 3D sederhana.
- Mouse dan keyboard.
- Aplikasi pengolah gambar (opsional), misalnya Krita, GIMP, atau Aseprite.
- Aplikasi model 3D (opsional), misalnya Blender.

---

# Bab 1 - Memahami Dunia Game Developer Indie

## 1.1 Apa itu game developer indie

Game developer indie adalah pembuat game yang bekerja secara independen, tanpa dukungan penerbit besar. Biasanya satu orang atau tim kecil yang mengerjakan banyak peran sekaligus: desain, pemrograman, seni, audio, dan pemasaran.

Konsekuensinya penting untuk kamu pahami sejak awal: **sumber daya (waktu, tenaga, uang) kamu terbatas**. Karena itu, kemampuan paling berharga seorang developer indie adalah menentukan scope (ruang lingkup) yang realistis.

## 1.2 Tahapan pembuatan game

Secara umum, game dibuat melalui tahapan berikut:

1. **Konsep**: ide inti game dalam satu atau dua kalimat.
2. **Prototype**: versi kasar untuk menguji apakah inti gameplay menyenangkan.
3. **Produksi**: membuat konten (level, musuh, UI, audio, cerita).
4. **Polish**: merapikan, menambah game feel, memperbaiki bug.
5. **Rilis**: export, distribusi, dan dokumentasi.
6. **Pasca rilis**: perbaikan dan pembaruan (opsional).

## 1.3 Gameplay terlebih dahulu

Buku ini menganut prinsip **gameplay-first**. Artinya urutan prioritasmu adalah:

1. Aksi utama pemain terasa enak (bergerak, melompat, menyerang, berinteraksi).
2. Ada tujuan dan tantangan yang jelas.
3. Ada umpan balik (feedback) saat pemain berhasil atau gagal: suara, animasi, efek.
4. Baru kemudian cerita, lore, dan dekorasi memperkuat pengalaman tersebut.

Cerita yang bagus tidak menyelamatkan gameplay yang membosankan, tetapi gameplay yang bagus bisa berdiri dengan cerita yang sederhana.

## 1.4 Konsep inti: game loop

Hampir semua game, sesederhana apa pun, mengulang siklus ini puluhan kali per detik:

```
Baca input pemain
   -> Perbarui keadaan game (posisi, nyawa, skor, AI musuh)
      -> Gambar hasilnya ke layar dan putar suara
         -> Ulangi
```

Siklus ini disebut **game loop**. Godot menjalankan game loop untukmu. Tugasmu adalah menulis logika yang dipanggil di dalam loop tersebut.

## 1.5 Scope: musuh terbesar developer pemula

Kesalahan paling umum pemula adalah memulai dengan game yang terlalu besar (misalnya RPG dunia terbuka). Aturan praktis:

- Proyek pertama: selesaikan dalam hitungan hari atau minggu.
- Proyek kedua dan ketiga: boleh sedikit lebih besar.
- Jika sebuah fitur tidak mendukung inti gameplay, tunda atau buang.
- Menyelesaikan 5 game kecil mengajarkan lebih banyak daripada meninggalkan 1 game besar yang setengah jadi.

## 1.6 Story dan lore tanpa voice actor

Tanpa voice actor, cerita disampaikan melalui:

- Teks dialog (kotak dialog dengan efek mengetik).
- Deskripsi item, buku catatan, atau jurnal yang bisa dibaca pemain.
- Environmental storytelling: desain level, objek, dan detail dunia yang bercerita tanpa kata-kata.
- Ilustrasi statis, potret karakter, atau adegan sinematik sederhana dengan animasi.
- Musik dan efek suara untuk membangun suasana.

Implementasi teknisnya dibahas di Bab 17.

## 1.7 Offline dan single player

Karena fokus kita game offline:

- Tidak ada server, login, atau matchmaking.
- Semua data (progres, pengaturan) disimpan lokal di komputer pemain.
- Game bisa dimainkan tanpa koneksi internet, sehingga lebih sederhana dibuat dan diuji.
- Kamu tidak perlu mempelajari fitur multiplayer Godot untuk buku ini.

## Ringkasan Bab 1

- Developer indie harus disiplin soal scope.
- Prioritaskan gameplay, lalu cerita.
- Game loop: input, update, render, ulangi.
- Cerita tanpa voice actor tetap bisa kuat lewat teks, level, dan suara.

## Latihan Bab 1

1. Tulis konsep game pertamamu dalam dua kalimat. Contoh: "Seorang robot kecil mengumpulkan baterai di gua sambil menghindari slime."
2. Tuliskan tiga aksi utama pemain di game itu.
3. Coret satu fitur dari daftar idemu yang sebenarnya tidak penting.

---

# Bab 2 - Mengenal Godot Engine dan Instalasi

## 2.1 Apa itu Godot

Godot adalah game engine gratis dan open source. Engine adalah kumpulan alat dan kode siap pakai (rendering, fisika, audio, input, editor) sehingga kamu tidak perlu membuatnya dari nol.

Poin penting tentang Godot:

- **Gratis dan open source** dengan lisensi MIT. Game yang kamu buat sepenuhnya milikmu, tanpa royalti dan tanpa biaya lisensi engine.
- **Ringan**: editor berupa satu file program, tidak perlu proses instalasi berat.
- **Mendukung 2D dan 3D**. Untuk 2D, Godot memiliki sistem 2D khusus (bukan 3D yang diratakan), sehingga koordinatnya memakai piksel dan terasa natural untuk game 2D.
- **Berbasis node dan scene**: game disusun dari blok-blok kecil yang bisa dipakai ulang.
- **Lintas platform**: bisa dipakai di Windows, macOS, Linux, dan bisa mengekspor game ke beberapa platform.

## 2.2 Godot 3 vs Godot 4

Godot 4 adalah generasi yang aktif dikembangkan, dirilis pertama kali pada 2023. Godot 3 adalah cabang lama yang masih ada tetapi tidak lagi menjadi fokus. Keduanya tidak kompatibel satu sama lain.

**Gunakan Godot 4.x untuk proyek baru.** Saat mencari tutorial di internet, perhatikan versinya. Banyak tutorial lama memakai sintaks Godot 3 yang berbeda, misalnya:

|Godot 3 (lama)|Godot 4 (dipakai di buku ini)|
|---|---|
|`KinematicBody2D`|`CharacterBody2D`|
|`move_and_slide(velocity)`|set `velocity` lalu panggil `move_and_slide()`|
|`onready var`|`@onready var`|
|`export var`|`@export var`|
|`yield(...)`|`await ...`|
|`connect("signal", self, "method")`|`signal.connect(method)`|
|`instance()`|`instantiate()`|
|`TileMap`|`TileMapLayer` (pada versi terbaru)|

## 2.3 Versi Standard vs .NET

Di halaman unduhan, Godot tersedia dalam dua varian:

- **Standard**: mendukung GDScript (dan C++ lewat GDExtension untuk kebutuhan lanjutan).
- **.NET**: menambah dukungan C# sebagai bahasa skrip, membutuhkan .NET SDK.

Untuk pemula, pilih **Standard dengan GDScript**. GDScript dirancang khusus untuk Godot, sintaksnya mirip Python, dan dokumentasi serta tutorial komunitas sebagian besar memakainya.

## 2.4 Mengunduh dan menjalankan Godot

1. Buka situs resmi `godotengine.org`, menu Download.
2. Pilih versi stabil terbaru (bukan versi dev, beta, atau rc) untuk sistem operasimu, varian **Standard**.
3. Ekstrak file zip. Di Windows kamu akan mendapat file `.exe`. Simpan di folder tetap, misalnya `D:\Godot\`.
4. Jalankan program tersebut. Tidak perlu instalasi.

Tips: jika sering memakai Godot, buat shortcut ke program tersebut. Saat versi baru keluar, simpan versi lama selama proyekmu masih memakainya. Hindari mengganti versi engine di tengah proyek tanpa alasan kuat, kecuali pembaruan maintenance (misalnya dari 4.7.1 ke 4.7.2) yang dirancang kompatibel.

## 2.5 Project Manager

Saat dibuka, Godot menampilkan **Project Manager** berisi daftar proyek. Tombol penting:

- **Create**: membuat proyek baru.
- **Import**: membuka proyek yang sudah ada (pilih file `project.godot`).
- **Scan**: mencari proyek di sebuah folder.
- **Asset Library**: tempat mengunduh aset dan add-on gratis.

## 2.6 Membuat proyek pertama

1. Klik **Create**.
2. Isi **Project Name**, misalnya `PetualanganPertama`.
3. Pilih **Project Path** pada folder kosong.
4. Pilih **Renderer**:

|Renderer|Cocok untuk|Catatan|
|---|---|---|
|Forward+|Game 3D modern di PC|Fitur grafis paling lengkap, perlu GPU yang cukup modern|
|Mobile|Perangkat mobile atau PC menengah|Keseimbangan fitur dan performa|
|Compatibility|Perangkat lama, GPU lemah, atau target yang luas|Fitur paling terbatas tetapi paling kompatibel|

Rekomendasi: untuk 2D sederhana atau laptop lama, **Compatibility** sudah cukup dan paling aman. Untuk 3D dengan pencahayaan bagus di PC modern, pilih **Forward+**. Renderer bisa diubah kemudian lewat Project Settings, tetapi beberapa efek visual akan berbeda.

5. Aktifkan opsi **Version Control Metadata** (Git) jika tersedia, agar file `.gitignore` dibuat otomatis.
6. Klik **Create**.

## 2.7 Struktur folder proyek

Setelah proyek dibuat, di dalam foldernya ada:

```
PetualanganPertama/
  project.godot      <- file konfigurasi utama proyek
  icon.svg           <- ikon bawaan
  .godot/            <- cache internal editor (jangan diedit, jangan di-commit ke Git)
  (file dan folder buatanmu)
```

Di dalam Godot, folder proyek dirujuk sebagai **`res://`** (resource). Contoh: `res://player/player.tscn`. Jangan memakai path absolut seperti `C:\Users\...` di dalam kode, karena akan rusak saat proyek dipindah atau diekspor.

Jenis file penting:

|Ekstensi|Arti|
|---|---|
|`.tscn`|Scene (format teks, mudah dibaca Git)|
|`.gd`|Skrip GDScript|
|`.tres`|Resource (data) dalam format teks|
|`.res`|Resource dalam format biner|
|`.import`|Pengaturan impor aset (dibuat otomatis)|

## 2.8 Susunan folder yang disarankan

Rapikan sejak awal. Salah satu pola sederhana:

```
res://
  assets/
    sprites/
    models/
    audio/
      music/
      sfx/
    fonts/
  scenes/
    levels/
    ui/
  entities/
    player/
    enemies/
    items/
  scripts/
    autoload/
  data/
    dialogue/
```

Aturan penamaan yang umum di komunitas Godot:

- File dan folder: `snake_case` (huruf kecil, pemisah garis bawah), misalnya `player_idle.png`. Ini menghindari masalah huruf besar-kecil antar sistem operasi.
- Nama node di scene: `PascalCase`, misalnya `PlayerSprite`.
- Variabel dan fungsi di kode: `snake_case`.
- Nama class: `PascalCase`.
- Konstanta: `HURUF_BESAR_DENGAN_UNDERSCORE`.

## Ringkasan Bab 2

- Godot gratis, ringan, open source, mendukung 2D dan 3D.
- Pakai Godot 4.x Standard dengan GDScript.
- `res://` adalah root proyekmu, `user://` adalah folder data pemain.
- Rapikan struktur folder dan konsisten dalam penamaan.

## Latihan Bab 2

1. Unduh Godot dan buat proyek bernama `Latihan01`.
2. Buat struktur folder seperti pada subbab 2.8 melalui panel FileSystem (klik kanan > New Folder).
3. Buka `Project > Project Settings` dan temukan nama proyekmu.

---

# Bab 3 - Tur Antarmuka Editor Godot

## 3.1 Bagian-bagian utama editor

Saat proyek terbuka, kamu melihat beberapa area:

```
+--------------------------------------------------------------+
| Menu (Scene, Project, Debug, Editor, Help)   2D 3D Script ... Play |
+----------+---------------------------------------+-----------+
| Scene    |                                       | Inspector |
| (daftar  |            Viewport                   | (properti |
|  node)   |     (area kerja 2D atau 3D)           |  node     |
+----------+                                       |  terpilih)|
| FileSys  |                                       |           |
| (file    +---------------------------------------+ Node dock |
|  proyek) |  Panel bawah: Output, Debugger, dll.  |           |
+----------+---------------------------------------+-----------+
```

|Area|Fungsi|
|---|---|
|**Scene dock**|Menampilkan hierarki node dalam scene yang sedang dibuka|
|**FileSystem dock**|Menampilkan semua file proyek di `res://`|
|**Viewport**|Area visual tempat kamu menata objek, dengan mode 2D dan 3D|
|**Inspector**|Mengubah properti node atau resource yang dipilih|
|**Node dock**|Tab untuk melihat dan menghubungkan **Signals**, serta mengatur **Groups**|
|**Panel bawah**|Output (hasil `print`), Debugger, Animation, dan lainnya|

## 3.2 Tombol utama di bagian atas

Di bagian tengah atas terdapat pilihan ruang kerja:

- **2D**: menata objek 2D.
- **3D**: menata objek 3D.
- **Script**: menulis kode.
- **AssetLib**: mengunduh aset.

Di sisi kanan atas ada kontrol menjalankan game:

|Tombol/Pintasan|Fungsi|
|---|---|
|F5|Jalankan proyek (Main Scene)|
|F6|Jalankan scene yang sedang dibuka|
|Tombol Pause dan Stop|Menjeda dan menghentikan game|
|Ctrl+S|Simpan scene|

Saat pertama kali menekan F5, Godot akan menanyakan Main Scene (scene awal game). Kamu bisa mengubahnya kapan saja di `Project > Project Settings > Application > Run > Main Scene`.

## 3.3 Navigasi viewport

**Viewport 2D:**

- Geser tampilan: tahan tombol tengah mouse (atau Space + drag).
- Zoom: scroll mouse.
- Alat: Select, Move, Rotate, Scale.

**Viewport 3D:**

- Orbit (putar kamera): tahan tombol tengah mouse dan geser.
- Geser (pan): Shift + tombol tengah mouse.
- Zoom: scroll mouse.
- Fly mode: tahan tombol kanan mouse dan gunakan W, A, S, D.

## 3.4 Inspector

Inspector menunjukkan semua properti dari node yang dipilih, dikelompokkan berdasarkan class. Contoh pada `Sprite2D`: `Texture`, `Offset`, `Flip H`, `Modulate`. Perubahan di Inspector langsung tampak di viewport.

Properti yang kamu tandai `@export` di skrip juga muncul di Inspector (dibahas di Bab 5).

## 3.5 Dokumentasi bawaan

Godot memiliki dokumentasi offline di dalam editor. Tekan **F1** atau klik `Help > Search Help`, lalu ketik nama class atau fungsi, misalnya `CharacterBody2D`. Kamu akan melihat daftar properti, metode, dan sinyal beserta penjelasannya. Biasakan membuka dokumentasi ini sebelum mencari di internet.

Di editor skrip, tahan Ctrl lalu klik nama class atau fungsi untuk melompat ke dokumentasinya.

## 3.6 Bekerja dengan dua jendela

Jika layarmu cukup besar, kamu bisa memisahkan editor skrip atau viewport ke jendela terpisah. Ini opsional. Untuk pemula, susunan bawaan sudah memadai.

## Ringkasan Bab 3

- Kenali lima area utama: Scene, FileSystem, Viewport, Inspector, Node dock.
- F5 menjalankan proyek, F6 menjalankan scene aktif.
- F1 membuka dokumentasi offline.

## Latihan Bab 3

1. Buat scene baru dengan root `Node2D`, tambahkan `Sprite2D`, dan tarik `icon.svg` ke properti `Texture` di Inspector.
2. Simpan scene sebagai `res://scenes/latihan.tscn`, lalu jalankan dengan F6.
3. Buka dokumentasi `Sprite2D` dengan F1 dan temukan properti `flip_h`.

---

# Bab 4 - Konsep Inti: Node, Scene, Scene Tree, dan Resource

Bab ini adalah fondasi terpenting dalam Godot. Luangkan waktu untuk memahaminya.

## 4.1 Node

**Node** adalah blok bangunan paling dasar di Godot. Setiap node punya satu tujuan spesifik.

Contoh:

- `Sprite2D`: menampilkan gambar 2D.
- `CollisionShape2D`: mendefinisikan bentuk tabrakan.
- `AudioStreamPlayer`: memutar suara.
- `Label`: menampilkan teks.
- `Camera3D`: kamera di dunia 3D.

Setiap node memiliki:

1. **Nama**.
2. **Properti** yang bisa diubah.
3. **Fungsi** yang bisa dipanggil.
4. **Signal** yang bisa dipancarkan saat sesuatu terjadi.
5. Bisa memiliki **node anak** (children) dan satu **induk** (parent).

## 4.2 Keluarga node yang perlu kamu tahu

Semua node berasal dari class `Node`. Dari sana bercabang beberapa keluarga utama:

```
Node
 |-- CanvasItem
 |     |-- Node2D        <- semua node 2D (Sprite2D, CharacterBody2D, Camera2D, ...)
 |     |-- Control       <- semua node UI (Label, Button, Panel, ...)
 |-- Node3D              <- semua node 3D (MeshInstance3D, Camera3D, ...)
 |-- (node non-visual: Timer, AudioStreamPlayer, HTTPRequest, ...)
```

Rule of thumb:

- Objek di dunia 2D: turunan `Node2D`.
- Antarmuka (menu, HUD, tombol): turunan `Control`.
- Objek di dunia 3D: turunan `Node3D`.

## 4.3 Scene

**Scene** adalah kumpulan node yang tersusun dalam pohon (tree) dan disimpan sebagai satu file `.tscn`. Satu scene bisa berupa apa saja:

- Satu karakter (player).
- Satu musuh.
- Satu item koin.
- Satu level.
- Satu menu.

Contoh scene `Player`:

```
Player (CharacterBody2D)
 |-- Sprite2D
 |-- CollisionShape2D
 |-- Camera2D
```

Node paling atas disebut **root node** dari scene tersebut.

Analogi: scene itu seperti resep atau cetakan LEGO. Kamu mendefinisikannya sekali, lalu bisa memakainya berkali-kali.

## 4.4 Instancing: memakai scene berulang kali

Scene bisa dimasukkan ke scene lain. Ini disebut **instancing** (membuat instance atau salinan hidup dari scene).

Contoh: scene `Coin` dibuat sekali. Di scene `Level1`, kamu bisa menaruh 50 koin dengan menyalin instance-nya. Jika kemudian kamu mengubah `Coin` (misalnya warnanya), seluruh 50 koin ikut berubah.

Cara instancing di editor: klik ikon rantai di Scene dock (`Instantiate Child Scene`) atau tarik file `.tscn` dari FileSystem ke viewport.

Cara instancing lewat kode:

```gdscript
var coin_scene: PackedScene = preload("res://entities/items/coin.tscn")

func spawn_coin(pos: Vector2) -> void:
    var coin = coin_scene.instantiate()
    coin.position = pos
    add_child(coin)
```

Penjelasan:

- `preload(...)` memuat file saat skrip dikompilasi, sehingga cepat.
- `PackedScene` adalah tipe data untuk scene yang sudah dimuat.
- `instantiate()` membuat salinan node dari scene tersebut.
- `add_child(coin)` memasukkan koin ke dalam scene tree. **Tanpa add_child, objek tidak muncul dan tidak berjalan.**

## 4.5 Scene Tree

Saat game berjalan, semua scene yang aktif tergabung dalam satu pohon besar bernama **Scene Tree**. Root pohon ini adalah objek `Window` (viewport utama). Scene utama yang kamu jalankan menjadi anak dari root tersebut.

Mengapa penting? Karena banyak hal bergantung pada posisi node di pohon:

- **Urutan proses**: node diproses dari atas ke bawah (induk sebelum anak untuk `_process`).
- **Urutan gambar**: node yang lebih bawah di daftar dan masih satu level digambar di atas node sebelumnya.
- **Transform**: posisi, rotasi, dan skala anak relatif terhadap induknya. Jika induk digeser, anak ikut bergeser.
- **Akses node**: kamu bisa menemukan node lain lewat path di pohon.

Akses ke Scene Tree dari kode dilakukan dengan `get_tree()`.

## 4.6 Mengakses node lain lewat path

Dari sebuah skrip, kamu bisa mengakses node anak dengan sintaks `$NamaNode`:

```gdscript
extends CharacterBody2D

func _ready() -> void:
    $Sprite2D.modulate = Color.RED    # mewarnai sprite jadi merah
    print($CollisionShape2D.name)     # mencetak "CollisionShape2D"
```

`$Sprite2D` adalah singkatan dari `get_node("Sprite2D")`. Untuk node yang lebih dalam: `$Body/Sprite2D`. Untuk node induk: `get_parent()`.

Jika path salah, kamu mendapat error "Invalid access to property or key ... on a base object of type 'null instance'". Penyebab paling umum: nama node berubah atau salah ketik.

**Unique Name (nama unik).** Jika kamu klik kanan sebuah node di Scene dock lalu pilih **Access as Unique Name**, node itu bisa diakses dengan `%NamaNode` dari mana saja dalam scene yang sama, tanpa peduli posisinya. Ini lebih tahan terhadap perubahan struktur.

## 4.7 Transform: posisi, rotasi, skala

**Di 2D** (`Node2D`):

- `position`: `Vector2(x, y)`.
- `rotation`: dalam radian (bukan derajat). Gunakan `rotation_degrees` untuk derajat.
- `scale`: `Vector2`.
- Sumbu **X** positif ke kanan, sumbu **Y** positif ke **bawah**. (Ini penting dan sering membingungkan: di 2D layar, nilai Y yang lebih besar berarti lebih rendah.)

**Di 3D** (`Node3D`):

- `position`: `Vector3(x, y, z)`.
- `rotation`: `Vector3` dalam radian (`rotation_degrees` untuk derajat).
- `scale`: `Vector3`.
- Sumbu **Y** positif ke **atas**. Arah "maju" bawaan adalah sumbu **-Z** (negatif Z). Kamera dan banyak node menghadap ke -Z.

Tabel ringkas:

||2D|3D|
|---|---|---|
|Tipe posisi|`Vector2`|`Vector3`|
|Atas|Y negatif|Y positif|
|Maju (default)|tergantung desain|-Z|
|Satuan|piksel|meter (umumnya 1 unit = 1 meter)|

## 4.8 Resource

**Resource** adalah wadah **data** yang bisa disimpan ke file dan dipakai bersama. Berbeda dengan Node, resource tidak berada di Scene Tree dan tidak punya posisi.

Contoh resource bawaan: `Texture2D` (gambar), `AudioStream` (suara), `Mesh`, `Material`, `Font`, `PackedScene`, `SpriteFrames`, `TileSet`.

Kamu juga bisa membuat resource sendiri untuk menyimpan data game, misalnya data senjata, data dialog, atau statistik musuh. Ini akan dipakai di Bab 17. Menyimpan data dalam Resource membuatmu bisa mengeditnya di Inspector tanpa mengubah kode.

Perbedaan singkat:

||Node|Resource|
|---|---|---|
|Ada di Scene Tree|Ya|Tidak|
|Punya posisi di dunia game|2D/3D: ya|Tidak|
|Fungsi utama|Perilaku dan tampilan|Data yang dibagikan|
|Contoh|`Sprite2D`, `Label`|`Texture2D`, `AudioStream`|

## 4.9 Prinsip komposisi

Godot mendorong **komposisi**: membangun objek kompleks dengan menggabungkan node-node kecil, bukan dengan pewarisan class yang sangat dalam.

Contoh: musuh bisa terdiri dari `CharacterBody2D` + `AnimatedSprite2D` + `CollisionShape2D` + node `HealthComponent` + node `Hurtbox`. Setiap bagian kecil dan bisa dipakai ulang di objek lain.

## Ringkasan Bab 4

- Node adalah blok bangunan, scene adalah kumpulan node yang disimpan di file.
- Instancing memungkinkan satu scene dipakai berkali-kali.
- Scene Tree adalah pohon semua node yang aktif saat game jalan.
- `$Nama` mengakses node anak, `%Nama` mengakses node dengan Unique Name.
- Y 2D menghadap ke bawah, Y 3D menghadap ke atas.
- Resource adalah wadah data yang bisa dibagikan dan disimpan.

## Latihan Bab 4

1. Buat scene `Coin` (root `Area2D`, anak `Sprite2D` dan `CollisionShape2D`). Simpan.
2. Buat scene `Level1` (root `Node2D`) dan instance `Coin` tiga kali. Geser posisinya masing-masing.
3. Ubah warna `Sprite2D` di scene `Coin` (properti `Modulate`) dan lihat apakah ketiga instance ikut berubah di `Level1`.

---

# Bab 5 - Dasar Pemrograman GDScript

GDScript adalah bahasa pemrograman bawaan Godot. Sintaksnya mirip Python: indentasi menentukan blok kode.

## 5.1 Membuat skrip

1. Klik kanan sebuah node di Scene dock, pilih **Attach Script**.
2. Tentukan lokasi dan nama file, misalnya `res://entities/player/player.gd`.
3. Klik Create. Editor skrip akan terbuka.

Setiap skrip diawali dengan `extends`, yang menyatakan class node apa yang diperluas:

```gdscript
extends CharacterBody2D
```

Artinya: skrip ini adalah perpanjangan dari `CharacterBody2D`, sehingga semua kemampuan class itu bisa dipakai.

## 5.2 Komentar dan print

```gdscript
# Ini komentar satu baris. Tidak dijalankan.

func _ready() -> void:
    print("Halo, Godot!")   # tampil di panel Output
```

`print()` adalah alat debugging paling dasar dan paling sering dipakai.

## 5.3 Variabel dan tipe data

Variabel adalah tempat menyimpan nilai. Dalam GDScript, deklarasi memakai `var`:

```gdscript
var score = 0
var player_name = "Budi"
```

Lebih baik lagi: **beri tipe data** (typed GDScript). Ini membuat editor bisa membantu dengan autocomplete dan mendeteksi kesalahan lebih awal, serta umumnya lebih cepat.

```gdscript
var score: int = 0
var speed: float = 200.0
var player_name: String = "Budi"
var is_alive: bool = true
var direction: Vector2 = Vector2.ZERO
```

Atau biarkan Godot menyimpulkan tipenya dengan `:=`:

```gdscript
var lives := 3               # int
var gravity_scale := 1.5     # float
```

Tipe data dasar:

|Tipe|Isi|Contoh|
|---|---|---|
|`int`|Bilangan bulat|`10`, `-3`|
|`float`|Bilangan desimal|`3.14`, `200.0`|
|`bool`|Benar atau salah|`true`, `false`|
|`String`|Teks|`"Halo"`|
|`Vector2`|Pasangan x, y|`Vector2(100, 50)`|
|`Vector3`|Tiga nilai x, y, z|`Vector3(0, 1, 0)`|
|`Color`|Warna|`Color.RED`, `Color(1, 0, 0)`|
|`Array`|Daftar berurutan|`[1, 2, 3]`|
|`Dictionary`|Pasangan kunci-nilai|`{"hp": 10}`|

Catatan: `200` adalah `int`, sedangkan `200.0` adalah `float`. Membagi dua integer menghasilkan integer (`5 / 2` hasilnya `2`). Gunakan `5 / 2.0` atau `5.0 / 2` untuk hasil desimal.

## 5.4 Konstanta

Nilai yang tidak berubah dideklarasikan dengan `const`:

```gdscript
const MAX_HEALTH: int = 5
const SAVE_PATH: String = "user://savegame.json"
```

## 5.5 Operator

```gdscript
var a := 10
var b := 3

print(a + b)    # 13  penjumlahan
print(a - b)    # 7   pengurangan
print(a * b)    # 30  perkalian
print(a / b)    # 3   pembagian (integer)
print(a % b)    # 1   sisa bagi (modulo)

a += 5          # sama dengan a = a + 5
a -= 1
a *= 2

print(a == b)   # sama dengan
print(a != b)   # tidak sama dengan
print(a > b)    # lebih besar
print(a <= b)   # lebih kecil atau sama dengan

# Operator logika
# and  (dan),  or  (atau),  not  (negasi)
```

## 5.6 Percabangan (if, elif, else)

```gdscript
var health := 3

if health <= 0:
    print("Game over")
elif health == 1:
    print("Hati-hati, nyawa tinggal satu")
else:
    print("Aman")
```

Ingat: tanda titik dua `:` di akhir baris dan **indentasi** (Godot memakai tab secara bawaan) wajib ada.

Kombinasi kondisi:

```gdscript
if is_alive and health > 0:
    print("Masih hidup")
```

## 5.7 match (seperti switch)

Cocok untuk memilih berdasarkan banyak kemungkinan nilai:

```gdscript
var state := "idle"

match state:
    "idle":
        print("Diam")
    "run":
        print("Berlari")
    "jump":
        print("Melompat")
    _:
        print("State tidak dikenal")   # _ berarti "selain semua di atas"
```

## 5.8 Perulangan

**for** untuk mengulang sejumlah kali atau setiap elemen:

```gdscript
for i in range(5):
    print(i)           # 0, 1, 2, 3, 4

var items: Array = ["Pedang", "Perisai", "Ramuan"]
for item in items:
    print(item)
```

**while** untuk mengulang selama kondisi benar:

```gdscript
var countdown := 3
while countdown > 0:
    print(countdown)
    countdown -= 1
```

Hati-hati: `while` dengan kondisi yang tidak pernah salah akan membuat game membeku. Di dalam `_process`, hindari loop panjang.

Kata kunci: `break` (keluar dari loop), `continue` (lompat ke iterasi berikutnya).

## 5.9 Fungsi

Fungsi adalah blok kode bernama yang bisa dipanggil berulang kali.

```gdscript
func tambah(a: int, b: int) -> int:
    return a + b

func sapa(nama: String) -> void:
    print("Halo, ", nama)

func _ready() -> void:
    var hasil := tambah(2, 3)    # hasil = 5
    sapa("Dewi")
```

- Parameter: nilai masukan fungsi (`a`, `b`).
- `-> int`: tipe data yang dikembalikan. `-> void` berarti tidak mengembalikan apa-apa.
- Parameter bisa memiliki nilai bawaan: `func heal(amount: int = 1) -> void:`.
- Fungsi yang diawali garis bawah, misalnya `_ready`, `_process`, adalah konvensi untuk fungsi "bawaan engine" atau fungsi privat.

## 5.10 Array

Array menyimpan daftar nilai.

```gdscript
var inventory: Array[String] = ["Kunci", "Peta"]

inventory.append("Obor")          # tambah di akhir
print(inventory[0])               # "Kunci" (indeks mulai dari 0)
print(inventory.size())           # 3
inventory.erase("Peta")           # hapus berdasarkan nilai
print(inventory.has("Kunci"))     # true
inventory.pop_back()              # ambil dan hapus elemen terakhir
```

`Array[String]` adalah array bertipe: hanya boleh berisi String.

## 5.11 Dictionary

Dictionary menyimpan pasangan kunci dan nilai.

```gdscript
var stats: Dictionary = {
    "hp": 10,
    "attack": 3,
    "name": "Slime"
}

print(stats["hp"])                  # 10
stats["hp"] -= 2                    # ubah nilai
stats["defense"] = 1                # tambah kunci baru
print(stats.has("attack"))          # true
print(stats.get("speed", 100))      # ambil, jika tidak ada pakai 100

for key in stats:
    print(key, " = ", stats[key])
```

## 5.12 Variabel anggota, @export, dan @onready

Variabel yang dideklarasikan di luar fungsi adalah **variabel anggota** (milik objek), dan bisa dipakai di semua fungsi dalam skrip.

**@export** menampilkan variabel di Inspector sehingga bisa diubah tanpa mengedit kode:

```gdscript
extends CharacterBody2D

@export var speed: float = 200.0
@export var max_health: int = 3
@export_range(0.0, 1.0) var volume: float = 0.5
@export var coin_scene: PackedScene
@export_multiline var description: String = ""
```

**@onready** mengisi variabel setelah node siap (setelah semua anak masuk ke pohon). Ini diperlukan karena anak belum ada saat variabel biasa dihitung:

```gdscript
@onready var sprite: Sprite2D = $Sprite2D
@onready var anim: AnimationPlayer = $AnimationPlayer
```

## 5.13 enum

`enum` membuat daftar nilai bernama. Berguna untuk state (keadaan):

```gdscript
enum State { IDLE, WALK, JUMP, HURT }

var current_state: State = State.IDLE

func _physics_process(_delta: float) -> void:
    match current_state:
        State.IDLE:
            pass
        State.WALK:
            pass
```

`pass` artinya "tidak melakukan apa-apa" (penanda blok kosong).

## 5.14 class_name dan inheritance

Dengan `class_name`, skripmu menjadi tipe yang dikenali seluruh proyek:

```gdscript
class_name Enemy
extends CharacterBody2D

@export var health: int = 3

func take_damage(amount: int) -> void:
    health -= amount
    if health <= 0:
        queue_free()
```

- `queue_free()` menghapus node dengan aman di akhir frame.
- Class lain bisa `extends Enemy` untuk mewarisi semua isi class ini.
- `class_name` juga membuat tipe tersebut muncul saat menambah node baru.

## 5.15 Signal (pengantar)

Signal adalah mekanisme "pemberitahuan": sebuah node memberi tahu bahwa sesuatu terjadi tanpa perlu tahu siapa yang mendengarkan. Detailnya ada di Bab 12. Contoh singkat:

```gdscript
signal health_changed(new_value: int)

func take_damage(amount: int) -> void:
    health -= amount
    health_changed.emit(health)    # memancarkan signal
```

## 5.16 Kesalahan sintaks yang sering terjadi

|Gejala|Penyebab umum|
|---|---|
|"Unexpected indent"|Campuran tab dan spasi, atau indentasi salah|
|"Expected ':'"|Lupa titik dua setelah `if`, `func`, `for`|
|"Identifier not declared"|Salah ketik nama variabel atau variabel di fungsi lain|
|"Invalid call. Nonexistent function"|Salah nama fungsi atau tipe objek tidak punya fungsi itu|
|"null instance"|Node yang diakses tidak ditemukan atau belum siap|

## Ringkasan Bab 5

- GDScript mirip Python, memakai indentasi dan titik dua.
- Gunakan tipe data (`var x: int`) agar editor lebih membantu.
- `@export` untuk mengatur nilai di Inspector, `@onready` untuk mengambil referensi node.
- `Array` dan `Dictionary` untuk menyimpan koleksi data.
- `enum` + `match` bagus untuk state.

## Latihan Bab 5

1. Buat skrip yang di `_ready()` mencetak angka 1 sampai 10 dengan `for`.
2. Buat fungsi `hitung_luas_persegi(sisi: float) -> float` dan cetak hasilnya.
3. Buat `Dictionary` berisi data tiga item (nama, harga) lalu cetak semuanya dengan `for`.

---

# Bab 6 - Siklus Hidup Node, Delta Time, dan Input

## 6.1 Fungsi bawaan (callback) penting

Godot memanggil fungsi tertentu secara otomatis pada saat tertentu. Fungsi ini disebut **callback**. Kamu cukup menulis isinya.

|Fungsi|Kapan dipanggil|Dipakai untuk|
|---|---|---|
|`_init()`|Saat objek dibuat|Inisialisasi sangat awal (jarang diperlukan)|
|`_ready()`|Sekali, saat node dan semua anaknya masuk ke Scene Tree|Setup awal, mengambil referensi, menghubungkan signal|
|`_process(delta)`|Setiap frame gambar|Logika visual, UI, hal yang tidak berkaitan dengan fisika|
|`_physics_process(delta)`|Setiap tick fisika (bawaan 60 kali per detik)|Pergerakan karakter, fisika, tabrakan|
|`_input(event)`|Setiap ada kejadian input|Menangani input mentah|
|`_unhandled_input(event)`|Input yang belum ditangani oleh UI|Input gameplay (disarankan untuk aksi game)|
|`_exit_tree()`|Saat node keluar dari tree|Pembersihan|

Contoh:

```gdscript
extends Node2D

func _ready() -> void:
    print("Node siap")

func _process(delta: float) -> void:
    print("Frame baru, delta = ", delta)

func _physics_process(delta: float) -> void:
    print("Tick fisika, delta = ", delta)
```

Pesan di Output akan sangat ramai. Jangan lupa hapus `print` yang dipanggil tiap frame setelah selesai uji.

## 6.2 Delta time

`delta` adalah waktu (dalam detik) sejak frame sebelumnya. Misalnya pada 60 FPS, `delta` kira-kira `0.0167`.

Mengapa penting? Komputer yang berbeda berjalan pada FPS berbeda. Tanpa delta, objek akan bergerak lebih cepat di komputer yang lebih cepat.

```gdscript
# SALAH: kecepatan bergantung FPS
position.x += 5

# BENAR: bergerak 300 piksel per detik di FPS berapa pun
position.x += 300 * delta
```

Aturan: **nilai yang berubah terus-menerus karena waktu, kalikan dengan delta**. Catatan: `move_and_slide()` pada `CharacterBody` sudah memperhitungkan delta sendiri untuk `velocity`, sehingga kamu **tidak** mengalikan `velocity` dengan delta saat memanggilnya. Namun gravitasi yang ditambahkan ke `velocity` per frame tetap dikalikan delta (karena percepatan).

## 6.3 _process vs _physics_process

- Pakai `_physics_process` untuk apapun yang melibatkan body fisika dan pergerakan karakter. Interval waktunya tetap sehingga hasil lebih stabil dan konsisten.
- Pakai `_process` untuk hal visual atau non-fisika: animasi UI, efek, kamera halus, timer sederhana.

## 6.4 Input dasar

Godot memakai sistem **Input Map**: kamu mendefinisikan **aksi** bernama (misalnya `jump`) dan menetapkan tombol atau tombol-tombol yang memicunya. Kode membaca aksi, bukan tombol spesifik, sehingga mudah mengubah kontrol dan mendukung gamepad.

Fungsi input yang sering dipakai (kelas `Input`):

```gdscript
# Apakah aksi sedang ditahan?
if Input.is_action_pressed("move_right"):
    ...

# Apakah aksi baru saja ditekan di frame ini? (sekali saja)
if Input.is_action_just_pressed("jump"):
    ...

# Apakah aksi baru saja dilepas?
if Input.is_action_just_released("jump"):
    ...

# Nilai sumbu antara -1 dan 1 (kiri dan kanan)
var dir_x: float = Input.get_axis("move_left", "move_right")

# Vektor arah 2D, sudah dinormalisasi (maksimum panjang 1)
var dir: Vector2 = Input.get_vector("move_left", "move_right", "move_up", "move_down")
```

Perbedaan kunci:

- `is_action_pressed`: bernilai true **selama tombol ditahan**.
- `is_action_just_pressed`: bernilai true **hanya pada frame saat tombol mulai ditekan**. Cocok untuk lompat dan interaksi.

## 6.5 Input berbasis event

Untuk menangani event tunggal (misalnya klik mouse atau tombol interaksi), gunakan `_unhandled_input`:

```gdscript
func _unhandled_input(event: InputEvent) -> void:
    if event.is_action_pressed("interact"):
        interact()
        get_viewport().set_input_as_handled()   # tandai input sudah ditangani
```

Jenis event umum: `InputEventKey`, `InputEventMouseButton`, `InputEventMouseMotion`, `InputEventJoypadButton`.

## 6.6 Vektor dan normalisasi (konsep penting)

Jika pemain menekan kanan dan atas bersamaan, vektor arah menjadi `(1, -1)` yang panjangnya sekitar 1,41. Akibatnya gerak diagonal lebih cepat. Solusinya **normalisasi**: ubah panjang vektor menjadi 1 tanpa mengubah arah.

```gdscript
var dir := Vector2(1, -1).normalized()   # panjang jadi 1
```

`Input.get_vector(...)` sudah menangani ini untukmu, jadi lebih disarankan untuk gerak 8 arah.

Operasi vektor yang sering dipakai:

```gdscript
var a := Vector2(3, 4)
print(a.length())                         # 5.0, panjang vektor
print(a.normalized())                     # arah dengan panjang 1
print(a.distance_to(Vector2(0, 0)))       # jarak antar titik
print(a.direction_to(Vector2(10, 4)))     # arah menuju titik lain (sudah normal)
print(Vector2.ZERO, Vector2.UP, Vector2.RIGHT)
```

## 6.7 Timer dan await

Untuk menunggu beberapa saat tanpa menahan game:

```gdscript
func flash_red() -> void:
    $Sprite2D.modulate = Color.RED
    await get_tree().create_timer(0.2).timeout    # tunggu 0.2 detik
    $Sprite2D.modulate = Color.WHITE
```

`await` menjeda fungsi tersebut saja sampai sinyal `timeout` terpancar. Game tetap berjalan normal.

Alternatif: node `Timer` di scene, dengan properti `Wait Time`, `One Shot`, dan `Autostart`, serta sinyal `timeout`.

## Ringkasan Bab 6

- `_ready` sekali saat awal, `_process` tiap frame, `_physics_process` tiap tick fisika.
- Kalikan perubahan berbasis waktu dengan `delta`.
- Pakai Input Map dan baca aksi (bukan tombol langsung).
- `is_action_just_pressed` untuk aksi sekali tekan.
- Normalisasi vektor gerak agar diagonal tidak lebih cepat.

## Latihan Bab 6

1. Buat `Sprite2D` yang berputar terus: `rotation += 2.0 * delta` di `_process`.
2. Buat sprite bergerak ke kanan 100 piksel per detik, lalu reset ke posisi awal saat melewati x = 600.
3. Cetak "Lompat!" setiap kali tombol Space ditekan (setelah Bab 7 untuk Input Map).

---

# Bab 7 - Menyiapkan Project dengan Benar

Sebelum membuat game, ada beberapa pengaturan yang menghemat banyak masalah di kemudian hari.

## 7.1 Input Map

Buka `Project > Project Settings > Input Map`.

1. Ketik nama aksi di kolom atas, misalnya `move_left`, lalu klik **Add**.
2. Klik ikon `+` di sebelah aksi, tekan tombol keyboard yang diinginkan, klik OK.
3. Kamu bisa menambahkan lebih dari satu tombol per aksi (keyboard dan gamepad).

Daftar aksi yang disarankan untuk dimulai:

|Aksi|Tombol keyboard|Gamepad (opsional)|
|---|---|---|
|`move_left`|A, Panah Kiri|Stick kiri ke kiri|
|`move_right`|D, Panah Kanan|Stick kiri ke kanan|
|`move_up`|W, Panah Atas|Stick kiri ke atas|
|`move_down`|S, Panah Bawah|Stick kiri ke bawah|
|`jump`|Space|Tombol bawah (A/Cross)|
|`interact`|E|Tombol kiri (X/Square)|
|`attack`|J atau klik kiri mouse|Tombol kanan (B/Circle)|
|`pause`|Escape|Start|

Untuk game 3D, kamu bisa menambah `move_forward` dan `move_back` (atau memakai `move_up` dan `move_down` yang dipetakan sebagai maju dan mundur).

Aksi bawaan seperti `ui_accept`, `ui_cancel`, `ui_left`, `ui_right` dipakai oleh sistem UI. Jangan dihapus.

## 7.2 Ukuran jendela dan stretch

Buka `Project Settings > Display > Window`:

- **Viewport Width / Height**: resolusi dasar game, misalnya `1280 x 720` untuk game 2D umum, atau `320 x 180` untuk pixel art beresolusi rendah.
- **Stretch > Mode**:
    - `canvas_items`: UI dan gambar menyesuaikan ukuran jendela dengan tajam. Umum untuk game 2D.
    - `viewport`: seluruh game dirender di resolusi dasar lalu diperbesar. Cocok untuk pixel art yang konsisten.
    - `disabled`: tidak ada penskalaan.
- **Stretch > Aspect**: `keep` (pertahankan rasio dengan garis hitam) atau `expand` (isi jendela).

## 7.3 Pixel art

Jika memakai pixel art, atur filter tekstur agar tidak buram:

`Project Settings > Rendering > Textures > Canvas Textures > Default Texture Filter` ubah menjadi **Nearest**.

Aktifkan juga `Rendering > 2D > Snap` (opsi pembulatan posisi ke piksel) sesuai kebutuhan, dan atur Stretch Mode ke `viewport` atau `canvas_items` dengan nilai yang sesuai.

## 7.4 Main Scene

`Project Settings > Application > Run > Main Scene`: pilih scene yang pertama kali berjalan saat game dimulai (biasanya menu utama atau level uji).

## 7.5 Layer fisika bernama

Di `Project Settings > Layer Names > 2D Physics` (dan `3D Physics`), beri nama layer agar mudah dipahami saat mengatur collision. Contoh:

|Layer|Nama|
|---|---|
|1|world|
|2|player|
|3|enemy|
|4|pickup|
|5|player_hitbox|
|6|enemy_hitbox|

Pembahasan lengkap tentang layer dan mask ada di Bab 9.

## 7.6 FPS dan fisika

`Project Settings > Physics > Common`:

- `Physics Ticks per Second` (bawaan 60): jumlah update fisika per detik.

`Project Settings > Display > Window > V-Sync` bisa diaktifkan agar gambar tidak sobek (tearing).

## 7.7 Mengaktifkan pengaturan lanjutan

Di jendela Project Settings ada toggle **Advanced Settings**. Aktifkan jika ingin melihat semua pengaturan. Untuk pemula, pengaturan dasar sudah cukup.

## Ringkasan Bab 7

- Definisikan Input Map sejak awal dengan nama aksi yang konsisten.
- Atur resolusi dasar dan stretch mode sesuai gaya visual.
- Pixel art butuh texture filter Nearest.
- Beri nama layer fisika.

## Latihan Bab 7

1. Buat semua aksi pada tabel 7.1 di proyekmu.
2. Atur resolusi 1280 x 720 dengan Stretch Mode `canvas_items`.
3. Beri nama minimal empat layer fisika 2D.

---

# Bab 8 - Game 2D Pertama: Player yang Bisa Bergerak

Pada bab ini kamu membuat karakter yang bisa dikendalikan. Kita akan membuat dua versi: platformer (tampak samping, ada gravitasi) dan top-down (tampak atas, 8 arah).

## 8.1 Mengenal CharacterBody2D

`CharacterBody2D` adalah node khusus untuk karakter yang dikendalikan lewat kode (pemain dan musuh). Ia tidak dipengaruhi fisika secara otomatis, kamu yang menentukan geraknya, tetapi ia bisa mendeteksi tabrakan dan meluncur (slide) di permukaan.

Konsep kunci:

- `velocity`: properti `Vector2` berisi kecepatan karakter (piksel per detik).
- `move_and_slide()`: fungsi yang menggerakkan karakter sesuai `velocity`, menangani tabrakan, dan menghitung delta otomatis.
- `is_on_floor()`, `is_on_wall()`, `is_on_ceiling()`: mengecek kontak setelah `move_and_slide()`.

## 8.2 Menyiapkan scene Player (platformer)

1. Buat scene baru, pilih **Other Node**, tambahkan `CharacterBody2D`, ganti nama menjadi `Player`.
2. Tambahkan anak `Sprite2D` (isi `Texture` dengan gambar karakter, atau pakai `icon.svg` untuk sementara).
3. Tambahkan anak `CollisionShape2D`. Di Inspector pada `Shape`, pilih `New RectangleShape2D` (atau `CapsuleShape2D`, sering lebih halus untuk karakter) lalu atur ukurannya agar pas dengan sprite.
4. Tambahkan anak `Camera2D` agar kamera mengikuti pemain.
5. Atur node `Player` ke group `player` (tab Node di sebelah Inspector > Groups > tulis `player` > Add).
6. Simpan sebagai `res://entities/player/player.tscn`.

Susunan akhir:

```
Player (CharacterBody2D)
 |-- Sprite2D
 |-- CollisionShape2D
 |-- Camera2D
```

Catatan: jika node menampilkan ikon segitiga kuning peringatan, biasanya ada hal yang belum diisi, misalnya `CollisionShape2D` belum punya `Shape`. Arahkan kursor ke ikon untuk melihat pesannya.

## 8.3 Skrip pergerakan platformer

Tempelkan skrip pada node `Player`:

```gdscript
extends CharacterBody2D

@export var speed: float = 200.0
@export var jump_velocity: float = -380.0

@onready var sprite: Sprite2D = $Sprite2D


func _physics_process(delta: float) -> void:
    # 1. Gravitasi: tambahkan ke velocity jika di udara
    if not is_on_floor():
        velocity += get_gravity() * delta

    # 2. Lompat: hanya jika menyentuh lantai
    if Input.is_action_just_pressed("jump") and is_on_floor():
        velocity.y = jump_velocity

    # 3. Gerak horizontal
    var direction: float = Input.get_axis("move_left", "move_right")
    if direction != 0.0:
        velocity.x = direction * speed
        sprite.flip_h = direction < 0.0       # balik sprite saat menghadap kiri
    else:
        velocity.x = move_toward(velocity.x, 0.0, speed)

    # 4. Terapkan gerak
    move_and_slide()
```

Penjelasan baris demi baris:

- `get_gravity()` mengembalikan vektor gravitasi (dari pengaturan fisika proyek). Dikalikan `delta` karena gravitasi adalah percepatan.
- `jump_velocity` negatif karena sumbu Y 2D positif ke bawah, sehingga lompat berarti Y negatif.
- `Input.get_axis` mengembalikan -1, 0, atau 1 (atau nilai pecahan pada analog stick).
- `move_toward(a, b, step)` menggeser nilai `a` menuju `b` sebanyak maksimal `step`. Di sini dipakai untuk berhenti.
- `sprite.flip_h` membalik gambar secara horizontal.

## 8.4 Membuat lantai sementara

Supaya player punya pijakan, buat scene `Level1`:

1. Root `Node2D`, ganti nama `Level1`.
2. Tambahkan `StaticBody2D` bernama `Ground`.
3. Di bawahnya tambahkan `CollisionShape2D` dengan `RectangleShape2D` yang lebar (misalnya 1200 x 40).
4. Tambahkan `ColorRect` atau `Sprite2D` sebagai tampilan visual lantai (agar kelihatan). `ColorRect` adalah node `Control`, tetapi tetap bisa dipakai untuk prototyping cepat.
5. Instance scene `Player` ke `Level1`, taruh di atas lantai.
6. Simpan, jalankan dengan F6.

`StaticBody2D` adalah benda tetap yang tidak bergerak tetapi bisa ditabrak. Cocok untuk lantai, dinding, dan platform.

## 8.5 Versi top-down (8 arah)

Untuk game tampak atas (gaya petualangan klasik), tidak ada gravitasi:

```gdscript
extends CharacterBody2D

@export var speed: float = 150.0


func _physics_process(_delta: float) -> void:
    var direction: Vector2 = Input.get_vector("move_left", "move_right", "move_up", "move_down")
    velocity = direction * speed
    move_and_slide()
```

Untuk top-down, pastikan gravitasi 2D tidak berpengaruh (karena kita tidak memakainya di skrip ini, tidak ada masalah). Jika memakai `CharacterBody2D`, ubah `Motion Mode` ke **Floating** pada Inspector agar `is_on_floor()` tidak relevan dan gerakan terasa bebas.

## 8.6 Menyempurnakan game feel platformer

Dua teknik sederhana yang membuat lompatan terasa jauh lebih enak.

**Coyote time**: pemain masih boleh melompat sesaat setelah meninggalkan tepi platform. **Jump buffer**: tekanan tombol lompat sedikit sebelum mendarat tetap dihitung.

```gdscript
extends CharacterBody2D

@export var speed: float = 200.0
@export var jump_velocity: float = -380.0
@export var coyote_time: float = 0.1
@export var jump_buffer_time: float = 0.1

var _coyote_timer: float = 0.0
var _jump_buffer_timer: float = 0.0


func _physics_process(delta: float) -> void:
    # Gravitasi
    if not is_on_floor():
        velocity += get_gravity() * delta

    # Atur timer
    if is_on_floor():
        _coyote_timer = coyote_time
    else:
        _coyote_timer -= delta

    if Input.is_action_just_pressed("jump"):
        _jump_buffer_timer = jump_buffer_time
    else:
        _jump_buffer_timer -= delta

    # Lompat jika kedua kondisi terpenuhi
    if _jump_buffer_timer > 0.0 and _coyote_timer > 0.0:
        velocity.y = jump_velocity
        _jump_buffer_timer = 0.0
        _coyote_timer = 0.0

    # Lompatan variabel: lepas tombol lebih awal = lompat lebih pendek
    if Input.is_action_just_released("jump") and velocity.y < 0.0:
        velocity.y *= 0.5

    var direction: float = Input.get_axis("move_left", "move_right")
    if direction != 0.0:
        velocity.x = direction * speed
    else:
        velocity.x = move_toward(velocity.x, 0.0, speed)

    move_and_slide()
```

Kamu tidak perlu menghafal ini. Cukup pahami idenya: **kontrol yang memaafkan membuat game terasa adil dan nyaman**.

## 8.7 Kamera 2D

Pada `Camera2D`:

- `Position Smoothing > Enabled`: kamera mengikuti dengan halus.
- `Limit Left/Top/Right/Bottom`: batas area kamera agar tidak keluar dari level.
- `Zoom`: perbesar atau perkecil tampilan (misalnya `Vector2(2, 2)` untuk pixel art).

Saat `Camera2D` menjadi anak dari `Player`, kamera otomatis mengikuti. Pastikan properti `Enabled` aktif.

## 8.8 Aset gratis untuk belajar

Untuk latihan, kamu bisa memakai aset gratis. Contoh sumber: Kenney (kenney.nl, banyak aset berlisensi CC0), OpenGameArt, dan itch.io (filter aset gratis). **Selalu baca lisensinya**: sebagian meminta atribusi (mencantumkan nama pembuat), sebagian melarang penggunaan komersial. Simpan catatan sumber dan lisensi setiap aset yang kamu pakai di file `CREDITS.md`.

## Ringkasan Bab 8

- `CharacterBody2D` dikendalikan lewat `velocity` dan `move_and_slide()`.
- Platformer: tambah gravitasi, lompat dengan Y negatif.
- Top-down: `Input.get_vector` dan tanpa gravitasi.
- Coyote time dan jump buffer meningkatkan kualitas kontrol.

## Latihan Bab 8

1. Buat player platformer dan lantai, pastikan bisa berjalan dan melompat.
2. Tambahkan platform kedua yang lebih tinggi agar player harus melompat ke atasnya.
3. Ubah `speed` dan `jump_velocity` dari Inspector sampai terasa pas.
4. Buat versi top-down dalam scene terpisah.

---

# Bab 9 - Fisika dan Collision 2D

## 9.1 Empat jenis objek fisika utama

|Node|Fungsi|Contoh|
|---|---|---|
|`StaticBody2D`|Benda tetap, tidak bergerak|Tanah, dinding, platform|
|`CharacterBody2D`|Dikendalikan kode, mendeteksi tabrakan|Pemain, musuh|
|`RigidBody2D`|Digerakkan mesin fisika (gaya, tumbukan, gravitasi)|Peti yang bisa didorong, bola|
|`Area2D`|Mendeteksi tumpang tindih, tidak menahan benda|Koin, zona bahaya, pemicu dialog|

Semua node tersebut **membutuhkan** `CollisionShape2D` (atau `CollisionPolygon2D`) sebagai anak untuk mendefinisikan bentuk tabrakannya. Tanpa bentuk, tidak ada tabrakan.

Tips memilih bentuk: pakai bentuk sederhana (kotak, kapsul, lingkaran) sebanyak mungkin. Lebih cepat dan lebih stabil daripada poligon rumit.

## 9.2 Collision Layer dan Collision Mask

Setiap objek fisika punya dua pengaturan:

- **Layer**: "Saya berada di layer nomor berapa."
- **Mask**: "Saya mendeteksi atau bertabrakan dengan layer nomor berapa."

Analogi: layer adalah "seragam" yang kamu pakai, mask adalah "siapa yang bisa kamu lihat".

Contoh konfigurasi (mengacu pada tabel di Bab 7.5):

|Objek|Layer|Mask|
|---|---|---|
|Tanah|world|(kosong)|
|Player|player|world, enemy, pickup|
|Musuh|enemy|world|
|Koin (Area2D)|pickup|player (koin yang mendeteksi pemain yang masuk)|

Aturan penting: tabrakan terdeteksi jika **mask A mencakup layer B**, atau sebaliknya untuk Area. Untuk `Area2D`, pengaturan mask menentukan siapa yang dideteksi oleh area tersebut. Jadi koin (Area2D) dengan mask `player` akan mendeteksi player yang masuk.

Kesalahan umum: objek saling menembus atau area tidak mendeteksi apa pun. Hampir selalu penyebabnya adalah layer/mask belum cocok.

Di kode:

```gdscript
set_collision_layer_value(2, true)    # aktifkan layer 2
set_collision_mask_value(1, true)     # aktifkan mask 1
```

## 9.3 Area2D dan signal body_entered

Contoh koin yang bisa dikumpulkan:

Struktur scene `Coin`:

```
Coin (Area2D)
 |-- Sprite2D
 |-- CollisionShape2D
 |-- AudioStreamPlayer
```

Atur `Collision > Mask` pada koin agar mencakup layer player.

```gdscript
extends Area2D

@onready var sfx: AudioStreamPlayer = $AudioStreamPlayer


func _ready() -> void:
    body_entered.connect(_on_body_entered)


func _on_body_entered(body: Node2D) -> void:
    if not body.is_in_group("player"):
        return

    GameState.add_coins(1)          # Autoload, dibahas di Bab 18

    # Matikan deteksi dan sembunyikan, tetapi biarkan suara selesai
    set_deferred("monitoring", false)
    $Sprite2D.hide()
    sfx.play()
    await sfx.finished
    queue_free()
```

Penjelasan:

- `body_entered` adalah signal yang dipancarkan saat sebuah body masuk area.
- `body.is_in_group("player")` memastikan hanya player yang diproses.
- `set_deferred("monitoring", false)` mengubah properti dengan aman di akhir frame, karena mengubah state fisika di tengah callback fisika bisa menimbulkan error.
- `await sfx.finished` menunggu suara selesai sebelum menghapus koin. Jika langsung `queue_free()`, suaranya terpotong.

Karena `GameState` belum dibuat, kamu bisa mengganti baris tersebut dengan `print("Koin diambil")` untuk sementara.

## 9.4 Hitbox dan Hurtbox

Pola umum untuk pertarungan:

- **Hurtbox**: area yang bisa terkena serangan (tubuh musuh atau pemain).
- **Hitbox**: area yang menyakiti (bilah pedang, peluru, tubuh musuh yang menyentuh).

Keduanya memakai `Area2D` dengan layer yang berbeda. Hitbox mendeteksi Hurtbox pada layer lawan, lalu memanggil fungsi `take_damage` pada pemilik Hurtbox.

Contoh hurtbox:

```gdscript
class_name Hurtbox
extends Area2D

signal hit(damage: int)


func receive_hit(damage: int) -> void:
    hit.emit(damage)
```

Contoh hitbox:

```gdscript
class_name Hitbox
extends Area2D

@export var damage: int = 1


func _ready() -> void:
    area_entered.connect(_on_area_entered)


func _on_area_entered(area: Area2D) -> void:
    if area is Hurtbox:
        area.receive_hit(damage)
```

Pemilik (misalnya Player atau Enemy) menghubungkan signal `hit` dari Hurtbox ke fungsi yang mengurangi nyawa. Dengan pola ini, hitbox tidak perlu tahu siapa yang dipukul. Ini contoh komposisi yang bersih.

## 9.5 RayCast2D

`RayCast2D` memancarkan sinar dari titik asal ke arah `Target Position` dan mendeteksi apa yang tertabrak. Dipakai untuk mengecek tepi jurang, jarak pandang musuh, atau apakah ada dinding di depan.

```gdscript
@onready var ray: RayCast2D = $RayCast2D

func _physics_process(_delta: float) -> void:
    if ray.is_colliding():
        var target: Object = ray.get_collider()
        print("Mengenai: ", target)
```

Atur `Enabled` aktif, `Target Position` (misalnya `Vector2(30, 0)`), dan `Collision Mask` yang sesuai.

## 9.6 RigidBody2D singkat

Gunakan `RigidBody2D` jika ingin objek patuh pada simulasi fisika penuh, misalnya peti yang bisa didorong. Jangan memindahkannya dengan `position = ...` langsung. Gunakan `apply_impulse()` atau `apply_force()`:

```gdscript
extends RigidBody2D

func _ready() -> void:
    apply_impulse(Vector2(200, -300))   # dorong sekali
```

Untuk karakter pemain, tetap pakai `CharacterBody2D` karena kontrolnya lebih bisa diprediksi.

## 9.7 Melihat bentuk collision saat bermain

Di menu `Debug`, aktifkan **Visible Collision Shapes**. Saat game berjalan, semua bentuk tabrakan akan digambar. Ini sangat membantu untuk mencari masalah collision.

## Ringkasan Bab 9

- Pilih node fisika sesuai tujuan: Static, Character, Rigid, Area.
- Collision Layer (saya di mana) dan Mask (saya melihat siapa) harus cocok.
- `Area2D` + `body_entered` cocok untuk pickup dan pemicu.
- Hitbox dan Hurtbox memisahkan penyerang dan korban secara bersih.
- Gunakan Visible Collision Shapes untuk debugging.

## Latihan Bab 9

1. Buat scene `Coin` dan taruh beberapa di `Level1`. Cetak pesan saat player menyentuhnya.
2. Buat zona bahaya (`Area2D`) yang mengembalikan player ke titik awal jika disentuh.
3. Aktifkan Visible Collision Shapes dan amati.

---

# Bab 10 - Membangun Level dengan TileMapLayer

## 10.1 Apa itu tilemap

Banyak game 2D membangun level dari kotak-kotak gambar kecil berukuran sama (tile) yang disusun seperti ubin. Keuntungannya: cepat dibuat, hemat memori, dan mudah diubah.

Di Godot 4 versi terbaru, node yang dipakai adalah **`TileMapLayer`**. (Node lama `TileMap` sudah ditandai usang sejak Godot 4.3. Jika tutorial lama memakai `TileMap`, konsepnya mirip, tetapi untuk proyek baru gunakan `TileMapLayer`.)

Setiap `TileMapLayer` adalah satu lapisan. Kamu bisa memakai beberapa layer, misalnya satu untuk tanah, satu untuk dekorasi, satu untuk latar.

## 10.2 Langkah membuat tilemap

1. Siapkan gambar **tileset** (satu gambar berisi banyak tile berukuran seragam, misalnya 16x16 atau 32x32 piksel).
2. Tambahkan node `TileMapLayer` ke scene level.
3. Di Inspector, pada `Tile Set`, pilih `New TileSet`, lalu klik untuk membuka panel **TileSet** di bagian bawah.
4. Ubah `Tile Size` sesuai ukuran tilemu.
5. Seret gambar tileset ke panel TileSet. Godot menawarkan membuat tile secara otomatis (pilih **Yes**).
6. Pindah ke tab **TileMap** (di panel bawah) lalu pilih tile dan lukis di viewport. Klik kiri melukis, klik kanan menghapus.

## 10.3 Menambahkan collision ke tile

Agar tile bisa menjadi tanah yang dipijak:

1. Pilih resource `TileSet` di Inspector, buka bagian **Physics Layers**, klik **Add Element**. Atur `Collision Layer` ke layer `world`.
2. Di panel TileSet, pilih mode **Paint** atau **Select** dan buka properti **Physics > Physics Layer 0**.
3. Pada tile yang ingin solid, gambar bentuk tabrakan (biasanya kotak penuh) di editor polygon yang muncul.

Setelah itu, player dengan `CharacterBody2D` akan berdiri di atas tile tersebut.

## 10.4 Terrain (autotile)

Fitur **Terrains** otomatis memilih tile yang tepat (sudut, tepi, tengah) saat kamu melukis, sehingga garis tanah menyatu rapi. Prosesnya: buat Terrain Set di TileSet, tetapkan tile ke terrain, lalu pakai mode Terrain saat melukis. Fitur ini opsional tetapi menghemat waktu bagi level yang besar.

## 10.5 Tips membangun level

- Gunakan beberapa layer: `Background`, `Ground`, `Foreground`.
- Atur **Z Index** atau urutan node untuk menentukan siapa yang tampak di depan.
- Jaga ukuran tile konsisten dengan ukuran karaktermu. Misalnya karakter setinggi 2 tile.
- Buat level dalam beberapa scene terpisah (`level_01.tscn`, `level_02.tscn`) agar mudah dikelola.
- Rancang level untuk **mengajarkan** mekanik: mulai dari ruang aman, perkenalkan mekanik baru, beri tantangan, lalu gabungkan dengan mekanik lain.

## Ringkasan Bab 10

- Tilemap menyusun level dari tile berukuran seragam.
- Gunakan `TileMapLayer` untuk proyek baru.
- Tambahkan Physics Layer di TileSet agar tile bisa ditabrak.
- Terrain membantu melukis tepi dan sudut otomatis.

## Latihan Bab 10

1. Impor tileset gratis (misalnya dari Kenney) dan buat level pendek dengan satu `TileMapLayer`.
2. Tambahkan collision pada tile tanah, lalu uji player berjalan di atasnya.
3. Tambahkan layer kedua untuk dekorasi tanpa collision.

---

# Bab 11 - Animasi 2D

## 11.1 Tiga cara animasi utama

|Alat|Cocok untuk|
|---|---|
|`AnimatedSprite2D`|Animasi frame-by-frame sederhana (idle, jalan, lompat) dari spritesheet|
|`AnimationPlayer`|Menganimasikan properti apa pun (posisi, warna, visibilitas, bahkan memanggil fungsi) dengan timeline|
|`Tween` (kode)|Animasi singkat yang dibuat lewat skrip (muncul, memudar, memantul)|

Pada level lebih lanjut ada juga `AnimationTree` untuk mencampur dan mengatur transisi animasi secara kompleks. Untuk pemula, tiga alat di atas sudah mencukupi.

## 11.2 AnimatedSprite2D

Langkah:

1. Tambahkan `AnimatedSprite2D` ke scene Player (ganti `Sprite2D` jika perlu).
2. Di Inspector, pada `Sprite Frames`, pilih `New SpriteFrames`, lalu klik untuk membuka panel SpriteFrames.
3. Buat animasi baru (misalnya `idle`, `run`, `jump`).
4. Tambahkan frame dari file gambar atau dari spritesheet (tombol **Add frames from Sprite Sheet**, tentukan jumlah baris dan kolom).
5. Atur **FPS** animasi dan aktifkan **Loop** jika perlu.

Memainkan lewat kode:

```gdscript
@onready var anim: AnimatedSprite2D = $AnimatedSprite2D


func _update_animation(direction: float) -> void:
    if not is_on_floor():
        anim.play("jump")
    elif direction != 0.0:
        anim.play("run")
        anim.flip_h = direction < 0.0
    else:
        anim.play("idle")
```

Panggil `_update_animation(direction)` di `_physics_process`. Memanggil `play()` dengan nama animasi yang sama yang sedang berjalan tidak akan mengulang dari awal, jadi aman dipanggil tiap frame.

## 11.3 AnimationPlayer

`AnimationPlayer` menganimasikan **properti apa pun** pada node mana pun.

Langkah membuat animasi:

1. Tambahkan `AnimationPlayer` ke scene.
2. Di panel Animation (bawah), klik **Animation > New**, beri nama (misalnya `hurt`).
3. Atur panjang animasi (Length), misalnya 0,4 detik.
4. Pilih node yang ingin dianimasikan, ubah properti di Inspector, lalu klik ikon kunci (key) di sebelah properti untuk membuat **keyframe** pada waktu tertentu di timeline.
5. Tambahkan keyframe lain di waktu berbeda dengan nilai berbeda. Godot menginterpolasi di antaranya.

Contoh animasi `hurt`: keyframe warna `Modulate` sprite dari putih ke merah lalu kembali ke putih dalam 0,3 detik.

Memainkan dari kode:

```gdscript
@onready var anim_player: AnimationPlayer = $AnimationPlayer

func take_damage() -> void:
    anim_player.play("hurt")
```

Fitur berguna:

- **Call Method Track**: memanggil fungsi di titik tertentu animasi (misalnya mengaktifkan hitbox tepat saat ayunan pedang).
- Signal `animation_finished(anim_name)` untuk bereaksi saat animasi selesai.

## 11.4 Tween lewat kode

Tween cocok untuk animasi cepat tanpa membuka editor:

```gdscript
func pop_in() -> void:
    scale = Vector2.ZERO
    var tween: Tween = create_tween()
    tween.tween_property(self, "scale", Vector2.ONE, 0.25).set_trans(Tween.TRANS_BACK).set_ease(Tween.EASE_OUT)


func fade_out_and_free() -> void:
    var tween: Tween = create_tween()
    tween.tween_property(self, "modulate:a", 0.0, 0.5)    # ubah alpha ke 0
    tween.tween_callback(queue_free)                       # lalu hapus node
```

Penjelasan:

- `tween_property(objek, "properti", nilai_akhir, durasi)` menganimasikan sebuah properti.
- Rantai `.set_trans(...)` dan `.set_ease(...)` mengatur kurva gerak.
- `tween_callback` memanggil fungsi setelah tween sebelumnya selesai.
- `modulate:a` berarti komponen alpha (transparansi) dari `modulate`.

## 11.5 Animasi 3D

Konsepnya sama: `AnimationPlayer` juga dipakai di 3D. Model yang diimpor dari Blender atau format glTF biasanya sudah membawa animasinya, dan Godot membuat `AnimationPlayer` otomatis untuknya (lihat Bab 15).

## Ringkasan Bab 11

- `AnimatedSprite2D` untuk animasi frame-by-frame, `AnimationPlayer` untuk animasi properti, `Tween` untuk animasi cepat dari kode.
- Pilih animasi berdasarkan state karakter (idle, run, jump).
- `Call Method Track` menyinkronkan gameplay dengan animasi.

## Latihan Bab 11

1. Buat animasi `idle` dan `run` untuk player (boleh memakai dua gambar sederhana yang kamu gambar sendiri).
2. Buat animasi `hurt` dengan `AnimationPlayer` yang mengubah warna menjadi merah sebentar.
3. Buat koin yang melayang naik turun terus-menerus dengan Tween.

---

# Bab 12 - Signal, Group, dan Komunikasi Antar Node

## 12.1 Masalah yang dipecahkan

Game dibuat dari banyak objek yang perlu saling berkomunikasi: pemain terkena damage, UI harus memperbarui bar nyawa. Jika kode pemain langsung memanipulasi UI, kedua bagian jadi saling bergantung dan sulit diubah. Signal memecahkan masalah ini.

## 12.2 Apa itu signal

Signal adalah "pengumuman" dari sebuah node bahwa sesuatu terjadi. Node lain yang berminat bisa **berlangganan** (connect) untuk bereaksi. Pengirim tidak perlu tahu siapa penerimanya.

Analogi: stasiun radio menyiarkan lagu. Ia tidak tahu siapa yang mendengarkan, siapa pun boleh menyetel frekuensinya.

## 12.3 Signal bawaan

Banyak node punya signal bawaan, misalnya:

- `Button`: `pressed`
- `Area2D`: `body_entered`, `body_exited`, `area_entered`
- `Timer`: `timeout`
- `AnimationPlayer`: `animation_finished`
- `AudioStreamPlayer`: `finished`

## 12.4 Menghubungkan signal

**Lewat editor**: pilih node, buka tab **Node** (di sebelah Inspector), klik dua kali signal yang diinginkan, pilih node penerima, lalu Godot membuat fungsi penerima otomatis.

**Lewat kode** (disarankan karena eksplisit dan mudah dilacak):

```gdscript
func _ready() -> void:
    $StartButton.pressed.connect(_on_start_button_pressed)
    $SpawnTimer.timeout.connect(_on_spawn_timer_timeout)


func _on_start_button_pressed() -> void:
    get_tree().change_scene_to_file("res://scenes/levels/level_01.tscn")


func _on_spawn_timer_timeout() -> void:
    print("Spawn musuh baru")
```

Konvensi nama fungsi penerima: `_on_NamaNode_nama_signal`.

## 12.5 Membuat signal sendiri

```gdscript
# health_component.gd
class_name HealthComponent
extends Node

signal health_changed(current: int, maximum: int)
signal died

@export var max_health: int = 3

var current_health: int


func _ready() -> void:
    current_health = max_health


func take_damage(amount: int) -> void:
    if current_health <= 0:
        return
    current_health = maxi(current_health - amount, 0)
    health_changed.emit(current_health, max_health)
    if current_health == 0:
        died.emit()
```

Penerima:

```gdscript
# player.gd (bagian)
@onready var health: HealthComponent = $HealthComponent

func _ready() -> void:
    health.died.connect(_on_died)

func _on_died() -> void:
    print("Player mati")
```

```gdscript
# hud.gd (bagian)
func bind_to(health: HealthComponent) -> void:
    health.health_changed.connect(_on_health_changed)

func _on_health_changed(current: int, maximum: int) -> void:
    $HealthBar.max_value = maximum
    $HealthBar.value = current
```

Perhatikan: `HealthComponent` tidak tahu apa pun tentang Player atau HUD. Ia hanya memancarkan signal. Inilah keindahan desain berbasis signal.

## 12.6 Signal dengan parameter dan Callable

Kamu bisa menyertakan data bersama signal (seperti `current` dan `maximum` di atas). Untuk meneruskan argumen tambahan saat connect, gunakan `bind`:

```gdscript
for button in $Menu.get_children():
    button.pressed.connect(_on_menu_button_pressed.bind(button.name))

func _on_menu_button_pressed(button_name: String) -> void:
    print("Ditekan: ", button_name)
```

## 12.7 Group

**Group** adalah label yang bisa ditempelkan ke node (satu node bisa punya banyak group). Berguna untuk mengelompokkan objek tanpa menyimpan referensi satu per satu.

```gdscript
# Menambahkan ke group lewat kode (alternatif editor)
add_to_group("enemies")

# Mengecek
if body.is_in_group("player"):
    ...

# Mengambil semua node dalam group
for enemy in get_tree().get_nodes_in_group("enemies"):
    enemy.queue_free()

# Memanggil fungsi pada semua anggota group
get_tree().call_group("enemies", "become_alert")
```

## 12.8 Prinsip "call down, signal up"

Aturan praktis agar kode rapi:

- **Call down**: induk boleh memanggil fungsi langsung pada anak-anaknya karena induk mengenal anaknya.
- **Signal up**: anak memberi tahu induk (atau pihak lain) lewat signal, karena anak sebaiknya tidak mengasumsikan siapa induknya.

Hindari `get_parent().get_parent().do_something()`. Itu rapuh. Jika struktur scene berubah, kode rusak.

## Ringkasan Bab 12

- Signal memungkinkan komunikasi tanpa ketergantungan erat.
- Connect lewat editor atau kode (`signal.connect(fungsi)`).
- Buat signal sendiri dengan `signal nama(param)` dan pancarkan dengan `nama.emit(...)`.
- Group untuk mengelompokkan node.
- Call down, signal up.

## Latihan Bab 12

1. Buat `HealthComponent` dan hubungkan signal `health_changed` ke sebuah `Label` yang menampilkan angka nyawa.
2. Buat tombol yang saat ditekan mengurangi nyawa player 1.
3. Taruh beberapa musuh dalam group `enemies` dan buat tombol yang menghapus semuanya.

---

# Bab 13 - User Interface (UI)

## 13.1 Node Control

Semua elemen UI adalah turunan `Control`. Node `Control` punya sistem **anchor** dan **container** yang membuat UI menyesuaikan berbagai ukuran layar.

Node UI yang paling sering dipakai:

|Node|Fungsi|
|---|---|
|`Label`|Teks sederhana|
|`RichTextLabel`|Teks dengan format (warna, tebal, efek) dan fitur mengetik bertahap|
|`Button`|Tombol|
|`TextureRect`|Menampilkan gambar di UI|
|`ProgressBar`, `TextureProgressBar`|Bar nyawa, stamina, loading|
|`Panel`, `PanelContainer`|Latar kotak|
|`HSlider`|Penggeser nilai (misalnya volume)|
|`CheckBox`, `OptionButton`|Pengaturan|
|`CanvasLayer`|Lapisan terpisah agar UI selalu di atas dunia game dan tidak ikut bergerak bersama kamera|

## 13.2 Container: kunci layout yang rapi

Container mengatur posisi dan ukuran anak-anaknya secara otomatis.

|Container|Perilaku|
|---|---|
|`VBoxContainer`|Menyusun anak ke bawah (vertikal)|
|`HBoxContainer`|Menyusun anak ke samping (horizontal)|
|`GridContainer`|Menyusun dalam kolom dan baris|
|`MarginContainer`|Memberi jarak (margin) di sekeliling anak|
|`CenterContainer`|Menaruh anak di tengah|
|`PanelContainer`|Seperti Panel yang sekaligus mengatur anak|

Untuk menu utama yang sederhana:

```
MainMenu (Control)           <- Layout: Full Rect
 |-- CenterContainer         <- Full Rect
      |-- VBoxContainer
           |-- TitleLabel
           |-- StartButton
           |-- ContinueButton
           |-- SettingsButton
           |-- QuitButton
```

Gunakan menu **Layout** di toolbar (saat node Control terpilih) untuk mengatur anchor, misalnya **Full Rect**.

## 13.3 HUD (Heads-Up Display)

HUD adalah tampilan yang menyertai gameplay: nyawa, skor, minimap.

Struktur:

```
HUD (CanvasLayer)
 |-- MarginContainer
      |-- HBoxContainer
           |-- HealthBar (ProgressBar)
           |-- CoinLabel (Label)
```

Mengapa `CanvasLayer`? Karena ia menggambar di atas dunia game dan tidak terpengaruh kamera. HUD tetap menempel di layar.

Skrip HUD:

```gdscript
extends CanvasLayer

@onready var coin_label: Label = %CoinLabel
@onready var health_bar: ProgressBar = %HealthBar


func _ready() -> void:
    GameState.coins_changed.connect(_on_coins_changed)
    _on_coins_changed(GameState.coins)


func _on_coins_changed(new_value: int) -> void:
    coin_label.text = "Koin: %d" % new_value
```

`"Koin: %d" % new_value` adalah format string: `%d` diganti bilangan bulat. Format lain: `%s` untuk teks, `%.2f` untuk desimal dua digit.

## 13.4 Menu pause

Saat game di-pause, kamu ingin UI pause tetap berfungsi:

1. Buat scene `PauseMenu` (root `CanvasLayer`).
2. Pada Inspector, buka **Node > Process > Mode**, ubah menjadi **When Paused** (atau **Always**).
3. Di skrip:

```gdscript
extends CanvasLayer


func _ready() -> void:
    hide()


func _unhandled_input(event: InputEvent) -> void:
    if event.is_action_pressed("pause"):
        toggle_pause()
        get_viewport().set_input_as_handled()


func toggle_pause() -> void:
    var new_state: bool = not get_tree().paused
    get_tree().paused = new_state
    visible = new_state
```

Mode proses node:

- **Inherit**: ikut induk (bawaan).
- **Pausable**: berhenti saat game di-pause.
- **When Paused**: hanya berjalan saat game di-pause.
- **Always**: selalu berjalan.
- **Disabled**: tidak pernah berjalan.

Pada contoh di atas, node yang sama harus bisa **membuka** pause (saat game berjalan normal) sekaligus **menutupnya** (saat game sedang dijeda). Karena itu pilih mode **Always**. Mode `When Paused` hanya cocok jika pembukaan pause ditangani node lain (misalnya skrip level), sedangkan menu hanya mengurus tombol di dalamnya.

## 13.5 Theme dan font

Agar UI konsisten:

- Buat resource **Theme** (`New Theme`) dan atur gaya Button, Label, Panel di satu tempat.
- Tetapkan Theme pada node root UI, anak-anaknya otomatis memakainya.
- Impor font (`.ttf` atau `.otf`) dengan lisensi yang sesuai dan atur di Theme.
- Pastikan teks cukup besar dan kontras agar nyaman dibaca. Teks yang panjang di game cerita adalah fitur utama, jadi perhatikan keterbacaan.

## 13.6 Fokus dan kontrol keyboard atau gamepad

Agar menu bisa dioperasikan tanpa mouse, panggil `grab_focus()` pada tombol pertama:

```gdscript
func _ready() -> void:
    $CenterContainer/VBoxContainer/StartButton.grab_focus()
```

Aksi `ui_up`, `ui_down`, dan `ui_accept` secara bawaan akan memindahkan fokus dan menekan tombol.

## Ringkasan Bab 13

- UI dibangun dari node `Control`, tata letak diatur dengan Container.
- Pakai `CanvasLayer` untuk HUD.
- Gunakan Process Mode agar menu pause tetap berfungsi saat game dijeda.
- Gunakan Theme untuk konsistensi dan `grab_focus()` untuk navigasi tanpa mouse.

## Latihan Bab 13

1. Buat menu utama dengan tombol Start dan Quit. Start berpindah ke Level1, Quit memanggil `get_tree().quit()`.
2. Buat HUD dengan label koin.
3. Buat menu pause yang bisa dibuka dan ditutup dengan Escape.

---

# Bab 14 - Audio: Musik dan Efek Suara

## 14.1 Ingat: tanpa voice actor

Di buku ini kita tidak memakai pengisi suara. Audio terdiri dari:

- **Musik** (BGM, background music): membangun suasana.
- **SFX** (sound effect): umpan balik aksi (lompat, ambil koin, terkena damage, klik tombol).
- **Ambient**: suara latar lingkungan (angin, gua, hujan).

Dialog disampaikan lewat teks. Trik umum game indie untuk memberi kesan "bicara" tanpa voice actor adalah memutar bunyi singkat ("blip") yang berulang saat teks muncul huruf demi huruf.

## 14.2 Node audio

|Node|Fungsi|
|---|---|
|`AudioStreamPlayer`|Memutar suara non-posisional (musik, UI, SFX umum)|
|`AudioStreamPlayer2D`|Suara berposisi di dunia 2D (volume berubah menurut jarak)|
|`AudioStreamPlayer3D`|Suara berposisi di dunia 3D|

Format yang disarankan: **OGG Vorbis** untuk musik (ukuran kecil, bisa loop) dan **WAV** untuk SFX pendek (tanpa kompresi, tanpa jeda dekode). MP3 juga didukung.

## 14.3 Memutar suara

Cara paling sederhana: tambahkan `AudioStreamPlayer`, isi properti `Stream` dengan file audio, aktifkan `Autoplay` untuk musik latar.

Lewat kode:

```gdscript
@onready var jump_sfx: AudioStreamPlayer = $JumpSFX

func jump() -> void:
    jump_sfx.play()
```

Mengulang musik (loop): pada file OGG atau WAV, buka tab **Import**, aktifkan **Loop**, lalu klik **Reimport**.

## 14.4 Audio Bus: mengatur volume per kategori

Panel **Audio** (bawah) menampilkan **bus**. Bus bawaan adalah `Master`. Buat bus tambahan `Music` dan `SFX`, lalu pada tiap `AudioStreamPlayer` ubah properti `Bus` agar masuk ke bus yang sesuai.

Dengan ini kamu bisa memberi pemain slider volume terpisah untuk musik dan efek:

```gdscript
func set_bus_volume(bus_name: String, linear_value: float) -> void:
    var index: int = AudioServer.get_bus_index(bus_name)
    AudioServer.set_bus_volume_db(index, linear_to_db(linear_value))
    AudioServer.set_bus_mute(index, linear_value <= 0.001)
```

Penjelasan: volume di Godot dalam desibel (dB), tetapi slider biasanya nilai linear 0 sampai 1. `linear_to_db()` mengonversinya. Menyimpan nilai linear di pengaturan lebih mudah dipahami pemain.

## 14.5 Variasi agar tidak monoton

Suara yang sama diputar berulang terasa membosankan. Beri variasi kecil pada pitch:

```gdscript
func play_varied(player: AudioStreamPlayer) -> void:
    player.pitch_scale = randf_range(0.9, 1.1)
    player.play()
```

Untuk SFX yang bisa tumpang tindih (misalnya banyak koin diambil berurutan), satu `AudioStreamPlayer` akan memotong suara sebelumnya. Properti `Max Polyphony` bisa dinaikkan, atau buat pemutar baru per suara.

## 14.6 Musik antar scene

Jika musik ditaruh di scene level, musik akan putus saat scene berganti. Solusi: pindahkan pemutar musik ke **Autoload** (Bab 18) sehingga hidup di antara scene.

## 14.7 Sumber audio

Aset audio gratis bisa ditemukan di situs seperti OpenGameArt, itch.io, Kenney (aset audio), atau Freesound. Seperti aset visual, **periksa lisensi** dan catat atribusi. Kamu juga bisa membuat SFX sendiri dengan alat seperti sfxr atau jsfxr (menghasilkan efek retro secara acak).

## Ringkasan Bab 14

- Audio game ini: musik, SFX, dan ambient. Dialog lewat teks.
- Pakai OGG untuk musik, WAV untuk SFX.
- Atur volume lewat Audio Bus, simpan nilai linear di pengaturan.
- Variasi pitch membuat SFX tidak monoton.

## Latihan Bab 14

1. Tambahkan SFX lompat dan SFX koin.
2. Buat bus `Music` dan `SFX`, lalu tambahkan dua slider volume di menu pengaturan.
3. Tambahkan musik latar yang berulang pada level.

---

# Bab 15 - Pengenalan Game 3D

Jika kamu sudah memahami 2D, 3D tidak jauh berbeda secara konsep. Node, scene, signal, dan GDScript bekerja sama persis. Yang berubah adalah dimensi: ada sumbu Z, kamera perspektif, pencahayaan, dan model 3D.

## 15.1 Node 3D dasar

|Node|Fungsi|
|---|---|
|`Node3D`|Node dasar 3D (punya posisi, rotasi, skala). Dipakai sebagai root atau pengelompok|
|`MeshInstance3D`|Menampilkan bentuk 3D (mesh)|
|`Camera3D`|Kamera, tempat pemain "melihat"|
|`DirectionalLight3D`|Cahaya paralel seperti matahari|
|`OmniLight3D`|Cahaya titik ke segala arah seperti bohlam|
|`SpotLight3D`|Cahaya kerucut seperti senter|
|`WorldEnvironment`|Pengaturan lingkungan: langit, cahaya sekitar, efek layar|
|`StaticBody3D`, `CharacterBody3D`, `RigidBody3D`, `Area3D`|Versi 3D dari node fisika|
|`CollisionShape3D`|Bentuk tabrakan 3D|

## 15.2 Membuat scene 3D pertama

1. Buat scene baru dengan root `Node3D`, ganti nama `World`.
2. Tambahkan `MeshInstance3D` sebagai lantai: pada `Mesh`, pilih `New PlaneMesh` (atau `BoxMesh`) lalu perbesar ukurannya.
3. Tambahkan `DirectionalLight3D`, putar agar menyinari lantai miring (rotasi X sekitar -45 derajat). Aktifkan `Shadow > Enabled`.
4. Tambahkan `WorldEnvironment`, di Inspector buat `New Environment`, lalu atur `Background > Mode` ke **Sky**, buat `New Sky` dengan `ProceduralSkyMaterial`. Atur `Ambient Light > Source` ke Sky.
5. Tambahkan `Camera3D`, geser dan putar sampai melihat lantai. Tips: pilih kamera lalu aktifkan **Preview** di viewport (menu `Perspective` atau tombol preview) untuk melihat dari sudut pandangnya.
6. Jalankan dengan F6.

## 15.3 Material

Warna dan tampilan permukaan diatur oleh **Material**. Yang paling umum adalah `StandardMaterial3D`:

- **Albedo > Color**: warna dasar. **Albedo > Texture**: gambar tekstur.
- **Metallic**: seberapa logam permukaannya (0 sampai 1).
- **Roughness**: kekasaran. 0 mengilap seperti cermin, 1 buram seperti kapur.
- **Emission**: membuat permukaan memancarkan cahaya (lampu neon, kristal bercahaya).
- **Normal Map**: tekstur untuk menambah detail relief tanpa menambah poligon.

Pada `MeshInstance3D`, buka `Surface Material Override` atau `Material` dan buat `New StandardMaterial3D`.

## 15.4 Memakai CSG untuk prototyping

Node `CSGBox3D`, `CSGSphere3D`, `CSGCylinder3D` memungkinkan membuat bentuk dan "memotongnya" (operasi gabung, kurang, irisan). Sangat berguna untuk menyusun level kasar (blockout) dengan cepat. Opsi **Use Collision** otomatis membuat tabrakan. Untuk level final, mesh yang sudah diimpor atau dibuat di Blender lebih efisien.

## 15.5 Mengimpor model 3D

Format yang direkomendasikan: **glTF 2.0** (`.glb` atau `.gltf`). Format ini didukung baik oleh Godot dan Blender.

Langkah:

1. Ekspor model dari Blender sebagai `glTF 2.0`.
2. Salin file `.glb` ke folder proyek (misalnya `res://assets/models/`).
3. Godot mengimpornya otomatis. Klik dua kali file untuk membuka sebagai **scene turunan** (inherited scene), atau tarik ke scene lain.
4. Pengaturan impor ada di tab **Import** (di sebelah Scene dock). Ubah lalu klik **Reimport**.

Hal yang perlu diperhatikan:

- **Skala**: satuan Godot 3D umumnya meter. Pastikan model punya skala yang masuk akal (karakter manusia sekitar 1,7 unit).
- **Animasi**: jika model membawa animasi, akan ada node `AnimationPlayer` yang bisa dipakai.
- **Poligon**: untuk game indie, model low-poly (sedikit poligon) lebih mudah dibuat dan lebih ringan.

## 15.6 Kamera 3D dan sudut pandang

Beberapa gaya kamera umum:

- **First person**: kamera berada di posisi mata karakter.
- **Third person**: kamera di belakang dan di atas karakter, biasanya memakai `SpringArm3D` agar kamera tidak menembus dinding.
- **Isometrik atau top-down 3D**: kamera di sudut tetap, sering memakai proyeksi Orthogonal.

Pengaturan `Camera3D`: `FOV` (field of view, bawaan 75 derajat), `Projection` (Perspective atau Orthogonal), `Near` dan `Far` (jarak dekat dan jauh yang dirender).

## 15.7 Pencahayaan dan performa

- Bayangan dan cahaya dinamis adalah bagian yang paling berat. Pakai sedikit cahaya dinamis.
- Cahaya yang tidak berubah bisa di-bake (LightmapGI) untuk performa lebih baik, tetapi ini topik lanjutan.
- Renderer **Compatibility** memiliki fitur 3D lebih terbatas dibanding Forward+. Jika targetmu perangkat lama, uji sejak awal.

## 15.8 Perbedaan 2D vs 3D (ringkasan)

|Aspek|2D|3D|
|---|---|---|
|Gambar|Sprite, tilemap|Mesh, material, cahaya|
|Karakter|`CharacterBody2D`|`CharacterBody3D`|
|Posisi|`Vector2`|`Vector3`|
|Kamera|`Camera2D`|`Camera3D`|
|Beban membuat aset|Lebih ringan untuk satu orang|Perlu pemodelan, tekstur, rigging|
|Sumbu atas|-Y|+Y|

Saran untuk developer solo pemula: bangun fondasi dengan 2D, lalu masuk ke 3D setelah menyelesaikan beberapa game kecil. Banyak game 3D indie yang sukses memakai gaya low-poly sederhana.

## Ringkasan Bab 15

- Konsep node dan scene sama di 3D. Tambahan: sumbu Z, cahaya, material, mesh.
- Siapkan minimal `DirectionalLight3D`, `WorldEnvironment`, dan `Camera3D`.
- Impor model dalam format glTF (`.glb`).
- Gunakan CSG untuk blockout level cepat.

## Latihan Bab 15

1. Buat scene 3D dengan lantai, tiga kotak berwarna berbeda, matahari, dan langit.
2. Ubah roughness dan metallic salah satu kotak, perhatikan perbedaannya.
3. Impor satu model `.glb` gratis dan letakkan di scene.

---

# Bab 16 - Karakter, Interaksi, dan Fisika 3D

## 16.1 Menyiapkan scene Player 3D (first person)

```
Player (CharacterBody3D)
 |-- CollisionShape3D       (CapsuleShape3D, tinggi sekitar 1.8)
 |-- Head (Node3D)          (posisi Y sekitar 1.6, setinggi mata)
      |-- Camera3D
      |-- InteractRay (RayCast3D)
```

Atur `RayCast3D`: `Target Position` ke `Vector3(0, 0, -2.5)` (ke depan sejauh 2,5 meter) dan aktifkan `Enabled`.

## 16.2 Skrip pergerakan first person

```gdscript
extends CharacterBody3D

@export var speed: float = 5.0
@export var jump_velocity: float = 4.5
@export var mouse_sensitivity: float = 0.003

@onready var head: Node3D = $Head
@onready var interact_ray: RayCast3D = $Head/InteractRay


func _ready() -> void:
    Input.mouse_mode = Input.MOUSE_MODE_CAPTURED


func _unhandled_input(event: InputEvent) -> void:
    # Melihat dengan mouse
    if event is InputEventMouseMotion and Input.mouse_mode == Input.MOUSE_MODE_CAPTURED:
        rotate_y(-event.relative.x * mouse_sensitivity)             # putar badan (kiri-kanan)
        head.rotate_x(-event.relative.y * mouse_sensitivity)        # putar kepala (atas-bawah)
        head.rotation.x = clampf(head.rotation.x, deg_to_rad(-80.0), deg_to_rad(80.0))

    # Lepas kursor mouse dengan Escape
    if event.is_action_pressed("ui_cancel"):
        Input.mouse_mode = Input.MOUSE_MODE_VISIBLE

    # Interaksi
    if event.is_action_pressed("interact"):
        _try_interact()


func _physics_process(delta: float) -> void:
    if not is_on_floor():
        velocity += get_gravity() * delta

    if Input.is_action_just_pressed("jump") and is_on_floor():
        velocity.y = jump_velocity

    var input_dir: Vector2 = Input.get_vector("move_left", "move_right", "move_up", "move_down")
    var direction: Vector3 = (transform.basis * Vector3(input_dir.x, 0.0, input_dir.y)).normalized()

    if direction != Vector3.ZERO:
        velocity.x = direction.x * speed
        velocity.z = direction.z * speed
    else:
        velocity.x = move_toward(velocity.x, 0.0, speed)
        velocity.z = move_toward(velocity.z, 0.0, speed)

    move_and_slide()


func _try_interact() -> void:
    if interact_ray.is_colliding():
        var target: Object = interact_ray.get_collider()
        if target.has_method("interact"):
            target.interact(self)
```

Penjelasan konsep penting:

- `Input.MOUSE_MODE_CAPTURED`: menyembunyikan dan mengunci kursor di tengah layar, standar untuk first person.
- `event.relative`: seberapa jauh mouse bergeser pada event tersebut.
- Badan diputar pada sumbu Y (menoleh kiri-kanan), kepala pada sumbu X (menengok atas-bawah). Memisahkan keduanya mencegah kamera "berguling" (roll).
- `clampf` membatasi nilai agar pemain tidak bisa menengok melewati vertikal.
- `transform.basis * Vector3(...)` mengubah arah input dari "relatif ke pemain" menjadi arah di dunia, sehingga W selalu maju menurut arah hadap.
- Di 3D, "maju" adalah sumbu -Z. Karena `get_vector` mengembalikan `y = -1` saat menekan aksi "move_up" (atas), nilainya masuk ke komponen Z dengan benar. Pastikan aksi `move_up` dipetakan ke W.
- `target.has_method("interact")` adalah **duck typing**: kita tidak peduli tipe objek, selama ia punya fungsi `interact`.

## 16.3 Objek yang bisa diinteraksi

```gdscript
# door_3d.gd, dipasang pada StaticBody3D
extends StaticBody3D

@export var is_locked: bool = false
var is_open: bool = false


func interact(_player: Node) -> void:
    if is_locked and not GameState.has_flag("has_key"):
        print("Pintu terkunci.")
        return
    is_open = not is_open
    var target_angle: float = deg_to_rad(90.0) if is_open else 0.0
    var tween: Tween = create_tween()
    tween.tween_property(self, "rotation:y", target_angle, 0.4)
```

Gunakan `RayCast3D` pada kamera untuk menyorot objek di depan pemain, lalu tampilkan prompt UI seperti "Tekan E untuk membuka" dengan memeriksa `interact_ray.get_collider()` tiap frame.

## 16.4 Area3D untuk pemicu

```gdscript
extends Area3D

func _ready() -> void:
    body_entered.connect(_on_body_entered)


func _on_body_entered(body: Node3D) -> void:
    if body.is_in_group("player"):
        print("Pemain memasuki zona")
```

Semua pola dari 2D (layer, mask, signal) bekerja sama di 3D.

## 16.5 Bentuk tabrakan 3D

|Bentuk|Penggunaan|
|---|---|
|`CapsuleShape3D`|Karakter|
|`BoxShape3D`|Kotak, ruangan, peti|
|`SphereShape3D`|Objek bulat, pemicu radius|
|`ConvexPolygonShape3D`|Bentuk cembung dari mesh|
|`ConcavePolygonShape3D` (trimesh)|Level statis yang rumit (hanya untuk benda statis)|

Jalan pintas: pilih `MeshInstance3D`, lalu klik menu **Mesh** di toolbar viewport > **Create Collision Shape...** untuk membuat tabrakan otomatis dari mesh.

## 16.6 Mesin fisika 3D

Godot memiliki lebih dari satu implementasi fisika 3D. Selain mesin bawaan Godot, tersedia **Jolt Physics** yang umumnya lebih stabil untuk banyak skenario 3D. Pada versi-versi Godot 4 yang lebih baru, Jolt sudah menjadi opsi resmi dan, tergantung versi, bisa menjadi pilihan bawaan untuk proyek baru. Untuk mengecek atau mengubahnya, lihat `Project Settings > Physics > 3D > Physics Engine`. Sebagai pemula, kamu cukup memakai pengaturan bawaan.

## 16.7 RigidBody3D singkat

Untuk objek yang bereaksi terhadap fisika (kotak yang bisa didorong, bola menggelinding):

- Tambahkan `RigidBody3D` dengan `CollisionShape3D` dan `MeshInstance3D`.
- Atur `Mass` dan `Physics Material Override` (friction dan bounce).
- Dorong lewat kode dengan `apply_central_impulse(Vector3(...))`.

Jangan mengubah `position` RigidBody secara langsung dalam keadaan normal karena akan mengganggu simulasi.

## 16.8 Third person (gambaran umum)

Susunan umum untuk kamera orang ketiga:

```
Player (CharacterBody3D)
 |-- CollisionShape3D
 |-- Model (Node3D)         <- model karakter, diputar menghadap arah gerak
 |-- CameraPivot (Node3D)   <- diputar dengan mouse atau stick kanan
      |-- SpringArm3D       <- menarik kamera mendekat jika ada dinding
           |-- Camera3D
```

Arah gerak dihitung relatif terhadap kamera, lalu `Model` diputar mulus menuju arah gerak (misalnya dengan `lerp_angle`).

## 16.9 Audio 3D

`AudioStreamPlayer3D` membuat suara terdengar berasal dari posisi tertentu, mengecil dengan jarak. Pengaturan penting: `Unit Size` (jangkauan), `Max Distance`, dan `Attenuation Model`. Kamera aktif bertindak sebagai "telinga" pemain (atau gunakan `AudioListener3D`).

## Ringkasan Bab 16

- Struktur first person: `CharacterBody3D` > `Head` > `Camera3D`.
- Badan berputar di sumbu Y, kepala di sumbu X, batasi sudut vertikal.
- Interaksi memakai `RayCast3D` dan pola `has_method("interact")`.
- `Area3D`, layer, mask, dan signal bekerja sama seperti di 2D.
- Pakai `Mesh > Create Collision Shape` untuk tabrakan cepat dari mesh.

## Latihan Bab 16

1. Buat player first person yang bisa berjalan, melompat, dan melihat sekeliling di scene 3D buatanmu.
2. Buat pintu 3D yang terbuka saat pemain menekan E sambil menghadapnya.
3. Buat zona `Area3D` yang mencetak pesan ketika pemain masuk.

---

# Bab 17 - Story dan Lore Tanpa Voice Actor

Cerita dalam game gameplay-first berfungsi sebagai **konteks** dan **motivasi**, bukan penghalang. Pemain tidak boleh dipaksa membaca banyak teks sebelum bisa bermain.

## 17.1 Prinsip menulis cerita untuk game indie

1. **Singkat**: satu kotak dialog sebaiknya hanya beberapa kalimat.
2. **Sambungkan ke aksi**: ceritakan hal yang relevan dengan apa yang sedang pemain lakukan.
3. **Opsional untuk lore dalam**: detail dunia ditaruh di item yang bisa dibaca (catatan, prasasti), sehingga pemain yang penasaran bisa menggali, pemain lain bisa melewatinya.
4. **Tunjukkan, jangan hanya katakan**: desain level yang menceritakan sesuatu (desa kosong, jejak pertempuran) sering lebih kuat daripada paragraf teks.
5. **Konsisten**: buat dokumen lore sederhana (siapa, apa, kapan, di mana) agar dunia tidak kontradiktif.

## 17.2 Cara menyampaikan cerita tanpa suara

|Teknik|Implementasi di Godot|
|---|---|
|Dialog NPC|Kotak dialog dengan efek mengetik (Bab 17.4)|
|Catatan, buku, prasasti|Objek interaktif yang membuka panel teks|
|Jurnal atau codex|Daftar entri lore yang terbuka seiring progres|
|Environmental storytelling|Tata letak level, dekorasi, pencahayaan, musik|
|Cutscene sederhana|`AnimationPlayer` yang menggerakkan kamera, karakter, dan memunculkan teks|
|Slide ilustrasi|Beberapa gambar statis dengan teks dan transisi fade (untuk pembuka dan penutup)|
|"Suara" karakter|Bunyi blip singkat per huruf dan potret karakter yang berubah ekspresi|

## 17.3 Menyimpan data dialog dengan Resource

Alih-alih menulis teks di dalam kode, simpan di resource agar bisa diedit di Inspector.

```gdscript
# dialogue_line.gd
class_name DialogueLine
extends Resource

@export var speaker: String = ""
@export_multiline var text: String = ""
@export var portrait: Texture2D
```

```gdscript
# dialogue_sequence.gd
class_name DialogueSequence
extends Resource

@export var lines: Array[DialogueLine] = []
```

Cara memakainya:

1. Di FileSystem, klik kanan > **New Resource**, cari `DialogueSequence`, simpan (misalnya `res://data/dialogue/elder_intro.tres`).
2. Klik file tersebut, di Inspector tambahkan elemen pada `Lines`, buat `New DialogueLine` untuk tiap baris, isi `Speaker` dan `Text`.

## 17.4 Kotak dialog dengan efek mengetik

Buat scene `DialogueBox` (nanti dijadikan Autoload di Bab 18) dengan struktur:

```
DialogueBox (CanvasLayer)             <- Process Mode: Always
 |-- Panel (PanelContainer)           <- tandai Unique Name: %Panel, atur di bagian bawah layar
      |-- MarginContainer
           |-- VBoxContainer
                |-- SpeakerLabel (Label)            <- Unique Name: %SpeakerLabel
                |-- TextLabel (RichTextLabel)       <- Unique Name: %TextLabel
```

Pada `TextLabel`, matikan `Scroll Active` dan aktifkan `Fit Content` jika ingin tinggi menyesuaikan.

```gdscript
extends CanvasLayer

signal dialogue_finished

@onready var panel: Control = %Panel
@onready var speaker_label: Label = %SpeakerLabel
@onready var text_label: RichTextLabel = %TextLabel
@onready var blip: AudioStreamPlayer = $Blip       # opsional, SFX "blip" singkat

const SECONDS_PER_CHAR: float = 0.03

var is_active: bool = false

var _lines: Array[DialogueLine] = []
var _index: int = 0
var _tween: Tween


func _ready() -> void:
    process_mode = Node.PROCESS_MODE_ALWAYS
    panel.hide()


func start(sequence: DialogueSequence) -> void:
    if is_active or sequence == null or sequence.lines.is_empty():
        return
    is_active = true
    _lines = sequence.lines
    _index = 0
    panel.show()
    get_tree().paused = true          # hentikan dunia game selama dialog
    _show_line()


func _show_line() -> void:
    var line: DialogueLine = _lines[_index]
    speaker_label.text = line.speaker
    text_label.text = line.text
    text_label.visible_ratio = 0.0

    if _tween:
        _tween.kill()
    _tween = create_tween()
    _tween.tween_property(text_label, "visible_ratio", 1.0, line.text.length() * SECONDS_PER_CHAR)


func _unhandled_input(event: InputEvent) -> void:
    if not is_active:
        return
    if event.is_action_pressed("interact") or event.is_action_pressed("ui_accept"):
        get_viewport().set_input_as_handled()
        if text_label.visible_ratio < 1.0:
            # Pemain menekan tombol saat teks masih mengetik: tampilkan semua
            _tween.kill()
            text_label.visible_ratio = 1.0
        else:
            _next_line()


func _next_line() -> void:
    _index += 1
    if _index >= _lines.size():
        _finish()
    else:
        _show_line()


func _finish() -> void:
    is_active = false
    panel.hide()
    get_tree().paused = false
    dialogue_finished.emit()
```

Konsep yang dipakai:

- `visible_ratio` (0 sampai 1) menentukan seberapa banyak teks `RichTextLabel` yang tampak. Di-tween dari 0 ke 1 menghasilkan efek mengetik.
- Menekan tombol saat sedang mengetik langsung menampilkan semua teks. Ini fitur kenyamanan penting.
- `get_tree().paused = true` menghentikan semua node dengan mode Pausable. `DialogueBox` diatur Always agar tetap berjalan.
- Variabel `is_active` mencegah dialog dimulai dua kali.

Menambah efek blip: hubungkan ke `Tween` dengan `tween_method`, atau gunakan `Timer` yang memainkan `blip` tiap beberapa huruf saat teks masih bergerak.

## 17.5 NPC dan objek yang memicu dialog

Pada scene NPC (root `Area2D` atau `StaticBody2D` dengan `Area2D` pendeteksi):

```gdscript
extends Area2D

@export var dialogue: DialogueSequence

var _player_in_range: bool = false


func _ready() -> void:
    body_entered.connect(_on_body_entered)
    body_exited.connect(_on_body_exited)


func _on_body_entered(body: Node2D) -> void:
    if body.is_in_group("player"):
        _player_in_range = true


func _on_body_exited(body: Node2D) -> void:
    if body.is_in_group("player"):
        _player_in_range = false


func _unhandled_input(event: InputEvent) -> void:
    if _player_in_range and not Dialogue.is_active and event.is_action_pressed("interact"):
        get_viewport().set_input_as_handled()
        Dialogue.start(dialogue)
```

`Dialogue` di sini adalah nama Autoload yang menunjuk ke scene `DialogueBox` (dibahas di Bab 18). Di Inspector NPC, seret file `elder_intro.tres` ke properti `Dialogue`. Dengan begitu satu skrip NPC bisa dipakai untuk puluhan NPC dengan dialog berbeda.

## 17.6 Lore yang bisa dikoleksi dan jurnal

Buat resource untuk entri lore:

```gdscript
# lore_entry.gd
class_name LoreEntry
extends Resource

@export var id: String = ""
@export var title: String = ""
@export_multiline var body: String = ""
```

Saat pemain membaca sebuah catatan (objek interaktif), buka entri lore dan simpan `id`-nya sebagai terbuka:

```gdscript
# di GameState (Autoload)
var unlocked_lore: Array[String] = []

func unlock_lore(entry_id: String) -> void:
    if entry_id not in unlocked_lore:
        unlocked_lore.append(entry_id)
```

Menu jurnal tinggal memuat semua `LoreEntry` dan menampilkan hanya yang `id`-nya ada di `unlocked_lore`.

## 17.7 Flag cerita: mengingat keputusan pemain

Banyak percabangan cerita sebenarnya hanya variabel **flag** (benar atau salah):

```gdscript
GameState.set_flag("met_elder")
GameState.set_flag("has_key")

if GameState.has_flag("met_elder"):
    print("Pemain sudah bertemu Tetua")
```

NPC bisa memilih dialog berbeda berdasarkan flag:

```gdscript
@export var dialogue_first_time: DialogueSequence
@export var dialogue_after: DialogueSequence

func _talk() -> void:
    if GameState.has_flag("met_elder"):
        Dialogue.start(dialogue_after)
    else:
        GameState.set_flag("met_elder")
        Dialogue.start(dialogue_first_time)
```

## 17.8 Alternatif: dialog dalam file JSON

Jika kamu atau penulis tim lebih nyaman mengedit teks di luar Godot, simpan dialog dalam JSON dan baca saat runtime.

`res://data/dialogue/elder.json`:

```json
{
  "id": "elder_intro",
  "lines": [
    { "speaker": "Tetua", "text": "Kau akhirnya datang, anak muda." },
    { "speaker": "Tetua", "text": "Tiga kristal telah hilang dari kuil." }
  ]
}
```

Membacanya:

```gdscript
func load_dialogue_json(path: String) -> Dictionary:
    var file: FileAccess = FileAccess.open(path, FileAccess.READ)
    if file == null:
        push_error("Gagal membuka: " + path)
        return {}
    var parsed: Variant = JSON.parse_string(file.get_as_text())
    if typeof(parsed) != TYPE_DICTIONARY:
        push_error("Format JSON tidak valid: " + path)
        return {}
    return parsed
```

Catatan: angka di JSON dibaca sebagai `float`. Pilih format sesuai alur kerjamu. Resource lebih nyaman di editor Godot, JSON lebih nyaman untuk penulis eksternal.

## 17.9 Cerita opening dan ending sederhana

Cara hemat biaya: 3 sampai 6 ilustrasi statis dengan teks, ditampilkan berurutan dengan transisi fade dan musik. Buat dengan `TextureRect` + `RichTextLabel` + `AnimationPlayer`, atau satu skrip yang menyimpan array berisi pasangan gambar dan teks.

## 17.10 Lokalisasi (opsional)

Godot mendukung terjemahan lewat file CSV atau PO. Jika kamu berencana merilis dalam banyak bahasa, tulis teks UI dan dialog dengan kunci terjemahan sejak awal, dan pakai `tr("KEY")`. Ini topik lanjutan, tetapi mengubah kebiasaan sejak awal jauh lebih mudah daripada memperbaikinya kelak.

## Ringkasan Bab 17

- Cerita mendukung gameplay: singkat, relevan, dan opsional untuk lore dalam.
- Gunakan Resource atau JSON untuk data dialog, bukan teks di dalam kode.
- Efek mengetik memakai `visible_ratio` dan Tween.
- Flag sederhana cukup untuk banyak percabangan cerita.
- Lore opsional lewat jurnal dan objek yang bisa dibaca.

## Latihan Bab 17

1. Buat `DialogueLine` dan `DialogueSequence`, lalu satu file dialog berisi tiga baris.
2. Buat kotak dialog dengan efek mengetik dan hubungkan ke seorang NPC.
3. Buat dialog kedua yang hanya muncul setelah flag tertentu aktif.

---

# Bab 18 - Autoload, Pergantian Scene, dan Game State

## 18.1 Masalah: data yang harus bertahan antar scene

Saat kamu berpindah dari scene menu ke scene level, scene lama dihapus beserta semua datanya. Namun beberapa hal harus bertahan: jumlah koin, flag cerita, pengaturan, musik latar. Solusinya: **Autoload**.

## 18.2 Apa itu Autoload

**Autoload** adalah skrip atau scene yang dimuat otomatis saat game dimulai dan tetap hidup selama game berjalan, tidak terpengaruh pergantian scene. Ia bisa diakses dari mana pun lewat nama global (disebut juga singleton).

Cara membuatnya:

1. Buat skrip, misalnya `res://scripts/autoload/game_state.gd`.
2. Buka `Project > Project Settings > Globals > Autoload`.
3. Pilih path skrip, isi **Node Name** (misalnya `GameState`), klik **Add**.

Sekarang `GameState` bisa dipakai di semua skrip.

Peringatan: jangan memberi `class_name` yang sama dengan nama Autoload (bentrok nama).

## 18.3 Contoh GameState

```gdscript
# game_state.gd (Autoload bernama GameState)
extends Node

signal coins_changed(new_value: int)
signal flag_changed(flag_name: String, value: bool)

var coins: int = 0
var flags: Dictionary = {}
var unlocked_lore: Array[String] = []


func add_coins(amount: int) -> void:
    coins += amount
    coins_changed.emit(coins)


func set_flag(flag_name: String, value: bool = true) -> void:
    flags[flag_name] = value
    flag_changed.emit(flag_name, value)


func has_flag(flag_name: String) -> bool:
    return flags.get(flag_name, false)


func unlock_lore(entry_id: String) -> void:
    if entry_id not in unlocked_lore:
        unlocked_lore.append(entry_id)


func reset() -> void:
    coins = 0
    flags.clear()
    unlocked_lore.clear()
    coins_changed.emit(coins)
```

Pola ini memberi satu "sumber kebenaran" untuk data progres. UI dan objek lain mendengarkan signal-nya.

## 18.4 Jangan berlebihan memakai Autoload

Autoload praktis, tetapi jika semuanya dijadikan global, kode jadi sulit dilacak. Aturan praktis: gunakan Autoload hanya untuk hal yang benar-benar global:

- Data progres (`GameState`).
- Sistem simpan dan muat (`SaveSystem`).
- Pengaturan (`Settings`).
- Pengelola pergantian scene (`SceneManager`).
- Kotak dialog (`Dialogue`) dan pemutar musik (`Music`).

## 18.5 Berpindah scene

Cara dasar:

```gdscript
get_tree().change_scene_to_file("res://scenes/levels/level_02.tscn")
```

Atau dengan `PackedScene` yang sudah dimuat:

```gdscript
@export var next_level: PackedScene

func go_next() -> void:
    get_tree().change_scene_to_packed(next_level)
```

Mulai ulang scene saat ini:

```gdscript
get_tree().reload_current_scene()
```

Keluar dari game:

```gdscript
get_tree().quit()
```

Penting: saat scene berganti, node scene lama dibebaskan dan semua variabel di dalamnya hilang. Data yang harus bertahan taruh di Autoload.

## 18.6 Transisi fade antar scene

Buat scene `SceneManager` (root `CanvasLayer`, `Layer` tinggi misalnya 100, anak `ColorRect` bernama `Fade` berwarna hitam, `Full Rect`, `Modulate` alpha awal 0, `Mouse Filter` diatur ke **Ignore**):

```gdscript
# scene_manager.gd (Autoload, dari scene)
extends CanvasLayer

@onready var fade: ColorRect = $Fade


func change_scene(path: String, duration: float = 0.3) -> void:
    var tween_out: Tween = create_tween()
    tween_out.tween_property(fade, "modulate:a", 1.0, duration)
    await tween_out.finished

    get_tree().change_scene_to_file(path)

    var tween_in: Tween = create_tween()
    tween_in.tween_property(fade, "modulate:a", 0.0, duration)
```

Pemakaian dari mana saja:

```gdscript
SceneManager.change_scene("res://scenes/levels/level_02.tscn")
```

## 18.7 Pause

```gdscript
get_tree().paused = true     # jeda dunia game
get_tree().paused = false    # lanjutkan
```

Node yang tidak boleh ikut berhenti (menu pause, kotak dialog) diatur `Process Mode` menjadi `Always` atau `When Paused` (lihat Bab 13.4).

## 18.8 Berbagi data antar scene tanpa Autoload

Untuk kasus sederhana, kamu bisa mengatur nilai pada scene baru sebelum menambahkannya:

```gdscript
var level_scene: PackedScene = preload("res://scenes/levels/level_02.tscn")
var level := level_scene.instantiate()
level.start_position = Vector2(100, 200)    # properti milik skrip level
add_child(level)
```

## Ringkasan Bab 18

- Autoload menyimpan data dan layanan global yang hidup antar scene.
- Gunakan secukupnya, jangan menjadikan semuanya global.
- `change_scene_to_file` untuk berpindah scene, `reload_current_scene` untuk mengulang.
- Transisi fade dibuat dengan `CanvasLayer` + `ColorRect` + Tween.

## Latihan Bab 18

1. Buat Autoload `GameState` dengan `coins` dan signal `coins_changed`. Hubungkan HUD ke signal tersebut.
2. Buat dua level dan pintu yang berpindah dari level 1 ke level 2.
3. Tambahkan transisi fade pada pergantian level.

---

# Bab 19 - Save, Load, dan Pengaturan (Offline)

Karena game kita offline, semua data disimpan lokal di komputer pemain. Godot menyediakan folder khusus untuk ini: **`user://`**.

## 19.1 Folder user://

`user://` selalu menunjuk ke folder data pengguna yang bisa ditulis, di semua platform, dan tidak berada di folder game. Lokasi sebenarnya bergantung pada sistem operasi dan nama proyek, kira-kira:

|Sistem|Lokasi umum|
|---|---|
|Windows|`%APPDATA%\Godot\app_userdata\NamaProyek\`|
|macOS|`~/Library/Application Support/Godot/app_userdata/NamaProyek/`|
|Linux|`~/.local/share/godot/app_userdata/NamaProyek/`|

Untuk membukanya dari editor: `Project > Open User Data Folder`. Dari kode: `OS.get_user_data_dir()`.

Jangan menyimpan save game ke `res://`. Folder `res://` tidak bisa ditulis setelah game diekspor.

## 19.2 Apa yang perlu disimpan

Rancang dulu apa yang ingin dipertahankan. Contoh untuk game petualangan kecil:

- Nama scene atau level saat ini.
- Posisi pemain.
- Nyawa dan jumlah koin.
- Flag cerita.
- Lore yang sudah terbuka.
- Item di inventaris.
- Waktu bermain.

Prinsip: simpan **data**, bukan objek. Objek seperti `Node` tidak disimpan langsung. Kamu menyimpan angka, teks, dan daftar yang cukup untuk membangun ulang keadaan.

## 19.3 Menyimpan dengan JSON

JSON adalah format teks yang mudah dibaca manusia dan mudah dipakai.

```gdscript
# save_system.gd (Autoload bernama SaveSystem)
extends Node

const SAVE_PATH: String = "user://savegame.json"
const SAVE_VERSION: int = 1


func has_save() -> bool:
    return FileAccess.file_exists(SAVE_PATH)


func save_game(player: Node2D) -> bool:
    var data: Dictionary = {
        "version": SAVE_VERSION,
        "scene": get_tree().current_scene.scene_file_path,
        "player_position": [player.global_position.x, player.global_position.y],
        "coins": GameState.coins,
        "flags": GameState.flags,
        "unlocked_lore": GameState.unlocked_lore,
    }

    var file: FileAccess = FileAccess.open(SAVE_PATH, FileAccess.WRITE)
    if file == null:
        push_error("Gagal menyimpan: %s" % error_string(FileAccess.get_open_error()))
        return false

    file.store_string(JSON.stringify(data, "\t"))
    file.close()
    return true


func load_game() -> Dictionary:
    if not has_save():
        return {}

    var file: FileAccess = FileAccess.open(SAVE_PATH, FileAccess.READ)
    if file == null:
        push_error("Gagal membuka save: %s" % error_string(FileAccess.get_open_error()))
        return {}

    var parsed: Variant = JSON.parse_string(file.get_as_text())
    file.close()

    if typeof(parsed) != TYPE_DICTIONARY:
        push_error("File save rusak atau tidak valid.")
        return {}

    return parsed
```

Penjelasan:

- `FileAccess.open(path, mode)` membuka file. Mengembalikan `null` jika gagal (cek hasilnya).
- `JSON.stringify(data, "\t")` mengubah Dictionary menjadi teks JSON dengan indentasi.
- `JSON.parse_string(teks)` mengubah teks JSON menjadi data GDScript. Jika gagal, hasilnya `null`.
- `Vector2` tidak bisa langsung disimpan ke JSON, jadi kita ubah menjadi array `[x, y]`.
- Angka dari JSON selalu terbaca sebagai `float`. Ubah ke `int(...)` saat memuat jika perlu.

## 19.4 Menerapkan data yang dimuat

```gdscript
func continue_game() -> void:
    var data: Dictionary = SaveSystem.load_game()
    if data.is_empty():
        return

    GameState.coins = int(data.get("coins", 0))
    GameState.flags = data.get("flags", {})
    GameState.unlocked_lore.assign(data.get("unlocked_lore", []))

    var scene_path: String = data.get("scene", "res://scenes/levels/level_01.tscn")
    SceneManager.change_scene(scene_path)
    # Setelah scene dimuat, level membaca posisi dari data dan memindahkan player
```

Pemulihan posisi pemain biasanya dilakukan oleh skrip level setelah scene siap. Simpan data muatan sementara di `GameState` (misalnya `pending_player_position`), lalu level membacanya di `_ready()`.

`unlocked_lore.assign(...)` dipakai karena `unlocked_lore` adalah array bertipe (`Array[String]`), dan `assign` mengisi array bertipe dari array biasa.

## 19.5 Praktik baik penyimpanan

- **Beri nomor versi** pada file save (`"version": 1`) agar kamu bisa menangani format lama saat game diperbarui.
- **Cek keberadaan kunci** dengan `data.get("key", nilai_bawaan)` agar tidak error jika kunci tidak ada.
- **Autosave** di titik aman (pindah level, checkpoint), bukan di tengah pertarungan.
- **Beberapa slot** save: gunakan nama file berbeda (`save_1.json`, `save_2.json`).
- **Cadangan**: sebelum menimpa, salin save lama menjadi `.bak` agar pemain tidak kehilangan progres jika proses terputus.
- Karena game offline, tidak perlu mengenkripsi save. Menjaga save tetap mudah dibaca justru membantu debugging.

## 19.6 Pengaturan dengan ConfigFile

Untuk pengaturan (volume, layar penuh), `ConfigFile` lebih cocok karena formatnya terstruktur per bagian:

```gdscript
# settings.gd (Autoload bernama Settings)
extends Node

const SETTINGS_PATH: String = "user://settings.cfg"

var music_volume: float = 0.8
var sfx_volume: float = 1.0
var fullscreen: bool = false


func _ready() -> void:
    load_settings()
    apply_settings()


func save_settings() -> void:
    var config: ConfigFile = ConfigFile.new()
    config.set_value("audio", "music", music_volume)
    config.set_value("audio", "sfx", sfx_volume)
    config.set_value("video", "fullscreen", fullscreen)
    config.save(SETTINGS_PATH)


func load_settings() -> void:
    var config: ConfigFile = ConfigFile.new()
    var err: Error = config.load(SETTINGS_PATH)
    if err != OK:
        return    # belum ada file, pakai nilai bawaan
    music_volume = config.get_value("audio", "music", music_volume)
    sfx_volume = config.get_value("audio", "sfx", sfx_volume)
    fullscreen = config.get_value("video", "fullscreen", fullscreen)


func apply_settings() -> void:
    _set_bus_volume("Music", music_volume)
    _set_bus_volume("SFX", sfx_volume)
    if fullscreen:
        DisplayServer.window_set_mode(DisplayServer.WINDOW_MODE_FULLSCREEN)
    else:
        DisplayServer.window_set_mode(DisplayServer.WINDOW_MODE_WINDOWED)


func _set_bus_volume(bus_name: String, linear_value: float) -> void:
    var index: int = AudioServer.get_bus_index(bus_name)
    if index == -1:
        return
    AudioServer.set_bus_volume_db(index, linear_to_db(linear_value))
    AudioServer.set_bus_mute(index, linear_value <= 0.001)
```

Slider volume di menu pengaturan tinggal mengubah `Settings.music_volume`, lalu memanggil `apply_settings()` dan `save_settings()`.

## 19.7 Mengubah kunci input (opsional lanjutan)

Pemain sering ingin mengubah tombol. Godot mendukung ini lewat `InputMap.action_erase_events()` dan `InputMap.action_add_event()`. Simpan pemetaan baru ke `ConfigFile`. Fitur ini nilai tambah, tetapi bukan prioritas untuk game pertama.

## Ringkasan Bab 19

- Simpan semua data lokal di `user://`.
- Simpan data (angka, teks, daftar), bukan objek node.
- JSON untuk save game, `ConfigFile` untuk pengaturan.
- Cek hasil operasi file, beri nomor versi, dan buat cadangan.

## Latihan Bab 19

1. Buat tombol Save yang menyimpan jumlah koin dan posisi pemain, lalu tombol Load yang memulihkannya.
2. Buka folder `user://` dari editor dan lihat isi file JSON-nya.
3. Buat menu pengaturan dengan slider volume yang tersimpan setelah game ditutup dan dibuka lagi.

---

# Bab 20 - Sistem Gameplay Dasar: Health, State Machine, Musuh, dan Game Feel

Bab ini merangkai konsep sebelumnya menjadi sistem yang membentuk inti gameplay.

## 20.1 Health dan damage

Gunakan `HealthComponent` dari Bab 12 sebagai node anak pada Player dan Musuh. Dengan begitu logika nyawa ditulis sekali.

Tambahkan **invulnerability frames** (kebal sesaat) agar pemain tidak mati dalam sekejap oleh serangan beruntun:

```gdscript
# di player.gd
@export var invulnerable_time: float = 0.8
var _invulnerable: bool = false

func take_hit(damage: int, from_position: Vector2) -> void:
    if _invulnerable:
        return
    $HealthComponent.take_damage(damage)
    _invulnerable = true

    # Knockback: dorong menjauh dari sumber serangan
    var knock_dir: Vector2 = (global_position - from_position).normalized()
    velocity = knock_dir * 250.0

    # Kedip selama kebal
    var tween: Tween = create_tween().set_loops(4)
    tween.tween_property($Sprite2D, "modulate:a", 0.3, invulnerable_time / 8.0)
    tween.tween_property($Sprite2D, "modulate:a", 1.0, invulnerable_time / 8.0)

    await get_tree().create_timer(invulnerable_time).timeout
    _invulnerable = false
```

## 20.2 State machine sederhana

Ketika karakter punya banyak keadaan (diam, berjalan, melompat, menyerang, terluka), kode `if` bertumpuk cepat menjadi berantakan. **State machine** mengatur: karakter hanya berada dalam satu state pada satu waktu, dan tiap state punya aturannya sendiri.

Versi paling sederhana dengan `enum` dan `match`:

```gdscript
extends CharacterBody2D

enum State { IDLE, RUN, JUMP, ATTACK, HURT }

var state: State = State.IDLE


func _physics_process(delta: float) -> void:
    if not is_on_floor():
        velocity += get_gravity() * delta

    match state:
        State.IDLE:
            _state_idle()
        State.RUN:
            _state_run()
        State.JUMP:
            _state_jump()
        State.ATTACK:
            _state_attack()
        State.HURT:
            _state_hurt()

    move_and_slide()


func change_state(new_state: State) -> void:
    if state == new_state:
        return
    state = new_state
    # Di sini bisa memutar animasi sesuai state baru


func _state_idle() -> void:
    velocity.x = move_toward(velocity.x, 0.0, 800.0)
    if Input.get_axis("move_left", "move_right") != 0.0:
        change_state(State.RUN)
    elif Input.is_action_just_pressed("attack"):
        change_state(State.ATTACK)


func _state_run() -> void:
    var dir: float = Input.get_axis("move_left", "move_right")
    velocity.x = dir * 200.0
    if dir == 0.0:
        change_state(State.IDLE)


func _state_jump() -> void:
    pass


func _state_attack() -> void:
    velocity.x = 0.0


func _state_hurt() -> void:
    pass
```

Keuntungan: tiap perilaku terisolasi, mudah menambah state baru, dan mudah men-debug karena kamu selalu tahu karakter sedang berada di state apa (cetak `State.keys()[state]` untuk melihat namanya).

## 20.3 Musuh patroli (platformer)

Struktur scene:

```
Slime (CharacterBody2D)
 |-- AnimatedSprite2D
 |-- CollisionShape2D
 |-- LedgeCheck (RayCast2D)       <- di depan kaki, menunjuk ke bawah
 |-- DetectionArea (Area2D)       <- area pendeteksi pemain
 |    |-- CollisionShape2D
 |-- Hitbox (Hitbox)              <- area yang melukai pemain
 |-- HealthComponent
```

```gdscript
extends CharacterBody2D

enum State { PATROL, CHASE }

@export var patrol_speed: float = 50.0
@export var chase_speed: float = 90.0

var state: State = State.PATROL
var direction: int = 1
var target: Node2D = null

@onready var ledge_check: RayCast2D = $LedgeCheck
@onready var sprite: AnimatedSprite2D = $AnimatedSprite2D


func _ready() -> void:
    $DetectionArea.body_entered.connect(_on_detection_body_entered)
    $DetectionArea.body_exited.connect(_on_detection_body_exited)
    add_to_group("enemies")


func _physics_process(delta: float) -> void:
    if not is_on_floor():
        velocity += get_gravity() * delta

    match state:
        State.PATROL:
            if is_on_floor() and (is_on_wall() or not ledge_check.is_colliding()):
                _flip()
            velocity.x = direction * patrol_speed
        State.CHASE:
            if target:
                var dir_to_target: float = signf(target.global_position.x - global_position.x)
                if dir_to_target != 0.0 and int(dir_to_target) != direction:
                    _flip()
                velocity.x = direction * chase_speed

    move_and_slide()


func _flip() -> void:
    direction *= -1
    sprite.flip_h = direction < 0
    ledge_check.position.x *= -1.0


func _on_detection_body_entered(body: Node2D) -> void:
    if body.is_in_group("player"):
        target = body
        state = State.CHASE


func _on_detection_body_exited(body: Node2D) -> void:
    if body == target:
        target = null
        state = State.PATROL
```

Penyesuaian di editor: posisikan `LedgeCheck` sedikit di depan kaki, dengan `Target Position` menunjuk ke bawah (misalnya `Vector2(0, 20)`), dan `Collision Mask` mencakup layer `world`.

## 20.4 Musuh top-down yang mengejar

```gdscript
extends CharacterBody2D

@export var speed: float = 40.0

var target: Node2D = null


func _physics_process(_delta: float) -> void:
    if target:
        velocity = global_position.direction_to(target.global_position) * speed
    else:
        velocity = Vector2.ZERO
    move_and_slide()
```

Untuk pencarian jalan yang menghindari tembok, Godot menyediakan `NavigationAgent2D` dan `NavigationAgent3D` bersama `NavigationRegion`. Ini topik lanjutan yang layak dipelajari setelah dasar kuat.

## 20.5 Game feel (juice)

"Juice" adalah umpan balik tambahan yang membuat aksi terasa memuaskan, tanpa mengubah aturan game. Beberapa teknik murah dan efektif:

|Teknik|Efek|
|---|---|
|Screen shake|Layar bergetar sesaat saat ledakan atau pukulan kuat|
|Hit stop|Game melambat sangat singkat saat serangan mengenai|
|Flash putih atau merah|Musuh berkedip saat terkena|
|Squash and stretch|Karakter memipih saat mendarat, memanjang saat melompat|
|Partikel|Debu saat mendarat, percikan saat terkena|
|SFX berlapis|Suara pukulan, suara musuh, dan suara kecil lain bersamaan|
|Knockback|Musuh terpental saat dipukul|

Screen shake sederhana pada `Camera2D`:

```gdscript
extends Camera2D

func shake(strength: float = 6.0, duration: float = 0.2) -> void:
    var steps: int = 6
    var tween: Tween = create_tween()
    for i in steps:
        var target_offset: Vector2 = Vector2(
            randf_range(-strength, strength),
            randf_range(-strength, strength)
        )
        tween.tween_property(self, "offset", target_offset, duration / steps)
    tween.tween_property(self, "offset", Vector2.ZERO, 0.05)
```

Hit stop:

```gdscript
func hit_stop(duration: float = 0.06) -> void:
    Engine.time_scale = 0.05
    # Parameter keempat true: timer mengabaikan time_scale
    await get_tree().create_timer(duration, true, false, true).timeout
    Engine.time_scale = 1.0
```

Partikel di Godot memakai `GPUParticles2D` atau `CPUParticles2D` (lebih kompatibel untuk perangkat lama). Mulailah dengan `CPUParticles2D` dan preset sederhana.

## 20.6 Merancang loop gameplay

Pertanyaan desain yang berguna untuk setiap game:

1. Apa **aksi inti** yang dilakukan pemain berulang kali? (melompat, menembak, mengumpulkan, memecahkan teka-teki)
2. Apa **tantangan** yang menghalangi? (musuh, jebakan, batas waktu, teka-teki)
3. Apa **hadiah** setelah berhasil? (kemajuan cerita, kemampuan baru, area baru, skor)
4. Apa yang **berubah** seiring waktu agar tidak monoton? (kesulitan, mekanik baru, lingkungan baru)

Jika kamu bisa menjawab keempat pertanyaan itu dalam satu kalimat tiap pertanyaan, kamu punya fondasi game.

## 20.7 Kesulitan dan keseimbangan

- Mulai dengan nilai yang mudah. Lebih baik pemain menang terlalu mudah di awal daripada frustrasi.
- Gunakan `@export` untuk semua angka keseimbangan (nyawa, damage, kecepatan) agar bisa disetel tanpa menyentuh kode.
- Ajak teman bermain. Perhatikan di mana mereka bingung atau frustrasi tanpa menjelaskan apa pun. Itu masukan paling jujur.

## Ringkasan Bab 20

- Gunakan komponen (Health, Hitbox, Hurtbox) agar sistem dapat dipakai ulang.
- State machine merapikan perilaku karakter dan musuh yang kompleks.
- Patroli dan pengejaran sederhana sudah cukup untuk banyak game.
- Juice (screen shake, hit stop, flash, partikel) meningkatkan kualitas rasa bermain secara signifikan.

## Latihan Bab 20

1. Buat musuh slime yang berpatroli dan membalik saat bertemu dinding atau tepi.
2. Buat player kehilangan nyawa saat disentuh musuh, dengan knockback dan kedip kebal.
3. Tambahkan screen shake saat player terkena damage.

---

# Bab 21 - Debugging dan Optimasi Dasar

## 21.1 Mindset debugging

Bug adalah hal normal dalam pembuatan game. Langkah umum menghadapinya:

1. **Reproduksi**: pastikan kamu bisa memunculkan bug secara konsisten.
2. **Isolasi**: cari bagian mana yang bermasalah. Matikan atau sederhanakan hal lain.
3. **Observasi**: cetak nilai variabel, lihat debugger.
4. **Hipotesis dan uji**: ubah satu hal pada satu waktu.
5. **Perbaiki dan verifikasi**.

## 21.2 Alat debugging dasar

**Print:**

```gdscript
print("Nilai health: ", health)
print_debug("Dipanggil dari fungsi ini")      # menyertakan lokasi di kode
push_warning("Peringatan: nilai kosong")      # tampil kuning di Debugger
push_error("Terjadi kesalahan")               # tampil merah di Debugger
```

**Assert**: menghentikan game di mode debug jika kondisi salah, berguna untuk mendeteksi asumsi yang keliru:

```gdscript
assert(health >= 0, "Health tidak boleh negatif")
```

**Breakpoint**: klik di margin kiri editor skrip (sebelah nomor baris) hingga muncul titik merah. Saat game berjalan dan eksekusi mencapai baris itu, game berhenti dan kamu bisa melihat isi variabel di panel Debugger, lalu melanjutkan langkah demi langkah (Step Into, Step Over, Continue).

## 21.3 Panel Debugger

Saat game berjalan, panel **Debugger** di bawah memiliki tab penting:

|Tab|Isi|
|---|---|
|Stack Trace|Urutan pemanggilan fungsi saat error atau breakpoint|
|Errors|Daftar error dan peringatan|
|Profiler|Waktu eksekusi tiap fungsi, untuk mencari kode yang lambat|
|Visual Profiler|Waktu render per frame|
|Monitors|Grafik FPS, memori, jumlah objek, dan sebagainya|
|Misc|Info tambahan|

## 21.4 Remote Scene Tree

Saat game berjalan, di Scene dock ada pilihan **Remote**. Ini menampilkan pohon scene yang sedang hidup. Kamu bisa memilih node dan mengubah propertinya di Inspector secara langsung untuk bereksperimen (perubahan tidak tersimpan). Sangat membantu untuk memeriksa apakah sebuah node benar-benar ada, atau berapa nilai variabelnya saat ini.

## 21.5 Opsi menu Debug

- **Visible Collision Shapes**: tampilkan semua bentuk tabrakan.
- **Visible Paths** dan **Visible Navigation**: tampilkan jalur dan mesh navigasi.
- **Keep Debug Menu Open** dan opsi lain sesuai versi.

## 21.6 Kesalahan runtime yang sering muncul

|Pesan atau gejala|Kemungkinan penyebab dan solusi|
|---|---|
|"Invalid access to property or key ... on a base object of type 'null instance'"|Variabel bernilai `null`. Cek path node (`$Nama`), pastikan node ada dan sudah siap (`@onready`)|
|"Node not found: ..."|Path node salah atau struktur scene berubah|
|Objek tidak muncul|Lupa `add_child()`, posisi di luar kamera, atau `visible = false`|
|Player tembus lantai|Tidak ada `CollisionShape2D`, shape belum diatur, atau layer dan mask tidak cocok|
|Area tidak mendeteksi|Mask Area tidak mencakup layer objek, atau `monitoring` mati|
|Signal tidak jalan|Lupa `connect`, nama signal salah, atau node pemancar dihapus|
|Game membeku|Loop tak berujung di `while`, atau `await` yang tidak pernah selesai|
|Teks atau tombol tidak merespons|`mouse_filter` pada node di atasnya menghalangi (ubah ke Ignore)|

## 21.7 Optimasi dasar

Mayoritas game 2D indie dan 3D sederhana sudah berjalan lancar tanpa optimasi khusus. Jangan mengoptimasi sebelum ada masalah nyata. Namun ada kebiasaan baik sejak awal:

1. **Simpan referensi node** dengan `@onready` alih-alih memanggil `get_node` atau `$` berulang di `_process`.
2. **Hindari pekerjaan berat tiap frame**: loop besar, pencarian group terus-menerus, pembuatan objek tiap frame.
3. **Gunakan signal** alih-alih mengecek kondisi tiap frame (polling) bila memungkinkan.
4. **Gunakan tipe data eksplisit** pada GDScript.
5. **Hapus objek yang tidak dipakai** dengan `queue_free()` (peluru yang keluar layar, efek yang selesai).
6. **Nonaktifkan proses** pada objek yang jauh dari layar dengan `VisibleOnScreenNotifier2D`.
7. **Kompres dan gabungkan gambar**: gunakan atlas atau spritesheet, jangan memakai gambar yang jauh lebih besar dari kebutuhan.
8. **3D**: batasi jumlah cahaya dinamis dan bayangan, gunakan model low-poly, atur jarak render (`Far`) secukupnya.
9. **Ukur dulu, baru optimasi**: gunakan Profiler untuk menemukan bagian paling lambat.

Menampilkan FPS saat pengembangan:

```gdscript
func _process(_delta: float) -> void:
    $FPSLabel.text = "FPS: %d" % Engine.get_frames_per_second()
```

## 21.8 Uji di komputer lain

Game yang berjalan mulus di komputermu belum tentu mulus di komputer pemain. Uji pada perangkat lebih lemah jika memungkinkan. Jika targetmu perangkat lama, pertimbangkan renderer Compatibility sejak awal.

## Ringkasan Bab 21

- Reproduksi, isolasi, observasi, uji, perbaiki.
- Gunakan `print`, breakpoint, Debugger, dan Remote Scene Tree.
- Banyak bug berasal dari path node salah, `null`, atau layer/mask tidak cocok.
- Ukur performa dengan Profiler sebelum mengoptimasi.

## Latihan Bab 21

1. Sengaja salah menulis nama node pada `$` dan baca pesan error di Debugger.
2. Pasang breakpoint di fungsi lompat dan amati nilai `velocity` saat berhenti.
3. Jalankan game, buka Remote Scene Tree, dan ubah warna sprite pemain secara langsung.

---

# Bab 22 - Export, Distribusi, dan Version Control

## 22.1 Persiapan sebelum export

- Isi **Project Settings > Application > Config**: nama game, ikon, dan versi.
- Atur **Main Scene** ke menu utama.
- Pastikan tidak ada path absolut dalam kode.
- Uji alur lengkap: menu, bermain, simpan, muat, keluar.
- Hapus `print` debug yang berlebihan.
- Siapkan `CREDITS.md` berisi semua aset pihak ketiga dan lisensinya.

## 22.2 Memasang Export Templates

Untuk mengekspor, Godot membutuhkan **export templates** yang versinya sama persis dengan editormu.

1. Buka `Editor > Manage Export Templates`.
2. Klik **Download and Install** (butuh internet satu kali).
3. Tunggu hingga selesai.

## 22.3 Mengekspor game

1. Buka `Project > Export`.
2. Klik **Add...** dan pilih platform (Windows Desktop, Linux, macOS, atau Android).
3. Atur opsi preset. Untuk Windows, kamu bisa mengisi ikon dan informasi produk.
4. Opsi **Embed PCK** menyatukan data game ke dalam satu file executable (lebih praktis dibagikan). Jika tidak diaktifkan, kamu mendapat file `.exe` dan file `.pck` yang harus dibagikan bersama.
5. Klik **Export Project**, pilih lokasi, nama file, dan pastikan kotak **Export With Debug** tidak dicentang untuk versi rilis.

Catatan per platform:

|Platform|Catatan|
|---|---|
|Windows|Paling mudah. Hasil berupa `.exe` (dan `.pck` jika tidak di-embed)|
|Linux|Hasil berupa executable. Beri izin eksekusi bila perlu|
|macOS|Ada ketentuan penandatanganan (code signing) dan notarization dari Apple agar mudah dijalankan di Mac lain. Prosesnya lebih rumit, baca dokumentasi resmi|
|Android|Perlu JDK dan Android SDK yang diatur di Editor Settings. Jika game dirancang untuk keyboard dan mouse, perlu penyesuaian kontrol sentuh|

Selalu uji hasil export di komputer lain atau akun pengguna lain yang bersih, bukan hanya di komputer tempat kamu mengembangkan.

## 22.4 Distribusi

Pilihan umum bagi developer indie:

- **itch.io**: mudah untuk pemula, bisa gratis atau berbayar, cocok untuk game jam dan demo.
- **Steam**: jangkauan luas, ada biaya pendaftaran dan proses peninjauan. Cek ketentuan terbaru di situs resmi Steamworks.
- **Game Jolt**, **Google Play**, dan lainnya sesuai target platform.

Rilis demo atau versi awal kecil lebih awal untuk mendapatkan masukan sebelum membuat game penuh.

## 22.5 Lisensi dan atribusi

- Godot berlisensi MIT. Kamu perlu menyertakan pemberitahuan lisensi Godot dalam game (misalnya di layar kredit atau berkas teks). Editor menyediakan teks lisensi di `Help > About Godot`.
- Penuhi atribusi untuk aset pihak ketiga sesuai lisensi masing-masing.
- Simpan bukti lisensi aset (tangkapan layar halaman atau file lisensi) di folder proyek.

## 22.6 Version control dengan Git

**Version control** merekam riwayat perubahan proyek sehingga kamu bisa kembali ke versi lama, mencoba eksperimen dengan aman, dan bekerja dalam tim.

Dasar Git:

```
git init                         # mulai repositori di folder proyek
git add .                        # tandai semua perubahan
git commit -m "Tambah player"    # simpan snapshot dengan pesan
git log --oneline                # lihat riwayat
```

File `.gitignore` untuk Godot minimal berisi:

```
.godot/
*.translation
export/
builds/
```

Alasannya: folder `.godot/` adalah cache yang dibuat ulang otomatis dan tidak perlu disimpan. Jika kamu mengaktifkan opsi Version Control saat membuat proyek, Godot membuat `.gitignore` untuk kamu.

Praktik baik:

- Commit kecil dan sering dengan pesan jelas.
- Gunakan branch untuk fitur eksperimen.
- Simpan repositori di layanan seperti GitHub, GitLab, atau Codeberg sebagai cadangan jarak jauh.
- Untuk aset biner besar (audio, model, gambar besar), pertimbangkan Git LFS.
- Terapkan prinsip cadangan 3-2-1: tiga salinan, dua jenis media, satu di luar lokasi.

## 22.7 Checklist sebelum rilis

- Game bisa dimulai, dimainkan sampai akhir, dan ditutup tanpa crash.
- Save dan load bekerja, termasuk setelah game ditutup dan dibuka lagi.
- Pengaturan volume dan layar penuh bekerja.
- Tidak ada teks placeholder (misalnya "lorem ipsum").
- Semua aset punya lisensi yang sesuai dan kredit sudah dicantumkan.
- Sudah diuji oleh orang lain.
- Halaman toko memiliki deskripsi, tangkapan layar, dan (opsional) trailer singkat.

## Ringkasan Bab 22

- Pasang export templates yang cocok dengan versi editor.
- Uji hasil export di komputer lain.
- Perhatikan lisensi Godot dan aset pihak ketiga.
- Gunakan Git dan `.gitignore` yang benar untuk menjaga proyek aman.

## Latihan Bab 22

1. Ekspor game latihanmu untuk sistem operasimu dan jalankan dari luar editor.
2. Inisialisasi repositori Git untuk proyekmu dan buat commit pertama.
3. Buat `CREDITS.md` berisi daftar aset dan lisensinya.

---

# Bab 23 - Mini Proyek: Game Petualangan Kecil "Kuil Kristal"

Mini proyek ini menggabungkan hampir semua materi di buku. Targetnya adalah game top-down 2D yang bisa selesai dalam beberapa hari sampai 2 minggu untuk pemula.

## 23.1 Konsep

- **Premis**: Seorang pengembara memasuki kuil tua untuk menemukan tiga kristal yang hilang dan membuka pintu ke ruang utama.
- **Aksi inti**: menjelajah, mengumpulkan kristal, menghindari slime, berbicara dengan penjaga kuil.
- **Tantangan**: slime yang mengejar, tata letak ruangan.
- **Hadiah**: pintu terbuka, potongan lore, ending singkat.
- **Durasi bermain**: 5 sampai 10 menit.
- **Tanpa voice actor**: dialog teks, SFX, dan musik latar.
- **Offline**: save di `user://`.

## 23.2 Daftar fitur (scope terkunci)

Wajib:

1. Menu utama (Mulai, Lanjutkan, Pengaturan, Keluar).
2. Player top-down dengan animasi idle dan jalan.
3. Tiga ruangan dengan TileMapLayer.
4. 3 kristal yang bisa dikumpulkan (menambah `coins`).
5. Satu NPC penjaga kuil dengan dialog (dua versi: sebelum dan sesudah pengumpulan kristal).
6. Dua sampai tiga slime yang mengejar pemain saat terdeteksi.
7. Nyawa pemain (3 hati), kebal sesaat, game over, dan ulang.
8. Pintu yang terbuka saat tiga kristal terkumpul.
9. Ending singkat berupa dialog atau layar teks.
10. Save dan load.
11. Musik latar dan SFX (ambil kristal, terkena damage, pintu terbuka).
12. Menu pause dan pengaturan volume.

Opsional (hanya jika waktu cukup): jurnal lore, dua jenis musuh, minimap.

Aturan: jangan menambah fitur wajib baru di tengah jalan.

## 23.3 Susunan folder

```
res://
  assets/ (sprites, audio, fonts)
  data/dialogue/ (guardian_intro.tres, guardian_after.tres)
  entities/
    player/ (player.tscn, player.gd)
    enemies/ (slime.tscn, slime.gd)
    items/ (crystal.tscn, crystal.gd)
    npc/ (guardian.tscn, guardian.gd)
    world/ (door.tscn, door.gd)
  components/ (health_component.gd, hitbox.gd, hurtbox.gd)
  scenes/
    levels/ (temple_main.tscn)
    ui/ (main_menu.tscn, hud.tscn, pause_menu.tscn, settings_menu.tscn, game_over.tscn)
  scripts/autoload/ (game_state.gd, save_system.gd, settings.gd, scene_manager.gd)
  scenes/ui/dialogue_box.tscn  (Autoload "Dialogue")
```

## 23.4 Langkah pengerjaan (milestone)

**Milestone 1 - Fondasi (Bab 2 sampai 7)**

- Buat proyek, struktur folder, dan Input Map (`move_*`, `interact`, `pause`).
- Atur resolusi dan texture filter sesuai gaya visual.
- Kriteria selesai: proyek terbuka, scene kosong berjalan dengan F5.

**Milestone 2 - Player (Bab 8, 11)**

- Buat `Player` top-down dengan `CharacterBody2D`, `Motion Mode` Floating, animasi idle dan jalan, `Camera2D`.
- Kriteria selesai: pemain bisa berjalan 8 arah dan animasi sesuai arah.

**Milestone 3 - Level (Bab 9, 10)**

- Buat tileset, `TileMapLayer` untuk lantai dan dinding dengan collision.
- Susun tiga ruangan yang terhubung.
- Kriteria selesai: pemain tidak bisa menembus dinding.

**Milestone 4 - Item dan Game State (Bab 9, 18)**

- Buat Autoload `GameState`.
- Buat `Crystal` (Area2D) yang menambah koin dan memutar SFX.
- Buat HUD yang menampilkan jumlah kristal.
- Kriteria selesai: mengambil kristal menambah angka di HUD.

**Milestone 5 - Pintu dan progres (Bab 12, 18)**

- Buat `Door` yang membuka ketika koin mencapai 3.
- Kriteria selesai: pintu terbuka setelah semua kristal terkumpul.

**Milestone 6 - Musuh dan nyawa (Bab 12, 20)**

- Buat `HealthComponent`, `Hitbox`, `Hurtbox`, slime pengejar.
- Terapkan kebal sesaat dan knockback pada pemain.
- Buat layar game over dengan tombol ulang.
- Kriteria selesai: pemain bisa terluka, mati, dan mengulang.

**Milestone 7 - Cerita (Bab 17)**

- Buat sistem dialog dan NPC penjaga kuil.
- Dialog berbeda sebelum dan sesudah mengumpulkan semua kristal (pakai flag).
- Buat ending singkat.
- Kriteria selesai: cerita dapat diikuti dari awal sampai akhir.

**Milestone 8 - Save, pengaturan, audio (Bab 14, 19)**

- Implementasikan `SaveSystem` dan `Settings`.
- Tambahkan musik dan SFX.
- Kriteria selesai: tutup game, buka lagi, tombol Lanjutkan memulihkan progres.

**Milestone 9 - Polish dan rilis (Bab 20 sampai 22)**

- Tambahkan juice (screen shake, kedip, partikel sederhana).
- Uji bersama teman, perbaiki bug.
- Ekspor dan uji di komputer lain.
- Unggah ke itch.io sebagai versi pertamamu.

## 23.5 Contoh kode kunci

**Kristal:**

```gdscript
# crystal.gd
extends Area2D

@onready var sfx: AudioStreamPlayer = $PickupSFX
@onready var sprite: Sprite2D = $Sprite2D

var _collected: bool = false


func _ready() -> void:
    body_entered.connect(_on_body_entered)


func _on_body_entered(body: Node2D) -> void:
    if _collected or not body.is_in_group("player"):
        return
    _collected = true
    GameState.add_coins(1)
    set_deferred("monitoring", false)
    sprite.hide()
    sfx.play()
    await sfx.finished
    queue_free()
```

**Pintu:**

```gdscript
# door.gd
extends StaticBody2D

@export var required_coins: int = 3

@onready var shape: CollisionShape2D = $CollisionShape2D
@onready var sprite: Sprite2D = $Sprite2D


func _ready() -> void:
    GameState.coins_changed.connect(_on_coins_changed)
    _on_coins_changed(GameState.coins)


func _on_coins_changed(total: int) -> void:
    if total >= required_coins:
        _open()


func _open() -> void:
    shape.set_deferred("disabled", true)
    var tween: Tween = create_tween()
    tween.tween_property(sprite, "modulate:a", 0.0, 0.5)
```

**Menandai penjaga setelah semua kristal terkumpul:** panggil `GameState.set_flag("all_crystals")` pada skrip `Door` saat `_open()`, lalu NPC memilih dialog berdasarkan flag tersebut (lihat Bab 17.7).

**Ending:** saat pemain memasuki `Area2D` di ruang utama, panggil `Dialogue.start(ending_dialogue)` lalu sambungkan `Dialogue.dialogue_finished` untuk berpindah ke scene kredit atau menu utama.

## 23.6 Rubrik penilaian diri

Beri nilai 1 sampai 5 untuk tiap poin setelah selesai:

- Kontrol terasa nyaman.
- Tujuan jelas tanpa banyak penjelasan.
- Ada umpan balik (suara dan animasi) untuk aksi penting.
- Tidak ada bug yang menghalangi progres.
- Save dan load bekerja andal.
- Cerita tersampaikan tanpa mengganggu gameplay.

Catat tiga hal yang akan kamu perbaiki di proyek berikutnya. Itu inti dari belajar.

---

# Bab 24 - Roadmap Belajar, Kesalahan Umum, Glosarium, dan Cheat Sheet

## 24.1 Roadmap belajar setelah buku ini

**Bulan 1 sampai 2: kuatkan dasar**

- Selesaikan 3 sampai 5 game mini (Pong, Breakout, Flappy-style, shooter sederhana, platformer satu level).
- Baca dokumentasi resmi bagian "Getting started" dan "Tutorials".

**Bulan 3 sampai 4: perdalam topik inti**

- Pelajari `AnimationTree`, shader dasar, `NavigationAgent`, dan partikel lebih jauh.
- Pelajari `Resource` kustom secara mendalam untuk data game (item, senjata, musuh).
- Ikut game jam (misalnya yang diadakan di itch.io atau komunitas Godot) untuk berlatih membatasi scope dan menyelesaikan game dalam waktu singkat.

**Bulan 5 sampai 6: proyek lebih serius**

- Rancang game yang sedikit lebih besar dengan dokumen desain singkat.
- Pelajari optimasi, struktur proyek yang lebih besar, dan unit pengujian sederhana.
- Rilis demo dan kumpulkan masukan.

**Topik lanjutan yang bisa dipelajari kemudian**

- Shader (Godot Shading Language) dan efek visual.
- C# sebagai alternatif bahasa skrip.
- GDExtension untuk kode native.
- Lokalisasi, aksesibilitas, dukungan gamepad penuh.
- Pipeline aset 3D (Blender ke Godot), animasi karakter, rigging.
- Integrasi toko seperti Steam (lewat add-on komunitas).

## 24.2 Ide proyek latihan bertahap

|Tingkat|Ide|Konsep yang dilatih|
|---|---|---|
|1|Pong|Input, gerak, collision, skor|
|1|Klik koin (clicker)|UI, signal, save sederhana|
|2|Breakout|Fisika, level, power-up|
|2|Flappy-style|Spawn objek, game over, skor tertinggi|
|3|Platformer 1 level|Player, tilemap, musuh, kamera|
|3|Top-down shooter|Peluru, musuh, health, gelombang|
|4|Petualangan kecil (Bab 23)|Dialog, save, scene, cerita|
|4|Koleksi 3D low-poly|Player 3D, kamera, interaksi, level|
|5|Dungeon crawler kecil|Prosedural sederhana, inventaris, sistem item|

## 24.3 Sumber belajar

- **Dokumentasi resmi Godot** (docs.godotengine.org): rujukan utama, tersedia juga versi offline di editor.
- **Dokumentasi bawaan editor** (F1): selalu cocok dengan versi yang kamu pakai.
- **Komunitas**: forum resmi Godot, Discord resmi, dan komunitas Godot Indonesia di berbagai platform.
- **Saluran video**: cari seri tutorial Godot 4 dari kreator-kreator yang aktif. Selalu cek tanggal dan versi video.
- **Aset**: Kenney, OpenGameArt, itch.io, dan Asset Library bawaan Godot.

Tips menjaga ilmu tetap terkini di tahun 2027 dan seterusnya: Godot merilis versi baru secara berkala. Saat belajar dari sumber lama, cocokkan nama node dan fungsi dengan dokumentasi versi yang kamu pakai. Sebelum meng-upgrade engine di tengah proyek, baca catatan rilis dan panduan upgrade. Perubahan antar versi minor (4.x ke 4.y) umumnya kecil tetapi tidak selalu nol. Buat cadangan atau commit sebelum meng-upgrade.

## 24.4 Kesalahan umum pemula

|Kesalahan|Cara menghindari|
|---|---|
|Scope terlalu besar|Mulai dari game mini, kunci daftar fitur sejak awal|
|Tidak menyimpan dan tidak memakai Git|Commit rutin, cadangan 3-2-1|
|Salah memakai tutorial Godot 3 untuk Godot 4|Periksa versi, pelajari tabel perbedaan di Bab 2.2|
|Hard-code angka di dalam kode|Gunakan `@export` dan `const`|
|Mengurusi grafis sebelum gameplay|Prototype dengan bentuk sederhana dulu|
|Semua kode menumpuk di satu skrip|Pecah menjadi scene dan komponen kecil|
|Semua dijadikan Autoload|Autoload hanya untuk hal yang benar-benar global|
|Memakai `_process` untuk fisika|Pakai `_physics_process`|
|Tidak menguji di komputer lain|Uji export di mesin bersih|
|Mengabaikan lisensi aset|Catat sumber dan lisensi sejak awal|
|Tidak pernah menyelesaikan game|Targetkan rilis versi kecil dan utuh|
|Bandingkan dengan game profesional|Bandingkan dengan dirimu bulan lalu|

## 24.5 Glosarium

|Istilah|Arti|
|---|---|
|Anchor|Titik acuan posisi node UI terhadap induknya|
|Asset|Berkas konten game (gambar, suara, model)|
|Autoload|Skrip atau scene global yang hidup sepanjang game berjalan|
|Bus (audio)|Jalur pengelompokan suara untuk mengatur volume dan efek|
|Callback|Fungsi yang dipanggil engine pada saat tertentu|
|CharacterBody|Node untuk karakter yang dikendalikan lewat kode|
|Collision Layer|Penanda "saya berada di layer apa"|
|Collision Mask|Penanda "saya mendeteksi layer apa"|
|Delta|Selisih waktu antar frame (detik)|
|Export (variabel)|Variabel yang tampil di Inspector (`@export`)|
|Export (proyek)|Proses membangun game menjadi program yang bisa dimainkan|
|Frame|Satu gambar dalam urutan render|
|FPS|Frame per detik|
|Game feel / juice|Umpan balik tambahan yang membuat aksi terasa memuaskan|
|Game loop|Siklus input, update, dan render yang berulang|
|GDScript|Bahasa skrip bawaan Godot|
|Hitbox|Area yang menyakiti|
|Hurtbox|Area yang bisa disakiti|
|Inspector|Panel pengubah properti node|
|Instance|Salinan hidup dari sebuah scene atau class|
|Lore|Latar belakang dan sejarah dunia game|
|Mesh|Bentuk 3D yang tersusun dari poligon|
|Node|Blok bangunan dasar di Godot|
|Prototype|Versi kasar untuk menguji ide|
|Resource|Wadah data yang bisa disimpan dan dibagikan|
|Scene|Kumpulan node yang disimpan sebagai berkas|
|Scene Tree|Pohon semua node yang aktif saat game berjalan|
|Scope|Ruang lingkup proyek|
|Signal|Mekanisme pemberitahuan antar node|
|Singleton|Objek tunggal yang diakses global|
|Sprite|Gambar 2D|
|State machine|Pola pengaturan keadaan karakter satu per satu|
|Tilemap|Level 2D yang disusun dari ubin gambar|
|Tween|Animasi perubahan nilai dari kode|
|Velocity|Kecepatan dan arah gerak|
|Viewport|Area tempat dunia game digambar|

## 24.6 Cheat sheet GDScript dan Godot

```gdscript
# --- Dasar ---
extends CharacterBody2D
class_name Player

@export var speed: float = 200.0
@onready var sprite: Sprite2D = $Sprite2D
signal died

const MAX_HP: int = 5
var hp: int = MAX_HP

# --- Siklus hidup ---
func _ready() -> void: pass
func _process(delta: float) -> void: pass
func _physics_process(delta: float) -> void: pass
func _unhandled_input(event: InputEvent) -> void: pass

# --- Input ---
Input.is_action_pressed("jump")
Input.is_action_just_pressed("jump")
Input.get_axis("move_left", "move_right")
Input.get_vector("move_left", "move_right", "move_up", "move_down")

# --- Gerak karakter ---
velocity = direction * speed
move_and_slide()
is_on_floor()
get_gravity()

# --- Scene dan node ---
var scene: PackedScene = preload("res://entities/enemy.tscn")
var node = scene.instantiate()
add_child(node)
node.queue_free()
get_tree().change_scene_to_file("res://scenes/level.tscn")
get_tree().reload_current_scene()
get_tree().paused = true
get_tree().quit()

# --- Signal ---
button.pressed.connect(_on_pressed)
died.emit()

# --- Group ---
add_to_group("enemies")
body.is_in_group("player")
get_tree().get_nodes_in_group("enemies")

# --- Timer dan Tween ---
await get_tree().create_timer(1.0).timeout
var tween: Tween = create_tween()
tween.tween_property(self, "modulate:a", 0.0, 0.5)

# --- Matematika ---
clampf(x, 0.0, 1.0)
lerpf(a, b, 0.5)
move_toward(current, target, step)
randf_range(0.0, 1.0)
randi_range(1, 6)
deg_to_rad(90.0)
vec.normalized()
vec.length()
a.distance_to(b)
a.direction_to(b)

# --- File ---
FileAccess.open("user://save.json", FileAccess.WRITE)
FileAccess.file_exists("user://save.json")
JSON.stringify(data)
JSON.parse_string(text)

# --- Debug ---
print("nilai: ", x)
push_warning("peringatan")
push_error("error")
assert(x > 0, "x harus positif")
```

Pintasan editor yang sering dipakai:

|Pintasan|Fungsi|
|---|---|
|F5|Jalankan proyek|
|F6|Jalankan scene aktif|
|F1|Cari dokumentasi|
|Ctrl+S|Simpan|
|Ctrl+Klik pada nama|Lompat ke definisi atau dokumentasi|

## 24.7 Penutup

Membuat game adalah keterampilan yang tumbuh lewat praktik. Kamu tidak perlu menghafal semua yang ada di buku ini. Yang paling penting adalah kebiasaan ini:

1. Mulai dari yang kecil.
2. Jalankan dan uji sesering mungkin.
3. Prioritaskan gameplay yang menyenangkan.
4. Rapikan struktur sambil berjalan.
5. Selesaikan game, lalu rilis.

Game kecil yang selesai jauh lebih berharga daripada game besar yang tidak pernah rampung. Selamat belajar dan selamat berkarya.

---

Catatan versi: buku ini mengacu pada Godot 4.7.x. Nama node dan fungsi pada bab-bab di atas termasuk bagian inti Godot 4 yang stabil. Jika ada perbedaan kecil di versi yang lebih baru, rujuk dokumentasi resmi di editor (F1) atau di docs.godotengine.org sesuai versi yang kamu pakai.