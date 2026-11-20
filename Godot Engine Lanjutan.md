# Godot Engine Lanjutan untuk Game Developer Indie

**Fokus: Game 2D, Offline (Single Player), Gameplay-First, Cerita dan Lore Tanpa Voice Actor**

Edisi: November 2026 Versi engine acuan: Godot 4.7.x (stable) dengan bahasa GDScript Tingkat: Menengah ke Lanjut (untuk pemula yang sudah menyelesaikan dasar Godot)

---

## Daftar Isi

- Pengantar dan Cara Memakai Buku Ini
- Bab 1. Filosofi: Gameplay Dulu, Cerita Mengikuti
- Bab 2. Setup Proyek 2D Profesional
- Bab 3. GDScript Lanjutan
- Bab 4. Arsitektur Game: Scene, Komposisi, Autoload, Event Bus
- Bab 5. Data-Driven Design dengan Resource
- Bab 6. State Machine
- Bab 7. Player Controller yang "Terasa Enak"
- Bab 8. Fisika 2D Lanjutan, Hitbox, dan Hurtbox
- Bab 9. Combat, Musuh, dan AI
- Bab 10. Animasi Lanjutan
- Bab 11. Level Design: TileMapLayer, Kamera, dan Transisi Ruangan
- Bab 12. Cerita dan Lore Tanpa Voice Actor
- Bab 13. Sistem Dialog, Flag, dan Quest
- Bab 14. Save dan Load (Offline)
- Bab 15. UI Lanjutan, Gamepad, dan Remap Input
- Bab 16. Audio untuk Game Tanpa Voice Actor
- Bab 17. Shader 2D dan Efek Visual
- Bab 18. Lokalisasi (Termasuk Bahasa Indonesia)
- Bab 19. Performa, Profiling, dan Debugging
- Bab 20. Tooling, Version Control, dan Testing
- Bab 21. Export dan Rilis Game Offline
- Bab 22. Proyek Penutup (Capstone) dan Peta Jalan
- Lampiran A. Glosarium
- Lampiran B. Cheat Sheet
- Lampiran C. Checklist Sebelum Rilis
- Lampiran D. Sumber Belajar

---

## Pengantar dan Cara Memakai Buku Ini

### Untuk siapa buku ini?

Buku ini untuk Anda yang:

- Sudah pernah membuka Godot dan membuat game kecil (misalnya game "Dodge the Creeps" atau platformer sederhana dari tutorial resmi).
- Ingin naik level dari "bisa bikin game kecil" menjadi "bisa bikin game 2D utuh yang layak dijual".
- Ingin membuat game offline untuk satu pemain, dengan cerita dan lore, tetapi yang utama adalah gameplay-nya.

Anda tidak perlu menjadi programmer berpengalaman. Setiap konsep dijelaskan dengan bahasa teknis yang tetap dibuat mudah, disertai contoh kode yang bisa disalin dan dicoba.

### Prasyarat

Anda sebaiknya sudah paham hal berikut (jika belum, pelajari dulu dokumentasi resmi Godot bagian "Getting Started"):

- Konsep Node dan Scene.
- Dasar GDScript: variabel, fungsi, `if`, `for`, `_ready()`, `_process()`.
- Cara menjalankan game (tombol Play atau F5) dan membaca panel Output.
- Cara membuat Input Action di Project Settings.

### Catatan versi (penting)

Godot dirilis dengan irama yang cepat. Berdasarkan sumber resmi dan pemberitaan yang saya periksa untuk menyusun buku ini:

- Godot 4.6 dirilis pada 26 Januari 2026.
- Godot 4.7 dirilis pada pertengahan Juni 2026, lalu mendapat rilis pemeliharaan (maintenance) seperti 4.7.1 dan 4.7.2.
- Godot 4.8 sempat berada pada tahap beta pada pertengahan 2026. Saat Anda membaca buku ini, versi 4.8 mungkin sudah stabil.

Aturan praktis: **pakai versi stable terbaru dari seri yang sama selama satu proyek**. Jangan pindah versi mayor (misalnya 4.7 ke 4.8) di tengah produksi tanpa alasan kuat dan tanpa backup. Pindah versi minor sebaiknya dilakukan di awal fase, bukan menjelang rilis.

Hampir seluruh kode dalam buku ini memakai API inti Godot 4 yang stabil, jadi akan tetap berlaku di 4.7, 4.8, dan seterusnya. Jika ada perbedaan kecil nama menu atau properti, cek dokumentasi resmi di `docs.godotengine.org` untuk versi Anda.

### Mengapa GDScript, bukan C#?

Buku ini memakai GDScript karena:

- Terintegrasi paling erat dengan editor (autocomplete, debugger, hot reload).
- Ringan, cepat ditulis, dan cocok untuk game 2D indie.
- Ekspor ke semua platform paling sedikit hambatannya.

C# tetap pilihan bagus jika Anda sudah mahir. Konsep arsitektur di buku ini berlaku sama untuk C#.

### Konvensi penulisan

- Kode ditulis dalam blok kode dengan bahasa `gdscript`.
- Kata dalam `format kode` adalah nama node, fungsi, atau properti.
- Bagian **Kesalahan Umum** menjelaskan jebakan yang sering membuat pemula frustrasi.
- Bagian **Latihan** adalah tugas kecil untuk memastikan Anda benar-benar paham.

---

## Bab 1. Filosofi: Gameplay Dulu, Cerita Mengikuti

### 1.1 Apa artinya "gameplay-first"?

Gameplay-first berarti keputusan desain selalu dimulai dari pertanyaan: "Apa yang dilakukan pemain setiap detik, dan apakah itu menyenangkan?" Cerita dan lore adalah lapisan yang memperkaya pengalaman itu, bukan penghalang antara pemain dan permainan.

Beberapa prinsip yang akan kita pakai di seluruh buku ini:

1. **Core loop dulu.** Core loop adalah siklus aksi inti yang diulang pemain. Contoh: jelajah, bertarung, ambil loot, perkuat karakter, jelajah lagi. Bangun dan uji ini sebelum menulis satu pun dialog.
2. **Cerita disampaikan lewat gameplay.** Pemain mempelajari dunia dari apa yang ia lihat, ambil, dan alami, bukan dari tembok teks.
3. **Cerita bisa dilewati.** Pemain yang hanya ingin bermain tidak boleh terhambat. Pemain yang peduli lore diberi cara untuk menggali lebih dalam (codex, deskripsi item, catatan tersebar).
4. **Skop kecil, polesan tinggi.** Indie developer solo atau tim kecil menang dengan game yang pendek tetapi matang, bukan game raksasa yang setengah jadi.

### 1.2 Mengapa 2D, offline, dan tanpa voice actor adalah keputusan bagus untuk indie

- **2D** lebih murah di aset, lebih mudah dibuat konsisten, dan Godot punya pipeline 2D yang sangat kuat (bukan 2D "palsu" di atas 3D, melainkan renderer 2D sendiri).
- **Offline** menghapus kebutuhan server, anti-cheat online, biaya hosting, dan masalah sinkronisasi jaringan. Anda hanya perlu fokus pada kualitas pengalaman satu pemain.
- **Tanpa voice actor** menghemat biaya produksi, menyederhanakan lokalisasi (cukup menerjemahkan teks), dan memaksa Anda memakai alat penceritaan yang lebih kreatif: teks, musik, bunyi, animasi, dan lingkungan.

### 1.3 Jenis game yang cocok dengan pendekatan ini

Buku ini menggunakan beberapa contoh genre agar konsep terasa nyata:

- Platformer aksi (gaya Metroidvania ringan).
- Action RPG top-down (gaya Zelda klasik).
- Roguelite berbasis ruangan.

Anda tidak harus membuat ketiganya. Pilih satu untuk proyek capstone di Bab 22.

### 1.4 Dokumen desain satu halaman

Sebelum menulis kode, tulis satu halaman berisi:

- **Pilar desain** (3 hal): misalnya "pertarungan cepat dan adil", "dunia misterius yang dijelajahi", "progres terasa nyata".
- **Core loop**: satu kalimat.
- **Fitur wajib** dan **fitur kalau sempat**.
- **Skop**: berapa area, berapa musuh, berapa jam bermain.

Latihan: tulis dokumen satu halaman untuk game impian Anda. Simpan sebagai `docs/desain.md` di proyek Anda.

---

## Bab 2. Setup Proyek 2D Profesional

### 2.1 Struktur folder

Struktur folder yang rapi mencegah proyek menjadi berantakan saat aset bertambah ratusan. Contoh yang dianjurkan:

```text
res://
  assets/
    art/
      characters/
      environment/
      ui/
      vfx/
    audio/
      music/
      sfx/
    fonts/
    shaders/
  data/
    items/
    enemies/
    dialogue/
    quests/
  scenes/
    actors/
      player/
      enemies/
      npcs/
    levels/
    ui/
    components/
  scripts/
    autoload/
    components/
    resources/
    state_machine/
  localization/
  addons/
  docs/
```

Prinsip penamaan:

- Folder dan file memakai `snake_case` huruf kecil (misalnya `player_idle.png`). Ini mencegah masalah di Linux yang membedakan huruf besar dan kecil.
- Scene dan script yang berpasangan memakai nama sama (`player.tscn` dan `player.gd`).
- Nama class memakai `PascalCase` (misalnya `HealthComponent`).

Kesalahan umum: nama file bercampur huruf besar kecil. Game berjalan di Windows, tetapi gagal memuat aset di Linux atau di build ekspor karena path berbeda huruf.

### 2.2 Pengaturan proyek untuk game 2D

Buka **Project > Project Settings** dan perhatikan:

**Display > Window**

- `Viewport Width` dan `Viewport Height`: resolusi dasar game Anda. Untuk pixel art, pilih resolusi kecil seperti 320x180 atau 480x270, lalu skalakan ke layar.
- `Stretch > Mode`: `canvas_items` untuk game 2D umumnya. Mode ini menjaga tampilan tajam saat jendela diperbesar.
- `Stretch > Aspect`: `keep` agar rasio aspek terjaga dengan bilah hitam (letterbox) bila perlu.
- `Stretch > Scale Mode`: `integer` untuk pixel art agar piksel tidak terlihat tidak rata. Untuk art beresolusi tinggi, gunakan `fractional`.

**Rendering > Textures**

- `Default Texture Filter`: `Nearest` untuk pixel art, `Linear` untuk art halus.

**Rendering > 2D**

- Ada opsi untuk "snap 2D transforms to pixel" (snap posisi ke piksel) yang berguna untuk pixel art agar sprite tidak bergetar saat kamera bergerak halus. Cari "snap" pada kotak pencarian Project Settings (aktifkan Advanced Settings).

**Physics > 2D**

- Atur `Default Gravity` sesuai skala dunia Anda. Nilai bawaan 980 cocok untuk dunia dengan skala piksel tertentu. Banyak developer mengubahnya atau mengabaikannya dengan memakai gravitasi sendiri (Bab 7).

**Physics > Common**

- `Physics Ticks per Second` (bawaan 60). Untuk game aksi presisi, 60 sudah cukup. Menaikkan nilai ini meningkatkan akurasi tetapi menambah beban CPU.

### 2.3 Layer fisika dan nama layer

Beri nama layer fisika agar tidak bingung. Di **Project Settings > Layer Names > 2D Physics**, isi misalnya:

|Layer|Nama|
|---|---|
|1|world (tanah dan dinding)|
|2|player|
|3|enemy|
|4|player_hitbox|
|5|enemy_hitbox|
|6|player_hurtbox|
|7|enemy_hurtbox|
|8|interactable|
|9|pickup|

Juga lakukan hal yang sama untuk **2D Navigation** dan **2D Render** bila dipakai.

### 2.4 Input Map

Buat action dengan nama yang menjelaskan fungsi, bukan tombol: `move_left`, `move_right`, `move_up`, `move_down`, `jump`, `attack`, `dash`, `interact`, `pause`.

Tambahkan beberapa event per action: keyboard, dan juga gamepad. Dukungan gamepad sejak awal jauh lebih mudah daripada menambahkannya belakangan.

### 2.5 Version control sejak hari pertama

Gunakan Git. Pada Godot 4, buat file `.gitignore` berisi minimal:

```text
# Godot
.godot/
*.import~
export_presets.cfg
build/
export/
*.tmp
```

Catatan: sejak Godot 4.4, file `.uid` ikut dibuat di samping script dan resource. File ini **sebaiknya di-commit** agar referensi antar-resource tetap stabil di antara anggota tim dan setelah memindahkan file. Jangan masukkan `*.uid` ke `.gitignore`.

Pada `export_presets.cfg`: jika file ini berisi path atau kredensial pribadi (misalnya keystore Android), jangan commit. Jika hanya berisi preset umum, banyak tim justru meng-commit-nya. Putuskan berdasarkan isinya.

### 2.6 Latihan Bab 2

1. Buat proyek baru dengan renderer `Compatibility` atau `Forward+`/`Mobile`. Untuk game 2D yang ingin jalan di banyak perangkat termasuk yang lawas, renderer Compatibility adalah pilihan aman dan ringan. Untuk efek cahaya 2D dan shader lebih berat, Forward+ atau Mobile juga bisa dipakai. Putuskan sesuai target perangkat pemain Anda.
2. Buat struktur folder di atas.
3. Inisialisasi Git dan commit pertama.

---

## Bab 3. GDScript Lanjutan

### 3.1 Static typing

Static typing berarti Anda memberi tahu GDScript tipe data setiap variabel dan fungsi. Manfaatnya: autocomplete lebih baik, error tertangkap sebelum game dijalankan, dan performa sedikit lebih baik.

```gdscript
# Tanpa tipe (dinamis)
var health = 10

# Dengan tipe eksplisit
var health: int = 10

# Inferensi tipe memakai :=
var speed := 120.0          # otomatis float
var player_name := "Aria"   # otomatis String

# Fungsi dengan tipe parameter dan return
func take_damage(amount: int) -> void:
	health -= amount

func is_dead() -> bool:
	return health <= 0
```

Array bertipe:

```gdscript
var enemies: Array[Enemy] = []
var scores: Array[int] = [10, 20, 30]
```

Anjuran: aktifkan peringatan untuk kode tanpa tipe di **Project Settings > Debug > GDScript** (cari "untyped declaration"). Mulailah dengan level "Warn" agar Anda terbiasa menulis tipe.

### 3.2 `class_name`, pewarisan, dan `extends`

`class_name` membuat script Anda dikenali sebagai tipe global. Anda bisa memakainya di `@export`, pengecekan `is`, dan deklarasi tipe.

```gdscript
class_name HealthComponent
extends Node

signal health_changed(current: int, maximum: int)
signal died

@export var max_health: int = 3

var current_health: int

func _ready() -> void:
	current_health = max_health
```

Gunakan dengan:

```gdscript
@onready var health: HealthComponent = $HealthComponent
```

### 3.3 Signal bertipe dan cara memakainya

Signal adalah mekanisme "kejadian" di Godot. Node pengirim memancarkan (emit) signal, node lain yang berlangganan (connect) akan bereaksi. Dengan signal, node tidak perlu saling mengenal secara langsung. Ini disebut **loose coupling**, dan merupakan kunci arsitektur bersih.

```gdscript
signal died
signal damaged(amount: int, source: Node)

func take_damage(amount: int, source: Node) -> void:
	current_health -= amount
	damaged.emit(amount, source)
	if current_health <= 0:
		died.emit()
```

Menghubungkan lewat kode:

```gdscript
func _ready() -> void:
	health.died.connect(_on_died)
	health.damaged.connect(_on_damaged)

func _on_died() -> void:
	queue_free()

func _on_damaged(amount: int, source: Node) -> void:
	print("Kena %d damage dari %s" % [amount, source.name])
```

Aturan emas: **"Call down, signal up."** Node induk boleh memanggil fungsi node anak secara langsung (turun). Node anak sebaiknya memberi tahu induk lewat signal (naik), bukan memanggil `get_parent().sesuatu()`.

### 3.4 Callable, lambda, dan `bind`

`Callable` adalah "referensi ke fungsi" yang bisa disimpan dan dipanggil nanti.

```gdscript
var aksi: Callable = func(x: int) -> int: return x * 2
print(aksi.call(5))  # 10
```

`bind` menambahkan argumen tetap saat menghubungkan signal:

```gdscript
for tombol in $Menu.get_children():
	if tombol is Button:
		tombol.pressed.connect(_on_menu_pressed.bind(tombol.name))

func _on_menu_pressed(nama: String) -> void:
	print("Ditekan: ", nama)
```

### 3.5 `await` dan coroutine

`await` menjeda fungsi sampai suatu signal terpancar, tanpa memblokir game. Ini sangat berguna untuk urutan (cutscene, tutorial, animasi bertahap).

```gdscript
func tampilkan_judul() -> void:
	$Judul.show()
	await get_tree().create_timer(2.0).timeout
	$Judul.hide()
	await $AnimationPlayer.animation_finished
	print("Selesai")
```

Peringatan: jika node dihapus (`queue_free`) saat sedang `await`, fungsi tidak akan dilanjutkan. Ini biasanya aman, tetapi ingat bahwa kode setelah `await` mungkin tidak pernah berjalan.

### 3.6 Enum, konstanta, dan `StringName`

```gdscript
enum Arah { KIRI, KANAN, ATAS, BAWAH }
const GRAVITY_SCALE: float = 1.0

var arah_sekarang: Arah = Arah.KANAN
```

`StringName` (ditulis `&"nama"`) adalah string yang dioptimalkan untuk perbandingan cepat. Dipakai untuk nama animasi, input action, dan flag.

```gdscript
if Input.is_action_just_pressed(&"jump"):
	$AnimationPlayer.play(&"jump")
```

### 3.7 `@export`, `@export_group`, `@onready`, `@tool`

Anotasi yang sering dipakai:

```gdscript
@export_group("Gerak")
@export var max_speed: float = 180.0
@export_range(0.0, 1.0, 0.05) var friction: float = 0.2
@export var weapon: PackedScene

@export_subgroup("Debug")
@export var tampilkan_garis: bool = false

@onready var sprite: Sprite2D = $Sprite2D
```

`@onready` menjalankan penetapan variabel tepat sebelum `_ready()`, setelah seluruh node anak siap. Tanpa `@onready`, `$Sprite2D` akan bernilai `null` jika dipakai saat inisialisasi variabel.

`@tool` membuat script berjalan di editor, berguna untuk alat bantu level design (misalnya menggambar gizmo atau mengubah properti otomatis). Gunakan hati-hati: error di script `@tool` bisa membuat editor tidak stabil.

### 3.8 Setter dan getter pada properti

```gdscript
var health: int = 3:
	set(value):
		health = clampi(value, 0, max_health)
		health_changed.emit(health, max_health)
	get:
		return health
```

Setiap kali `health = 5` dijalankan, kode `set` ikut berjalan. Praktis untuk memastikan nilai valid dan memperbarui UI otomatis.

### 3.9 Kesalahan umum Bab 3

- Memakai `get_node("../../Sesuatu")` panjang-panjang. Ini rapuh. Gunakan signal, `@export var target: Node`, atau grup.
- Lupa `await` pada fungsi coroutine, sehingga hasilnya tidak ditunggu.
- Menyimpan referensi node yang sudah di-`queue_free()` lalu mengaksesnya. Periksa dengan `is_instance_valid(node)`.

### 3.10 Latihan Bab 3

1. Tulis `HealthComponent` lengkap dengan signal `health_changed` dan `died`, serta `heal()` dan `take_damage()`.
2. Ubah script lama Anda agar memakai static typing penuh.

---

## Bab 4. Arsitektur Game: Scene, Komposisi, Autoload, Event Bus

### 4.1 Komposisi lebih baik daripada pewarisan dalam

Godot mendorong **komposisi**: membangun objek kompleks dari node-node kecil yang masing-masing punya satu tugas. Contoh musuh:

```text
Slime (CharacterBody2D)
  Sprite2D / AnimatedSprite2D
  CollisionShape2D
  HealthComponent (Node)
  Hurtbox (Area2D)
    CollisionShape2D
  Hitbox (Area2D)
    CollisionShape2D
  StateMachine (Node)
    Idle
    Chase
    Attack
    Hurt
    Dead
```

Keuntungannya: `HealthComponent` yang sama bisa dipakai pemain, musuh, peti, bahkan pintu yang bisa dihancurkan. Anda tidak perlu menulis ulang.

Hindari pohon pewarisan yang dalam seperti `Entity > Character > Enemy > FlyingEnemy > FlyingFireEnemy`. Setiap perubahan di atas pohon bisa merusak semua turunan.

### 4.2 Scene sebagai "prefab"

Setiap hal yang berulang dijadikan scene sendiri: pemain, tiap jenis musuh, peti, pintu, pickup, partikel, UI popup. Scene lalu di-instantiate di level.

```gdscript
@export var enemy_scene: PackedScene

func spawn_enemy(posisi: Vector2) -> void:
	var enemy := enemy_scene.instantiate() as Node2D
	enemy.global_position = posisi
	add_child(enemy)
```

### 4.3 Autoload (singleton)

Autoload adalah script/scene yang dimuat otomatis saat game dimulai dan dapat diakses dari mana saja lewat namanya. Atur di **Project Settings > Globals > Autoload**.

Gunakan autoload untuk hal yang benar-benar global:

- `EventBus` (siaran kejadian lintas sistem).
- `GameState` (flag cerita, data progres).
- `SaveManager` (simpan dan muat).
- `AudioManager` (musik dan SFX).
- `SceneManager` (pindah level dengan transisi).
- `Settings` (volume, kontrol, bahasa).

Jangan menjadikan semuanya autoload. Autoload yang terlalu banyak membuat kode saling bergantung dan sulit diuji. Aturan praktis: jika hanya satu scene yang butuh, jangan jadikan autoload.

### 4.4 Event Bus

Event Bus adalah autoload yang hanya berisi signal. Sistem yang tidak saling kenal bisa berkomunikasi lewatnya.

`scripts/autoload/event_bus.gd`:

```gdscript
extends Node

signal player_health_changed(current: int, maximum: int)
signal enemy_killed(enemy_id: StringName)
signal item_picked_up(item_id: StringName, amount: int)
signal flag_changed(flag: StringName, value: Variant)
signal dialogue_requested(dialogue_id: StringName)
signal level_change_requested(level_path: String, spawn_id: StringName)
signal screen_shake_requested(strength: float)
```

Memancarkan dari musuh:

```gdscript
func _on_died() -> void:
	EventBus.enemy_killed.emit(enemy_id)
	queue_free()
```

Mendengarkan dari UI atau sistem quest:

```gdscript
func _ready() -> void:
	EventBus.enemy_killed.connect(_on_enemy_killed)

func _on_enemy_killed(enemy_id: StringName) -> void:
	# update objektif quest
	pass
```

Peringatan: Event Bus yang berlebihan membuat alur sulit dilacak ("siapa yang memancarkan ini?"). Pakai untuk kejadian lintas sistem saja. Komunikasi dalam satu scene cukup dengan signal biasa.

### 4.5 Scene Manager dengan transisi

```gdscript
# scripts/autoload/scene_manager.gd
extends CanvasLayer

@onready var fade: ColorRect = $Fade
var _busy: bool = false

func change_level(path: String, spawn_id: StringName = &"default") -> void:
	if _busy:
		return
	_busy = true
	get_tree().paused = true
	var tw := create_tween()
	tw.tween_property(fade, "modulate:a", 1.0, 0.25)
	await tw.finished
	get_tree().change_scene_to_file(path)
	await get_tree().scene_changed
	_place_player(spawn_id)
	var tw2 := create_tween()
	tw2.tween_property(fade, "modulate:a", 0.0, 0.25)
	await tw2.finished
	get_tree().paused = false
	_busy = false

func _place_player(spawn_id: StringName) -> void:
	for node in get_tree().get_nodes_in_group(&"spawn_point"):
		if node.name == spawn_id:
			var player := get_tree().get_first_node_in_group(&"player") as Node2D
			if player:
				player.global_position = (node as Node2D).global_position
```

Catatan: agar tween tetap berjalan saat game di-pause, atur `process_mode` node `SceneManager` menjadi `Always`. Dan tween yang dibuat dari node itu akan mengikuti `process_mode` node tersebut. Verifikasi perilaku tween dan pause pada versi Godot Anda, karena opsi `Tween.set_pause_mode` juga tersedia.

Catatan lain: signal `scene_changed` tersedia di `SceneTree` pada Godot versi baru. Jika versi Anda tidak memilikinya, gunakan `await get_tree().process_frame` setelah `change_scene_to_file`. Selalu cek dokumentasi versi Anda.

### 4.6 Grup (Groups)

Grup adalah label untuk mengelompokkan node. Praktis untuk "semua musuh", "semua titik spawn", "semua objek yang bisa disimpan".

```gdscript
add_to_group(&"enemy")
for e in get_tree().get_nodes_in_group(&"enemy"):
	e.queue_free()

get_tree().call_group(&"enemy", "alert", player.global_position)
```

### 4.7 Latihan Bab 4

1. Buat `EventBus` dan hubungkan dengan satu HUD yang menampilkan nyawa.
2. Buat scene `Slime` memakai komposisi (HealthComponent, Hurtbox, StateMachine kosong).

---

## Bab 5. Data-Driven Design dengan Resource

### 5.1 Apa itu Resource?

`Resource` adalah wadah data yang dapat disimpan sebagai file (`.tres`) dan diedit di Inspector. Dengan Resource, Anda memisahkan **data** (statistik, teks, harga) dari **logika** (kode). Hasilnya: balancing game bisa dilakukan tanpa menyentuh kode, dan desainer (atau Anda di kemudian hari) bisa mengubah data dengan cepat.

### 5.2 Contoh: data item

`scripts/resources/item_data.gd`:

```gdscript
class_name ItemData
extends Resource

enum Kategori { SENJATA, ARMOR, KONSUMSI, KUNCI, LORE }

@export var id: StringName
@export var nama: String
@export_multiline var deskripsi: String
@export var ikon: Texture2D
@export var kategori: Kategori = Kategori.KONSUMSI
@export var harga: int = 0
@export var bisa_ditumpuk: bool = true
@export var maks_tumpukan: int = 99
```

Buat file item lewat **klik kanan di FileSystem > New Resource > ItemData**, simpan sebagai `data/items/potion_kecil.tres`, lalu isi di Inspector.

### 5.3 Contoh: data musuh

```gdscript
class_name EnemyData
extends Resource

@export var id: StringName
@export var nama: String
@export var max_health: int = 3
@export var move_speed: float = 60.0
@export var contact_damage: int = 1
@export var detect_range: float = 120.0
@export var xp_reward: int = 5
@export var drop_table: Array[DropEntry] = []
```

```gdscript
class_name DropEntry
extends Resource

@export var item: ItemData
@export_range(0.0, 1.0, 0.01) var chance: float = 0.25
@export var min_amount: int = 1
@export var max_amount: int = 1
```

Pemakaian di musuh:

```gdscript
class_name Enemy
extends CharacterBody2D

@export var data: EnemyData

func _ready() -> void:
	$HealthComponent.max_health = data.max_health
	$HealthComponent.current_health = data.max_health
```

Satu scene `Slime` dapat menjadi `Slime Hijau`, `Slime Api`, dan `Slime Es` hanya dengan mengganti `EnemyData`.

### 5.4 Resource dibagi bersama (shared)

Perhatian penting: ketika beberapa node memakai file `.tres` yang sama, mereka berbagi **satu objek yang sama**. Jika Anda mengubah nilainya lewat kode saat game berjalan (misalnya `data.max_health -= 1`), semua musuh yang memakai data itu ikut berubah.

Solusinya:

- Perlakukan Resource sebagai data baca-saja (immutable) saat runtime. Simpan nilai berubah (seperti darah saat ini) di node, bukan di Resource.
- Atau buat salinan unik dengan `data.duplicate()` jika benar-benar perlu mengubahnya.
- Atau aktifkan "Local to Scene" untuk resource yang memang harus unik per instance.

### 5.5 Registry (daftar semua data)

Agar bisa mencari item berdasarkan `id`, buat registry sederhana:

```gdscript
# scripts/autoload/item_db.gd
extends Node

var _items: Dictionary = {}  # StringName -> ItemData

func _ready() -> void:
	_scan("res://data/items/")

func _scan(folder: String) -> void:
	var dir := DirAccess.open(folder)
	if dir == null:
		push_warning("Folder tidak ditemukan: " + folder)
		return
	for file in dir.get_files():
		# Setelah ekspor, file dapat berakhiran .tres.remap
		var nama := file.trim_suffix(".remap")
		if nama.ends_with(".tres"):
			var item := load(folder + nama) as ItemData
			if item:
				_items[item.id] = item

func get_item(id: StringName) -> ItemData:
	return _items.get(id)
```

Perhatikan trik `.remap`: pada game yang sudah diekspor, resource di `res://` bisa muncul dengan akhiran `.remap`. Kode di atas menanganinya. Ini jebakan klasik: pemindai folder bekerja di editor tetapi gagal di build ekspor jika tidak menangani hal ini.

### 5.6 Latihan Bab 5

1. Buat `ItemData` untuk 3 item dan `ItemDB` yang memuatnya.
2. Buat 3 varian musuh dari satu scene dengan `EnemyData` berbeda.

---

## Bab 6. State Machine

### 6.1 Mengapa state machine?

Karakter punya banyak keadaan: diam, lari, lompat, jatuh, menyerang, terluka, mati. Tanpa struktur, kode berubah menjadi rangkaian `if` raksasa yang saling bertabrakan. State machine memastikan **hanya satu state aktif**, dan tiap state hanya berisi logika miliknya sendiri.

### 6.2 State machine berbasis node

Kelas dasar `State`:

```gdscript
# scripts/state_machine/state.gd
class_name State
extends Node

signal transition_requested(next_state: StringName)

# Diisi oleh StateMachine; aktor = node pemilik (mis. Player atau Enemy)
var actor: Node

func enter(_previous: StringName) -> void:
	pass

func exit() -> void:
	pass

func handle_input(_event: InputEvent) -> void:
	pass

func update(_delta: float) -> void:
	pass

func physics_update(_delta: float) -> void:
	pass
```

`StateMachine`:

```gdscript
# scripts/state_machine/state_machine.gd
class_name StateMachine
extends Node

@export var initial_state: State

var current_state: State
var _states: Dictionary = {}  # StringName -> State

func _ready() -> void:
	# Tunggu pemilik siap agar referensi node lain aman dipakai.
	await owner.ready
	for child in get_children():
		if child is State:
			var s := child as State
			_states[StringName(s.name.to_lower())] = s
			s.actor = owner
			s.transition_requested.connect(_on_transition_requested)
	if initial_state:
		current_state = initial_state
		current_state.enter(&"")

func _unhandled_input(event: InputEvent) -> void:
	if current_state:
		current_state.handle_input(event)

func _process(delta: float) -> void:
	if current_state:
		current_state.update(delta)

func _physics_process(delta: float) -> void:
	if current_state:
		current_state.physics_update(delta)

func _on_transition_requested(next_state: StringName) -> void:
	var target: State = _states.get(next_state)
	if target == null:
		push_warning("State tidak ditemukan: %s" % next_state)
		return
	var previous := StringName(current_state.name.to_lower()) if current_state else &""
	if current_state:
		current_state.exit()
	current_state = target
	current_state.enter(previous)
```

Catatan: pada kode di atas, nama node state (misalnya `Idle`) diubah menjadi huruf kecil (`idle`) sebagai kunci. Jadi saat meminta transisi, tulis `&"idle"`, `&"run"`, dan seterusnya, semuanya huruf kecil.

### 6.3 Contoh state untuk pemain

```gdscript
# scripts/state_machine/player_idle.gd
extends State

func enter(_previous: StringName) -> void:
	(actor as Player).play_anim(&"idle")

func physics_update(_delta: float) -> void:
	var p := actor as Player
	p.apply_gravity(_delta)
	p.apply_friction(_delta)
	p.move_and_slide()

	if not p.is_on_floor():
		transition_requested.emit(&"fall")
	elif Input.is_action_just_pressed(&"jump"):
		transition_requested.emit(&"jump")
	elif absf(Input.get_axis(&"move_left", &"move_right")) > 0.1:
		transition_requested.emit(&"run")
```

Struktur scene pemain:

```text
Player (CharacterBody2D) [player.gd]
  AnimatedSprite2D
  CollisionShape2D
  Hurtbox
  StateMachine [state_machine.gd]
    Idle [player_idle.gd]
    Run [player_run.gd]
    Jump [player_jump.gd]
    Fall [player_fall.gd]
    Attack [player_attack.gd]
    Hurt [player_hurt.gd]
    Dead [player_dead.gd]
```

### 6.4 Kapan memakai apa

- **Enum + `match`**: untuk state machine kecil (3 sampai 5 state), cukup dan lebih sederhana.
- **State machine berbasis node**: untuk karakter kompleks, mudah dikembangkan, tiap state punya file sendiri.
- **AnimationTree state machine**: khusus untuk mengatur transisi animasi (Bab 10), bukan menggantikan logika gameplay.

Versi sederhana dengan enum:

```gdscript
enum Keadaan { DIAM, KEJAR, SERANG, TERLUKA }
var keadaan: Keadaan = Keadaan.DIAM

func _physics_process(delta: float) -> void:
	match keadaan:
		Keadaan.DIAM:
			_proses_diam(delta)
		Keadaan.KEJAR:
			_proses_kejar(delta)
		Keadaan.SERANG:
			_proses_serang(delta)
		Keadaan.TERLUKA:
			_proses_terluka(delta)
```

### 6.5 Kesalahan umum

- Transisi dipicu dua kali dalam satu frame. Pastikan setelah `transition_requested.emit(...)` Anda tidak melanjutkan logika lain yang bergantung pada state lama (pakai `return`).
- State saling memanggil `enter` satu sama lain secara langsung. Biarkan hanya `StateMachine` yang mengatur peralihan.

### 6.6 Latihan Bab 6

Buat state `Idle`, `Run`, `Jump`, `Fall` untuk pemain, lalu tambahkan `Attack` yang kembali ke `Idle` setelah animasi selesai.

---

## Bab 7. Player Controller yang "Terasa Enak"

Di game aksi, **game feel** (rasa kontrol) menentukan apakah game terasa profesional atau kaku. Perbedaannya sering hanya soal beberapa trik kecil.

### 7.1 Trik-trik penting

1. **Akselerasi dan gesekan**: karakter tidak langsung berkecepatan penuh atau berhenti total.
2. **Coyote time**: pemain masih boleh melompat sesaat (sekitar 0,08 sampai 0,12 detik) setelah meninggalkan tepi platform. Terasa adil.
3. **Jump buffer**: jika pemain menekan lompat sesaat sebelum mendarat, lompatan dieksekusi saat menyentuh tanah. Terasa responsif.
4. **Variable jump height**: lompat lebih tinggi jika tombol ditahan, lebih rendah jika dilepas cepat.
5. **Gravitasi berbeda saat jatuh**: jatuh sedikit lebih cepat daripada naik, agar lompatan terasa "berbobot".
6. **Corner correction** dan **ledge forgiveness**: toleransi kecil di sudut agar pemain tidak "tersangkut".

### 7.2 Kode platformer lengkap

```gdscript
class_name Player
extends CharacterBody2D

@export_group("Gerak")
@export var max_speed: float = 180.0
@export var acceleration: float = 1400.0
@export var friction: float = 1800.0
@export var air_control: float = 0.8   # pengali akselerasi di udara

@export_group("Lompat")
@export var jump_velocity: float = -360.0
@export var coyote_time: float = 0.10
@export var jump_buffer_time: float = 0.12
@export var jump_cut_multiplier: float = 0.5
@export var fall_gravity_multiplier: float = 1.4
@export var max_fall_speed: float = 520.0

var _gravity: float = ProjectSettings.get_setting("physics/2d/default_gravity")
var _coyote_timer: float = 0.0
var _buffer_timer: float = 0.0

func _physics_process(delta: float) -> void:
	_update_timers(delta)
	_apply_gravity(delta)
	_handle_horizontal(delta)
	_handle_jump()
	move_and_slide()

func _update_timers(delta: float) -> void:
	if is_on_floor():
		_coyote_timer = coyote_time
	else:
		_coyote_timer -= delta

	if Input.is_action_just_pressed(&"jump"):
		_buffer_timer = jump_buffer_time
	else:
		_buffer_timer -= delta

func _apply_gravity(delta: float) -> void:
	if is_on_floor():
		return
	var g := _gravity
	if velocity.y > 0.0:
		g *= fall_gravity_multiplier
	velocity.y = minf(velocity.y + g * delta, max_fall_speed)

func _handle_horizontal(delta: float) -> void:
	var dir := Input.get_axis(&"move_left", &"move_right")
	var accel := acceleration
	if not is_on_floor():
		accel *= air_control

	if absf(dir) > 0.01:
		velocity.x = move_toward(velocity.x, dir * max_speed, accel * delta)
		$AnimatedSprite2D.flip_h = dir < 0.0
	else:
		velocity.x = move_toward(velocity.x, 0.0, friction * delta)

func _handle_jump() -> void:
	if _buffer_timer > 0.0 and _coyote_timer > 0.0:
		velocity.y = jump_velocity
		_buffer_timer = 0.0
		_coyote_timer = 0.0

	# Lompat variabel: lepas tombol saat naik, potong kecepatan
	if Input.is_action_just_released(&"jump") and velocity.y < 0.0:
		velocity.y *= jump_cut_multiplier
```

Penjelasan singkat bagian penting:

- `move_toward(a, b, langkah)` menggeser `a` menuju `b` sebesar `langkah`. Ini cara termudah membuat akselerasi dan gesekan yang mulus.
- `_coyote_timer` di-reset penuh saat di lantai, lalu berkurang saat di udara. Selama masih positif, lompat diizinkan.
- `_buffer_timer` mulai saat tombol ditekan dan berkurang tiap frame. Jika pemain mendarat sebelum habis, lompat terjadi.
- Memotong `velocity.y` saat tombol dilepas menghasilkan lompat pendek.

Mengapa `_physics_process`? Gerak fisika harus dilakukan di sini agar konsisten dengan tick fisika (default 60 per detik) dan tidak bergantung pada frame rate.

### 7.3 Dash

```gdscript
@export var dash_speed: float = 420.0
@export var dash_duration: float = 0.14
@export var dash_cooldown: float = 0.5

var _dash_time_left: float = 0.0
var _dash_cooldown_left: float = 0.0
var _dash_dir: float = 1.0

func try_dash() -> void:
	if _dash_cooldown_left > 0.0:
		return
	_dash_dir = signf(Input.get_axis(&"move_left", &"move_right"))
	if _dash_dir == 0.0:
		_dash_dir = -1.0 if $AnimatedSprite2D.flip_h else 1.0
	_dash_time_left = dash_duration
	_dash_cooldown_left = dash_cooldown

func _process_dash(delta: float) -> bool:
	_dash_cooldown_left = maxf(_dash_cooldown_left - delta, 0.0)
	if _dash_time_left > 0.0:
		_dash_time_left -= delta
		velocity = Vector2(_dash_dir * dash_speed, 0.0)  # abaikan gravitasi saat dash
		return true
	return false
```

Dalam arsitektur state machine, dash lebih bersih sebagai state `Dash` tersendiri.

### 7.4 Top-down (gerak 8 arah)

```gdscript
extends CharacterBody2D

@export var speed: float = 120.0
@export var accel: float = 900.0
@export var friction: float = 1100.0

func _physics_process(delta: float) -> void:
	var input := Input.get_vector(&"move_left", &"move_right", &"move_up", &"move_down")
	if input != Vector2.ZERO:
		velocity = velocity.move_toward(input * speed, accel * delta)
	else:
		velocity = velocity.move_toward(Vector2.ZERO, friction * delta)
	move_and_slide()
```

`Input.get_vector` otomatis menormalkan input diagonal dan menangani deadzone gamepad, sehingga gerak diagonal tidak lebih cepat.

Untuk top-down, ubah `Motion Mode` di Inspector `CharacterBody2D` menjadi `Floating` agar tidak ada konsep lantai dan dinding ala platformer.

### 7.5 Kesalahan umum

- Mengalikan `velocity` dengan `delta` sebelum `move_and_slide()`. `move_and_slide()` sudah memakai `delta` secara internal. Jangan dikalikan lagi.
- Memakai `_process` untuk gerak fisika. Pakai `_physics_process`.
- Mengubah `position` langsung pada `CharacterBody2D` sehingga tumbukan terlewati.

### 7.6 Latihan Bab 7

Tambahkan fitur coyote time dan jump buffer pada proyek Anda, lalu uji dengan mengubah nilainya (0, 0.05, 0.15). Rasakan perbedaannya.

---

## Bab 8. Fisika 2D Lanjutan, Hitbox, dan Hurtbox

### 8.1 Jenis body fisika di Godot 2D

|Node|Dipakai untuk|
|---|---|
|`CharacterBody2D`|Karakter yang digerakkan lewat kode (pemain, musuh).|
|`StaticBody2D`|Objek diam (tanah, dinding).|
|`RigidBody2D`|Objek yang diatur mesin fisika (kotak, bola).|
|`AnimatableBody2D`|Platform bergerak.|
|`Area2D`|Zona deteksi (hitbox, pickup, trigger). Tidak menahan gerak.|

### 8.2 Layer dan mask

Setiap objek punya dua pengaturan:

- **Layer**: "Saya berada di layer berapa?"
- **Mask**: "Saya mendeteksi layer berapa?"

Contoh: hitbox pedang pemain berada di layer `player_hitbox` dan memiliki mask `enemy_hurtbox`. Hurtbox musuh berada di layer `enemy_hurtbox`. Maka pedang hanya mengenai musuh, tidak mengenai pemain sendiri.

Pengaturan layer dan mask yang benar jauh lebih baik daripada memeriksa `if body.is_in_group(...)` di mana-mana.

### 8.3 Hitbox dan Hurtbox

- **Hitbox**: area yang menyakiti (misalnya bilah pedang).
- **Hurtbox**: area yang bisa disakiti (tubuh karakter).

```gdscript
# scripts/components/hitbox.gd
class_name Hitbox
extends Area2D

@export var damage: int = 1
@export var knockback_force: float = 220.0
```

```gdscript
# scripts/components/hurtbox.gd
class_name Hurtbox
extends Area2D

signal hit_received(hitbox: Hitbox)

@export var invincibility_time: float = 0.6

var _invincible: bool = false

func _ready() -> void:
	area_entered.connect(_on_area_entered)

func _on_area_entered(area: Area2D) -> void:
	if _invincible:
		return
	if area is Hitbox:
		hit_received.emit(area as Hitbox)
		if invincibility_time > 0.0:
			_start_invincibility()

func _start_invincibility() -> void:
	_invincible = true
	await get_tree().create_timer(invincibility_time).timeout
	_invincible = false
```

Menghubungkan ke karakter:

```gdscript
# di player.gd atau enemy.gd
@onready var hurtbox: Hurtbox = $Hurtbox
@onready var health: HealthComponent = $HealthComponent

func _ready() -> void:
	hurtbox.hit_received.connect(_on_hit_received)

func _on_hit_received(hitbox: Hitbox) -> void:
	health.take_damage(hitbox.damage)
	var arah := (global_position - hitbox.global_position).normalized()
	velocity = arah * hitbox.knockback_force
```

### 8.4 Mengaktifkan dan menonaktifkan hitbox dengan aman

Perubahan pada bentuk tumbukan saat fisika sedang diproses harus ditunda, kalau tidak Godot akan memberi error ("Can't change this state while flushing queries").

Salah:

```gdscript
$Hitbox/CollisionShape2D.disabled = true
```

Benar saat berada di dalam callback fisika (misalnya `area_entered`):

```gdscript
$Hitbox/CollisionShape2D.set_deferred("disabled", true)
```

Biasanya hitbox pedang diaktifkan hanya pada frame tertentu dari animasi serangan, menggunakan **Call Method Track** atau **Property Track** pada `AnimationPlayer` (Bab 10).

### 8.5 RayCast2D dan ShapeCast2D

`RayCast2D` memancarkan garis untuk mendeteksi tabrakan. Contoh umum:

- Cek apakah ada lantai di depan musuh (agar tidak jatuh dari tebing).
- Cek apakah ada dinding di depan.
- Garis pandang (line of sight) untuk musuh pengintai.

```gdscript
@onready var ledge_check: RayCast2D = $LedgeCheck
@onready var wall_check: RayCast2D = $WallCheck

func _physics_process(delta: float) -> void:
	if not ledge_check.is_colliding() or wall_check.is_colliding():
		_balik_arah()
```

Raycast diperbarui setiap tick fisika. Jika Anda mengubah posisinya lalu langsung membaca hasilnya dalam frame yang sama, panggil `force_raycast_update()`.

### 8.6 One-way platform

Pada `CollisionShape2D` platform, aktifkan `One Way Collision`. Pemain bisa melompat dari bawah dan berdiri di atasnya. Untuk turun menembus:

```gdscript
if Input.is_action_just_pressed(&"move_down") and is_on_floor():
	position.y += 1  # sedikit geser agar lepas dari platform satu arah
```

Pendekatan lebih rapi: pakai layer khusus untuk platform satu arah, dan matikan mask pada layer itu selama sesaat saat pemain menekan bawah.

### 8.7 Fisika dan interpolasi

Jika tick fisika (60 Hz) berbeda dengan refresh rate monitor (misalnya 144 Hz), gerak bisa terlihat patah-patah. Godot 4 menyediakan **physics interpolation** (aktifkan di Project Settings > Physics > Common). Fitur ini menghaluskan gerak visual di antara tick fisika. Uji pada proyek Anda, karena perilakunya dapat berinteraksi dengan kamera dan teleportasi (untuk teleportasi, panggil `reset_physics_interpolation()` pada node tersebut agar tidak "meluncur" aneh).

### 8.8 Latihan Bab 8

1. Buat `Hitbox` dan `Hurtbox` lalu uji pemain menyerang slime.
2. Tambahkan waktu kebal (i-frame) setelah pemain terkena serangan, dengan efek kedip.

---

## Bab 9. Combat, Musuh, dan AI

### 9.1 Health component lengkap

```gdscript
class_name HealthComponent
extends Node

signal health_changed(current: int, maximum: int)
signal damaged(amount: int)
signal healed(amount: int)
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
	if current_health <= 0:
		return
	var sebelum := current_health
	current_health = mini(current_health + amount, max_health)
	healed.emit(current_health - sebelum)
	health_changed.emit(current_health, max_health)
```

### 9.2 Game juice: umpan balik serangan

"Juice" adalah umpan balik visual dan audio yang membuat aksi terasa memuaskan. Untuk satu pukulan yang mengenai, kombinasikan:

1. **Hitstop**: jeda sangat singkat (0,04 sampai 0,08 detik).
2. **Screen shake**: guncangan kamera kecil.
3. **Flash putih** pada musuh.
4. **Knockback** (terpental).
5. **Partikel** dan **SFX** benturan.

Hitstop sederhana:

```gdscript
# scripts/autoload/game_feel.gd
extends Node

func hitstop(durasi: float = 0.06, skala: float = 0.05) -> void:
	Engine.time_scale = skala
	# Argumen: waktu, process_always, process_in_physics, ignore_time_scale
	await get_tree().create_timer(durasi, true, false, true).timeout
	Engine.time_scale = 1.0
```

Argumen keempat (`ignore_time_scale = true`) penting. Tanpa itu, timer ikut melambat dan hitstop terasa jauh lebih lama dari seharusnya.

Camera shake berbasis "trauma":

```gdscript
class_name ShakeCamera
extends Camera2D

@export var decay: float = 1.6
@export var max_offset: Vector2 = Vector2(10.0, 8.0)

var _trauma: float = 0.0

func _ready() -> void:
	EventBus.screen_shake_requested.connect(add_trauma)

func add_trauma(amount: float) -> void:
	_trauma = clampf(_trauma + amount, 0.0, 1.0)

func _process(delta: float) -> void:
	if _trauma > 0.0:
		_trauma = maxf(_trauma - decay * delta, 0.0)
		var kekuatan := _trauma * _trauma  # kuadrat agar guncangan kecil terasa halus
		offset = Vector2(
			randf_range(-1.0, 1.0) * max_offset.x,
			randf_range(-1.0, 1.0) * max_offset.y
		) * kekuatan
	else:
		offset = Vector2.ZERO
```

Berikan opsi di menu pengaturan untuk mengurangi atau mematikan screen shake (aksesibilitas, lihat Bab 15).

### 9.3 AI musuh dengan state machine

Pola dasar musuh patroli:

```gdscript
# scripts/state_machine/enemy_patrol.gd
extends State

@export var speed: float = 40.0
var _dir: float = 1.0

func physics_update(delta: float) -> void:
	var e := actor as Enemy
	e.velocity.x = _dir * speed
	e.apply_gravity(delta)
	e.move_and_slide()

	if e.is_on_wall() or not e.ledge_check_has_floor():
		_dir *= -1.0
		e.flip(_dir)

	if e.can_see_player():
		transition_requested.emit(&"chase")
```

Musuh yang menarik biasanya punya **tell** (tanda sebelum menyerang): animasi aba-aba 0,3 sampai 0,5 detik sebelum serangan. Ini membuat pemain merasa kalah karena kesalahan sendiri, bukan karena game curang. Itu inti dari pertarungan yang adil.

### 9.4 Navigasi dengan NavigationAgent2D

Untuk musuh yang mengejar melewati labirin atau rintangan:

1. Tambahkan `NavigationRegion2D` ke level dan buat `NavigationPolygon` yang menutupi area yang bisa dilalui.
2. Pada musuh, tambahkan `NavigationAgent2D`.
3. Gunakan kode berikut:

```gdscript
@onready var nav: NavigationAgent2D = $NavigationAgent2D
@export var speed: float = 70.0

func _ready() -> void:
	# Tunggu satu tick fisika agar peta navigasi selesai tersinkron.
	await get_tree().physics_frame
	nav.target_position = _player().global_position

func _physics_process(_delta: float) -> void:
	if nav.is_navigation_finished():
		return
	var next_pos := nav.get_next_path_position()
	var arah := (next_pos - global_position).normalized()
	velocity = arah * speed
	move_and_slide()

func _on_repath_timer_timeout() -> void:
	# Perbarui target secara berkala, bukan setiap frame (hemat CPU).
	nav.target_position = _player().global_position

func _player() -> Node2D:
	return get_tree().get_first_node_in_group(&"player")
```

Tips:

- Perbarui target tiap 0,2 sampai 0,5 detik memakai `Timer`, bukan setiap frame.
- Jika banyak agen, aktifkan avoidance pada `NavigationAgent2D` dan gunakan sinyal `velocity_computed`.
- Untuk platformer, navigasi 2D berbasis poligon kurang cocok. Gunakan AI berbasis state, raycast, dan titik patroli.

### 9.5 Boss

Boss adalah state machine yang lebih besar dengan **fase**. Rancang boss seperti ini:

- Daftar serangan (3 sampai 5), masing-masing dengan tell yang jelas.
- Fase berubah berdasarkan persentase darah (misalnya 100%, 60%, 25%).
- Jeda "kesempatan membalas" setelah serangan besar.
- Data fase disimpan di Resource agar mudah diatur.

```gdscript
class_name BossPhase
extends Resource

@export_range(0.0, 1.0, 0.01) var health_threshold: float = 1.0
@export var attack_ids: Array[StringName] = []
@export var speed_multiplier: float = 1.0
@export var attack_interval: float = 2.0
```

### 9.6 Keseimbangan (balancing)

- Mulai dari angka sederhana dan catat dalam spreadsheet: darah pemain, damage rata-rata, darah musuh, jumlah pukulan untuk mengalahkan musuh.
- Tujuan umum: musuh biasa mati dalam 2 sampai 4 pukulan, pemain bertahan 4 sampai 6 pukulan musuh. Sesuaikan dengan genre Anda.
- Uji dengan orang lain (playtest). Perhatikan di mana mereka mati berulang kali.

### 9.7 Latihan Bab 9

Buat satu musuh dengan state `Patrol`, `Chase`, `Attack` (dengan tell), `Hurt`, dan `Dead`. Tambahkan hitstop dan screen shake saat pemain memukulnya.

---

## Bab 10. Animasi Lanjutan

### 10.1 Tiga alat animasi 2D utama

1. **AnimatedSprite2D**: memutar rangkaian frame (sprite sheet). Sederhana, bagus untuk animasi pixel art per frame.
2. **AnimationPlayer**: menganimasikan properti apa pun (posisi, warna, visibilitas, bahkan memanggil fungsi). Paling fleksibel.
3. **AnimationTree**: mengatur transisi dan pencampuran animasi dengan state machine atau blend space.

### 10.2 Menggabungkan AnimatedSprite2D dan AnimationPlayer

Pendekatan populer: pakai `Sprite2D` dengan `Hframes`/`Vframes` (atau `AnimatedSprite2D`), lalu animasikan properti `frame` lewat `AnimationPlayer`. Keuntungannya, pada timeline yang sama Anda bisa menganimasikan hitbox, memutar SFX, dan memanggil fungsi pada frame tertentu.

Contoh animasi serangan (`attack`) di `AnimationPlayer`:

- Track `Sprite2D:frame`: frame 0 sampai 5.
- Track `Hitbox/CollisionShape2D:disabled`: `true` pada 0,00 s; `false` pada 0,15 s; `true` lagi pada 0,25 s.
- Track `AudioStreamPlayer2D`: putar bunyi tebasan pada 0,12 s.
- Call Method Track: panggil `_on_attack_end()` di akhir.

Dengan begini hitbox aktif tepat pada frame yang terlihat mengenai musuh, sehingga serangan terasa akurat. Jika Anda menganimasikan `disabled` lewat Property Track, pengubahan terjadi dengan aman terhadap fisika.

### 10.3 Memutar animasi dengan aman

```gdscript
func play_anim(nama: StringName) -> void:
	if $AnimationPlayer.current_animation != nama:
		$AnimationPlayer.play(nama)
```

Tanpa pengecekan, memanggil `play` pada animasi yang sama setiap frame akan mengulang animasi dari awal sehingga tampak macet.

### 10.4 AnimationTree

Gunakan `AnimationTree` ketika ada banyak animasi yang bertransisi kompleks, atau ketika butuh blending (misalnya jalan menjadi lari berdasarkan kecepatan, atau 4/8 arah pada game top-down).

Langkah dasar:

1. Tambahkan node `AnimationTree`, atur `Anim Player` ke `AnimationPlayer` Anda.
2. Atur `Tree Root` menjadi `AnimationNodeStateMachine` atau `AnimationNodeBlendSpace2D`.
3. Aktifkan `Active`.
4. Kendalikan lewat kode:

```gdscript
@onready var anim_tree: AnimationTree = $AnimationTree
@onready var playback: AnimationNodeStateMachinePlayback = anim_tree.get("parameters/playback")

func _physics_process(_delta: float) -> void:
	# Contoh BlendSpace2D untuk top-down
	var arah := Input.get_vector(&"move_left", &"move_right", &"move_up", &"move_down")
	if arah != Vector2.ZERO:
		anim_tree.set("parameters/Walk/blend_position", arah)
		anim_tree.set("parameters/Idle/blend_position", arah)
		playback.travel(&"Walk")
	else:
		playback.travel(&"Idle")
```

Saran: untuk game 2D dengan skala kecil, `AnimationPlayer` + state machine kode Anda sudah cukup. `AnimationTree` bagus bila animasi Anda banyak dan transisinya rumit. Jangan memakai dua state machine yang bersaing mengontrol hal yang sama.

### 10.5 Tween untuk animasi lewat kode

`Tween` cocok untuk efek singkat yang dibuat saat runtime (muncul, memudar, memantul).

```gdscript
func efek_muncul() -> void:
	scale = Vector2.ZERO
	var tw := create_tween().set_trans(Tween.TRANS_BACK).set_ease(Tween.EASE_OUT)
	tw.tween_property(self, "scale", Vector2.ONE, 0.25)

func efek_kedip(kali: int = 4) -> void:
	var tw := create_tween()
	for i in kali:
		tw.tween_property($Sprite2D, "modulate:a", 0.2, 0.05)
		tw.tween_property($Sprite2D, "modulate:a", 1.0, 0.05)
```

Catatan: `Tween` bersifat sekali pakai dan tidak bisa dipakai ulang setelah selesai. Buat tween baru setiap kali. Matikan tween lama dengan `tw.kill()` bila akan membuat yang baru pada properti yang sama.

### 10.6 Prinsip animasi untuk game feel

- **Anticipation**: gerakan awal sebelum aksi (menarik pedang ke belakang).
- **Squash and stretch**: tubuh memipih saat mendarat, memanjang saat melompat. Cukup lewat `scale` dengan tween singkat.
- **Frame hitung**: serangan cepat biasanya 3 sampai 6 frame aktif. Jangan membuat semua animasi terlalu panjang.
- **Prioritas respons**: animasi tidak boleh menghalangi input terlalu lama (misalnya pemain tak bisa lompat selama 0,5 detik karena menunggu animasi mendarat). Izinkan animasi dibatalkan (cancel).

### 10.7 Latihan Bab 10

Buat animasi `attack` pada `AnimationPlayer` yang mengaktifkan hitbox hanya pada frame ayunan, lalu tambahkan squash and stretch saat mendarat.

---

## Bab 11. Level Design: TileMapLayer, Kamera, dan Transisi Ruangan

### 11.1 TileMapLayer

Sejak Godot 4.3, node `TileMap` lama digantikan oleh `TileMapLayer`. Satu `TileMapLayer` mewakili satu lapisan. Untuk beberapa lapisan (tanah, dekorasi, latar), gunakan beberapa node `TileMapLayer`. Jika Anda menemukan tutorial lama yang memakai `TileMap`, ketahuilah bahwa node itu sudah ditandai usang (deprecated) dan sebaiknya tidak dipakai untuk proyek baru.

Struktur level yang disarankan:

```text
Level01 (Node2D)
  Background (ParallaxBackground atau Parallax2D)
  Ground (TileMapLayer)      # tumbukan
  Decoration (TileMapLayer)  # tanpa tumbukan
  Foreground (TileMapLayer)  # di depan pemain
  Entities (Node2D)
    Player
    Enemies
    Pickups
  SpawnPoints (Node2D)
  Camera
```

### 11.2 TileSet: fitur yang wajib dikuasai

Buat resource `TileSet` dan atur:

- **Physics Layer**: untuk tumbukan per tile.
- **Terrain Sets**: autotile. Anda menggambar area, dan tepi serta sudut dipilih otomatis. Menghemat waktu sangat besar.
- **Custom Data Layers**: data tambahan per tile, misalnya `jenis_permukaan` (rumput, batu, air) untuk memilih bunyi langkah, atau `damage` untuk duri.
- **Navigation Layer**: untuk area yang bisa dilewati.
- **Scene Collection**: menaruh scene utuh sebagai tile (misalnya obor dengan partikel, peti, atau pintu), memadukan kemudahan menggambar tile dengan fleksibilitas scene.

Membaca data custom tile (misalnya untuk bunyi langkah):

```gdscript
func permukaan_di_bawah(tilemap: TileMapLayer, posisi_dunia: Vector2) -> StringName:
	var sel := tilemap.local_to_map(tilemap.to_local(posisi_dunia))
	var data := tilemap.get_cell_tile_data(sel)
	if data:
		return data.get_custom_data("jenis_permukaan")
	return &"default"
```

### 11.3 Kamera 2D yang baik

Properti `Camera2D` penting:

- `Position Smoothing`: kamera mengikuti dengan halus.
- `Limit Left/Right/Top/Bottom`: batas level agar kamera tidak menampilkan area kosong.
- `Drag Margin`: zona mati di tengah layar.
- `Zoom`: untuk pixel art, gunakan zoom bilangan bulat agar tajam.

Trik look-ahead (kamera sedikit mendahului arah gerak):

```gdscript
extends Camera2D

@export var target: Node2D
@export var look_ahead: float = 40.0
@export var look_speed: float = 4.0

var _offset_x: float = 0.0

func _physics_process(delta: float) -> void:
	if target == null:
		return
	var arah := signf(target.velocity.x) if "velocity" in target else 0.0
	_offset_x = lerpf(_offset_x, arah * look_ahead, look_speed * delta)
	global_position = target.global_position + Vector2(_offset_x, 0.0)
```

Jika Anda menggerakkan kamera dengan kode sendiri sementara `Position Smoothing` aktif, hasilnya bisa saling bertabrakan. Pilih salah satu.

### 11.4 Transisi ruangan (gaya Metroidvania)

Pola yang umum: tiap ruangan adalah scene sendiri, dan pintu atau tepi layar memicu perpindahan ke ruangan lain di titik spawn tertentu.

```gdscript
# scenes/components/room_exit.gd
class_name RoomExit
extends Area2D

@export_file("*.tscn") var target_level: String
@export var target_spawn: StringName = &"default"

func _ready() -> void:
	body_entered.connect(_on_body_entered)

func _on_body_entered(body: Node2D) -> void:
	if body.is_in_group(&"player"):
		EventBus.level_change_requested.emit(target_level, target_spawn)
```

Gunakan `@export_file` agar Anda memilih file scene lewat Inspector, bukan mengetik path manual yang rawan salah ketik.

Tips level design untuk gameplay-first:

- **Teach, test, twist**: perkenalkan mekanik di tempat aman, uji dengan tantangan ringan, lalu beri variasi menantang.
- **Gunakan komposisi visual** untuk menuntun mata pemain ke arah tujuan (cahaya, warna, garis).
- **Checkpoint** yang adil. Jangan menghukum pemain dengan harus mengulang 5 menit hanya karena satu kesalahan.
- **Prototipe kotak abu-abu (graybox)** dulu. Pastikan level seru dengan kotak polos sebelum memoles seni.

### 11.5 Streaming level dan pemuatan di latar

Level besar bisa lambat dimuat. Gunakan pemuatan berulir:

```gdscript
func muat_level_async(path: String) -> void:
	ResourceLoader.load_threaded_request(path)
	while true:
		var progres: Array = []
		var status := ResourceLoader.load_threaded_get_status(path, progres)
		if status == ResourceLoader.THREAD_LOAD_LOADED:
			break
		if status == ResourceLoader.THREAD_LOAD_FAILED:
			push_error("Gagal memuat " + path)
			return
		# progres[0] bernilai 0.0 sampai 1.0, bisa dipakai untuk bar loading
		await get_tree().process_frame
	var scene := ResourceLoader.load_threaded_get(path) as PackedScene
	get_tree().change_scene_to_packed(scene)
```

Untuk game 2D berukuran kecil, `change_scene_to_file` biasa sering sudah cukup cepat. Optimalkan hanya bila ada jeda yang terasa.

### 11.6 Latihan Bab 11

Buat 3 ruangan yang tersambung lewat `RoomExit`, dengan `TileMapLayer` bertumbukan dan kamera dengan batas level.

---

## Bab 12. Cerita dan Lore Tanpa Voice Actor

### 12.1 Cerita sebagai pelayan gameplay

Karena fokus kita gameplay, cerita ditulis dengan aturan berikut:

1. **Hook di 5 menit pertama**: satu pertanyaan misterius yang membuat pemain penasaran ("Mengapa kota ini sunyi?").
2. **Cerita bisa dilewati, lore bisa digali**: jalur utama pendek dan jelas; kedalaman ada di opsional.
3. **Pemain adalah pengamat aktif**: lore ditemukan, bukan dipaksa dibaca.
4. **Tema selaras dengan mekanik**: jika temanya "ingatan yang memudar", mekaniknya bisa tentang kehilangan kemampuan seiring waktu.

### 12.2 Teknik penyampaian cerita tanpa suara pengisi

Tanpa voice actor, Anda punya banyak alat yang murah tetapi kuat:

**1. Environmental storytelling (cerita lewat lingkungan).** Susun adegan yang bercerita: kamp yang ditinggalkan terburu-buru, bekas pertarungan, mural di dinding, kerangka di depan pintu terkunci. Pemain menyimpulkan sendiri apa yang terjadi.

**2. Deskripsi item.** Setiap item punya potongan cerita 1 sampai 3 kalimat. Sistem ini murah dan sangat efektif, serta mudah dilokalisasi (Bab 5).

**3. Catatan, surat, dan prasasti tersebar.** Pemain menemukan dan membaca (opsional). Simpan di Codex/Jurnal agar bisa dibaca ulang.

**4. Dialog teks bergaya.** Gunakan efek ketik (typewriter), bunyi "blip" per huruf yang berbeda per karakter, potret karakter dengan ekspresi, dan jeda dramatis. Ini menggantikan suara pengisi secara efektif dan sudah menjadi gaya klasik (banyak RPG).

**5. Musik dan motif (leitmotif).** Setiap tokoh atau lokasi punya melodi khas. Pemain mengaitkan emosi dengan musik tanpa perlu kata.

**6. Animasi dan bahasa tubuh.** Ekspresi sprite, gestur, dan animasi singkat menyampaikan emosi. Satu animasi "menunduk" bisa menggantikan satu paragraf.

**7. Bahasa fiktif atau gumaman.** Beberapa game memakai bunyi gumaman pendek atau bahasa karangan sebagai pengganti suara. Ini murah dan memberi karakter. Gunakan SFX pendek yang Anda buat atau beli lisensinya.

**8. Sinematik berbasis gambar.** Panel gambar diam dengan pergerakan kamera atau efek paralaks ringan, ditemani musik dan teks.

### 12.3 Struktur dunia (world bible) yang ringan

Buat dokumen `docs/lore.md` yang berisi:

- **Premis dunia**: 1 paragraf.
- **Lokasi utama**: nama, suasana, peran dalam gameplay.
- **Faksi atau tokoh utama**: tujuan, konflik.
- **Garis waktu singkat**: 5 sampai 10 peristiwa besar.
- **Aturan dunia**: apa yang mustahil atau berbeda dari dunia nyata (misalnya cara kerja sihir).
- **Glosarium istilah**: nama-nama khusus, agar konsisten.

Jangan menulis 100 halaman lore sebelum memiliki prototipe yang seru. Tulis seperlunya, tambah secara bertahap.

### 12.4 Pacing: menempatkan cerita di antara aksi

Pola sederhana untuk satu bab (contoh 30 sampai 40 menit):

1. Tempat aman (hub) dengan interaksi singkat dan satu petunjuk cerita.
2. Eksplorasi dan pertarungan (gameplay utama).
3. Penemuan lore opsional di sudut tersembunyi.
4. Boss atau tantangan puncak.
5. Resolusi singkat: adegan pendek yang menggerakkan plot dan membuka area baru.

Hindari menempatkan dua adegan dialog panjang berturut-turut tanpa interaksi. Beri pemain sesuatu untuk dilakukan di antaranya.

### 12.5 Penulisan dialog yang efisien

- Satu kotak dialog sebaiknya tidak lebih dari 2 sampai 3 baris.
- Setiap karakter punya "suara" tulisan yang khas (panjang kalimat, pilihan kata).
- Hindari eksposisi yang berat. Biarkan pemain bertanya lewat pilihan dialog bila tertarik.
- Beri pilihan "lewati" (skip) dan kecepatan teks yang dapat diatur.

### 12.6 Latihan Bab 12

1. Tulis `docs/lore.md` satu halaman untuk dunia game Anda.
2. Tulis deskripsi item untuk 5 item sehingga bersama-sama membocorkan satu rahasia kecil tentang dunia.

---

## Bab 13. Sistem Dialog, Flag, dan Quest

### 13.1 Model data dialog

Gunakan Resource agar dialog bisa diedit di Inspector, dan gunakan **kunci terjemahan** agar mudah dilokalisasi (Bab 18).

```gdscript
# scripts/resources/dialogue_line.gd
class_name DialogueLine
extends Resource

@export var speaker_key: StringName            # kunci nama pembicara, mis. &"NPC_ELDER"
@export var text_key: StringName               # kunci teks, mis. &"DLG_ELDER_001"
@export var portrait: Texture2D
@export var blip_sound: AudioStream
@export var choices: Array[DialogueChoice] = []
@export var set_flag: StringName = &""         # flag yang dinyalakan setelah baris ini
@export var next_index: int = -1               # -1 = lanjut ke baris berikutnya
```

```gdscript
# scripts/resources/dialogue_choice.gd
class_name DialogueChoice
extends Resource

@export var text_key: StringName
@export var next_index: int = -1               # lompat ke baris ini bila dipilih
@export var required_flag: StringName = &""    # pilihan muncul hanya jika flag aktif
```

```gdscript
# scripts/resources/dialogue_data.gd
class_name DialogueData
extends Resource

@export var id: StringName
@export var lines: Array[DialogueLine] = []
```

### 13.2 GameState dan flag cerita

Flag adalah penanda boolean atau nilai yang mencatat apa yang sudah terjadi ("sudah bicara dengan tetua", "boss pertama dikalahkan").

```gdscript
# scripts/autoload/game_state.gd
extends Node

var flags: Dictionary = {}      # StringName -> Variant
var inventory: Dictionary = {}  # StringName -> int
var play_time: float = 0.0

func _process(delta: float) -> void:
	play_time += delta

func set_flag(flag: StringName, value: Variant = true) -> void:
	flags[flag] = value
	EventBus.flag_changed.emit(flag, value)

func has_flag(flag: StringName) -> bool:
	return flags.get(flag, false) == true

func get_flag(flag: StringName, default: Variant = null) -> Variant:
	return flags.get(flag, default)

func add_item(id: StringName, amount: int = 1) -> void:
	inventory[id] = inventory.get(id, 0) + amount
	EventBus.item_picked_up.emit(id, amount)

func to_dict() -> Dictionary:
	return {
		"flags": flags,
		"inventory": inventory,
		"play_time": play_time,
	}

func from_dict(data: Dictionary) -> void:
	flags = data.get("flags", {})
	inventory = data.get("inventory", {})
	play_time = data.get("play_time", 0.0)
```

Catatan teknis tentang JSON: ketika dimuat dari JSON, `StringName` menjadi `String` biasa dan semua angka menjadi `float`. Karena `Dictionary` Godot menganggap `&"flag"` dan `"flag"` setara untuk kunci, ini biasanya aman. Tetapi nilai integer yang dimuat bisa berupa `float`, jadi gunakan `int(nilai)` saat membaca jumlah item.

### 13.3 Dialog Runner

```gdscript
# scripts/autoload/dialogue_runner.gd
extends Node

signal line_started(line: DialogueLine)
signal choices_presented(choices: Array[DialogueChoice])
signal dialogue_finished

var _data: DialogueData
var _index: int = 0
var active: bool = false

func start(data: DialogueData) -> void:
	if active or data == null or data.lines.is_empty():
		return
	_data = data
	_index = 0
	active = true
	_show_current()

func advance() -> void:
	if not active:
		return
	var line := _data.lines[_index]
	if not line.choices.is_empty():
		return  # menunggu pemain memilih
	_go_next(line.next_index)

func choose(choice: DialogueChoice) -> void:
	_go_next(choice.next_index)

func _go_next(jump: int) -> void:
	var line := _data.lines[_index]
	if line.set_flag != &"":
		GameState.set_flag(line.set_flag)
	_index = jump if jump >= 0 else _index + 1
	if _index >= _data.lines.size():
		_end()
	else:
		_show_current()

func _show_current() -> void:
	var line := _data.lines[_index]
	line_started.emit(line)
	if not line.choices.is_empty():
		var tersedia: Array[DialogueChoice] = []
		for c in line.choices:
			if c.required_flag == &"" or GameState.has_flag(c.required_flag):
				tersedia.append(c)
		choices_presented.emit(tersedia)

func _end() -> void:
	active = false
	_data = null
	dialogue_finished.emit()
```

Saat dialog aktif, nonaktifkan kontrol pemain dengan memeriksa `DialogueRunner.active` di state machine pemain, atau lewat pause sebagian (`process_mode`).

### 13.4 Efek ketik (typewriter) dan bunyi blip

Pada `RichTextLabel`, properti `visible_ratio` mengatur proporsi teks yang tampil. Tween-kan dari 0 ke 1.

```gdscript
# scenes/ui/dialogue_box.gd
extends Control

@onready var nama: Label = %Nama
@onready var teks: RichTextLabel = %Teks
@onready var potret: TextureRect = %Potret
@onready var blip: AudioStreamPlayer = $Blip
@onready var daftar_pilihan: VBoxContainer = %Pilihan

@export var chars_per_second: float = 40.0

var _tween: Tween
var _mengetik: bool = false
var _hitung_terakhir: int = 0

func _ready() -> void:
	hide()
	DialogueRunner.line_started.connect(_on_line_started)
	DialogueRunner.choices_presented.connect(_on_choices)
	DialogueRunner.dialogue_finished.connect(hide)

func _on_line_started(line: DialogueLine) -> void:
	show()
	_bersihkan_pilihan()
	nama.text = tr(line.speaker_key)
	potret.texture = line.portrait
	teks.text = tr(line.text_key)
	if line.blip_sound:
		blip.stream = line.blip_sound
	teks.visible_ratio = 0.0
	_hitung_terakhir = 0
	var total := teks.get_total_character_count()
	var durasi := float(total) / chars_per_second
	if _tween:
		_tween.kill()
	_mengetik = true
	_tween = create_tween()
	_tween.tween_property(teks, "visible_ratio", 1.0, durasi)
	_tween.finished.connect(func(): _mengetik = false)

func _process(_delta: float) -> void:
	if _mengetik:
		var tampil := teks.visible_characters
		if tampil != _hitung_terakhir:
			_hitung_terakhir = tampil
			if tampil % 2 == 0:  # bunyi tiap 2 huruf agar tidak terlalu ramai
				blip.pitch_scale = randf_range(0.95, 1.05)
				blip.play()

func _unhandled_input(event: InputEvent) -> void:
	if not visible or not event.is_action_pressed(&"interact"):
		return
	get_viewport().set_input_as_handled()
	if _mengetik:
		# Tekan sekali: tampilkan semua teks langsung
		_tween.kill()
		teks.visible_ratio = 1.0
		_mengetik = false
	else:
		DialogueRunner.advance()

func _on_choices(choices: Array[DialogueChoice]) -> void:
	_bersihkan_pilihan()
	for c in choices:
		var tombol := Button.new()
		tombol.text = tr(c.text_key)
		tombol.pressed.connect(DialogueRunner.choose.bind(c))
		daftar_pilihan.add_child(tombol)
	if daftar_pilihan.get_child_count() > 0:
		daftar_pilihan.get_child(0).grab_focus()

func _bersihkan_pilihan() -> void:
	for anak in daftar_pilihan.get_children():
		anak.queue_free()
```

Catatan: `%Nama` memakai **Unique Name** (klik kanan node di scene tree > "Access as Unique Name"). Ini membuat referensi node tidak bergantung pada posisi di hierarki.

Pada `RichTextLabel`, gunakan BBCode untuk gaya teks: `[b]tebal[/b]`, `[color=red]merah[/color]`, `[shake]`, `[wave]`. Aktifkan `BBCode Enabled`.

### 13.5 NPC interaksi

```gdscript
class_name NPC
extends Area2D

@export var dialogue: DialogueData
@export var dialogue_after_flag: DialogueData
@export var flag_untuk_dialog_alternatif: StringName = &""

var _player_dekat: bool = false

func _ready() -> void:
	body_entered.connect(func(b): if b.is_in_group(&"player"): _player_dekat = true)
	body_exited.connect(func(b): if b.is_in_group(&"player"): _player_dekat = false)

func _unhandled_input(event: InputEvent) -> void:
	if _player_dekat and event.is_action_pressed(&"interact") and not DialogueRunner.active:
		var data := dialogue
		if flag_untuk_dialog_alternatif != &"" and GameState.has_flag(flag_untuk_dialog_alternatif):
			data = dialogue_after_flag
		DialogueRunner.start(data)
		get_viewport().set_input_as_handled()
```

### 13.6 Quest sederhana

```gdscript
class_name QuestData
extends Resource

@export var id: StringName
@export var judul_key: StringName
@export var deskripsi_key: StringName
@export var objektif: Array[QuestObjective] = []
```

```gdscript
class_name QuestObjective
extends Resource

enum Jenis { KILL, COLLECT, TALK, REACH }

@export var jenis: Jenis = Jenis.KILL
@export var target_id: StringName
@export var jumlah: int = 1
```

`QuestManager` (autoload) mendengarkan `EventBus.enemy_killed`, `item_picked_up`, dan seterusnya, memperbarui kemajuan, lalu menyalakan flag saat quest selesai. Simpan progres quest di `GameState` agar ikut tersimpan.

### 13.7 Codex (jurnal lore)

Codex mencatat lore yang ditemukan. Entri berupa Resource (`CodexEntry` dengan `id`, `judul_key`, `isi_key`, `kategori`). Saat pemain menemukan catatan, panggil `GameState.set_flag("codex_" + id)`. Layar Codex menampilkan entri yang flag-nya aktif. Entri yang belum ditemukan tampil sebagai "???" untuk memancing rasa ingin tahu dan mendorong eksplorasi.

### 13.8 Alternatif: tool dialog siap pakai

Menulis dialog panjang lewat Inspector bisa membosankan. Ada add-on komunitas untuk dialog bercabang (misalnya Dialogic atau Dialogue Manager). Keduanya adalah proyek komunitas dengan perkembangan sendiri; periksa kompatibilitasnya dengan versi Godot Anda dan lisensinya sebelum memakai. Untuk memahami konsepnya, membangun sistem sederhana sendiri seperti di bab ini sangat bermanfaat.

### 13.9 Latihan Bab 13

Buat satu NPC dengan dialog yang berubah setelah Anda mengalahkan satu musuh (memakai flag), lengkap dengan efek ketik dan dua pilihan jawaban.

---

## Bab 14. Save dan Load (Offline)

### 14.1 Prinsip dasar

Game offline menyimpan semuanya secara lokal. Aturan penting:

1. Simpan di `user://`, **bukan** `res://`. Folder `res://` bersifat baca-saja pada game yang sudah diekspor.
2. Gunakan format yang bisa dibaca (JSON) selama pengembangan agar mudah di-debug.
3. Sertakan **nomor versi** pada data simpanan.
4. Tulis dengan aman agar file tidak rusak jika game ditutup mendadak.
5. Sediakan beberapa slot dan backup.

Lokasi `user://` di desktop (bisa berbeda sesuai pengaturan proyek):

- Windows: `%APPDATA%\Godot\app_userdata\<nama proyek>\`
- Linux: `~/.local/share/godot/app_userdata/<nama proyek>/`
- macOS: `~/Library/Application Support/Godot/app_userdata/<nama proyek>/`

Anda bisa membuka folder ini dari editor lewat **Project > Open User Data Folder**. Anda juga dapat memakai folder kustom lewat opsi `Use Custom User Dir` di Project Settings.

### 14.2 Apa yang disimpan?

Simpan **data**, bukan **node**. Contoh: posisi pemain, darah, inventaris, flag cerita, area saat ini, objek yang sudah dihancurkan atau diambil, waktu bermain.

Jangan mencoba menyimpan seluruh scene tree secara langsung. Itu rapuh dan sulit dimigrasi saat game diperbarui.

### 14.3 Save Manager

```gdscript
# scripts/autoload/save_manager.gd
extends Node

const SAVE_VERSION: int = 2
const SAVE_DIR: String = "user://saves/"

signal save_completed(slot: int)
signal load_completed(slot: int)

func _ready() -> void:
	DirAccess.make_dir_recursive_absolute(SAVE_DIR)

func _path(slot: int) -> String:
	return SAVE_DIR + "slot_%d.json" % slot

func save_game(slot: int) -> bool:
	var player := get_tree().get_first_node_in_group(&"player") as Node2D
	var data: Dictionary = {
		"version": SAVE_VERSION,
		"saved_at": Time.get_datetime_string_from_system(),
		"level": get_tree().current_scene.scene_file_path,
		"player": {
			"x": player.global_position.x if player else 0.0,
			"y": player.global_position.y if player else 0.0,
		},
		"state": GameState.to_dict(),
	}
	var teks := JSON.stringify(data, "\t")

	# Tulis ke file sementara dulu, lalu ganti nama (hindari file setengah tertulis)
	var final_path := _path(slot)
	var tmp_path := final_path + ".tmp"
	var f := FileAccess.open(tmp_path, FileAccess.WRITE)
	if f == null:
		push_error("Gagal menulis: %s (error %d)" % [tmp_path, FileAccess.get_open_error()])
		return false
	f.store_string(teks)
	f.close()

	# Simpan backup dari file lama bila ada
	var dir := DirAccess.open(SAVE_DIR)
	if dir == null:
		return false
	if dir.file_exists(final_path.get_file()):
		dir.copy(final_path, final_path + ".bak")
		dir.remove(final_path.get_file())
	var err := dir.rename(tmp_path.get_file(), final_path.get_file())
	if err != OK:
		push_error("Gagal mengganti nama file simpanan: %d" % err)
		return false

	save_completed.emit(slot)
	return true

func load_game(slot: int) -> bool:
	var path := _path(slot)
	if not FileAccess.file_exists(path):
		return false
	var f := FileAccess.open(path, FileAccess.READ)
	if f == null:
		return false
	var hasil: Variant = JSON.parse_string(f.get_as_text())
	f.close()
	if typeof(hasil) != TYPE_DICTIONARY:
		push_error("File simpanan rusak: " + path)
		return false

	var data: Dictionary = _migrate(hasil)
	GameState.from_dict(data.get("state", {}))
	# Pindah ke level tersimpan, lalu letakkan pemain
	get_tree().change_scene_to_file(data["level"])
	await get_tree().process_frame
	await get_tree().process_frame
	var player := get_tree().get_first_node_in_group(&"player") as Node2D
	if player:
		var p: Dictionary = data["player"]
		player.global_position = Vector2(p["x"], p["y"])
	load_completed.emit(slot)
	return true

func _migrate(data: Dictionary) -> Dictionary:
	var v := int(data.get("version", 1))
	if v < 2:
		# Contoh migrasi: versi 1 belum punya "saved_at"
		data["saved_at"] = data.get("saved_at", "tidak diketahui")
		data["version"] = 2
	return data

func slot_info(slot: int) -> Dictionary:
	var path := _path(slot)
	if not FileAccess.file_exists(path):
		return {}
	var f := FileAccess.open(path, FileAccess.READ)
	var hasil: Variant = JSON.parse_string(f.get_as_text())
	f.close()
	return hasil if typeof(hasil) == TYPE_DICTIONARY else {}
```

Perhatikan beberapa detail penting:

- `JSON.parse_string` mengembalikan `null` jika gagal. Selalu periksa tipe hasilnya.
- Fungsi `_migrate` menjaga kompatibilitas ke belakang. Setiap kali Anda mengubah struktur simpanan, naikkan `SAVE_VERSION` dan tambahkan langkah migrasi. Ini sangat penting setelah game dirilis: pemain tidak boleh kehilangan progres setelah pembaruan.
- Pada sebagian platform, `DirAccess.rename` terhadap file yang sudah ada dapat berperilaku berbeda. Karena itu kode di atas menghapus file lama (setelah dibackup) sebelum mengganti nama. Uji di platform target Anda.
- Pada `load_game`, jeda dua frame memberi waktu scene baru dan pemain siap. Pendekatan yang lebih rapi: `SceneManager` memancarkan signal "level siap", lalu data pemain diterapkan saat itu.

### 14.4 Objek dunia yang bisa berubah

Contoh: peti yang sudah dibuka tidak boleh terisi lagi saat dimuat. Beri setiap objek **ID unik** (misalnya `level01_chest_03`) dan catat statusnya di flag:

```gdscript
class_name Chest
extends Area2D

@export var chest_id: StringName
@export var item: ItemData

func _ready() -> void:
	if GameState.has_flag(chest_id):
		$Sprite2D.frame = 1  # tampilan terbuka
		set_process_unhandled_input(false)

func buka() -> void:
	GameState.set_flag(chest_id)
	GameState.add_item(item.id)
	$Sprite2D.frame = 1
```

### 14.5 Autosave dan checkpoint

Lakukan autosave pada momen aman: saat masuk ruangan baru, setelah mengalahkan boss, atau saat mengaktifkan checkpoint. Tampilkan ikon kecil "menyimpan..." agar pemain tidak mematikan game di tengah penyimpanan. Hindari autosave saat pertempuran berlangsung.

### 14.6 Pengaturan (Settings) memakai ConfigFile

`ConfigFile` cocok untuk preferensi karena formatnya mirip file `.ini`.

```gdscript
# scripts/autoload/settings.gd
extends Node

const PATH: String = "user://settings.cfg"

var master_volume: float = 1.0
var music_volume: float = 0.8
var sfx_volume: float = 1.0
var screen_shake: float = 1.0
var fullscreen: bool = false
var locale: String = "id"

func _ready() -> void:
	load_settings()
	apply()

func load_settings() -> void:
	var cfg := ConfigFile.new()
	if cfg.load(PATH) != OK:
		return
	master_volume = cfg.get_value("audio", "master", master_volume)
	music_volume = cfg.get_value("audio", "music", music_volume)
	sfx_volume = cfg.get_value("audio", "sfx", sfx_volume)
	screen_shake = cfg.get_value("gameplay", "screen_shake", screen_shake)
	fullscreen = cfg.get_value("video", "fullscreen", fullscreen)
	locale = cfg.get_value("general", "locale", locale)

func save_settings() -> void:
	var cfg := ConfigFile.new()
	cfg.set_value("audio", "master", master_volume)
	cfg.set_value("audio", "music", music_volume)
	cfg.set_value("audio", "sfx", sfx_volume)
	cfg.set_value("gameplay", "screen_shake", screen_shake)
	cfg.set_value("video", "fullscreen", fullscreen)
	cfg.set_value("general", "locale", locale)
	cfg.save(PATH)

func apply() -> void:
	_set_bus(&"Master", master_volume)
	_set_bus(&"Music", music_volume)
	_set_bus(&"SFX", sfx_volume)
	DisplayServer.window_set_mode(
		DisplayServer.WINDOW_MODE_FULLSCREEN if fullscreen
		else DisplayServer.WINDOW_MODE_WINDOWED
	)
	TranslationServer.set_locale(locale)

func _set_bus(nama: StringName, linear: float) -> void:
	var idx := AudioServer.get_bus_index(nama)
	if idx >= 0:
		AudioServer.set_bus_volume_db(idx, linear_to_db(linear))
		AudioServer.set_bus_mute(idx, linear <= 0.001)
```

### 14.6.1 Keamanan save: perlu enkripsi?

Untuk game single player offline, enkripsi save game umumnya tidak diperlukan. Pemain berhak mengubah save mereka, dan itu tidak merugikan siapa pun. Menyimpan dalam format biner atau mengenkripsi hanya mempersulit debugging dan dukungan pemain. Jika ingin sekadar mencegah perubahan tidak sengaja, `FileAccess.open_encrypted_with_pass` tersedia, tetapi pertimbangkan apakah manfaatnya sebanding.

### 14.7 Latihan Bab 14

Buat `SaveManager` dengan 3 slot, tampilkan layar pilih slot dengan info (waktu dan area), lalu uji dengan sengaja merusak file JSON untuk memastikan game tidak crash.

---

## Bab 15. UI Lanjutan, Gamepad, dan Remap Input

### 15.1 Node Control dan Container

UI di Godot dibangun dari node `Control`. Kuncinya adalah **Container** yang mengatur tata letak otomatis:

- `VBoxContainer` dan `HBoxContainer`: susun vertikal atau horizontal.
- `GridContainer`: kisi (cocok untuk inventaris).
- `MarginContainer`: beri margin.
- `CenterContainer`: pusatkan isi.
- `PanelContainer`: panel dengan latar.
- `ScrollContainer`: area gulir.

Jangan menaruh posisi UI dengan angka piksel manual. Gunakan **anchors** dan **containers** agar UI menyesuaikan berbagai resolusi dan bahasa (teks Indonesia sering lebih panjang daripada Inggris).

### 15.2 Theme

`Theme` adalah resource gaya terpusat (font, warna, gaya tombol). Buat satu `Theme` untuk seluruh game, lalu atur di **Project Settings > GUI > Theme > Custom**. Dengan begitu semua tombol, label, dan panel konsisten, dan Anda dapat mengubah gaya di satu tempat.

### 15.3 Fokus dan navigasi gamepad

Game yang baik bisa dimainkan dengan keyboard, mouse, dan gamepad. Pastikan:

- Setiap menu punya elemen yang mendapat fokus awal (`grab_focus()`).
- Atur `Focus Neighbor` bila urutan otomatis kurang tepat.
- Gunakan action bawaan `ui_accept`, `ui_cancel`, `ui_up`, `ui_down`, `ui_left`, `ui_right` untuk menu.

```gdscript
func _ready() -> void:
	$VBox/MulaiButton.grab_focus()
```

Saat menu dibuka lewat kode, tunggu satu frame jika `grab_focus()` tidak bekerja karena node belum terlihat:

```gdscript
await get_tree().process_frame
$VBox/MulaiButton.grab_focus()
```

### 15.4 HUD yang bersih

Prinsip:

- Tampilkan hanya yang dibutuhkan saat itu (darah, sumber daya utama).
- Hubungkan ke data lewat signal (`health_changed`), bukan membaca nilai tiap frame.
- Beri animasi kecil saat nilai berubah (bar darah menyusut halus dengan tween, bagian "kehilangan" berwarna berbeda yang menyusul kemudian).

```gdscript
extends Control

@onready var bar: ProgressBar = %HealthBar
@onready var bar_lag: ProgressBar = %HealthBarLag

func _ready() -> void:
	EventBus.player_health_changed.connect(_on_health_changed)

func _on_health_changed(current: int, maximum: int) -> void:
	bar.max_value = maximum
	bar_lag.max_value = maximum
	bar.value = current
	var tw := create_tween()
	tw.tween_interval(0.35)
	tw.tween_property(bar_lag, "value", current, 0.3)
```

### 15.5 Menu pause

```gdscript
extends CanvasLayer

func _ready() -> void:
	process_mode = Node.PROCESS_MODE_ALWAYS
	hide()

func _unhandled_input(event: InputEvent) -> void:
	if event.is_action_pressed(&"pause"):
		toggle()
		get_viewport().set_input_as_handled()

func toggle() -> void:
	var jeda := not get_tree().paused
	get_tree().paused = jeda
	visible = jeda
	if jeda:
		$VBox/LanjutButton.grab_focus()
```

`process_mode = Always` membuat menu ini tetap berfungsi saat game di-pause. Node gameplay otomatis berhenti karena mengikuti mode `Inherit` bawaan, sehingga ikut terjeda.

### 15.6 Remap kontrol

Pemain berhak mengubah tombol. Godot menyediakan `InputMap` untuk memanipulasi action saat runtime.

```gdscript
# Mengganti tombol keyboard untuk suatu action
func remap_key(action: StringName, event: InputEventKey) -> void:
	# Hapus event keyboard lama saja (pertahankan gamepad)
	for lama in InputMap.action_get_events(action):
		if lama is InputEventKey:
			InputMap.action_erase_event(action, lama)
	InputMap.action_add_event(action, event)
```

Menangkap tombol berikutnya yang ditekan pemain:

```gdscript
var _menunggu_action: StringName = &""

func mulai_remap(action: StringName) -> void:
	_menunggu_action = action
	$Label.text = "Tekan tombol baru..."

func _input(event: InputEvent) -> void:
	if _menunggu_action == &"":
		return
	if event is InputEventKey and event.pressed:
		remap_key(_menunggu_action, event)
		_menunggu_action = &""
		get_viewport().set_input_as_handled()
```

Simpan pemetaan ke `ConfigFile` dan muat kembali saat game mulai. Untuk menyimpan `InputEvent`, Anda dapat menyimpan `keycode` (untuk keyboard) atau `button_index` (untuk gamepad) sebagai angka. Untuk `InputEventKey`, `physical_keycode` lebih baik agar tata letak keyboard non-QWERTY tetap bekerja.

### 15.7 Aksesibilitas (hal kecil dengan dampak besar)

- Opsi ukuran teks dan kontras tinggi.
- Opsi mengurangi screen shake dan efek berkedip (penting untuk pemain yang sensitif terhadap kilatan).
- Mode warna aman bagi buta warna: jangan hanya mengandalkan warna untuk informasi, tambahkan ikon atau bentuk.
- Opsi menahan tombol sebagai ganti menekan berulang.
- Opsi bantuan (misalnya darah musuh lebih sedikit atau kebal sementara).
- Pause kapan saja, termasuk saat dialog.

Dukungan aksesibilitas memperluas jangkauan pemain tanpa menurunkan kualitas bagi yang lain.

### 15.8 Latihan Bab 15

Buat menu pengaturan dengan slider volume, toggle layar penuh, pilihan bahasa, dan satu tombol yang bisa di-remap, lalu simpan dengan `ConfigFile`.

---

## Bab 16. Audio untuk Game Tanpa Voice Actor

### 16.1 Audio bus

Buka panel **Audio** di bagian bawah editor dan buat bus: `Master`, `Music`, `SFX`, `UI`, `Ambience`. Arahkan setiap `AudioStreamPlayer` ke bus yang sesuai. Dengan bus terpisah, pemain bisa mengatur volume musik dan efek secara terpisah (lihat `Settings` di Bab 14).

Tambahkan efek pada bus: `Reverb` untuk gua, `LowPassFilter` untuk efek "teredam" saat pause atau di bawah air, `Compressor` pada Master untuk mencegah distorsi.

### 16.2 SFX: banyak variasi, sedikit suara sama

Mendengar bunyi yang sama berulang kali terasa membosankan. Tips:

- Variasikan `pitch_scale` secara acak kecil (0,92 sampai 1,08).
- Siapkan 3 sampai 5 variasi bunyi untuk aksi yang sering (langkah, tebasan).
- Gunakan `AudioStreamRandomizer` (resource bawaan) untuk memilih variasi dan pitch acak otomatis tanpa kode.

```gdscript
# Memutar SFX satu-kali di posisi tertentu tanpa node tetap
func play_sfx_at(stream: AudioStream, posisi: Vector2) -> void:
	var p := AudioStreamPlayer2D.new()
	p.stream = stream
	p.global_position = posisi
	p.bus = &"SFX"
	p.finished.connect(p.queue_free)
	add_child(p)
	p.play()
```

Catatan: `add_child(p)` sebelum `global_position` kadang lebih aman; tetapi pada node yang belum masuk tree, `global_position` tetap dapat diatur. Jika Anda menemukan posisi tidak sesuai, atur posisi setelah `add_child`.

### 16.3 Musik dinamis

Musik yang bereaksi terhadap gameplay membuat dunia terasa hidup:

- **Crossfade** antar-trek saat pindah area atau memulai pertarungan.
- **Layering**: trek dasar selalu berjalan, lapisan tambahan (perkusi, melodi) dimunculkan saat bahaya meningkat.
- **Stinger**: jingle pendek untuk momen penting (menemukan rahasia, menang).

Crossfade sederhana dengan dua pemutar:

```gdscript
# scripts/autoload/audio_manager.gd
extends Node

@onready var a: AudioStreamPlayer = $MusicA
@onready var b: AudioStreamPlayer = $MusicB
var _aktif: AudioStreamPlayer

func _ready() -> void:
	_aktif = a

func play_music(stream: AudioStream, fade: float = 1.0) -> void:
	if _aktif.stream == stream and _aktif.playing:
		return
	var lama := _aktif
	var baru := b if _aktif == a else a
	baru.stream = stream
	baru.volume_db = -60.0
	baru.play()
	var tw := create_tween().set_parallel(true)
	tw.tween_property(baru, "volume_db", 0.0, fade)
	tw.tween_property(lama, "volume_db", -60.0, fade)
	tw.chain().tween_callback(lama.stop)
	_aktif = baru
```

Godot 4 juga memiliki `AudioStreamInteractive` dan `AudioStreamSynchronized` (sejak seri 4.3) untuk musik interaktif dan berlapis tanpa banyak kode. Jika Anda ingin sistem lebih canggih, pelajari kedua resource ini di dokumentasi resmi.

### 16.4 Audio sebagai bahasa cerita

Karena tidak ada suara pengisi, audio menjadi alat emosi utama:

- **Motif tokoh**: melodi khas untuk setiap karakter penting.
- **Keheningan**: jeda musik sebelum momen penting sering lebih kuat daripada musik keras.
- **Ambience**: bunyi lingkungan (angin, tetesan air, dengung mesin) menceritakan tempat.
- **Blip dialog**: ciri khas "suara" tiap karakter lewat bunyi per huruf (Bab 13).
- **Bunyi UI** yang konsisten membantu identitas game.

### 16.5 Sumber audio dan lisensi

Anda dapat membuat sendiri, membeli, atau memakai aset berlisensi bebas. **Selalu periksa lisensi** (CC0, CC-BY, dan lainnya punya syarat berbeda) dan catat atribusi di file `CREDITS.md` serta layar kredit game. Mencatat sejak awal menyelamatkan Anda dari masalah hukum saat rilis.

### 16.6 Latihan Bab 16

Buat `AudioManager` dengan crossfade musik, dan tambahkan variasi pitch pada bunyi langkah dan tebasan.

---

## Bab 17. Shader 2D dan Efek Visual

### 17.1 Pengantar shader canvas_item

Shader adalah program kecil yang berjalan di GPU untuk mengubah tampilan. Untuk 2D, kita memakai `shader_type canvas_item`. Anda membuatnya dengan **klik kanan > New Resource > Shader**, lalu menempelkannya pada `ShaderMaterial` di properti `Material` suatu node.

Fungsi utama adalah `fragment()`, yang berjalan untuk setiap piksel. Variabel penting:

- `UV`: koordinat tekstur piksel (0 sampai 1).
- `TEXTURE`: tekstur node.
- `COLOR`: warna keluaran piksel.
- `TIME`: waktu dalam detik sejak game mulai.

### 17.2 Shader flash saat terkena serangan

```glsl
shader_type canvas_item;

uniform vec4 flash_color : source_color = vec4(1.0, 1.0, 1.0, 1.0);
uniform float flash_amount : hint_range(0.0, 1.0) = 0.0;

void fragment() {
	vec4 tex = texture(TEXTURE, UV);
	COLOR = vec4(mix(tex.rgb, flash_color.rgb, flash_amount), tex.a);
}
```

Memicu dari GDScript:

```gdscript
func flash(durasi: float = 0.12) -> void:
	var mat := $Sprite2D.material as ShaderMaterial
	mat.set_shader_parameter("flash_amount", 1.0)
	var tw := create_tween()
	tw.tween_property(mat, "shader_parameter/flash_amount", 0.0, durasi)
```

Peringatan: jika beberapa musuh berbagi satu `ShaderMaterial` (resource yang sama), semuanya akan berkedip bersamaan. Aktifkan **Local to Scene** pada material, atau gunakan `material = material.duplicate()` di `_ready()`.

Alternatif tanpa shader: animasikan `modulate` ke warna sangat terang. Cukup untuk banyak kasus, tetapi `modulate` hanya bisa mengalikan warna sehingga tidak bisa membuat sprite benar-benar putih polos.

### 17.3 Outline dan dissolve

Dissolve (menghilang bertahap) menggunakan noise:

```glsl
shader_type canvas_item;

uniform sampler2D noise_tex;
uniform float dissolve : hint_range(0.0, 1.0) = 0.0;
uniform vec4 edge_color : source_color = vec4(1.0, 0.6, 0.1, 1.0);
uniform float edge_width : hint_range(0.0, 0.2) = 0.05;

void fragment() {
	vec4 tex = texture(TEXTURE, UV);
	float n = texture(noise_tex, UV).r;
	if (n < dissolve) {
		discard;
	}
	float edge = smoothstep(dissolve, dissolve + edge_width, n);
	vec3 rgb = mix(edge_color.rgb, tex.rgb, edge);
	COLOR = vec4(rgb, tex.a);
}
```

Atur `noise_tex` ke `NoiseTexture2D` dengan noise bawaan. Animasikan `dissolve` dari 0 ke 1 saat musuh mati.

### 17.4 Partikel dengan GPUParticles2D

Gunakan `GPUParticles2D` untuk efek seperti debu langkah, percikan benturan, api, dan hujan. Beberapa catatan:

- Atur `One Shot` untuk efek sekali (ledakan) dan `Emitting` lewat kode.
- Gunakan `ParticleProcessMaterial` untuk mengatur kecepatan, gravitasi, warna, ukuran.
- Pada perangkat lawas atau renderer Compatibility, `CPUParticles2D` bisa menjadi alternatif yang lebih kompatibel. Anda dapat mengonversi lewat menu **Convert to CPUParticles2D**.
- Hapus efek sekali pakai setelah selesai (`finished` signal + `queue_free`).

```gdscript
func spawn_impact(posisi: Vector2) -> void:
	var fx := impact_scene.instantiate() as GPUParticles2D
	fx.global_position = posisi
	fx.one_shot = true
	fx.finished.connect(fx.queue_free)
	get_tree().current_scene.add_child(fx)
	fx.emitting = true
```

### 17.5 Cahaya 2D

Godot 2D mendukung `PointLight2D` dan `DirectionalLight2D`, `LightOccluder2D` untuk bayangan, dan `CanvasModulate` untuk menggelapkan seluruh adegan. Cocok untuk suasana gua, malam hari, dan obor.

Resep suasana gelap dengan obor:

1. Tambahkan `CanvasModulate` dengan warna gelap kebiruan.
2. Tambahkan `PointLight2D` pada pemain dan obor dengan `Texture` gradien radial.
3. Tambahkan `LightOccluder2D` pada dinding untuk bayangan.

Gunakan **Normal Map** pada sprite jika Anda ingin kesan volume dari cahaya dinamis. Perhatikan biaya performa pada perangkat lemah. Uji di perangkat target.

### 17.6 Post-processing ringan

Untuk efek layar penuh (misalnya vignette, aberasi kromatik, efek bergetar saat terluka), gunakan `ColorRect` atau `TextureRect` yang menutupi layar dengan shader yang membaca `hint_screen_texture`:

```glsl
shader_type canvas_item;

uniform sampler2D screen_tex : hint_screen_texture, filter_linear_mipmap;
uniform float intensity : hint_range(0.0, 1.0) = 0.5;

void fragment() {
	vec4 col = texture(screen_tex, SCREEN_UV);
	float v = smoothstep(0.8, 0.2, distance(UV, vec2(0.5)));
	col.rgb *= mix(1.0, v, intensity);
	COLOR = col;
}
```

Sertakan opsi mematikan efek ini di pengaturan, terutama untuk efek yang bergetar atau berkedip.

### 17.7 Latihan Bab 17

Buat shader flash putih, lalu gunakan saat musuh terkena serangan. Tambahkan efek dissolve saat musuh mati.

---

## Bab 18. Lokalisasi (Termasuk Bahasa Indonesia)

### 18.1 Mengapa lokalisasi lebih mudah tanpa voice actor

Tanpa suara pengisi, lokalisasi hanya perlu menerjemahkan teks (dan beberapa gambar yang berisi teks). Ini membuat game Anda dapat menjangkau pasar global dengan biaya jauh lebih rendah. Untuk game yang ditulis dalam bahasa Indonesia, menambahkan bahasa Inggris saja sudah membuka pasar jauh lebih besar.

### 18.2 Cara kerja terjemahan di Godot

Anda menyimpan teks di tabel terjemahan dengan **kunci**, dan memanggil `tr("KUNCI")` di kode. Node `Control` seperti `Label` dan `Button` juga otomatis menerjemahkan teksnya jika teksnya cocok dengan sebuah kunci.

Format paling mudah: **CSV**. Contoh `localization/teks.csv`:

```csv
keys,en,id
MENU_MULAI,Start,Mulai
MENU_PENGATURAN,Settings,Pengaturan
MENU_KELUAR,Quit,Keluar
NPC_ELDER,Elder,Tetua
DLG_ELDER_001,"The lantern still burns, traveler.","Lentera itu masih menyala, wahai pengelana."
ITEM_POTION_NAMA,Small Potion,Ramuan Kecil
ITEM_POTION_DESK,Restores a little health.,Memulihkan sedikit darah.
```

Langkah:

1. Simpan CSV dengan encoding UTF-8.
2. Godot akan mengimpor CSV menjadi file `.translation` per bahasa.
3. Daftarkan di **Project Settings > Localization > Translations**.
4. Aturkan bahasa dengan `TranslationServer.set_locale("id")`.

Beberapa catatan praktis:

- Kolom pertama adalah kunci. Header kolom lain adalah kode bahasa (`en`, `id`, `ja`).
- Jika teks mengandung koma, bungkus dengan tanda kutip ganda.
- Teks bisa memuat baris baru lewat `\n`.

### 18.3 Placeholder dan format

```gdscript
# Kunci: DLG_REWARD = "Kamu mendapat %d koin dari %s."
var teks := tr("DLG_REWARD") % [jumlah, nama]
```

Perhatikan bahwa urutan kata berbeda antarbahasa. Pakai penamaan placeholder yang jelas, dan hindari menyusun kalimat dengan menyambung potongan teks (misalnya `tr("KAMU") + " " + tr("MENDAPAT")`), karena tata bahasa tiap bahasa berbeda.

### 18.4 Font dan karakter

Pastikan font mendukung semua karakter bahasa target (misalnya aksara Jepang, Korea, atau Mandarin butuh font khusus). Untuk Indonesia dan Inggris, font Latin standar cukup. Atur `FontFile` dengan **Fallback** agar karakter yang tidak ada dialihkan ke font lain.

### 18.5 Panjang teks dan tata letak

Terjemahan Indonesia sering lebih panjang daripada bahasa Inggris. Rancang UI dengan ruang cadangan, aktifkan `Autowrap` pada label, dan gunakan container supaya tata letak menyesuaikan. Uji semua layar dengan bahasa terpanjang.

### 18.6 Pergantian bahasa saat runtime

```gdscript
func ganti_bahasa(kode: String) -> void:
	TranslationServer.set_locale(kode)
	Settings.locale = kode
	Settings.save_settings()
```

Node `Control` memperbarui teks otomatis. Untuk teks yang Anda set lewat kode (`label.text = tr(...)`), hubungkan ke notifikasi `NOTIFICATION_TRANSLATION_CHANGED` agar diperbarui ulang:

```gdscript
func _notification(what: int) -> void:
	if what == NOTIFICATION_TRANSLATION_CHANGED:
		_perbarui_teks()
```

### 18.7 Latihan Bab 18

Pindahkan semua teks menu dan dialog Anda ke CSV dengan dua bahasa (Indonesia dan Inggris), lalu buat tombol pengganti bahasa.

---

## Bab 19. Performa, Profiling, dan Debugging

### 19.1 Aturan utama: ukur dulu, optimalkan kemudian

Jangan menebak sumber kelambatan. Gunakan alat profil bawaan:

- **Debugger > Profiler**: waktu eksekusi per fungsi script.
- **Debugger > Monitors**: FPS, penggunaan memori, jumlah objek, jumlah node, draw calls, dan lainnya.
- **Debugger > Visual Profiler**: pembagian waktu CPU dan GPU per tahap render.
- **Debug > Visible Collision Shapes** dan **Visible Navigation**: untuk melihat bentuk tumbukan dan navigasi saat game berjalan.
- **Remote tab** pada scene tree: periksa node pada game yang sedang berjalan.

Target umum: stabil 60 FPS di perangkat minimum yang Anda dukung. Tentukan perangkat minimum sejak awal.

### 19.2 Penyebab kelambatan 2D yang umum

1. **Terlalu banyak node aktif di luar layar.** Gunakan `VisibleOnScreenEnabler2D` untuk menonaktifkan musuh dan objek yang jauh dari kamera.
2. **Pekerjaan berat di `_process`/`_physics_process` setiap frame.** Pindahkan ke `Timer`, atau lakukan hanya saat berubah.
3. **Pencarian node berulang** (`get_node`, `get_nodes_in_group`) di dalam loop per frame. Simpan referensi di variabel `@onready`.
4. **Terlalu banyak draw call** akibat banyak tekstur berbeda atau material berbeda. Gabungkan sprite ke satu atlas tekstur. Godot melakukan batching untuk item 2D yang menggunakan tekstur dan material yang sama.
5. **Shader dan cahaya 2D yang berat** di perangkat lemah.
6. **Partikel terlalu banyak.**
7. **Pembuatan dan penghapusan objek berulang** (peluru, partikel). Gunakan object pooling.
8. **Bentuk tumbukan yang terlalu rumit.** Gunakan bentuk sederhana (persegi, lingkaran, kapsul).

### 19.3 Menonaktifkan objek di luar layar

```gdscript
# Tambahkan VisibleOnScreenEnabler2D sebagai anak musuh.
# Atur "Enable Mode" dan "Enable Node Path" ke node yang ingin dikontrol.
# Secara bawaan, ia menghentikan pemrosesan node induk saat di luar layar.
```

Anda cukup menambahkan node ini dan mengatur `rect` yang sedikit lebih besar dari layar. Musuh berhenti diproses saat jauh dari kamera dan aktif lagi saat mendekat.

### 19.4 Object pooling

Membuat dan menghapus ratusan objek (peluru) per detik menekan memori dan CPU. Pooling mendaur ulang objek.

```gdscript
class_name Pool
extends Node

@export var scene: PackedScene
@export var ukuran_awal: int = 20

var _bebas: Array[Node] = []

func _ready() -> void:
	for i in ukuran_awal:
		var obj := scene.instantiate()
		_matikan(obj)
		add_child(obj)
		_bebas.append(obj)

func ambil() -> Node:
	var obj: Node = _bebas.pop_back() if not _bebas.is_empty() else scene.instantiate()
	if obj.get_parent() == null:
		add_child(obj)
	obj.process_mode = Node.PROCESS_MODE_INHERIT
	obj.show()
	return obj

func kembalikan(obj: Node) -> void:
	_matikan(obj)
	_bebas.append(obj)

func _matikan(obj: Node) -> void:
	obj.process_mode = Node.PROCESS_MODE_DISABLED
	obj.hide()
```

Gunakan pooling hanya jika profil menunjukkan masalah. Untuk jumlah objek kecil, `instantiate()` dan `queue_free()` sudah cukup.

### 19.5 Perubahan state fisika yang aman

Jika Anda mendapat error terkait "flushing queries", itu berarti Anda mengubah state fisika di dalam callback fisika. Gunakan:

```gdscript
set_deferred("monitoring", false)
$CollisionShape2D.set_deferred("disabled", true)
call_deferred("add_child", node_baru)
```

### 19.6 Multithreading dengan hati-hati

Godot menyediakan `Thread` dan `WorkerThreadPool` untuk pekerjaan berat di latar (misalnya generasi level prosedural). Aturan penting:

- Jangan mengubah node yang ada di scene tree dari thread lain secara langsung. Gunakan `call_deferred` untuk menyerahkan hasil kembali ke thread utama.
- Untuk game 2D indie biasa, jarang diperlukan. Mulai dari pemuatan berulir (`ResourceLoader.load_threaded_request`) sebelum menyentuh thread manual.

### 19.7 Debugging

- Gunakan `print()` seperlunya. Gunakan `print_debug()` atau `push_warning()` / `push_error()` agar pesan terlihat di panel Debugger.
- Gunakan `assert(kondisi, "pesan")` untuk memastikan asumsi (hanya aktif pada build debug).
- Pasang **breakpoint** dengan klik di sebelah nomor baris di editor script. Saat game berhenti, periksa nilai variabel di panel Debugger.
- Gunakan **Remote** scene tree untuk melihat dan mengubah properti node saat game berjalan.
- Buat **debug overlay** sederhana (FPS, posisi, state, flag) yang bisa diaktifkan dengan tombol F3.

```gdscript
extends CanvasLayer

@onready var label: Label = $Label

func _ready() -> void:
	visible = OS.is_debug_build()

func _unhandled_input(event: InputEvent) -> void:
	if event is InputEventKey and event.pressed and event.keycode == KEY_F3:
		visible = not visible

func _process(_delta: float) -> void:
	if not visible:
		return
	label.text = "FPS: %d\nNode: %d\nFlag: %d" % [
		Engine.get_frames_per_second(),
		get_tree().get_node_count(),
		GameState.flags.size(),
	]
```

### 19.8 Kesalahan umum yang sering ditemui

|Gejala|Kemungkinan penyebab|Solusi|
|---|---|---|
|`Invalid get index on base: 'Nil'`|Node tidak ditemukan atau belum siap|Periksa path, gunakan `@onready`, periksa `null`|
|Sprite bergetar saat kamera bergerak|Posisi tidak sejajar piksel|Aktifkan snap ke piksel, gunakan zoom bilangan bulat|
|Musuh tembus dinding|Kecepatan terlalu tinggi, bentuk tipis|Perbesar bentuk tumbukan, pakai continuous collision (untuk RigidBody)|
|Gerak lambat atau cepat di perangkat berbeda|Memakai `_process` untuk fisika|Pindahkan ke `_physics_process` dan pakai `delta`|
|Resource ikut berubah di semua instance|Resource dibagi bersama|`duplicate()` atau Local to Scene|
|Error `.remap` di build ekspor|Pemindai folder tidak menangani|Tangani akhiran `.remap` (Bab 5)|
|Teks tidak diterjemahkan|Kunci tidak cocok atau CSV tidak terdaftar|Periksa kunci dan Project Settings > Localization|

### 19.9 Latihan Bab 19

Jalankan game Anda dengan Profiler, temukan fungsi yang paling lama, dan catat angkanya sebelum dan sesudah optimasi.

---

## Bab 20. Tooling, Version Control, dan Testing

### 20.1 Alur kerja Git yang sederhana

Untuk tim kecil atau solo:

- Cabang `main` selalu dalam keadaan bisa dimainkan.
- Buat cabang untuk fitur (`fitur/dash`, `fitur/dialog`).
- Commit kecil dan sering dengan pesan jelas ("Tambah coyote time pada pemain").
- Beri tag untuk versi rilis (`v0.1.0`, `v1.0.0`).
- Backup repositori ke tempat lain (remote Git atau penyimpanan eksternal).

Untuk aset biner besar (gambar dan audio ukuran besar), pertimbangkan Git LFS bila repositori membengkak.

Tips: gunakan format teks (`.tscn`, `.tres`) agar diff dan merge lebih mudah. Hindari dua orang mengedit scene yang sama pada waktu bersamaan. Pecah scene besar menjadi scene kecil (komposisi, Bab 4) untuk mengurangi konflik.

### 20.2 Menulis alat editor dengan `@tool`

`@tool` membuat script berjalan di editor. Contoh sederhana: node yang menampilkan nama dan area di editor.

```gdscript
@tool
extends Marker2D

@export var spawn_name: StringName = &"default":
	set(v):
		spawn_name = v
		name = v
		queue_redraw()

func _draw() -> void:
	if Engine.is_editor_hint():
		draw_circle(Vector2.ZERO, 6.0, Color.CYAN)
```

`Engine.is_editor_hint()` membedakan apakah kode berjalan di editor atau di game. Pakai untuk menjaga kode editor tidak ikut berjalan saat bermain.

Peringatan: bug pada script `@tool` dapat membuat editor menolak membuka scene. Selalu commit sebelum bereksperimen dan simpan salinan script.

### 20.3 Plugin editor

Jika Anda ingin membuat alat sendiri (misalnya editor dialog visual atau pemilih item), pelajari `EditorPlugin` dan buat plugin di folder `addons/nama_plugin/`. Mulai dari yang sederhana seperti dock kustom atau inspector khusus untuk Resource Anda. Ini lanjutan; kuasai dahulu semua bab sebelumnya.

### 20.4 Testing otomatis

Game tidak selalu perlu pengujian otomatis, tetapi bagian yang bersifat logika murni sangat terbantu, misalnya:

- Perhitungan damage dan drop.
- Dialog runner dan percabangan flag.
- Migrasi data simpanan.
- Sistem quest.

Ada framework pengujian komunitas untuk Godot seperti GUT dan gdUnit4. Keduanya proyek komunitas; cek kompatibilitas dengan versi Godot Anda sebelum memakai. Pisahkan logika dari node (misalnya kelas `RefCounted` murni) agar mudah diuji tanpa menjalankan seluruh game.

```gdscript
# Contoh logika murni yang mudah diuji
class_name DamageCalculator
extends RefCounted

static func hitung(base: int, armor: int, crit: bool) -> int:
	var dmg := maxi(base - armor, 1)
	return dmg * 2 if crit else dmg
```

### 20.5 Playtest manual: jenis tes yang paling berharga

Tidak ada otomatisasi yang menggantikan orang sungguhan memainkan game Anda. Lakukan:

- **Playtest diam-diam**: biarkan teman memainkan tanpa Anda memberi petunjuk. Catat di mana mereka bingung, mati, atau bosan.
- **Catat bug** di daftar sederhana (spreadsheet atau papan tugas).
- **Tes dengan perangkat berbeda**: resolusi, gamepad, laptop lemah.
- **Tes jalur tidak biasa**: menyimpan di tengah dialog, memutus game saat menyimpan, melewati bagian cerita.

### 20.6 Latihan Bab 20

Siapkan repositori Git yang bersih, buat tag `v0.1.0`, dan tulis dua tes sederhana untuk `DamageCalculator` serta migrasi save.

---

## Bab 21. Export dan Rilis Game Offline

### 21.1 Menyiapkan export

1. Unduh **Export Templates** lewat **Editor > Manage Export Templates**. Versinya harus sama persis dengan versi editor Anda.
2. Buka **Project > Export**, tambahkan preset untuk platform target (Windows Desktop, Linux, macOS, Android, Web).
3. Atur nama, ikon, versi, dan opsi lain.
4. Ekspor dengan **Export Project** (bukan Export PCK, kecuali Anda memang menginginkannya).

Perbedaan penting:

- **Debug** vs **Release**: build release lebih ringan, tanpa alat debug. Rilis ke pemain memakai release.
- Opsi **Embed PCK** pada Windows memasukkan data game ke dalam satu file `.exe`, praktis untuk distribusi sederhana.
- Gunakan **Resources > Filters to exclude** untuk menyingkirkan berkas yang tidak perlu (dokumen, aset mentah) dari build.

### 21.2 Platform dan catatan khusus

**Windows**: cukup mudah. Pertimbangkan menandatangani (code signing) bila Anda ingin menghindari peringatan SmartScreen; ini berbayar dan tidak wajib untuk rilis awal. Antivirus kadang salah mendeteksi build Godot; unggah ke platform resmi (Steam atau itch.io) mengurangi masalah ini.

**Linux**: bangun sebagai biner 64-bit. Uji pada distribusi populer. Jika memakai Steam, runtime Steam membantu kompatibilitas.

**macOS**: butuh proses penandatanganan dan notarisasi bila didistribusikan di luar App Store, dan memerlukan akun pengembang Apple. Ini langkah paling merepotkan; rencanakan waktu ekstra, atau lewati macOS pada rilis awal.

**Android**: memerlukan JDK dan Android SDK serta keystore untuk menandatangani. Atur izin seminimal mungkin. Untuk game offline murni, tidak butuh izin Internet. Perhatikan ukuran layar dan kontrol sentuh yang berbeda; menyesuaikan game aksi presisi ke sentuh bukan pekerjaan kecil.

**Web (HTML5)**: bisa dimainkan di browser, tetapi ada keterbatasan (audio perlu interaksi pengguna, ukuran unduhan, dan persyaratan header tertentu untuk fitur thread). Bagus untuk demo gratis di itch.io. Uji dengan serius sebelum dijadikan rilis utama.

### 21.3 Menjamin game benar-benar offline

- Jangan menyertakan kode jaringan atau analitik pihak ketiga yang meminta koneksi.
- Jangan membutuhkan akun atau login untuk bermain.
- Pastikan semua aset tertanam; tidak ada unduhan saat runtime.
- Uji game dengan koneksi internet dimatikan.
- Simpan semua progres secara lokal (Bab 14).

Keuntungan: game Anda tetap berfungsi bertahun-tahun ke depan tanpa server yang harus dirawat, dan Anda tidak perlu menulis kebijakan privasi yang rumit karena tidak ada data pemain yang dikirim keluar. Tetap periksa persyaratan hukum di wilayah Anda dan syarat toko tempat Anda merilis.

### 21.4 Opsi distribusi

- **itch.io**: ramah indie, pengaturan mudah, cocok untuk demo dan game jam.
- **Steam**: jangkauan terbesar; ada biaya pendaftaran per game dan proses peninjauan halaman toko. Untuk game offline, fitur Steam seperti Achievements dan Cloud Save bersifat opsional. Ada integrasi komunitas (misalnya GodotSteam) bila ingin memakai fitur Steam.
- **Toko lain** (misalnya GOG, Google Play, Epic): masing-masing punya syarat dan proses berbeda. Periksa langsung persyaratan terbaru di situs resmi mereka.

Karena kebijakan dan biaya toko dapat berubah, selalu verifikasi di situs resmi sebelum merencanakan anggaran.

### 21.5 Halaman toko dan pemasaran yang tepat

Untuk game indie, pemasaran sama pentingnya dengan pengembangan:

- **Trailer** 30 sampai 60 detik yang langsung memperlihatkan gameplay dalam 5 detik pertama.
- **Tangkapan layar** yang menunjukkan variasi (aksi, boss, lingkungan, UI).
- **GIF pendek** yang menonjolkan game feel.
- **Deskripsi** singkat yang menekankan gameplay, bukan hanya cerita.
- **Demo** gratis yang menarik; bangun daftar keinginan (wishlist) sejak lama sebelum rilis.
- **Devlog** reguler di media sosial dan komunitas game indie.

### 21.6 Pembaruan pasca-rilis dan kompatibilitas save

Rencanakan pembaruan sejak awal:

- Naikkan `SAVE_VERSION` bila struktur simpanan berubah dan sediakan migrasi (Bab 14).
- Jangan mengganti ID item atau flag yang sudah dirilis tanpa alias.
- Catat perubahan di `CHANGELOG.md`.
- Gunakan penomoran versi semantik (mayor.minor.patch).

### 21.7 Latihan Bab 21

Ekspor build release untuk platform Anda, lalu uji pada komputer lain (atau mesin virtual) tanpa Godot terpasang, dengan koneksi internet dimatikan.

---

## Bab 22. Proyek Penutup (Capstone) dan Peta Jalan

### 22.1 Rancangan proyek: "Lentera Terakhir" (contoh)

Gunakan contoh ini sebagai kerangka, atau ganti dengan ide Anda sendiri.

**Premis**: Dunia yang tenggelam dalam kabut. Seorang penjaga lentera menjelajahi reruntuhan untuk menyalakan kembali lima mercusuar kuno.

**Genre**: Platformer aksi 2D bergaya Metroidvania ringan, offline, single player.

**Pilar desain**:

1. Gerak dan pertarungan yang presisi dan adil.
2. Eksplorasi yang selalu memberi hadiah (jalan pintas, rahasia, lore).
3. Dunia bercerita lewat lingkungan dan musik.

**Core loop**: jelajahi area, hadapi musuh, temukan item dan lore, kalahkan penjaga mercusuar, buka kemampuan baru, jelajahi area yang tadinya terkunci.

**Skop minimum (MVP)**:

- 1 pemain dengan: lari, lompat variabel, dash, serangan.
- 3 jenis musuh dan 1 boss.
- 6 sampai 8 ruangan yang tersambung.
- 1 kemampuan baru yang membuka area (misalnya lompat ganda).
- Sistem dialog dengan 2 NPC dan 5 catatan lore.
- Save/load, menu pengaturan, dua bahasa.
- Satu lagu area, satu lagu boss, SFX lengkap.

**Cerita tanpa suara pengisi**: dialog teks dengan blip, potret karakter, catatan tersebar, mural di dinding, dan motif musik untuk penjaga lentera.

### 22.2 Peta jalan 12 minggu (contoh untuk solo developer paruh waktu)

|Minggu|Fokus|Hasil|
|---|---|---|
|1|Desain satu halaman, setup proyek, Git|Proyek kosong rapi|
|2|Player controller (Bab 7)|Gerak terasa enak di graybox|
|3|Hitbox, hurtbox, health, combat dasar (Bab 8 dan 9)|Bisa memukul dan terluka|
|4|Satu musuh lengkap dengan state machine|Musuh pertama|
|5|TileMapLayer, kamera, 3 ruangan (Bab 11)|Level pertama|
|6|Animasi dan juice (Bab 10 dan 17)|Terasa hidup|
|7|Dialog, flag, NPC (Bab 12 dan 13)|Cerita dasar|
|8|Save/load dan pengaturan (Bab 14 dan 15)|Bisa menyimpan|
|9|Boss dan kemampuan baru|Puncak game|
|10|Audio, musik, dan ambience (Bab 16)|Suasana|
|11|Lokalisasi, profil performa, perbaikan bug (Bab 18 dan 19)|Stabil|
|12|Playtest, export, halaman toko (Bab 21)|Siap rilis demo|

Jadwal ini hanya contoh. Pekerjaan nyata hampir selalu lebih lama. Yang penting adalah **selalu memiliki build yang bisa dimainkan** di setiap akhir minggu.

### 22.3 Cara menghindari jebakan yang umum bagi developer indie

1. **Scope creep (skop membengkak)**: tulis daftar "tidak akan dikerjakan di versi 1.0" dan patuhi.
2. **Polesan terlalu dini**: graybox dulu, seni belakangan.
3. **Mengejar kesempurnaan teknis**: kode yang bekerja dan terbaca lebih baik daripada arsitektur sempurna yang tak pernah selesai.
4. **Tidak memainkan game sendiri dan tidak meminta orang lain bermain**.
5. **Burnout**: jaga ritme, tidur cukup, rayakan milestone kecil.
6. **Melupakan bagian membosankan**: menu, pengaturan, save, kredit, dan halaman toko memerlukan waktu nyata.

### 22.4 Setelah buku ini

Langkah berikutnya sesuai minat Anda:

- **Pendalaman gameplay**: pelajari desain level, desain pertarungan, dan balancing (buku dan talk tentang game design).
- **Pendalaman teknis**: GDExtension (untuk performa ekstrem), shader lanjutan, generasi prosedural.
- **Prosedural**: generasi ruangan acak untuk roguelite (algoritma BSP, random walk, wave function collapse).
- **Seni dan animasi**: pixel art, animasi frame-by-frame, atau animasi tulang 2D (Skeleton2D).
- **Bisnis game**: pemasaran, manajemen komunitas, penetapan harga.
- **Mengikuti game jam**: cara tercepat untuk melatih menyelesaikan game dari awal sampai akhir.

---

## Lampiran A. Glosarium

|Istilah|Arti sederhana|
|---|---|
|Node|Unit dasar di Godot; setiap objek di game adalah node.|
|Scene|Kumpulan node yang disimpan sebagai satu file; bisa dipakai ulang seperti prefab.|
|Signal|Pemberitahuan antar node saat suatu kejadian terjadi.|
|Autoload|Skrip atau scene yang dimuat otomatis dan dapat diakses global.|
|Resource|Wadah data yang bisa disimpan sebagai file (`.tres`).|
|Komposisi|Membangun objek dari bagian-bagian kecil, bukan dari pewarisan yang dalam.|
|State machine|Pola yang memastikan hanya satu "keadaan" aktif pada satu waktu.|
|Hitbox|Area yang menyakiti.|
|Hurtbox|Area yang bisa disakiti.|
|I-frame|Waktu kebal singkat setelah terkena serangan.|
|Coyote time|Toleransi melompat sesaat setelah meninggalkan tepi platform.|
|Jump buffer|Menyimpan input lompat sesaat sebelum mendarat.|
|Game feel|Rasa kontrol dan umpan balik pada permainan.|
|Juice|Efek visual dan audio yang memperkuat aksi.|
|Hitstop|Jeda sangat singkat saat serangan mengenai sasaran.|
|Telegraph / tell|Tanda sebelum musuh menyerang.|
|Core loop|Siklus aksi inti yang diulang pemain.|
|Graybox|Prototipe level dengan bentuk polos tanpa seni final.|
|Metroidvania|Genre eksplorasi dengan area terkunci yang terbuka lewat kemampuan baru.|
|Roguelite|Genre dengan elemen acak dan progres antar-percobaan.|
|Environmental storytelling|Bercerita lewat tata letak dan detail lingkungan.|
|Leitmotif|Melodi khas yang terkait dengan tokoh atau tema.|
|Lore|Latar belakang dan sejarah dunia game.|
|Flag|Penanda status (misalnya "boss sudah dikalahkan").|
|Tween|Animasi nilai dari awal ke akhir lewat kode.|
|Shader|Program GPU yang mengubah tampilan.|
|Object pooling|Mendaur ulang objek agar tidak sering dibuat dan dihapus.|
|Lokalisasi|Menyesuaikan game ke bahasa dan budaya lain.|
|Export template|Berkas mesin yang dipakai untuk membangun game ke platform tertentu.|
|MVP|Versi minimal yang sudah bisa dimainkan dan menunjukkan inti game.|
|Playtest|Sesi di mana orang memainkan game untuk menemukan masalah.|

---

## Lampiran B. Cheat Sheet

### B.1 Pola kode yang sering dipakai

```gdscript
# Referensi node
@onready var sprite: Sprite2D = $Sprite2D
@onready var label: Label = %NamaLabel   # Unique Name

# Input
Input.is_action_pressed(&"move_left")
Input.is_action_just_pressed(&"jump")
Input.get_axis(&"move_left", &"move_right")
Input.get_vector(&"move_left", &"move_right", &"move_up", &"move_down")

# Timer sekali jalan
await get_tree().create_timer(1.0).timeout

# Tween
var tw := create_tween()
tw.tween_property(node, "modulate:a", 0.0, 0.3)

# Grup
add_to_group(&"enemy")
get_tree().get_nodes_in_group(&"enemy")
get_tree().get_first_node_in_group(&"player")

# Instance scene
var obj := scene.instantiate()
add_child(obj)

# Hapus aman
queue_free()
if is_instance_valid(ref): ref.queue_free()

# Perubahan fisika aman
set_deferred("monitoring", false)
call_deferred("add_child", obj)

# Pindah scene
get_tree().change_scene_to_file("res://scenes/levels/level_02.tscn")

# Jeda
get_tree().paused = true

# Acak
randf_range(0.9, 1.1)
randi_range(1, 6)
[a, b, c].pick_random()

# Matematika berguna
lerpf(a, b, t)
move_toward(a, b, langkah)
clampf(x, min, maks)
signf(x)
absf(x)
```

### B.2 Arsitektur ringkas

```text
Autoload (global):
  EventBus, GameState, SaveManager, SceneManager,
  AudioManager, Settings, DialogueRunner, ItemDB

Per scene (komposisi):
  Actor + HealthComponent + Hurtbox + Hitbox + StateMachine

Data (Resource):
  ItemData, EnemyData, DialogueData, QuestData, CodexEntry

Aturan:
  Panggil ke bawah, sinyal ke atas.
  Data di Resource, logika di script, status runtime di node.
  Simpan data, bukan node.
```

### B.3 Urutan prioritas pengembangan

1. Gerak dan kamera enak.
2. Pertarungan dasar yang adil.
3. Satu level yang seru (graybox).
4. Loop lengkap: mulai, bermain, mati/menang, ulang.
5. Save dan menu.
6. Cerita dan lore di atas gameplay yang sudah solid.
7. Polesan: animasi, audio, efek.
8. Lokalisasi, performa, playtest, rilis.

---

## Lampiran C. Checklist Sebelum Rilis

**Gameplay**

- [ ] Kontrol responsif; coyote time dan jump buffer diuji.
- [ ] Tingkat kesulitan diuji oleh minimal 5 orang berbeda.
- [ ] Tidak ada jalan buntu yang membuat game tidak bisa diselesaikan (soft lock).
- [ ] Checkpoint adil.
- [ ] Boss dan musuh memiliki tell yang jelas.

**Cerita dan lore**

- [ ] Jalur utama dapat diikuti tanpa membaca lore opsional.
- [ ] Semua teks sudah dikoreksi ejaan dan tata bahasa.
- [ ] Nama dan istilah konsisten dengan glosarium dunia.
- [ ] Dialog dapat dilewati dan kecepatannya dapat diatur.

**Teknis**

- [ ] Save/load diuji, termasuk file rusak dan pembaruan versi.
- [ ] Game berjalan stabil pada perangkat minimum.
- [ ] Build release diuji pada komputer lain tanpa Godot.
- [ ] Diuji tanpa koneksi internet.
- [ ] Tidak ada error atau peringatan penting di log.
- [ ] Pengaturan tersimpan dan dimuat benar.

**Aksesibilitas dan kenyamanan**

- [ ] Remap kontrol berfungsi; gamepad didukung.
- [ ] Opsi mengurangi screen shake dan efek berkedip.
- [ ] Ukuran teks terbaca; kontras memadai.
- [ ] Volume musik, SFX terpisah.

**Aset dan hukum**

- [ ] Semua aset memiliki lisensi yang jelas dan dicatat di `CREDITS.md`.
- [ ] Layar kredit lengkap.
- [ ] Lisensi Godot (MIT) dan pihak ketiga dicantumkan sesuai ketentuan.

**Rilis**

- [ ] Halaman toko lengkap (trailer, tangkapan layar, deskripsi).
- [ ] Demo atau trailer sudah dibagikan ke calon pemain.
- [ ] Rencana pembaruan awal (patch hari pertama) disiapkan.
- [ ] Cadangan seluruh proyek tersimpan di dua tempat.

---

## Lampiran D. Sumber Belajar

Gunakan sumber resmi sebagai rujukan utama karena paling mutakhir:

- Dokumentasi resmi Godot: `docs.godotengine.org` (pilih versi yang Anda pakai).
- Situs dan blog resmi Godot: `godotengine.org` (catatan rilis tiap versi).
- Demo resmi Godot (repositori contoh proyek): cari "godot-demo-projects" di GitHub.
- Komunitas: forum dan Discord resmi Godot, serta komunitas pengembang game Indonesia di media sosial.
- Game jam (misalnya yang diselenggarakan di itch.io) untuk latihan menyelesaikan game kecil.

Catatan: tautan, nama add-on, dan fitur pada ekosistem Godot dapat berubah dari waktu ke waktu. Verifikasi selalu di sumber resmi sebelum mengandalkannya untuk proyek besar.

---

## Penutup

Anda sekarang memiliki peta lengkap untuk membangun game 2D offline yang utuh dengan Godot: dari fondasi proyek, gerak yang terasa enak, pertarungan yang adil, penyampaian cerita tanpa suara pengisi, hingga rilis. Kunci sukses indie bukan menguasai semua fitur, tetapi **menyelesaikan satu game kecil yang dipoles dengan baik**, lalu belajar dari reaksi pemain dan membuat yang berikutnya lebih baik.

Mulailah dari yang paling kecil: satu karakter yang gerakannya enak dan satu ruangan yang seru. Sisanya dibangun selapis demi selapis.

Selamat berkarya.