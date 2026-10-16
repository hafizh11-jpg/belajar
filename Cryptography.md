# Buku Pembelajaran Cryptography (Kriptografi)

Panduan untuk Pemula, Program Studi Teknik Informatika

Edisi 2026/2027 (mencakup perkembangan terbaru hingga kriptografi pasca-kuantum)

---

## Kata Pengantar

Buku ini ditulis untuk mahasiswa Teknik Informatika yang baru pertama kali belajar kriptografi. Anda tidak perlu menjadi ahli matematika. Setiap konsep dijelaskan dengan bahasa teknis yang tetap sederhana, disertai analogi, diagram teks, dan contoh kode Python yang bisa langsung dijalankan.

Kriptografi adalah salah satu fondasi keamanan digital modern. Setiap kali Anda membuka situs dengan `https://`, mengirim pesan lewat aplikasi pesan terenkripsi, login memakai passkey, atau melakukan transaksi perbankan digital, kriptografi bekerja di balik layar.

### Cara Menggunakan Buku Ini

1. Baca bab secara berurutan. Setiap bab membangun konsep dari bab sebelumnya.
2. Jalankan semua contoh kode. Kriptografi lebih mudah dipahami jika dicoba langsung.
3. Kerjakan latihan di akhir setiap bab sebelum lanjut.
4. Gunakan glosarium di bagian akhir jika menemukan istilah yang belum dikenal.

### Prasyarat

- Pemahaman dasar pemrograman (Python lebih disarankan).
- Pemahaman dasar bilangan biner dan heksadesimal (akan diulas singkat di Bab 3).
- Python 3.10 atau lebih baru dan library `cryptography`:

```bash
pip install cryptography argon2-cffi
```

### Peringatan Penting

Buku ini bersifat edukatif. Contoh kode "mainan" (toy) di bab-bab awal sengaja disederhanakan agar mudah dipahami dan **tidak boleh dipakai untuk mengamankan data sungguhan**. Aturan emas kriptografi:

> Jangan pernah membuat algoritma kriptografi sendiri untuk produksi. Gunakan library yang sudah teruji dan standar yang sudah dikaji publik.

### Catatan tentang Kemutakhiran

Bidang kriptografi, terutama standar pasca-kuantum dan kebijakan sertifikat, terus berkembang. Informasi dalam buku ini mencerminkan kondisi sampai pertengahan 2026. Untuk keputusan desain sistem nyata, selalu periksa sumber primer seperti NIST (csrc.nist.gov), IETF (datatracker.ietf.org), dan BSSN (bssn.go.id).

---

## Daftar Isi

- Bab 1. Pengantar Kriptografi
- Bab 2. Kriptografi Klasik
- Bab 3. Matematika Dasar untuk Kriptografi
- Bab 4. Kriptografi Simetris
- Bab 5. Fungsi Hash, MAC, dan Penyimpanan Password
- Bab 6. Kriptografi Asimetris
- Bab 7. Tanda Tangan Digital
- Bab 8. PKI, Sertifikat Digital, dan TLS
- Bab 9. Protokol Kriptografi dalam Praktik
- Bab 10. Bilangan Acak dan Manajemen Kunci
- Bab 11. Kriptografi Pasca-Kuantum
- Bab 12. Topik Lanjutan
- Bab 13. Serangan Umum dan Kesalahan Implementasi
- Bab 14. Kriptografi dalam Konteks Indonesia
- Bab 15. Praktikum Terpadu
- Bab 16. Peta Belajar Selanjutnya
- Glosarium
- Referensi

---

# Bab 1. Pengantar Kriptografi

## Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

- Menjelaskan apa itu kriptografi dan perbedaannya dengan istilah terkait.
- Menyebutkan tujuan utama keamanan informasi.
- Memahami istilah dasar: plaintext, ciphertext, kunci, enkripsi, dekripsi.
- Memahami prinsip Kerckhoffs dan konsep model ancaman.

## 1.1 Apa Itu Kriptografi?

Kata kriptografi berasal dari bahasa Yunani: _kryptos_ (tersembunyi) dan _graphein_ (menulis). Secara teknis, **kriptografi adalah ilmu dan seni mengamankan informasi menggunakan teknik matematika sehingga hanya pihak yang berhak yang dapat membaca, mengubah, atau memverifikasinya.**

Beberapa istilah yang sering tertukar:

|Istilah|Arti Singkat|
|---|---|
|Kriptografi (cryptography)|Ilmu merancang skema pengamanan informasi|
|Kriptanalisis (cryptanalysis)|Ilmu memecahkan atau melemahkan skema kriptografi|
|Kriptologi (cryptology)|Gabungan kriptografi dan kriptanalisis|
|Steganografi|Menyembunyikan keberadaan pesan (misalnya dalam gambar), bukan mengacak isinya|
|Enkripsi|Mengubah data yang bisa dibaca menjadi data teracak|

## 1.2 Tujuan Keamanan Informasi

Kriptografi tidak hanya soal menyembunyikan pesan. Ada beberapa tujuan keamanan yang ingin dicapai.

1. **Kerahasiaan (confidentiality).** Hanya pihak berwenang yang dapat membaca data. Dicapai dengan enkripsi.
2. **Integritas (integrity).** Data tidak berubah tanpa terdeteksi. Dicapai dengan hash, MAC, dan tanda tangan digital.
3. **Autentikasi (authentication).** Kita bisa memastikan siapa yang mengirim data atau siapa lawan bicara kita. Dicapai dengan MAC, tanda tangan digital, dan sertifikat.
4. **Non-repudiation (anti-penyangkalan).** Pengirim tidak dapat menyangkal telah mengirim pesan. Dicapai dengan tanda tangan digital.

Tiga yang pertama sering disebut **CIA triad** (Confidentiality, Integrity, Availability), walaupun huruf A di sana berarti ketersediaan, yang lebih terkait rekayasa sistem daripada kriptografi.

## 1.3 Istilah Dasar

```
  Plaintext  --[ Enkripsi + Kunci ]-->  Ciphertext  --[ Dekripsi + Kunci ]-->  Plaintext
  (pesan asli)                          (pesan teracak)                         (pesan asli)
```

- **Plaintext**: data asli yang dapat dibaca.
- **Ciphertext**: hasil enkripsi.
- **Cipher**: algoritma enkripsi dan dekripsi.
- **Kunci (key)**: parameter rahasia yang mengendalikan cipher.
- **Enkripsi**: plaintext menjadi ciphertext.
- **Dekripsi**: ciphertext kembali menjadi plaintext.

## 1.4 Prinsip Kerckhoffs

Pada tahun 1883, Auguste Kerckhoffs menyatakan bahwa sistem kriptografi harus tetap aman walaupun semua detail sistem diketahui musuh, kecuali kuncinya.

Konsekuensi praktis:

- Keamanan bergantung pada **kerahasiaan kunci**, bukan kerahasiaan algoritma.
- Algoritma sebaiknya dipublikasikan dan dikaji oleh banyak ahli (algoritma publik seperti AES telah diuji puluhan tahun).
- "Security through obscurity" (keamanan karena disembunyikan) adalah praktik yang buruk.

## 1.5 Model Ancaman

Sebelum memilih kriptografi, tanyakan: siapa yang kita lawan dan apa kemampuannya? Beberapa model penyerang:

- **Penyerang pasif (eavesdropper)**: hanya menyadap lalu lintas data.
- **Penyerang aktif (man-in-the-middle)**: dapat menyadap, mengubah, menyisipkan, atau memblokir data.
- **Penyerang dengan akses fisik**: dapat mengukur waktu, konsumsi daya, atau membaca memori perangkat (side-channel).
- **Penyerang dengan sumber daya besar**: memiliki komputasi sangat besar, dan di masa depan mungkin memiliki komputer kuantum.

Model serangan terhadap cipher (dari paling lemah ke paling kuat bagi penyerang yang memiliki akses):

|Model|Kemampuan Penyerang|
|---|---|
|Ciphertext-only|Hanya memiliki ciphertext|
|Known-plaintext|Memiliki beberapa pasangan plaintext dan ciphertext|
|Chosen-plaintext|Dapat memilih plaintext untuk dienkripsi|
|Chosen-ciphertext|Dapat memilih ciphertext untuk didekripsi|

Cipher modern dirancang aman minimal terhadap chosen-plaintext attack, dan skema enkripsi praktis harus aman terhadap chosen-ciphertext attack.

## 1.6 Tiga Cabang Utama Kriptografi Modern

1. **Kriptografi simetris**: satu kunci yang sama untuk enkripsi dan dekripsi (Bab 4).
2. **Kriptografi asimetris (kunci publik)**: sepasang kunci, kunci publik dan kunci privat (Bab 6 dan 7).
3. **Fungsi hash**: sidik jari data, tanpa kunci (Bab 5).

Ketiganya dipadukan dalam protokol seperti TLS (Bab 8 dan 9).

## Ringkasan Bab 1

- Kriptografi bertujuan menjaga kerahasiaan, integritas, autentikasi, dan non-repudiation.
- Keamanan harus bergantung pada kunci, bukan pada kerahasiaan algoritma.
- Selalu definisikan model ancaman sebelum memilih solusi.

## Latihan Bab 1

1. Jelaskan perbedaan kriptografi dan steganografi dengan contoh.
2. Apa tujuan keamanan yang dicapai oleh tanda tangan digital?
3. Mengapa algoritma rahasia buatan sendiri justru dianggap berbahaya?
4. Sebutkan dua perbedaan kemampuan penyerang pasif dan aktif.

---

# Bab 2. Kriptografi Klasik

## Tujuan Pembelajaran

- Memahami cipher substitusi dan transposisi.
- Mengimplementasikan Caesar dan Vigenere.
- Memahami mengapa cipher klasik mudah dipecahkan.
- Memahami one-time pad sebagai satu-satunya cipher dengan kerahasiaan sempurna.

Mempelajari cipher klasik bukan untuk dipakai, tetapi untuk memahami ide inti dan alasan mengapa rancangan modern dibuat seperti sekarang.

## 2.1 Caesar Cipher

Setiap huruf digeser sejumlah posisi tetap di alfabet. Dengan kunci 3: A menjadi D, B menjadi E, dan seterusnya.

Contoh: `HELLO` dengan kunci 3 menjadi `KHOOR`.

Rumus matematis, dengan huruf dinomori A=0 sampai Z=25:

```
Enkripsi: C = (P + k) mod 26
Dekripsi: P = (C - k) mod 26
```

```python
def caesar(teks: str, k: int, dekripsi: bool = False) -> str:
    if dekripsi:
        k = -k
    hasil = []
    for ch in teks.upper():
        if "A" <= ch <= "Z":
            hasil.append(chr((ord(ch) - ord("A") + k) % 26 + ord("A")))
        else:
            hasil.append(ch)
    return "".join(hasil)

c = caesar("HELLO", 3)
print(c)                          # KHOOR
print(caesar(c, 3, dekripsi=True))  # HELLO
```

**Kelemahan**: ruang kunci hanya 25 kemungkinan, sehingga bisa dicoba semuanya dalam hitungan milidetik (brute force).

## 2.2 Cipher Substitusi Monoalfabetik

Setiap huruf diganti dengan huruf lain menurut tabel acak. Ruang kuncinya 26! (sekitar 4 x 10^26), tampak besar, tetapi tetap mudah dipecahkan dengan **analisis frekuensi**: dalam bahasa Indonesia, huruf A, N, I, E sangat sering muncul. Pola frekuensi huruf tetap terbawa ke ciphertext.

Pelajaran penting: ruang kunci yang besar saja tidak cukup. Cipher yang baik harus menyembunyikan pola statistik plaintext.

## 2.3 Vigenere Cipher

Memakai kata kunci berulang sehingga setiap posisi digeser dengan jumlah berbeda.

```
Plaintext : ATTACKATDAWN
Kunci     : LEMONLEMONLE
Ciphertext: LXFOPVEFRNHR
```

```python
def vigenere(teks: str, kunci: str, dekripsi: bool = False) -> str:
    hasil, j = [], 0
    kunci = kunci.upper()
    for ch in teks.upper():
        if "A" <= ch <= "Z":
            geser = ord(kunci[j % len(kunci)]) - ord("A")
            if dekripsi:
                geser = -geser
            hasil.append(chr((ord(ch) - ord("A") + geser) % 26 + ord("A")))
            j += 1
        else:
            hasil.append(ch)
    return "".join(hasil)

print(vigenere("ATTACKATDAWN", "LEMON"))  # LXFOPVEFRNHR
```

Vigenere pernah dijuluki le chiffre indechiffrable (cipher yang tak terpecahkan), namun dipecahkan pada abad ke-19 lewat metode Kasiski dan indeks kebetulan (index of coincidence) yang mencari panjang kunci lalu menerapkan analisis frekuensi pada tiap kolom.

## 2.4 Cipher Transposisi

Huruf tidak diganti, tetapi **posisinya diacak**. Contoh rail fence dengan 2 baris untuk `HELLOWORLD`:

```
H L O O L
 E L W R D
```

Dibaca baris demi baris: `HLOOL` lalu `ELWRD`, menjadi `HLOOLELWRD`.

Gagasan substitusi dan transposisi yang digabung berulang kali menjadi dasar cipher blok modern (disebut konfusi dan difusi oleh Claude Shannon).

## 2.5 Operasi XOR

XOR (exclusive OR), ditulis `^` di banyak bahasa pemrograman, adalah operasi bit paling penting di kriptografi.

|A|B|A XOR B|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

Sifat kunci: `(P XOR K) XOR K = P`. Artinya, XOR dengan kunci yang sama dua kali mengembalikan data asli.

```python
pesan = b"HALO"
kunci = b"\x1f\x2a\x3c\x4d"
c = bytes(p ^ k for p, k in zip(pesan, kunci))
p = bytes(x ^ k for x, k in zip(c, kunci))
print(c.hex(), p)  # p kembali b'HALO'
```

## 2.6 One-Time Pad (OTP)

OTP meng-XOR plaintext dengan kunci yang:

1. benar-benar acak,
2. sepanjang pesan,
3. **hanya dipakai satu kali**,
4. dirahasiakan.

Claude Shannon membuktikan bahwa OTP memiliki **kerahasiaan sempurna (perfect secrecy)**: ciphertext tidak memberi informasi apa pun tentang plaintext, bahkan kepada penyerang dengan komputasi tak terbatas.

Masalah praktisnya: kunci harus sepanjang pesan dan harus dibagikan secara aman terlebih dahulu. Jika kunci dipakai dua kali, penyerang cukup meng-XOR dua ciphertext untuk mendapatkan `P1 XOR P2` yang membocorkan banyak informasi. Kesalahan "reuse kunci atau nonce" ini terus muncul di kriptografi modern (lihat Bab 4 dan 13).

## Ringkasan Bab 2

- Cipher klasik gagal karena ruang kunci kecil atau pola statistik bocor.
- XOR adalah operasi fundamental yang akan sering muncul.
- OTP aman sempurna, tetapi tidak praktis; cipher modern berusaha mendekati sifat acaknya dengan kunci pendek.

## Latihan Bab 2

1. Enkripsi `INFORMATIKA` dengan Caesar kunci 5. Tulis juga kodenya.
2. Tulis program brute force yang mencoba semua 25 kunci Caesar pada `KHOOR`.
3. Mengapa analisis frekuensi tidak langsung bekerja pada Vigenere? Bagaimana cara mengatasinya?
4. Jelaskan apa yang terjadi jika OTP dipakai dua kali.

---

# Bab 3. Matematika Dasar untuk Kriptografi

## Tujuan Pembelajaran

- Memahami aritmetika modular.
- Memahami bilangan prima, FPB (GCD), dan invers modular.
- Memahami representasi biner dan heksadesimal.
- Memahami konsep keamanan komputasional dan entropi.

Bagian ini cukup untuk memahami bab-bab berikutnya, bukan pengganti buku teori bilangan.

## 3.1 Aritmetika Modular

Aritmetika modular adalah aritmetika "jam". Pada jam 12, pukul 10 ditambah 5 jam menjadi pukul 3, bukan 15. Dalam notasi matematika:

```
15 mod 12 = 3
```

`a mod n` adalah sisa pembagian a oleh n. Dua bilangan dikatakan kongruen modulo n jika sisanya sama, ditulis `a ≡ b (mod n)`.

Sifat yang berguna:

```
(a + b) mod n = ((a mod n) + (b mod n)) mod n
(a * b) mod n = ((a mod n) * (b mod n)) mod n
```

Di Python, `pow(a, b, n)` menghitung `a^b mod n` secara efisien meski bilangannya sangat besar.

```python
print(pow(5, 6, 23))   # 8
print((17 * 3) % 5)    # 1
```

## 3.2 Bilangan Prima dan FPB

**Bilangan prima** adalah bilangan lebih dari 1 yang hanya habis dibagi 1 dan dirinya sendiri. Dua bilangan **relatif prima (coprime)** jika FPB-nya 1.

Algoritma Euclid menghitung FPB dengan cepat:

```python
def fpb(a, b):
    while b:
        a, b = b, a % b
    return a

print(fpb(48, 18))  # 6
```

## 3.3 Invers Modular

Invers modular dari `a` modulo `n` adalah bilangan `x` sehingga `(a * x) mod n = 1`. Invers hanya ada jika `a` dan `n` relatif prima.

```python
print(pow(7, -1, 40))  # 23, karena 7 * 23 = 161 = 4*40 + 1
```

Invers modular dipakai untuk menghitung kunci privat RSA (Bab 6).

## 3.4 Fungsi Satu Arah dan Masalah Sulit

Kriptografi kunci publik bersandar pada masalah matematika yang mudah dihitung ke satu arah tetapi sangat sulit dibalik:

|Masalah|Mudah|Sulit|
|---|---|---|
|Faktorisasi (dasar RSA)|Mengalikan dua bilangan prima besar|Memfaktorkan hasil kalinya|
|Logaritma diskret (dasar Diffie-Hellman)|Menghitung `g^x mod p`|Mencari `x` dari hasilnya|
|Logaritma diskret kurva eliptik (dasar ECC)|Menghitung `x * G` pada kurva|Mencari `x` dari `x * G`|
|Masalah lattice (dasar pasca-kuantum)|Membangkitkan instance|Menemukan vektor pendek dalam lattice|

Perlu dicatat: sulit di sini berarti "belum ada algoritma efisien yang diketahui", bukan "terbukti mustahil". Karena itu keamanan kriptografi modern disebut **keamanan komputasional**.

## 3.5 Biner, Heksadesimal, dan Byte

Komputer menyimpan data sebagai bit. Delapan bit membentuk satu byte, yang sering ditulis sebagai dua digit heksadesimal.

```
Desimal 255  = Biner 11111111 = Heksadesimal FF
Karakter 'A' = Desimal 65     = Heksadesimal 41
```

```python
data = "Halo".encode("utf-8")
print(data)          # b'Halo'
print(data.hex())    # 48616c6f
print(bytes.fromhex("48616c6f"))  # b'Halo'
```

Primitif kriptografi bekerja pada **byte**, bukan string. Selalu ubah teks ke byte dengan encoding yang jelas (umumnya UTF-8).

## 3.6 Ukuran Keamanan dan Entropi

Keamanan diukur dalam **bit keamanan**. Keamanan 128 bit berarti penyerang butuh sekitar 2^128 operasi untuk menembusnya, yang di luar jangkauan komputasi klasik manapun.

**Entropi** mengukur ketidakpastian. Kunci 256 bit yang dibangkitkan acak memiliki entropi 256 bit. Password manusia seperti `Password123` memiliki entropi sangat rendah walau panjangnya 11 karakter, karena polanya mudah ditebak. Inilah mengapa password tidak boleh langsung dipakai sebagai kunci tanpa fungsi penurun kunci khusus (Bab 5).

## Ringkasan Bab 3

- Aritmetika modular, FPB, dan invers modular adalah alat dasar kriptografi kunci publik.
- Keamanan kriptografi bergantung pada masalah yang diyakini sulit dipecahkan.
- Bekerjalah dengan byte, dan pahami bit keamanan serta entropi.

## Latihan Bab 3

1. Hitung `(7^5) mod 13` dengan tangan, lalu verifikasi dengan `pow`.
2. Cari invers modular 5 modulo 17.
3. Mengapa `Password123` lemah walau 11 karakter?
4. Konversi kata `INFO` ke heksadesimal.

---

# Bab 4. Kriptografi Simetris

## Tujuan Pembelajaran

- Membedakan cipher blok dan cipher aliran.
- Memahami AES dan mode operasinya.
- Memahami mengapa AEAD (misalnya AES-GCM dan ChaCha20-Poly1305) adalah pilihan default.
- Mengenali bahaya penggunaan ulang nonce.

## 4.1 Konsep

Pada kriptografi simetris, pengirim dan penerima memakai **kunci yang sama**.

```
  Alice ---[ kunci K ]--->  enkripsi  ---> ciphertext ---> dekripsi ---[ kunci K ]---> Bob
```

Kelebihan: sangat cepat dan efisien. Kelemahan: **masalah distribusi kunci**, yaitu bagaimana kedua pihak menyepakati kunci rahasia tanpa dikirim lewat saluran yang bisa disadap. Masalah ini dipecahkan oleh kriptografi asimetris (Bab 6).

## 4.2 Cipher Blok dan Cipher Aliran

- **Cipher blok** mengenkripsi data dalam blok berukuran tetap. AES memakai blok 128 bit (16 byte).
- **Cipher aliran** membangkitkan aliran bit pseudo-acak (keystream) yang di-XOR dengan plaintext, seperti OTP tetapi dengan keystream dari kunci pendek. Contoh modern: ChaCha20.

## 4.3 AES (Advanced Encryption Standard)

AES adalah standar enkripsi simetris yang dipilih NIST pada tahun 2001, berdasarkan algoritma Rijndael.

|Varian|Panjang Kunci|Jumlah Putaran (round)|
|---|---|---|
|AES-128|128 bit|10|
|AES-192|192 bit|12|
|AES-256|256 bit|14|

Setiap putaran memakai empat operasi pada state 4x4 byte: SubBytes (substitusi), ShiftRows dan MixColumns (difusi), dan AddRoundKey (XOR dengan kunci putaran). Anda tidak perlu menghafal detailnya, cukup paham bahwa AES menggabungkan konfusi dan difusi berulang kali.

Hingga kini tidak ada serangan praktis terhadap AES yang utuh. Perangkat modern juga memiliki instruksi perangkat keras (AES-NI pada x86, ekstensi serupa pada ARM) yang membuatnya sangat cepat dan tahan serangan timing.

## 4.4 Mode Operasi

Cipher blok hanya mengenkripsi satu blok. Untuk data panjang, dibutuhkan **mode operasi**.

### ECB (Electronic Codebook): jangan dipakai

Setiap blok dienkripsi independen dengan kunci yang sama. Blok plaintext identik menghasilkan blok ciphertext identik sehingga pola data bocor. Contoh klasik: gambar yang dienkripsi ECB masih memperlihatkan siluet gambar aslinya.

### CBC (Cipher Block Chaining)

Setiap blok plaintext di-XOR dengan blok ciphertext sebelumnya sebelum dienkripsi, dengan IV (initialization vector) acak untuk blok pertama. Aman jika dipakai benar, tetapi tidak memberi integritas dan rentan terhadap serangan padding oracle jika implementasi salah (Bab 13). Kini jarang direkomendasikan untuk desain baru.

### CTR (Counter)

Mengubah AES menjadi cipher aliran: yang dienkripsi adalah nilai counter yang bertambah, hasilnya di-XOR dengan plaintext. Cepat dan dapat diparalelkan, tetapi **tidak ada integritas** dan nonce tidak boleh berulang.

### GCM (Galois/Counter Mode)

Menggabungkan CTR dengan autentikasi. Ini adalah mode **AEAD** (lihat bagian berikut) yang paling umum dipakai.

## 4.5 AEAD: Enkripsi yang Terautentikasi

Enkripsi saja tidak cukup. Penyerang aktif bisa mengubah ciphertext tanpa mengetahui isinya, dan dekripsi akan menghasilkan data yang rusak atau dimanipulasi. Karena itu enkripsi modern harus memberi **kerahasiaan dan integritas sekaligus**.

**AEAD (Authenticated Encryption with Associated Data)** menghasilkan ciphertext ditambah **tag autentikasi**. Saat dekripsi, tag diverifikasi lebih dulu; jika data diubah satu bit pun, dekripsi gagal. **Associated Data** adalah data tambahan (misalnya header paket) yang tidak dienkripsi tetapi ikut diautentikasi.

Dua pilihan AEAD yang direkomendasikan:

- **AES-GCM** (cepat jika ada dukungan perangkat keras).
- **ChaCha20-Poly1305** (cepat dan aman dalam perangkat lunak murni, populer di perangkat seluler).

```python
import os
from cryptography.hazmat.primitives.ciphers.aead import AESGCM

kunci = AESGCM.generate_key(bit_length=256)
aesgcm = AESGCM(kunci)

nonce = os.urandom(12)               # 96 bit, unik untuk setiap enkripsi
header = b"versi=1;pengirim=alice"   # associated data (tidak dienkripsi, tapi diautentikasi)
pesan = "Rapat dimulai pukul 09.00".encode()

ciphertext = aesgcm.encrypt(nonce, pesan, header)
print(ciphertext.hex())

# Dekripsi: nonce dan header harus sama persis
hasil = aesgcm.decrypt(nonce, ciphertext, header)
print(hasil.decode())

# Uji manipulasi: ubah satu byte ciphertext
rusak = bytearray(ciphertext)
rusak[0] ^= 1
try:
    aesgcm.decrypt(nonce, bytes(rusak), header)
except Exception as e:
    print("Manipulasi terdeteksi:", type(e).__name__)
```

## 4.6 Nonce: Aturan yang Tidak Boleh Dilanggar

**Nonce** (number used once) adalah nilai yang tidak boleh berulang untuk kunci yang sama.

- Pada AES-GCM, mengulang nonce dengan kunci yang sama adalah **kegagalan fatal**: penyerang dapat membocorkan XOR plaintext dan bahkan memalsukan pesan.
- Nonce 96 bit yang dipilih acak aman untuk jumlah pesan terbatas per kunci (pedoman umum: jauh di bawah 2^32 pesan per kunci). Untuk volume sangat besar, gunakan nonce berbasis counter atau rotasi kunci, atau pertimbangkan skema tahan salah-pakai nonce seperti AES-GCM-SIV.

## 4.7 Panjang Kunci dan Ancaman Kuantum

Algoritma Grover pada komputer kuantum secara teori menggandakan kecepatan pencarian brute force, sehingga keamanan efektif kunci simetris berkurang setengahnya dalam bit. Karena itu, untuk perlindungan jangka panjang, **AES-256** menjadi pilihan yang lebih aman (setara 128 bit terhadap penyerang kuantum). Dalam praktik, Grover sulit diparalelkan sehingga AES-128 pun dianggap masih memadai untuk banyak kasus, tetapi banyak pedoman organisasi pemerintah dan sistem berumur panjang memilih AES-256.

## Ringkasan Bab 4

- Gunakan AEAD (AES-GCM atau ChaCha20-Poly1305), bukan enkripsi mentah.
- Hindari ECB. Jangan merancang mode sendiri.
- Jangan pernah mengulang nonce untuk kunci yang sama.
- AES-256 adalah pilihan aman untuk keamanan jangka panjang.

## Latihan Bab 4

1. Mengapa ECB membocorkan pola data?
2. Jelaskan apa itu associated data dan berikan contoh pemakaian.
3. Modifikasi kode AES-GCM agar memakai ChaCha20Poly1305 (`from cryptography.hazmat.primitives.ciphers.aead import ChaCha20Poly1305`).
4. Apa yang bisa terjadi jika dua pesan berbeda dienkripsi dengan kunci dan nonce yang sama pada mode CTR?

---

# Bab 5. Fungsi Hash, MAC, dan Penyimpanan Password

## Tujuan Pembelajaran

- Memahami sifat-sifat fungsi hash kriptografis.
- Mengenal SHA-2, SHA-3, dan BLAKE.
- Membedakan hash biasa, MAC, dan HMAC.
- Menyimpan password dengan benar menggunakan fungsi hash password.

## 5.1 Apa Itu Fungsi Hash?

Fungsi hash mengubah data berukuran berapa pun menjadi keluaran berukuran tetap yang disebut **digest** atau sidik jari (fingerprint).

```
  "Halo"            --SHA-256-->  a 256-bit digest (64 karakter hex)
  seluruh isi film  --SHA-256-->  tetap 256 bit
```

Sebagai contoh, SHA-256 dari string kosong adalah:

```
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
```

## 5.2 Sifat Fungsi Hash Kriptografis

1. **Deterministik**: input sama selalu menghasilkan output sama.
2. **Efisien**: cepat dihitung.
3. **Pre-image resistance (satu arah)**: dari digest, sulit menemukan input.
4. **Second pre-image resistance**: diberi satu input, sulit menemukan input lain berhash sama.
5. **Collision resistance**: sulit menemukan dua input berbeda yang berhash sama.
6. **Efek longsoran (avalanche effect)**: perubahan satu bit input mengubah sekitar separuh bit output.

```python
import hashlib

print(hashlib.sha256(b"Halo").hexdigest())
print(hashlib.sha256(b"halo").hexdigest())   # satu huruf berbeda, hasil sangat berbeda
print(hashlib.sha3_256(b"Halo").hexdigest())
print(hashlib.blake2b(b"Halo", digest_size=32).hexdigest())
```

## 5.3 Algoritma Hash yang Umum

|Algoritma|Ukuran Output|Status|
|---|---|---|
|MD5|128 bit|**Rusak**. Tabrakan bisa dibuat dalam hitungan detik. Jangan dipakai untuk keamanan|
|SHA-1|160 bit|**Rusak**. Tabrakan pertama diperlihatkan tahun 2017 (SHAttered). Sudah ditinggalkan|
|SHA-256, SHA-384, SHA-512 (keluarga SHA-2)|256 sampai 512 bit|Aman, paling luas dipakai|
|SHA3-256, SHA3-512|256 sampai 512 bit|Aman, desain berbeda (Keccak) sebagai cadangan jika SHA-2 bermasalah|
|BLAKE2, BLAKE3|Fleksibel|Aman dan sangat cepat|

Catatan teknis: SHA-2 rentan terhadap **length extension attack** jika dipakai sembarangan untuk membuat MAC (misalnya `SHA256(rahasia + pesan)`). Gunakan HMAC, bukan konstruksi buatan sendiri.

Pemakaian hash: verifikasi integritas file, pengenal data (content addressing), komponen tanda tangan digital, pohon Merkle (blockchain, Certificate Transparency), dan penurunan kunci.

## 5.4 MAC dan HMAC

Hash biasa tidak memakai kunci, sehingga penyerang aktif bisa mengubah data lalu menghitung ulang hash-nya. Untuk menjamin integritas **dan keaslian**, dipakai **MAC (Message Authentication Code)**, yaitu hash berkunci.

**HMAC** membangun MAC dari fungsi hash dan kunci rahasia, dan standar yang sangat teruji.

```python
import hmac, hashlib, os

kunci = os.urandom(32)
pesan = b"transfer=500000;ke=12345"

tag = hmac.new(kunci, pesan, hashlib.sha256).digest()

# Verifikasi harus memakai perbandingan waktu-konstan, bukan ==
def verifikasi(kunci, pesan, tag_diterima):
    tag_hitung = hmac.new(kunci, pesan, hashlib.sha256).digest()
    return hmac.compare_digest(tag_hitung, tag_diterima)

print(verifikasi(kunci, pesan, tag))                 # True
print(verifikasi(kunci, b"transfer=999999;ke=12345", tag))  # False
```

Perhatikan `hmac.compare_digest`: perbandingan biasa dengan `==` berhenti di byte pertama yang berbeda sehingga bisa membocorkan informasi lewat waktu respons (timing attack).

## 5.5 Menyimpan Password dengan Benar

Aturan utama: **jangan pernah menyimpan password dalam bentuk asli (plaintext), dan jangan pakai hash cepat seperti SHA-256 polos.**

Alasannya, hash cepat dapat ditebak miliaran kali per detik dengan GPU. Jika database bocor, penyerang melakukan serangan kamus, brute force, atau memakai **rainbow table** (tabel hash yang sudah dihitung sebelumnya).

Solusinya:

1. **Salt**: nilai acak unik per pengguna yang digabung dengan password sebelum di-hash. Salt tidak rahasia, tetapi menggagalkan rainbow table dan membuat password sama menghasilkan hash berbeda.
2. **Fungsi hash password yang sengaja lambat dan boros memori**, dengan faktor biaya yang bisa diatur.

Pilihan yang direkomendasikan:

|Algoritma|Catatan|
|---|---|
|**Argon2id**|Pemenang Password Hashing Competition, distandarkan di RFC 9106. Pilihan utama untuk sistem baru|
|scrypt|Boros memori, tersedia di `hashlib`|
|bcrypt|Teruji lama, masih diterima, batas panjang input 72 byte|
|PBKDF2|Diterima untuk kepatuhan standar (misal FIPS), tetapi tidak tahan GPU sebaik Argon2|

```python
from argon2 import PasswordHasher
from argon2.exceptions import VerifyMismatchError

ph = PasswordHasher()   # parameter default sudah wajar; sesuaikan dengan beban server Anda
hash_tersimpan = ph.hash("PasswordRahasia!2026")
print(hash_tersimpan)   # sudah memuat salt dan parameter

try:
    ph.verify(hash_tersimpan, "PasswordRahasia!2026")
    print("Password benar")
    ph.verify(hash_tersimpan, "salah")
except VerifyMismatchError:
    print("Password salah")
```

Praktik tambahan: gunakan autentikasi multi-faktor, dan pertimbangkan passkey (Bab 9) yang menghilangkan password dari persamaan.

## 5.6 KDF: Menurunkan Kunci

**KDF (Key Derivation Function)** mengubah materi kunci awal (misalnya hasil pertukaran kunci atau password) menjadi satu atau banyak kunci kriptografis berkualitas.

- Dari password: Argon2, scrypt, PBKDF2.
- Dari rahasia acak berentropi tinggi: **HKDF** (RFC 5869), yang dipakai luas di TLS 1.3, Signal, dan WireGuard.

```python
from cryptography.hazmat.primitives.kdf.hkdf import HKDF
from cryptography.hazmat.primitives import hashes
import os

rahasia_awal = os.urandom(32)
kunci_enkripsi = HKDF(algorithm=hashes.SHA256(), length=32, salt=None,
                      info=b"aplikasi-saya enkripsi v1").derive(rahasia_awal)
kunci_mac = HKDF(algorithm=hashes.SHA256(), length=32, salt=None,
                 info=b"aplikasi-saya mac v1").derive(rahasia_awal)
print(kunci_enkripsi != kunci_mac)  # True: parameter info berbeda, kunci berbeda
```

## Ringkasan Bab 5

- Hash: sidik jari data. Hindari MD5 dan SHA-1. Gunakan SHA-256/SHA-3/BLAKE.
- Untuk keaslian pesan, gunakan HMAC dan bandingkan dengan waktu konstan.
- Simpan password dengan Argon2id (atau scrypt, bcrypt) plus salt, jangan SHA-256 polos.
- Gunakan HKDF atau KDF password untuk menurunkan kunci.

## Latihan Bab 5

1. Hitung SHA-256 dua file yang hanya berbeda satu byte. Bandingkan hasilnya.
2. Mengapa salt tidak perlu dirahasiakan tetapi tetap berguna?
3. Mengapa `SHA256(kunci + pesan)` bukan MAC yang baik?
4. Tulis fungsi `daftar_pengguna` yang menyimpan hash Argon2 dan memverifikasi login.

---

# Bab 6. Kriptografi Asimetris

## Tujuan Pembelajaran

- Memahami konsep pasangan kunci publik dan privat.
- Memahami pertukaran kunci Diffie-Hellman.
- Memahami RSA secara konseptual dan dengan contoh kecil.
- Mengenal kriptografi kurva eliptik (ECC), X25519, dan enkripsi hibrida.

## 6.1 Konsep Kunci Publik

Pada tahun 1976, Whitfield Diffie dan Martin Hellman memperkenalkan gagasan revolusioner: **pasangan kunci**.

- **Kunci publik**: boleh disebarkan ke siapa pun.
- **Kunci privat**: dirahasiakan oleh pemiliknya.

Dua penggunaan utama:

1. **Enkripsi / pertukaran kunci**: data yang dikunci dengan kunci publik hanya bisa dibuka dengan kunci privat pasangannya.
2. **Tanda tangan digital**: dibuat dengan kunci privat, diverifikasi dengan kunci publik (Bab 7).

Analogi: kunci publik seperti kotak surat dengan celah; siapa pun boleh memasukkan surat, tetapi hanya pemilik kunci kotak yang bisa mengambilnya.

Kriptografi asimetris jauh lebih lambat daripada simetris, jadi dalam praktik keduanya digabung (bagian 6.6).

## 6.2 Pertukaran Kunci Diffie-Hellman (DH)

Dua pihak yang belum pernah bertemu dapat menyepakati rahasia bersama lewat saluran terbuka. Contoh dengan angka kecil:

```
Publik: p = 23, g = 5

Alice memilih rahasia a = 6   ->  A = g^a mod p = 5^6  mod 23 = 8
Bob   memilih rahasia b = 15  ->  B = g^b mod p = 5^15 mod 23 = 19

Alice dan Bob bertukar A dan B secara terbuka.

Alice menghitung: B^a mod p = 19^6  mod 23 = 2
Bob   menghitung: A^b mod p = 8^15  mod 23 = 2

Rahasia bersama = 2
```

Penyadap hanya melihat `p, g, A, B`. Untuk mendapatkan `a` ia harus menyelesaikan masalah logaritma diskret, yang untuk bilangan besar sangat sulit.

Catatan penting: DH polos tidak mengautentikasi pihak lawan, sehingga rentan man-in-the-middle. Karena itu selalu dikombinasikan dengan tanda tangan atau sertifikat (Bab 7 dan 8). Praktik modern memakai **ephemeral DH (DHE/ECDHE)**, yaitu kunci DH baru untuk setiap sesi, yang memberikan **forward secrecy**: jika kunci jangka panjang bocor di masa depan, sesi lama tetap aman.

## 6.3 RSA

RSA (Rivest, Shamir, Adleman, 1977) bersandar pada sulitnya memfaktorkan bilangan besar.

Pembangkitan kunci (contoh kecil):

```
1. Pilih dua bilangan prima:     p = 61, q = 53
2. Hitung modulus:               n = p * q = 3233
3. Hitung phi:                   phi = (p-1)(q-1) = 3120
4. Pilih eksponen publik e:      e = 17  (relatif prima dengan phi)
5. Hitung eksponen privat d:     d = e^-1 mod phi = 2753

Kunci publik : (n = 3233, e = 17)
Kunci privat : (n = 3233, d = 2753)

Enkripsi : c = m^e mod n   -> m = 65  ->  c = 65^17 mod 3233 = 2790
Dekripsi : m = c^d mod n   -> 2790^2753 mod 3233 = 65
```

```python
# TOY RSA: hanya untuk belajar, JANGAN dipakai untuk data nyata
p, q = 61, 53
n = p * q
phi = (p - 1) * (q - 1)
e = 17
d = pow(e, -1, phi)       # 2753

m = 65
c = pow(m, e, n)
print(c)                  # 2790
print(pow(c, d, n))       # 65
```

Mengapa contoh di atas tidak aman:

- Bilangan terlalu kecil sehingga n mudah difaktorkan. RSA nyata memakai n minimal 2048 bit (disarankan 3072 bit untuk perlindungan jangka panjang).
- **Textbook RSA** tanpa padding bersifat deterministik dan bisa dimanipulasi. RSA nyata wajib memakai padding: **OAEP** untuk enkripsi dan **PSS** untuk tanda tangan. Padding PKCS#1 v1.5 untuk enkripsi sudah rentan dan sebaiknya dihindari.

Di praktik, RSA untuk enkripsi langsung semakin jarang dipakai; tren menuju pertukaran kunci berbasis kurva eliptik, dan kemudian KEM pasca-kuantum.

## 6.4 Kriptografi Kurva Eliptik (ECC)

ECC memakai operasi pada titik-titik di kurva eliptik atas bidang berhingga. Operasi utamanya adalah perkalian skalar: diberi titik dasar `G` dan bilangan rahasia `k`, mudah menghitung `K = k * G`, tetapi sangat sulit mencari `k` dari `K` (masalah logaritma diskret kurva eliptik).

Keuntungan: kunci jauh lebih pendek untuk tingkat keamanan sama.

|Keamanan (bit)|RSA / DH (modulus)|ECC (ukuran kunci)|
|---|---|---|
|112|2048 bit|224 bit|
|128|3072 bit|256 bit|
|192|7680 bit|384 bit|
|256|15360 bit|512 bit|

Kurva yang umum dipakai:

- **P-256 (secp256r1)**, standar NIST, luas dipakai.
- **Curve25519** (untuk pertukaran kunci dengan X25519 dan tanda tangan Ed25519), dirancang agar mudah diimplementasikan dengan aman dan cepat. Distandarkan di RFC 7748 dan RFC 8032.

## 6.5 Contoh: Pertukaran Kunci X25519

```python
from cryptography.hazmat.primitives.asymmetric.x25519 import X25519PrivateKey
from cryptography.hazmat.primitives.kdf.hkdf import HKDF
from cryptography.hazmat.primitives import hashes

# Alice dan Bob masing-masing membuat pasangan kunci sementara (ephemeral)
priv_alice = X25519PrivateKey.generate()
priv_bob = X25519PrivateKey.generate()

pub_alice = priv_alice.public_key()
pub_bob = priv_bob.public_key()

# Hanya kunci publik yang dikirim lewat jaringan
rahasia_alice = priv_alice.exchange(pub_bob)
rahasia_bob = priv_bob.exchange(pub_alice)
print(rahasia_alice == rahasia_bob)   # True

# Jangan memakai hasil exchange langsung sebagai kunci. Turunkan dengan HKDF.
kunci_sesi = HKDF(algorithm=hashes.SHA256(), length=32, salt=None,
                  info=b"demo sesi").derive(rahasia_alice)
print(len(kunci_sesi))                # 32 byte, siap untuk AES-256-GCM
```

## 6.6 Enkripsi Hibrida

Kriptografi simetris cepat tetapi punya masalah distribusi kunci; asimetris menyelesaikan distribusi kunci tetapi lambat. Solusi praktis adalah **enkripsi hibrida**:

```
1. Pihak-pihak menyepakati kunci sesi memakai pertukaran kunci asimetris (misal ECDHE).
2. Kunci sesi diturunkan dengan KDF.
3. Seluruh data dienkripsi memakai AEAD simetris (misal AES-256-GCM).
```

Pola ini dipakai TLS, SSH, Signal, WireGuard, dan hampir semua protokol modern.

## Ringkasan Bab 6

- Kunci publik menyelesaikan masalah distribusi kunci.
- DH dan ECDH menyepakati rahasia bersama; gunakan versi ephemeral untuk forward secrecy.
- RSA butuh ukuran besar dan padding (OAEP, PSS). ECC lebih ringkas; X25519 adalah pilihan modern.
- Dalam praktik: pertukaran kunci asimetris, lalu enkripsi data dengan AEAD simetris.
- RSA, DH, dan ECC semuanya rentan terhadap komputer kuantum skala besar (Bab 11).

## Latihan Bab 6

1. Ulangi contoh DH dengan `p = 23, g = 5, a = 4, b = 3`. Berapa rahasia bersamanya?
2. Hitung RSA kecil dengan `p = 11, q = 13, e = 7`, lalu enkripsi `m = 9`.
3. Mengapa textbook RSA tanpa padding tidak aman?
4. Apa itu forward secrecy dan mengapa penting?

---

# Bab 7. Tanda Tangan Digital

## Tujuan Pembelajaran

- Memahami cara kerja tanda tangan digital.
- Membedakan MAC dan tanda tangan digital.
- Mengenal RSA-PSS, ECDSA, dan Ed25519.
- Membuat dan memverifikasi tanda tangan dengan Python.

## 7.1 Cara Kerja

Tanda tangan digital membuktikan bahwa:

1. pesan benar-benar dibuat oleh pemilik kunci privat (**autentikasi**),
2. pesan tidak diubah (**integritas**),
3. pemilik tidak dapat menyangkal (**non-repudiation**).

```
Penandatangan:  hash(pesan)  --[kunci privat]-->  tanda tangan
Pemeriksa    :  verifikasi(tanda tangan, pesan, kunci publik)  ->  sah / tidak sah
```

Dalam praktik algoritma modern menangani hashing secara internal, jadi Anda cukup memanggil `sign(pesan)` dan `verify(tanda_tangan, pesan)`.

## 7.2 MAC Versus Tanda Tangan Digital

|Aspek|MAC (HMAC)|Tanda Tangan Digital|
|---|---|---|
|Kunci|Simetris (dibagi dua pihak)|Asimetris (privat dan publik)|
|Siapa bisa memverifikasi|Pihak yang punya kunci|Siapa saja yang punya kunci publik|
|Non-repudiation|Tidak ada (kedua pihak bisa membuat tag)|Ada|
|Kecepatan|Sangat cepat|Lebih lambat|

## 7.3 Algoritma yang Umum

- **RSA-PSS**: tanda tangan RSA dengan padding probabilistik. Hindari PKCS#1 v1.5 untuk desain baru jika bisa.
- **ECDSA**: tanda tangan di kurva eliptik (P-256, P-384). Sangat bergantung pada nonce acak yang baik; nonce lemah atau berulang membocorkan kunci privat (peristiwa nyata pernah terjadi pada konsol game dan dompet kripto).
- **Ed25519**: skema deterministik, cepat, kunci kecil (32 byte), tanda tangan 64 byte, dan menghilangkan risiko nonce buruk dari ECDSA. Pilihan default yang baik untuk sistem baru jika tidak ada kendala kompatibilitas.

## 7.4 Contoh Ed25519

```python
from cryptography.hazmat.primitives.asymmetric.ed25519 import Ed25519PrivateKey
from cryptography.exceptions import InvalidSignature

kunci_privat = Ed25519PrivateKey.generate()
kunci_publik = kunci_privat.public_key()

dokumen = b"Surat keputusan nomor 123/2026"
tanda_tangan = kunci_privat.sign(dokumen)
print(len(tanda_tangan))   # 64 byte

# Verifikasi dokumen asli
try:
    kunci_publik.verify(tanda_tangan, dokumen)
    print("Tanda tangan SAH")
except InvalidSignature:
    print("Tanda tangan TIDAK sah")

# Verifikasi dokumen yang diubah
try:
    kunci_publik.verify(tanda_tangan, b"Surat keputusan nomor 999/2026")
    print("Tanda tangan SAH")
except InvalidSignature:
    print("Dokumen telah diubah atau tanda tangan palsu")
```

## 7.5 Contoh RSA-PSS

```python
from cryptography.hazmat.primitives.asymmetric import rsa, padding
from cryptography.hazmat.primitives import hashes

privat = rsa.generate_private_key(public_exponent=65537, key_size=3072)
publik = privat.public_key()

data = b"Kontrak kerja sama"
ttd = privat.sign(
    data,
    padding.PSS(mgf=padding.MGF1(hashes.SHA256()),
                salt_length=padding.PSS.MAX_LENGTH),
    hashes.SHA256(),
)
publik.verify(
    ttd, data,
    padding.PSS(mgf=padding.MGF1(hashes.SHA256()),
                salt_length=padding.PSS.MAX_LENGTH),
    hashes.SHA256(),
)
print("RSA-PSS terverifikasi")   # exception InvalidSignature jika gagal
```

## 7.6 Pertanyaan yang Belum Terjawab: Siapa Pemilik Kunci Publik Itu?

Tanda tangan hanya membuktikan bahwa pesan dibuat oleh pemegang kunci privat pasangan sebuah kunci publik. Namun, bagaimana kita yakin kunci publik itu milik orang atau organisasi yang kita maksud? Jawabannya adalah sertifikat digital dan PKI, dibahas di bab berikut.

## Ringkasan Bab 7

- Tanda tangan digital memberi autentikasi, integritas, dan non-repudiation.
- Ed25519 adalah pilihan modern; RSA-PSS dan ECDSA masih luas dipakai.
- Nonce yang buruk pada ECDSA dapat membocorkan kunci privat.
- Tanda tangan tidak menjawab "kunci publik ini milik siapa"; itu tugas PKI.

## Latihan Bab 7

1. Mengapa HMAC tidak memberi non-repudiation?
2. Ubah satu byte pada `tanda_tangan` di contoh Ed25519 dan amati hasilnya.
3. Bandingkan ukuran tanda tangan Ed25519 dan RSA-3072.
4. Mengapa Ed25519 lebih sulit disalahgunakan dibanding ECDSA?

---

# Bab 8. PKI, Sertifikat Digital, dan TLS

## Tujuan Pembelajaran

- Memahami masalah autentikasi kunci publik dan solusi PKI.
- Memahami struktur sertifikat X.509 dan rantai kepercayaan.
- Memahami cara kerja TLS 1.3 secara garis besar.
- Memahami tren terbaru, seperti masa berlaku sertifikat yang makin pendek.

## 8.1 Masalah Utama

Jika Anda membuka `https://bank.example`, bagaimana browser tahu kunci publik yang diterima benar-benar milik bank, bukan penyerang di tengah jaringan? Jawabannya adalah **sertifikat digital** yang ditandatangani pihak tepercaya.

## 8.2 Sertifikat X.509

Sertifikat adalah dokumen digital yang mengikat identitas (misalnya nama domain) dengan kunci publik, lalu ditandatangani oleh **Certificate Authority (CA)**.

Isi penting sertifikat:

- Subject (pemilik, misalnya nama domain) dan Subject Alternative Name (SAN).
- Kunci publik pemilik.
- Issuer (CA penerbit).
- Masa berlaku (not before dan not after).
- Tanda tangan digital CA.

## 8.3 Rantai Kepercayaan

```
 Root CA (ada di trust store OS/browser, disimpan offline dengan sangat aman)
    |  menandatangani
    v
 Intermediate CA
    |  menandatangani
    v
 Sertifikat Server (misalnya untuk example.co.id)
```

Browser memverifikasi rantai tanda tangan sampai ke root CA yang sudah dipercaya, memeriksa nama domain, masa berlaku, dan status pencabutan.

Mekanisme pendukung:

- **Revocation**: pencabutan sertifikat (CRL, OCSP). Karena pencabutan sulit dijalankan andal, tren industri menuju sertifikat berumur pendek.
- **Certificate Transparency (CT)**: log publik yang hanya bisa ditambah (append-only) berisi semua sertifikat yang diterbitkan, sehingga penerbitan sertifikat palsu dapat dideteksi.
- **ACME** (RFC 8555) dan layanan seperti Let's Encrypt: otomatisasi penerbitan dan perpanjangan sertifikat secara gratis.

## 8.4 Masa Berlaku Sertifikat yang Semakin Pendek

CA/Browser Forum menyetujui pengurangan bertahap masa berlaku maksimum sertifikat TLS publik. Jadwal yang disepakati:

|Berlaku untuk sertifikat yang diterbitkan mulai|Masa berlaku maksimum|
|---|---|
|15 Maret 2026|200 hari|
|15 Maret 2027|100 hari|
|15 Maret 2029|47 hari|

Implikasinya bagi Anda sebagai calon engineer: **otomatisasi sertifikat (ACME) bukan lagi pilihan, melainkan keharusan.** Perpanjangan manual setiap tahun tidak lagi realistis. Periksa selalu kebijakan terbaru di cabforum.org karena jadwal seperti ini dapat diperbarui.

## 8.5 TLS 1.3 secara Garis Besar

TLS (Transport Layer Security) adalah protokol yang mengamankan HTTP menjadi HTTPS, serta banyak protokol lain. Versi terkini adalah **TLS 1.3 (RFC 8446)**. Versi lama (SSL, TLS 1.0, TLS 1.1) sudah ditinggalkan; TLS 1.2 masih dipakai luas tetapi desain baru sebaiknya memprioritaskan TLS 1.3.

Alur handshake TLS 1.3 (disederhanakan):

```
Klien                                             Server
  |--- ClientHello (versi, cipher yang didukung,     |
  |    kunci publik ephemeral untuk key exchange) -->|
  |                                                  |
  |<-- ServerHello (pilihan cipher, kunci ephemeral) |
  |<-- {Sertifikat, tanda tangan, Finished}  (sudah  |
  |     terenkripsi)                                 |
  |                                                  |
  |--- {Finished} -------------------------------->  |
  |                                                  |
  |<=========== Data aplikasi (AEAD) ===============>|
```

Poin penting TLS 1.3:

- Hanya cipher suite modern berbasis AEAD (AES-GCM, ChaCha20-Poly1305).
- Pertukaran kunci selalu ephemeral (ECDHE atau, kini, hybrid pasca-kuantum), sehingga ada **forward secrecy**.
- Handshake lebih singkat (1 round trip) dan sebagian besar terenkripsi.
- Algoritma lemah (RC4, MD5, SHA-1 untuk tanda tangan, mode CBC, RSA key exchange statis) dihapus.

Anda dapat melihat sertifikat sebuah situs dengan:

```bash
openssl s_client -connect example.com:443 -servername example.com -tls1_3 </dev/null 2>/dev/null | openssl x509 -noout -subject -issuer -dates
```

## Ringkasan Bab 8

- PKI mengikat identitas dengan kunci publik lewat sertifikat yang ditandatangani CA.
- Browser memverifikasi rantai sertifikat sampai root CA tepercaya.
- Masa berlaku sertifikat publik terus memendek, sehingga otomatisasi (ACME) wajib.
- TLS 1.3 memakai key exchange ephemeral dan AEAD sehingga lebih aman dan lebih cepat.

## Latihan Bab 8

1. Gambarkan rantai sertifikat sebuah situs pilihan Anda lewat browser (klik ikon gembok).
2. Mengapa Certificate Transparency mengurangi risiko CA yang disusupi?
3. Mengapa TLS 1.3 menghapus RSA key exchange statis?
4. Mengapa masa berlaku sertifikat yang lebih pendek meningkatkan keamanan?

---

# Bab 9. Protokol Kriptografi dalam Praktik

## Tujuan Pembelajaran

- Mengenal protokol yang mengamankan komunikasi sehari-hari.
- Memahami konsep end-to-end encryption (E2EE) dan double ratchet.
- Memahami passkey (WebAuthn/FIDO2).

## 9.1 Protokol Itu Lebih Dari Algoritma

Algoritma yang kuat bisa gagal jika protokolnya salah dirancang. Protokol menyatukan primitif (enkripsi, hash, tanda tangan, pertukaran kunci) menjadi sistem utuh. Merancang protokol sangat sulit; gunakan protokol yang sudah teruji.

## 9.2 SSH

SSH mengamankan akses terminal jarak jauh. Server memiliki kunci host yang dicatat klien saat koneksi pertama (`known_hosts`), dan pengguna dapat login dengan kunci publik (disarankan: Ed25519) alih-alih password.

```bash
ssh-keygen -t ed25519 -C "email@contoh.id"
```

Versi OpenSSH terbaru telah menjadikan pertukaran kunci hybrid pasca-kuantum (`mlkem768x25519-sha256`) sebagai default, sehingga koneksi SSH sudah mulai terlindung dari ancaman "harvest now, decrypt later" (Bab 11).

## 9.3 VPN dan WireGuard

WireGuard adalah protokol VPN modern yang sengaja dibuat sederhana, dengan set algoritma tetap: Curve25519 (pertukaran kunci), ChaCha20-Poly1305 (enkripsi), BLAKE2s (hash), dan HKDF. Basis kode yang kecil memudahkan audit keamanan.

## 9.4 End-to-End Encryption dan Protokol Signal

Pada E2EE, hanya pengirim dan penerima yang dapat membaca pesan; server pun tidak bisa. Protokol Signal (dipakai Signal dan sebagai basis aplikasi pesan lain) memiliki dua komponen utama:

1. **Pertukaran kunci awal (X3DH, kini PQXDH)**: menyepakati kunci awal bahkan saat penerima sedang offline. PQXDH menambahkan komponen pasca-kuantum.
2. **Double Ratchet**: kunci pesan diperbarui terus-menerus. Hasilnya:
    - **Forward secrecy**: kunci lama tidak dapat dipakai membuka pesan lama jika kunci saat ini bocor.
    - **Post-compromise security**: sistem pulih secara otomatis setelah kebocoran kunci sementara.

## 9.5 Passkey (WebAuthn / FIDO2)

Passkey menggantikan password dengan kriptografi kunci publik.

```
Pendaftaran : perangkat membuat pasangan kunci untuk situs tersebut;
              kunci publik dikirim ke server, kunci privat tetap di perangkat.
Login       : server mengirim challenge acak;
              perangkat menandatanganinya (setelah verifikasi biometrik/PIN);
              server memverifikasi dengan kunci publik.
```

Keunggulan: tahan phishing (kunci terikat pada domain asli), tidak ada rahasia bersama di server yang bisa bocor, dan tidak ada password untuk dilupakan atau dicuri. Dukungannya sudah luas di sistem operasi dan browser, dan merupakan arah masa depan autentikasi.

## 9.6 Ringkasan Primitif dalam Protokol Populer

|Protokol|Pertukaran Kunci|Enkripsi|Autentikasi|
|---|---|---|---|
|TLS 1.3|ECDHE / hybrid ML-KEM|AES-GCM, ChaCha20-Poly1305|Sertifikat + tanda tangan|
|SSH|X25519 / hybrid ML-KEM|AES-GCM, ChaCha20-Poly1305|Kunci host + kunci pengguna|
|WireGuard|Curve25519|ChaCha20-Poly1305|Kunci publik peer|
|Signal|X3DH/PQXDH + Double Ratchet|AEAD|Kunci identitas|
|Passkey|(tanda tangan challenge)|Tidak relevan|ECDSA/Ed25519 pada perangkat|

## Ringkasan Bab 9

- Protokol menggabungkan primitif; jangan merancang protokol sendiri.
- E2EE dengan double ratchet memberi forward secrecy dan post-compromise security.
- Passkey adalah autentikasi tahan phishing berbasis kunci publik.

## Latihan Bab 9

1. Buat pasangan kunci SSH Ed25519 dan jelaskan isi file `.pub` dan file privatnya.
2. Jelaskan perbedaan forward secrecy dan post-compromise security.
3. Mengapa passkey tahan terhadap phishing, sedangkan password tidak?

---

# Bab 10. Bilangan Acak dan Manajemen Kunci

## Tujuan Pembelajaran

- Memahami pentingnya bilangan acak yang aman secara kriptografis.
- Memahami siklus hidup kunci dan praktik manajemen kunci.
- Mengenal HSM, KMS, dan konsep envelope encryption.

## 10.1 Bilangan Acak

Semua kunci, nonce, dan salt harus dibangkitkan dengan **CSPRNG (Cryptographically Secure Pseudo-Random Number Generator)** yang mengambil entropi dari sistem operasi.

```python
import os, secrets

kunci = os.urandom(32)            # 32 byte acak aman dari OS
token = secrets.token_hex(16)     # token acak aman, cocok untuk reset password
print(kunci.hex(), token)
```

**Jangan pernah** memakai modul `random` Python (atau `Math.random()` di JavaScript, `rand()` di C) untuk keperluan keamanan. Generator tersebut dapat diprediksi. Kelemahan RNG adalah penyebab banyak kebocoran kunci di dunia nyata.

## 10.2 Siklus Hidup Kunci

1. **Pembangkitan**: dengan CSPRNG, panjang sesuai kebijakan.
2. **Distribusi**: aman (pertukaran kunci, bukan dikirim lewat email atau chat).
3. **Penyimpanan**: terenkripsi, akses terbatas (HSM, KMS, secret manager), tidak disimpan di source code atau repositori.
4. **Penggunaan**: satu kunci untuk satu tujuan (pisahkan kunci enkripsi dan kunci tanda tangan).
5. **Rotasi**: penggantian berkala dan saat dicurigai bocor.
6. **Pencadangan dan pemulihan**: dengan kendali ketat.
7. **Pemusnahan**: penghapusan aman saat tidak dipakai lagi.

## 10.3 Envelope Encryption

Pola umum di layanan cloud:

```
   Master Key (KEK)  : disimpan di KMS/HSM, tidak pernah keluar
        |
        | mengenkripsi
        v
   Data Key (DEK)    : kunci unik per objek/berkas, disimpan terenkripsi di samping data
        |
        | mengenkripsi
        v
   Data              : dienkripsi dengan AES-256-GCM
```

Manfaatnya: rotasi master key cukup mengenkripsi ulang DEK, bukan seluruh data; dan kompromi satu DEK hanya memengaruhi satu objek.

## 10.4 Perangkat Keras Pengaman Kunci

- **HSM (Hardware Security Module)**: perangkat khusus tahan modifikasi yang menyimpan kunci dan melakukan operasi kriptografi di dalamnya sehingga kunci privat tidak pernah keluar.
- **TPM (Trusted Platform Module)**: chip pada komputer untuk menyimpan kunci dan mengukur integritas boot.
- **Secure Enclave dan TEE**: area terisolasi pada prosesor ponsel dan komputer.
- **Cloud KMS**: layanan manajemen kunci terkelola di penyedia cloud.

## 10.5 Crypto Agility

**Crypto agility** adalah kemampuan sistem mengganti algoritma kriptografi tanpa merombak total arsitektur. Dengan transisi ke pasca-kuantum (Bab 11), ini menjadi prinsip desain wajib:

- Jangan menanam nama algoritma secara permanen di banyak tempat.
- Simpan versi atau identifier algoritma pada data terenkripsi dan tanda tangan.
- Buat inventaris penggunaan kriptografi (sering disebut CBOM: Cryptographic Bill of Materials) agar tahu apa yang harus dimigrasikan.

## Ringkasan Bab 10

- Selalu gunakan CSPRNG (`os.urandom`, `secrets`) untuk materi kunci.
- Kelola siklus hidup kunci; jangan simpan kunci di kode atau repositori.
- Gunakan envelope encryption, HSM, atau KMS pada sistem serius.
- Rancang sistem dengan crypto agility.

## Latihan Bab 10

1. Mengapa `random.randint` tidak boleh dipakai untuk membuat token reset password?
2. Jelaskan envelope encryption dengan gambar sederhana buatan Anda sendiri.
3. Cari satu insiden kebocoran kunci API di repositori publik dan identifikasi kesalahan manajemen kuncinya.

---

# Bab 11. Kriptografi Pasca-Kuantum

## Tujuan Pembelajaran

- Memahami ancaman komputer kuantum terhadap kriptografi saat ini.
- Memahami konsep "harvest now, decrypt later".
- Mengenal standar NIST: ML-KEM, ML-DSA, SLH-DSA, dan perkembangannya.
- Memahami pendekatan hybrid dan rencana migrasi.

## 11.1 Ancaman Komputer Kuantum

Komputer kuantum memanfaatkan superposisi dan keterkaitan (entanglement) untuk menyelesaikan masalah tertentu jauh lebih cepat dari komputer klasik. Dua algoritma kuantum penting bagi kriptografi:

|Algoritma|Dampak|
|---|---|
|**Shor**|Memecahkan faktorisasi dan logaritma diskret secara efisien. Artinya RSA, Diffie-Hellman, dan ECC (ECDH, ECDSA, Ed25519) **dapat dipatahkan**|
|**Grover**|Mempercepat pencarian brute force secara kuadratik. Kunci simetris dan hash kehilangan kira-kira setengah bit keamanan; solusinya cukup menambah panjang kunci (AES-256)|

Kesimpulan: yang terancam serius adalah **kriptografi kunci publik**, sedangkan kriptografi simetris dan hash relatif aman dengan penyesuaian ukuran.

Hingga pertengahan 2026, belum ada komputer kuantum yang mampu memecahkan RSA-2048 atau kurva eliptik yang dipakai praktis. Namun perkembangan perangkat keras dan koreksi kesalahan kuantum terus berjalan, dan waktu kedatangannya tidak pasti. Karena itu pendekatan yang bijak adalah bersiap lebih awal.

## 11.2 Harvest Now, Decrypt Later

Penyerang yang kuat dapat **merekam lalu lintas terenkripsi hari ini** dan menyimpannya, lalu mendekripsinya kelak ketika komputer kuantum tersedia. Ini membuat data dengan masa sensitif panjang (rahasia negara, data kesehatan, data keuangan, kekayaan intelektual) sudah berisiko sekarang.

Aturan praktis (teorema Mosca): jika

```
(masa data harus dirahasiakan) + (waktu migrasi sistem) > (waktu sampai komputer kuantum relevan)
```

maka Anda sudah terlambat. Untuk **kerahasiaan**, migrasi harus diprioritaskan karena risiko harvest-now-decrypt-later. Untuk **tanda tangan**, risikonya baru muncul saat komputer kuantum benar-benar ada (penyerang tidak bisa memalsukan tanda tangan di masa lalu), tetapi sistem berumur panjang seperti firmware dan root CA tetap perlu direncanakan dari sekarang.

## 11.3 Standar NIST

Setelah kompetisi publik sejak 2016, NIST menerbitkan standar pasca-kuantum pertama pada Agustus 2024:

|Standar|Nama Algoritma|Fungsi|Asal Nama Awal|Basis Matematika|
|---|---|---|---|---|
|FIPS 203|**ML-KEM**|Pertukaran kunci (KEM)|CRYSTALS-Kyber|Module lattice|
|FIPS 204|**ML-DSA**|Tanda tangan digital|CRYSTALS-Dilithium|Module lattice|
|FIPS 205|**SLH-DSA**|Tanda tangan digital|SPHINCS+|Fungsi hash (stateless)|

Perkembangan lain yang perlu Anda ketahui (periksa status terbaru di situs NIST):

- **FN-DSA** (berbasis Falcon): tanda tangan lattice dengan ukuran lebih kecil, sedang dalam proses standardisasi sebagai FIPS 206.
- **HQC**: dipilih NIST pada tahun 2025 sebagai KEM cadangan berbasis kode (code-based), agar tidak semua bergantung pada lattice.
- Standar stateful hash-based signature (LMS dan XMSS) sudah ada untuk kasus tertentu seperti penandatanganan firmware.
- NIST juga menerbitkan rencana transisi: algoritma klasik dengan keamanan 112 bit (misalnya RSA-2048) direncanakan **ditinggalkan (deprecated) setelah 2030** dan **dilarang setelah 2035**. Rencana ini disampaikan dalam bentuk draf (NIST IR 8547), jadi pastikan Anda memeriksa versi finalnya.
- Pedoman NSA (CNSA 2.0) untuk sistem keamanan nasional AS juga menargetkan transisi bertahap menuju algoritma pasca-kuantum dengan batas akhir sekitar 2035.

## 11.4 KEM: Konsep Baru yang Perlu Dipahami

Berbeda dengan Diffie-Hellman yang bersifat interaktif, ML-KEM memakai antarmuka **KEM (Key Encapsulation Mechanism)** dengan tiga operasi:

```
KeyGen()           -> (kunci_publik, kunci_privat)
Encaps(kunci_publik) -> (ciphertext, rahasia_bersama)
Decaps(kunci_privat, ciphertext) -> rahasia_bersama
```

Alur: penerima mengirim kunci publik; pengirim menjalankan Encaps dan mengirim ciphertext; penerima menjalankan Decaps. Keduanya kini memiliki rahasia bersama yang kemudian dimasukkan ke KDF seperti pada Bab 6.

## 11.5 Basis Matematika: Sekilas Lattice

Lattice adalah kisi titik teratur dalam ruang berdimensi tinggi. Masalah seperti **Learning With Errors (LWE)** meminta kita memulihkan rahasia dari persamaan linear yang sengaja ditambahi derau (noise) kecil. Tanpa derau, masalahnya mudah (eliminasi Gauss); dengan derau pada dimensi tinggi, tidak ada algoritma efisien yang diketahui, baik klasik maupun kuantum. ML-KEM dan ML-DSA memakai varian terstruktur (Module-LWE) agar kunci lebih kecil dan operasi lebih cepat.

## 11.6 Perbandingan Ukuran

Algoritma pasca-kuantum umumnya memiliki kunci dan tanda tangan **jauh lebih besar** daripada ECC.

|Skema|Kunci Publik|Ciphertext / Tanda Tangan|
|---|---|---|
|X25519|32 byte|(32 byte kunci publik pihak lain)|
|**ML-KEM-768**|1.184 byte|1.088 byte|
|Ed25519|32 byte|64 byte|
|**ML-DSA-65**|1.952 byte|3.309 byte|
|SLH-DSA (varian umum)|sangat kecil (32 sampai 64 byte)|sekitar 8 KB hingga puluhan KB|

Dampak praktis: handshake TLS menjadi lebih besar, rantai sertifikat bisa membengkak, dan perangkat IoT dengan memori terbatas membutuhkan perhatian khusus. Ini sebabnya migrasi tanda tangan dan sertifikat lebih rumit daripada migrasi pertukaran kunci.

## 11.7 Pendekatan Hybrid

Karena algoritma pasca-kuantum relatif baru (belum seusia RSA atau ECC dalam hal kajian), praktik yang dianjurkan adalah **hybrid**: menjalankan algoritma klasik dan pasca-kuantum **bersamaan**, lalu menggabungkan rahasianya. Keamanan hasil akhir bertahan selama **salah satu** dari keduanya masih kuat.

Contoh nyata yang sudah dipakai luas:

- **X25519MLKEM768** pada TLS 1.3: browser besar (Chrome, Firefox, Edge, Safari pada versi terbaru) dan layanan seperti Cloudflare telah mengaktifkannya sehingga sebagian besar lalu lintas HTTPS modern sudah terlindung dari harvest-now-decrypt-later.
- **mlkem768x25519-sha256** pada OpenSSH, sudah default pada rilis terbaru.
- **PQXDH** pada Signal, dan pengembangan ratchet pasca-kuantum.
- OpenSSL 3.5 ke atas mendukung ML-KEM, ML-DSA, dan SLH-DSA.

## 11.8 Rencana Migrasi untuk Organisasi

Langkah praktis yang dapat Anda terapkan sebagai engineer:

1. **Inventarisasi** seluruh pemakaian kriptografi kunci publik (TLS, VPN, SSH, tanda tangan kode, sertifikat, database, perangkat IoT).
2. **Klasifikasi data** berdasarkan masa sensitivitas. Prioritaskan yang harus tetap rahasia lebih dari 10 tahun.
3. **Pastikan crypto agility** pada arsitektur sistem baru.
4. **Aktifkan hybrid key exchange** di layanan yang mendukungnya (TLS, SSH, VPN).
5. **Uji dampak ukuran** pada jaringan, firmware, dan perangkat kecil.
6. **Pantau standar dan regulasi** yang terus berkembang.
7. Untuk kunci simetris dan hash, gunakan AES-256 dan SHA-384/SHA-512 pada sistem berumur panjang.

Perlu dibedakan: **PQC (Post-Quantum Cryptography)** adalah algoritma klasik yang berjalan di komputer biasa tetapi tahan terhadap serangan kuantum, sedangkan **QKD (Quantum Key Distribution)** adalah teknik berbasis fisika kuantum yang memerlukan perangkat keras khusus. Mayoritas lembaga keamanan siber merekomendasikan PQC sebagai jalur migrasi utama.

## 11.9 Contoh Kode (Opsional)

Dukungan PQC di library Python masih berkembang cepat. Karena API berubah-ubah, periksa dokumentasi library terkini (misalnya `liboqs-python`, atau fitur PQC pada OpenSSL 3.5 ke atas). Anda dapat mencoba lewat OpenSSL dari baris perintah:

```bash
# Memeriksa dukungan ML-KEM pada OpenSSL Anda (butuh OpenSSL 3.5 atau lebih baru)
openssl list -kem-algorithms

# Membuat pasangan kunci ML-DSA-65
openssl genpkey -algorithm ML-DSA-65 -out mldsa65.pem
openssl pkey -in mldsa65.pem -pubout -out mldsa65.pub
```

## Ringkasan Bab 11

- Shor mematahkan RSA, DH, dan ECC; Grover hanya mengurangi keamanan simetris (solusi: AES-256).
- "Harvest now, decrypt later" membuat migrasi kerahasiaan mendesak.
- Standar utama: ML-KEM (FIPS 203), ML-DSA (FIPS 204), SLH-DSA (FIPS 205); FN-DSA dan HQC menyusul.
- Gunakan pendekatan hybrid dan rancang crypto agility.
- Tanda tangan dan sertifikat pasca-kuantum lebih besar sehingga migrasinya lebih kompleks.

## Latihan Bab 11

1. Jelaskan mengapa AES-256 dianggap tahan kuantum, sedangkan RSA-4096 tidak.
2. Hitung selisih ukuran kunci publik + ciphertext antara X25519 dan ML-KEM-768.
3. Apa alasan pendekatan hybrid dianjurkan dibanding langsung beralih penuh?
4. Susun daftar sistem di kampus Anda yang memakai kriptografi kunci publik dan prioritaskan migrasinya.

---

# Bab 12. Topik Lanjutan

Bab ini memberi gambaran umum topik yang akan Anda temui saat melanjutkan studi. Tidak perlu dikuasai penuh pada tahap pemula.

## 12.1 Zero-Knowledge Proof (ZKP)

Bukti tanpa pengungkapan pengetahuan memungkinkan satu pihak (prover) meyakinkan pihak lain (verifier) bahwa suatu pernyataan benar **tanpa membocorkan informasi apa pun selain kebenaran pernyataan itu**.

Analogi: membuktikan Anda tahu jalan keluar sebuah labirin tanpa menunjukkan jalannya.

Penerapan: verifikasi identitas yang menjaga privasi (misalnya membuktikan usia di atas 18 tanpa menunjukkan tanggal lahir), transaksi privat, dan skalabilitas blockchain (zk-rollup). Contoh sistem: zk-SNARK dan zk-STARK. zk-STARK berbasis hash sehingga umumnya dianggap tahan kuantum.

## 12.2 Homomorphic Encryption (HE)

Enkripsi homomorfik memungkinkan komputasi **langsung pada data terenkripsi**; hasilnya, ketika didekripsi, sama dengan hasil komputasi pada data asli. Cocok untuk analitik pada data sensitif di cloud (misalnya data medis). Kelemahan utama: overhead komputasi masih besar, walau terus membaik. Skema modern (BFV, BGV, CKKS, TFHE) berbasis lattice sehingga tahan kuantum.

## 12.3 Secure Multi-Party Computation (MPC)

Beberapa pihak menghitung bersama suatu fungsi atas input rahasia masing-masing tanpa saling membuka input. Contoh: beberapa bank menghitung statistik penipuan gabungan tanpa berbagi data nasabah. MPC juga dipakai untuk menyimpan kunci kripto secara terdistribusi (threshold signature).

## 12.4 Kriptografi pada Blockchain

Blockchain memakai hash (pohon Merkle, proof of work), tanda tangan digital (kepemilikan aset), dan semakin banyak ZKP. Karena kunci tanda tangan umumnya berbasis ECC, blockchain termasuk sistem yang perlu merencanakan migrasi pasca-kuantum.

## 12.5 Confidential Computing

Menggunakan Trusted Execution Environment (TEE) pada prosesor untuk melindungi data **saat diproses** (in use), melengkapi enkripsi saat disimpan (at rest) dan saat dikirim (in transit).

## 12.6 Format-Preserving dan Searchable Encryption

Skema khusus yang menjaga format data (misalnya nomor kartu tetap 16 digit setelah dienkripsi) atau memungkinkan pencarian pada data terenkripsi dengan kebocoran informasi terbatas. Berguna di sistem legacy dan basis data, tetapi desainnya rumit dan penuh pertukaran keamanan.

## 12.7 Kriptografi Ringan (Lightweight Cryptography)

Perangkat IoT dengan sumber daya terbatas membutuhkan algoritma hemat memori dan daya. NIST telah memilih keluarga **Ascon** sebagai standar kriptografi ringan untuk enkripsi terautentikasi dan hashing.

## 12.8 Differential Privacy dan Privasi Data

Walaupun bukan kriptografi murni, differential privacy menambah derau terkontrol pada hasil analisis agar data individu tidak dapat disimpulkan. Sering dipadukan dengan kriptografi untuk perlindungan data pribadi.

## Latihan Bab 12

1. Berikan satu contoh nyata penggunaan ZKP yang melindungi privasi.
2. Apa perbedaan data "at rest", "in transit", dan "in use"? Teknologi apa melindungi masing-masing?
3. Mengapa homomorphic encryption belum dipakai untuk semua kasus?

---

# Bab 13. Serangan Umum dan Kesalahan Implementasi

## Tujuan Pembelajaran

- Mengenali kategori serangan terhadap kriptografi.
- Memahami bahwa kegagalan biasanya terjadi di implementasi, bukan di matematika.
- Memiliki daftar periksa praktik aman.

## 13.1 Serangan terhadap Matematika dan Parameter

- **Brute force**: mencoba semua kunci. Ditangkal dengan ruang kunci besar.
- **Serangan kamus dan rainbow table**: pada password lemah. Ditangkal dengan salt dan hash password lambat.
- **Birthday attack**: mencari tabrakan hash lebih cepat daripada pre-image; karena itu hash 256 bit hanya memberi keamanan tabrakan sekitar 128 bit.
- **Kriptanalisis diferensial dan linear**: serangan statistik pada cipher blok; cipher modern dirancang tahan terhadapnya.
- **Parameter lemah**: kunci RSA terlalu pendek, kurva tidak aman, atau bilangan prima yang dihasilkan dengan RNG buruk.

## 13.2 Serangan Protokol

- **Man-in-the-middle (MITM)**: penyerang berada di tengah jalur komunikasi. Ditangkal dengan autentikasi (sertifikat, tanda tangan).
- **Replay attack**: pesan sah direkam dan dikirim ulang. Ditangkal dengan nonce, timestamp, atau counter.
- **Downgrade attack**: memaksa kedua pihak memakai versi atau algoritma lama yang lemah. Ditangkal dengan menonaktifkan versi lama dan perlindungan downgrade bawaan TLS 1.3.
- **Phishing**: menipu pengguna, bukan memecahkan kriptografi. Passkey membantu mengurangi risikonya.

## 13.3 Serangan Implementasi

- **Timing attack**: waktu eksekusi membocorkan informasi rahasia. Gunakan operasi waktu konstan (misalnya `hmac.compare_digest`).
- **Side-channel**: konsumsi daya, radiasi elektromagnetik, cache, suara. Perlu implementasi khusus dan perangkat keras terlindung.
- **Padding oracle**: server yang membedakan galat padding membocorkan plaintext pada mode CBC. Gunakan AEAD, hindari pesan galat yang berbeda-beda.
- **Fault injection**: menimbulkan galat perangkat keras (voltase, laser) untuk mengekstrak kunci.
- **Bug perangkat lunak**: contoh terkenal adalah Heartbleed (2014) pada OpenSSL, buffer over-read yang membocorkan memori server termasuk kunci privat. Pelajaran: kriptografi yang benar tidak menolong jika perangkat lunaknya rapuh.

## 13.4 Kesalahan Umum Pengembang

|Kesalahan|Akibat|Perbaikan|
|---|---|---|
|Membuat algoritma sendiri|Hampir pasti lemah|Pakai standar dan library teruji|
|Memakai ECB|Pola data bocor|Pakai AEAD (GCM atau ChaCha20-Poly1305)|
|Mengulang nonce|Kerahasiaan dan integritas runtuh|Nonce unik per pesan atau SIV|
|Memakai `random` untuk kunci|Kunci dapat ditebak|Pakai `os.urandom` atau `secrets`|
|Menyimpan password dengan SHA-256 polos atau MD5|Mudah dipecahkan saat database bocor|Argon2id, scrypt, bcrypt|
|Hardcode kunci di source code|Kunci bocor lewat repositori|Pakai secret manager atau KMS|
|Menonaktifkan verifikasi sertifikat (`verify=False`)|MITM mudah|Selalu verifikasi sertifikat|
|Membandingkan MAC dengan `==`|Timing attack|`hmac.compare_digest`|
|Enkripsi tanpa autentikasi|Data bisa dimanipulasi|AEAD|
|Satu kunci untuk banyak tujuan|Serangan lintas protokol|Pisahkan kunci per fungsi (HKDF dengan `info` berbeda)|
|Mengabaikan migrasi pasca-kuantum|Risiko harvest-now-decrypt-later|Mulai inventaris dan hybrid|

## 13.5 Daftar Periksa Praktik Aman

- Gunakan library populer dan terawat: `cryptography` (Python), libsodium, Tink, atau pustaka bawaan platform.
- Pilih algoritma standar: AES-256-GCM atau ChaCha20-Poly1305, SHA-256/SHA-3, Ed25519 atau ECDSA/RSA-PSS, X25519/ECDH, Argon2id.
- Gunakan TLS 1.3 (minimal TLS 1.2 dengan konfigurasi aman) dan otomatiskan sertifikat.
- Bangkitkan semua acak dengan CSPRNG.
- Kelola kunci dengan KMS atau HSM, rotasi berkala, dan jangan simpan di kode.
- Rencanakan crypto agility dan migrasi pasca-kuantum.
- Perbarui dependensi secara rutin, dan lakukan audit atau penetration test.

## Latihan Bab 13

1. Cari tahu cara kerja Heartbleed secara garis besar. Mengapa tidak ada hubungannya dengan kelemahan algoritma?
2. Tinjau sebuah potongan kode (cari contoh di internet) yang memakai `random` untuk token dan perbaiki.
3. Mengapa pesan galat yang berbeda untuk "padding salah" dan "MAC salah" berbahaya?

---

# Bab 14. Kriptografi dalam Konteks Indonesia

Bab ini memberi gambaran umum. Peraturan dapat berubah, sehingga selalu rujuk teks resmi dan konsultasikan ke ahli hukum untuk keputusan formal.

## 14.1 Lembaga dan Istilah

- **BSSN (Badan Siber dan Sandi Negara)** adalah lembaga pemerintah yang bertugas di bidang keamanan siber dan persandian. Kata "sandi" adalah padanan Indonesia untuk kriptografi.
- **BSrE (Balai Sertifikasi Elektronik)** berada di bawah BSSN dan menyelenggarakan sertifikasi elektronik untuk instansi pemerintah dan kebutuhan tertentu.
- **PSrE (Penyelenggara Sertifikasi Elektronik)** adalah penyelenggara layanan sertifikat elektronik yang diakui di Indonesia; terdapat PSrE swasta yang tersertifikasi.

## 14.2 Tanda Tangan Elektronik

Regulasi Indonesia (antara lain UU ITE beserta perubahannya dan PP No. 71 Tahun 2019 tentang Penyelenggaraan Sistem dan Transaksi Elektronik) membedakan tanda tangan elektronik **tersertifikasi** (dibuat dengan layanan PSrE dan memiliki kekuatan hukum yang kuat) dan **tidak tersertifikasi**. Secara teknis, tanda tangan tersertifikasi dibangun di atas konsep yang sama dengan Bab 7 dan 8: tanda tangan digital, sertifikat X.509, dan PKI.

## 14.3 Pelindungan Data Pribadi

UU No. 27 Tahun 2022 tentang Pelindungan Data Pribadi (UU PDP) mewajibkan pengendali dan prosesor data pribadi menerapkan langkah keamanan yang memadai. Walaupun undang-undang tidak menunjuk algoritma tertentu, praktik seperti enkripsi data saat disimpan dan dikirim, pengelolaan kunci, kontrol akses, serta pencatatan (log) merupakan langkah teknis yang lazim dipakai untuk memenuhi kewajiban tersebut. Penting dipahami: kebocoran data terenkripsi dengan kunci yang dikelola baik berdampak jauh lebih kecil dibanding kebocoran data mentah.

## 14.4 Peluang Karier

Bidang yang relevan: security engineer, application security, kriptografer terapan, pengembang sistem pembayaran digital, DevSecOps, penguji penetrasi, peneliti PQC, dan auditor keamanan. Sertifikasi dan komunitas lokal serta kompetisi CTF (Capture The Flag) adalah jalur belajar yang baik.

## Latihan Bab 14

1. Cari dan baca ringkasan PP No. 71 Tahun 2019 terkait sertifikat elektronik dan tuliskan tiga poin utama dengan bahasa Anda sendiri.
2. Identifikasi data pribadi apa saja yang diproses sebuah aplikasi kampus, dan rancang kontrol kriptografi untuk masing-masingnya.

---

# Bab 15. Praktikum Terpadu

## Tujuan

Menyatukan seluruh konsep menjadi aplikasi kecil: **brankas pesan** dengan pertukaran kunci X25519, penurunan kunci HKDF, enkripsi AES-GCM, dan tanda tangan Ed25519.

## 15.1 Skenario

Alice ingin mengirim pesan rahasia ke Bob.

1. Alice dan Bob membuat pasangan kunci X25519 (untuk kerahasiaan) dan Ed25519 (untuk identitas).
2. Alice menurunkan kunci sesi dari X25519 dan kunci publik Bob.
3. Alice mengenkripsi pesan dengan AES-GCM.
4. Alice menandatangani paket (kunci publik efemeral + nonce + ciphertext) dengan Ed25519.
5. Bob memverifikasi tanda tangan, menurunkan kunci sesi yang sama, lalu mendekripsi.

## 15.2 Kode

```python
import os
from cryptography.hazmat.primitives.asymmetric.x25519 import (
    X25519PrivateKey, X25519PublicKey)
from cryptography.hazmat.primitives.asymmetric.ed25519 import Ed25519PrivateKey
from cryptography.hazmat.primitives.ciphers.aead import AESGCM
from cryptography.hazmat.primitives.kdf.hkdf import HKDF
from cryptography.hazmat.primitives import hashes, serialization

RAW = dict(encoding=serialization.Encoding.Raw,
           format=serialization.PublicFormat.Raw)

def turunkan_kunci(rahasia: bytes) -> bytes:
    return HKDF(algorithm=hashes.SHA256(), length=32, salt=None,
                info=b"brankas-pesan v1").derive(rahasia)

# --- Persiapan kunci jangka panjang ---
bob_x_priv = X25519PrivateKey.generate()          # kunci enkripsi Bob
bob_x_pub = bob_x_priv.public_key()
alice_sign_priv = Ed25519PrivateKey.generate()    # kunci identitas Alice
alice_sign_pub = alice_sign_priv.public_key()

# --- Sisi Alice: kirim pesan ---
def kirim(pesan: bytes, bob_x_pub: X25519PublicKey):
    eph_priv = X25519PrivateKey.generate()        # kunci sementara (forward secrecy)
    eph_pub_bytes = eph_priv.public_key().public_bytes(**RAW)

    kunci = turunkan_kunci(eph_priv.exchange(bob_x_pub))
    nonce = os.urandom(12)
    ct = AESGCM(kunci).encrypt(nonce, pesan, eph_pub_bytes)

    paket = eph_pub_bytes + nonce + ct
    tanda_tangan = alice_sign_priv.sign(paket)
    return paket, tanda_tangan

# --- Sisi Bob: terima pesan ---
def terima(paket: bytes, tanda_tangan: bytes):
    alice_sign_pub.verify(tanda_tangan, paket)    # InvalidSignature jika palsu/diubah

    eph_pub_bytes, nonce, ct = paket[:32], paket[32:44], paket[44:]
    eph_pub = X25519PublicKey.from_public_bytes(eph_pub_bytes)

    kunci = turunkan_kunci(bob_x_priv.exchange(eph_pub))
    return AESGCM(kunci).decrypt(nonce, ct, eph_pub_bytes)

paket, ttd = kirim("Nilai ujian dirilis besok pagi".encode(), bob_x_pub)
print("Ukuran paket:", len(paket), "byte")
print("Bob membaca:", terima(paket, ttd).decode())
```

## 15.3 Analisis

Diskusikan:

- Properti keamanan apa yang dicapai? (kerahasiaan, integritas, autentikasi pengirim, forward secrecy terhadap kunci pengirim)
- Properti apa yang **tidak** dicapai? (misalnya Alice mengenal kunci publik Bob dengan benar? Bagaimana jika penyerang mengganti `bob_x_pub`? Perlindungan terhadap replay? Forward secrecy dari sisi Bob karena `bob_x_priv` bersifat statis?)
- Bagaimana protokol ini dapat dimodifikasi agar hybrid pasca-kuantum?

## 15.4 Tantangan Pengembangan

1. Tambahkan pencegahan replay dengan nomor urut atau timestamp yang ikut ditandatangani.
2. Ganti AES-GCM dengan ChaCha20-Poly1305.
3. Simpan kunci jangka panjang ke file terenkripsi dengan kunci turunan Argon2id dari passphrase.
4. Tambahkan kolom versi algoritma pada paket untuk mendukung crypto agility.

## 15.5 Perintah OpenSSL yang Berguna

```bash
# Hash file
openssl dgst -sha256 berkas.txt

# Membuat kunci acak 32 byte dalam heksadesimal
openssl rand -hex 32

# Enkripsi file dengan AES-256-CBC dan KDF PBKDF2 (untuk latihan; desain baru gunakan AEAD)
openssl enc -aes-256-cbc -pbkdf2 -salt -in berkas.txt -out berkas.enc

# Membuat sertifikat self-signed untuk uji lokal
openssl req -x509 -newkey ed25519 -nodes -keyout kunci.pem -out sert.pem \
  -days 30 -subj "/CN=localhost"

# Melihat isi sertifikat
openssl x509 -in sert.pem -noout -text
```

---

# Bab 16. Peta Belajar Selanjutnya

## 16.1 Jalur Belajar yang Disarankan

Tahap 1 (dasar, 1 sampai 2 bulan):

- Selesaikan buku ini, termasuk seluruh latihan dan praktikum.
- Latihan interaktif: tantangan Cryptopals (cryptopals.com) untuk memahami serangan nyata pada implementasi.

Tahap 2 (menengah, 3 sampai 6 bulan):

- Teori bilangan, aljabar abstrak dasar, dan probabilitas.
- Baca dokumen RFC TLS 1.3 (RFC 8446), serta pelajari cara kerja Signal dan WireGuard.
- Ikut kompetisi CTF kategori crypto.

Tahap 3 (lanjut):

- Bukti keamanan (provable security), model keamanan formal (IND-CPA, IND-CCA, EUF-CMA).
- Kriptografi pasca-kuantum: lattice, kode koreksi galat, isogeni, dan tanda tangan berbasis hash.
- Topik lanjutan: ZKP, MPC, FHE.

## 16.2 Buku dan Sumber Belajar yang Disarankan

- Jean-Philippe Aumasson, _Serious Cryptography_ (edisi kedua tersedia).
- Jonathan Katz dan Yehuda Lindell, _Introduction to Modern Cryptography_.
- Dan Boneh dan Victor Shoup, _A Graduate Course in Applied Cryptography_ (gratis daring).
- Bruce Schneier, _Applied Cryptography_ (klasik, sebagian sudah usang) dan _Cryptography Engineering_.
- Kuliah daring Cryptography oleh Dan Boneh (Stanford, tersedia di Coursera).
- Dokumentasi library `cryptography` (cryptography.io) dan libsodium (doc.libsodium.org).

## 16.3 Pantau Perkembangan Terbaru

- NIST Computer Security Resource Center: csrc.nist.gov (standar PQC, pedoman).
- IETF: datatracker.ietf.org (RFC dan draf protokol).
- IACR ePrint Archive: eprint.iacr.org (makalah riset kriptografi).
- CA/Browser Forum: cabforum.org (kebijakan sertifikat TLS).
- BSSN: bssn.go.id (kebijakan siber dan sandi nasional).

---

# Glosarium

|Istilah|Penjelasan|
|---|---|
|AEAD|Authenticated Encryption with Associated Data; enkripsi yang sekaligus menjamin kerahasiaan dan integritas|
|AES|Advanced Encryption Standard; cipher blok standar dunia|
|Asimetris|Kriptografi dengan pasangan kunci publik dan privat|
|Birthday attack|Serangan yang memanfaatkan paradoks ulang tahun untuk menemukan tabrakan hash|
|Cipher|Algoritma enkripsi dan dekripsi|
|Ciphertext|Data terenkripsi|
|Collision|Dua input berbeda dengan hash yang sama|
|CSPRNG|Pembangkit bilangan acak semu yang aman secara kriptografis|
|Crypto agility|Kemampuan mengganti algoritma kriptografi dengan mudah|
|Digest|Keluaran fungsi hash|
|ECC|Elliptic Curve Cryptography; kriptografi kurva eliptik|
|Entropi|Ukuran ketidakpastian atau keacakan|
|Forward secrecy|Kompromi kunci di masa depan tidak membuka komunikasi masa lalu|
|Harvest now, decrypt later|Merekam data terenkripsi sekarang untuk didekripsi saat komputer kuantum tersedia|
|HKDF|HMAC-based Key Derivation Function|
|HMAC|MAC yang dibangun dari fungsi hash|
|HSM|Hardware Security Module; perangkat keras penyimpan kunci|
|IV|Initialization Vector; nilai awal pada beberapa mode cipher blok|
|KDF|Key Derivation Function; fungsi penurun kunci|
|KEM|Key Encapsulation Mechanism; antarmuka pertukaran kunci pasca-kuantum|
|Kunci privat|Kunci rahasia pemilik pada pasangan kunci asimetris|
|Kunci publik|Kunci yang boleh disebarkan|
|MAC|Message Authentication Code; kode autentikasi pesan berkunci|
|MITM|Man-in-the-middle; penyerang yang berada di antara dua pihak|
|ML-KEM|Standar NIST pertukaran kunci pasca-kuantum (FIPS 203)|
|ML-DSA|Standar NIST tanda tangan pasca-kuantum berbasis lattice (FIPS 204)|
|Nonce|Nilai yang hanya dipakai sekali untuk kunci tertentu|
|Non-repudiation|Pelaku tidak dapat menyangkal tindakannya|
|PKI|Public Key Infrastructure; infrastruktur kunci publik|
|Plaintext|Data asli yang belum dienkripsi|
|PQC|Post-Quantum Cryptography; kriptografi tahan komputer kuantum|
|Salt|Nilai acak unik yang ditambahkan sebelum hashing password|
|SLH-DSA|Standar NIST tanda tangan pasca-kuantum berbasis hash (FIPS 205)|
|Side-channel|Kebocoran informasi lewat waktu, daya, atau radiasi perangkat|
|Simetris|Kriptografi dengan satu kunci yang sama untuk enkripsi dan dekripsi|
|TLS|Transport Layer Security; protokol pengaman komunikasi jaringan|
|ZKP|Zero-Knowledge Proof; bukti tanpa pengungkapan pengetahuan|

---

# Referensi

1. NIST. FIPS 203, Module-Lattice-Based Key-Encapsulation Mechanism Standard (ML-KEM). 2024.
2. NIST. FIPS 204, Module-Lattice-Based Digital Signature Standard (ML-DSA). 2024.
3. NIST. FIPS 205, Stateless Hash-Based Digital Signature Standard (SLH-DSA). 2024.
4. NIST. FIPS 197, Advanced Encryption Standard (AES). 2001.
5. NIST. FIPS 180-4, Secure Hash Standard; FIPS 202, SHA-3 Standard.
6. NIST. NIST SP 800-38D, Recommendation for GCM and GMAC.
7. NIST. NIST IR 8547 (draf), Transition to Post-Quantum Cryptography Standards.
8. IETF. RFC 8446, The Transport Layer Security (TLS) Protocol Version 1.3.
9. IETF. RFC 5869, HMAC-based Extract-and-Expand Key Derivation Function (HKDF).
10. IETF. RFC 7748, Elliptic Curves for Security (X25519, X448); RFC 8032, Edwards-Curve Digital Signature Algorithm (EdDSA).
11. IETF. RFC 9106, Argon2 Memory-Hard Function for Password Hashing.
12. IETF. RFC 8555, Automatic Certificate Management Environment (ACME).
13. CA/Browser Forum. Baseline Requirements for TLS Server Certificates (ballot SC-081 tentang masa berlaku sertifikat).
14. Katz, J. dan Lindell, Y. Introduction to Modern Cryptography. CRC Press.
15. Aumasson, J.-P. Serious Cryptography. No Starch Press.
16. Boneh, D. dan Shoup, V. A Graduate Course in Applied Cryptography.
17. Republik Indonesia. UU No. 27 Tahun 2022 tentang Pelindungan Data Pribadi; PP No. 71 Tahun 2019 tentang Penyelenggaraan Sistem dan Transaksi Elektronik.

---

Akhir buku. Selamat belajar, dan ingat: gunakan kriptografi yang sudah teruji, kelola kunci dengan disiplin, dan selalu perbarui pengetahuan Anda karena bidang ini terus berkembang.