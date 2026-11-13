# Game Developer Indie dengan Godot Engine (Tingkat Menengah)

**Fokus: Game 2D, Cerita dan Lore Pendukung Gameplay, Tanpa Voice Actor, Game Offline**

Edisi: November 2026 Bahasa pemrograman utama: GDScript (Godot 4.x)

---

## Daftar Isi

- Kata Pengantar dan Cara Memakai Buku Ini
- Bagian 0: Persiapan
    - Bab 1: Peta Jalan, Versi Godot, dan Filosofi Buku
    - Bab 2: Menyiapkan Proyek 2D yang Rapi
- Bagian 1: Fondasi Menengah
    - Bab 3: GDScript Menengah
    - Bab 4: Arsitektur Scene dan Komposisi
    - Bab 5: Signal, Group, dan Autoload
- Bagian 2: Gameplay 2D
    - Bab 6: Input dan Pergerakan Karakter
    - Bab 7: State Machine
    - Bab 8: Sistem Combat (Health, Hitbox, Hurtbox)
    - Bab 9: Animasi
    - Bab 10: TileMapLayer dan Desain Level
    - Bab 11: Kamera dan Game Feel
    - Bab 12: Musuh dan AI Sederhana
    - Bab 13: Desain Berbasis Data dengan Resource
    - Bab 14: Spawning, Proyektil, dan Pickup
- Bagian 3: Cerita dan Lore (Tanpa Voice Actor)
    - Bab 15: Cerita yang Melayani Gameplay
    - Bab 16: Sistem Dialog
    - Bab 17: Lore, Codex, dan Penceritaan Lewat Lingkungan
    - Bab 18: Cutscene Tanpa Suara Manusia
    - Bab 19: Lokalisasi (Multi-Bahasa)
- Bagian 4: Game Offline
    - Bab 20: Sistem Save dan Load
    - Bab 21: Pengaturan (Settings), Audio, dan Rebinding Input
    - Bab 22: UI, Menu, Pause, dan Pergantian Scene
- Bagian 5: Kualitas dan Rilis
    - Bab 23: Debugging dan Profiling
    - Bab 24: Optimasi Game 2D
    - Bab 25: Testing dan Playtest
    - Bab 26: Export dan Distribusi
- Bagian 6: Proyek Akhir
    - Bab 27: Proyek Capstone "Lentera Rimba"
    - Bab 28: Mengelola Scope dan Jalan Menuju Rilis
- Lampiran
    - A: Glosarium
    - B: Cheat Sheet
    - C: Kesalahan Umum
    - D: Sumber Belajar Lanjutan

---

## Kata Pengantar dan Cara Memakai Buku Ini

Buku ini dibuat untuk Anda yang sudah pernah membuka Godot, mungkin sudah mengikuti satu atau dua tutorial dasar, tetapi merasa proyek Anda cepat berantakan begitu fiturnya bertambah. Itu pertanda yang bagus: Anda siap naik ke tingkat menengah.

Pada tingkat menengah, pertanyaan Anda berubah. Bukan lagi "bagaimana membuat karakter bergerak", tetapi:

- Bagaimana menyusun kode agar bisa ditambah fitur tanpa merusak fitur lama?
- Bagaimana membuat gerakan karakter terasa enak, bukan sekadar berfungsi?
- Bagaimana menyimpan progres pemain dengan aman?
- Bagaimana menyampaikan cerita tanpa pengisi suara dan tanpa mengorbankan gameplay?
- Bagaimana menyelesaikan game, bukan hanya memulainya?

### Batasan Buku Ini

|Aspek|Keputusan|
|---|---|
|Dimensi|2D saja. Tidak membahas 3D.|
|Cerita dan lore|Ada, tetapi sebagai pendukung. Gameplay adalah bintang utama.|
|Voice actor|Tidak ada. Seluruh cerita lewat teks, visual, musik, dan efek suara.|
|Mode|Offline, pemain tunggal. Tidak membahas multiplayer atau server.|
|Bahasa|GDScript. C# tidak dibahas.|

### Cara Membaca

1. Ikuti berurutan untuk Bagian 0 sampai 2. Bagian 3 sampai 5 boleh dibaca sesuai kebutuhan.
2. Ketik kodenya sendiri, jangan hanya salin-tempel. Salah ketik adalah bagian dari belajar.
3. Kerjakan "Latihan" di akhir bab. Latihan itu sengaja dibuat kecil.
4. Gunakan satu proyek yang sama (proyek capstone di Bab 27) sebagai tempat menerapkan semuanya.

### Konvensi Penulisan

- Kode ditulis dalam blok kode. Nama variabel dan fungsi memakai bahasa Inggris (standar industri), sedangkan penjelasan memakai bahasa Indonesia.
- Setiap istilah teknis dijelaskan saat pertama muncul, dan dikumpulkan di Lampiran A.
- Blok "Catatan" berisi hal yang sering membingungkan. Blok "Jebakan" berisi kesalahan yang sering terjadi.

---

# Bagian 0: Persiapan

## Bab 1: Peta Jalan, Versi Godot, dan Filosofi Buku

### 1.1 Versi Godot yang Dipakai

Buku ini ditulis untuk **Godot 4.x**. Semua konsep di sini berlaku untuk seluruh seri 4.x, tetapi beberapa fitur baru memerlukan versi minimum tertentu. Yang penting untuk Anda ketahui:

|Fitur|Versi minimum|Catatan|
|---|---|---|
|`TileMapLayer` (pengganti `TileMap`)|4.3|Node `TileMap` lama sudah ditandai usang (deprecated).|
|Typed Dictionary (`Dictionary[String, int]`)|4.4|Opsional, tetapi sangat membantu.|
|Web export single-thread|4.3|Tidak lagi wajib pengaturan header khusus di server.|
|Integer scaling untuk pixel art|4.3|Berguna agar piksel tidak terlihat "bergetar".|

Per penulisan buku ini, rilis stabil resmi yang saya verifikasi di situs Godot adalah seri 4.6 (dirilis Januari 2026) dengan rilis perbaikan 4.6.1 (Februari 2026). Ada kemungkinan sudah ada rilis yang lebih baru saat Anda membaca ini. Cek selalu di godotengine.org. Aturan praktisnya:

- Pilih versi stabil terbaru **saat memulai proyek**, lalu **tetap di versi itu** sampai proyek selesai, kecuali ada perbaikan bug penting. Berpindah versi di tengah jalan menambah risiko tanpa menambah nilai.
- Unduh versi **standar** (GDScript), bukan versi .NET, kecuali Anda memang ingin memakai C#.
- Jika ada perbedaan kecil antara buku ini dan editor Anda (nama properti, letak menu), buka dokumentasi resmi untuk versi Anda di docs.godotengine.org.

### 1.2 Mengapa Godot Cocok untuk Indie 2D

- Godot memiliki mesin 2D yang asli (native), bukan 3D yang "dipaksa" menjadi 2D. Koordinat piksel bekerja langsung.
- Ukuran editor kecil, cepat dibuka, dan gratis dengan lisensi MIT. Tidak ada royalti.
- Sistem scene dan node membuat kita berpikir dalam potongan kecil yang bisa dipakai ulang.
- GDScript dirancang khusus untuk Godot dan mudah dibaca.

### 1.3 Filosofi Buku: Gameplay Dahulu, Cerita Menyusul

Banyak developer indie pemula tenggelam karena menulis lore sepanjang novel sebelum ada satu pun mekanik yang menyenangkan. Aturan yang dipakai buku ini:

1. **Core loop dahulu.** Core loop adalah rangkaian aksi yang diulang-ulang pemain, misalnya "jelajah, bertarung, ambil upgrade, jelajah lebih jauh". Jika loop ini tidak menyenangkan tanpa cerita, cerita tidak akan menyelamatkannya.
2. **Cerita sebagai bumbu.** Cerita dan lore memberi alasan mengapa pemain bertindak, bukan menghalangi mereka bertindak.
3. **Tanpa voice actor.** Ini menguntungkan: biaya lebih murah, perubahan naskah lebih mudah, dan lokalisasi jauh lebih ringan.
4. **Offline.** Tidak ada server berarti tidak ada biaya hosting, tidak ada masalah latensi, dan tidak ada celah keamanan jaringan. Fokus penuh pada pengalaman pemain tunggal yang solid.

### 1.4 Peta Jalan Belajar (Perkiraan)

|Tahap|Isi|Perkiraan waktu (paruh waktu)|
|---|---|---|
|1|Bagian 0 dan 1|1 sampai 2 minggu|
|2|Bagian 2 (gameplay)|3 sampai 5 minggu|
|3|Bagian 3 dan 4 (cerita, save, UI)|3 sampai 4 minggu|
|4|Bagian 5 dan 6 (kualitas, rilis, capstone)|4 sampai 8 minggu|

Angka ini hanya perkiraan. Kecepatan belajar tiap orang berbeda.

### Rangkuman Bab 1

- Pakai satu versi Godot 4.x yang stabil sepanjang proyek.
- Gameplay adalah prioritas, cerita mendukungnya.
- Batasan (2D, offline, tanpa suara manusia) adalah keuntungan untuk developer solo atau tim kecil.

---

## Bab 2: Menyiapkan Proyek 2D yang Rapi

Proyek yang rapi sejak hari pertama menghemat puluhan jam di kemudian hari.

### 2.1 Struktur Folder

Ada dua gaya umum: berdasarkan **jenis berkas** (semua skrip di satu folder, semua gambar di folder lain) atau berdasarkan **fitur** (semua berkas milik "pemain" ada di folder pemain). Untuk game yang makin besar, gaya berdasarkan fitur jauh lebih mudah dirawat, karena berkas yang saling terkait letaknya berdekatan.

Contoh struktur yang disarankan:

```
res://
  assets/
    art/
    audio/
      music/
      sfx/
    fonts/
  autoload/              <- skrip global (Events, GameState, SaveManager, ...)
  components/            <- komponen yang dipakai ulang (health, hitbox, ...)
  data/
    items/               <- berkas .tres untuk item
    enemies/
    dialogues/
    lore/
  entities/
    player/
    enemies/
    npcs/
    pickups/
  levels/
  ui/
  localization/
```

Aturan nama:

- Folder dan berkas: `snake_case` (huruf kecil, pemisah garis bawah), misalnya `player_idle.png`, `health_component.gd`.
- Nama class dan node: `PascalCase`, misalnya `HealthComponent`.
- Variabel dan fungsi: `snake_case`.
- Konstanta: `SCREAMING_SNAKE_CASE`.
- Signal: kata kerja bentuk lampau, misalnya `died`, `health_changed`.

Alasan memakai huruf kecil untuk nama berkas: Windows tidak membedakan huruf besar-kecil, tetapi Linux dan hasil export (`.pck`) membedakannya. Proyek yang berjalan di komputer Anda bisa gagal di komputer pemain gara-gara `Player.png` versus `player.png`.

### 2.2 Pengaturan Proyek untuk Pixel Art

Jika game Anda bergaya pixel art, atur hal berikut di **Project > Project Settings**:

|Pengaturan|Nilai yang disarankan|Fungsi|
|---|---|---|
|Display > Window > Size > Viewport Width / Height|320 x 180 (atau 480 x 270)|Resolusi "dunia" game. Angka kecil membuat piksel terlihat besar.|
|Display > Window > Size > Window Width Override / Height Override|1280 x 720|Ukuran jendela saat dimainkan.|
|Display > Window > Stretch > Mode|`canvas_items` atau `viewport`|Cara layar diskalakan.|
|Display > Window > Stretch > Aspect|`keep`|Menjaga rasio.|
|Display > Window > Stretch > Scale Mode|`integer`|Skala kelipatan bulat agar piksel tajam.|
|Rendering > Textures > Canvas Textures > Default Texture Filter|`Nearest`|Tanpa penghalusan, piksel tetap tajam.|
|Rendering > 2D > Snap > Snap 2D Transforms to Pixel|aktif (opsional)|Mengurangi getaran piksel saat bergerak.|

Catatan: untuk game 2D non-pixel (misalnya gambar vektor atau lukisan), biarkan filter pada `Linear` dan pilih resolusi dasar seperti 1920 x 1080.

### 2.3 Layer Collision Diberi Nama

Buka **Project Settings > Layer Names > 2D Physics** dan beri nama tiap layer. Ini kebiasaan kecil yang sangat menyelamatkan. Contoh:

|Layer|Nama|
|---|---|
|1|world|
|2|player|
|3|enemy|
|4|player_hitbox|
|5|enemy_hitbox|
|6|hurtbox_player|
|7|hurtbox_enemy|
|8|pickup|
|9|interactable|

Konsep singkatnya:

- **Layer** = "saya ini apa".
- **Mask** = "saya mau mendeteksi apa".

Jadi musuh yang berada di layer `enemy` dan memiliki mask `world` akan bertabrakan dengan dinding tetapi tidak dengan pemain (kecuali mask-nya juga mencakup `player`).

### 2.4 Version Control dengan Git

Gunakan Git sejak awal. Ini bukan opsional untuk proyek yang serius, karena Git memungkinkan Anda "kembali ke kemarin" jika sesuatu rusak.

Berkas `.gitignore` minimal untuk Godot 4:

```
# Godot 4
.godot/
*.translation

# Android / export
/android/
export_credentials.cfg
*.apk
*.aab

# Hasil build
/build/
```

Tips:

- Commit kecil dan sering, dengan pesan yang jelas: "Tambah coyote time pada lompatan".
- Gunakan format teks untuk scene (`.tscn`) dan resource (`.tres`), yang memang bawaan Godot, agar perubahan terbaca di Git.
- Jika proyek memiliki berkas besar (musik, sprite sheet besar), pertimbangkan Git LFS.
- Simpan cadangan di tempat lain (repositori daring atau disk eksternal).

### 2.5 Setup Editor

- Aktifkan **Editor Settings > Text Editor > Behavior > Indent > Type: Tabs** (standar GDScript memakai tab).
- Aktifkan **warning** GDScript dan perlakukan dengan serius. Warning sering menunjukkan bug yang belum terjadi.
- Pelajari pintasan keyboard dasar: `F5` (jalankan proyek), `F6` (jalankan scene aktif), `Ctrl+D` (duplikat), `Ctrl+Shift+F` (cari di seluruh proyek).

### Latihan Bab 2

1. Buat proyek baru, atur resolusi pixel art 320 x 180, dan jendela 1280 x 720.
2. Buat struktur folder seperti contoh di atas.
3. Beri nama minimal 6 layer collision 2D.
4. Inisialisasi repositori Git dan buat commit pertama.

---

# Bagian 1: Fondasi Menengah

## Bab 3: GDScript Menengah

Bab ini bukan pengantar GDScript. Anggap Anda sudah tahu variabel, `if`, `for`, dan fungsi. Kita fokus pada fitur yang membedakan kode amatir dan kode yang tahan lama.

### 3.1 Static Typing (Pengetikan Statis)

Di GDScript Anda boleh menulis variabel tanpa tipe (dynamic typing). Tetapi menambahkan tipe memberi tiga keuntungan: editor memberi saran kode lebih baik, kesalahan tertangkap sebelum game dijalankan, dan kode sedikit lebih cepat.

```gdscript
# Tanpa tipe: boleh, tapi rawan salah
var speed = 200

# Dengan tipe eksplisit
var speed: float = 200.0

# Tipe disimpulkan otomatis dengan :=
var jump_height := 64.0   # float
var player_name := "Aria" # String

# Fungsi dengan tipe parameter dan tipe kembalian
func take_damage(amount: int) -> void:
	health -= amount

func get_direction() -> Vector2:
	return Input.get_vector("move_left", "move_right", "move_up", "move_down")

# Array bertipe
var enemies: Array[Node2D] = []
var inventory: Array[ItemData] = []

# Dictionary bertipe (Godot 4.4+)
var flags: Dictionary[String, bool] = {}
```

Aturan praktis: **beri tipe pada semua yang bisa diberi tipe**. Gunakan `:=` bila tipenya jelas dari sisi kanan.

Jebakan: `:=` tidak bisa menyimpulkan tipe dari nilai bertipe Variant, misalnya hasil `JSON.parse_string()`. Dalam kasus itu tulis `var data: Variant = ...`.

### 3.2 `class_name` dan Pewarisan

`class_name` mendaftarkan skrip sebagai tipe global, sehingga bisa dipakai sebagai tipe variabel dan muncul di dialog "Create Node".

```gdscript
class_name Player
extends CharacterBody2D
```

Setelah itu Anda bisa menulis `var target: Player`, atau memeriksa `if body is Player:`.

Pewarisan dan `super()`:

```gdscript
# enemy_base.gd
class_name EnemyBase
extends CharacterBody2D

@export var max_health: int = 3

func _ready() -> void:
	print("Musuh siap")

func take_hit(amount: int) -> void:
	max_health -= amount
```

```gdscript
# slime.gd
class_name Slime
extends EnemyBase

func _ready() -> void:
	super()                 # jalankan _ready milik EnemyBase dulu
	print("Slime siap")
```

Gunakan pewarisan hemat. Terlalu dalam (A mewarisi B mewarisi C mewarisi D) membuat kode sulit diikuti. Alternatifnya adalah komposisi, dibahas di Bab 4.

### 3.3 Variabel Export

`@export` menampilkan variabel di Inspector sehingga desainer (atau Anda sendiri) bisa mengubah nilai tanpa menyentuh kode.

```gdscript
@export var speed: float = 180.0
@export_range(0.0, 1.0, 0.05) var friction: float = 0.2
@export_enum("Lemah", "Sedang", "Kuat") var tier: int = 0
@export_multiline var note: String
@export_file("*.tscn") var next_level_path: String
@export var icon: Texture2D
@export var stats: EnemyData            # resource buatan sendiri
@export var patrol_points: Array[Marker2D]

@export_group("Lompatan")
@export var jump_velocity: float = -380.0
@export var coyote_time: float = 0.1
```

`@export_group` hanya merapikan tampilan di Inspector.

### 3.4 `@onready`, Node Unik, dan `get_node`

Node anak baru siap setelah scene masuk ke tree. `@onready` menunda penugasan sampai `_ready()`.

```gdscript
@onready var sprite: AnimatedSprite2D = $AnimatedSprite2D
@onready var health: HealthComponent = %HealthComponent
```

Tanda `%` memakai **Unique Name**: klik kanan node, pilih "Access as Unique Name". Keuntungannya, kode tidak patah ketika Anda memindahkan node ke tempat lain dalam scene yang sama.

### 3.5 Setter dan Getter

Jalankan kode setiap kali variabel berubah:

```gdscript
var health: int = 3:
	set(value):
		health = clampi(value, 0, max_health)
		health_changed.emit(health, max_health)
		if health == 0:
			died.emit()
```

Cocok untuk menjaga agar nilai selalu valid dan UI otomatis diperbarui.

### 3.6 Enum dan `match`

```gdscript
enum Facing { LEFT, RIGHT }
enum EnemyState { IDLE, PATROL, CHASE, ATTACK, HURT, DEAD }

var state: EnemyState = EnemyState.IDLE

func _physics_process(delta: float) -> void:
	match state:
		EnemyState.IDLE:
			_do_idle(delta)
		EnemyState.PATROL:
			_do_patrol(delta)
		EnemyState.CHASE:
			_do_chase(delta)
		_:
			pass
```

Enum menggantikan "angka sihir" (`if state == 2`) yang tidak bisa dibaca orang lain, bahkan oleh Anda sendiri sebulan kemudian.

### 3.7 `await` dan Coroutine

`await` menjeda fungsi sampai suatu signal terjadi, tanpa membekukan game.

```gdscript
func flash_white() -> void:
	sprite.modulate = Color(3, 3, 3)
	await get_tree().create_timer(0.08).timeout
	sprite.modulate = Color.WHITE
```

Jebakan: jika node dihapus saat fungsi masih menunggu, Godot bisa menampilkan error. Periksa `is_inside_tree()` setelah `await` jika ada kemungkinan node hilang.

### 3.7a Lambda dan Callable

```gdscript
button.pressed.connect(func(): print("Ditekan"))

# Menyambung dengan argumen tambahan
button.pressed.connect(_on_button_pressed.bind("start"))

func _on_button_pressed(which: String) -> void:
	print(which)
```

### 3.8 Konstanta, `preload`, dan `load`

```gdscript
const BULLET_SCENE: PackedScene = preload("res://entities/pickups/bullet.tscn")
```

- `preload` dimuat saat skrip dikompilasi. Jalurnya harus berupa string literal.
- `load` dimuat saat dipanggil. Jalurnya boleh berupa variabel.

### 3.9 Fungsi Statis dan Kelas Pembantu

Untuk fungsi murni yang tidak bergantung pada node, gunakan `static func`:

```gdscript
class_name MathUtil

static func approach(current: float, target: float, step: float) -> float:
	return move_toward(current, target, step)
```

Panggil dengan `MathUtil.approach(a, b, c)`.

### 3.10 Anotasi `@warning_ignore`

Kadang Godot memberi warning yang Anda tahu aman. Matikan dengan sengaja dan sempit:

```gdscript
@warning_ignore("unused_signal")
signal player_died
```

Jangan mematikan warning secara global.

### Latihan Bab 3

1. Tulis skrip `HealthComponent` dengan setter yang menjaga nilai 0 sampai `max_health`.
2. Buat `enum` untuk keadaan musuh dan fungsi `match` yang mencetak keadaan.
3. Tulis fungsi dengan `await` yang membuat sprite berkedip tiga kali.

---

## Bab 4: Arsitektur Scene dan Komposisi

### 4.1 Scene adalah Blok Bangunan

Di Godot, **scene** bukan hanya "level". Scene adalah paket node yang bisa disimpan dan dipakai ulang (di-instance). Pemain adalah scene. Musuh adalah scene. Tombol menu adalah scene. Level adalah scene yang berisi instance scene lain.

Prinsip: **satu scene, satu tanggung jawab**. Scene `Player` mengurus pemain, bukan HUD dan bukan kamera seluruh game.

### 4.2 Komposisi Lebih Baik daripada Pewarisan Dalam

Bayangkan Anda punya Pemain, Musuh, Peti, dan Drum Peledak. Semua bisa rusak/terkena damage. Pendekatan pewarisan membuat Anda berdebat tentang siapa mewarisi siapa. Pendekatan komposisi membuat Anda cukup menempelkan satu node `HealthComponent` ke semuanya.

Contoh struktur scene musuh dengan komponen:

```
Slime (CharacterBody2D)            <- slime.gd
  AnimatedSprite2D
  CollisionShape2D                 <- badan fisik
  HealthComponent (Node)           <- health_component.gd
  Hurtbox (Area2D)                 <- hurtbox.gd, bisa kena serang
    CollisionShape2D
  Hitbox (Area2D)                  <- hitbox.gd, memberi damage ke pemain
    CollisionShape2D
  StateMachine (Node)
    Idle (Node)
    Chase (Node)
    Hurt (Node)
```

Keuntungan: `HealthComponent` ditulis sekali, dites sekali, dipakai di mana-mana.

### 4.3 "Call Down, Signal Up"

Aturan emas komunikasi antar node:

- **Panggil ke bawah**: induk boleh memanggil fungsi anaknya langsung (`$Sprite.play("run")`), karena induk mengenal anaknya.
- **Signal ke atas**: anak tidak boleh bergantung pada induknya. Ia cukup memancarkan signal, dan induk yang memutuskan reaksinya.

Contoh buruk (anak mengenal induk dan "kakaknya"):

```gdscript
# Di HealthComponent
func die() -> void:
	get_parent().get_node("../HUD").hide()   # rapuh!
```

Contoh baik:

```gdscript
# Di HealthComponent
signal died

func die() -> void:
	died.emit()
```

```gdscript
# Di slime.gd (induk)
func _ready() -> void:
	$HealthComponent.died.connect(_on_died)

func _on_died() -> void:
	queue_free()
```

Hasilnya, `HealthComponent` bisa dipakai di scene mana pun tanpa mengubah satu baris pun.

### 4.4 Menyusun Level

Struktur level yang umum:

```
Level01 (Node2D)
  TileMapLayer (Ground)
  TileMapLayer (Decoration)
  Entities (Node2D)
    Player (instance)
    Slime (instance)
    Slime2 (instance)
  Pickups (Node2D)
  Markers (Node2D)
    PlayerSpawn (Marker2D)
    ExitDoor (instance)
  Camera2D
```

Mengelompokkan dengan node kosong (`Entities`, `Pickups`) membuat editor tidak penuh sesak dan memudahkan kode mencari anak berdasarkan kategori.

### 4.5 Urutan Gambar (Z-Index dan Y-Sort)

Untuk game 2D, urutan menggambar penting:

- **Urutan node**: node yang berada lebih bawah di daftar digambar di atas.
- **Z Index**: angka yang lebih besar digambar di atas.
- **Y Sort**: aktifkan `y_sort_enabled` pada induk. Objek yang lebih rendah di layar digambar di depan. Sangat berguna untuk game top-down (pemain berjalan di belakang pohon, lalu di depan pohon).

### Latihan Bab 4

1. Buat scene `HealthComponent` yang berdiri sendiri, lalu pasang ke scene pemain dan scene musuh.
2. Pastikan kode `HealthComponent` tidak memakai `get_parent()` sama sekali.

---

## Bab 5: Signal, Group, dan Autoload

### 5.1 Signal Mendalam

Signal adalah cara sebuah node berkata "sesuatu terjadi" tanpa peduli siapa yang mendengar.

```gdscript
# Mendeklarasikan
signal health_changed(current: int, maximum: int)

# Memancarkan
health_changed.emit(health, max_health)

# Menyambung (di tempat lain)
health_component.health_changed.connect(_on_health_changed)

func _on_health_changed(current: int, maximum: int) -> void:
	bar.value = float(current) / maximum * 100.0
```

Opsi sambungan yang berguna:

```gdscript
# Hanya sekali, lalu otomatis putus
signal_name.connect(_handler, CONNECT_ONE_SHOT)

# Memutus manual
signal_name.disconnect(_handler)

# Cek apakah sudah tersambung
if not signal_name.is_connected(_handler):
	signal_name.connect(_handler)
```

Menunggu signal dengan `await`:

```gdscript
await $AnimationPlayer.animation_finished
await get_tree().process_frame
await get_tree().physics_frame
```

### 5.2 Group

Group adalah label yang bisa ditempelkan pada node. Cocok untuk "semua musuh", "semua objek yang bisa disimpan", atau "semua objek yang bisa dibuka".

```gdscript
# Menambah (bisa juga lewat tab Node > Groups di editor)
add_to_group("enemies")

# Mengambil semua anggota
for e in get_tree().get_nodes_in_group("enemies"):
	e.take_hit(1)

# Memanggil fungsi pada semua anggota sekaligus
get_tree().call_group("enemies", "become_alert")
```

### 5.3 Autoload (Singleton)

**Autoload** adalah skrip atau scene yang dimuat otomatis saat game mulai dan tetap ada selama game berjalan. Daftarkan di **Project Settings > Globals > Autoload** (di beberapa versi tab ini bernama "Autoload").

Autoload yang lazim dipakai game indie:

|Nama|Tugas|
|---|---|
|`Events`|Event bus: kumpulan signal global.|
|`GameState`|Data progres game (flag cerita, item, lokasi terakhir).|
|`SaveManager`|Baca dan tulis berkas save.|
|`AudioManager`|Musik dan efek suara.|
|`SceneChanger`|Perpindahan scene dengan transisi.|
|`Settings`|Pengaturan pemain.|

### 5.4 Event Bus

Event bus adalah autoload yang isinya hanya signal. Berguna ketika dua bagian game yang jauh letaknya perlu berkomunikasi tanpa saling mengenal, misalnya pickup koin (di level) dan penghitung koin (di HUD).

```gdscript
# autoload/events.gd  (daftarkan sebagai autoload bernama "Events")
extends Node

@warning_ignore("unused_signal")
signal coin_collected(amount: int)
@warning_ignore("unused_signal")
signal player_died
@warning_ignore("unused_signal")
signal flag_changed(flag_name: String, value: bool)
@warning_ignore("unused_signal")
signal lore_unlocked(entry_id: StringName)
```

```gdscript
# coin.gd
func _on_body_entered(body: Node2D) -> void:
	if body is Player:
		Events.coin_collected.emit(1)
		queue_free()
```

```gdscript
# hud.gd
func _ready() -> void:
	Events.coin_collected.connect(_on_coin_collected)

func _on_coin_collected(amount: int) -> void:
	coins += amount
	%CoinLabel.text = str(coins)
```

### 5.5 Jangan Berlebihan dengan Autoload

Autoload itu nyaman tetapi berbahaya jika berlebihan, karena semua bagian game mulai bergantung padanya dan Anda kesulitan mengetes bagian tertentu secara terpisah. Pedoman:

- Pakai autoload untuk hal yang **memang global**: audio, save, pengaturan, event bus, state progres.
- Jangan jadikan autoload sebagai tempat menaruh semua variabel "biar gampang diakses".
- Jika sebuah scene hanya butuh satu data dari scene lain, pertimbangkan meneruskannya lewat `@export` atau parameter fungsi.

### Latihan Bab 5

1. Buat autoload `Events` dengan signal `coin_collected`.
2. Buat scene `Coin` dan scene `HUD` yang berkomunikasi hanya lewat `Events`.
3. Tambahkan group `"enemies"` ke semua musuh dan buat tombol debug yang memanggil `become_alert` pada semuanya.

---

# Bagian 2: Gameplay 2D

## Bab 6: Input dan Pergerakan Karakter

### 6.1 Input Map

Jangan pernah mengecek tombol secara langsung (misalnya `KEY_SPACE`). Selalu pakai **action** yang didefinisikan di **Project Settings > Input Map**. Dengan begitu satu action bisa dipetakan ke keyboard, gamepad, dan tombol yang bisa diubah pemain.

Action yang disarankan: `move_left`, `move_right`, `move_up`, `move_down`, `jump`, `attack`, `dash`, `interact`, `pause`.

```gdscript
Input.is_action_pressed("move_left")        # sedang ditahan
Input.is_action_just_pressed("jump")        # baru ditekan frame ini
Input.is_action_just_released("jump")       # baru dilepas frame ini
Input.get_axis("move_left", "move_right")   # -1.0 sampai 1.0
Input.get_vector("move_left", "move_right", "move_up", "move_down")  # Vector2
```

Untuk event yang hanya sekali (misalnya dialog lanjut), pakai `_unhandled_input`:

```gdscript
func _unhandled_input(event: InputEvent) -> void:
	if event.is_action_pressed("interact"):
		_try_interact()
		get_viewport().set_input_as_handled()
```

### 6.2 `_process` versus `_physics_process`

|Fungsi|Dipanggil|Cocok untuk|
|---|---|---|
|`_process(delta)`|Setiap frame gambar (laju bervariasi)|Visual, UI, animasi, kamera|
|`_physics_process(delta)`|Interval tetap (bawaan 60 kali per detik)|Pergerakan, tabrakan, logika gameplay|

`delta` adalah waktu (detik) sejak panggilan sebelumnya. Mengalikan kecepatan dengan `delta` membuat gerakan konsisten walau frame rate berubah.

### 6.3 Platformer: CharacterBody2D yang Terasa Enak

`CharacterBody2D` adalah node untuk karakter yang digerakkan lewat kode. Anda mengatur properti `velocity`, lalu memanggil `move_and_slide()` yang menggerakkan sambil menangani tabrakan.

Gerakan "benar secara teknis" belum tentu terasa enak. Tiga teknik berikut adalah standar industri untuk platformer:

1. **Coyote time**: pemain masih boleh melompat sesaat (sekitar 0,1 detik) setelah berjalan lewat tepi platform. Nama ini dari kartun Wile E. Coyote yang sempat "melayang" sebelum jatuh.
2. **Jump buffering**: jika pemain menekan lompat sedikit **sebelum** mendarat, lompatan tetap dijalankan begitu mendarat.
3. **Variable jump height**: menahan tombol lompat lebih lama menghasilkan lompatan lebih tinggi.

Ditambah akselerasi dan gesekan agar gerakan horizontal tidak kaku.

```gdscript
# player.gd
class_name Player
extends CharacterBody2D

@export_group("Gerak")
@export var speed: float = 180.0
@export var acceleration: float = 1200.0
@export var friction: float = 1400.0

@export_group("Lompat")
@export var jump_velocity: float = -380.0
@export var coyote_time: float = 0.1
@export var jump_buffer_time: float = 0.1
@export var jump_cut_multiplier: float = 0.5

var gravity: float = ProjectSettings.get_setting("physics/2d/default_gravity")

var _coyote_timer: float = 0.0
var _jump_buffer_timer: float = 0.0

func _physics_process(delta: float) -> void:
	_apply_gravity(delta)
	_update_timers(delta)
	_handle_jump()
	_handle_horizontal(delta)
	move_and_slide()

func _apply_gravity(delta: float) -> void:
	if not is_on_floor():
		velocity.y += gravity * delta

func _update_timers(delta: float) -> void:
	if is_on_floor():
		_coyote_timer = coyote_time
	else:
		_coyote_timer = maxf(_coyote_timer - delta, 0.0)

	if Input.is_action_just_pressed("jump"):
		_jump_buffer_timer = jump_buffer_time
	else:
		_jump_buffer_timer = maxf(_jump_buffer_timer - delta, 0.0)

func _handle_jump() -> void:
	if _jump_buffer_timer > 0.0 and _coyote_timer > 0.0:
		velocity.y = jump_velocity
		_jump_buffer_timer = 0.0
		_coyote_timer = 0.0

	# Lompatan pendek jika tombol dilepas lebih awal
	if Input.is_action_just_released("jump") and velocity.y < 0.0:
		velocity.y *= jump_cut_multiplier

func _handle_horizontal(delta: float) -> void:
	var direction := Input.get_axis("move_left", "move_right")
	if direction != 0.0:
		velocity.x = move_toward(velocity.x, direction * speed, acceleration * delta)
	else:
		velocity.x = move_toward(velocity.x, 0.0, friction * delta)
```

Penjelasan singkat:

- `move_toward(a, b, step)` menggeser `a` mendekati `b` sebesar paling banyak `step`. Ini cara sederhana membuat akselerasi dan gesekan.
- Nilai gravitasi diambil dari Project Settings agar konsisten dengan pengaturan fisika.
- Fungsi dipecah kecil-kecil agar mudah dibaca dan diubah.

Tips menyetel: ubah satu angka, jalankan, rasakan. Menyetel "game feel" memang soal mencoba berulang kali.

### 6.4 Top-Down

Untuk game dari sudut pandang atas, atur `motion_mode` pada `CharacterBody2D` menjadi **Floating** dan nol-kan gravitasi.

```gdscript
extends CharacterBody2D

@export var speed: float = 120.0

func _physics_process(_delta: float) -> void:
	var input_vector := Input.get_vector("move_left", "move_right", "move_up", "move_down")
	velocity = input_vector * speed
	move_and_slide()
```

`get_vector` sudah menormalkan arah diagonal sehingga gerak miring tidak lebih cepat.

### 6.5 Membalik Sprite

```gdscript
func _update_facing(direction: float) -> void:
	if direction != 0.0:
		$AnimatedSprite2D.flip_h = direction < 0.0
```

Jebakan: jika Anda menaruh hitbox serangan di sebelah kanan, ia tidak ikut terbalik saat `flip_h` diubah. Solusi umum: taruh sprite dan hitbox di bawah satu node pivot (`Node2D`), lalu balikkan pivot dengan `pivot.scale.x = -1`.

### 6.6 Gamepad

Karena Anda memakai Input Map, tambahkan saja event dari gamepad ke action yang sama (misalnya tombol bawah untuk `jump`, stik kiri untuk `move_*`). Atur **deadzone** pada action agar stik yang sedikit bergeser tidak menghasilkan gerakan.

### Latihan Bab 6

1. Implementasikan pemain platformer dengan coyote time, jump buffer, dan lompatan variabel.
2. Ubah angka `coyote_time` menjadi 0, 0,1, dan 0,2. Rasakan perbedaannya.
3. Tambahkan **dash** horizontal dengan cooldown 0,6 detik.

---

## Bab 7: State Machine

### 7.1 Masalah yang Diselesaikan

Karakter punya banyak keadaan: diam, lari, lompat, jatuh, menyerang, terkena damage, mati. Jika semuanya ditulis dengan `if` bertumpuk di satu fungsi, kode menjadi spaghetti. **State machine** (mesin keadaan) memastikan karakter berada di **tepat satu** keadaan pada satu waktu, dan setiap keadaan punya kodenya sendiri.

### 7.2 State Machine Berbasis Node

Setiap state adalah node anak dari `StateMachine`.

```gdscript
# state.gd
class_name State
extends Node

signal transition_requested(new_state_name: String)

func enter(_msg: Dictionary = {}) -> void:
	pass

func exit() -> void:
	pass

func update(_delta: float) -> void:
	pass

func physics_update(_delta: float) -> void:
	pass
```

```gdscript
# state_machine.gd
class_name StateMachine
extends Node

@export var initial_state: State

var current_state: State
var states: Dictionary = {}

func _ready() -> void:
	for child in get_children():
		if child is State:
			states[child.name.to_lower()] = child
			child.transition_requested.connect(_on_transition_requested)
	# Tunggu pemilik (owner) selesai menyiapkan diri
	await owner.ready
	if initial_state:
		current_state = initial_state
		current_state.enter()

func _process(delta: float) -> void:
	if current_state:
		current_state.update(delta)

func _physics_process(delta: float) -> void:
	if current_state:
		current_state.physics_update(delta)

func _on_transition_requested(new_state_name: String) -> void:
	var key := new_state_name.to_lower()
	if not states.has(key):
		push_warning("State tidak ditemukan: %s" % new_state_name)
		return
	if current_state:
		current_state.exit()
	current_state = states[key]
	current_state.enter()
```

Contoh state untuk pemain. State menerima referensi pemain lewat `owner`:

```gdscript
# player_idle.gd  (node bernama "Idle" di bawah StateMachine)
extends State

func enter(_msg: Dictionary = {}) -> void:
	var player := owner as Player
	player.get_node("AnimatedSprite2D").play("idle")

func physics_update(delta: float) -> void:
	var player := owner as Player
	player.apply_gravity(delta)
	player.apply_friction(delta)
	player.move_and_slide()

	if not player.is_on_floor():
		transition_requested.emit("Fall")
	elif Input.is_action_just_pressed("jump"):
		transition_requested.emit("Jump")
	elif Input.get_axis("move_left", "move_right") != 0.0:
		transition_requested.emit("Run")
	elif Input.is_action_just_pressed("attack"):
		transition_requested.emit("Attack")
```

Catatan desain: di pendekatan ini, fungsi bersama seperti `apply_gravity` ditaruh di skrip `Player`, sedangkan keputusan "kapan pindah state" ditaruh di masing-masing state.

### 7.3 Alternatif Sederhana: Enum + match

Untuk karakter dengan state sedikit (sekitar 3 sampai 5), `enum` dengan `match` sudah cukup dan lebih ringkas. Pindah ke state machine berbasis node ketika jumlah state dan kerumitannya membuat satu berkas skrip terasa penuh.

```gdscript
enum State { IDLE, RUN, JUMP, FALL, ATTACK }
var state: State = State.IDLE

func change_state(new_state: State) -> void:
	if state == new_state:
		return
	_exit_state(state)
	state = new_state
	_enter_state(state)
```

### 7.4 Buffer Input dan Kunci Aksi

Masalah umum: pemain menekan serang saat animasi serang sedang berjalan. Pilihan desain:

- Abaikan input (animasi tidak bisa dibatalkan, terasa "berat").
- Simpan input dan jalankan setelah animasi selesai (input buffer, terasa responsif).
- Izinkan pembatalan pada frame tertentu (cancel window, populer di game aksi cepat).

Putuskan berdasarkan karakter game Anda, lalu konsisten.

### Latihan Bab 7

1. Buat state machine pemain dengan state `Idle`, `Run`, `Jump`, `Fall`.
2. Tambahkan state `Attack` yang mengunci pergerakan horizontal selama 0,3 detik.
3. Tambahkan state `Hurt` yang mendorong pemain ke belakang (knockback) dan kebal sementara.

---

## Bab 8: Sistem Combat (Health, Hitbox, Hurtbox)

### 8.1 Konsep Tiga Komponen

|Komponen|Peran|Node|
|---|---|---|
|`HealthComponent`|Menyimpan dan mengubah nyawa|`Node`|
|`Hurtbox`|Area yang **bisa dilukai** (badan makhluk)|`Area2D`|
|`Hitbox`|Area yang **melukai** (senjata, ujung pedang, badan musuh)|`Area2D`|

Alurnya: `Hitbox` menyentuh `Hurtbox` yang tepat, `Hurtbox` memancarkan signal, pemilik menerjemahkannya menjadi pengurangan nyawa lewat `HealthComponent`.

### 8.2 Implementasi

```gdscript
# health_component.gd
class_name HealthComponent
extends Node

signal health_changed(current: int, maximum: int)
signal damaged(amount: int)
signal died

@export var max_health: int = 3

var current_health: int

func _ready() -> void:
	current_health = max_health

func take_damage(amount: int) -> void:
	if current_health <= 0:
		return
	current_health = maxi(current_health - amount, 0)
	damaged.emit(amount)
	health_changed.emit(current_health, max_health)
	if current_health == 0:
		died.emit()

func heal(amount: int) -> void:
	current_health = mini(current_health + amount, max_health)
	health_changed.emit(current_health, max_health)
```

```gdscript
# hurtbox.gd
class_name Hurtbox
extends Area2D

signal hit_received(damage: int, source_position: Vector2)

func receive_hit(damage: int, source_position: Vector2) -> void:
	hit_received.emit(damage, source_position)
```

```gdscript
# hitbox.gd
class_name Hitbox
extends Area2D

@export var damage: int = 1

func _ready() -> void:
	area_entered.connect(_on_area_entered)

func _on_area_entered(area: Area2D) -> void:
	if area is Hurtbox:
		area.receive_hit(damage, global_position)
```

Pasang di pemain:

```gdscript
# Di player.gd
@onready var health: HealthComponent = %HealthComponent
@onready var hurtbox: Hurtbox = %Hurtbox

func _ready() -> void:
	hurtbox.hit_received.connect(_on_hit_received)
	health.died.connect(_on_died)

func _on_hit_received(damage: int, source_position: Vector2) -> void:
	health.take_damage(damage)
	var knock_dir := signf(global_position.x - source_position.x)
	velocity = Vector2(knock_dir * 200.0, -150.0)
	# Pindah ke state Hurt di sini bila memakai state machine

func _on_died() -> void:
	Events.player_died.emit()
```

### 8.3 Mengatur Layer dan Mask

Dengan layer yang sudah bernama di Bab 2:

|Node|Layer|Mask|
|---|---|---|
|Hurtbox pemain|hurtbox_player|enemy_hitbox|
|Hitbox serangan pemain|player_hitbox|hurtbox_enemy|
|Hurtbox musuh|hurtbox_enemy|player_hitbox|
|Hitbox badan musuh|enemy_hitbox|hurtbox_player|

Dengan ini, serangan pemain tidak akan melukai pemain sendiri, dan musuh tidak saling melukai.

### 8.4 Mengaktifkan Hitbox Hanya Saat Serangan

Hitbox sebaiknya aktif hanya pada frame serangan. Caranya, di `AnimationPlayer` buat track properti untuk `Hitbox/CollisionShape2D:disabled`: nonaktif (`true`) di awal animasi, aktif (`false`) pada frame ayunan, lalu nonaktif lagi.

Jika Anda menggantinya lewat kode di dalam callback fisika, gunakan `set_deferred`:

```gdscript
$Hitbox/CollisionShape2D.set_deferred("disabled", false)
```

Jebakan: error "Can't change this state while flushing queries" muncul ketika Anda mengubah state fisika di tengah callback `body_entered` atau `area_entered`. `set_deferred` menunda perubahan ke akhir frame sehingga aman.

### 8.5 Invincibility Frames (I-Frames)

Setelah terkena serangan, beri pemain kekebalan sebentar agar tidak mati dalam satu detik oleh serangan beruntun.

```gdscript
var _invincible: bool = false

func _on_hit_received(damage: int, source_position: Vector2) -> void:
	if _invincible:
		return
	_invincible = true
	health.take_damage(damage)
	_blink(0.8)
	await get_tree().create_timer(0.8).timeout
	_invincible = false

func _blink(duration: float) -> void:
	var tween := create_tween().set_loops(int(duration / 0.1))
	tween.tween_property($AnimatedSprite2D, "modulate:a", 0.3, 0.05)
	tween.tween_property($AnimatedSprite2D, "modulate:a", 1.0, 0.05)
```

### Latihan Bab 8

1. Buat sistem Health, Hitbox, Hurtbox lengkap dan uji dengan satu musuh diam.
2. Tambahkan knockback dan i-frames.
3. Tambahkan objek dekorasi "pot tanah liat" yang pecah ketika diserang menggunakan komponen yang sama.

---

## Bab 9: Animasi

### 9.1 Dua Alat Utama

|Alat|Kegunaan|
|---|---|
|`AnimatedSprite2D`|Memutar urutan frame sprite (idle, lari). Sederhana dan cepat disiapkan.|
|`AnimationPlayer`|Menganimasikan **properti apa saja** (posisi, warna, hitbox aktif, suara) dan memanggil fungsi pada frame tertentu.|

Kombinasi yang umum untuk karakter: `AnimatedSprite2D` atau `Sprite2D` untuk gambar, `AnimationPlayer` untuk logika yang selaras dengan animasi (hitbox, suara langkah, efek).

### 9.2 AnimatedSprite2D dan SpriteFrames

1. Tambah node `AnimatedSprite2D`.
2. Di Inspector, buat resource `SpriteFrames` baru.
3. Di panel SpriteFrames, buat animasi (`idle`, `run`, `jump`, `fall`, `attack`) dan tambahkan frame dari sprite sheet.
4. Atur FPS dan centang `Loop` untuk animasi yang berulang.

```gdscript
@onready var sprite: AnimatedSprite2D = $AnimatedSprite2D

func _update_animation() -> void:
	if not is_on_floor():
		sprite.play("jump" if velocity.y < 0.0 else "fall")
	elif absf(velocity.x) > 5.0:
		sprite.play("run")
	else:
		sprite.play("idle")
```

### 9.3 Memanggil Fungsi dari Animasi

Di `AnimationPlayer`, tambahkan track **Call Method**. Misalnya, pada frame di mana kaki menyentuh tanah, panggil `play_footstep()`. Hasilnya, suara selaras dengan gambar tanpa Anda menghitung waktu secara manual.

### 9.4 Tween untuk Animasi Cepat Lewat Kode

Untuk efek singkat (berkedip, membesar, muncul), `Tween` jauh lebih praktis daripada membuat animasi di editor.

```gdscript
func pop_in() -> void:
	scale = Vector2.ZERO
	var tween := create_tween()
	tween.set_trans(Tween.TRANS_BACK).set_ease(Tween.EASE_OUT)
	tween.tween_property(self, "scale", Vector2.ONE, 0.25)
```

Tween dapat dirangkai (berurutan) atau diparalelkan dengan `tween.parallel()`.

### 9.5 AnimationTree (Opsional)

`AnimationTree` dengan `AnimationNodeStateMachine` berguna ketika animasi punya banyak transisi. Untuk game 2D indie, tahap pertama cukup dengan `AnimatedSprite2D` atau `AnimationPlayer` yang dipicu dari state machine Anda sendiri. Pelajari `AnimationTree` setelah merasa perlu.

### 9.6 Prinsip Animasi yang Murah tetapi Efektif

- **Squash and stretch**: sprite sedikit memipih saat mendarat dan memanjang saat melompat. Bisa dilakukan hanya dengan mengubah `scale` lewat Tween.
- **Anticipation**: sedikit gerakan "menarik ke belakang" sebelum menyerang, sehingga pemain bisa membaca serangan musuh.
- **Follow-through**: gerakan tidak berhenti mendadak.

### Latihan Bab 9

1. Buat animasi `idle`, `run`, `jump`, `fall` (boleh memakai kotak berwarna dahulu).
2. Tambahkan efek squash saat mendarat memakai Tween.
3. Gunakan track Call Method untuk memutar suara langkah.

---

## Bab 10: TileMapLayer dan Desain Level

### 10.1 TileSet dan TileMapLayer

Sejak Godot 4.3, level dibangun memakai **`TileMapLayer`**. Setiap layer visual adalah satu node `TileMapLayer`. Ini menggantikan node `TileMap` lama yang menampung banyak layer sekaligus.

Langkah dasar:

1. Impor gambar tileset (misalnya 16 x 16 piksel per tile).
2. Pada node `TileMapLayer`, buat resource `TileSet` baru dan atur `Tile Size`.
3. Buka panel TileSet, tambahkan gambar sebagai atlas.
4. Di panel TileMap, pilih tile dan gambar di level.

### 10.2 Layer pada TileSet

Di Inspector `TileSet`, Anda bisa menambahkan beberapa jenis layer:

|Layer pada TileSet|Fungsi|
|---|---|
|Physics Layers|Memberi bentuk tabrakan pada tile (dinding dan lantai).|
|Terrains|Auto-tiling: Godot memilih tile tepi dan sudut otomatis.|
|Navigation Layers|Area yang bisa dilalui AI.|
|Custom Data Layers|Data bebas per tile (misalnya `damage`, `is_ice`, `footstep_sound`).|
|Occlusion, Light|Bayangan dan cahaya 2D.|

Pada tab Physics di panel TileSet, gambar bentuk tabrakan untuk tiap tile padat. Pastikan layer tabrakannya adalah `world`.

### 10.3 Terrain (Auto-Tiling)

Dengan **Terrain**, Anda tidak perlu memilih tile sudut secara manual. Anda mendefinisikan aturan sekali, lalu menggambar "tanah" dan Godot memilih tile yang cocok. Ini mempercepat pembuatan level secara drastis.

### 10.4 Membaca Data Tile dari Kode

Misalnya, tile es membuat pemain licin. Buat Custom Data Layer bernama `surface` (tipe String), lalu:

```gdscript
@export var ground_layer: TileMapLayer

func get_surface_at(world_pos: Vector2) -> String:
	var cell := ground_layer.local_to_map(ground_layer.to_local(world_pos))
	var data := ground_layer.get_cell_tile_data(cell)
	if data == null:
		return ""
	return data.get_custom_data("surface")
```

Hasilnya dapat dipakai untuk mengubah gesekan atau suara langkah.

### 10.5 Prinsip Desain Level untuk Gameplay

Untuk game yang fokus gameplay, desain level adalah tempat gameplay "diajarkan".

1. **Ajarkan lewat situasi aman.** Sebelum menaruh jurang berbahaya, beri pemain kesempatan mencoba mekanik lompatan di tempat aman.
2. **Satu ide baru per area.** Perkenalkan, uji, variasikan, lalu gabungkan dengan ide lain.
3. **Tempatkan imbalan.** Jalur samping yang berisi item atau lore membuat eksplorasi terasa bermakna.
4. **Beri titik istirahat.** Setelah bagian sulit, beri ruang tenang (dan titik simpan).
5. **Gunakan cahaya, warna, dan bentuk** untuk menuntun mata pemain ke arah yang benar tanpa teks.

### 10.6 Mengelola Banyak Level

Simpan tiap level sebagai scene terpisah. Gunakan satu skrip dasar `Level` (dengan `class_name Level`) yang berisi hal umum seperti `Marker2D` untuk titik spawn dan batas kamera, sehingga `SceneChanger` dapat memperlakukan semua level secara seragam.

### Latihan Bab 10

1. Buat TileSet dengan collision dan satu terrain, lalu gambar satu level kecil.
2. Tambahkan Custom Data Layer `surface` dan ubah suara langkah berdasarkan tile yang diinjak.
3. Rancang tiga ruangan: ruang mengajarkan lompat, ruang menguji lompat, ruang menggabungkan lompat dengan musuh.

---

## Bab 11: Kamera dan Game Feel

### 11.1 Camera2D

Pasang `Camera2D` sebagai anak pemain (atau gerakkan lewat kode) dan atur:

- `position_smoothing_enabled`: kamera mengikuti dengan halus.
- `limit_left`, `limit_right`, `limit_top`, `limit_bottom`: batas dunia agar kamera tidak menampilkan area kosong.
- `drag_horizontal_enabled`: area mati (dead zone) tempat pemain boleh bergerak tanpa menggerakkan kamera.

### 11.2 Screen Shake

Teknik "trauma": goyangan dihitung dari nilai trauma yang meluruh, dan intensitasnya dikuadratkan agar terasa alami.

```gdscript
# camera_shake.gd (dipasang pada Camera2D)
extends Camera2D

@export var decay: float = 1.5
@export var max_offset: Vector2 = Vector2(8.0, 6.0)

var _trauma: float = 0.0

func add_trauma(amount: float) -> void:
	_trauma = minf(_trauma + amount, 1.0)

func _process(delta: float) -> void:
	if _trauma > 0.0:
		_trauma = maxf(_trauma - decay * delta, 0.0)
		var shake := _trauma * _trauma
		offset = Vector2(
			randf_range(-1.0, 1.0),
			randf_range(-1.0, 1.0)
		) * max_offset * shake
	else:
		offset = Vector2.ZERO
```

Gunakan lewat event bus, misalnya `Events.camera_shake_requested.emit(0.4)`, atau lewat group `"camera"`.

### 11.3 Hit Stop (Jeda Sesaat Saat Menghantam)

Membekukan game selama beberapa milidetik saat serangan mengenai sasaran membuat pukulan terasa berbobot.

```gdscript
# Pada autoload, mis. GameFeel
func hit_stop(duration: float = 0.06) -> void:
	Engine.time_scale = 0.05
	# Argumen ke-4 = true: timer mengabaikan time_scale
	await get_tree().create_timer(duration, true, false, true).timeout
	Engine.time_scale = 1.0
```

Jebakan: jika sesuatu memanggil `hit_stop` beberapa kali bersamaan, pastikan `time_scale` dikembalikan ke 1,0 dan jangan sampai macet di nilai kecil.

### 11.4 Daftar "Juice" Murah dan Efektif

"Juice" adalah umpan balik visual dan audio yang membuat tindakan terasa memuaskan. Beberapa yang murah:

|Teknik|Cara cepat|
|---|---|
|Kedip putih saat kena|Ubah `modulate` atau pakai shader sederhana sesaat.|
|Partikel debu saat mendarat|`GPUParticles2D` atau `CPUParticles2D` sekali tembak.|
|Variasi nada efek suara|Acak `pitch_scale` antara 0,9 dan 1,1.|
|Screen shake kecil|Lihat 11.2.|
|Hit stop|Lihat 11.3.|
|Angka damage melayang|`Label` dengan Tween naik dan memudar.|

### 11.5 Menyetel Rasa (Game Feel) Secara Disiplin

- Ubah **satu** variabel dalam satu waktu.
- Catat nilai yang terasa baik.
- Minta orang lain mencoba. Pemain baru merasakan hal yang sudah tidak Anda rasakan.
- Jangan menambah juice berlebihan: terlalu banyak guncangan dan kilatan melelahkan, bahkan bisa mengganggu pemain yang sensitif. Sediakan opsi untuk menguranginya di menu pengaturan.

### Latihan Bab 11

1. Pasang Camera2D dengan smoothing dan batas level.
2. Tambahkan screen shake ketika pemain terkena damage.
3. Tambahkan hit stop 0,06 detik ketika pedang mengenai musuh, dan opsi "kurangi efek layar" di pengaturan.

---

## Bab 12: Musuh dan AI Sederhana

### 12.1 AI itu Sebenarnya State Machine

AI musuh di game 2D indie hampir selalu state machine dengan beberapa keadaan: **Patrol**, **Chase**, **Attack**, **Hurt**, **Dead**. Gunakan pola dari Bab 7.

### 12.2 Patroli Platformer Sederhana

```gdscript
# slime.gd
class_name Slime
extends CharacterBody2D

@export var speed: float = 40.0

var direction: float = 1.0
var gravity: float = ProjectSettings.get_setting("physics/2d/default_gravity")

@onready var ground_check: RayCast2D = $GroundCheck
@onready var wall_check: RayCast2D = $WallCheck
@onready var sprite: AnimatedSprite2D = $AnimatedSprite2D

func _physics_process(delta: float) -> void:
	if not is_on_floor():
		velocity.y += gravity * delta

	# Balik arah jika ujung platform atau menabrak dinding
	if is_on_floor() and (not ground_check.is_colliding() or wall_check.is_colliding()):
		_flip()

	velocity.x = direction * speed
	move_and_slide()

func _flip() -> void:
	direction *= -1.0
	sprite.flip_h = direction < 0.0
	ground_check.position.x = absf(ground_check.position.x) * direction
	wall_check.target_position.x = absf(wall_check.target_position.x) * direction
```

`RayCast2D` adalah "sinar" tak terlihat. `GroundCheck` diarahkan ke bawah di depan kaki musuh, dan `WallCheck` diarahkan ke depan. Pastikan keduanya hanya mendeteksi layer `world`.

### 12.3 Mendeteksi Pemain

Gunakan `Area2D` besar sebagai "zona penglihatan":

```gdscript
@onready var vision: Area2D = $VisionArea
var target: Player = null

func _ready() -> void:
	vision.body_entered.connect(_on_vision_body_entered)
	vision.body_exited.connect(_on_vision_body_exited)

func _on_vision_body_entered(body: Node2D) -> void:
	if body is Player:
		target = body

func _on_vision_body_exited(body: Node2D) -> void:
	if body == target:
		target = null
```

Untuk "garis pandang" yang tidak tembus dinding, tambahkan `RayCast2D` dari musuh ke pemain dan periksa apakah sinar mengenai dinding lebih dulu.

### 12.4 Pathfinding dengan NavigationAgent2D

Untuk game top-down dengan labirin atau ruangan kompleks, gunakan sistem navigasi:

1. Tambah `NavigationRegion2D` ke level dan buat `NavigationPolygon` yang menutupi area berjalan. Pada TileSet, Anda bisa menggambar navigasi per tile lewat Navigation Layer.
2. Pada musuh tambahkan `NavigationAgent2D`.

```gdscript
extends CharacterBody2D

@export var speed: float = 70.0
@onready var nav: NavigationAgent2D = $NavigationAgent2D

func _ready() -> void:
	# Peta navigasi baru siap setelah satu frame fisika
	await get_tree().physics_frame

func set_target(world_position: Vector2) -> void:
	nav.target_position = world_position

func _physics_process(_delta: float) -> void:
	if nav.is_navigation_finished():
		velocity = Vector2.ZERO
	else:
		var next_point := nav.get_next_path_position()
		velocity = global_position.direction_to(next_point) * speed
	move_and_slide()
```

Perbarui `target_position` tidak setiap frame, tetapi dengan `Timer` (misalnya 0,2 detik sekali) untuk menghemat performa.

### 12.5 Prinsip Desain Musuh yang Adil

- **Telegraph** (isyarat): serangan harus punya tanda sebelum terjadi, misalnya sedikit membungkuk atau berkedip.
- **Konsisten**: musuh yang sama bereaksi dengan cara yang sama.
- **Dapat dipelajari**: pemain menang karena memahami pola, bukan karena refleks gila.
- **Variasi lewat data**: satu skrip musuh, beberapa varian lewat resource (Bab 13).

### Latihan Bab 12

1. Buat musuh yang berpatroli dan berbalik di tepi platform.
2. Tambahkan state Chase saat pemain memasuki zona penglihatan.
3. Tambahkan telegraph 0,4 detik sebelum musuh menyerang.

---

## Bab 13: Desain Berbasis Data dengan Resource

### 13.1 Apa itu Resource

**Resource** adalah wadah data yang bisa disimpan sebagai berkas (`.tres`) dan diedit di Inspector. Resource sangat cocok untuk data game: statistik musuh, informasi item, baris dialog, entri lore.

Manfaatnya: desainer (Anda sendiri) dapat membuat varian baru tanpa menulis kode, dan data terpisah dari logika.

### 13.2 Membuat Resource Sendiri

```gdscript
# data/enemy_data.gd
class_name EnemyData
extends Resource

@export var id: StringName
@export var display_name: String
@export var max_health: int = 3
@export var move_speed: float = 40.0
@export var contact_damage: int = 1
@export var sprite_frames: SpriteFrames
@export var drop_table: Array[ItemData] = []
```

Cara membuat berkas data: di panel FileSystem klik kanan, pilih **New Resource**, cari `EnemyData`, lalu simpan misalnya sebagai `res://data/enemies/slime_green.tres`. Duplikat untuk membuat `slime_red.tres` dengan angka berbeda.

Pemakaian:

```gdscript
# enemy.gd
extends CharacterBody2D

@export var data: EnemyData

func _ready() -> void:
	$HealthComponent.max_health = data.max_health
	$AnimatedSprite2D.sprite_frames = data.sprite_frames
```

### 13.3 Jebakan Besar: Resource Itu Dibagi

Semua node yang memakai berkas `.tres` yang sama **berbagi satu objek** yang sama di memori. Jika Anda mengubah `data.max_health` saat game berjalan (misalnya musuh terkena damage dan Anda mengurangi `data.max_health`), seluruh musuh sejenis ikut berubah.

Aturannya:

- Perlakukan resource data sebagai **hanya-baca (read-only)**.
- Simpan nilai yang berubah (nyawa saat ini) di node atau variabel instance.
- Jika terpaksa mengubah, panggil `data.duplicate()` untuk membuat salinan.

### 13.4 Resource untuk Item

```gdscript
# data/item_data.gd
class_name ItemData
extends Resource

enum Kind { CONSUMABLE, EQUIPMENT, KEY, LORE }

@export var id: StringName
@export var display_name: String
@export_multiline var description: String
@export var icon: Texture2D
@export var kind: Kind = Kind.CONSUMABLE
@export var max_stack: int = 1
@export var heal_amount: int = 0
```

Sistem inventori sederhana:

```gdscript
# inventory.gd
class_name Inventory
extends Node

signal changed

# id item -> jumlah
var _items: Dictionary[StringName, int] = {}

func add(item: ItemData, amount: int = 1) -> void:
	var current := _items.get(item.id, 0)
	_items[item.id] = mini(current + amount, item.max_stack)
	changed.emit()

func remove(item: ItemData, amount: int = 1) -> bool:
	var current := _items.get(item.id, 0)
	if current < amount:
		return false
	_items[item.id] = current - amount
	if _items[item.id] == 0:
		_items.erase(item.id)
	changed.emit()
	return true

func count(item: ItemData) -> int:
	return _items.get(item.id, 0)

func to_dict() -> Dictionary:
	return _items.duplicate()
```

Perhatikan: inventori menyimpan **id** item (bukan objek resource) agar mudah disimpan ke berkas save (Bab 20). Untuk mengubah id kembali menjadi `ItemData`, buat `ItemDatabase` yang memuat semua berkas di `res://data/items/` ke sebuah dictionary.

Catatan: jika Anda memakai Godot di bawah 4.4, ganti `Dictionary[StringName, int]` dengan `Dictionary` biasa.

### 13.5 Kapan Memakai Resource, JSON, atau Kode

|Cara|Cocok untuk|Kekurangan|
|---|---|---|
|Resource `.tres`|Data yang diedit di Inspector, memiliki referensi ke aset (gambar, suara)|Tidak mudah diedit di luar Godot|
|JSON|Teks panjang (dialog), data yang ingin diedit di editor teks atau spreadsheet|Tidak bisa merujuk aset langsung, harus lewat jalur teks|
|Konstanta di kode|Angka kecil yang jarang berubah|Perubahan memerlukan edit kode|

### Latihan Bab 13

1. Buat `EnemyData` dan dua varian musuh dari satu scene.
2. Buat `ItemData` untuk ramuan penyembuh dan hubungkan ke `Inventory`.
3. Buktikan jebakan resource bersama: ubah nilai pada resource saat berjalan dan amati efeknya, lalu perbaiki dengan `duplicate()`.

---

## Bab 14: Spawning, Proyektil, dan Pickup

### 14.1 Membuat Objek Saat Game Berjalan

```gdscript
const BULLET: PackedScene = preload("res://entities/projectiles/bullet.tscn")

func shoot(direction: Vector2) -> void:
	var bullet := BULLET.instantiate() as Bullet
	bullet.global_position = $Muzzle.global_position
	bullet.direction = direction
	# Tambahkan ke level, bukan ke pemain, agar peluru tidak ikut bergerak bersama pemain
	get_tree().current_scene.add_child(bullet)
```

Aturan penting: **atur properti sebelum atau sesudah `add_child`** dengan sadar. `global_position` hanya bermakna setelah node berada di tree. Untuk aman, tambahkan dulu, baru atur posisi, atau gunakan `position` untuk node yang belum di tree.

### 14.2 Peluru

```gdscript
# bullet.gd
class_name Bullet
extends Area2D

@export var speed: float = 300.0
@export var lifetime: float = 2.0
var direction: Vector2 = Vector2.RIGHT

func _ready() -> void:
	body_entered.connect(_on_body_entered)
	await get_tree().create_timer(lifetime).timeout
	queue_free()

func _physics_process(delta: float) -> void:
	position += direction * speed * delta

func _on_body_entered(_body: Node2D) -> void:
	queue_free()
```

Hapus objek dengan `queue_free()` (menghapus di akhir frame, aman). Hindari `free()` kecuali Anda paham risikonya.

### 14.3 Object Pooling (Opsional)

Jika game menembakkan ratusan objek (peluru, partikel), membuat dan menghapus terus-menerus bisa memberatkan. **Object pool** menyimpan objek untuk dipakai ulang. Untuk sebagian besar game indie 2D yang sederhana, ini tidak perlu di tahap awal. Ukur dahulu dengan Profiler (Bab 23), baru optimasi.

### 14.4 Pickup

```gdscript
# pickup.gd
class_name Pickup
extends Area2D

@export var item: ItemData
@export var amount: int = 1

func _ready() -> void:
	body_entered.connect(_on_body_entered)

func _on_body_entered(body: Node2D) -> void:
	if body is Player:
		body.inventory.add(item, amount)
		Events.item_picked_up.emit(item)
		set_deferred("monitoring", false)
		queue_free()
```

Pastikan `Events` memiliki signal `item_picked_up(item: ItemData)`.

### 14.4a Objek yang Bisa Berinteraksi

Untuk NPC, peti, pintu: gunakan `Area2D` "zona interaksi", tampilkan petunjuk tombol saat pemain berada di dalam zona, lalu jalankan aksi saat `interact` ditekan.

```gdscript
# interactable.gd
class_name Interactable
extends Area2D

signal interacted(by: Node)

@export var prompt_text: String = "INTERACT"

func interact(by: Node) -> void:
	interacted.emit(by)
```

Pemain menyimpan daftar `Interactable` yang sedang berada di dekatnya dan memanggil `interact()` pada yang terdekat.

### Latihan Bab 14

1. Buat pemain yang bisa menembak proyektil dan peluru yang hilang saat menabrak dinding.
2. Buat pickup yang menambahkan item ke inventori.
3. Buat peti yang bisa dibuka dengan tombol `interact`.

---

# Bagian 3: Cerita dan Lore (Tanpa Voice Actor)

## Bab 15: Cerita yang Melayani Gameplay

### 15.1 Prinsip

Dalam game yang berfokus gameplay, cerita bukan penghalang antara pemain dan aksi. Cerita adalah **alasan**, **konteks**, dan **hadiah**.

Panduan praktis:

1. **Satu kalimat premis.** Contoh: "Seorang penjaga lentera harus menyalakan kembali lima mercusuar hutan sebelum kegelapan menelan desa." Jika premis tidak muat dalam satu kalimat, kemungkinan terlalu rumit untuk game indie.
2. **Cerita mengikuti mekanik.** Jika mekanik inti Anda adalah cahaya dan bayangan, tema cerita (kegelapan, harapan) sebaiknya selaras.
3. **Tunjukkan, jangan jelaskan.** Sebuah desa kosong dengan piring berantakan menyampaikan lebih banyak daripada tiga paragraf teks.
4. **Teks pendek.** Pemain game aksi ingin kembali bermain. Satu kotak dialog sebaiknya hanya beberapa kalimat.
5. **Opsional bagi yang penasaran.** Cerita utama pendek dan jelas, lore mendalam disembunyikan untuk pemain yang mencari.

### 15.2 Struktur Berlapis

Susun informasi cerita dalam lapisan:

|Lapisan|Siapa yang melihat|Contoh|
|---|---|---|
|Lapisan 1: alur utama|Semua pemain|Dialog dan cutscene wajib.|
|Lapisan 2: konteks dunia|Pemain yang menjelajah|NPC opsional, papan petunjuk, deskripsi item.|
|Lapisan 3: lore dalam|Pemain yang mengumpulkan|Codex, catatan tersembunyi, relief dinding.|

Dengan begini, pemain yang hanya ingin bermain tidak terbebani, dan pemain yang suka cerita mendapat banyak hal.

### 15.3 Tanpa Voice Actor: Keuntungan dan Cara Mengimbangi

Keuntungan: biaya dan waktu lebih kecil, mudah merevisi naskah, mudah lokalisasi.

Kekurangan: emosi tidak terbawa suara. Cara mengimbanginya:

|Teknik|Penjelasan|
|---|---|
|Potret karakter dengan ekspresi|Beberapa varian wajah (netral, senang, sedih, marah) sudah banyak menyampaikan emosi.|
|Bunyi "blip" per huruf|Suara pendek saat teks muncul, dengan nada berbeda tiap karakter (ciri khas banyak game).|
|Efek teks|Bergetar saat takut, besar saat berteriak, melambat saat ragu.|
|Musik dan tema per karakter|Motif musik pendek yang berulang.|
|Animasi kecil|Anggukan, gemetar, menunduk.|
|Gaya tulis khas|Setiap karakter punya cara bicara berbeda (panjang-pendek kalimat, kosakata).|

### 15.4 Alat Bantu Naskah

Tulis naskah di editor teks atau spreadsheet dahulu, bukan langsung di Godot. Beri setiap kalimat sebuah **kunci** (misalnya `NPC_ELDER_001`) agar mudah dilokalisasi (Bab 19).

### Latihan Bab 15

1. Tulis premis game Anda dalam satu kalimat.
2. Pisahkan isi cerita ke tiga lapisan seperti tabel di atas.
3. Tulis dialog pembuka untuk satu NPC dengan maksimal empat kotak teks.

---

## Bab 16: Sistem Dialog

### 16.1 Kebutuhan Minimal

Sistem dialog untuk game indie yang fokus gameplay sebaiknya punya:

- Kotak teks dengan nama pembicara dan potret.
- Efek mesin ketik (typewriter) yang bisa dilewati.
- Pilihan jawaban (opsional).
- Kondisi sederhana (misalnya "jika pemain sudah punya kunci, tampilkan baris lain").
- Terhubung dengan `GameState` (flag cerita).

Anda bisa membangunnya sendiri (cukup mudah) atau memakai add-on dari komunitas. Beberapa yang populer dan diperbarui oleh komunitas adalah **Dialogue Manager** dan **Dialogic**. Selalu periksa halaman add-on untuk memastikan kompatibel dengan versi Godot Anda. Untuk belajar, membangun versi sendiri yang sederhana sangat bermanfaat.

### 16.2 Model Data Dialog dengan Resource

```gdscript
# data/dialogue_choice.gd
class_name DialogueChoice
extends Resource

@export var text_key: String
@export var set_flag: String          # flag yang diaktifkan jika dipilih
@export var next_sequence: DialogueSequence
```

```gdscript
# data/dialogue_line.gd
class_name DialogueLine
extends Resource

@export var speaker_key: String       # kunci terjemahan nama pembicara
@export var text_key: String          # kunci terjemahan teks
@export var portrait: Texture2D
@export var required_flag: String     # kosong = selalu tampil
@export var choices: Array[DialogueChoice] = []
```

```gdscript
# data/dialogue_sequence.gd
class_name DialogueSequence
extends Resource

@export var lines: Array[DialogueLine] = []
```

Dengan ini, Anda dapat membuat `elder_intro.tres` langsung di Inspector tanpa kode.

Catatan: jika Anda lebih nyaman menulis dialog dalam berkas teks atau JSON, struktur datanya sama; hanya cara memuatnya yang berbeda.

### 16.3 Kotak Dialog dengan Efek Mesin Ketik

Susunan scene `DialogueBox` (`Control`, disimpan di `CanvasLayer`):

```
DialogueBox (Control)
  Panel
    MarginContainer
      HBoxContainer
        Portrait (TextureRect)
        VBoxContainer
          NameLabel (Label, unique name)
          TextLabel (RichTextLabel, unique name, bbcode_enabled)
          ContinueIcon (TextureRect, unique name)
```

```gdscript
# dialogue_box.gd
class_name DialogueBox
extends Control

signal line_finished
signal advance_requested

@export var chars_per_second: float = 40.0

@onready var name_label: Label = %NameLabel
@onready var text_label: RichTextLabel = %TextLabel
@onready var portrait: TextureRect = %Portrait
@onready var continue_icon: Control = %ContinueIcon
@onready var blip: AudioStreamPlayer = %BlipPlayer

var _tween: Tween
var _is_typing: bool = false

func show_line(speaker: String, text: String, portrait_tex: Texture2D) -> void:
	name_label.text = speaker
	portrait.texture = portrait_tex
	portrait.visible = portrait_tex != null
	continue_icon.hide()

	text_label.text = text            # mendukung BBCode, mis. [shake]
	text_label.visible_ratio = 0.0
	_is_typing = true

	var total := text_label.get_total_character_count()
	var duration := float(total) / chars_per_second

	if _tween:
		_tween.kill()
	_tween = create_tween()
	_tween.tween_property(text_label, "visible_ratio", 1.0, duration)
	_tween.finished.connect(_finish_typing)

func _finish_typing() -> void:
	_is_typing = false
	continue_icon.show()
	line_finished.emit()

func _unhandled_input(event: InputEvent) -> void:
	if not visible:
		return
	if event.is_action_pressed("interact") or event.is_action_pressed("ui_accept"):
		get_viewport().set_input_as_handled()
		if _is_typing:
			# Lewati efek mesin ketik
			if _tween:
				_tween.kill()
			text_label.visible_ratio = 1.0
			_finish_typing()
		else:
			advance_requested.emit()
```

Catatan teknis:

- Memakai `visible_ratio` pada `RichTextLabel` lebih aman daripada memotong string, karena kode BBCode (misalnya `[b]`) tidak ikut tertampil setengah-setengah.
- `Tween.kill()` tidak memancarkan signal `finished`, jadi kita memanggil `_finish_typing()` sendiri.

Blip per huruf (opsional): hubungkan ke perubahan jumlah karakter yang terlihat, lalu putar `AudioStreamPlayer` dengan `pitch_scale` yang diacak sedikit tiap beberapa huruf. Cukup mainkan blip pada setiap huruf ke-2 atau ke-3 agar tidak terdengar seperti senapan mesin.

### 16.4 Pengendali Dialog (Dialogue Runner)

Sebuah autoload yang menjalankan urutan baris dan pilihan:

```gdscript
# autoload/dialogue_manager.gd  (autoload "DialogueRunner")
extends Node

signal dialogue_started
signal dialogue_ended

var box: DialogueBox
var is_active: bool = false

func play(sequence: DialogueSequence) -> void:
	if is_active or box == null:
		return
	is_active = true
	dialogue_started.emit()
	get_tree().paused = false    # atur sesuai desain Anda
	box.show()

	var current := sequence
	while current != null:
		var next_sequence: DialogueSequence = null
		for line in current.lines:
			# Lewati baris yang kondisinya belum terpenuhi
			if line.required_flag != "" and not GameState.has_flag(line.required_flag):
				continue

			box.show_line(tr(line.speaker_key), tr(line.text_key), line.portrait)
			await box.advance_requested

			if line.choices.size() > 0:
				var chosen: DialogueChoice = await _ask_choice(line.choices)
				if chosen.set_flag != "":
					GameState.set_flag(chosen.set_flag, true)
				next_sequence = chosen.next_sequence
				break
		current = next_sequence

	box.hide()
	is_active = false
	dialogue_ended.emit()

func _ask_choice(choices: Array[DialogueChoice]) -> DialogueChoice:
	# Tampilkan tombol pilihan, tunggu salah satunya dipencet.
	# Implementasi UI diserahkan ke Anda (latihan).
	return choices[0]
```

Pada tahap pertama, `_ask_choice` boleh dikembalikan ke pilihan pertama dahulu, lalu Anda lengkapi dengan UI tombol di latihan.

Saat dialog aktif, hentikan kontrol pemain. Cara termudah: pemain memeriksa `DialogueRunner.is_active` dan mengabaikan input jika benar.

```gdscript
# Di player.gd
func _physics_process(delta: float) -> void:
	if DialogueRunner.is_active:
		velocity.x = move_toward(velocity.x, 0.0, friction * delta)
		_apply_gravity(delta)
		move_and_slide()
		return
	# ... logika normal
```

### 16.5 Flag Cerita (GameState)

```gdscript
# autoload/game_state.gd  (autoload "GameState")
extends Node

var flags: Dictionary[String, bool] = {}

func set_flag(flag_name: String, value: bool = true) -> void:
	flags[flag_name] = value
	Events.flag_changed.emit(flag_name, value)

func has_flag(flag_name: String) -> bool:
	return flags.get(flag_name, false)

func to_dict() -> Dictionary:
	return {"flags": flags.duplicate()}

func from_dict(data: Dictionary) -> void:
	flags.clear()
	for key in data.get("flags", {}):
		flags[key] = bool(data["flags"][key])
```

Contoh pemakaian: pintu terkunci memeriksa `GameState.has_flag("has_rusty_key")`. NPC mengganti dialog setelah `GameState.has_flag("lighthouse_1_lit")`.

### 16.6 Praktik Baik Menulis Dialog

- Maksimal 2 sampai 3 baris tampilan per kotak.
- Hindari eksposisi panjang ("Seperti yang kau tahu, Bob...").
- Beri NPC fungsi gameplay: petunjuk, toko, hadiah, bukan sekadar penjelasan.
- Jangan paksa dialog panjang tepat sebelum bos atau area sulit.
- Selalu izinkan melewati (skip) teks yang sudah pernah dibaca.

### Latihan Bab 16

1. Bangun `DialogueBox` dengan mesin ketik dan tombol lewati.
2. Buat `DialogueSequence` untuk satu NPC dengan satu baris bersyarat flag.
3. Lengkapi `_ask_choice` dengan dua tombol pilihan yang mendukung gamepad (`grab_focus`).

---

## Bab 17: Lore, Codex, dan Penceritaan Lewat Lingkungan

### 17.1 Lore sebagai Hadiah Eksplorasi

Lore terbaik di game gameplay-first adalah lore yang **ditemukan**, bukan dipaksakan. Beberapa sumber lore yang murah dan efektif:

|Sumber|Contoh|
|---|---|
|Deskripsi item|"Cincin Penjaga. Bagian dalamnya terukir nama yang sudah memudar."|
|Catatan dan surat|Kertas di meja yang menceritakan nasib penghuni sebelumnya.|
|Relief dan grafiti|Gambar di dinding dengan sedikit teks.|
|Desain visual|Reruntuhan, patung, warna area yang menyiratkan sejarah.|
|NPC opsional|Karakter yang menceritakan potongan sejarah jika diajak bicara.|
|Nama tempat|"Jembatan Terakhir", "Sumur Tanpa Dasar". Nama saja sudah bercerita.|

### 17.2 Resource Entri Lore

```gdscript
# data/lore_entry.gd
class_name LoreEntry
extends Resource

@export var id: StringName
@export var title_key: String
@export_multiline var body_key: String
@export var category: StringName = &"world"      # world, people, creatures, ...
@export var image: Texture2D
```

### 17.3 Manajer Codex

```gdscript
# autoload/codex.gd  (autoload "Codex")
extends Node

signal entry_unlocked(entry: LoreEntry)

var _all_entries: Dictionary[StringName, LoreEntry] = {}
var _unlocked: Array[StringName] = []

func _ready() -> void:
	_load_entries("res://data/lore/")

func _load_entries(dir_path: String) -> void:
	var dir := DirAccess.open(dir_path)
	if dir == null:
		push_warning("Folder lore tidak ditemukan: %s" % dir_path)
		return
	for file_name in dir.get_files():
		# Di hasil export, berkas resource bisa berakhiran .remap
		var clean := file_name.trim_suffix(".remap")
		if clean.ends_with(".tres"):
			var entry := load(dir_path + clean) as LoreEntry
			if entry:
				_all_entries[entry.id] = entry

func unlock(entry_id: StringName) -> void:
	if entry_id in _unlocked or not _all_entries.has(entry_id):
		return
	_unlocked.append(entry_id)
	entry_unlocked.emit(_all_entries[entry_id])
	Events.lore_unlocked.emit(entry_id)

func is_unlocked(entry_id: StringName) -> bool:
	return entry_id in _unlocked

func get_unlocked_entries() -> Array[LoreEntry]:
	var result: Array[LoreEntry] = []
	for id in _unlocked:
		result.append(_all_entries[id])
	return result

func to_dict() -> Dictionary:
	return {"unlocked": _unlocked.map(func(id): return String(id))}

func from_dict(data: Dictionary) -> void:
	_unlocked.clear()
	for id in data.get("unlocked", []):
		_unlocked.append(StringName(id))
```

Perhatikan detail penting tentang **export**: pada hasil export, berkas `.tres` bisa ditampilkan dengan akhiran `.remap` saat Anda membaca folder lewat `DirAccess`. Itu sebabnya ada `trim_suffix(".remap")`. Jika folder pemindaian banyak dan Anda ingin cara yang lebih aman, daftarkan entri lore secara eksplisit dalam satu resource daftar (`LoreIndex`) dengan `@export var entries: Array[LoreEntry]`.

### 17.4 Pemicu Lore di Dunia

```gdscript
# lore_pickup.gd
extends Interactable

@export var entry_id: StringName

func _ready() -> void:
	interacted.connect(_on_interacted)

func _on_interacted(_by: Node) -> void:
	Codex.unlock(entry_id)
```

Beri umpan balik saat lore terbuka, misalnya ikon kecil "Catatan baru" di sudut layar, supaya pemain tahu ada hal yang bisa dibaca nanti, tanpa menghentikan permainan.

### 17.5 Penceritaan Lewat Lingkungan: Daftar Periksa

- Apakah ada sesuatu di ruangan ini yang menunjukkan siapa yang pernah di sini?
- Apakah warna dan pencahayaan sesuai dengan suasana (sepi, hangat, mengancam)?
- Apakah musuh di area ini masuk akal secara cerita?
- Apakah ada satu detail "kecil tapi aneh" yang membuat pemain penasaran?

### Latihan Bab 17

1. Buat tiga `LoreEntry` (`.tres`) dan Codex yang membukanya.
2. Buat layar Codex sederhana (daftar di kiri, isi di kanan) yang hanya menampilkan entri terbuka.
3. Tulis lima deskripsi item yang masing-masing mengisyaratkan satu fakta tentang dunia, tanpa eksposisi panjang.

---

## Bab 18: Cutscene Tanpa Suara Manusia

### 18.1 Prinsip

Cutscene pada game gameplay-first sebaiknya **pendek dan bisa dilewati**. Karena Anda tidak memakai voice actor, cutscene mengandalkan gambar, animasi, musik, efek suara, dan teks.

### 18.2 Dua Pendekatan

|Pendekatan|Cara|Kapan|
|---|---|---|
|Berbasis AnimationPlayer|Satu `AnimationPlayer` menjalankan gerakan karakter, kamera, suara, dan memanggil dialog lewat track Call Method|Cutscene dengan banyak elemen yang harus selaras waktu|
|Berbasis skrip (coroutine)|Fungsi dengan `await` yang menjalankan langkah berurutan|Cutscene yang bergantung kondisi atau flag|

Contoh berbasis skrip:

```gdscript
# cutscenes/intro_cutscene.gd
extends Node

@export var intro_dialogue: DialogueSequence

func play() -> void:
	var player := get_tree().get_first_node_in_group("player") as Player
	player.set_input_enabled(false)

	await SceneChanger.fade_out()
	$Camera2D.make_current()
	await SceneChanger.fade_in()

	var tween := create_tween()
	tween.tween_property($Camera2D, "position", Vector2(400, 120), 2.0)
	await tween.finished

	DialogueRunner.play(intro_dialogue)
	await DialogueRunner.dialogue_ended

	player.set_input_enabled(true)
	player.get_node("Camera2D").make_current()
```

### 18.3 Dapat Dilewati dan Tidak Mengunci Pemain

- Sediakan tombol lewati (tahan beberapa detik agar tidak terpencet tidak sengaja).
- Cutscene yang diulang setelah pemain mati sangat menyebalkan. Simpan flag setelah cutscene diputar agar tidak muncul lagi.
- Hindari cutscene tepat sebelum bagian sulit.

### 18.4 Menyampaikan Emosi Tanpa Suara

- Gunakan **jeda**: layar diam sebelum kalimat penting.
- Gunakan **musik yang berhenti** pada momen dramatis.
- Gunakan **kamera**: zoom pelan ke wajah, atau menjauh untuk menunjukkan kesendirian.
- Gunakan **efek suara lingkungan** (angin, tetesan air) sebagai pengganti suara manusia.

### Latihan Bab 18

1. Buat cutscene intro 20 detik: kamera bergerak, satu kotak dialog, kembali ke pemain.
2. Tambahkan flag `intro_seen` agar cutscene tidak diputar ulang.
3. Tambahkan fitur "tahan tombol untuk melewati".

---

## Bab 19: Lokalisasi (Multi-Bahasa)

### 19.1 Mengapa Lokalisasi Penting untuk Game Offline Indie

Game tanpa voice actor sangat mudah dilokalisasi, karena yang diterjemahkan hanya teks. Mendukung bahasa Inggris plus beberapa bahasa lain sering menambah jangkauan pemain secara signifikan. Mendukung Bahasa Indonesia juga menjangkau komunitas lokal.

### 19.2 Cara Kerja di Godot

Godot memiliki sistem terjemahan bawaan. Anda menulis **kunci**, dan Godot menggantinya dengan teks sesuai bahasa aktif.

1. Siapkan berkas CSV (bisa dibuat dengan spreadsheet):

```
keys,en,id
UI_START,Start,Mulai
UI_SETTINGS,Settings,Pengaturan
NPC_ELDER_001,"The lighthouse has gone dark.","Mercusuar itu telah padam."
```

2. Simpan sebagai `localization/translations.csv`. Godot akan mengimpornya menjadi berkas `.translation` untuk setiap bahasa.
3. Daftarkan di **Project Settings > Localization > Translations**.
4. Pakai di kode atau UI:

```gdscript
label.text = tr("UI_START")
```

Node `Label` dan `Button` dapat menerjemahkan teksnya otomatis jika teksnya berisi kunci (fitur "auto translate").

5. Ganti bahasa saat game berjalan:

```gdscript
TranslationServer.set_locale("id")
```

Pastikan pilihan bahasa disimpan di pengaturan pemain (Bab 21).

### 19.3 Tips Lokalisasi

- Jangan menyambung kalimat dari potongan (`"Kamu menemukan " + item + "!"`). Urutan kata berbeda tiap bahasa. Gunakan placeholder: `"FOUND_ITEM": "Kamu menemukan %s!"` lalu `tr("FOUND_ITEM") % item_name`.
- Beri ruang ekstra pada UI. Teks bahasa tertentu bisa 30 persen lebih panjang.
- Pilih font yang mendukung semua aksara bahasa yang Anda targetkan. Bahasa seperti Jepang, Mandarin, atau Korea memerlukan font khusus.
- Simpan kunci teks (bukan teks) di resource dan save file agar tidak bergantung bahasa.
- Sediakan konteks untuk penerjemah (kolom komentar di CSV).

### Latihan Bab 19

1. Buat CSV dengan tiga kunci untuk bahasa Inggris dan Indonesia.
2. Buat tombol pengganti bahasa di menu dan simpan pilihannya.
3. Ubah satu kalimat bergabung (`+`) menjadi placeholder `%s`.

---

# Bagian 4: Game Offline

## Bab 20: Sistem Save dan Load

### 20.1 Prinsip Dasar

Karena game Anda offline, semua data tersimpan di komputer pemain. Godot menyediakan jalur khusus: **`user://`**.

- `res://` adalah folder proyek Anda. Setelah di-export, bagian ini **hanya-baca**.
- `user://` adalah folder data pengguna yang **bisa ditulis**. Lokasi fisiknya berbeda tiap sistem operasi, dan Godot mengurusnya. Anda dapat membukanya dari editor lewat **Project > Open User Data Folder**.

Selalu simpan data pemain (save, pengaturan) di `user://`.

### 20.2 Tiga Cara Menyimpan

|Cara|Kelebihan|Kekurangan|Rekomendasi|
|---|---|---|---|
|JSON|Terbaca manusia, mudah di-debug, aman|Tidak mendukung tipe Godot (Vector2) langsung|Pilihan utama|
|`ConfigFile`|Format INI, mudah|Kurang cocok untuk data bersarang kompleks|Pengaturan pemain|
|`Resource` + `ResourceSaver`|Bisa menyimpan tipe Godot apa adanya|Memuat resource dari sumber tak tepercaya berisiko (bisa mengandung skrip)|Hindari untuk save pemain|
|`FileAccess.store_var`|Cepat, mendukung banyak tipe|Format biner, sulit di-debug|Opsional|

Peringatan keamanan: memuat berkas `.tres` atau `.res` dari `user://` bisa mengeksekusi skrip yang tertanam di dalamnya. Jika pemain berbagi berkas save di internet, hal itu berisiko. Itu alasan JSON dianjurkan untuk save game.

### 20.3 Menulis dan Membaca JSON

```gdscript
# autoload/save_manager.gd  (autoload "SaveManager")
extends Node

const SAVE_PATH_TEMPLATE: String = "user://save_slot_%d.json"
const SAVE_VERSION: int = 2

func save_game(slot: int) -> bool:
	var data: Dictionary = {
		"version": SAVE_VERSION,
		"saved_at": Time.get_datetime_string_from_system(),
		"game_state": GameState.to_dict(),
		"codex": Codex.to_dict(),
		"player": _collect_player_data(),
	}
	return _write_json(SAVE_PATH_TEMPLATE % slot, data)

func load_game(slot: int) -> bool:
	var path := SAVE_PATH_TEMPLATE % slot
	var data := _read_json(path)
	if data.is_empty():
		return false
	data = _migrate(data)
	GameState.from_dict(data.get("game_state", {}))
	Codex.from_dict(data.get("codex", {}))
	_apply_player_data(data.get("player", {}))
	return true

func has_save(slot: int) -> bool:
	return FileAccess.file_exists(SAVE_PATH_TEMPLATE % slot)

func delete_save(slot: int) -> void:
	var path := SAVE_PATH_TEMPLATE % slot
	if FileAccess.file_exists(path):
		DirAccess.remove_absolute(path)

# --- Penulisan aman (tulis ke berkas sementara, lalu ganti) ---
func _write_json(path: String, data: Dictionary) -> bool:
	var tmp_path := path + ".tmp"
	var file := FileAccess.open(tmp_path, FileAccess.WRITE)
	if file == null:
		push_error("Gagal menulis save: %s" % error_string(FileAccess.get_open_error()))
		return false
	file.store_string(JSON.stringify(data, "\t"))
	file.close()
	var err := DirAccess.rename_absolute(tmp_path, path)
	if err != OK:
		push_error("Gagal mengganti berkas save: %s" % error_string(err))
		return false
	return true

func _read_json(path: String) -> Dictionary:
	if not FileAccess.file_exists(path):
		return {}
	var file := FileAccess.open(path, FileAccess.READ)
	if file == null:
		return {}
	var parsed: Variant = JSON.parse_string(file.get_as_text())
	if parsed is Dictionary:
		return parsed
	push_warning("Berkas save rusak: %s" % path)
	return {}
```

Mengapa menulis ke berkas sementara dulu? Jika game crash atau listrik padam di tengah penulisan, berkas save lama tetap utuh. Menimpa langsung berkas lama berisiko meninggalkan save setengah jadi dan merusak progres pemain.

### 20.4 Perangkap JSON yang Sering Terjadi

1. **Angka menjadi float.** Setelah dibaca, semua angka dari JSON berupa `float`. Konversi: `int(data["coins"])`.
2. **Vector2 tidak bisa langsung disimpan.** Simpan sebagai array `[x, y]` dan rakit ulang:

```gdscript
# Menyimpan
"position": [player.global_position.x, player.global_position.y]

# Memuat
var pos_array: Array = data["position"]
player.global_position = Vector2(pos_array[0], pos_array[1])
```

3. **Kunci Dictionary menjadi String.** Kunci `StringName` atau angka diubah menjadi String saat disimpan.
4. **Data yang hilang.** Selalu pakai `data.get("kunci", nilai_default)` agar save lama tidak membuat game crash.

### 20.5 Versi Save dan Migrasi

Saat Anda menambah fitur baru, format save berubah. Sertakan `version` dan buat fungsi migrasi agar save lama tetap bisa dimuat.

```gdscript
func _migrate(data: Dictionary) -> Dictionary:
	var version := int(data.get("version", 1))

	if version < 2:
		# Versi 2 menambahkan "codex". Isi default untuk save lama.
		if not data.has("codex"):
			data["codex"] = {"unlocked": []}
		version = 2

	# if version < 3: ... (tambahkan di masa depan)

	data["version"] = version
	return data
```

### 20.6 Menyimpan Objek Dunia (Pola Group "persist")

Untuk objek dunia yang perlu diingat (peti sudah dibuka, pintu sudah terbuka, musuh bos sudah dikalahkan), ada dua pendekatan:

1. **Flag global** di `GameState` (paling sederhana, direkomendasikan): `chest_forest_01_opened = true`. Objek memeriksa flag saat `_ready()` dan menyesuaikan dirinya.
2. **Group "persist"**: setiap objek dalam group memiliki fungsi `save_data()` dan `load_data()`.

Pendekatan flag lebih mudah dikelola. Contoh:

```gdscript
# chest.gd
extends Interactable

@export var chest_id: String
@export var item: ItemData

var _opened: bool = false

func _ready() -> void:
	interacted.connect(_on_interacted)
	if GameState.has_flag("chest_" + chest_id):
		_set_opened_visual()

func _on_interacted(by: Node) -> void:
	if GameState.has_flag("chest_" + chest_id):
		return
	GameState.set_flag("chest_" + chest_id, true)
	by.inventory.add(item)
	_set_opened_visual()

func _set_opened_visual() -> void:
	$AnimatedSprite2D.play("opened")
```

### 20.7 Autosave dan Checkpoint

- Autosave pada titik wajar: masuk area baru, mengalahkan bos, menyalakan titik istirahat.
- Beri indikator kecil bahwa game sedang menyimpan (ikon berputar singkat). Jangan simpan di tengah aksi intens.
- Gunakan beberapa slot dan simpan satu cadangan (misalnya `save_slot_1.json.bak`).
- Jangan menyimpan tepat saat pemain sekarat atau berada di udara dekat jurang.

### 20.8 Menguji Save

- Uji muat save yang dibuat versi lama game Anda.
- Hapus sebagian kunci dari berkas JSON dan pastikan game tidak crash.
- Uji menyimpan lalu langsung menutup paksa game.
- Uji di komputer lain (hasil export), bukan hanya di editor.

### Latihan Bab 20

1. Buat `SaveManager` yang menyimpan flag, posisi pemain, dan inventori ke `user://`.
2. Tambahkan `version` dan fungsi `_migrate` dengan satu migrasi contoh.
3. Rusak berkas save secara manual (hapus kurung kurawal) dan pastikan game menampilkan pesan, bukan crash.

---

## Bab 21: Pengaturan (Settings), Audio, dan Rebinding Input

### 21.1 Menyimpan Pengaturan dengan ConfigFile

```gdscript
# autoload/settings.gd  (autoload "Settings")
extends Node

const PATH: String = "user://settings.cfg"

var music_volume: float = 0.8
var sfx_volume: float = 1.0
var fullscreen: bool = false
var language: String = "en"
var screen_shake: bool = true

func _ready() -> void:
	load_settings()
	apply()

func apply() -> void:
	_set_bus_volume("Music", music_volume)
	_set_bus_volume("SFX", sfx_volume)
	DisplayServer.window_set_mode(
		DisplayServer.WINDOW_MODE_FULLSCREEN if fullscreen
		else DisplayServer.WINDOW_MODE_WINDOWED
	)
	TranslationServer.set_locale(language)

func _set_bus_volume(bus_name: String, linear: float) -> void:
	var idx := AudioServer.get_bus_index(bus_name)
	if idx == -1:
		return
	AudioServer.set_bus_volume_db(idx, linear_to_db(linear))
	AudioServer.set_bus_mute(idx, linear <= 0.001)

func save_settings() -> void:
	var cfg := ConfigFile.new()
	cfg.set_value("audio", "music", music_volume)
	cfg.set_value("audio", "sfx", sfx_volume)
	cfg.set_value("video", "fullscreen", fullscreen)
	cfg.set_value("game", "language", language)
	cfg.set_value("game", "screen_shake", screen_shake)
	cfg.save(PATH)

func load_settings() -> void:
	var cfg := ConfigFile.new()
	if cfg.load(PATH) != OK:
		return      # belum ada berkas, pakai nilai bawaan
	music_volume = cfg.get_value("audio", "music", music_volume)
	sfx_volume = cfg.get_value("audio", "sfx", sfx_volume)
	fullscreen = cfg.get_value("video", "fullscreen", fullscreen)
	language = cfg.get_value("game", "language", language)
	screen_shake = cfg.get_value("game", "screen_shake", screen_shake)
```

Catatan: volume pada slider disimpan sebagai angka linear (0 sampai 1), lalu diubah ke desibel dengan `linear_to_db()`. Jika Anda memakai slider langsung ke desibel, kontrol terasa tidak natural.

### 21.2 Audio Bus

Di panel **Audio** (bagian bawah editor), buat bus: `Master`, `Music`, `SFX`, (opsional) `UI` dan `Ambience`. Arahkan `AudioStreamPlayer` ke bus yang sesuai lewat properti `Bus`. Dengan begitu pemain bisa mengatur volume musik dan efek terpisah, yang merupakan standar yang dihargai pemain.

### 21.3 Audio Manager Sederhana

```gdscript
# autoload/audio_manager.gd  (autoload "AudioManager")
extends Node

var _music_player: AudioStreamPlayer
var _sfx_pool: Array[AudioStreamPlayer] = []

const SFX_POOL_SIZE: int = 12

func _ready() -> void:
	process_mode = Node.PROCESS_MODE_ALWAYS
	_music_player = AudioStreamPlayer.new()
	_music_player.bus = "Music"
	add_child(_music_player)
	for i in SFX_POOL_SIZE:
		var p := AudioStreamPlayer.new()
		p.bus = "SFX"
		add_child(p)
		_sfx_pool.append(p)

func play_music(stream: AudioStream, fade_time: float = 0.8) -> void:
	if _music_player.stream == stream and _music_player.playing:
		return
	var tween := create_tween()
	if _music_player.playing:
		tween.tween_property(_music_player, "volume_db", -40.0, fade_time)
		await tween.finished
	_music_player.stream = stream
	_music_player.volume_db = -40.0
	_music_player.play()
	create_tween().tween_property(_music_player, "volume_db", 0.0, fade_time)

func play_sfx(stream: AudioStream, pitch_variation: float = 0.08) -> void:
	for p in _sfx_pool:
		if not p.playing:
			p.stream = stream
			p.pitch_scale = 1.0 + randf_range(-pitch_variation, pitch_variation)
			p.play()
			return
	# Semua pemutar sibuk: abaikan agar tidak menumpuk
```

Mengacak `pitch_scale` sedikit membuat efek suara yang berulang (langkah kaki, pukulan) tidak terdengar monoton. Atur musik agar bisa mengulang (loop) lewat pengaturan impor berkas audio.

### 21.4 Format Audio

- **WAV**: tanpa kompresi, cocok untuk efek suara pendek.
- **OGG Vorbis**: terkompresi, cocok untuk musik dan ambience yang panjang.
- Normalkan volume semua aset agar tidak ada yang tiba-tiba terlalu keras.
- Pastikan Anda memiliki hak (lisensi) atas semua musik dan suara yang dipakai.

### 21.5 Rebinding Tombol

Pemain menghargai kemampuan mengubah tombol. Godot memungkinkan ini lewat `InputMap`.

```gdscript
# keybinding_button.gd (tombol yang menunggu input baru)
extends Button

@export var action_name: StringName

var _listening: bool = false

func _ready() -> void:
	toggle_mode = true
	toggled.connect(_on_toggled)
	_refresh_text()

func _on_toggled(pressed_now: bool) -> void:
	_listening = pressed_now
	if _listening:
		text = tr("PRESS_ANY_KEY")

func _unhandled_input(event: InputEvent) -> void:
	if not _listening:
		return
	if event is InputEventKey and event.pressed:
		_apply_event(event)
	elif event is InputEventJoypadButton and event.pressed:
		_apply_event(event)

func _apply_event(event: InputEvent) -> void:
	get_viewport().set_input_as_handled()
	InputMap.action_erase_events(action_name)
	InputMap.action_add_event(action_name, event)
	button_pressed = false
	_listening = false
	_refresh_text()
	# Simpan ke settings.cfg agar bertahan antar sesi

func _refresh_text() -> void:
	var events := InputMap.action_get_events(action_name)
	text = events[0].as_text() if events.size() > 0 else "-"
```

Hal yang harus Anda tangani:

- Simpan daftar event ke berkas pengaturan dan terapkan saat game mulai.
- Sediakan tombol "Kembalikan ke bawaan" (`InputMap.load_from_project_settings()`).
- Cegah dua aksi memakai tombol yang sama tanpa peringatan.

### 21.6 Opsi Aksesibilitas Dasar

Hal sederhana yang berdampak besar:

- Slider volume terpisah.
- Opsi mengurangi screen shake dan kilatan.
- Ukuran teks dialog yang bisa diubah.
- Kecepatan teks yang bisa diatur (atau tampil instan).
- Rebinding tombol.
- Mode kontras tinggi atau opsi untuk tidak mengandalkan warna saja.

### Latihan Bab 21

1. Buat menu pengaturan dengan slider musik dan efek, dan simpan ke `settings.cfg`.
2. Buat tombol rebinding untuk `jump` dan `attack`.
3. Tambahkan opsi "kurangi screen shake" dan hubungkan ke kamera.

---

## Bab 22: UI, Menu, Pause, dan Pergantian Scene

### 22.1 Dasar UI di Godot

UI di Godot dibangun dari node **Control**. Konsep kunci:

- **Anchor**: menempelkan node ke sisi atau sudut layar sehingga posisinya menyesuaikan ukuran jendela.
- **Container** (`VBoxContainer`, `HBoxContainer`, `GridContainer`, `MarginContainer`, `CenterContainer`): menata anak-anaknya otomatis.
- **Theme**: satu resource yang mengatur font, warna, dan gaya tombol untuk seluruh UI. Buat satu Theme dan terapkan pada node akar UI Anda.
- Taruh UI di dalam `CanvasLayer` agar tidak ikut bergerak bersama kamera.

Tata letak dengan container lebih tahan perubahan ukuran dan bahasa daripada menaruh node pada posisi piksel tetap.

### 22.2 Navigasi dengan Gamepad dan Keyboard

Pastikan seluruh menu dapat dioperasikan tanpa mouse:

```gdscript
# main_menu.gd
extends Control

func _ready() -> void:
	%StartButton.grab_focus()
	%StartButton.pressed.connect(_on_start_pressed)
	%ContinueButton.pressed.connect(_on_continue_pressed)
	%QuitButton.pressed.connect(get_tree().quit)
	%ContinueButton.disabled = not SaveManager.has_save(1)

func _on_start_pressed() -> void:
	SceneChanger.change_scene("res://levels/level_01.tscn")

func _on_continue_pressed() -> void:
	if SaveManager.load_game(1):
		SceneChanger.change_scene(GameState.current_level_path)
```

Tips: atur `focus_neighbor_*` pada tombol jika urutan fokus bawaan tidak sesuai. Beri gaya visual yang jelas untuk tombol yang sedang fokus.

### 22.3 HUD

HUD sebaiknya hanya **mendengarkan** (signal), bukan memerintah. Contoh bar nyawa berbentuk hati:

```gdscript
# hud_health.gd
extends HBoxContainer

@export var full_heart: Texture2D
@export var empty_heart: Texture2D

func _ready() -> void:
	var player := get_tree().get_first_node_in_group("player") as Player
	if player:
		player.health.health_changed.connect(_on_health_changed)
		_on_health_changed(player.health.current_health, player.health.max_health)

func _on_health_changed(current: int, maximum: int) -> void:
	for child in get_children():
		child.queue_free()
	for i in maximum:
		var heart := TextureRect.new()
		heart.texture = full_heart if i < current else empty_heart
		add_child(heart)
```

Jangan lupa menambahkan pemain ke group `"player"` (`add_to_group("player")` di `_ready()` pemain).

### 22.4 Pause

```gdscript
# pause_menu.gd
extends Control

func _ready() -> void:
	process_mode = Node.PROCESS_MODE_WHEN_PAUSED
	hide()

func _unhandled_input(event: InputEvent) -> void:
	if event.is_action_pressed("pause"):
		get_viewport().set_input_as_handled()
		_toggle()

func _toggle() -> void:
	var now_paused := not get_tree().paused
	get_tree().paused = now_paused
	visible = now_paused
	if now_paused:
		%ResumeButton.grab_focus()
```

Poin penting tentang **`process_mode`**:

|Mode|Perilaku|
|---|---|
|`Inherit`|Mengikuti induk (bawaan).|
|`Pausable`|Berhenti saat pause.|
|`When Paused`|Hanya berjalan saat pause. Cocok untuk menu pause.|
|`Always`|Selalu berjalan. Cocok untuk audio manager.|
|`Disabled`|Tidak pernah berjalan.|

Jebakan: `Engine.time_scale` (hit stop) berbeda dari pause. Jangan memakai `time_scale = 0` untuk pause.

### 22.5 Perpindahan Scene dengan Transisi

```gdscript
# autoload/scene_changer.gd  (autoload "SceneChanger")
extends CanvasLayer

@onready var fade: ColorRect = $Fade

var _busy: bool = false

func _ready() -> void:
	layer = 100                       # selalu di atas
	process_mode = Node.PROCESS_MODE_ALWAYS
	fade.modulate.a = 0.0
	fade.mouse_filter = Control.MOUSE_FILTER_IGNORE

func fade_out(duration: float = 0.3) -> void:
	fade.mouse_filter = Control.MOUSE_FILTER_STOP
	var t := create_tween()
	t.tween_property(fade, "modulate:a", 1.0, duration)
	await t.finished

func fade_in(duration: float = 0.3) -> void:
	var t := create_tween()
	t.tween_property(fade, "modulate:a", 0.0, duration)
	await t.finished
	fade.mouse_filter = Control.MOUSE_FILTER_IGNORE

func change_scene(path: String) -> void:
	if _busy:
		return
	_busy = true
	await fade_out()
	var err := get_tree().change_scene_to_file(path)
	if err != OK:
		push_error("Gagal pindah scene: %s" % path)
	await get_tree().process_frame     # tunggu scene baru terpasang
	await fade_in()
	_busy = false
```

Struktur node `SceneChanger`: `CanvasLayer` (skrip di atas) berisi `ColorRect` bernama `Fade` yang menutupi layar dengan warna hitam dan `modulate.a` awal 0.

### 22.6 Titik Muncul (Spawn) Antar Level

Ketika pemain masuk melalui pintu tertentu, ia perlu muncul di titik yang benar di level berikutnya.

```gdscript
# Di GameState
var next_spawn_id: String = "default"
var current_level_path: String = ""
```

```gdscript
# door.gd
extends Interactable

@export_file("*.tscn") var target_level: String
@export var target_spawn_id: String = "default"

func _ready() -> void:
	interacted.connect(_on_interacted)

func _on_interacted(_by: Node) -> void:
	GameState.next_spawn_id = target_spawn_id
	GameState.current_level_path = target_level
	SceneChanger.change_scene(target_level)
```

```gdscript
# level.gd (skrip dasar level)
class_name Level
extends Node2D

@export var player_scene: PackedScene

func _ready() -> void:
	var spawn := get_node_or_null("Markers/Spawn_" + GameState.next_spawn_id) as Marker2D
	if spawn == null:
		spawn = $Markers/Spawn_default
	var player := player_scene.instantiate() as Player
	player.global_position = spawn.global_position
	add_child(player)
```

### 22.7 Memuat Scene Besar di Latar Belakang

Jika level besar menyebabkan layar membeku saat dimuat, gunakan pemuatan bertahap:

```gdscript
ResourceLoader.load_threaded_request(path)
# ... periksa dengan ResourceLoader.load_threaded_get_status(path)
var packed := ResourceLoader.load_threaded_get(path) as PackedScene
```

Untuk game 2D kecil sampai menengah, `change_scene_to_file` dengan layar fade biasanya sudah cukup.

### Latihan Bab 22

1. Buat menu utama dengan tombol Mulai, Lanjut, Pengaturan, Keluar, semuanya dapat dioperasikan dengan gamepad.
2. Buat menu pause yang bekerja dan tidak menghentikan audio manager.
3. Buat dua level yang terhubung dengan pintu dan titik spawn yang benar.

---

# Bagian 5: Kualitas dan Rilis

## Bab 23: Debugging dan Profiling

### 23.1 Alat Dasar

```gdscript
print("nilai: ", value)                 # cetak sederhana
print_debug("nilai: ", value)           # cetak plus info skrip dan baris
push_warning("Ada yang janggal")        # tampil sebagai warning
push_error("Ini salah")                 # tampil sebagai error
assert(health >= 0, "Nyawa negatif!")   # hanya aktif saat debug
```

Gunakan **breakpoint**: klik di sebelah kiri nomor baris di editor skrip. Saat game berhenti di titik itu, Anda dapat memeriksa variabel pada panel **Debugger** dan melanjutkan langkah demi langkah.

### 23.2 Panel Debugger

|Tab|Fungsi|
|---|---|
|Stack Trace / Errors|Melihat error dan urutan pemanggilan fungsi.|
|Profiler|Mencari fungsi yang memakan waktu paling banyak.|
|Visual Profiler|Waktu untuk CPU dan GPU per frame.|
|Monitors|Grafik FPS, memori, jumlah objek, jumlah node.|
|Video RAM|Penggunaan memori tekstur.|

### 23.3 Remote Scene Tree

Saat game berjalan dari editor, tab **Remote** pada panel Scene menampilkan tree yang sedang berjalan. Anda dapat memeriksa node dan mengubah nilai properti saat berjalan. Sangat berguna untuk menemukan "Mengapa musuh ini tidak bergerak?".

### 23.4 Visible Collision Shapes

Aktifkan **Debug > Visible Collision Shapes** untuk melihat semua bentuk tabrakan, hitbox, dan hurtbox saat game berjalan. Banyak bug tabrakan terlihat jelas dengan opsi ini.

### 23.5 Pesan Error yang Sering Ditemui

|Pesan|Penyebab umum|
|---|---|
|`Invalid access to property or key ... on a base object of type 'Nil'`|Variabel bernilai `null` (node tidak ditemukan, atau sudah dihapus).|
|`Node not found: "..."`|Jalur `$Node` salah atau node belum siap. Periksa nama dan `@onready`.|
|`Can't change this state while flushing queries`|Mengubah fisika di dalam callback fisika. Gunakan `set_deferred`.|
|`Cannot call method '...' on a previously freed instance`|Memakai node yang sudah `queue_free()`. Periksa dengan `is_instance_valid(node)`.|
|`Trying to assign value of type 'X' to a variable of type 'Y'`|Tipe tidak cocok. Periksa tipe statis.|

### 23.6 Cara Berpikir Saat Debug

1. **Reproduksi**: temukan langkah pasti yang memunculkan bug.
2. **Perkecil**: matikan bagian lain sampai bug tinggal di satu tempat.
3. **Hipotesis**: tebak penyebabnya, lalu uji dengan `print` atau breakpoint.
4. **Perbaiki satu hal**, uji lagi.
5. **Catat** penyebabnya agar tidak terulang.

### Latihan Bab 23

1. Sengaja buat error `Nil` lalu baca pesan errornya sampai paham.
2. Aktifkan Visible Collision Shapes dan periksa hitbox serangan pemain.
3. Gunakan Remote tree untuk mengubah kecepatan musuh saat game berjalan.

---

## Bab 24: Optimasi Game 2D

### 24.1 Aturan Utama

**Ukur dahulu, optimasi kemudian.** Kebanyakan game 2D indie sudah berjalan lancar tanpa optimasi khusus. Jangan menulis kode rumit demi kecepatan sebelum Profiler menunjukkan masalah nyata.

### 24.2 Masalah Umum dan Solusinya

|Masalah|Gejala|Solusi|
|---|---|---|
|Terlalu banyak `_process` aktif|FPS turun saat banyak musuh|Matikan proses musuh yang jauh: `set_physics_process(false)`. Gunakan `VisibleOnScreenEnabler2D`.|
|`get_node` atau `get_nodes_in_group` tiap frame|Spike CPU|Simpan referensi di variabel (`@onready`). Hitung sekali.|
|Banyak objek kecil dibuat dan dihapus|Patah-patah saat banyak proyektil|Object pool.|
|Tekstur terlalu besar|Memori video tinggi|Kecilkan ukuran, gunakan atlas.|
|Pathfinding tiap frame|CPU tinggi|Perbarui target dengan Timer.|
|Terlalu banyak cahaya dan bayangan 2D|GPU tinggi|Kurangi jumlah `Light2D`, batasi area bayangan.|
|Partikel berlebihan|GPU atau CPU tinggi|Kurangi jumlah, pakai `CPUParticles2D` untuk efek kecil.|

### 24.3 VisibleOnScreenEnabler2D

Node ini mengaktifkan atau menonaktifkan node tertentu (misalnya musuh) tergantung apakah berada di layar. Sangat efektif untuk level panjang dengan banyak musuh.

### 24.4 Tips Aset

- Pakai satu sprite sheet per karakter, bukan puluhan berkas kecil.
- Hindari ukuran gambar yang jauh lebih besar dari yang tampil di layar.
- Untuk pixel art, gunakan resolusi asli (jangan memperbesar di editor gambar).
- Kompres musik panjang sebagai OGG.

### 24.5 Frame Rate dan Fisika

Laju fisika bawaan 60 kali per detik. Anda dapat mengubahnya di **Project Settings > Physics > Common > Physics Ticks per Second**, tetapi mengubah ini memengaruhi perilaku fisika dan "rasa" gerakan, jadi putuskan di awal proyek, bukan di akhir.

Aktifkan **Physics Interpolation** pada game dengan kamera yang bergerak halus pada monitor refresh rate tinggi (periksa opsi ini di dokumentasi versi Godot Anda) agar gerakan tetap mulus.

### Latihan Bab 24

1. Buat level dengan 100 musuh, lalu lihat FPS dan Profiler.
2. Pasang `VisibleOnScreenEnabler2D` pada musuh dan bandingkan hasilnya.
3. Cari satu fungsi yang paling lambat di Profiler dan jelaskan alasannya.

---

## Bab 25: Testing dan Playtest

### 25.1 Mengapa Testing Penting

Game yang tampak bekerja di komputer Anda belum tentu bekerja bagi orang lain. Testing menangkap bug sebelum pemain menemukannya.

### 25.2 Jenis Pengujian

|Jenis|Cara|
|---|---|
|Uji manual berstruktur|Daftar periksa yang Anda ikuti setiap kali merilis versi baru.|
|Uji unit otomatis|Menguji fungsi kecil (misalnya `HealthComponent`) tanpa menjalankan game. Add-on **GUT** (Godot Unit Test) populer untuk ini.|
|Playtest|Orang lain bermain, Anda **mengamati tanpa membantu**.|

Uji unit otomatis paling berguna untuk logika murni: perhitungan damage, inventori, migrasi save, parsing dialog. Anda tidak perlu menguji semuanya, cukup bagian yang rawan rusak.

### 25.3 Daftar Periksa Uji Manual (Contoh)

- Mulai game baru, selesaikan level 1 sampai akhir.
- Simpan, tutup game, buka lagi, muat save.
- Mati di tiga tempat berbeda, pastikan respawn benar.
- Buka dan tutup menu pause di berbagai situasi (saat dialog, saat cutscene, saat di udara).
- Ganti bahasa lalu cek tidak ada teks yang terpotong.
- Cabut dan colok gamepad saat bermain.
- Ubah ukuran jendela dan resolusi.
- Putar game sampai 30 menit untuk melihat kebocoran memori (grafik di Monitors).

### 25.4 Playtest yang Efektif

1. Cari 3 sampai 5 orang yang belum pernah melihat game Anda.
2. Beri mereka game tanpa instruksi (sesuai pengalaman pemain nyata).
3. Diam dan amati: di mana mereka bingung, mati berulang kali, atau berhenti bermain?
4. Catat **perilaku**, bukan hanya pendapat. "Saya suka" kurang berguna dibanding "dia melewati tombol itu tiga kali".
5. Perbaiki masalah yang dialami **banyak** orang terlebih dahulu.

### 25.5 Metrik Sederhana Tanpa Internet

Karena game Anda offline dan Anda menghargai privasi pemain, jangan mengirim data apa pun tanpa izin. Alternatif: buat tombol "Salin Info Debug" di menu pengaturan, atau minta tester mengirim berkas log (`user://logs/`) secara manual.

### Latihan Bab 25

1. Tulis daftar periksa manual untuk game Anda (minimal 10 butir).
2. Lakukan satu sesi playtest dengan satu orang dan tulis tiga temuan.
3. (Opsional) Pasang GUT dan tulis satu tes untuk `HealthComponent`.

---

## Bab 26: Export dan Distribusi

### 26.1 Mengekspor Game

Langkah dasar:

1. Buka **Editor > Manage Export Templates** dan pasang template yang **versinya sama persis** dengan editor Anda.
2. Buka **Project > Export**, klik **Add...**, pilih platform (Windows Desktop, Linux, macOS, Web).
3. Isi nama, ikon, versi, dan informasi perusahaan.
4. Klik **Export Project** dan pilih lokasi.

Tips penting:

- Beri nama dan versi yang konsisten: `lentera-rimba-0.3.1-win.zip`.
- Uji hasil export di komputer yang **tidak memiliki** Godot terpasang.
- Pastikan semua berkas yang dipakai lewat `load()` dengan jalur dinamis disertakan. Atur **Resources > Export mode** dan filter berkas non-resource (misalnya berkas `.json` dan `.csv` yang Anda baca sendiri) agar masuk ke paket. Berkas yang tidak ikut diekspor adalah penyebab umum "jalan di editor tapi tidak di hasil export".
- Sertakan berkas `export_presets.cfg` dalam Git jika tidak memuat rahasia (kunci tanda tangan), atau simpan terpisah.

### 26.2 Platform

|Platform|Catatan|
|---|---|
|Windows|Paling mudah. Atur ikon. Antivirus kadang salah mendeteksi game baru (false positive), jadi tanda tangan digital membantu.|
|Linux|Mudah. Uji di distribusi populer jika memungkinkan.|
|macOS|Lebih rumit: perlu penandatanganan dan notarization agar tidak diblokir sistem. Periksa dokumentasi resmi untuk langkah terbaru.|
|Web|Cocok untuk demo di itch.io. Sejak 4.3 tersedia export single-thread yang lebih mudah dihosting. Performa dan fitur terbatas dibandingkan desktop.|
|Android dan iOS|Di luar cakupan buku ini.|

Karena game Anda offline, Anda tidak perlu khawatir soal server. Tetapi, pastikan game tidak mencoba mengakses internet tanpa perlu.

### 26.3 Tempat Merilis

|Platform|Kelebihan|Catatan|
|---|---|---|
|itch.io|Mudah, cocok untuk demo, jam game, dan rilis awal|Cocok untuk membangun komunitas awal.|
|Steam|Jangkauan terbesar untuk game PC|Ada biaya pendaftaran per game dan proses peninjauan. Siapkan halaman toko jauh sebelum rilis. Periksa syarat dan biaya terbaru di situs Steamworks.|
|GOG, Epic, lainnya|Jangkauan tambahan|Biasanya setelah Steam atau dengan penerbit.|

Fitur Steam seperti achievement dapat dipakai pada game offline lewat integrasi komunitas (misalnya GodotSteam). Periksa kompatibilitas dengan versi Godot Anda sebelum memutuskan.

### 26.4 Persiapan Rilis (Daftar Periksa)

- Nama dan ikon game final, tidak melanggar merek dagang.
- Layar kredit lengkap, termasuk lisensi aset dan pustaka pihak ketiga (musik, font, add-on).
- Lisensi Godot: Godot memakai lisensi MIT. Sertakan pemberitahuan lisensi sesuai ketentuan (ada opsi di menu Help > About Godot > Licenses, dan layar kredit).
- Versi demo atau Next Fest (untuk Steam) untuk menjaring umpan balik.
- Trailer pendek (30 sampai 60 detik) dan 5 sampai 8 tangkapan layar yang menarik.
- Deskripsi toko jelas: apa gameplay inti, apa yang unik.
- Rencana pasca-rilis: perbaikan bug cepat lewat patch.

### 26.5 Aspek Hukum dan Bisnis Ringkas

Bagian ini informasi umum, bukan nasihat hukum. Konsultasikan dengan ahli untuk keputusan penting.

- Pastikan Anda memiliki hak atas semua aset (gambar, musik, font, suara). Simpan bukti lisensi.
- Pertimbangkan bentuk usaha dan perpajakan di negara Anda sebelum menerima pembayaran dari platform distribusi.
- Platform seperti Steam dan itch.io memiliki ketentuan bagi hasil dan dokumen pajak yang harus Anda isi.

### Latihan Bab 26

1. Pasang export template yang sesuai, lalu ekspor game ke Windows atau Linux.
2. Jalankan hasil export di komputer lain (atau akun pengguna baru) dan catat masalah.
3. Buat daftar kredit lengkap dengan lisensi setiap aset.

---

# Bagian 6: Proyek Akhir

## Bab 27: Proyek Capstone "Lentera Rimba"

Proyek ini menggabungkan semua materi. Ukurannya sengaja kecil dan bisa diselesaikan.

### 27.1 Ringkasan Game

- **Genre**: platformer aksi 2D dengan sedikit eksplorasi (gaya "metroidvania ringan").
- **Premis**: Seorang penjaga lentera menyalakan kembali tiga mercusuar hutan sebelum kegelapan menelan desa.
- **Mekanik inti**: lompat, serang jarak dekat, dan **cahaya lentera** yang bisa diarahkan untuk mengusir musuh bayangan dan menyingkapkan platform tersembunyi.
- **Mode**: offline, pemain tunggal.
- **Cerita**: pendek, lewat teks dan lingkungan. Tanpa voice actor.
- **Durasi**: sekitar 20 sampai 30 menit untuk versi pertama.

### 27.2 Cakupan (Scope) Versi 1.0

Fitur yang **masuk**:

- Satu desa (hub), tiga area berbeda, satu bos mini per area.
- Pemain: lari, lompat (coyote, buffer), serang, dash.
- Tiga jenis musuh dan tiga bos mini dari satu kerangka musuh berbasis resource.
- Cahaya lentera sebagai mekanik (pengaruh pada musuh dan platform).
- Inventori ringan: ramuan penyembuh dan kunci.
- Dialog dengan 5 sampai 8 NPC.
- Codex dengan 15 entri lore.
- Save otomatis di titik istirahat, tiga slot.
- Menu utama, pengaturan (audio, layar penuh, rebinding), pause.
- Bahasa: Inggris dan Indonesia.

Fitur yang **tidak masuk** (catat sebagai ide masa depan, jangan dikerjakan dulu):

- Multiplayer atau fitur daring apa pun.
- Sistem crafting.
- Peta dunia terbuka yang besar.
- Cutscene berat.
- Banyak senjata.

### 27.3 Rencana Per Tahap (Milestone)

|Tahap|Tujuan|Selesai jika|
|---|---|---|
|1. Prototipe abu-abu|Pemain bergerak enak di level kotak polos|Anda sendiri senang menggerakkan pemain 5 menit tanpa bosan.|
|2. Combat dasar|Serang, hit, damage, satu jenis musuh|Pertarungan dengan satu musuh terasa adil dan jelas.|
|3. Mekanik cahaya|Lentera memengaruhi musuh dan platform|Ada setidaknya tiga situasi unik yang memakai cahaya.|
|4. Satu area lengkap (vertical slice)|Satu area dari awal sampai bos, dengan visual dan audio sementara|Orang lain bisa memainkannya tanpa bantuan Anda.|
|5. Sistem pendukung|Save, menu, pengaturan, dialog, codex|Pemain bisa keluar dan melanjutkan permainan dengan aman.|
|6. Konten|Dua area sisanya, musuh, bos, NPC, lore|Seluruh alur dari awal sampai akhir bisa diselesaikan.|
|7. Polesan|Juice, audio final, keseimbangan, bug|Daftar bug mayor kosong.|
|8. Rilis|Export, halaman toko, demo, kredit|Game diunggah dan dapat diunduh orang lain.|

**Vertical slice** adalah satu potongan kecil game yang kualitasnya mendekati hasil akhir. Dengan membuatnya lebih awal, Anda tahu apakah game ini menyenangkan sebelum menghabiskan berbulan-bulan membuat konten.

### 27.4 Arsitektur yang Disarankan

Autoload:

|Nama|Tugas|
|---|---|
|`Events`|Event bus.|
|`GameState`|Flag, lokasi, spawn.|
|`SaveManager`|Baca dan tulis save.|
|`Settings`|Pengaturan pemain.|
|`AudioManager`|Musik dan efek.|
|`SceneChanger`|Transisi scene.|
|`DialogueRunner`|Menjalankan dialog.|
|`Codex`|Entri lore yang terbuka.|

Komponen yang dipakai ulang: `HealthComponent`, `Hurtbox`, `Hitbox`, `StateMachine`, `Interactable`, `Inventory`.

Data (resource): `EnemyData`, `ItemData`, `DialogueSequence`, `LoreEntry`.

### 27.5 Contoh Mekanik Cahaya Sederhana

Gunakan `Area2D` berbentuk kerucut atau lingkaran yang mengikuti pemain. Musuh bayangan memeriksa apakah mereka berada di dalam area cahaya.

```gdscript
# lantern_light.gd (Area2D di bawah Player)
class_name LanternLight
extends Area2D

@export var light_damage_per_second: float = 1.0

var _enemies_in_light: Array[Node2D] = []

func _ready() -> void:
	body_entered.connect(func(b): if b.is_in_group("shadow_enemies"): _enemies_in_light.append(b))
	body_exited.connect(func(b): _enemies_in_light.erase(b))

func _physics_process(delta: float) -> void:
	for enemy in _enemies_in_light:
		if is_instance_valid(enemy) and enemy.has_method("take_light"):
			enemy.take_light(light_damage_per_second * delta)
```

Visualnya bisa dengan `PointLight2D` (cahaya 2D bawaan) yang diberi tekstur gradien, lalu atur `CanvasModulate` pada level agar gelap. Dengan begitu cahaya lentera terlihat menyala. Perhatikan performa: batasi jumlah cahaya aktif.

Alur cerita singkat sebagai contoh: setiap mercusuar yang dinyalakan membuka sepotong lore tentang mengapa kegelapan datang, dan mengubah dialog NPC di desa (lewat flag `lighthouse_1_lit`, `lighthouse_2_lit`, dan seterusnya).

### 27.6 Kriteria Kelulusan Proyek

Anda dinyatakan menyelesaikan capstone jika:

- Game bisa dimainkan dari menu utama sampai akhir tanpa crash.
- Save dan load bekerja, termasuk setelah game ditutup paksa.
- Semua menu bisa dioperasikan dengan keyboard dan gamepad.
- Teks dapat berganti bahasa tanpa teks terpotong.
- Hasil export berjalan di komputer lain.
- Setidaknya tiga orang lain sudah bermain dan Anda sudah memperbaiki masalah terbesar yang mereka temukan.

---

## Bab 28: Mengelola Scope dan Jalan Menuju Rilis

### 28.1 Penyebab Utama Proyek Indie Gagal

Bukan kurang bakat. Penyebabnya hampir selalu **scope yang terlalu besar** dan **kehilangan motivasi di tengah**. Cara mengatasinya:

1. **Mulai kecil.** Game pertama sebaiknya bisa diselesaikan dalam 3 sampai 6 bulan paruh waktu.
2. **Potong fitur secara rutin.** Tanyakan: "Jika fitur ini dihapus, apakah game masih menyenangkan?" Jika ya, simpan untuk nanti.
3. **Selesaikan, jangan sempurnakan.** Game selesai yang agak kasar lebih berharga daripada game sempurna yang tidak pernah rilis.
4. **Kerjakan hal tersulit dan terpenting lebih awal.** Jika mekanik inti belum menyenangkan, jangan habiskan waktu untuk menu.
5. **Buat jadwal yang realistis**, lalu kalikan estimasi waktu Anda dengan 2 sampai 3. Ini kebiasaan yang wajar bagi hampir semua developer.

### 28.2 Kebiasaan Kerja yang Berkelanjutan

- Bekerja sedikit tetapi rutin (misalnya 1 sampai 2 jam per hari) lebih efektif daripada maraton sesekali.
- Akhiri sesi dengan catatan "langkah berikutnya" agar sesi berikutnya mudah dimulai.
- Rayakan pencapaian kecil. Rekam GIF pendek dan bagikan ke teman atau komunitas.
- Jaga kesehatan: tidur, istirahat mata, dan peregangan. Proyek panjang butuh tubuh yang sehat.

### 28.3 Membangun Audiens Sejak Awal

- Bagikan perkembangan secara berkala di media sosial atau komunitas pengembang.
- Buat halaman toko lebih awal (di Steam, ini memungkinkan orang menambahkan game ke daftar keinginan).
- Kumpulkan alamat surel peminat jika Anda nyaman melakukannya.
- Ikuti game jam untuk melatih menyelesaikan proyek kecil dalam waktu singkat.

### 28.4 Setelah Rilis

- Pantau laporan bug, perbaiki yang kritis dahulu.
- Baca ulasan, tetapi jangan membiarkan satu komentar buruk merusak semangat Anda.
- Catat pelajaran untuk proyek berikutnya. Game berikutnya akan jauh lebih baik karena Anda sudah melewati seluruh proses.

---

# Lampiran

## Lampiran A: Glosarium

|Istilah|Arti sederhana|
|---|---|
|Node|Satu objek dasar di Godot (sprite, tombol, kamera, dan sebagainya).|
|Scene|Kumpulan node yang disimpan sebagai berkas dan dapat dipakai ulang.|
|Scene tree|Susunan pohon seluruh node yang sedang aktif dalam game.|
|Instance|Salinan hidup dari sebuah scene atau class.|
|Signal|Pesan "sesuatu terjadi" yang dapat didengar node lain.|
|Autoload|Skrip atau scene yang dimuat otomatis dan tersedia global.|
|Resource|Wadah data yang dapat disimpan sebagai berkas (`.tres`).|
|Inspector|Panel di editor untuk mengubah properti node atau resource.|
|Delta|Waktu (detik) sejak frame sebelumnya.|
|Static typing|Menuliskan tipe data variabel secara eksplisit.|
|Core loop|Rangkaian aksi inti yang berulang dalam game.|
|Game feel|Seberapa enak dan responsif sebuah aksi terasa.|
|Juice|Umpan balik visual dan audio yang membuat aksi terasa memuaskan.|
|Hitbox|Area yang memberi damage.|
|Hurtbox|Area yang bisa menerima damage.|
|I-frames|Masa kebal sesaat setelah terkena serangan.|
|Coyote time|Jeda singkat untuk melompat setelah melewati tepi platform.|
|Jump buffer|Menyimpan tombol lompat yang ditekan sedikit sebelum mendarat.|
|State machine|Pola kode di mana objek berada di tepat satu keadaan pada satu waktu.|
|Tween|Alat untuk mengubah nilai secara halus dalam waktu tertentu.|
|TileMapLayer|Node untuk menggambar level dari ubin (tile).|
|Telegraph|Isyarat visual sebelum serangan musuh terjadi.|
|Vertical slice|Satu potongan game yang kualitasnya mendekati hasil akhir.|
|Scope|Ukuran atau cakupan proyek.|
|Lokalisasi|Menyesuaikan game ke bahasa dan budaya lain.|
|Export template|Berkas Godot yang diperlukan untuk membuat hasil build game.|
|Playtest|Sesi di mana orang lain memainkan game Anda untuk diamati.|
|Lore|Latar belakang dan sejarah dunia game.|

---

## Lampiran B: Cheat Sheet

### B.1 Pola Kode yang Sering Dipakai

```gdscript
# Referensi node
@onready var sprite: AnimatedSprite2D = $AnimatedSprite2D
@onready var timer: Timer = %CooldownTimer

# Signal
signal died
died.emit()
other.died.connect(_on_died)

# Menunggu
await get_tree().create_timer(1.0).timeout
await $AnimationPlayer.animation_finished

# Instansiasi
var node := SCENE.instantiate()
get_tree().current_scene.add_child(node)

# Hapus
queue_free()

# Cari node
get_tree().get_first_node_in_group("player")
get_tree().get_nodes_in_group("enemies")

# Aman terhadap node yang sudah dihapus
if is_instance_valid(target):
	target.take_damage(1)

# Tween
var t := create_tween()
t.tween_property(self, "modulate:a", 0.0, 0.3)

# Acak
randf_range(0.0, 1.0)
randi_range(1, 6)
[1, 2, 3].pick_random()
```

### B.2 Matematika 2D Penting

```gdscript
Vector2.ZERO / Vector2.ONE / Vector2.UP / Vector2.DOWN / Vector2.LEFT / Vector2.RIGHT
a.distance_to(b)                  # jarak
a.direction_to(b)                 # arah ternormalisasi dari a ke b
v.normalized()                    # panjang menjadi 1
v.length()                        # panjang vektor
lerp(a, b, 0.5)                   # interpolasi linear
move_toward(a, b, step)           # mendekat dengan langkah tetap
clampf(x, 0.0, 1.0)               # batasi nilai
signf(x)                          # -1, 0, atau 1
```

### B.3 Pengaturan Proyek yang Sering Dicari

|Kebutuhan|Lokasi|
|---|---|
|Input action|Project Settings > Input Map|
|Autoload|Project Settings > Globals > Autoload|
|Layer collision bernama|Project Settings > Layer Names > 2D Physics|
|Resolusi dan stretch|Project Settings > Display > Window|
|Filter tekstur pixel art|Project Settings > Rendering > Textures|
|Terjemahan|Project Settings > Localization|
|Folder data pengguna|Project > Open User Data Folder|
|Export template|Editor > Manage Export Templates|

### B.4 Konvensi Layer Collision (Contoh)

|Layer|Isi|
|---|---|
|1 world|Tanah, dinding, platform|
|2 player|Badan pemain|
|3 enemy|Badan musuh|
|4 player_hitbox|Serangan pemain|
|5 enemy_hitbox|Serangan musuh|
|6 hurtbox_player|Area rentan pemain|
|7 hurtbox_enemy|Area rentan musuh|
|8 pickup|Item di lantai|
|9 interactable|NPC, peti, pintu|

---

## Lampiran C: Kesalahan Umum

|Kesalahan|Akibat|Solusi|
|---|---|---|
|Menaruh semua logika di satu skrip raksasa|Sulit dirawat|Pecah menjadi komponen dan state machine.|
|Anak memanggil `get_parent()` berlapis|Scene tidak bisa dipakai ulang|Gunakan signal ke atas.|
|Terlalu banyak autoload|Ketergantungan kusut|Batasi autoload untuk hal yang benar-benar global.|
|Mengubah resource data saat berjalan|Semua instance ikut berubah|Perlakukan sebagai hanya-baca atau `duplicate()`.|
|Menyimpan save dengan `Resource`|Risiko keamanan dan rapuh|Pakai JSON dengan versi.|
|Menimpa berkas save langsung|Save rusak saat crash|Tulis ke berkas sementara lalu ganti nama.|
|Menggunakan `KEY_*` langsung|Pemain tidak bisa mengubah tombol|Pakai Input Map.|
|Nama berkas campur huruf besar-kecil|Gagal di Linux atau hasil export|Pakai `snake_case` huruf kecil.|
|Tidak menguji hasil export|Masalah baru muncul saat dirilis|Uji export sejak awal dan berkala.|
|Menambah fitur sebelum inti game menyenangkan|Waktu terbuang|Perbaiki core loop dahulu.|
|Menunda lokalisasi sampai akhir|Teks tertanam di kode, perombakan besar|Pakai kunci terjemahan sejak awal.|
|Mengabaikan warning GDScript|Bug tersembunyi|Perlakukan warning sebagai peringatan nyata.|
|Mengubah versi Godot di tengah proyek tanpa alasan|Perilaku berubah, bug baru|Tetap di satu versi, upgrade terencana.|
|Tidak melakukan commit rutin|Sulit kembali saat ada kesalahan|Commit kecil dan sering.|

---

## Lampiran D: Sumber Belajar Lanjutan

Daftar ini berisi jenis sumber yang layak dicari. Periksa selalu bahwa materi sesuai dengan **Godot 4.x**, karena banyak tutorial lama untuk Godot 3 sudah tidak cocok (sintaks dan nama node berbeda).

**Resmi**

- Dokumentasi Godot di docs.godotengine.org. Pilih versi yang sama dengan editor Anda. Bagian "Tutorials > 2D" dan "Best practices" sangat relevan.
- Demo proyek resmi Godot di repositori GitHub godotengine/godot-demo-projects, berguna untuk melihat contoh kode kerja.
- Blog resmi godotengine.org untuk catatan rilis dan fitur baru.

**Komunitas**

- Forum dan server komunitas Godot (Godot Forum, Discord, Reddit r/godot) untuk bertanya.
- Situs seperti itch.io dan komunitas game jam untuk mencoba dan berbagi game kecil.
- Kanal dan kursus video berbahasa Inggris maupun Indonesia dari kreator Godot. Cari yang menggunakan Godot 4.

**Desain Game dan Cerita**

- Buku dan ceramah tentang desain game (misalnya konsep core loop, level design, dan game feel). Cari ceramah GDC yang tersedia gratis.
- Analisis game 2D indie favorit Anda: apa mekanik intinya, bagaimana ia mengajarkan pemain, bagaimana ia menyampaikan cerita tanpa banyak teks.

**Aset**

- Gunakan aset berlisensi jelas (misalnya CC0 atau berbayar dengan lisensi komersial). Simpan catatan sumber dan lisensi untuk setiap aset.

---

## Penutup

Anda sekarang memiliki peta lengkap dari tingkat menengah Godot untuk game 2D indie: dari struktur proyek, kode yang rapi, gameplay yang terasa enak, cerita yang mendukung, sampai game yang aman disimpan, diuji, dan dirilis.

Tiga pesan terakhir:

1. **Selesaikan proyek kecil.** Satu game kecil yang rilis mengajarkan lebih banyak daripada sepuluh prototipe yang ditinggalkan.
2. **Gameplay adalah fondasi.** Cerita, lore, dan seni memperkaya, tetapi yang membuat pemain kembali adalah rasa bermain yang menyenangkan.
3. **Belajar sambil membuat.** Setiap bab di buku ini paling berguna jika langsung dipraktikkan di proyek Anda sendiri.

Selamat membuat game.