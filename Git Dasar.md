# Buku Pembelajaran Backend Developer

## Seri 1: Version Control System dengan Git (Tingkat Dasar)

Edisi: 2026/2027 dan seterusnya Bahasa: Indonesia Target pembaca: pemula yang baru memulai perjalanan menjadi Backend Developer

---

## Daftar Isi

1. Cara Menggunakan Buku Ini
2. Bab 1 - Mengenal Version Control System
3. Bab 2 - Instalasi dan Konfigurasi Awal Git
4. Bab 3 - Konsep Inti Git
5. Bab 4 - Alur Kerja Dasar: init, add, commit
6. Bab 5 - Membaca Riwayat dan Perbedaan Perubahan
7. Bab 6 - Membatalkan dan Memperbaiki Perubahan
8. Bab 7 - File .gitignore
9. Bab 8 - Branching dan Merging
10. Bab 9 - Menangani Merge Conflict
11. Bab 10 - Remote Repository (GitHub, GitLab, dan sejenisnya)
12. Bab 11 - Alur Kolaborasi dengan Pull Request
13. Bab 12 - Fitur Pendukung: stash, tag, blame
14. Bab 13 - Praktik Baik (Best Practices)
15. Bab 14 - Troubleshooting Masalah Umum
16. Bab 15 - Proyek Latihan Akhir
17. Lampiran A - Cheat Sheet Perintah
18. Lampiran B - Glosarium
19. Lampiran C - Kuis dan Kunci Jawaban
20. Lampiran D - Referensi Lanjutan

---

## Cara Menggunakan Buku Ini

### Untuk siapa buku ini

Buku ini ditulis untuk Anda yang belum pernah memakai Git sama sekali, atau pernah memakainya tetapi hanya menghafal perintah tanpa memahami alasannya. Anda tidak perlu pengalaman pemrograman yang dalam. Cukup mampu membuka terminal dan membuat file teks.

### Mengapa Git penting untuk Backend Developer

Seorang Backend Developer bekerja dengan kode yang terus berubah: API, logika bisnis, skema database, konfigurasi server, skrip deployment. Hampir semua tim engineering di dunia memakai Git untuk mengelola perubahan tersebut. Tanpa Git, Anda akan kesulitan:

- Bekerja bersama anggota tim di kode yang sama.
- Kembali ke versi kode yang masih berfungsi saat terjadi bug di production.
- Mengikuti proses code review dan CI/CD (pipeline otomatis untuk test dan deploy).
- Mengikuti proyek open source.

Kemampuan Git dasar hampir selalu menjadi syarat implisit di lowongan Backend Developer.

### Cara belajar yang disarankan

1. Baca satu bab, lalu langsung praktikkan semua contoh di terminal Anda sendiri.
2. Jangan hanya menyalin perintah. Setelah menjalankan perintah, perhatikan keluarannya dan cocokkan dengan penjelasan di buku.
3. Kerjakan latihan di akhir bab penting. Kunci jawaban ada di Lampiran C dan Bab 15.
4. Jangan takut salah. Selama Anda berlatih di folder percobaan, tidak ada yang bisa rusak.

### Konvensi penulisan

- Blok kode berawalan `$` menunjukkan perintah yang Anda ketik di terminal. Tanda `$` itu sendiri tidak ikut diketik.
- Baris tanpa `$` di bawah perintah adalah contoh keluaran (output). Keluaran di komputer Anda bisa sedikit berbeda, misalnya hash commit dan tanggal.
- Teks dalam tanda kurung siku seperti `<nama-branch>` adalah placeholder. Ganti dengan nilai Anda sendiri, tanpa tanda kurung sikunya.

### Catatan tentang versi

Git terus berkembang. Perintah inti seperti `add`, `commit`, `branch`, dan `merge` sangat stabil dan tidak banyak berubah selama bertahun-tahun. Beberapa perintah yang lebih baru (misalnya `git switch` dan `git restore`) sudah menjadi standar modern dan dipakai di buku ini. Untuk detail terbaru, selalu cek dokumentasi resmi di https://git-scm.com/doc.

---

# Bab 1 - Mengenal Version Control System

## 1.1 Masalah yang ingin diselesaikan

Bayangkan Anda sedang mengerjakan tugas dan menyimpan file seperti ini:

```
laporan.docx
laporan_revisi.docx
laporan_revisi2.docx
laporan_final.docx
laporan_final_BENERAN.docx
laporan_final_BENERAN_fix.docx
```

Masalahnya jelas:

- Mana yang versi terbaru? Anda harus menebak.
- Apa yang berubah antara versi 2 dan versi 3? Anda harus membandingkan manual.
- Jika dikerjakan berdua, siapa yang mengubah apa? Tidak jelas.
- Folder cepat penuh dan berantakan.

Dalam pemrograman masalahnya lebih serius, karena satu proyek bisa berisi ratusan hingga ribuan file, dan satu perubahan kecil bisa merusak fitur lain.

## 1.2 Definisi Version Control System (VCS)

**Version Control System (VCS)**, atau sistem kendali versi, adalah perangkat lunak yang:

1. **Merekam** setiap perubahan pada sekumpulan file dari waktu ke waktu.
2. **Menyimpan riwayat** lengkap: siapa mengubah, kapan, dan mengapa.
3. **Memungkinkan Anda kembali** ke kondisi file pada titik waktu mana pun.
4. **Memfasilitasi kerja tim** sehingga banyak orang bisa mengubah proyek yang sama tanpa saling menimpa pekerjaan.

Analogi sederhana: VCS itu seperti fitur "riwayat versi" di dokumen online, tetapi jauh lebih canggih, dan Anda yang mengontrol kapan sebuah versi dicatat beserta penjelasannya.

## 1.3 Tiga generasi VCS

### a. VCS Lokal

Riwayat disimpan hanya di komputer Anda sendiri. Contoh: RCS. Kelemahan: tidak cocok untuk kerja tim, dan jika disk rusak, semua riwayat hilang.

### b. VCS Terpusat (Centralized VCS)

Ada satu server pusat yang menyimpan semua riwayat. Developer mengambil (checkout) file dari server itu. Contoh: Subversion (SVN), CVS.

```
          +----------------+
          |  Server Pusat  |
          |  (semua versi) |
          +----------------+
           /      |       \
    Developer A  Dev B   Dev C
```

Kelemahan: jika server mati, tidak ada yang bisa menyimpan versi baru atau melihat riwayat. Jika server rusak tanpa backup, riwayat bisa hilang.

### c. VCS Terdistribusi (Distributed VCS)

Setiap developer memiliki **salinan lengkap** repository, termasuk seluruh riwayatnya. Contoh: **Git**, Mercurial.

```
   +-----------------+
   | Remote (GitHub) |
   +-----------------+
     /      |       \
 +------+ +------+ +------+
 | Dev A| | Dev B| | Dev C|
 | full | | full | | full |
 | copy | | copy | | copy |
 +------+ +------+ +------+
```

Keunggulan:

- Hampir semua operasi berjalan lokal, sehingga cepat dan bisa dilakukan tanpa internet.
- Setiap salinan adalah backup lengkap.
- Fleksibel dalam alur kerja (workflow) tim.

## 1.4 Apa itu Git

**Git** adalah VCS terdistribusi yang dibuat oleh Linus Torvalds pada tahun 2005 untuk mengelola pengembangan kernel Linux. Git bersifat open source dan gratis. Saat ini Git adalah standar de facto di industri perangkat lunak.

Penting dipahami sejak awal:

|Istilah|Penjelasan|
|---|---|
|**Git**|Program/alat yang berjalan di komputer Anda. Fungsinya mengelola versi.|
|**GitHub, GitLab, Bitbucket**|Layanan web untuk menyimpan repository Git secara online dan berkolaborasi. Mereka **bukan** Git itu sendiri.|

Anda bisa memakai Git sepenuhnya tanpa GitHub. Sebaliknya, GitHub hanyalah salah satu tempat untuk menaruh repository Git.

## 1.5 Rangkuman Bab 1

- VCS merekam riwayat perubahan dan memudahkan kerja tim.
- Ada VCS lokal, terpusat, dan terdistribusi. Git termasuk yang terdistribusi.
- Git adalah alat; GitHub/GitLab adalah layanan hosting.

---

# Bab 2 - Instalasi dan Konfigurasi Awal Git

## 2.1 Memasang Git

### Windows

1. Unduh installer dari https://git-scm.com/downloads.
2. Jalankan installer. Untuk pemula, pengaturan bawaan (default) umumnya sudah baik.
3. Installer ini juga menyertakan **Git Bash**, yaitu terminal bergaya Linux yang nyaman untuk mengikuti buku ini.

Alternatif lewat terminal (jika memakai winget):

```
$ winget install --id Git.Git -e
```

### macOS

Cara termudah: pasang lewat Homebrew.

```
$ brew install git
```

Atau jalankan `git --version`; jika belum terpasang, macOS biasanya menawarkan pemasangan Xcode Command Line Tools.

### Linux

Debian/Ubuntu dan turunannya:

```
$ sudo apt update
$ sudo apt install git
```

Fedora:

```
$ sudo dnf install git
```

Arch Linux:

```
$ sudo pacman -S git
```

## 2.2 Memeriksa instalasi

```
$ git --version
git version 2.xx.x
```

Angka versi di komputer Anda mungkin berbeda. Selama perintah ini menampilkan nomor versi, Git sudah terpasang.

## 2.3 Konfigurasi identitas (wajib)

Setiap commit yang Anda buat mencatat nama dan email pembuatnya. Karena itu Anda perlu mengaturnya satu kali:

```
$ git config --global user.name "Nama Anda"
$ git config --global user.email "email@contoh.com"
```

Jika Anda memakai GitHub, gunakan email yang sama dengan yang terdaftar di akun GitHub Anda (atau alamat email "noreply" yang disediakan GitHub di pengaturan akun) agar commit terhubung dengan profil Anda.

## 2.4 Konfigurasi yang sangat disarankan

### Nama branch awal

Secara historis Git memakai nama `master` untuk branch awal. Hampir semua layanan hosting dan tim kini memakai `main`. Atur agar repository baru Anda memakai `main`:

```
$ git config --global init.defaultBranch main
```

### Editor teks

Saat Git meminta Anda menulis pesan (misalnya pada merge), Git membuka editor. Jika Anda tidak ingin terjebak di editor Vim, tentukan editor yang Anda kuasai. Contoh untuk VS Code:

```
$ git config --global core.editor "code --wait"
```

### Penanganan akhir baris (line ending)

Windows memakai `CRLF`, sedangkan Linux/macOS memakai `LF`. Perbedaan ini bisa memunculkan perubahan "palsu" di Git.

- Pengguna Windows:

```
$ git config --global core.autocrlf true
```

- Pengguna macOS/Linux:

```
$ git config --global core.autocrlf input
```

### Melihat semua konfigurasi

```
$ git config --list
```

Untuk melihat satu nilai saja:

```
$ git config user.name
```

## 2.5 Tiga tingkat konfigurasi

|Tingkat|Opsi|Berlaku untuk|Lokasi file (umum)|
|---|---|---|---|
|System|`--system`|Semua user di komputer|Folder instalasi Git|
|Global|`--global`|Semua repository milik user Anda|`~/.gitconfig`|
|Local|`--local` (default)|Hanya repository saat ini|`.git/config`|

Tingkat yang lebih spesifik menimpa yang lebih umum. Contoh: Anda memakai email pribadi secara global, tetapi di satu repository kantor ingin memakai email kantor:

```
$ cd proyek-kantor
$ git config user.email "nama@perusahaan.com"
```

## 2.6 Meminta bantuan dari Git sendiri

```
$ git help commit
$ git commit --help
$ git commit -h
```

Perintah pertama dan kedua membuka manual lengkap. Yang ketiga hanya menampilkan ringkasan opsi.

## 2.7 Latihan Bab 2

1. Pasang Git dan jalankan `git --version`.
2. Atur `user.name`, `user.email`, dan `init.defaultBranch`.
3. Jalankan `git config --list` dan pastikan ketiga nilai tadi muncul.

---

# Bab 3 - Konsep Inti Git

Bab ini paling penting. Jika konsep di bab ini benar-benar Anda pahami, sisa buku akan terasa jauh lebih mudah.

## 3.1 Repository

**Repository** (sering disingkat repo) adalah folder proyek yang dikelola Git, lengkap dengan seluruh riwayat perubahannya. Riwayat itu disimpan di folder tersembunyi bernama `.git` di dalam folder proyek.

```
proyek-saya/
  |-- .git/          <- "otak" Git: riwayat, konfigurasi, dsb. JANGAN dihapus/diedit manual
  |-- src/
  |-- README.md
```

Jika folder `.git` dihapus, folder tersebut kembali menjadi folder biasa dan seluruh riwayat lokal hilang.

## 3.2 Snapshot, bukan selisih

Banyak sistem lama menyimpan riwayat sebagai daftar selisih (delta) antar versi. Git berpikir berbeda: setiap kali Anda melakukan commit, Git menyimpan **snapshot** (potret) kondisi seluruh proyek pada saat itu. Untuk file yang tidak berubah, Git cukup menyimpan referensi ke versi sebelumnya sehingga tetap efisien.

Anda tidak perlu memahami detail internalnya sekarang. Cukup ingat: **commit = potret kondisi proyek pada satu titik waktu.**

## 3.3 Tiga area kerja

Ini konsep yang paling sering membingungkan pemula. Git memiliki tiga area utama:

```
 Working Directory        Staging Area            Repository (.git)
 (folder kerja)           (index)                 (riwayat commit)
 +----------------+  add  +----------------+ commit +----------------+
 |  Anda mengedit |-----> | Calon isi      |------> | Snapshot       |
 |  file di sini  |       | commit berikut |        | tersimpan      |
 +----------------+       +----------------+        +----------------+
        ^                                                   |
        |__________________ checkout / switch / restore ____|
```

1. **Working Directory (folder kerja)**: file-file yang tampak di folder Anda dan yang Anda edit dengan editor.
2. **Staging Area (index)**: "ruang tunggu" tempat Anda menyiapkan perubahan mana yang akan dimasukkan ke commit berikutnya.
3. **Repository**: tempat commit-commit yang sudah resmi tersimpan.

Analogi: bayangkan Anda mengemas barang untuk pindahan.

- Barang yang tersebar di rumah = working directory.
- Barang yang sudah Anda taruh di kardus tetapi belum ditutup = staging area.
- Kardus yang sudah ditutup, diberi label, dan disegel = commit.

Mengapa ada staging area? Agar Anda bisa memilih. Misalnya Anda mengubah 5 file, tetapi hanya 2 file yang berkaitan dengan fitur login. Anda bisa menaruh 2 file itu di staging, membuat satu commit khusus login, lalu 3 file sisanya di commit lain. Hasilnya riwayat yang rapi dan mudah dipahami.

## 3.4 Status file

Setiap file di proyek Anda berada dalam salah satu kondisi berikut:

|Status|Arti|
|---|---|
|**Untracked**|File baru yang belum pernah dikenal Git.|
|**Unmodified**|File dikenal Git dan isinya sama dengan commit terakhir.|
|**Modified**|File dikenal Git dan isinya sudah berubah, tetapi belum di-stage.|
|**Staged**|Perubahan sudah dimasukkan ke staging area, siap di-commit.|

Alur hidupnya:

```
Untracked --add--> Staged --commit--> Unmodified --edit--> Modified --add--> Staged
```

## 3.5 Commit

**Commit** adalah satu titik tersimpan dalam riwayat. Setiap commit memiliki:

- **Hash**: pengenal unik berupa deretan karakter heksadesimal, misalnya `a3f9c2e1b7d4...`. Anda biasanya cukup memakai 7 karakter pertama (`a3f9c2e`).
- **Author**: nama dan email pembuat.
- **Tanggal dan waktu.**
- **Pesan commit**: penjelasan singkat tentang perubahan.
- **Parent**: referensi ke commit sebelumnya. Inilah yang membentuk rantai riwayat.

```
 [A] <-- [B] <-- [C] <-- [D]
```

Panah menunjuk ke parent (commit sebelumnya). Semakin ke kanan, semakin baru.

## 3.6 Branch

**Branch** adalah "jalur" pengembangan. Secara teknis, branch hanyalah **penunjuk (pointer) bergerak** ke sebuah commit. Dengan branch Anda bisa mengembangkan fitur baru tanpa mengganggu kode utama.

```
              fitur-login
                   |
                   v
 [A] <-- [B] <-- [E] <-- [F]
          ^
          |
        [C] <-- [D]
                 ^
                 |
               main
```

Pada bab 8 kita akan membahas ini dengan praktik langsung.

## 3.7 HEAD

**HEAD** adalah penunjuk yang menandai "Anda sedang berada di mana" saat ini. Biasanya HEAD menunjuk ke sebuah branch, dan branch itu menunjuk ke commit terbaru di branch tersebut. Saat Anda membuat commit baru, branch yang ditunjuk HEAD bergerak maju.

## 3.8 Remote

**Remote** adalah versi repository Anda yang berada di tempat lain (biasanya server seperti GitHub). Remote standar biasanya bernama **origin**. Bab 10 membahasnya.

## 3.9 Rangkuman Bab 3

- Repository = folder proyek + riwayat di `.git`.
- Commit = snapshot proyek dengan pesan dan hash unik.
- Tiga area: working directory, staging area, repository.
- Branch = pointer ke commit; HEAD = posisi Anda saat ini.
- Remote = repository di tempat lain, umumnya bernama `origin`.

---

# Bab 4 - Alur Kerja Dasar: init, add, commit

Sekarang kita praktik. Siapkan terminal (Git Bash di Windows, Terminal di macOS/Linux).

## 4.1 Menyiapkan folder latihan

```
$ mkdir belajar-git
$ cd belajar-git
```

## 4.2 `git init` - membuat repository

```
$ git init
Initialized empty Git repository in /.../belajar-git/.git/
```

Perintah ini membuat folder `.git` dan menjadikan folder saat ini sebuah repository. Cukup dijalankan satu kali per proyek.

Untuk melihat folder tersembunyi:

```
$ ls -a
.  ..  .git
```

## 4.3 `git status` - perintah yang paling sering dipakai

```
$ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Biasakan menjalankan `git status` sesering mungkin. Perintah ini aman (tidak mengubah apa pun) dan selalu memberi tahu kondisi terkini serta langkah selanjutnya.

## 4.4 Membuat file pertama

Buat file `README.md`:

```
$ echo "# Belajar Git" > README.md
```

Cek status:

```
$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```

File `README.md` berstatus **untracked**: ada di folder kerja, tetapi belum dikenal Git.

## 4.5 `git add` - memasukkan ke staging area

```
$ git add README.md
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```

Sekarang file berstatus **staged** ("Changes to be committed").

Variasi `git add` yang sering dipakai:

|Perintah|Fungsi|
|---|---|
|`git add nama-file`|Stage satu file.|
|`git add file1 file2`|Stage beberapa file tertentu.|
|`git add folder/`|Stage semua perubahan di dalam satu folder.|
|`git add .`|Stage semua perubahan di folder saat ini dan sub-foldernya.|
|`git add -p`|Mode interaktif: pilih potongan (hunk) perubahan satu per satu.|

Peringatan untuk pemula: `git add .` praktis, tetapi hati-hati. Jika ada file sensitif (misalnya `.env` berisi password database) yang belum diabaikan lewat `.gitignore` (lihat Bab 7), file itu ikut ter-stage. Biasakan mengecek `git status` sebelum commit.

## 4.6 `git commit` - menyimpan snapshot

```
$ git commit -m "Tambah README awal"
[main (root-commit) 3b1f7a2] Tambah README awal
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

Penjelasan keluaran:

- `main`: branch tempat commit dibuat.
- `root-commit`: ini commit pertama (tidak punya parent).
- `3b1f7a2`: hash singkat commit.
- Sisanya ringkasan perubahan.

Opsi `-m` berarti "message" (pesan). Jika `-m` dihilangkan, Git membuka editor agar Anda menulis pesan yang lebih panjang.

Cek status lagi:

```
$ git status
On branch main
nothing to commit, working tree clean
```

"Working tree clean" artinya tidak ada perubahan yang belum di-commit.

## 4.7 Siklus kerja harian

Dalam praktik, siklus Anda akan berulang seperti ini:

```
1. Edit file
2. git status          (lihat apa yang berubah)
3. git diff            (lihat isi perubahannya)
4. git add ...         (pilih yang akan masuk commit)
5. git commit -m "..." (simpan snapshot)
```

Mari praktik. Ubah `README.md`:

```
$ echo "Repository ini untuk latihan Git." >> README.md
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Sekarang statusnya **modified**. Stage lalu commit:

```
$ git add README.md
$ git commit -m "Tambah deskripsi singkat di README"
```

Catatan: tanda `>>` menambahkan teks di akhir file, sedangkan `>` menimpa seluruh isi file. Hati-hati membedakannya.

## 4.8 Pintasan: `git commit -a`

```
$ git commit -am "Pesan commit"
```

Opsi `-a` otomatis men-stage semua file yang **sudah dikenal Git dan dimodifikasi**, lalu langsung commit. Opsi ini **tidak** menyertakan file untracked (file baru). Gunakan saat Anda yakin semua perubahan memang ingin dimasukkan.

## 4.9 Menulis pesan commit yang baik (pengantar)

Contoh buruk:

```
$ git commit -m "update"
$ git commit -m "fix"
$ git commit -m "asdf"
```

Contoh baik:

```
$ git commit -m "Tambah endpoint GET /users untuk daftar pengguna"
$ git commit -m "Perbaiki validasi email yang menerima string kosong"
```

Pesan commit adalah dokumentasi untuk diri Anda di masa depan dan anggota tim. Panduan lengkapnya ada di Bab 13.

## 4.10 Latihan Bab 4

1. Di folder `belajar-git`, buat file `catatan.txt` berisi satu baris bebas.
2. Jalankan `git status` dan catat statusnya.
3. Stage file tersebut, lalu jalankan `git status` lagi. Apa bedanya?
4. Commit dengan pesan yang bermakna.
5. Ubah file itu, lalu ulangi siklus stage dan commit.

---

# Bab 5 - Membaca Riwayat dan Perbedaan Perubahan

## 5.1 `git log` - melihat riwayat commit

```
$ git log
commit 8c2d9e4f1a7b6c3d5e0f9a8b7c6d5e4f3a2b1c0d (HEAD -> main)
Author: Nama Anda <email@contoh.com>
Date:   Fri Nov 6 07:30:00 2026 +0700

    Tambah deskripsi singkat di README

commit 3b1f7a2...
Author: Nama Anda <email@contoh.com>
Date:   Fri Nov 6 07:25:00 2026 +0700

    Tambah README awal
```

Commit terbaru tampil paling atas. Tekan `q` untuk keluar dari tampilan jika riwayat panjang.

Opsi yang sangat berguna:

|Perintah|Fungsi|
|---|---|
|`git log --oneline`|Satu baris per commit (hash singkat + pesan).|
|`git log --oneline --graph --all`|Tampilan grafik cabang (sangat membantu memahami branch).|
|`git log -n 5`|Hanya 5 commit terakhir.|
|`git log --author="Nama"`|Filter berdasarkan pembuat.|
|`git log -- nama-file`|Riwayat untuk satu file saja.|
|`git log --stat`|Sertakan ringkasan file yang berubah.|
|`git log -p`|Sertakan isi perubahan (patch) setiap commit.|

Contoh `--oneline`:

```
$ git log --oneline
8c2d9e4 Tambah deskripsi singkat di README
3b1f7a2 Tambah README awal
```

## 5.2 `git diff` - melihat isi perubahan

Perintah ini menunjukkan baris mana yang ditambah atau dihapus.

|Perintah|Membandingkan|
|---|---|
|`git diff`|Working directory dengan staging area (perubahan yang **belum** di-stage).|
|`git diff --staged`|Staging area dengan commit terakhir (perubahan yang **sudah** di-stage).|
|`git diff A B`|Dua commit atau dua branch.|
|`git diff HEAD`|Working directory dengan commit terakhir (staged dan unstaged sekaligus).|

Contoh keluaran:

```
$ git diff
diff --git a/README.md b/README.md
index 1a2b3c4..5d6e7f8 100644
--- a/README.md
+++ b/README.md
@@ -1,2 +1,3 @@
 # Belajar Git
 Repository ini untuk latihan Git.
+Ditambahkan baris baru.
```

Cara membaca:

- Baris berawalan `+` (biasanya hijau) adalah baris yang **ditambahkan**.
- Baris berawalan `-` (biasanya merah) adalah baris yang **dihapus**.
- Baris tanpa tanda adalah konteks yang tidak berubah.
- `@@ -1,2 +1,3 @@` menunjukkan posisi: dari baris 1 sepanjang 2 baris (lama) menjadi baris 1 sepanjang 3 baris (baru).

## 5.3 `git show` - melihat satu commit

```
$ git show 3b1f7a2
```

Menampilkan metadata dan perubahan pada commit tersebut. Tanpa argumen, `git show` menampilkan commit terakhir.

## 5.4 Cara merujuk commit

Selain hash, Anda bisa memakai:

|Penulisan|Arti|
|---|---|
|`HEAD`|Commit yang sedang Anda tempati.|
|`HEAD~1` atau `HEAD^`|Satu commit sebelum HEAD.|
|`HEAD~3`|Tiga commit sebelum HEAD.|
|`main`|Commit terbaru di branch `main`.|

Contoh: `git diff HEAD~1 HEAD` membandingkan commit sebelumnya dengan commit terakhir.

## 5.5 Latihan Bab 5

1. Buat tiga commit dengan perubahan berbeda di `catatan.txt`.
2. Jalankan `git log --oneline` dan salin hash commit kedua.
3. Jalankan `git show <hash-tersebut>` dan baca keluarannya.
4. Ubah file tanpa di-stage, jalankan `git diff`. Stage, lalu jalankan `git diff --staged`. Jelaskan perbedaan kedua keluaran.

---

# Bab 6 - Membatalkan dan Memperbaiki Perubahan

Kesalahan itu wajar. Git menyediakan beberapa cara untuk memperbaikinya, tetapi cara yang tepat bergantung pada **di mana** kesalahan itu berada (working directory, staging area, atau sudah di-commit) dan **apakah sudah dibagikan** ke orang lain.

## 6.1 Peta keputusan

```
Perubahan belum di-stage?     -> git restore <file>
Sudah di-stage, belum commit? -> git restore --staged <file>
Sudah commit, belum di-push?  -> git commit --amend   (commit terakhir)
                                 atau git reset       (beberapa commit)
Sudah commit DAN sudah di-push -> git revert <hash>   (cara aman)
```

## 6.2 Membuang perubahan di working directory: `git restore`

Mengembalikan file ke kondisi commit terakhir (atau kondisi staging):

```
$ git restore README.md
```

**Peringatan:** perubahan yang belum di-commit akan **hilang permanen** dan tidak bisa dipulihkan Git, karena Git tidak pernah merekamnya. Pastikan Anda benar-benar tidak membutuhkannya.

## 6.3 Mengeluarkan file dari staging area

Anda terlanjur `git add` file yang salah:

```
$ git restore --staged catatan.txt
```

File kembali ke status modified (perubahan isinya tetap ada, hanya keluar dari staging).

Catatan: di materi lama Anda mungkin menjumpai `git reset HEAD <file>` yang fungsinya sama. Keduanya valid, tetapi `git restore --staged` lebih jelas maksudnya.

## 6.4 Memperbaiki commit terakhir: `git commit --amend`

Skenario 1: salah menulis pesan commit.

```
$ git commit --amend -m "Pesan yang sudah diperbaiki"
```

Skenario 2: lupa menyertakan satu file.

```
$ git add file-yang-lupa.txt
$ git commit --amend --no-edit
```

Opsi `--no-edit` mempertahankan pesan lama.

**Penting:** `--amend` sebenarnya **mengganti** commit terakhir dengan commit baru (hash berubah). Karena itu, hanya gunakan pada commit yang **belum di-push** atau belum dipakai orang lain.

## 6.5 Memindahkan posisi branch: `git reset`

`git reset` memundurkan branch ke commit tertentu. Ada tiga mode utama:

|Mode|Pointer branch|Staging area|Working directory|
|---|---|---|---|
|`--soft`|Mundur|Tetap (perubahan tetap staged)|Tetap|
|`--mixed` (default)|Mundur|Dikosongkan|Tetap|
|`--hard`|Mundur|Dikosongkan|**Dikembalikan (perubahan hilang)**|

Contoh: batalkan commit terakhir tetapi pertahankan perubahannya agar bisa diedit ulang:

```
$ git reset --soft HEAD~1
```

Contoh: batalkan commit terakhir dan keluarkan dari staging, perubahan tetap ada di file:

```
$ git reset HEAD~1
```

Contoh berbahaya: buang commit terakhir **beserta** semua perubahannya:

```
$ git reset --hard HEAD~1
```

**Peringatan:** `--hard` bisa menghapus pekerjaan yang belum di-commit tanpa bisa dipulihkan. Pemula sebaiknya berhati-hati dan memakai `--soft` atau `--mixed` terlebih dahulu. Seperti `--amend`, `reset` yang mengubah riwayat sebaiknya hanya dipakai pada commit yang belum dibagikan.

## 6.6 Membatalkan dengan aman: `git revert`

Jika commit yang bermasalah sudah di-push dan mungkin sudah dipakai orang lain, **jangan ubah riwayat**. Gunakan `git revert`, yang membuat **commit baru** berisi kebalikan dari perubahan commit yang dituju.

```
$ git revert 8c2d9e4
```

Git akan membuka editor untuk pesan commit revert. Simpan dan tutup editor. Hasilnya:

```
 [A] <-- [B] <-- [C] <-- [D: Revert "C"]
```

Riwayat tetap utuh dan transparan: terlihat bahwa C pernah ada lalu dibatalkan.

## 6.7 Perbandingan reset dan revert

|Aspek|`git reset`|`git revert`|
|---|---|---|
|Cara kerja|Memundurkan pointer, riwayat "dihapus"|Menambah commit baru yang membalikkan|
|Mengubah riwayat|Ya|Tidak|
|Aman untuk commit yang sudah di-push|Tidak|Ya|
|Cocok untuk|Merapikan commit lokal|Membatalkan commit yang sudah dibagikan|

## 6.8 Jaring pengaman: `git reflog`

Jika Anda terlanjur melakukan `reset --hard` atau kehilangan commit, Git menyimpan catatan perpindahan HEAD selama beberapa waktu:

```
$ git reflog
8c2d9e4 HEAD@{0}: reset: moving to HEAD~1
3b1f7a2 HEAD@{1}: commit: Tambah deskripsi
```

Anda bisa kembali ke kondisi sebelumnya:

```
$ git reset --hard HEAD@{1}
```

Catatan: reflog hanya merekam commit. Perubahan yang **tidak pernah di-commit** tidak bisa diselamatkan. Karena itu, **commit lebih sering** adalah kebiasaan yang melindungi pekerjaan Anda. Reflog juga bersifat lokal dan entrinya akhirnya kedaluwarsa.

## 6.9 Menghapus dan memindahkan file lewat Git

```
$ git rm nama-file.txt            # hapus file dan stage penghapusannya
$ git rm --cached nama-file.txt   # berhenti melacak file, tetapi file tetap ada di disk
$ git mv nama-lama.txt nama-baru.txt  # ganti nama/pindah file
```

`git rm --cached` berguna saat Anda terlanjur melacak file yang seharusnya diabaikan (misalnya `.env`).

## 6.10 Latihan Bab 6

1. Ubah `catatan.txt`, lalu buang perubahannya dengan `git restore`. Pastikan isi file kembali seperti semula.
2. Stage sebuah perubahan lalu keluarkan dari staging dengan `git restore --staged`.
3. Buat commit dengan pesan yang salah ketik, lalu perbaiki dengan `git commit --amend`.
4. Buat dua commit percobaan, lalu pakai `git reset --soft HEAD~1`. Jalankan `git status` dan jelaskan apa yang terlihat.
5. Buat satu commit percobaan lalu batalkan dengan `git revert`. Lihat hasilnya di `git log --oneline`.

---

# Bab 7 - File .gitignore

## 7.1 Mengapa perlu mengabaikan file

Tidak semua file layak dimasukkan ke repository. Contoh yang **sebaiknya tidak** di-commit:

- **Rahasia dan kredensial**: `.env`, kunci API, password database, private key.
- **Dependensi yang bisa diunduh ulang**: `node_modules/`, `vendor/`, `venv/`, `.venv/`.
- **Hasil build/kompilasi**: `dist/`, `build/`, `target/`, `__pycache__/`, `*.class`.
- **File sistem dan editor**: `.DS_Store`, `Thumbs.db`, `.idea/`, `.vscode/` (tergantung kesepakatan tim).
- **Log dan file sementara**: `*.log`, `tmp/`.
- **Database lokal**: `*.sqlite3` untuk pengembangan lokal.

Untuk Backend Developer, poin pertama sangat krusial. Rahasia yang ter-commit dan ter-push ke repository (terutama yang publik) bisa disalahgunakan dalam hitungan menit. Mengabaikannya sejak awal adalah kebiasaan wajib.

## 7.2 Membuat .gitignore

Buat file bernama `.gitignore` di root repository. Contoh isi untuk proyek Node.js:

```
# Dependensi
node_modules/

# Rahasia dan konfigurasi lokal
.env
.env.local

# Hasil build
dist/
build/

# Log
*.log

# File sistem operasi
.DS_Store
Thumbs.db

# Editor
.idea/
```

## 7.3 Aturan penulisan pola

|Pola|Arti|
|---|---|
|`#`|Komentar.|
|`*.log`|Semua file berakhiran `.log`.|
|`node_modules/`|Folder bernama `node_modules` (tanda `/` di akhir berarti folder).|
|`/config.local.js`|Hanya file di root repository (tanda `/` di awal).|
|`!penting.log`|Pengecualian: tetap lacak file ini meskipun cocok pola lain.|
|`docs/**/*.tmp`|Semua `.tmp` di bawah `docs` pada kedalaman berapa pun.|

## 7.4 Pola berguna: file contoh konfigurasi

Praktik umum: jangan commit `.env`, tetapi commit `.env.example` yang berisi nama variabel tanpa nilai rahasia:

```
# .env.example
DATABASE_URL=
JWT_SECRET=
PORT=3000
```

Anggota tim baru cukup menyalin `.env.example` menjadi `.env` lalu mengisi nilainya.

## 7.5 Jebakan penting

`.gitignore` **hanya berlaku untuk file yang belum dilacak**. Jika sebuah file sudah pernah di-commit, menambahkannya ke `.gitignore` tidak menghapusnya dari pelacakan. Perbaikannya:

```
$ git rm --cached .env
$ git commit -m "Berhenti melacak .env"
```

Namun ingat: file itu **masih ada di riwayat lama**. Jika berisi rahasia sungguhan yang sempat ter-push, anggap rahasia itu **sudah bocor**: segera ganti (rotate) password atau kunci tersebut. Membersihkan riwayat adalah topik lanjutan.

## 7.6 Memeriksa apakah suatu file diabaikan

```
$ git check-ignore -v .env
.gitignore:4:.env       .env
```

## 7.7 Sumber template

Situs https://github.com/github/gitignore menyediakan template `.gitignore` untuk berbagai bahasa dan framework. Gunakan sebagai titik awal, lalu sesuaikan.

## 7.8 Latihan Bab 7

1. Buat file `rahasia.env` berisi teks bebas dan folder `tmp/` berisi satu file.
2. Buat `.gitignore` yang mengabaikan keduanya.
3. Jalankan `git status`. Pastikan keduanya tidak muncul sebagai untracked.
4. Commit `.gitignore` itu.

---

# Bab 8 - Branching dan Merging

## 8.1 Mengapa branch

Bayangkan tim Anda punya aplikasi yang sedang berjalan di production. Anda diminta menambah fitur baru. Jika Anda mengerjakannya langsung di jalur utama dan fitur itu belum selesai, jalur utama bisa menjadi rusak. Solusinya: buat **branch** terpisah untuk fitur tersebut. Setelah selesai dan teruji, baru digabungkan (merge) ke jalur utama.

Keuntungan branch:

- Pekerjaan yang belum selesai terisolasi dari kode yang stabil.
- Beberapa orang dapat mengerjakan fitur berbeda secara paralel.
- Murah dan cepat dibuat karena branch hanyalah pointer.

Konvensi: branch utama bernama `main` dan berisi kode yang stabil.

## 8.2 Melihat branch

```
$ git branch
* main
```

Tanda `*` menandai branch yang sedang aktif (tempat HEAD berada).

## 8.3 Membuat dan berpindah branch

Cara modern:

```
$ git switch -c fitur-profil
Switched to a new branch 'fitur-profil'
```

Opsi `-c` berarti create (buat baru). Perintah lain yang sering dipakai:

|Perintah|Fungsi|
|---|---|
|`git branch nama-branch`|Membuat branch baru tanpa berpindah.|
|`git switch nama-branch`|Berpindah ke branch yang sudah ada.|
|`git switch -c nama-branch`|Membuat lalu langsung berpindah.|
|`git switch -`|Kembali ke branch sebelumnya.|
|`git branch -d nama-branch`|Menghapus branch yang sudah di-merge.|
|`git branch -D nama-branch`|Memaksa menghapus branch (meski belum di-merge).|

Catatan: di materi lama Anda akan sering melihat `git checkout nama-branch` dan `git checkout -b nama-branch`. Keduanya masih berfungsi dan bisa Anda temui di banyak tutorial dan kode tim. Untuk pemula, `git switch` lebih mudah dipahami karena fungsinya fokus pada pindah branch.

## 8.4 Bekerja di branch

Setelah berpindah ke `fitur-profil`, buat file dan commit seperti biasa:

```
$ echo "Halaman profil pengguna" > profil.txt
$ git add profil.txt
$ git commit -m "Tambah halaman profil pengguna"
```

Lihat grafiknya:

```
$ git log --oneline --graph --all
* 5e8a1b3 (HEAD -> fitur-profil) Tambah halaman profil pengguna
* 8c2d9e4 (main) Tambah deskripsi singkat di README
* 3b1f7a2 Tambah README awal
```

Branch `main` masih berada di `8c2d9e4`. Perubahan Anda aman di `fitur-profil`. Coba pindah ke `main` dan lihat bahwa file `profil.txt` menghilang dari folder, lalu muncul lagi saat Anda kembali ke `fitur-profil`. Git mengubah isi folder kerja mengikuti branch yang aktif.

## 8.5 Menggabungkan branch: `git merge`

Aturan: **berpindah dulu ke branch penerima**, lalu merge branch sumber.

```
$ git switch main
$ git merge fitur-profil
```

### Jenis 1: Fast-forward

Terjadi jika `main` belum berubah sejak branch dibuat. Git cukup menggeser pointer `main` maju.

Sebelum:

```
 [A] <-- [B] <-- [C]
          ^        ^
        main    fitur-profil
```

Sesudah merge:

```
 [A] <-- [B] <-- [C]
                  ^
          main, fitur-profil
```

Keluaran:

```
Updating 8c2d9e4..5e8a1b3
Fast-forward
 profil.txt | 1 +
 1 file changed, 1 insertion(+)
```

### Jenis 2: Three-way merge (merge commit)

Terjadi jika `main` dan branch fitur **sama-sama** punya commit baru sejak percabangan. Git membuat **merge commit** baru yang memiliki dua parent.

Sebelum:

```
         [D] <-- [E]   <- fitur
        /
 [A] <-- [B] <-- [C]   <- main
```

Sesudah (pada main):

```
         [D] <-- [E]
        /           \
 [A] <-- [B] <-- [C] <-- [M]   <- main (M = merge commit)
```

Git akan membuka editor untuk pesan merge commit. Pesan bawaan biasanya sudah cukup; simpan dan tutup editor.

## 8.6 Membersihkan branch

Setelah fitur digabung dan tidak dibutuhkan lagi:

```
$ git branch -d fitur-profil
```

Opsi `-d` aman: Git menolak menghapus branch yang belum di-merge, sehingga Anda tidak kehilangan pekerjaan tanpa sengaja.

## 8.7 Konvensi penamaan branch

Nama yang deskriptif membantu tim. Pola umum:

```
fitur/login-jwt
perbaikan/validasi-email
hotfix/error-500-checkout
```

Atau dalam bahasa Inggris yang lazim di industri: `feature/...`, `fix/...`, `hotfix/...`, `chore/...`. Ikuti kesepakatan tim Anda. Hindari spasi; gunakan tanda hubung.

## 8.8 Sekilas tentang rebase (pengetahuan awal)

Selain merge, ada `git rebase` yang "memindahkan" commit-commit sebuah branch agar seolah-olah dibuat di atas ujung branch lain, menghasilkan riwayat yang lurus. Rebase kuat tetapi mengubah riwayat, sehingga memerlukan kehati-hatian dan bukan materi dasar. Untuk saat ini cukup ketahui bahwa rebase ada, dan fokus mahir di merge terlebih dahulu. Aturan emas rebase: jangan pernah rebase commit yang sudah dibagikan ke orang lain.

## 8.9 Latihan Bab 8

1. Buat branch `fitur-a`, tambahkan satu file dan satu commit. Merge ke `main` dan perhatikan bahwa hasilnya fast-forward.
2. Buat branch `fitur-b` dan `fitur-c` dari `main`. Beri masing-masing satu commit pada **file berbeda**. Merge keduanya ke `main` secara berurutan. Amati mana yang fast-forward dan mana yang membuat merge commit.
3. Jalankan `git log --oneline --graph --all` dan gambar ulang grafiknya di kertas.
4. Hapus branch yang sudah di-merge.

---

# Bab 9 - Menangani Merge Conflict

## 9.1 Apa itu conflict

**Merge conflict** terjadi saat Git tidak bisa menggabungkan perubahan secara otomatis, biasanya karena dua branch mengubah **baris yang sama** pada **file yang sama** dengan isi berbeda. Git tidak tahu versi mana yang benar, sehingga meminta Anda memutuskan.

Conflict bukan tanda Anda berbuat salah. Ini hal yang normal dalam kerja tim. Yang penting adalah tahu cara menyelesaikannya dengan tenang.

## 9.2 Membuat conflict untuk latihan

```
$ git switch main
$ echo "Versi: 1.0" > versi.txt
$ git add versi.txt
$ git commit -m "Tambah file versi"

$ git switch -c branch-satu
$ echo "Versi: 2.0 dari branch-satu" > versi.txt
$ git commit -am "Ubah versi di branch-satu"

$ git switch main
$ echo "Versi: 3.0 dari main" > versi.txt
$ git commit -am "Ubah versi di main"

$ git merge branch-satu
Auto-merging versi.txt
CONFLICT (content): Merge conflict in versi.txt
Automatic merge failed; fix conflicts and then commit the result.
```

## 9.3 Membaca penanda conflict

Buka `versi.txt`:

```
<<<<<<< HEAD
Versi: 3.0 dari main
=======
Versi: 2.0 dari branch-satu
>>>>>>> branch-satu
```

Artinya:

- `<<<<<<< HEAD` sampai `=======`: versi di branch Anda saat ini (`main`).
- `=======` sampai `>>>>>>> branch-satu`: versi dari branch yang sedang digabung.
- Tanda-tanda itu sendiri **bukan** isi file; harus dihapus.

## 9.4 Langkah penyelesaian

1. Jalankan `git status` untuk melihat file mana yang conflict (bagian "Unmerged paths").
2. Buka file, putuskan hasil akhirnya: ambil salah satu, ambil dua-duanya, atau tulis versi baru.
3. **Hapus** semua penanda `<<<<<<<`, `=======`, dan `>>>>>>>`.
4. Simpan file.
5. `git add nama-file` untuk menandai conflict selesai.
6. `git commit` untuk menyelesaikan merge (pesan bawaan biasanya sudah cukup).

Misalnya Anda memutuskan hasil akhir:

```
Versi: 3.0
```

Lalu:

```
$ git add versi.txt
$ git commit
```

## 9.5 Membatalkan merge

Jika Anda bingung dan ingin mengulang dari awal:

```
$ git merge --abort
```

Repository kembali ke kondisi sebelum merge dimulai.

## 9.6 Tips mengurangi conflict

- Merge atau ambil perubahan terbaru dari `main` ke branch Anda secara berkala, jangan menunggu berminggu-minggu.
- Buat branch yang kecil dan fokus, lalu selesaikan dengan cepat.
- Komunikasikan dengan tim siapa mengerjakan file apa.
- Gunakan editor yang mendukung tampilan conflict (VS Code menampilkan tombol "Accept Current Change", "Accept Incoming Change", dan "Accept Both Changes").
- Setelah menyelesaikan conflict, jalankan test atau aplikasi untuk memastikan hasil gabungan tetap berfungsi. Kode yang bebas conflict secara tekstual belum tentu benar secara logika.

## 9.7 Latihan Bab 9

1. Ulangi skenario di 9.2 dan selesaikan conflict dengan memilih versi `main`.
2. Ulangi lagi, lalu coba `git merge --abort` di tengah proses.
3. Ulangi sekali lagi dan selesaikan dengan menggabungkan kedua baris menjadi satu kalimat baru.

---

# Bab 10 - Remote Repository (GitHub, GitLab, dan sejenisnya)

## 10.1 Mengapa butuh remote

Sejauh ini semua pekerjaan hanya ada di komputer Anda. Remote repository memberi Anda:

- **Backup** di luar komputer.
- **Kolaborasi**: tim berbagi kode lewat satu tempat bersama.
- **Portofolio**: profil GitHub Anda menjadi etalase karya.
- **Integrasi** dengan CI/CD, issue tracker, dan code review.

Layanan populer: GitHub, GitLab, Bitbucket. Konsep di bawah berlaku sama untuk semuanya. Contoh di buku ini memakai GitHub.

## 10.2 Menyiapkan akun dan autentikasi

1. Buat akun di https://github.com.
2. Anda perlu cara untuk membuktikan identitas saat berinteraksi dari terminal. GitHub **tidak lagi menerima password akun biasa** untuk operasi Git lewat HTTPS. Dua metode yang umum:

### Metode A: SSH key (disarankan untuk penggunaan rutin)

Buat pasangan kunci:

```
$ ssh-keygen -t ed25519 -C "email@contoh.com"
```

Tekan Enter untuk lokasi bawaan, dan sebaiknya isi passphrase. Lalu salin isi **kunci publik** (file berakhiran `.pub`):

```
$ cat ~/.ssh/id_ed25519.pub
```

Tempel ke GitHub melalui: Settings, SSH and GPG keys, New SSH key. Uji koneksi:

```
$ ssh -T git@github.com
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

Aturan keamanan: **kunci privat** (file tanpa `.pub`) tidak boleh dibagikan kepada siapa pun dan tidak boleh di-commit.

### Metode B: HTTPS dengan Personal Access Token atau Git Credential Manager

Untuk HTTPS, gunakan token akses pribadi (Personal Access Token) sebagai pengganti password, atau pakai Git Credential Manager (sudah termasuk di instalasi Git untuk Windows) yang membantu proses login lewat browser. Untuk langkah terkini, ikuti panduan resmi GitHub karena antarmukanya dapat berubah.

## 10.3 Dua cara memulai dengan remote

### Skenario 1: Mulai dari repository yang sudah ada di server: `git clone`

```
$ git clone git@github.com:username/nama-repo.git
$ cd nama-repo
```

Atau lewat HTTPS:

```
$ git clone https://github.com/username/nama-repo.git
```

`clone` mengunduh seluruh repository beserta riwayatnya dan otomatis mengatur remote bernama `origin`.

### Skenario 2: Punya repository lokal, ingin dikirim ke server

1. Buat repository kosong di GitHub (tanpa menambah README jika repository lokal Anda sudah punya commit).
2. Sambungkan remote:

```
$ git remote add origin git@github.com:username/belajar-git.git
```

3. Pastikan nama branch lokal adalah `main`, lalu kirim:

```
$ git push -u origin main
```

Opsi `-u` (upstream) menghubungkan branch lokal `main` dengan `origin/main`, sehingga selanjutnya Anda cukup mengetik `git push` atau `git pull`.

## 10.4 Mengelola remote

```
$ git remote -v
origin  git@github.com:username/belajar-git.git (fetch)
origin  git@github.com:username/belajar-git.git (push)
```

|Perintah|Fungsi|
|---|---|
|`git remote -v`|Daftar remote beserta URL-nya.|
|`git remote add <nama> <url>`|Menambah remote.|
|`git remote remove <nama>`|Menghapus remote.|
|`git remote set-url origin <url-baru>`|Mengubah URL remote.|

## 10.5 Tiga perintah sinkronisasi

### `git push` - mengirim commit lokal ke remote

```
$ git push
```

Untuk branch baru yang belum punya upstream:

```
$ git push -u origin fitur-profil
```

### `git fetch` - mengambil data terbaru dari remote tanpa menggabungkan

```
$ git fetch
```

Perintah ini mengunduh commit baru dan memperbarui "remote-tracking branch" seperti `origin/main`, tetapi **tidak mengubah** branch lokal maupun folder kerja Anda. Aman dijalankan kapan saja.

### `git pull` - fetch lalu merge

```
$ git pull
```

Secara sederhana: `git pull` = `git fetch` + `git merge` untuk branch yang sedang aktif. Jika ada conflict, selesaikan seperti di Bab 9.

Perbandingan:

|Perintah|Mengubah branch lokal?|Fungsi|
|---|---|---|
|`git fetch`|Tidak|Hanya mengunduh informasi terbaru.|
|`git pull`|Ya|Mengunduh dan menggabungkan.|
|`git push`|Tidak (mengubah remote)|Mengirim commit lokal.|

## 10.6 Ditolak saat push

Jika Anda melihat pesan seperti:

```
! [rejected]        main -> main (fetch first)
error: failed to push some refs
```

Artinya remote punya commit yang belum ada di lokal Anda (misalnya rekan sudah push lebih dulu). Solusi standar:

```
$ git pull
# selesaikan conflict jika ada
$ git push
```

Jangan menggunakan `git push --force` untuk "memaksa lolos" kecuali Anda benar-benar paham dampaknya, karena dapat menimpa pekerjaan orang lain.

## 10.6 Memahami remote-tracking branch

Ketika Anda melihat `origin/main`, itu adalah salinan lokal dari posisi branch `main` di remote **pada saat terakhir Anda fetch/pull/push**. Ia hanya diperbarui saat Anda berkomunikasi dengan remote.

```
$ git log --oneline --graph --all
* 7a1b2c3 (origin/main) Commit terakhir yang diketahui di remote
* 5e8a1b3 (HEAD -> main) Commit lokal yang belum di-push
```

Pada contoh ini, `main` lokal lebih maju satu commit daripada `origin/main`; commit itu belum dikirim.

## 10.7 File README di repository

Biasakan setiap repository punya `README.md` yang menjelaskan: tujuan proyek, cara instalasi, cara menjalankan, dan cara kontribusi. Ini wajah proyek Anda dan hal pertama yang dilihat orang yang membuka repository.

## 10.8 Latihan Bab 10

1. Buat akun GitHub (jika belum) dan atur autentikasi (SSH atau token).
2. Buat repository baru di GitHub bernama `belajar-git`.
3. Hubungkan repository lokal Anda ke GitHub dan `push` branch `main`.
4. Edit `README.md` langsung lewat antarmuka web GitHub, commit di sana, lalu jalankan `git pull` di lokal. Amati perubahannya.
5. Jalankan `git clone` repository Anda ke folder lain untuk mensimulasikan "komputer kedua".

---

# Bab 11 - Alur Kolaborasi dengan Pull Request

## 11.1 Apa itu Pull Request

**Pull Request (PR)** (di GitLab disebut **Merge Request**, MR) adalah permintaan untuk menggabungkan branch Anda ke branch tujuan (biasanya `main`). PR bukan fitur inti Git, melainkan fitur layanan hosting. Fungsinya:

- Tempat diskusi dan **code review** oleh rekan satu tim.
- Menjalankan pemeriksaan otomatis (test, linting) lewat CI.
- Mendokumentasikan alasan sebuah perubahan.

## 11.2 Alur Feature Branch Workflow

Ini alur kerja paling umum bagi pemula yang masuk ke tim:

```
1. Perbarui main lokal:        git switch main
                               git pull
2. Buat branch fitur:          git switch -c fitur/endpoint-produk
3. Kerjakan dan commit:        git add ... ; git commit -m "..."
4. Kirim branch ke remote:     git push -u origin fitur/endpoint-produk
5. Buka Pull Request di web    (GitHub/GitLab)
6. Review dan perbaikan:       commit tambahan, push lagi
7. Merge PR oleh pihak berwenang
8. Bersihkan:                  git switch main
                               git pull
                               git branch -d fitur/endpoint-produk
```

## 11.3 Tips membuat PR yang baik

- Ukuran kecil dan fokus pada satu tujuan. PR yang sangat besar sulit direview.
- Judul jelas, deskripsi menjelaskan **apa**, **mengapa**, dan **cara mengujinya**.
- Pastikan test lulus sebelum meminta review.
- Tanggapi komentar reviewer dengan sopan. Review adalah proses belajar, bukan penilaian pribadi.

## 11.4 Fork (untuk kontribusi open source)

Jika Anda ingin berkontribusi ke proyek milik orang lain yang tidak memberi Anda akses tulis:

1. **Fork**: salin repository tersebut ke akun Anda (tombol Fork di GitHub).
2. **Clone** fork Anda ke komputer.
3. Buat branch, commit, push ke fork Anda.
4. Buka Pull Request dari fork Anda ke repository asli.

Praktik tambahan: daftarkan repository asli sebagai remote bernama `upstream` agar Anda bisa menyinkronkan fork:

```
$ git remote add upstream https://github.com/pemilik-asli/proyek.git
$ git fetch upstream
```

## 11.5 Proteksi branch

Banyak tim mengaktifkan **branch protection** pada `main`: tidak boleh push langsung, harus lewat PR, wajib ada approval dan test lulus. Jika `git push` ke `main` ditolak di tempat kerja, kemungkinan besar ini penyebabnya, dan itu memang disengaja.

## 11.6 Latihan Bab 11

1. Di repository `belajar-git` milik Anda, buat branch `fitur/tentang`, tambahkan file `TENTANG.md`, commit, dan push.
2. Buka Pull Request dari branch tersebut ke `main` lewat antarmuka web, tulis deskripsi yang jelas, lalu merge sendiri.
3. Pada komputer lokal, kembali ke `main`, `git pull`, dan hapus branch lokal yang sudah selesai.

---

# Bab 12 - Fitur Pendukung: stash, tag, blame

## 12.1 `git stash` - menyimpan pekerjaan sementara

Skenario: Anda sedang mengubah beberapa file dan belum siap commit, tetapi tiba-tiba harus berpindah branch untuk memperbaiki bug mendesak. Git mungkin menolak berpindah karena ada perubahan yang belum disimpan. `stash` menyimpan perubahan itu sementara.

```
$ git stash
Saved working directory and index state WIP on main: 8c2d9e4 ...
```

Folder kerja kembali bersih. Setelah urusan mendesak selesai:

```
$ git stash pop
```

Perintah terkait:

|Perintah|Fungsi|
|---|---|
|`git stash`|Simpan perubahan yang dilacak (modified dan staged).|
|`git stash -u`|Termasuk file untracked.|
|`git stash list`|Daftar stash.|
|`git stash pop`|Terapkan stash terbaru lalu hapus dari daftar.|
|`git stash apply`|Terapkan stash tanpa menghapusnya dari daftar.|
|`git stash drop`|Hapus stash terbaru.|

Stash bersifat sementara. Jangan menjadikannya tempat menyimpan pekerjaan jangka panjang; lebih baik buat commit di branch tersendiri.

## 12.2 `git tag` - menandai versi rilis

Tag memberi nama permanen pada sebuah commit, biasanya untuk versi rilis seperti `v1.0.0`.

Tag beranotasi (disarankan, menyimpan pembuat, tanggal, dan pesan):

```
$ git tag -a v1.0.0 -m "Rilis pertama"
```

Melihat daftar tag:

```
$ git tag
```

Mengirim tag ke remote (tag tidak ikut terkirim otomatis dengan `git push` biasa):

```
$ git push origin v1.0.0
```

Konvensi penomoran yang populer adalah **Semantic Versioning**: `MAJOR.MINOR.PATCH`.

- `MAJOR` naik bila ada perubahan yang tidak kompatibel dengan versi lama.
- `MINOR` naik bila menambah fitur yang kompatibel.
- `PATCH` naik bila hanya memperbaiki bug.

Contoh: 1.4.2 menjadi 1.4.3 (perbaikan bug), 1.5.0 (fitur baru), atau 2.0.0 (perubahan besar yang memutus kompatibilitas).

## 12.3 `git blame` - mencari tahu siapa mengubah baris tertentu

```
$ git blame README.md
```

Menampilkan, untuk setiap baris, commit dan pembuat terakhir yang mengubahnya. Tujuannya bukan mencari siapa yang salah, melainkan memahami **konteks**: lihat commit terkait lalu baca pesannya untuk mengerti alasan perubahan.

## 12.4 `git restore` dari commit tertentu

Mengambil isi sebuah file dari commit lama tanpa memindahkan branch:

```
$ git restore --source=3b1f7a2 README.md
```

## 12.5 Alias untuk mempercepat kerja

```
$ git config --global alias.st status
$ git config --global alias.co checkout
$ git config --global alias.lg "log --oneline --graph --all"
```

Setelah itu `git lg` menjalankan perintah log bergrafik. Untuk pemula, pahami perintah lengkapnya dulu sebelum memakai alias.

## 12.6 Latihan Bab 12

1. Ubah sebuah file, jalankan `git stash`, cek bahwa folder bersih, lalu `git stash pop`.
2. Buat tag `v0.1.0` pada commit terakhir dan push tag ke GitHub. Cek di tab Releases atau Tags di GitHub.
3. Jalankan `git blame` pada `README.md` dan baca keluarannya.

---

# Bab 13 - Praktik Baik (Best Practices)

## 13.1 Pesan commit yang baik

Struktur yang disarankan:

```
Ringkasan singkat dalam satu baris (maksimal sekitar 50-72 karakter)

Penjelasan lebih rinci jika perlu: apa yang diubah dan MENGAPA.
Jelaskan alasan, bukan sekadar mengulang isi kode.
```

Kaidah praktis:

- Baris pertama ringkas, spesifik, dan dalam gaya perintah atau deskriptif yang konsisten (pilih satu gaya dan tetap konsisten dalam tim).
- Pisahkan baris ringkasan dari isi dengan satu baris kosong.
- Satu commit membahas satu hal.
- Hindari pesan tak bermakna seperti "update", "fix", "perubahan".

### Conventional Commits (populer di banyak tim)

Format: `tipe(cakupan): deskripsi`

|Tipe|Kegunaan|
|---|---|
|`feat`|Fitur baru.|
|`fix`|Perbaikan bug.|
|`docs`|Perubahan dokumentasi.|
|`refactor`|Perbaikan struktur kode tanpa mengubah perilaku.|
|`test`|Menambah atau memperbaiki test.|
|`chore`|Tugas pemeliharaan (dependensi, konfigurasi).|

Contoh:

```
feat(auth): tambah login dengan JWT
fix(user): perbaiki validasi email kosong
docs: perbarui langkah instalasi di README
```

Tim Anda mungkin punya aturan sendiri. Selalu ikuti kesepakatan tim.

## 13.2 Commit kecil dan sering (atomic commits)

Satu commit sebaiknya berupa satu perubahan logis yang utuh. Manfaatnya:

- Mudah dibaca dan direview.
- Mudah dibatalkan (`revert`) jika bermasalah.
- Mudah dilacak penyebab bug.

Hindari commit raksasa berisi puluhan perubahan tak berhubungan.

## 13.3 Jangan commit hal-hal berikut

- Password, token, API key, private key, file `.env` asli.
- Dependensi yang bisa diunduh ulang (`node_modules/`, dan sejenisnya).
- File besar biner yang tidak perlu (video, dump database besar).
- Kode yang jelas-jelas tidak bisa dijalankan, kecuali di branch kerja pribadi.

Jika rahasia terlanjur ter-push, tindakan pertama adalah **mengganti (rotate) rahasia tersebut**, bukan sekadar menghapus filenya.

## 13.4 Perlakukan `main` sebagai jalur stabil

- Jangan kerjakan fitur langsung di `main`.
- Gunakan branch dan Pull Request.
- Pastikan test lulus sebelum merge.

## 13.5 Sinkronkan secara berkala

- Jalankan `git pull` sebelum mulai bekerja.
- Jalankan `git status` sebelum dan sesudah operasi penting.
- Push pekerjaan Anda di akhir hari agar tidak hanya ada di satu komputer.

## 13.6 Jangan ubah riwayat yang sudah dibagikan

Perintah yang mengubah riwayat (`commit --amend`, `reset`, `rebase`) aman untuk commit lokal yang belum di-push. Setelah commit dipush dan dipakai orang lain, gunakan `revert`. Hindari `git push --force` di branch bersama.

## 13.7 Sebelum commit, periksa dulu

Kebiasaan tiga langkah:

```
$ git status
$ git diff --staged
$ git commit -m "..."
```

Dengan `git diff --staged` Anda melihat persis apa yang akan masuk commit, sehingga file debug atau rahasia yang terselip bisa ketahuan.

## 13.8 Pelajari alat bantu visual (opsional)

Terminal adalah fondasi yang harus dipahami, tetapi antarmuka grafis dapat membantu memvisualisasikan riwayat: ekstensi Git di VS Code, GitHub Desktop, GitKraken, dan sejenisnya. Gunakan sebagai pendamping, bukan pengganti pemahaman perintah dasar.

---

# Bab 14 - Troubleshooting Masalah Umum

## 14.1 "fatal: not a git repository"

**Penyebab:** Anda menjalankan perintah Git di folder yang bukan repository. **Solusi:** pindah ke folder proyek yang benar (`cd`), atau jalankan `git init` jika memang ingin membuat repository di folder itu.

## 14.2 "Please tell me who you are" saat commit

**Penyebab:** `user.name` dan `user.email` belum diatur. **Solusi:** jalankan `git config --global user.name "..."` dan `git config --global user.email "..."`.

## 14.3 "nothing to commit, working tree clean" padahal merasa sudah mengedit

**Kemungkinan penyebab:** file belum disimpan di editor, Anda berada di folder yang salah, atau file yang diedit ada di `.gitignore`. **Cek:** `git status`, `pwd`, dan `git check-ignore -v nama-file`.

## 14.4 Salah commit ke branch yang keliru

Misalnya Anda commit di `main` padahal harusnya di branch fitur, dan **belum push**:

```
$ git branch fitur-baru        # buat branch dari posisi commit sekarang
$ git reset --hard HEAD~1      # mundurkan main satu commit (hati-hati, lihat Bab 6)
$ git switch fitur-baru        # lanjutkan di branch yang benar
```

Jika ragu, minta bantuan rekan atau gunakan `git reflog` sebagai jaring pengaman. Alternatif yang lebih aman bagi pemula: gunakan `git reset --soft HEAD~1`, pindah branch, lalu commit ulang.

## 14.5 "Your branch is behind 'origin/main'"

**Arti:** remote punya commit yang belum ada di lokal. **Solusi:** `git pull`.

## 14.6 "Your branch and 'origin/main' have diverged"

**Arti:** lokal dan remote sama-sama punya commit baru yang berbeda. **Solusi umum bagi pemula:** `git pull`, selesaikan conflict bila ada, lalu `git push`.

## 14.7 "Permission denied (publickey)"

**Penyebab:** SSH key belum terpasang di akun atau belum dimuat ke SSH agent. **Solusi:** periksa kembali langkah di 10.2 dan uji dengan `ssh -T git@github.com`.

## 14.8 Gagal autentikasi lewat HTTPS

**Penyebab:** memakai password akun biasa, atau token kedaluwarsa. **Solusi:** pakai Personal Access Token atau Git Credential Manager, atau beralih ke SSH.

## 14.9 Terjebak di editor Vim saat commit/merge

Jika Anda tidak sengaja masuk ke Vim:

- Untuk menyimpan dan keluar: tekan `Esc`, ketik `:wq`, tekan Enter.
- Untuk keluar tanpa menyimpan (membatalkan): tekan `Esc`, ketik `:q!`, tekan Enter.

Agar tidak terulang, atur editor lain (lihat 2.4).

## 14.10 Terlanjur commit file rahasia

1. Jika **belum di-push**: hapus dari commit dengan `git rm --cached`, tambahkan ke `.gitignore`, lalu `git commit --amend`.
2. Jika **sudah di-push**: anggap rahasia sudah bocor. **Ganti rahasia itu segera.** Lalu bersihkan riwayat dengan bantuan yang lebih lanjut (topik di luar buku ini; mintalah bantuan senior atau pelajari dokumentasi `git filter-repo`).

## 14.11 Folder kerja "berantakan" dan ingin kembali bersih

Buang semua perubahan yang belum di-commit pada file yang dilacak:

```
$ git restore .
```

Hapus file untracked (hati-hati, tidak bisa dipulihkan). Lihat dulu apa yang akan dihapus:

```
$ git clean -n
```

Jika sudah yakin:

```
$ git clean -f
```

---

# Bab 15 - Proyek Latihan Akhir

Proyek ini menggabungkan hampir semua yang telah dipelajari. Kerjakan berurutan dan jangan lompat.

## Skenario

Anda membuat repository kecil bernama `catatan-api` yang berisi dokumentasi dan contoh data untuk sebuah API sederhana. Anda akan bekerja dengan branch, melakukan merge, menangani conflict, dan mengirim ke GitHub.

## Bagian A - Inisialisasi

1. Buat folder `catatan-api` dan jalankan `git init`.
2. Buat `README.md` berisi judul dan satu kalimat deskripsi.
3. Buat `.gitignore` yang mengabaikan `.env`, `node_modules/`, dan `*.log`.
4. Buat `.env.example` berisi `PORT=3000`.
5. Commit dalam **dua commit terpisah**: satu untuk `README.md`, satu untuk `.gitignore` dan `.env.example`.

## Bagian B - Branch fitur

1. Buat branch `fitur/dokumentasi-endpoint`.
2. Buat file `ENDPOINT.md` yang mendeskripsikan dua endpoint fiktif, misalnya `GET /catatan` dan `POST /catatan`. Commit satu per satu (dua commit).
3. Kembali ke `main` dan merge branch itu. Perhatikan jenis merge-nya.

## Bagian C - Conflict yang disengaja

1. Buat dua branch dari `main`: `branch-x` dan `branch-y`.
2. Di `branch-x`, ubah baris judul `README.md` menjadi versi X dan commit.
3. Di `branch-y`, ubah baris judul yang sama menjadi versi Y dan commit.
4. Merge `branch-x` ke `main`, lalu merge `branch-y` ke `main`. Akan terjadi conflict.
5. Selesaikan conflict dengan menulis judul final yang menggabungkan keduanya.
6. Selesaikan merge dengan commit.

## Bagian D - Memperbaiki kesalahan

1. Buat commit dengan pesan sengaja salah ketik, lalu perbaiki dengan `--amend`.
2. Buat commit percobaan yang menambah file `sampah.txt`, lalu batalkan dengan `git revert`.
3. Ubah `README.md` tanpa commit, lalu buang perubahan dengan `git restore`.

## Bagian E - Remote dan rilis

1. Buat repository kosong `catatan-api` di GitHub.
2. Sambungkan remote `origin` dan `push -u origin main`.
3. Buat tag `v0.1.0` dan push tag tersebut.
4. Buat satu branch baru, push, lalu buka Pull Request dan merge lewat antarmuka web.
5. Di lokal, `git switch main`, `git pull`, dan hapus branch yang sudah selesai.

## Bagian F - Refleksi (jawab untuk diri sendiri)

- Apa beda `git fetch` dan `git pull`?
- Kapan memakai `revert` dan kapan memakai `reset`?
- Mengapa `.env` tidak boleh di-commit?
- Apa yang terjadi pada staging area saat Anda menjalankan `git commit`?

## Kriteria keberhasilan

Anda dianggap menguasai dasar Git jika bisa:

- Menjalankan siklus `status`, `add`, `commit`, `log` tanpa melihat catatan.
- Membuat dan menggabungkan branch.
- Menyelesaikan conflict sederhana.
- Membatalkan kesalahan dengan alat yang tepat.
- Mengirim dan mengambil perubahan dari GitHub.
- Menjelaskan konsep tiga area kerja dengan kata-kata Anda sendiri.

## Hasil akhir yang diharapkan pada `git log --oneline --graph --all`

Bentuknya akan kira-kira seperti ini (hash dan jumlah commit akan berbeda):

```
*   a1b2c3d Merge branch 'branch-y'
|\
| * 9f8e7d6 Ubah judul versi Y
* | 6c5b4a3 Merge branch 'branch-x'
...
```

---

# Lampiran A - Cheat Sheet Perintah

## Pengaturan

|Perintah|Fungsi|
|---|---|
|`git config --global user.name "Nama"`|Atur nama.|
|`git config --global user.email "e@mail"`|Atur email.|
|`git config --global init.defaultBranch main`|Branch awal bernama main.|
|`git config --list`|Lihat semua konfigurasi.|

## Memulai

|Perintah|Fungsi|
|---|---|
|`git init`|Buat repository baru di folder ini.|
|`git clone <url>`|Salin repository dari remote.|

## Siklus harian

|Perintah|Fungsi|
|---|---|
|`git status`|Lihat kondisi saat ini.|
|`git add <file>`|Masukkan ke staging.|
|`git add .`|Stage semua perubahan.|
|`git add -p`|Stage per potongan perubahan.|
|`git commit -m "pesan"`|Simpan snapshot.|
|`git commit -am "pesan"`|Stage file terlacak yang berubah lalu commit.|
|`git diff`|Perubahan yang belum di-stage.|
|`git diff --staged`|Perubahan yang sudah di-stage.|

## Riwayat

|Perintah|Fungsi|
|---|---|
|`git log`|Riwayat lengkap.|
|`git log --oneline`|Riwayat ringkas.|
|`git log --oneline --graph --all`|Riwayat bergrafik semua branch.|
|`git show <hash>`|Detail satu commit.|
|`git blame <file>`|Siapa mengubah tiap baris.|

## Membatalkan

|Perintah|Fungsi|
|---|---|
|`git restore <file>`|Buang perubahan belum di-stage.|
|`git restore --staged <file>`|Keluarkan dari staging.|
|`git commit --amend`|Perbaiki commit terakhir (lokal saja).|
|`git reset --soft HEAD~1`|Batalkan commit, perubahan tetap staged.|
|`git reset HEAD~1`|Batalkan commit, perubahan tetap di file.|
|`git reset --hard HEAD~1`|Batalkan commit dan buang perubahannya (berbahaya).|
|`git revert <hash>`|Batalkan dengan commit baru (aman untuk yang sudah dibagikan).|
|`git reflog`|Riwayat perpindahan HEAD, jaring pengaman.|

## Branch dan merge

|Perintah|Fungsi|
|---|---|
|`git branch`|Daftar branch.|
|`git switch -c <nama>`|Buat dan pindah ke branch baru.|
|`git switch <nama>`|Pindah branch.|
|`git merge <nama>`|Gabungkan branch ke branch aktif.|
|`git merge --abort`|Batalkan merge yang sedang conflict.|
|`git branch -d <nama>`|Hapus branch yang sudah di-merge.|

## Remote

|Perintah|Fungsi|
|---|---|
|`git remote -v`|Lihat remote.|
|`git remote add origin <url>`|Tambah remote.|
|`git push -u origin <branch>`|Kirim dan set upstream.|
|`git push`|Kirim commit.|
|`git fetch`|Ambil info terbaru tanpa merge.|
|`git pull`|Ambil dan merge.|

## Lain-lain

|Perintah|Fungsi|
|---|---|
|`git stash` / `git stash pop`|Simpan sementara / pulihkan.|
|`git tag -a v1.0.0 -m "pesan"`|Buat tag beranotasi.|
|`git push origin <tag>`|Kirim tag ke remote.|
|`git rm --cached <file>`|Berhenti melacak file.|
|`git clean -n`|Pratinjau penghapusan file untracked.|

---

# Lampiran B - Glosarium

|Istilah|Arti|
|---|---|
|**Repository (repo)**|Folder proyek yang dikelola Git beserta riwayatnya.|
|**Commit**|Snapshot proyek pada satu titik waktu, dengan pesan dan hash unik.|
|**Hash**|Pengenal unik commit berupa deretan karakter heksadesimal.|
|**Working directory**|Folder kerja tempat Anda mengedit file.|
|**Staging area / index**|Area penyiapan perubahan sebelum di-commit.|
|**Stage**|Memasukkan perubahan ke staging area (`git add`).|
|**Tracked / untracked**|File yang dikenal / belum dikenal Git.|
|**Branch**|Jalur pengembangan; pointer bergerak ke sebuah commit.|
|**HEAD**|Penunjuk posisi Anda saat ini.|
|**Merge**|Menggabungkan perubahan dari satu branch ke branch lain.|
|**Fast-forward**|Merge yang hanya menggeser pointer, tanpa merge commit.|
|**Merge commit**|Commit khusus dengan dua parent hasil penggabungan.|
|**Conflict**|Kondisi saat Git tidak dapat menggabungkan otomatis dan butuh keputusan manusia.|
|**Remote**|Versi repository yang berada di server atau komputer lain.|
|**Origin**|Nama bawaan untuk remote utama.|
|**Upstream**|Branch remote yang ditautkan dengan branch lokal; juga nama umum untuk repository asli pada alur fork.|
|**Clone**|Menyalin seluruh repository dari remote ke lokal.|
|**Push**|Mengirim commit lokal ke remote.|
|**Pull**|Mengambil dan menggabungkan perubahan dari remote.|
|**Fetch**|Mengambil informasi terbaru dari remote tanpa menggabungkan.|
|**Fork**|Salinan repository orang lain di akun Anda (fitur layanan hosting).|
|**Pull Request / Merge Request**|Permintaan menggabungkan branch, disertai review (fitur layanan hosting).|
|**Tag**|Penanda permanen pada commit tertentu, biasanya untuk rilis.|
|**Stash**|Tempat penyimpanan sementara untuk perubahan yang belum di-commit.|
|**Rebase**|Memindahkan commit sebuah branch ke atas ujung branch lain (topik lanjutan).|
|**Reflog**|Catatan lokal perpindahan HEAD, berguna untuk memulihkan commit yang hilang.|
|**CI/CD**|Proses otomatis untuk menguji dan merilis kode setiap ada perubahan.|
|**Semantic Versioning**|Konvensi penomoran versi MAJOR.MINOR.PATCH.|

---

# Lampiran C - Kuis dan Kunci Jawaban

## Soal pilihan ganda

**1.** Manakah yang merupakan VCS terdistribusi? a. SVN b. CVS c. Git d. RCS

**2.** Urutan alur perubahan yang benar adalah: a. Repository, staging area, working directory b. Working directory, staging area, repository c. Staging area, working directory, repository d. Working directory, repository, staging area

**3.** Perintah untuk melihat perubahan yang sudah di-stage tetapi belum di-commit adalah: a. `git diff` b. `git diff --staged` c. `git log` d. `git status -v`

**4.** Anda ingin membatalkan commit yang sudah di-push dan dipakai rekan satu tim. Cara yang paling aman adalah: a. `git reset --hard` lalu `git push --force` b. `git revert <hash>` c. Menghapus folder `.git` d. `git commit --amend`

**5.** Perintah yang membuat branch baru sekaligus berpindah ke branch itu: a. `git branch -d nama` b. `git switch nama` c. `git switch -c nama` d. `git merge nama`

**6.** `git pull` pada dasarnya sama dengan: a. `git push` lalu `git fetch` b. `git fetch` lalu `git merge` c. `git clone` lalu `git add` d. `git stash` lalu `git commit`

**7.** Manakah yang sebaiknya **tidak** di-commit ke repository? a. `README.md` b. `.gitignore` c. File `.env` berisi password database asli d. File kode sumber

**8.** Penanda `<<<<<<<`, `=======`, `>>>>>>>` muncul saat: a. Anda melakukan `git init` b. Terjadi merge conflict c. Anda membuat tag d. Anda menjalankan `git log`

**9.** Opsi `-u` pada `git push -u origin main` berfungsi untuk: a. Memaksa push menimpa remote b. Menautkan branch lokal dengan branch remote sebagai upstream c. Membatalkan push d. Mengunggah tag

**10.** Tag `v2.0.0` dalam Semantic Versioning umumnya menandakan: a. Perbaikan bug kecil b. Penambahan fitur kecil yang kompatibel c. Perubahan besar yang dapat memutus kompatibilitas dengan versi sebelumnya d. Penghapusan repository

## Soal uraian singkat

**11.** Jelaskan perbedaan Git dan GitHub dengan kalimat Anda sendiri.

**12.** Mengapa Git memiliki staging area? Berikan satu contoh situasi yang memperlihatkan manfaatnya.

**13.** Jelaskan perbedaan `git reset --soft`, `--mixed`, dan `--hard`.

**14.** Jelaskan langkah menyelesaikan merge conflict dari awal sampai commit.

**15.** Anda tidak sengaja men-commit file `.env` berisi kunci rahasia dan sudah mem-push-nya. Apa dua tindakan terpenting yang harus dilakukan?

## Kunci jawaban

**Pilihan ganda:**

1. c
2. b
3. b
4. b
5. c
6. b
7. c
8. b
9. b
10. c

**Uraian (jawaban ringkas):**

**11.** Git adalah perangkat lunak (alat) di komputer Anda untuk mengelola riwayat versi kode. GitHub adalah layanan web untuk menyimpan repository Git secara online dan berkolaborasi (PR, issue, dan sebagainya). Git bisa dipakai tanpa GitHub.

**12.** Staging area memungkinkan Anda memilih perubahan mana yang masuk ke commit berikutnya. Contoh: Anda mengubah lima file, dua di antaranya untuk fitur login dan tiga untuk perbaikan tampilan. Anda dapat men-stage dua file login, membuat satu commit khusus login, lalu tiga file sisanya di commit terpisah, sehingga riwayat rapi dan mudah dipahami.

**13.** Ketiganya memundurkan pointer branch. `--soft` mempertahankan perubahan di staging area dan working directory. `--mixed` (default) mengosongkan staging tetapi mempertahankan perubahan di file. `--hard` mengosongkan staging dan juga mengembalikan file ke kondisi commit tujuan, sehingga perubahan yang belum di-commit hilang.

**14.** Jalankan `git status` untuk melihat file conflict; buka file dan putuskan isi akhirnya; hapus semua penanda conflict; simpan file; `git add` file tersebut; lalu `git commit` untuk menyelesaikan merge. Jika ingin membatalkan, gunakan `git merge --abort`.

**15.** Pertama, segera **ganti (rotate) kunci rahasia** karena sudah dianggap bocor. Kedua, hentikan pelacakan file (`git rm --cached .env`), tambahkan ke `.gitignore`, dan commit; lalu pertimbangkan membersihkan riwayat dengan alat yang tepat atau meminta bantuan anggota tim yang berpengalaman.

---

# Lampiran D - Referensi Lanjutan

Sumber resmi dan terpercaya untuk melanjutkan belajar:

- Dokumentasi resmi Git: https://git-scm.com/doc
- Buku Pro Git (gratis, tersedia online, ada terjemahan ke beberapa bahasa): https://git-scm.com/book
- Dokumentasi GitHub: https://docs.github.com
- Dokumentasi GitLab: https://docs.gitlab.com
- Template .gitignore: https://github.com/github/gitignore
- Conventional Commits: https://www.conventionalcommits.org
- Semantic Versioning: https://semver.org
- Latihan interaktif visual: Learn Git Branching (https://learngitbranching.js.org)

## Topik lanjutan yang disarankan setelah buku ini

Setelah nyaman dengan materi dasar, urutan belajar yang disarankan:

1. `git rebase` dan `git rebase -i` (merapikan riwayat).
2. `git cherry-pick` (mengambil satu commit tertentu).
3. Strategi branching tim: GitHub Flow, Git Flow, trunk-based development.
4. Git hooks dan integrasi dengan CI/CD (misalnya GitHub Actions).
5. Commit bertanda tangan (signed commits) dan keamanan repository.
6. Membersihkan riwayat dari data sensitif (`git filter-repo`).
7. Git submodule dan monorepo.

## Penutup

Git adalah keterampilan yang hanya mahir lewat latihan. Jangan khawatir jika awalnya terasa membingungkan; hampir semua developer pernah mengalaminya. Kuncinya: pahami konsep tiga area kerja, biasakan `git status` dan `git diff` sebelum commit, commit kecil dan sering, serta jangan pernah menyimpan rahasia di repository.

Selanjutnya dalam seri Backend Developer Anda dapat melanjutkan ke topik berikutnya, misalnya dasar terminal/command line, HTTP dan REST API, database SQL, dan seterusnya, dengan Git sebagai alat pendamping di setiap proyek yang Anda kerjakan.

Selamat belajar.