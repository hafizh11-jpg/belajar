# Network Security: Buku Pembelajaran untuk Pemula

Edisi 2026/2027 dan seterusnya

Program Studi: Teknik Informatika Bahasa: Indonesia Level: Pemula hingga menengah awal

---

## Kata Pengantar

Hampir semua hal yang kita lakukan hari ini bergantung pada jaringan: belajar daring, bekerja jarak jauh, membayar lewat aplikasi, memakai layanan cloud, hingga mengendalikan perangkat rumah pintar. Setiap koneksi yang kita buat adalah pintu yang bisa dimanfaatkan orang yang tidak berhak. Network Security (keamanan jaringan) adalah ilmu dan praktik untuk menjaga agar pintu-pintu itu hanya bisa dilewati oleh pihak yang berwenang, dengan cara yang aman.

Buku ini ditulis untuk Anda yang baru mulai. Anda tidak perlu sudah mahir jaringan atau pemrograman. Setiap istilah teknis dijelaskan dari dasar, disertai analogi, contoh, dan latihan. Di akhir buku Anda akan memiliki kerangka berpikir yang utuh: memahami cara kerja jaringan, jenis ancaman, cara bertahan, cara mendeteksi serangan, dan cara merespons ketika kejadian buruk terjadi.

Buku ini juga memperhatikan perkembangan yang relevan untuk tahun 2026, 2027, dan seterusnya, seperti migrasi ke TLS 1.3, kriptografi pasca-kuantum, passkeys, Zero Trust, dan penggunaan kecerdasan buatan oleh penyerang maupun pembela.

## Cara Menggunakan Buku Ini

1. Baca bab secara berurutan. Bab awal adalah fondasi bagi bab berikutnya.
2. Setiap bab berisi: tujuan pembelajaran, materi, ringkasan, dan latihan soal.
3. Kunci jawaban singkat ada di bagian akhir buku. Coba jawab sendiri terlebih dahulu.
4. Lakukan praktik di lingkungan laboratorium milik sendiri (mesin virtual atau jaringan rumah Anda sendiri). Petunjuknya ada di Bab 16.
5. Jika menemukan istilah asing, cek Glosarium di bagian akhir.

### Perlengkapan yang Disarankan untuk Praktik

|Kebutuhan|Rekomendasi|Keterangan|
|---|---|---|
|Hipervisor|VirtualBox atau VMware Workstation Player|Gratis untuk penggunaan pribadi|
|Sistem operasi lab|Ubuntu Server atau Debian|Sebagai target dan server latihan|
|Sistem operasi analis|Kali Linux atau Ubuntu Desktop|Alat analisis jaringan|
|Alat analisis paket|Wireshark, tcpdump|Melihat isi lalu lintas jaringan|
|Alat pemindai|Nmap|Hanya untuk jaringan milik sendiri|
|IDS|Suricata|Latihan deteksi serangan|
|RAM minimal|8 GB (disarankan 16 GB)|Untuk menjalankan 2 sampai 3 VM sekaligus|

## Peringatan Etika dan Hukum

Pengetahuan dalam buku ini bersifat ganda: teknik yang dipakai untuk bertahan juga dapat disalahgunakan untuk menyerang. Karena itu, patuhi aturan berikut.

- Lakukan percobaan hanya pada sistem milik Anda sendiri atau sistem yang Anda punya izin tertulis untuk mengujinya.
- Mengakses, memindai secara agresif, mengganggu, atau merusak sistem milik orang lain tanpa izin dapat dikenai sanksi pidana. Di Indonesia, ketentuan terkait ada pada Undang-Undang Informasi dan Transaksi Elektronik (UU ITE) beserta perubahannya, serta Undang-Undang Pelindungan Data Pribadi (UU PDP). Periksa selalu versi terbaru peraturan tersebut.
- Jika menemukan kerentanan pada sistem pihak lain, laporkan secara bertanggung jawab (responsible disclosure) kepada pemilik sistem atau kepada lembaga seperti BSSN, dan jangan mengeksploitasinya.
- Buku ini bukan nasihat hukum. Untuk urusan hukum, konsultasikan dengan ahli hukum.

---

## Daftar Isi

- [Bab 1: Pengantar Keamanan Jaringan](#bab-1-pengantar-keamanan-jaringan)
- [Bab 2: Dasar Jaringan untuk Keamanan](#bab-2-dasar-jaringan-untuk-keamanan)
- [Bab 3: Ancaman dan Serangan Jaringan](#bab-3-ancaman-dan-serangan-jaringan)
- [Bab 4: Kriptografi Dasar](#bab-4-kriptografi-dasar)
- [Bab 5: Autentikasi dan Kontrol Akses](#bab-5-autentikasi-dan-kontrol-akses)
- [Bab 6: Protokol Komunikasi Aman](#bab-6-protokol-komunikasi-aman)
- [Bab 7: Firewall dan Segmentasi Jaringan](#bab-7-firewall-dan-segmentasi-jaringan)
- [Bab 8: IDS, IPS, Logging, dan Monitoring](#bab-8-ids-ips-logging-dan-monitoring)
- [Bab 9: VPN, Zero Trust, dan SASE](#bab-9-vpn-zero-trust-dan-sase)
- [Bab 10: Keamanan Jaringan Nirkabel (Wi-Fi)](#bab-10-keamanan-jaringan-nirkabel-wi-fi)
- [Bab 11: Keamanan Cloud, Container, dan IoT](#bab-11-keamanan-cloud-container-dan-iot)
- [Bab 12: Penilaian Kerentanan dan Uji Penetrasi](#bab-12-penilaian-kerentanan-dan-uji-penetrasi)
- [Bab 13: Respons Insiden dan Forensik Jaringan](#bab-13-respons-insiden-dan-forensik-jaringan)
- [Bab 14: Tata Kelola, Manajemen Risiko, dan Standar](#bab-14-tata-kelola-manajemen-risiko-dan-standar)
- [Bab 15: Tren 2026 dan Seterusnya serta Jalur Karier](#bab-15-tren-2026-dan-seterusnya-serta-jalur-karier)
- [Bab 16: Lab Praktik Terpandu](#bab-16-lab-praktik-terpandu)
- [Kunci Jawaban Singkat](#kunci-jawaban-singkat)
- [Glosarium](#glosarium)
- [Rujukan dan Bacaan Lanjutan](#rujukan-dan-bacaan-lanjutan)

---

## Bab 1: Pengantar Keamanan Jaringan

### Tujuan Pembelajaran

Setelah mempelajari bab ini, Anda mampu:

- Menjelaskan apa itu keamanan jaringan dan mengapa penting.
- Menjelaskan tiga tujuan utama keamanan (CIA) dan konsep pendukungnya.
- Membedakan istilah aset, ancaman, kerentanan, risiko, dan kontrol.
- Menjelaskan prinsip desain keamanan seperti defense in depth dan least privilege.

### 1.1 Apa Itu Keamanan Jaringan?

Keamanan jaringan adalah kumpulan kebijakan, proses, dan teknologi yang bertujuan melindungi jaringan komputer beserta data yang melewatinya dari akses tanpa izin, penyalahgunaan, gangguan, atau kerusakan.

Analogi sederhana: jaringan adalah jalan raya, data adalah kendaraan dan muatannya. Keamanan jaringan mencakup pagar dan gerbang (firewall), petugas pemeriksa identitas (autentikasi), kendaraan lapis baja untuk muatan berharga (enkripsi), kamera pengawas (monitoring), dan prosedur darurat ketika terjadi kecelakaan (respons insiden).

### 1.2 Segitiga CIA

Tiga tujuan utama keamanan informasi dikenal sebagai CIA triad.

|Tujuan|Arti|Contoh pelanggaran|Contoh perlindungan|
|---|---|---|---|
|Confidentiality (kerahasiaan)|Hanya pihak berwenang yang dapat membaca data|Penyerang menyadap kata sandi di Wi-Fi publik|Enkripsi (TLS, VPN), kontrol akses|
|Integrity (integritas)|Data tidak berubah tanpa sepengetahuan pemiliknya|Penyerang mengubah nominal transfer di tengah jalan|Hash, tanda tangan digital, HMAC|
|Availability (ketersediaan)|Layanan dan data dapat diakses saat dibutuhkan|Serangan DDoS membuat situs tidak bisa dibuka|Redundansi, mitigasi DDoS, backup|

Ketiganya sering saling tarik-menarik. Misalnya, sistem yang sangat ketat (kerahasiaan tinggi) bisa menyulitkan pengguna sah (ketersediaan menurun). Tugas praktisi keamanan adalah mencari keseimbangan sesuai kebutuhan bisnis.

### 1.3 Konsep Pendukung: AAA dan Non-Repudiation

- Authentication (autentikasi): membuktikan identitas. Contoh: login dengan kata sandi dan kode OTP.
- Authorization (otorisasi): menentukan apa yang boleh dilakukan setelah identitas terbukti. Contoh: mahasiswa boleh melihat nilai sendiri, dosen boleh mengisi nilai.
- Accounting (pencatatan): merekam siapa melakukan apa dan kapan. Contoh: log login dan log perubahan konfigurasi.
- Non-repudiation (nirsangkal): pelaku tidak dapat menyangkal perbuatannya. Biasanya dicapai dengan tanda tangan digital dan log yang tidak dapat diubah.

### 1.4 Istilah Penting: Aset, Ancaman, Kerentanan, Risiko

|Istilah|Definisi|Contoh|
|---|---|---|
|Aset|Sesuatu yang bernilai dan perlu dilindungi|Database pelanggan, server web, reputasi perusahaan|
|Ancaman (threat)|Sesuatu yang berpotensi menimbulkan kerugian|Peretas, malware, bencana alam, kelalaian staf|
|Kerentanan (vulnerability)|Kelemahan yang dapat dimanfaatkan ancaman|Perangkat lunak belum di-update, kata sandi default|
|Eksploit|Cara atau kode yang memanfaatkan kerentanan|Skrip yang memanfaatkan celah pada layanan|
|Risiko|Kemungkinan terjadinya kerugian akibat ancaman yang memanfaatkan kerentanan|Peluang data bocor dikali dampak kebocoran|
|Kontrol (countermeasure)|Tindakan untuk mengurangi risiko|Patch, firewall, pelatihan kesadaran keamanan|

Rumus konseptual yang sering dipakai:

```
Risiko = Kemungkinan (likelihood) x Dampak (impact)
```

Rumus ini bukan perhitungan matematis ketat, melainkan cara berpikir untuk menentukan prioritas. Risiko yang kemungkinannya tinggi dan dampaknya besar harus ditangani lebih dulu.

### 1.5 Jenis Kontrol Keamanan

Kontrol dapat dikelompokkan berdasarkan sifat dan fungsinya.

Berdasarkan sifat:

- Administratif: kebijakan, prosedur, pelatihan.
- Teknis: firewall, enkripsi, antivirus, MFA.
- Fisik: pintu terkunci, kamera CCTV, ruang server yang dijaga.

Berdasarkan fungsi:

- Preventif: mencegah kejadian (firewall, kontrol akses).
- Detektif: mendeteksi kejadian (IDS, log, SIEM).
- Korektif: memulihkan setelah kejadian (backup, patch, rencana pemulihan).
- Deterrent dan kompensasi: menakut-nakuti atau menutupi kekurangan kontrol lain.

### 1.6 Prinsip Desain Keamanan

1. Defense in depth (pertahanan berlapis). Jangan mengandalkan satu pelindung. Jika firewall tertembus, masih ada segmentasi, autentikasi, enkripsi, dan monitoring. Analogi: kastil dengan parit, tembok, gerbang, dan penjaga.
2. Least privilege (hak akses minimum). Pengguna dan program hanya diberi hak yang benar-benar dibutuhkan.
3. Default deny. Semua dilarang kecuali yang secara eksplisit diizinkan.
4. Separation of duties (pemisahan tugas). Tidak ada satu orang yang menguasai seluruh proses kritis.
5. Fail secure. Bila sistem gagal, ia harus gagal ke kondisi aman, bukan kondisi terbuka.
6. Keep it simple. Sistem yang rumit lebih sulit diamankan dan lebih mudah salah konfigurasi.
7. Assume breach (anggap sudah ditembus). Rancang sistem agar tetap membatasi kerusakan jika penyerang berhasil masuk. Prinsip ini menjadi dasar Zero Trust (Bab 9).

### 1.7 Lanskap Ancaman Saat Ini

Beberapa pola yang konsisten terlihat dalam beberapa tahun terakhir dan diperkirakan berlanjut:

- Ransomware tetap menjadi ancaman utama bagi organisasi dari berbagai ukuran.
- Phishing dan rekayasa sosial masih menjadi pintu masuk terbanyak, kini semakin meyakinkan karena memanfaatkan kecerdasan buatan (teks, suara, dan video tiruan).
- Pencurian kredensial dan penyalahgunaan akun sah lebih umum dibanding peretasan teknis yang rumit.
- Perangkat tepi jaringan (VPN gateway, firewall, router) yang tidak ter-patch menjadi target favorit.
- Serangan rantai pasok (supply chain), yaitu menyerang vendor atau pustaka perangkat lunak yang dipakai banyak pihak.
- Pergeseran ke cloud membuat kesalahan konfigurasi (misalnya penyimpanan terbuka ke publik) menjadi sumber kebocoran besar.

### Ringkasan Bab 1

- Keamanan jaringan melindungi kerahasiaan, integritas, dan ketersediaan data serta layanan.
- Risiko adalah gabungan kemungkinan dan dampak. Kontrol dipilih untuk menurunkannya.
- Prinsip utama: pertahanan berlapis, hak akses minimum, default deny, dan asumsi bahwa pelanggaran bisa terjadi.

### Latihan Bab 1

1. Sebutkan tiga komponen CIA triad dan berikan satu contoh serangan untuk masing-masing.
2. Apa perbedaan ancaman dan kerentanan? Berikan satu contoh yang menghubungkan keduanya.
3. Sebuah toko daring menyimpan kata sandi pelanggan dalam bentuk teks biasa. Prinsip CIA mana yang terancam, dan kontrol apa yang sesuai?
4. Jelaskan dengan bahasa Anda sendiri mengapa defense in depth lebih baik daripada hanya memasang satu firewall yang sangat mahal.

---

## Bab 2: Dasar Jaringan untuk Keamanan

### Tujuan Pembelajaran

- Menjelaskan model OSI dan TCP/IP serta kaitannya dengan keamanan.
- Memahami alamat IP, port, TCP, UDP, DNS, DHCP, ARP, dan NAT.
- Memetakan protokol umum ke kelemahan yang sering dieksploitasi.

Anda tidak bisa mengamankan sesuatu yang tidak Anda pahami cara kerjanya. Bab ini menyegarkan dasar jaringan dari sudut pandang keamanan.

### 2.1 Model OSI dan TCP/IP

Model OSI membagi komunikasi jaringan menjadi tujuh lapisan. Model TCP/IP yang dipakai di internet lebih ringkas.

|Lapisan OSI|Nama|Contoh protokol/perangkat|Contoh ancaman|
|---|---|---|---|
|7|Application|HTTP, DNS, SMTP, SSH|SQL injection, phishing, DNS poisoning|
|6|Presentation|TLS (sering dianggap di sini), enkode data|Downgrade enkripsi, sertifikat palsu|
|5|Session|Sesi login, token|Session hijacking|
|4|Transport|TCP, UDP|SYN flood, port scanning|
|3|Network|IP, ICMP, router|IP spoofing, ICMP flood|
|2|Data Link|Ethernet, Wi-Fi, switch, ARP|ARP spoofing, MAC flooding|
|1|Physical|Kabel, radio, hub|Penyadapan kabel, jamming|

Pelajaran penting: serangan dan pertahanan terjadi di setiap lapisan. Firewall di lapisan 3 dan 4 tidak akan menghentikan SQL injection di lapisan 7, sehingga kita butuh kontrol berlapis.

Pemetaan ke model TCP/IP:

```
OSI 7,6,5  ->  Application (HTTP, DNS, TLS, SSH)
OSI 4      ->  Transport   (TCP, UDP)
OSI 3      ->  Internet    (IP, ICMP)
OSI 2,1    ->  Network Access / Link (Ethernet, Wi-Fi)
```

### 2.2 Alamat IP, Subnet, dan Port

Alamat IP mengidentifikasi perangkat di jaringan. IPv4 berukuran 32 bit (contoh 192.168.1.10), IPv6 berukuran 128 bit (contoh 2001:db8::1). Pada tahun 2026 keduanya hidup berdampingan, sehingga aturan keamanan harus mencakup IPv4 dan IPv6. Kesalahan umum adalah mengamankan IPv4 tetapi lupa IPv6 yang aktif secara bawaan.

Rentang alamat privat IPv4 (RFC 1918), tidak dapat dirutekan langsung di internet:

|Rentang|Notasi CIDR|
|---|---|
|10.0.0.0 sampai 10.255.255.255|10.0.0.0/8|
|172.16.0.0 sampai 172.31.255.255|172.16.0.0/12|
|192.168.0.0 sampai 192.168.255.255|192.168.0.0/16|

Notasi CIDR (misalnya /24) menyatakan berapa bit pertama yang menjadi bagian jaringan.

|CIDR|Subnet mask|Jumlah alamat|Host usable|
|---|---|---|---|
|/24|255.255.255.0|256|254|
|/26|255.255.255.192|64|62|
|/28|255.255.255.240|16|14|
|/30|255.255.255.252|4|2|

Mengapa subnet penting bagi keamanan? Karena subnet adalah dasar segmentasi: memisahkan jaringan staf, server, tamu, dan perangkat IoT sehingga serangan di satu segmen tidak otomatis menjalar ke segmen lain (Bab 7).

Port adalah angka 0 sampai 65535 yang menentukan layanan mana pada sebuah host yang dituju. Alamat IP ibarat alamat gedung, port ibarat nomor ruangan.

|Port|Protokol|Layanan|Catatan keamanan|
|---|---|---|---|
|20/21|TCP|FTP|Tidak terenkripsi. Ganti dengan SFTP atau FTPS|
|22|TCP|SSH|Aman bila dikonfigurasi benar. Sering diserang brute force|
|23|TCP|Telnet|Tidak terenkripsi. Jangan dipakai|
|25|TCP|SMTP|Pengiriman email antar server|
|53|UDP/TCP|DNS|Rawan spoofing dan amplifikasi DDoS|
|67/68|UDP|DHCP|Rawan rogue DHCP server|
|80|TCP|HTTP|Tidak terenkripsi. Arahkan ke HTTPS|
|123|UDP|NTP|Waktu harus akurat untuk log dan sertifikat|
|443|TCP/UDP|HTTPS dan HTTP/3 (QUIC)|Standar web aman|
|445|TCP|SMB|Sering dieksploitasi ransomware. Jangan buka ke internet|
|3306|TCP|MySQL|Jangan buka ke internet|
|3389|TCP|RDP|Target utama brute force dan ransomware. Lindungi dengan VPN atau ZTNA|

### 2.3 TCP, UDP, dan Three-Way Handshake

- TCP: andal, berorientasi koneksi, menjamin urutan dan pengiriman. Dipakai web, email, SSH.
- UDP: ringan, tanpa koneksi, tanpa jaminan. Dipakai DNS, video streaming, VoIP, dan QUIC (dasar HTTP/3).

Sebelum data dikirim, TCP melakukan jabat tangan tiga langkah:

```
Klien                         Server
  |  --- SYN ---------------->  |   "Saya ingin terhubung"
  |  <-- SYN + ACK -----------  |   "Baik, saya siap"
  |  --- ACK ---------------->  |   "Oke, mulai"
```

Keamanan: penyerang dapat mengirim banyak SYN tanpa menyelesaikan jabat tangan sehingga tabel koneksi server penuh. Ini disebut SYN flood. Pemindai port seperti Nmap juga memanfaatkan perilaku jabat tangan ini untuk mengetahui port mana yang terbuka (SYN diterima SYN+ACK berarti terbuka, dijawab RST berarti tertutup).

### 2.4 Protokol Pendukung dan Kelemahannya

DNS (Domain Name System) menerjemahkan nama (contoh: kampus.ac.id) menjadi alamat IP. Pada awalnya DNS tidak punya autentikasi sehingga jawaban palsu dapat disisipkan (DNS spoofing atau cache poisoning). Pertahanan: DNSSEC, DNS terenkripsi (DoH dan DoT), dan resolver tepercaya.

DHCP memberikan alamat IP otomatis. Penyerang dapat memasang rogue DHCP server yang memberi pengaturan palsu (gateway atau DNS jahat). Pertahanan: fitur DHCP snooping pada switch.

ARP (Address Resolution Protocol) memetakan alamat IP ke alamat MAC dalam satu jaringan lokal. ARP tidak punya autentikasi. Penyerang dapat mengirim balasan ARP palsu (ARP spoofing) agar lalu lintas korban lewat perangkat penyerang. Pertahanan: Dynamic ARP Inspection, segmentasi, dan enkripsi end-to-end.

ICMP dipakai untuk ping dan pesan kontrol. Dapat disalahgunakan untuk pengintaian atau flood. Jangan memblokir seluruh ICMP secara membabi buta karena beberapa jenisnya dibutuhkan (terutama pada IPv6).

NAT (Network Address Translation) menerjemahkan alamat privat ke alamat publik. NAT bukan firewall. Meskipun secara tidak langsung menyembunyikan host internal, NAT tidak menggantikan kontrol akses.

HTTP adalah protokol web. Tanpa TLS, isinya terbaca dan dapat diubah oleh siapa pun di jalur. HTTPS membungkus HTTP dengan TLS (Bab 6).

### 2.5 Perangkat Jaringan dan Peran Keamanannya

|Perangkat|Fungsi|Pertimbangan keamanan|
|---|---|---|
|Hub|Mengulang sinyal ke semua port|Usang. Mudah disadap|
|Switch|Meneruskan frame berdasarkan MAC|Aktifkan port security, VLAN, DHCP snooping, DAI|
|Router|Menghubungkan jaringan berbeda|Kunci akses admin, ACL, update firmware|
|Firewall|Menyaring lalu lintas|Aturan default deny, logging aktif|
|Access Point|Menyediakan Wi-Fi|WPA3, pisahkan SSID tamu|
|Load balancer / reverse proxy|Mendistribusikan lalu lintas|Terminasi TLS, mitigasi DDoS, WAF|

Pastikan firmware perangkat selalu diperbarui dan akses manajemen (SSH, web admin) tidak terbuka ke internet.

### 2.6 Menganalisis Lalu Lintas Dasar

Dua alat dasar yang wajib dikenal:

- tcpdump: menangkap paket di terminal.
- Wireshark: antarmuka grafis untuk menganalisis paket.

Contoh perintah tcpdump (jalankan hanya di jaringan milik sendiri):

```bash
# Menangkap paket DNS pada antarmuka eth0, tanpa menerjemahkan nama
sudo tcpdump -i eth0 -nn port 53

# Menangkap lalu lintas dari/ke satu host dan menyimpannya ke file
sudo tcpdump -i eth0 -nn host 192.168.1.20 -w tangkapan.pcap
```

Contoh filter tampilan Wireshark:

```
dns                                  # hanya lalu lintas DNS
tcp.flags.syn == 1 && tcp.flags.ack == 0   # paket SYN awal
tls.handshake.type == 1              # ClientHello pada TLS
http.request.method == "POST"        # permintaan HTTP POST
```

Jika Anda membuka lalu lintas HTTP biasa (tanpa TLS) di lab, Anda akan melihat isi permintaan dalam teks jelas. Itu demonstrasi nyata mengapa enkripsi diperlukan.

### Ringkasan Bab 2

- Keamanan harus dipikirkan di setiap lapisan model OSI dan TCP/IP.
- Banyak protokol dasar (ARP, DNS, DHCP) dirancang tanpa autentikasi dan karenanya rentan dipalsukan.
- Subnet dan port adalah dasar segmentasi dan pembatasan layanan.
- Tcpdump dan Wireshark adalah alat dasar untuk melihat apa yang sebenarnya terjadi di jaringan.

### Latihan Bab 2

1. Pada lapisan OSI mana ARP spoofing terjadi? Apa pertahanan yang dapat dipasang di switch?
2. Jelaskan mengapa SYN flood dapat membuat server tidak responsif.
3. Berapa jumlah host usable pada subnet 10.10.10.0/26?
4. Mengapa port 3389 dan 445 sebaiknya tidak dibuka langsung ke internet?

---

## Bab 3: Ancaman dan Serangan Jaringan

### Tujuan Pembelajaran

- Mengenali kategori serangan jaringan utama beserta cara kerjanya secara konseptual.
- Memahami tahapan serangan (kill chain) dan kerangka MITRE ATT&CK.
- Menghubungkan setiap serangan dengan kontrol pertahanan yang sesuai.

Catatan: bab ini menjelaskan serangan pada tingkat konsep untuk keperluan bertahan. Tidak ada instruksi langkah demi langkah untuk menyerang sistem nyata.

### 3.1 Aktor Ancaman

|Aktor|Motivasi|Contoh|
|---|---|---|
|Penjahat siber|Uang|Kelompok ransomware, penipu daring|
|Hacktivist|Ideologi atau protes|Defacement situs, DDoS bermotif politik|
|Kelompok yang disponsori negara|Spionase atau sabotase|Pencurian data strategis|
|Insider|Dendam, uang, atau kelalaian|Karyawan yang membocorkan data|
|Script kiddie|Rasa penasaran atau pamer|Memakai alat jadi tanpa paham mendalam|

### 3.2 Siklus Serangan: Cyber Kill Chain

Model Cyber Kill Chain menggambarkan tahapan umum sebuah serangan.

1. Reconnaissance: pengintaian dan pengumpulan informasi target.
2. Weaponization: penyiapan alat serangan.
3. Delivery: pengiriman (email phishing, situs jahat, USB).
4. Exploitation: pemanfaatan kerentanan atau kelalaian pengguna.
5. Installation: pemasangan akses menetap (persistence).
6. Command and Control (C2): komunikasi dengan server penyerang.
7. Actions on Objectives: mencuri data, mengenkripsi file, merusak.

Manfaat bagi pembela: kita dapat memutus rantai di tahap mana pun. Semakin awal diputus, semakin kecil kerugiannya.

Kerangka lain yang sangat berguna adalah MITRE ATT&CK, yaitu basis pengetahuan terbuka yang mencatat taktik dan teknik yang dipakai penyerang di dunia nyata (misalnya Initial Access, Lateral Movement, Exfiltration). Tim keamanan memakainya untuk memetakan deteksi dan mengukur cakupan pertahanan.

### 3.3 Serangan pada Kerahasiaan

Sniffing (penyadapan paket). Penyerang menangkap lalu lintas yang lewat. Pada jaringan yang memakai protokol tanpa enkripsi (HTTP, FTP, Telnet), isi termasuk kata sandi dapat terbaca. Pertahanan: enkripsi (HTTPS, SSH, VPN), segmentasi, dan switch (bukan hub).

Man-in-the-Middle (MITM). Penyerang menyisipkan diri di antara dua pihak yang berkomunikasi untuk membaca atau mengubah data. Teknik pendukungnya antara lain ARP spoofing, DNS spoofing, rogue access point, dan sertifikat palsu. Pertahanan: TLS dengan validasi sertifikat yang benar, HSTS, certificate pinning pada aplikasi tertentu, DNSSEC, dan kewaspadaan terhadap peringatan sertifikat.

Phishing dan rekayasa sosial. Menipu manusia agar memberikan kredensial atau menjalankan berkas berbahaya. Variannya: spear phishing (dipersonalisasi), whaling (menyasar eksekutif), smishing (SMS), vishing (telepon), dan kini penipuan berbasis suara dan video tiruan (deepfake). Pertahanan: pelatihan, filter email (SPF, DKIM, DMARC), MFA tahan phishing (passkeys), dan prosedur verifikasi untuk permintaan sensitif seperti transfer uang.

Pencurian kredensial. Meliputi brute force (mencoba banyak kombinasi), password spraying (satu kata sandi umum dicoba ke banyak akun), dan credential stuffing (memakai pasangan username dan kata sandi dari kebocoran lain). Pertahanan: MFA, pembatasan percobaan login, deteksi anomali, pemantauan kebocoran kredensial, dan kata sandi unik per layanan.

### 3.4 Serangan pada Integritas

Spoofing. Memalsukan identitas atau alamat: IP spoofing, MAC spoofing, email spoofing. Pertahanan: filtering ingress dan egress, autentikasi kuat, SPF, DKIM, DMARC.

Session hijacking. Mengambil alih sesi pengguna yang sah, misalnya dengan mencuri cookie sesi. Pertahanan: HTTPS penuh, cookie dengan atribut Secure, HttpOnly, dan SameSite, masa berlaku sesi yang pendek.

Serangan aplikasi web seperti SQL injection dan cross-site scripting (XSS). Keduanya muncul karena aplikasi mempercayai masukan pengguna. Pertahanan: validasi dan sanitasi masukan, parameterized query, pengkodean keluaran, Web Application Firewall (WAF), dan pengujian keamanan aplikasi.

Malware yang mengubah data. Contohnya trojan perbankan yang memodifikasi tampilan transaksi. Pertahanan: EDR, whitelist aplikasi, patching.

### 3.5 Serangan pada Ketersediaan

DoS dan DDoS. Denial of Service membuat layanan tidak dapat dipakai dengan membanjirinya atau menghabiskan sumber dayanya. Distributed DoS memakai ribuan sumber (botnet).

Jenis umum:

|Jenis|Cara kerja|Contoh|
|---|---|---|
|Volumetrik|Membanjiri bandwidth|UDP flood, amplifikasi DNS/NTP|
|Protokol|Menghabiskan tabel koneksi|SYN flood|
|Lapisan aplikasi|Membanjiri fungsi aplikasi yang mahal|HTTP flood|

Pertahanan: layanan mitigasi DDoS (CDN dan scrubbing), rate limiting, SYN cookies, anycast, kapasitas cadangan, dan rencana respons yang sudah dilatih.

Ransomware. Malware yang mengenkripsi data lalu meminta tebusan. Pola modern adalah double extortion: data dicuri terlebih dahulu, lalu diancam dibocorkan. Pertahanan: backup yang terisolasi dan teruji (aturan 3-2-1), patching, segmentasi, MFA, pembatasan hak admin, EDR, dan latihan pemulihan.

### 3.6 Pergerakan Lateral dan Eksfiltrasi

Setelah masuk, penyerang biasanya bergerak lateral dari satu mesin ke mesin lain untuk mencapai target berharga, lalu mengekstrak data (eksfiltrasi) melalui saluran yang tampak normal seperti HTTPS atau DNS. Pertahanan: segmentasi, mikrosegmentasi, pembatasan lalu lintas keluar (egress filtering), monitoring perilaku, dan prinsip least privilege.

### 3.7 Ancaman yang Meningkat

- Serangan berbantuan AI: pembuatan email phishing yang fasih dan tanpa salah ketik, tiruan suara dan wajah untuk penipuan, serta otomatisasi pengintaian. Pembela juga memakai AI untuk deteksi anomali dan triase peringatan, sehingga prinsip dasarnya tetap: verifikasi lewat saluran kedua dan gunakan autentikasi tahan phishing.
- Serangan rantai pasok perangkat lunak: pustaka atau pembaruan yang disusupi. Pertahanan: SBOM (Software Bill of Materials), penguncian versi dependensi, verifikasi tanda tangan, dan pemindaian dependensi.
- Eksploitasi perangkat tepi: kerentanan pada VPN gateway, firewall, dan perangkat manajemen. Pertahanan: inventaris aset yang akurat, patching cepat untuk perangkat yang menghadap internet, dan membatasi antarmuka manajemen.
- Harvest now, decrypt later: penyerang menyimpan data terenkripsi hari ini untuk didekripsi saat komputer kuantum memadai. Pertahanan jangka panjang: migrasi ke kriptografi pasca-kuantum (Bab 4 dan 15).

### 3.8 Tabel Ringkas: Serangan dan Pertahanannya

|Serangan|Lapisan utama|Pertahanan inti|
|---|---|---|
|Sniffing|1 sampai 2|Enkripsi, segmentasi|
|ARP spoofing|2|Dynamic ARP Inspection, VLAN|
|IP spoofing|3|Ingress/egress filtering|
|SYN flood|4|SYN cookies, rate limit|
|DNS poisoning|7|DNSSEC, resolver tepercaya|
|MITM|2 sampai 7|TLS, validasi sertifikat, HSTS|
|Brute force|7|MFA, lockout, rate limit|
|SQLi dan XSS|7|Kode aman, WAF|
|DDoS|3 sampai 7|CDN, scrubbing, rate limit|
|Ransomware|7|Backup, segmentasi, EDR, patch|
|Phishing|7 (manusia)|Pelatihan, MFA tahan phishing, filter email|

### Ringkasan Bab 3

- Serangan dapat dikelompokkan berdasarkan tujuan CIA yang diserang.
- Kill Chain dan MITRE ATT&CK membantu memahami dan memutus rantai serangan.
- Faktor manusia dan kredensial masih menjadi titik lemah terbesar.
- Setiap serangan memiliki pertahanan yang jelas; kuncinya adalah penerapan yang konsisten.

### Latihan Bab 3

1. Jelaskan perbedaan brute force, password spraying, dan credential stuffing.
2. Mengapa ARP spoofing hanya efektif di jaringan lokal yang sama?
3. Sebutkan minimal tiga kontrol untuk menurunkan dampak ransomware.
4. Sebuah staf keuangan menerima telepon dengan suara yang mirip direkturnya untuk mentransfer dana mendesak. Apa prosedur yang seharusnya diterapkan?

---

## Bab 4: Kriptografi Dasar

### Tujuan Pembelajaran

- Menjelaskan enkripsi simetris, asimetris, hash, dan tanda tangan digital.
- Menjelaskan sertifikat digital dan PKI.
- Mengetahui algoritma yang direkomendasikan, yang harus dihindari, dan arah menuju kriptografi pasca-kuantum.

Kriptografi adalah fondasi hampir seluruh mekanisme keamanan jaringan: HTTPS, VPN, Wi-Fi aman, tanda tangan digital, dan penyimpanan kata sandi.

### 4.1 Istilah Dasar

- Plaintext: data asli yang dapat dibaca.
- Ciphertext: data terenkripsi.
- Kunci (key): rahasia yang dipakai untuk enkripsi dan dekripsi.
- Algoritma (cipher): prosedur matematis untuk enkripsi.

Prinsip Kerckhoffs: keamanan sistem harus bergantung pada kerahasiaan kunci, bukan pada kerahasiaan algoritma. Karena itu kita memakai algoritma publik yang sudah diuji luas oleh komunitas, dan tidak menciptakan algoritma sendiri.

### 4.2 Enkripsi Simetris

Satu kunci yang sama dipakai untuk mengenkripsi dan mendekripsi.

```
Plaintext --[kunci K]--> Ciphertext --[kunci K]--> Plaintext
```

- Kelebihan: sangat cepat, cocok untuk data besar.
- Kekurangan: bagaimana membagikan kunci dengan aman?

Algoritma dan mode yang umum dan direkomendasikan:

- AES (128, 192, atau 256 bit) dengan mode AEAD seperti GCM.
- ChaCha20-Poly1305, populer di perangkat tanpa akselerasi AES perangkat keras.

Istilah AEAD (Authenticated Encryption with Associated Data) berarti enkripsi sekaligus menjamin integritas, sehingga data yang dimodifikasi akan terdeteksi. Hindari mode lama tanpa autentikasi (misalnya ECB) dan algoritma usang seperti DES, 3DES, dan RC4.

### 4.3 Enkripsi Asimetris

Memakai sepasang kunci: kunci publik (boleh disebar) dan kunci privat (dirahasiakan).

- Kunci publik mengenkripsi, kunci privat mendekripsi (untuk kerahasiaan).
- Kunci privat menandatangani, kunci publik memverifikasi (untuk tanda tangan digital).

Analogi: kunci publik seperti kotak surat dengan celah. Siapa pun dapat memasukkan surat, tetapi hanya pemilik kunci yang dapat membukanya.

Algoritma umum: RSA (disarankan minimal 2048 bit, 3072 bit untuk perlindungan jangka panjang), ECC seperti kurva P-256 dan X25519 untuk pertukaran kunci, serta Ed25519 untuk tanda tangan.

Karena asimetris lebih lambat, praktik umum adalah hibrida: gunakan asimetris untuk menyepakati kunci rahasia, lalu gunakan simetris untuk data. TLS bekerja seperti ini.

### 4.4 Pertukaran Kunci dan Forward Secrecy

Diffie-Hellman (dan versi kurva eliptiknya, ECDHE) memungkinkan dua pihak menyepakati rahasia bersama melalui saluran yang bisa disadap, tanpa pernah mengirim rahasia itu sendiri.

Jika kunci sesi dibuat sementara (ephemeral) untuk tiap sesi, kita mendapat perfect forward secrecy (PFS): kebocoran kunci privat server di masa depan tidak membuka rekaman lalu lintas lama. TLS 1.3 mewajibkan pertukaran kunci ephemeral sehingga PFS menjadi standar.

### 4.5 Fungsi Hash

Hash mengubah data berukuran apa pun menjadi nilai tetap (sidik jari, digest). Sifat penting:

- Satu arah: sulit mengembalikan dari hash ke data asli.
- Deterministik: data yang sama selalu menghasilkan hash yang sama.
- Efek longsor: perubahan satu bit mengubah hash secara drastis.
- Tahan tabrakan: sulit menemukan dua data berbeda dengan hash sama.

Rekomendasi: SHA-256, SHA-384, SHA-512, atau SHA-3. Hindari MD5 dan SHA-1 untuk keperluan keamanan.

Contoh di terminal:

```bash
echo -n "halo" | sha256sum
echo -n "Halo" | sha256sum   # hash sangat berbeda hanya karena huruf besar
```

Kegunaan: memeriksa integritas berkas unduhan, menyimpan kata sandi (dengan fungsi khusus, lihat Bab 5), dan tanda tangan digital.

HMAC adalah hash yang menggunakan kunci rahasia untuk menjamin integritas dan keaslian pesan antara dua pihak yang berbagi kunci.

### 4.6 Tanda Tangan Digital

Pengirim menghitung hash pesan, lalu mengenkripsinya dengan kunci privat. Penerima memverifikasi memakai kunci publik pengirim. Hasilnya:

- Integritas: pesan tidak berubah.
- Autentikasi: benar berasal dari pemilik kunci privat.
- Non-repudiation: pengirim sulit menyangkal.

### 4.7 Sertifikat Digital dan PKI

Pertanyaan penting: bagaimana kita yakin sebuah kunci publik benar milik situs tertentu? Jawabannya adalah sertifikat digital X.509, yaitu dokumen yang mengikat identitas (misalnya nama domain) dengan kunci publik, ditandatangani oleh Certificate Authority (CA) tepercaya.

```
Sertifikat Root CA (dipercaya browser/OS)
   |
   +-- Sertifikat Intermediate CA
          |
          +-- Sertifikat situs (contoh: www.contoh.ac.id)
```

Ini disebut rantai kepercayaan (chain of trust). Komponen PKI (Public Key Infrastructure) meliputi CA, registrasi identitas, penerbitan, pencabutan (CRL atau OCSP), dan manajemen siklus hidup.

Praktik penting:

- Perhatikan masa berlaku. Masa berlaku sertifikat publik cenderung diperpendek oleh industri sehingga otomatisasi perpanjangan (misalnya protokol ACME) hampir wajib.
- Lindungi kunci privat. Simpan di HSM atau penyimpanan aman, dan jangan pernah mengirimnya lewat email atau chat.
- Jangan mengabaikan peringatan sertifikat pada browser.

### 4.8 Ancaman Komputer Kuantum dan Kriptografi Pasca-Kuantum

Komputer kuantum berskala besar, jika terwujud, dapat memecahkan RSA dan ECC memakai algoritma Shor. Enkripsi simetris dan hash terpengaruh lebih ringan (umumnya cukup menambah ukuran kunci, misalnya memakai AES-256).

Ancaman yang sudah nyata hari ini adalah harvest now, decrypt later: data sensitif yang disadap sekarang bisa didekripsi di masa depan. Karena itu migrasi sudah dimulai.

Status standar NIST yang relevan:

|Standar|Algoritma|Fungsi|Status|
|---|---|---|---|
|FIPS 203|ML-KEM (dari CRYSTALS-Kyber)|Pertukaran kunci (KEM)|Final, diterbitkan Agustus 2024|
|FIPS 204|ML-DSA (dari CRYSTALS-Dilithium)|Tanda tangan digital|Final, diterbitkan Agustus 2024|
|FIPS 205|SLH-DSA (dari SPHINCS+)|Tanda tangan berbasis hash|Final, diterbitkan Agustus 2024|
|FIPS 206|FN-DSA (dari FALCON)|Tanda tangan digital|Dalam pengembangan|
|HQC|HQC (berbasis kode)|KEM cadangan non-lattice|Dipilih Maret 2025. Draf standar diperkirakan 2026 dan final 2027|

Langkah praktis bagi organisasi:

1. Buat inventaris kriptografi: di mana RSA dan ECC dipakai (TLS, VPN, sertifikat, tanda tangan kode, perangkat IoT).
2. Prioritaskan data yang harus tetap rahasia dalam jangka sangat panjang.
3. Terapkan crypto agility, yaitu merancang sistem agar algoritma dapat diganti tanpa membongkar seluruh arsitektur.
4. Gunakan mode hibrida (misalnya klasik X25519 digabung ML-KEM) selama masa transisi. Mode hibrida ini sudah mulai tersedia di sejumlah browser, pustaka TLS, dan layanan CDN.
5. Pantau pedoman lembaga standar dan regulator di negara Anda. Jadwal migrasi dapat berubah, sehingga selalu periksa dokumen terbaru.

### Ringkasan Bab 4

- Simetris cepat untuk data, asimetris untuk pertukaran kunci dan tanda tangan, hash untuk integritas.
- Sertifikat dan PKI menjawab masalah kepercayaan kunci publik.
- Gunakan AES-GCM atau ChaCha20-Poly1305, SHA-2 atau SHA-3, dan ECDHE dengan forward secrecy.
- Mulailah merencanakan migrasi ke kriptografi pasca-kuantum.

### Latihan Bab 4

1. Mengapa TLS memakai kombinasi enkripsi asimetris dan simetris?
2. Apa yang dimaksud forward secrecy dan mengapa penting?
3. Mengapa MD5 tidak lagi layak dipakai untuk keperluan keamanan?
4. Jelaskan apa itu ancaman harvest now, decrypt later dan dua langkah awal untuk menghadapinya.

---

## Bab 5: Autentikasi dan Kontrol Akses

### Tujuan Pembelajaran

- Menjelaskan faktor autentikasi dan cara kerja MFA.
- Memahami penyimpanan kata sandi yang benar dan mengapa passkeys lebih tahan phishing.
- Menjelaskan SSO, RADIUS, 802.1X, serta model kontrol akses seperti RBAC.

### 5.1 Faktor Autentikasi

|Faktor|Penjelasan|Contoh|
|---|---|---|
|Something you know|Sesuatu yang Anda ketahui|Kata sandi, PIN|
|Something you have|Sesuatu yang Anda miliki|HP, kunci keamanan FIDO2, kartu pintar|
|Something you are|Sesuatu yang melekat pada Anda|Sidik jari, wajah|
|Somewhere you are|Lokasi atau konteks|Alamat IP, perangkat terdaftar|

Multi-Factor Authentication (MFA) memakai dua faktor atau lebih dari kategori yang berbeda. Dua kata sandi bukan MFA karena keduanya berasal dari faktor yang sama.

Tidak semua MFA sama kuat:

|Metode MFA|Ketahanan terhadap phishing|Catatan|
|---|---|---|
|SMS OTP|Rendah|Rentan SIM swap dan pengalihan pesan. Lebih baik daripada tanpa MFA|
|Kode aplikasi authenticator (TOTP)|Sedang|Kode dapat diminta penipu lewat situs palsu|
|Notifikasi push|Sedang|Rentan MFA fatigue (diteror notifikasi hingga pengguna menekan setuju)|
|Passkeys dan kunci keamanan FIDO2|Tinggi|Terikat ke domain asli sehingga tidak bisa dipakai di situs palsu|

### 5.2 Kata Sandi yang Baik dan Passkeys

Pedoman modern (misalnya dari NIST SP 800-63B) menekankan:

- Panjang lebih penting daripada kerumitan. Frasa sandi yang panjang lebih baik daripada kombinasi simbol pendek yang sulit diingat.
- Jangan memaksa penggantian kata sandi berkala tanpa alasan. Ganti saat ada indikasi kebocoran.
- Periksa kata sandi baru terhadap daftar kata sandi yang pernah bocor.
- Izinkan penggunaan pengelola kata sandi (password manager) dan fitur tempel (paste).
- Gunakan kata sandi unik untuk setiap layanan.

Passkeys adalah pengganti kata sandi berbasis kriptografi kunci publik (standar FIDO2 dan WebAuthn). Perangkat Anda menyimpan kunci privat, server hanya menyimpan kunci publik. Saat login, perangkat menandatangani tantangan dari server setelah Anda membuka kunci dengan sidik jari, wajah, atau PIN. Keuntungan:

- Tidak ada rahasia bersama yang bisa dicuri dari server.
- Tidak dapat dikelabui situs phishing karena terikat ke domain yang benar.
- Lebih mudah bagi pengguna.

Dukungan passkeys sudah luas di sistem operasi, browser, dan layanan besar, dan diperkirakan terus tumbuh pada 2026 dan 2027.

### 5.3 Menyimpan Kata Sandi dengan Benar (untuk Pengembang)

Jangan simpan kata sandi sebagai teks biasa atau dengan hash cepat seperti SHA-256 polos. Gunakan fungsi hash kata sandi yang lambat dan memakai salt acak: Argon2id (pilihan modern), bcrypt, scrypt, atau PBKDF2 dengan jumlah iterasi tinggi.

- Salt: nilai acak unik per pengguna yang ditambahkan sebelum hash, sehingga dua pengguna dengan kata sandi sama tetap menghasilkan hash berbeda dan serangan tabel pelangi (rainbow table) menjadi tidak efektif.
- Pepper (opsional): rahasia tambahan yang disimpan terpisah dari database.
- Faktor kerja (cost) dapat dinaikkan seiring waktu seiring meningkatnya kecepatan perangkat keras.

### 5.4 Single Sign-On dan Federasi Identitas

SSO memungkinkan pengguna login sekali untuk mengakses banyak aplikasi. Protokol umum:

- SAML 2.0: banyak dipakai pada aplikasi enterprise.
- OAuth 2.0: kerangka otorisasi (memberi aplikasi akses terbatas tanpa membagikan kata sandi).
- OpenID Connect (OIDC): lapisan identitas di atas OAuth 2.0, dipakai pada tombol "Login dengan ..." di berbagai aplikasi.

Keuntungan SSO: kebijakan MFA dan pencabutan akses dapat dikelola terpusat. Risikonya: akun SSO yang diretas membuka banyak aplikasi sekaligus, sehingga akun ini wajib diberi perlindungan paling kuat.

### 5.5 AAA di Jaringan: RADIUS, TACACS+, dan 802.1X

- RADIUS: protokol AAA yang umum untuk akses jaringan (Wi-Fi enterprise, VPN).
- TACACS+: sering dipakai untuk mengontrol dan mencatat akses administrator ke perangkat jaringan, dengan otorisasi per perintah.
- IEEE 802.1X: kontrol akses berbasis port. Perangkat harus mengautentikasi diri dulu sebelum port switch atau Wi-Fi memberi akses penuh.

```
Perangkat (supplicant) --> Switch/AP (authenticator) --> Server RADIUS (authentication server)
```

Pada jaringan kampus atau perusahaan, 802.1X dengan sertifikat atau kredensial pengguna jauh lebih aman daripada satu kata sandi Wi-Fi yang dibagikan ke semua orang.

### 5.6 Model Kontrol Akses

|Model|Prinsip|Contoh|
|---|---|---|
|DAC (Discretionary)|Pemilik sumber daya menentukan akses|Izin berkas di folder pribadi|
|MAC (Mandatory)|Sistem menerapkan label klasifikasi|Lingkungan militer, SELinux|
|RBAC (Role-Based)|Akses berdasarkan peran|Peran "Admin", "Dosen", "Mahasiswa"|
|ABAC (Attribute-Based)|Akses berdasarkan atribut (pengguna, perangkat, lokasi, waktu)|Boleh akses hanya dari perangkat terkelola pada jam kerja|

Praktik penting:

- Terapkan least privilege dan tinjau hak akses secara berkala (access review).
- Pisahkan akun administrator dari akun harian.
- Pakai Privileged Access Management (PAM) untuk akun berhak tinggi: peminjaman kredensial sementara, perekaman sesi, dan persetujuan.
- Cabut akses segera saat karyawan atau mahasiswa keluar (offboarding).
- Hapus atau ganti kredensial bawaan perangkat (default password).

### Ringkasan Bab 5

- Gunakan MFA, terutama yang tahan phishing (passkeys atau kunci FIDO2).
- Simpan kata sandi dengan Argon2id, bcrypt, atau sejenisnya, bersama salt.
- SSO, RADIUS, dan 802.1X memusatkan dan memperkuat kontrol akses.
- Terapkan RBAC dan least privilege, serta tinjau akses secara berkala.

### Latihan Bab 5

1. Mengapa SMS OTP dianggap kurang kuat dibanding passkeys?
2. Apa fungsi salt pada penyimpanan kata sandi?
3. Jelaskan peran supplicant, authenticator, dan authentication server pada 802.1X.
4. Berikan contoh penerapan RBAC pada sistem akademik kampus.

---

## Bab 6: Protokol Komunikasi Aman

### Tujuan Pembelajaran

- Menjelaskan cara kerja TLS 1.3 dan HTTPS.
- Mengetahui SSH, IPsec, WireGuard, DNS aman, dan keamanan email.
- Mengonfigurasi dan memeriksa pengaturan keamanan dasar protokol-protokol tersebut.

### 6.1 TLS dan HTTPS

Transport Layer Security (TLS) melindungi komunikasi di atas TCP (dan QUIC) dengan tiga jaminan: kerahasiaan (enkripsi), integritas (deteksi perubahan), dan autentikasi (server, dan opsional klien, terbukti identitasnya). HTTPS adalah HTTP di atas TLS.

Versi dan status:

|Versi|Status|
|---|---|
|SSL 2.0 dan 3.0|Usang dan tidak boleh dipakai|
|TLS 1.0 dan 1.1|Usang|
|TLS 1.2|Masih dianggap aman jika dikonfigurasi benar, tetapi bertahap digeser|
|TLS 1.3 (RFC 8446, 2018)|Standar saat ini. Lebih cepat dan lebih aman|

Perbaikan utama TLS 1.3: jabat tangan lebih singkat, hanya cipher suite modern berstandar AEAD, forward secrecy diwajibkan, serta menghapus fitur rawan seperti pertukaran kunci RSA statis, mode CBC, dan SHA-1. Lembaga standar seperti NIST juga sedang meninjau pedoman TLS mereka agar lebih condong ke TLS 1.3. Praktik terbaik untuk server baru adalah mengaktifkan TLS 1.3 dan, bila perlu kompatibilitas, TLS 1.2 dengan cipher suite yang kuat (rujukan: RFC 9325).

Alur jabat tangan TLS 1.3 yang disederhanakan:

```
Klien                                   Server
  | -- ClientHello (versi, cipher,        |
  |     key share ECDHE) --------------->  |
  | <-- ServerHello (key share) ---------- |   Kunci sesi sudah dapat dihitung
  | <-- {Sertifikat, tanda tangan,         |   (sejak sini data terenkripsi)
  |      Finished} ----------------------- |
  | -- {Finished} ----------------------> |
  | <======= Data aplikasi terenkripsi ==> |
```

Langkah ringkasnya:

1. Klien mengusulkan parameter dan mengirim bagian pertukaran kunci ECDHE.
2. Server membalas dengan bagiannya. Kedua pihak menghitung kunci sesi yang sama.
3. Server membuktikan identitasnya dengan sertifikat dan tanda tangan.
4. Data dikirim terenkripsi dengan AEAD.

Catatan keamanan penting terkait pasca-kuantum: pertukaran kunci hibrida (misalnya X25519 digabung ML-KEM) di TLS 1.3 sudah mulai dipakai di banyak browser dan CDN. Versi TLS yang lebih lama tidak akan mendapat dukungan pasca-kuantum, sehingga ini salah satu alasan migrasi ke TLS 1.3 bersifat strategis.

Praktik pengamanan web:

- Aktifkan HSTS (HTTP Strict Transport Security) agar browser selalu memakai HTTPS.
- Arahkan seluruh HTTP ke HTTPS.
- Otomatiskan penerbitan dan perpanjangan sertifikat.
- Nonaktifkan versi dan cipher usang.
- Pertimbangkan Certificate Transparency monitoring untuk mendeteksi penerbitan sertifikat yang tidak sah atas domain Anda.

Catatan untuk tim keamanan: karena TLS 1.3 mengenkripsi lebih banyak bagian jabat tangan, beberapa teknik inspeksi lalu lintas lama tidak lagi bekerja. NIST menerbitkan panduan praktik (SP 1800-37) untuk mempertahankan visibilitas jaringan perusahaan tanpa meninggalkan TLS 1.3.

Memeriksa koneksi TLS dengan OpenSSL (pada server milik sendiri atau situs publik, hanya untuk membaca informasi koneksi):

```bash
# Menguji koneksi memakai TLS 1.3 dan menampilkan sertifikat
openssl s_client -connect contoh.com:443 -tls1_3 -servername contoh.com

# Melihat detail isi sertifikat dari file
openssl x509 -in sertifikat.pem -text -noout
```

### 6.2 SSH

SSH (Secure Shell, port 22) menyediakan akses terminal jarak jauh, transfer berkas (SFTP, SCP), dan tunnel yang terenkripsi. Pengganti Telnet dan FTP.

Hardening dasar pada /etc/ssh/sshd_config:

```
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
MaxAuthTries 3
X11Forwarding no
AllowUsers deploy admin
```

Membuat pasangan kunci modern dan memasangnya:

```bash
ssh-keygen -t ed25519 -C "nama@kampus.ac.id"
ssh-copy-id deploy@192.168.56.10
```

Setelah mengubah konfigurasi, muat ulang layanan (nama layanan bisa `ssh` atau `sshd` tergantung distribusi) dan uji login dari sesi kedua sebelum menutup sesi pertama agar tidak terkunci dari server.

Tips tambahan: batasi sumber alamat IP yang boleh mengakses SSH lewat firewall, gunakan fail2ban atau sejenis untuk memblokir percobaan berulang, dan lindungi kunci privat dengan passphrase.

### 6.3 IPsec

IPsec mengamankan lalu lintas pada lapisan jaringan (IP) dan banyak dipakai untuk VPN site-to-site.

- IKEv2: protokol untuk menegosiasikan dan mengelola kunci.
- ESP (Encapsulating Security Payload): memberi enkripsi dan integritas.
- AH (Authentication Header): hanya integritas dan autentikasi, jarang dipakai.
- Mode transport (melindungi isi paket) dan mode tunnel (membungkus seluruh paket asli, umum untuk VPN).

### 6.4 WireGuard

WireGuard adalah VPN modern yang sederhana (kode sangat ringkas), cepat, dan memakai kriptografi pilihan tetap: Curve25519 untuk pertukaran kunci, ChaCha20-Poly1305 untuk enkripsi, dan BLAKE2s untuk hash. Berjalan di atas UDP. Konfigurasinya berbasis pasangan kunci publik antar peer. Kesederhanaan memudahkan audit dan mengurangi salah konfigurasi.

### 6.5 DNS yang Lebih Aman

|Teknologi|Fungsi|
|---|---|
|DNSSEC|Menandatangani data DNS secara digital sehingga jawaban palsu dapat terdeteksi (integritas dan keaslian, bukan kerahasiaan)|
|DoT (DNS over TLS, port 853)|Mengenkripsi kueri DNS antara klien dan resolver|
|DoH (DNS over HTTPS)|Mengenkripsi kueri DNS di dalam HTTPS|
|Resolver tepercaya dan DNS filtering|Memblokir domain berbahaya yang diketahui|

DNS juga sering disalahgunakan malware untuk komunikasi C2 dan eksfiltrasi (DNS tunneling), sehingga log dan monitoring DNS bernilai tinggi.

### 6.6 Keamanan Email: SPF, DKIM, DMARC

Email aslinya tidak memverifikasi pengirim. Tiga mekanisme berbasis DNS menutup celah itu:

|Mekanisme|Fungsi|
|---|---|
|SPF|Mendaftar server mana yang berhak mengirim email atas nama domain Anda|
|DKIM|Menambahkan tanda tangan digital pada email sehingga keaslian dan integritasnya dapat diverifikasi|
|DMARC|Menetapkan kebijakan (none, quarantine, reject) bila SPF dan DKIM gagal, serta mengirim laporan|

Contoh catatan TXT sederhana (ilustrasi):

```
contoh.ac.id.         TXT  "v=spf1 include:_spf.penyedia-email.com -all"
_dmarc.contoh.ac.id.  TXT  "v=DMARC1; p=quarantine; rua=mailto:dmarc@contoh.ac.id"
```

Semakin ketat DMARC (reject), semakin sulit domain Anda dipalsukan untuk phishing. Terapkan bertahap dan pantau laporan agar email sah tidak ikut terblokir.

### 6.7 Mengganti Protokol Tak Aman

|Protokol lama|Masalah|Pengganti|
|---|---|---|
|Telnet|Teks biasa|SSH|
|FTP|Teks biasa|SFTP atau FTPS|
|HTTP|Teks biasa|HTTPS|
|SNMP v1/v2c|Community string teks biasa|SNMPv3|
|POP3/IMAP/SMTP polos|Teks biasa|Versi dengan TLS|
|PPTP VPN|Kriptografi lemah|WireGuard, IPsec/IKEv2, OpenVPN|

### Ringkasan Bab 6

- TLS 1.3 adalah standar saat ini dan jalur menuju kriptografi pasca-kuantum.
- SSH harus memakai kunci publik, tanpa login root dan tanpa kata sandi.
- IPsec dan WireGuard untuk VPN. DNSSEC, DoT, dan DoH untuk DNS yang lebih aman.
- SPF, DKIM, dan DMARC melindungi domain dari pemalsuan email.

### Latihan Bab 6

1. Sebutkan tiga perbedaan utama TLS 1.3 dibanding TLS 1.2.
2. Mengapa login SSH dengan kunci publik lebih aman daripada kata sandi?
3. Apa perbedaan DNSSEC dengan DoH?
4. Jelaskan fungsi SPF, DKIM, dan DMARC dengan analogi Anda sendiri.

---

## Bab 7: Firewall dan Segmentasi Jaringan

### Tujuan Pembelajaran

- Menjelaskan jenis-jenis firewall dan perbedaan stateless dan stateful.
- Memahami DMZ, VLAN, dan mikrosegmentasi.
- Menulis aturan firewall dasar dengan prinsip default deny.

### 7.1 Apa Itu Firewall?

Firewall adalah komponen yang memeriksa lalu lintas dan memutuskan untuk mengizinkan atau memblokirnya berdasarkan aturan. Dapat berupa perangkat keras, perangkat lunak pada host, atau layanan cloud.

### 7.2 Jenis Firewall

|Jenis|Cara kerja|Kelebihan|Keterbatasan|
|---|---|---|---|
|Packet filter (stateless)|Memeriksa tiap paket berdasarkan IP, port, protokol|Cepat, sederhana|Tidak memahami konteks koneksi|
|Stateful|Melacak status koneksi (tabel koneksi)|Mengizinkan balasan sah otomatis|Tidak memahami isi aplikasi|
|Proxy / application gateway|Menjadi perantara dan memahami protokol aplikasi|Inspeksi mendalam|Lebih lambat, perlu per-aplikasi|
|NGFW (Next-Generation)|Stateful ditambah identifikasi aplikasi, IPS, filtering URL, integrasi identitas|Visibilitas luas|Lebih mahal dan kompleks|
|WAF (Web Application Firewall)|Melindungi aplikasi web dari SQLi, XSS, dan sejenisnya|Fokus ke lapisan 7 web|Bukan pengganti kode yang aman|
|Host-based firewall|Firewall pada tiap server atau komputer|Perlindungan per mesin|Perlu pengelolaan terpusat|

Perbedaan stateless dan stateful dengan analogi: stateless seperti satpam yang mengecek setiap orang tanpa ingatan, sedangkan stateful seperti satpam yang ingat bahwa Anda tadi keluar membeli kopi dan mengizinkan Anda kembali masuk.

### 7.3 Prinsip Aturan Firewall

1. Default deny: kebijakan dasar blokir semua, lalu izinkan seperlunya.
2. Aturan spesifik: sebut sumber, tujuan, port, dan protokol sesempit mungkin.
3. Urutan penting: banyak firewall memproses aturan dari atas ke bawah dan berhenti pada kecocokan pertama.
4. Ingress dan egress: filter lalu lintas masuk dan juga keluar. Pembatasan keluar mempersulit malware menghubungi server C2.
5. Dokumentasikan dan tinjau aturan secara berkala. Aturan sementara yang terlupakan adalah celah klasik.
6. Aktifkan logging pada aturan penting.

### 7.4 Contoh Konfigurasi dengan nftables (Linux)

Contoh berikut untuk server yang hanya melayani SSH dan web. Uji pada VM lab, bukan langsung pada server produksi yang diakses jarak jauh, karena salah aturan dapat memutus koneksi Anda.

```
table inet filter {
  chain input {
    type filter hook input priority 0; policy drop;

    ct state established,related accept
    ct state invalid drop
    iif lo accept

    # ICMP dasar dengan batas laju, dan ICMPv6 yang dibutuhkan IPv6
    ip protocol icmp icmp type echo-request limit rate 5/second accept
    ip6 nexthdr icmpv6 icmpv6 type { echo-request, nd-neighbor-solicit, nd-neighbor-advert, nd-router-advert } accept

    # Layanan yang diizinkan
    tcp dport 22 ip saddr 192.168.56.0/24 accept
    tcp dport { 80, 443 } accept
  }

  chain forward {
    type filter hook forward priority 0; policy drop;
  }

  chain output {
    type filter hook output priority 0; policy accept;
  }
}
```

Penjelasan:

- `policy drop`: default deny untuk lalu lintas masuk.
- `ct state established,related accept`: memperbolehkan balasan atas koneksi yang sudah sah (stateful).
- SSH dibatasi hanya dari subnet manajemen 192.168.56.0/24.
- Aturan mencakup IPv4 dan IPv6 melalui tabel `inet`.

Menerapkan aturan dan melihat hasilnya:

```bash
sudo nft -f /etc/nftables.conf
sudo nft list ruleset
```

### 7.5 Contoh ACL pada Router (Konsep)

Access Control List (ACL) pada router atau switch layer 3 bekerja serupa. Contoh gaya Cisco IOS (ilustrasi):

```
ip access-list extended DARI-TAMU
 deny   ip 10.20.0.0 0.0.255.255 10.10.0.0 0.0.255.255
 permit tcp 10.20.0.0 0.0.255.255 any eq 443
 permit udp 10.20.0.0 0.0.255.255 any eq 53
 deny   ip any any log
```

Aturan ini melarang jaringan tamu (10.20.0.0/16) mengakses jaringan internal (10.10.0.0/16), tetapi membolehkan HTTPS dan DNS ke luar.

### 7.6 Segmentasi Jaringan

Segmentasi memecah jaringan menjadi zona-zona dengan kontrol di antaranya. Tujuannya membatasi radius kerusakan (blast radius) dan menyulitkan pergerakan lateral.

Contoh zona:

```
Internet
   |
[Firewall]----DMZ (web server publik, mail gateway)
   |
   +----LAN Staf
   +----Zona Server Internal (database, aplikasi)
   +----Zona Manajemen (akses admin, monitoring)
   +----Jaringan Tamu
   +----Zona IoT / CCTV
```

DMZ (Demilitarized Zone) adalah zona terpisah untuk layanan yang harus dapat diakses dari internet. Jika server di DMZ diretas, penyerang masih harus melewati firewall lagi untuk mencapai jaringan internal.

Teknik segmentasi:

- VLAN: memisahkan domain broadcast secara logis pada switch. VLAN saja bukan batas keamanan yang kuat bila tanpa kontrol antar-VLAN (ACL atau firewall) dan konfigurasi trunk yang benar.
- Subnet dan firewall antar zona.
- Mikrosegmentasi: kontrol granular sampai level beban kerja atau aplikasi (misalnya server A hanya boleh bicara ke database B pada port tertentu), umum di data center virtual, cloud, dan Kubernetes.
- Pemisahan jaringan tamu dan IoT dari jaringan kerja.

Praktik tambahan pada switch: port security, nonaktifkan port yang tidak dipakai, DHCP snooping, Dynamic ARP Inspection, dan hindari VLAN 1 untuk lalu lintas pengguna.

### 7.7 Kesalahan Umum

- Aturan "any any allow" yang dibuat sementara lalu terlupakan.
- Antarmuka manajemen firewall atau router terbuka ke internet.
- Hanya memfilter lalu lintas masuk, mengabaikan lalu lintas keluar.
- Lupa IPv6.
- Tidak ada pencadangan konfigurasi dan tidak ada kontrol perubahan.

### Ringkasan Bab 7

- Firewall menegakkan kebijakan berdasarkan aturan. Mulailah dengan default deny.
- Stateful memahami koneksi. NGFW dan WAF menambah pemahaman aplikasi.
- Segmentasi (DMZ, VLAN, mikrosegmentasi) membatasi dampak jika terjadi pelanggaran.

### Latihan Bab 7

1. Apa perbedaan firewall stateless dan stateful? Beri analogi.
2. Mengapa pembatasan lalu lintas keluar (egress) penting?
3. Pada contoh nftables, mengapa SSH hanya diizinkan dari 192.168.56.0/24?
4. Rancang segmentasi sederhana untuk laboratorium komputer kampus yang berisi komputer mahasiswa, server dosen, dan printer jaringan.

---

## Bab 8: IDS, IPS, Logging, dan Monitoring

### Tujuan Pembelajaran

- Membedakan IDS dan IPS, serta deteksi berbasis tanda tangan dan anomali.
- Memahami logging, SIEM, dan peran Security Operations Center (SOC).
- Menulis aturan deteksi sederhana dan memahami alat seperti Suricata dan Zeek.

Pencegahan saja tidak cukup. Kita harus berasumsi kontrol pencegahan sesekali gagal, sehingga kemampuan mendeteksi dan merespons cepat sama pentingnya.

### 8.1 IDS dan IPS

||IDS|IPS|
|---|---|---|
|Kepanjangan|Intrusion Detection System|Intrusion Prevention System|
|Posisi|Pasif (mengamati salinan lalu lintas)|Inline (lalu lintas melewatinya)|
|Tindakan|Memberi peringatan|Memberi peringatan dan memblokir|
|Risiko|Tidak menghentikan serangan|False positive dapat memblokir lalu lintas sah|

Berdasarkan lokasi:

- NIDS/NIPS: pada jaringan (contoh: Suricata, Snort, Zeek).
- HIDS: pada host (contoh: Wazuh, OSSEC), memantau log, integritas berkas, dan proses.

Berdasarkan metode deteksi:

- Signature-based: mencocokkan pola serangan yang sudah dikenal. Akurat untuk ancaman lama, tetapi lemah terhadap serangan baru.
- Anomaly-based: mempelajari perilaku normal dan memberi tanda pada penyimpangan. Mampu mendeteksi hal baru, tetapi rawan false positive. Pembelajaran mesin banyak dipakai di sini.
- Behavior dan threat-intelligence-based: menggunakan indikator kompromi (IoC) seperti alamat IP, domain, dan hash berkas berbahaya.

Istilah evaluasi:

- True positive: serangan nyata terdeteksi.
- False positive: lalu lintas normal ditandai serangan.
- False negative: serangan nyata tidak terdeteksi (paling berbahaya).

### 8.2 Contoh Aturan Suricata

```
alert tcp any any -> $HOME_NET 22 (msg:"LAB Percobaan login SSH berulang"; flow:to_server; flags:S; threshold:type both, track by_src, count 5, seconds 60; classtype:attempted-recon; sid:1000001; rev:1;)
```

Arti ringkas: beri peringatan bila satu sumber mengirim 5 koneksi SYN ke port 22 pada jaringan internal dalam 60 detik. Ini mendeteksi pola yang mirip percobaan brute force SSH. Aturan ini hanya contoh latihan dan perlu disesuaikan agar tidak berisik pada lingkungan nyata.

### 8.3 Visibilitas Jaringan: Flow, Paket, dan Metadata

|Sumber data|Isi|Kegunaan|
|---|---|---|
|Full packet capture (PCAP)|Seluruh isi paket|Forensik mendalam, mahal di penyimpanan|
|Metadata jaringan (Zeek)|Ringkasan koneksi, DNS, HTTP, TLS|Investigasi efisien|
|NetFlow/IPFIX|Siapa bicara ke siapa, berapa banyak|Deteksi anomali volume, pola eksfiltrasi|
|Log firewall, proxy, DNS|Keputusan dan kueri|Korelasi serangan|
|Log autentikasi dan endpoint|Login, proses, perubahan|Deteksi penyalahgunaan akun|

Karena TLS 1.3 mengenkripsi lebih banyak, deteksi modern lebih mengandalkan metadata, perilaku, dan telemetri endpoint, bukan hanya membaca isi payload.

### 8.4 Logging yang Baik

- Catat peristiwa penting: login berhasil dan gagal, perubahan hak akses, perubahan konfigurasi, akses data sensitif, keputusan firewall.
- Sinkronkan waktu semua perangkat dengan NTP agar urutan peristiwa dapat dikorelasikan.
- Kirim log ke lokasi terpusat dan terpisah dari sumbernya agar tidak dihapus penyerang.
- Lindungi integritas log dan tentukan masa retensi sesuai kebutuhan dan regulasi.
- Hindari mencatat data sensitif (kata sandi, token, data pribadi) dalam log.

### 8.5 SIEM, SOAR, dan SOC

- SIEM (Security Information and Event Management): mengumpulkan, menormalkan, mengorelasikan log dari banyak sumber, dan menghasilkan peringatan. Contoh: Wazuh dengan stack Elastic, Splunk, Microsoft Sentinel.
- SOAR (Security Orchestration, Automation, and Response): mengotomatisasi respons rutin lewat playbook.
- EDR/XDR dan NDR: deteksi dan respons pada endpoint dan jaringan.
- SOC (Security Operations Center): tim dan proses yang memantau peringatan 24 jam, melakukan triase, dan mengeskalasi insiden. Tingkat analis biasanya dibagi menjadi tier 1 (triase), tier 2 (investigasi), dan tier 3 (pemburu ancaman dan rekayasa deteksi).

Peringatan yang terlalu banyak menyebabkan alert fatigue. Karena itu kualitas aturan lebih penting daripada jumlahnya. Penyesuaian (tuning) dan prioritisasi berdasarkan risiko adalah pekerjaan berkelanjutan. Banyak SOC kini memanfaatkan AI untuk merangkum peringatan dan membantu triase, tetapi keputusan penting tetap perlu pengawasan manusia.

### 8.6 Honeypot dan Threat Hunting

- Honeypot: sistem umpan yang sengaja tampak menarik untuk mendeteksi dan mempelajari perilaku penyerang. Setiap interaksi dengannya patut dicurigai.
- Threat hunting: pencarian proaktif jejak penyerang berdasarkan hipotesis (misalnya dari teknik MITRE ATT&CK), bukan menunggu peringatan.

### Ringkasan Bab 8

- IDS mendeteksi, IPS mencegah. Keduanya perlu tuning untuk menekan false positive.
- Log yang lengkap, terpusat, dan tersinkron waktu adalah modal utama investigasi.
- SIEM, SOAR, dan SOC mengubah data mentah menjadi deteksi dan respons yang terorganisasi.

### Latihan Bab 8

1. Apa risiko memasang IPS inline dengan aturan yang terlalu agresif?
2. Jelaskan perbedaan false positive dan false negative, dan mana yang lebih berbahaya.
3. Mengapa sinkronisasi waktu (NTP) penting untuk logging?
4. Mengapa metadata dan telemetri endpoint makin penting saat sebagian besar lalu lintas sudah terenkripsi?

---

## Bab 9: VPN, Zero Trust, dan SASE

### Tujuan Pembelajaran

- Menjelaskan jenis VPN dan keterbatasannya.
- Memahami prinsip Zero Trust dan ZTNA.
- Mengenal konsep SASE dan arah arsitektur jaringan aman modern.

### 9.1 VPN

Virtual Private Network membuat terowongan terenkripsi di atas jaringan yang tidak tepercaya (internet).

|Jenis|Kegunaan|Contoh|
|---|---|---|
|Remote access VPN|Pegawai atau mahasiswa terhubung ke jaringan kantor atau kampus dari luar|WireGuard, OpenVPN, IPsec/IKEv2, SSL VPN|
|Site-to-site VPN|Menghubungkan dua jaringan (kantor pusat dan cabang)|IPsec antar firewall|
|VPN konsumen|Mengenkripsi lalu lintas ke penyedia VPN|Aplikasi VPN komersial|

Pemahaman yang tepat tentang VPN konsumen: VPN memindahkan kepercayaan dari penyedia internet ke penyedia VPN. VPN tidak membuat Anda anonim sepenuhnya dan tidak melindungi dari malware atau phishing.

Keterbatasan VPN tradisional untuk perusahaan:

- Setelah terhubung, pengguna sering mendapat akses jaringan yang luas, sehingga akun yang dicuri bisa dipakai bergerak lateral.
- Gateway VPN yang menghadap internet menjadi target serangan dan harus rajin di-patch.
- Pola "kastil dan parit" (aman di dalam, berbahaya di luar) tidak lagi cocok untuk dunia cloud dan kerja hibrida.

### 9.2 Zero Trust

Zero Trust adalah pendekatan keamanan yang tidak memberikan kepercayaan otomatis berdasarkan lokasi jaringan. Slogan intinya: never trust, always verify (jangan pernah percaya begitu saja, selalu verifikasi). Kerangka rujukan yang banyak dipakai adalah NIST SP 800-207.

Prinsip inti:

1. Verifikasi eksplisit: autentikasi dan otorisasi berdasarkan semua data yang tersedia (identitas, perangkat, lokasi, perilaku).
2. Least privilege: akses sekecil dan sesingkat mungkin (just-in-time, just-enough-access).
3. Assume breach: rancang dengan asumsi penyerang mungkin sudah ada di dalam. Segmentasikan, enkripsi, dan pantau terus.
4. Akses per sumber daya, bukan per jaringan. Mendapat akses ke satu aplikasi tidak berarti mendapat akses ke seluruh jaringan.
5. Evaluasi berkelanjutan, bukan hanya saat login.

Komponen konseptual:

```
Pengguna + Perangkat
        |
   [Policy Enforcement Point]  <--  [Policy Decision Point / Policy Engine]
        |                                   ^
   Sumber daya (aplikasi, data)             |
                                  Sinyal: identitas, kesehatan perangkat,
                                  lokasi, risiko, threat intelligence
```

ZTNA (Zero Trust Network Access) adalah implementasi praktisnya: pengguna mendapat akses ke aplikasi tertentu setelah identitas dan kondisi perangkat diperiksa, tanpa ditempatkan "di dalam jaringan". Aplikasi tidak perlu terekspos langsung ke internet.

Zero Trust bukan produk tunggal yang dapat dibeli, melainkan strategi yang diterapkan bertahap: mulai dari inventaris aset, penguatan identitas (MFA tahan phishing), segmentasi, pemantauan, lalu otomatisasi kebijakan.

### 9.3 SASE dan SSE

SASE (Secure Access Service Edge) menggabungkan fungsi jaringan (SD-WAN) dan keamanan (SWG, CASB, ZTNA, firewall as a service) yang disampaikan dari cloud. SSE (Security Service Edge) adalah bagian keamanannya saja. Tujuannya memberi perlindungan yang konsisten bagi pengguna di mana pun, terutama untuk organisasi dengan banyak cabang, pekerja hibrida, dan aplikasi SaaS.

|Komponen|Fungsi|
|---|---|
|SD-WAN|Mengatur konektivitas antar cabang secara cerdas|
|SWG (Secure Web Gateway)|Memfilter dan memeriksa lalu lintas web pengguna|
|CASB|Mengontrol penggunaan aplikasi cloud/SaaS|
|ZTNA|Akses per aplikasi berbasis Zero Trust|
|FWaaS|Firewall yang disampaikan sebagai layanan cloud|

### 9.4 Contoh Konfigurasi WireGuard Sederhana (Lab)

Sisi server (ilustrasi, kunci diganti placeholder):

```
[Interface]
Address = 10.8.0.1/24
ListenPort = 51820
PrivateKey = <KUNCI_PRIVAT_SERVER>

[Peer]
PublicKey = <KUNCI_PUBLIK_KLIEN>
AllowedIPs = 10.8.0.2/32
```

Membuat pasangan kunci:

```bash
wg genkey | tee privatekey | wg pubkey > publickey
```

Jangan pernah membagikan file privatekey. Hanya kunci publik yang dipertukarkan. Dalam praktik, batasi `AllowedIPs` seketat mungkin agar peer hanya dapat menjangkau alamat yang diperlukan.

### Ringkasan Bab 9

- VPN mengamankan jalur, tetapi VPN tradisional sering memberi akses terlalu luas.
- Zero Trust menggeser kepercayaan dari lokasi jaringan ke identitas, perangkat, dan konteks, dengan verifikasi berkelanjutan.
- ZTNA dan SASE adalah cara penerapan Zero Trust untuk dunia cloud dan kerja hibrida.

### Latihan Bab 9

1. Mengapa lokasi di dalam jaringan kantor tidak lagi dianggap cukup untuk memberi kepercayaan?
2. Sebutkan tiga prinsip inti Zero Trust.
3. Apa perbedaan akses VPN tradisional dengan ZTNA dari sisi cakupan akses?
4. Mengapa menjaga gateway VPN tetap ter-patch sangat penting?

---

## Bab 10: Keamanan Jaringan Nirkabel (Wi-Fi)

### Tujuan Pembelajaran

- Menjelaskan evolusi standar keamanan Wi-Fi dari WEP hingga WPA3.
- Mengenali ancaman khas jaringan nirkabel.
- Menerapkan konfigurasi Wi-Fi yang aman untuk rumah dan kampus.

### 10.1 Mengapa Wi-Fi Istimewa?

Pada jaringan kabel, penyerang harus terhubung secara fisik. Pada Wi-Fi, sinyal radio merambat ke segala arah sehingga siapa pun dalam jangkauan dapat mencoba menangkap sinyal atau mencoba terhubung. Karena itu enkripsi dan autentikasi pada lapisan Wi-Fi wajib.

### 10.2 Evolusi Standar Keamanan Wi-Fi

|Standar|Enkripsi|Status|
|---|---|---|
|WEP|RC4 dengan IV pendek|Rusak total. Dapat ditembus dalam hitungan menit. Jangan dipakai|
|WPA|TKIP|Usang|
|WPA2|AES-CCMP|Masih umum. Mode Personal (PSK) rentan serangan tebak kata sandi secara offline jika jabat tangan ditangkap dan kata sandinya lemah|
|WPA3-Personal|AES dengan SAE (Simultaneous Authentication of Equals)|Direkomendasikan. Tahan terhadap tebak offline, forward secrecy, dan Protected Management Frames (PMF) diwajibkan|
|WPA3-Enterprise|802.1X dengan opsi mode 192-bit|Direkomendasikan untuk kampus dan perusahaan|
|Enhanced Open (OWE)|Enkripsi oportunistik untuk jaringan terbuka|Meningkatkan privasi di hotspot tanpa kata sandi, tetapi tidak membuktikan identitas jaringan|

Catatan: banyak perangkat mendukung mode transisi WPA2/WPA3 demi kompatibilitas. Mode transisi berguna saat migrasi, tetapi keamanannya mengikuti klien terlemah. Setelah semua perangkat mendukung, gunakan WPA3 murni.

### 10.3 Ancaman Khas Nirkabel

|Ancaman|Penjelasan|Pertahanan|
|---|---|---|
|Rogue AP|Access point tidak sah dipasang di jaringan internal|Pemantauan nirkabel (WIPS), 802.1X, inventaris AP|
|Evil twin|AP palsu meniru SSID sah untuk memancing korban|WPA3-Enterprise dengan validasi sertifikat server, edukasi pengguna, VPN di jaringan publik|
|Deauthentication attack|Mengirim frame untuk memutus klien dari AP|Protected Management Frames (802.11w)|
|Penebakan kata sandi PSK|Menangkap jabat tangan lalu menebak offline|Kata sandi panjang dan acak, WPA3-SAE, 802.1X|
|WPS dengan PIN|Fitur kemudahan yang lemah|Nonaktifkan WPS|
|Penyadapan di jaringan terbuka|Lalu lintas tak terenkripsi terbaca|HTTPS di mana-mana, VPN, OWE|

### 10.4 Konfigurasi Wi-Fi Aman

Untuk rumah atau kantor kecil:

1. Gunakan WPA3-Personal atau, bila perangkat belum mendukung, WPA2-AES (jangan TKIP) dengan frasa sandi panjang (lebih dari 14 karakter) yang unik.
2. Ganti kata sandi admin router dan nama pengguna bawaan.
3. Nonaktifkan WPS dan manajemen dari sisi internet (remote administration).
4. Perbarui firmware router secara berkala. Jika vendor sudah berhenti memberi pembaruan, ganti perangkat.
5. Buat SSID tamu terpisah dengan isolasi klien, dan letakkan perangkat IoT di jaringan terpisah.
6. Aktifkan PMF (802.11w) jika tersedia.

Untuk kampus atau perusahaan:

1. Gunakan WPA3-Enterprise atau WPA2-Enterprise dengan 802.1X dan server RADIUS.
2. Konfigurasi klien untuk memvalidasi sertifikat server RADIUS agar terlindung dari evil twin.
3. Pisahkan SSID dan VLAN untuk staf, mahasiswa, tamu, dan perangkat IoT.
4. Terapkan Wireless IPS untuk mendeteksi rogue AP.
5. Rencanakan frekuensi dan daya sinyal agar tidak bocor berlebihan ke luar gedung.

### 10.5 Bluetooth dan Teknologi Nirkabel Lain

Bluetooth, NFC, Zigbee, dan jaringan seluler juga punya risiko tersendiri. Prinsip umumnya sama: matikan yang tidak dipakai, perbarui firmware, gunakan pairing yang aman, dan jangan menerima koneksi dari perangkat tak dikenal.

### Ringkasan Bab 10

- Gunakan WPA3 bila memungkinkan. Hindari WEP, WPA, dan TKIP.
- Untuk organisasi, 802.1X dengan validasi sertifikat lebih aman daripada satu kata sandi bersama.
- Pisahkan jaringan tamu dan IoT, nonaktifkan WPS, dan rawat firmware.

### Latihan Bab 10

1. Mengapa WEP dianggap rusak total?
2. Apa itu evil twin dan bagaimana WPA3-Enterprise dengan validasi sertifikat membantu?
3. Apa fungsi Protected Management Frames?
4. Susun daftar periksa pengamanan Wi-Fi untuk sebuah kafe yang menyediakan Wi-Fi pelanggan dan Wi-Fi untuk kasir.

---

## Bab 11: Keamanan Cloud, Container, dan IoT

### Tujuan Pembelajaran

- Menjelaskan model tanggung jawab bersama (shared responsibility) pada cloud.
- Mengenali kesalahan konfigurasi cloud yang umum dan cara mencegahnya.
- Memahami dasar keamanan container, Kubernetes, dan perangkat IoT.

### 11.1 Model Tanggung Jawab Bersama

Penyedia cloud mengamankan infrastruktur dasar (pusat data, perangkat keras, hipervisor). Pelanggan bertanggung jawab atas apa yang mereka tempatkan dan konfigurasi di atasnya.

|Model layanan|Penyedia bertanggung jawab atas|Anda bertanggung jawab atas|
|---|---|---|
|IaaS (mesin virtual, jaringan)|Fisik, jaringan inti, virtualisasi|Sistem operasi, patch, firewall, aplikasi, data, identitas|
|PaaS (platform)|Sistem operasi dan runtime|Aplikasi, data, konfigurasi, identitas|
|SaaS (aplikasi jadi)|Hampir seluruh tumpukan|Data, akun pengguna, pengaturan akses, MFA|

Kesalahpahaman umum: "Sudah di cloud berarti sudah aman". Kenyataannya sebagian besar insiden cloud berasal dari konfigurasi dan identitas yang salah di sisi pelanggan.

### 11.2 Kontrol Jaringan di Cloud

- VPC/VNet: jaringan virtual privat milik Anda di dalam cloud.
- Subnet publik dan privat: letakkan database dan layanan internal di subnet privat tanpa rute langsung dari internet.
- Security group (stateful) dan network ACL (stateless): firewall tingkat instans dan subnet. Terapkan default deny dan buka port seperlunya.
- Private endpoint/private link: mengakses layanan cloud tanpa melalui internet publik.
- Bastion host atau akses terkelola: jangan membuka SSH dan RDP ke seluruh internet.
- WAF dan perlindungan DDoS pada tepi aplikasi.
- Enkripsi data saat transit (TLS) dan saat disimpan (at rest), dengan manajemen kunci yang jelas (KMS).

### 11.3 Identitas adalah Perimeter Baru

Di cloud, identitas dan hak akses (IAM) sering menjadi pertahanan utama.

- Terapkan MFA pada semua akun, terutama akun root atau administrator.
- Jangan pakai akun root untuk pekerjaan harian.
- Gunakan peran (role) dengan kredensial sementara daripada kunci akses statis yang panjang umur.
- Terapkan least privilege dan tinjau izin yang tidak terpakai.
- Simpan rahasia (API key, kata sandi database) di layanan secrets manager, bukan di kode atau repositori.

### 11.4 Kesalahan Konfigurasi yang Sering Terjadi

|Kesalahan|Akibat|Pencegahan|
|---|---|---|
|Bucket penyimpanan terbuka ke publik|Kebocoran data massal|Blokir akses publik secara default, audit berkala|
|Port database terbuka ke internet|Pencurian atau pemerasan data|Subnet privat, security group ketat|
|Kunci akses bocor di repositori kode|Pengambilalihan akun cloud|Secrets scanning, rotasi kunci, peran sementara|
|Log tidak diaktifkan|Tidak bisa investigasi|Aktifkan log audit di semua akun dan wilayah|
|Izin IAM terlalu luas (wildcard)|Eskalasi hak akses|Least privilege, review izin|

Alat bantu: Cloud Security Posture Management (CSPM) untuk mendeteksi konfigurasi berisiko secara otomatis, dan Infrastructure as Code (IaC) scanning untuk memeriksa template sebelum diterapkan.

### 11.5 Keamanan Container dan Kubernetes

Container (misalnya Docker) mengemas aplikasi beserta dependensinya. Container berbagi kernel dengan host sehingga isolasinya lebih tipis daripada mesin virtual.

Praktik utama:

- Gunakan image dasar yang kecil dan terpercaya, dan pindai kerentanannya.
- Jangan menjalankan proses sebagai root di dalam container.
- Jangan menanam rahasia ke dalam image.
- Batasi kemampuan (capabilities) dan gunakan filesystem read-only bila memungkinkan.
- Perbarui image secara rutin dan tanda tangani image.

Pada Kubernetes, lalu lintas antar pod secara bawaan terbuka. Gunakan NetworkPolicy untuk mengimplementasikan mikrosegmentasi. Kebijakan dasar default deny:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-all
  namespace: aplikasi
spec:
  podSelector: {}
  policyTypes:
    - Ingress
    - Egress
```

Setelah itu izinkan jalur yang dibutuhkan saja dengan NetworkPolicy tambahan (misalnya frontend ke backend pada port 8080). Perhatikan bahwa NetworkPolicy hanya berfungsi bila plugin jaringan (CNI) yang dipakai mendukungnya.

Praktik lain: aktifkan RBAC dengan hak minimum, lindungi API server, enkripsi secrets, dan pantau perilaku runtime.

### 11.6 Keamanan IoT dan OT

Perangkat IoT (kamera, sensor, lampu pintar, printer) sering lemah karena kata sandi bawaan, firmware jarang diperbarui, dan sumber daya terbatas untuk enkripsi. Perangkat yang terinfeksi dapat dijadikan botnet untuk DDoS.

Langkah pengamanan:

1. Ganti kredensial bawaan dan nonaktifkan layanan yang tidak dipakai.
2. Letakkan IoT di VLAN atau SSID khusus dengan aturan firewall ketat (default deny ke jaringan internal).
3. Batasi komunikasi keluar hanya ke tujuan yang dibutuhkan.
4. Pilih produk dengan dukungan pembaruan keamanan yang jelas.
5. Gunakan protokol dengan enkripsi (misalnya MQTT di atas TLS).
6. Buat inventaris perangkat dan pantau perilakunya.

Sistem kendali industri (OT/ICS) memiliki prioritas berbeda: ketersediaan dan keselamatan sering lebih utama daripada kerahasiaan, dan perangkat bisa berumur puluhan tahun. Prinsip kunci: pisahkan jaringan OT dari IT, kendalikan akses jarak jauh dengan ketat, dan pantau secara pasif.

### Ringkasan Bab 11

- Di cloud, keamanan adalah tanggung jawab bersama. Identitas dan konfigurasi adalah area risiko terbesar.
- Gunakan subnet privat, security group ketat, enkripsi, dan secrets manager.
- Untuk container, minimalkan image dan hak akses serta terapkan NetworkPolicy.
- IoT harus diisolasi dan dirawat.

### Latihan Bab 11

1. Pada layanan SaaS, hal apa saja yang tetap menjadi tanggung jawab pelanggan?
2. Mengapa menyimpan kunci akses cloud di repositori kode publik sangat berbahaya?
3. Apa fungsi NetworkPolicy dengan podSelector kosong dan policyTypes Ingress dan Egress?
4. Mengapa kamera IP sebaiknya ditempatkan pada VLAN terpisah?

---

## Bab 12: Penilaian Kerentanan dan Uji Penetrasi

### Tujuan Pembelajaran

- Membedakan vulnerability assessment dan penetration testing.
- Memahami CVE, CVSS, dan prioritisasi kerentanan.
- Menjalankan pemindaian dasar secara etis di laboratorium sendiri.

### 12.1 Vulnerability Assessment vs Penetration Testing

|Aspek|Vulnerability Assessment|Penetration Testing|
|---|---|---|
|Tujuan|Menemukan sebanyak mungkin kerentanan|Membuktikan dampak nyata dengan mensimulasikan serangan|
|Cara|Umumnya otomatis dengan pemindai|Gabungan alat dan analisis manual|
|Hasil|Daftar kerentanan dan tingkat keparahan|Skenario serangan, bukti, dan rekomendasi|
|Frekuensi|Berkala (mingguan atau bulanan)|Berkala (tahunan) atau saat ada perubahan besar|

Keduanya saling melengkapi. Uji penetrasi tanpa manajemen kerentanan yang baik hanya menunjukkan masalah yang berulang.

### 12.2 Siklus Manajemen Kerentanan

1. Inventarisasi aset: apa yang kita miliki, di mana, siapa pemiliknya. Anda tidak dapat melindungi aset yang tidak Anda ketahui.
2. Pemindaian: temukan kerentanan secara terjadwal.
3. Prioritisasi: tentukan mana yang ditangani lebih dulu.
4. Perbaikan: patch, perubahan konfigurasi, atau kontrol kompensasi.
5. Verifikasi: pindai ulang untuk memastikan sudah teratasi.
6. Pelaporan dan perbaikan proses.

### 12.3 CVE, CVSS, dan Prioritisasi

- CVE (Common Vulnerabilities and Exposures): pengenal unik untuk kerentanan yang diketahui, contoh format CVE-2024-12345.
- CVSS (Common Vulnerability Scoring System): skor keparahan 0,0 sampai 10,0. Kategori umum: rendah, sedang, tinggi, kritis. Versi 4.0 telah diterbitkan dan mulai dipakai.
- Daftar kerentanan yang diketahui sedang dieksploitasi (misalnya katalog KEV dari CISA) dan skor probabilitas eksploitasi (EPSS) membantu menentukan prioritas.

Skor CVSS tinggi tidak otomatis berarti mendesak bagi Anda. Pertimbangkan juga:

- Apakah ada eksploit aktif di dunia nyata?
- Apakah aset menghadap internet?
- Seberapa penting aset dan datanya?
- Apakah ada kontrol kompensasi?

Contoh: kerentanan sedang pada server yang menghadap internet dan sudah dieksploitasi aktif bisa lebih mendesak daripada kerentanan kritis pada server terisolasi yang tidak menyimpan data penting.

### 12.4 Tahapan Uji Penetrasi

Mengacu pada kerangka umum seperti PTES:

1. Pra-engagement: menentukan ruang lingkup, tujuan, aturan main (Rules of Engagement), izin tertulis, dan kontak darurat.
2. Pengumpulan informasi (reconnaissance): pasif dan aktif.
3. Pemodelan ancaman.
4. Analisis kerentanan.
5. Eksploitasi terkontrol sesuai ruang lingkup.
6. Pascaeksploitasi: menilai dampak, tanpa merusak.
7. Pelaporan: temuan, bukti, tingkat risiko, dan rekomendasi perbaikan yang dapat ditindaklanjuti.
8. Pengujian ulang setelah perbaikan.

Jenis pendekatan: black box (tanpa informasi awal), gray box (informasi terbatas), dan white box (informasi penuh seperti kode sumber dan arsitektur).

Istilah tim:

- Red team: mensimulasikan penyerang secara lebih luas dan realistis.
- Blue team: bertahan dan mendeteksi.
- Purple team: kolaborasi keduanya untuk meningkatkan deteksi.

Kode etik: tetap dalam ruang lingkup, lindungi data temuan, hindari gangguan layanan, dan laporkan segera bila menemukan masalah kritis.

### 12.5 Pemindaian Port dengan Nmap (Hanya di Lab Sendiri)

Peringatan: pindai hanya mesin milik sendiri atau yang Anda punya izin tertulis. Pemindaian jaringan pihak lain tanpa izin dapat melanggar hukum.

```bash
# Menemukan host yang aktif pada subnet lab
nmap -sn 192.168.56.0/24

# Pemindaian SYN pada port umum (memerlukan hak root)
sudo nmap -sS 192.168.56.101

# Mendeteksi versi layanan pada port tertentu
nmap -sV -p 22,80,443 192.168.56.101

# Menjalankan skrip bawaan yang aman untuk informasi dasar
nmap -sC -sV 192.168.56.101
```

Cara membaca hasil:

|Status port|Arti|
|---|---|
|open|Ada layanan yang menerima koneksi|
|closed|Dapat dijangkau, tetapi tidak ada layanan|
|filtered|Terhalang firewall sehingga status tidak diketahui|

Gunakan hasil pemindaian untuk bertanya: apakah layanan ini memang perlu terbuka? Apakah versinya mutakhir? Siapa yang boleh mengaksesnya?

Alat lain yang umum: Greenbone/OpenVAS atau Nessus (pemindai kerentanan), Burp Suite dan OWASP ZAP (pengujian aplikasi web), serta Wireshark (analisis paket).

### 12.6 Menulis Laporan yang Berguna

Laporan yang baik berisi ringkasan eksekutif yang mudah dipahami manajemen, daftar temuan dengan tingkat risiko, deskripsi, bukti, dampak, langkah perbaikan konkret, dan prioritas. Hindari jargon berlebihan tanpa penjelasan, dan jangan hanya menempelkan keluaran alat.

### Ringkasan Bab 12

- Vulnerability assessment menemukan kelemahan secara luas, penetration test membuktikan dampak.
- Prioritisasi memperhatikan keparahan, eksploitasi aktif, paparan, dan nilai aset.
- Selalu bekerja dengan izin tertulis dan ruang lingkup yang jelas.

### Latihan Bab 12

1. Apa perbedaan utama vulnerability assessment dan penetration testing?
2. Mengapa skor CVSS saja tidak cukup untuk menentukan prioritas perbaikan?
3. Apa isi minimal dari Rules of Engagement?
4. Pada hasil Nmap sebuah port berstatus filtered. Apa kemungkinan artinya?

---

## Bab 13: Respons Insiden dan Forensik Jaringan

### Tujuan Pembelajaran

- Menjelaskan tahapan respons insiden.
- Memahami dasar penanganan bukti dan forensik jaringan.
- Menyusun strategi backup dan pemulihan.

Insiden keamanan akan terjadi pada waktu tertentu, walaupun pertahanan sudah baik. Yang membedakan organisasi adalah seberapa siap dan cepat ia merespons.

### 13.1 Tahapan Respons Insiden

Pedoman yang banyak dirujuk adalah NIST SP 800-61. Edisi sebelumnya menggunakan empat fase, dan edisi terbaru menyelaraskan aktivitas respons insiden dengan fungsi-fungsi NIST CSF 2.0. Untuk pemula, siklus klasik berikut mudah dipahami.

1. Persiapan (Preparation): kebijakan, tim, peran, kontak, alat, playbook, pelatihan, dan simulasi.
2. Deteksi dan analisis: memastikan bahwa itu benar insiden, menentukan cakupan dan tingkat keparahan.
3. Pembatasan (Containment): menghentikan penyebaran. Jangka pendek (isolasi segera) dan jangka panjang (perbaikan sementara).
4. Pemberantasan (Eradication): menghapus penyebab, malware, akun jahat, dan celah awal.
5. Pemulihan (Recovery): mengembalikan sistem ke operasi normal dengan pemantauan ketat.
6. Pelajaran yang dipetik (Lessons learned): rapat tinjauan tanpa mencari kambing hitam, dan perbaikan proses.

```
Persiapan -> Deteksi & Analisis -> Containment -> Eradication -> Recovery -> Lessons Learned
     ^                                                                           |
     +---------------------------------------------------------------------------+
```

### 13.2 Peran dalam Tim Insiden

|Peran|Tugas|
|---|---|
|Incident commander|Memimpin dan mengambil keputusan|
|Analis teknis|Investigasi, analisis log, forensik|
|Komunikasi|Koordinasi internal dan eksternal, pernyataan publik|
|Hukum dan kepatuhan|Kewajiban pelaporan dan pelindungan hak|
|Manajemen/bisnis|Dampak bisnis dan keputusan strategis|

### 13.3 Contoh Skenario: Dugaan Ransomware

Gejala: banyak berkas berubah ekstensi dan muncul pesan tebusan pada beberapa komputer.

Langkah awal yang umum:

1. Isolasi mesin terdampak dari jaringan (cabut kabel atau nonaktifkan Wi-Fi). Jangan langsung mematikan daya bila ingin menjaga bukti di memori, kecuali tim forensik menginstruksikan lain.
2. Aktifkan tim insiden dan catat waktu serta tindakan.
3. Tentukan cakupan: mesin mana yang terdampak, akun mana yang terlibat, dan apakah ada tanda eksfiltrasi data.
4. Blokir akun dan alamat yang dicurigai, serta ubah kredensial yang mungkin bocor.
5. Pastikan backup bersih dan terisolasi, lalu rencanakan pemulihan.
6. Libatkan pihak berwenang, ahli hukum, dan penyedia respons insiden bila diperlukan.
7. Perhatikan kewajiban pelaporan, misalnya pemberitahuan kebocoran data pribadi menurut UU PDP (periksa ketentuan dan batas waktu terbaru yang berlaku).

Keputusan membayar tebusan adalah keputusan bisnis dan hukum yang kompleks. Pembayaran tidak menjamin data kembali atau tidak dibocorkan, dan dapat mendorong serangan berikutnya. Persiapan terbaik adalah backup yang andal sehingga tebusan tidak menjadi satu-satunya jalan.

### 13.4 Dasar Forensik Digital dan Jaringan

Prinsip penanganan bukti:

- Jaga chain of custody: catat siapa memegang bukti, kapan, dan mengapa.
- Ikuti order of volatility: kumpulkan data yang paling mudah hilang lebih dulu (memori dan koneksi aktif sebelum disk, disk sebelum arsip).
- Kerjakan pada salinan (image) dan verifikasi integritas dengan hash (SHA-256).
- Dokumentasikan semua tindakan secara rinci.

Sumber bukti jaringan: log firewall, proxy, DNS, VPN, autentikasi, NetFlow, tangkapan paket, dan log IDS.

Contoh pencarian sederhana dengan tcpdump pada berkas tangkapan yang sudah ada:

```bash
# Membaca file tangkapan dan menampilkan hanya lalu lintas ke port 443 dari satu host
tcpdump -nn -r tangkapan.pcap 'host 192.168.1.50 and tcp port 443'

# Menghitung jumlah koneksi per alamat sumber (ilustrasi ringkas)
tcpdump -nn -r tangkapan.pcap 'tcp[tcpflags] & tcp-syn != 0' | awk '{print $3}' | sort | uniq -c | sort -nr | head
```

Indikator kompromi yang sering dicari: koneksi ke alamat atau domain yang dikenal berbahaya, volume keluar yang tidak wajar, pola beacon (koneksi berkala yang sangat teratur), kueri DNS aneh, dan login dari lokasi atau waktu tidak biasa.

### 13.5 Backup dan Pemulihan

Aturan 3-2-1 (dengan penguatan modern):

- 3 salinan data,
- pada 2 jenis media berbeda,
- 1 salinan di lokasi lain (offsite),
- 1 salinan yang offline atau tidak dapat diubah (immutable),
- 0 kesalahan: lakukan uji pemulihan berkala.

Backup yang tidak pernah diuji pemulihannya hanyalah harapan.

Istilah perencanaan:

- RPO (Recovery Point Objective): batas kehilangan data yang dapat diterima (misalnya maksimal 1 jam data terakhir).
- RTO (Recovery Time Objective): batas waktu pemulihan layanan yang dapat diterima.
- BCP (Business Continuity Plan) dan DRP (Disaster Recovery Plan): rencana agar bisnis tetap berjalan dan pulih dari bencana.

Pisahkan kredensial backup dari domain utama dan lindungi dengan MFA, karena penyerang sering menargetkan backup lebih dulu.

### Ringkasan Bab 13

- Respons insiden butuh persiapan: kebijakan, peran, playbook, dan latihan.
- Siklus: persiapan, deteksi dan analisis, containment, eradication, recovery, lessons learned.
- Kelola bukti dengan benar dan siapkan backup yang terisolasi serta teruji.

### Latihan Bab 13

1. Apa tujuan fase containment dan apa perbedaannya dengan eradication?
2. Mengapa pencatatan waktu dan tindakan selama insiden penting?
3. Jelaskan aturan backup 3-2-1 dan mengapa salinan immutable berguna.
4. Apa arti RPO 4 jam dan RTO 2 jam bagi sebuah layanan?

---

## Bab 14: Tata Kelola, Manajemen Risiko, dan Standar

### Tujuan Pembelajaran

- Memahami proses manajemen risiko keamanan.
- Mengenal standar dan kerangka kerja utama (ISO 27001, NIST CSF 2.0, CIS Controls).
- Memahami peran kebijakan, kepatuhan, dan regulasi di Indonesia secara garis besar.

Keamanan bukan hanya soal teknologi. Tanpa tata kelola, alat paling canggih pun tidak dipakai dengan benar.

### 14.1 Proses Manajemen Risiko

1. Identifikasi aset dan nilainya.
2. Identifikasi ancaman dan kerentanan.
3. Analisis risiko: kemungkinan dan dampak.
4. Evaluasi: bandingkan dengan toleransi risiko organisasi.
5. Perlakuan risiko, empat pilihan umum:
    - Mitigasi: kurangi dengan kontrol.
    - Transfer: alihkan sebagian, misalnya lewat asuransi atau kontrak.
    - Hindari: hentikan aktivitas yang menimbulkan risiko.
    - Terima: sadari dan setujui risiko sisa (secara tertulis dan oleh pihak berwenang).
6. Pantau dan tinjau secara berkala.

Contoh sederhana register risiko:

|Aset|Ancaman|Kerentanan|Kemungkinan|Dampak|Tingkat|Perlakuan|
|---|---|---|---|---|---|---|
|Server database mahasiswa|Pencurian data lewat akun admin|Tanpa MFA|Tinggi|Tinggi|Tinggi|Aktifkan MFA, PAM, log akses|
|Router cabang|Eksploitasi firmware lama|Belum di-update|Sedang|Sedang|Sedang|Jadwal patch bulanan|
|Wi-Fi tamu|Penyalahgunaan untuk aktivitas ilegal|Tanpa pembatasan|Sedang|Rendah|Rendah|Isolasi, batas bandwidth, log|

### 14.2 Kebijakan, Standar, Prosedur, dan Pedoman

|Dokumen|Fungsi|Contoh|
|---|---|---|
|Kebijakan (policy)|Arah dan aturan tingkat tinggi, disetujui manajemen|Kebijakan penggunaan yang dapat diterima, kebijakan kata sandi|
|Standar|Persyaratan spesifik yang wajib|Semua server memakai TLS 1.2 atau lebih tinggi|
|Prosedur|Langkah rinci melakukan tugas|Prosedur offboarding akun|
|Pedoman (guideline)|Saran yang tidak wajib|Praktik terbaik pembuatan frasa sandi|
|Baseline|Konfigurasi minimum yang aman|Baseline hardening server|

### 14.3 Kerangka Kerja dan Standar Utama

|Kerangka/Standar|Ringkasan|
|---|---|
|ISO/IEC 27001:2022|Standar internasional sistem manajemen keamanan informasi (SMKI/ISMS) yang dapat disertifikasi. Lampiran A versi 2022 berisi 93 kontrol dalam empat tema: organisasi, orang, fisik, dan teknologi. Pedoman penerapan kontrol ada di ISO/IEC 27002|
|NIST Cybersecurity Framework (CSF) 2.0|Kerangka sukarela dengan enam fungsi: Govern, Identify, Protect, Detect, Respond, Recover. Fungsi Govern ditambahkan pada versi 2.0 (2024) untuk menekankan tata kelola|
|CIS Critical Security Controls (v8.x)|Daftar kontrol praktis yang diprioritaskan, cocok sebagai langkah awal konkret|
|CIS Benchmarks|Panduan konfigurasi aman per produk (sistem operasi, perangkat jaringan, cloud)|
|NIST SP 800-53|Katalog kontrol keamanan dan privasi yang rinci|
|PCI DSS|Standar keamanan untuk data kartu pembayaran|
|MITRE ATT&CK|Basis pengetahuan taktik dan teknik penyerang untuk deteksi dan evaluasi|

Untuk pemula, urutan belajar yang masuk akal: CIS Controls (konkret), lalu NIST CSF 2.0 (kerangka besar), lalu ISO 27001 (sistem manajemen dan sertifikasi).

### 14.4 Regulasi dan Kelembagaan di Indonesia (Gambaran Umum)

- UU Informasi dan Transaksi Elektronik (UU ITE) beserta perubahannya: mengatur transaksi elektronik dan pidana terkait akses ilegal, penyadapan, dan gangguan sistem.
- UU Pelindungan Data Pribadi (UU No. 27 Tahun 2022): mengatur hak subjek data, kewajiban pengendali dan prosesor data, serta pemberitahuan kegagalan pelindungan data pribadi. Masa transisi penerapannya telah berakhir pada 2024.
- Badan Siber dan Sandi Negara (BSSN): lembaga yang menyusun kebijakan dan koordinasi keamanan siber nasional serta memiliki unit tanggap insiden.
- Regulator sektoral seperti OJK dan Bank Indonesia memiliki ketentuan keamanan siber untuk sektor keuangan.

Catatan: peraturan dapat diubah dan diperbarui. Selalu rujuk teks terbaru dan konsultasikan dengan ahli hukum untuk penerapan pada organisasi Anda.

### 14.5 Fondasi yang Sering Terlewat

Banyak insiden besar berawal dari hal mendasar yang diabaikan. Lima fondasi yang paling berpengaruh:

1. Inventaris aset yang akurat.
2. Patch dan pembaruan yang cepat, terutama untuk sistem yang menghadap internet.
3. MFA pada semua akun penting, dengan prioritas pada yang tahan phishing.
4. Backup terisolasi dan teruji.
5. Pelatihan kesadaran keamanan yang rutin dan realistis, serta budaya melapor tanpa takut disalahkan.

### 14.6 Keamanan Pihak Ketiga dan Rantai Pasok

Vendor, kontraktor, dan penyedia layanan memiliki akses ke sistem atau data Anda. Lakukan penilaian risiko vendor, batasi akses seperlunya, tuntut kewajiban keamanan dalam kontrak, dan pantau. Untuk perangkat lunak, kelola dependensi dan gunakan SBOM agar Anda tahu komponen apa yang ada di dalam aplikasi.

### Ringkasan Bab 14

- Manajemen risiko adalah siklus: identifikasi, analisis, perlakuan, pemantauan.
- ISO 27001, NIST CSF 2.0, dan CIS Controls memberi kerangka yang dapat diikuti.
- Kebijakan, kepatuhan, dan kebiasaan dasar yang disiplin sering lebih menentukan daripada alat canggih.

### Latihan Bab 14

1. Sebutkan empat pilihan perlakuan risiko dan beri contoh masing-masing.
2. Apa enam fungsi pada NIST CSF 2.0 dan fungsi mana yang baru pada versi 2.0?
3. Mengapa inventaris aset disebut fondasi keamanan?
4. Apa perbedaan kebijakan, standar, dan prosedur?

---

## Bab 15: Tren 2026 dan Seterusnya serta Jalur Karier

### Tujuan Pembelajaran

- Memahami tren utama keamanan jaringan untuk beberapa tahun ke depan.
- Menyusun rencana belajar dan jalur karier di bidang keamanan jaringan.

Tren di bawah ini adalah arah umum yang sudah terlihat. Detail teknis dan jadwal dapat berubah, sehingga biasakan memeriksa sumber resmi terbaru.

### 15.1 Migrasi Menuju Kriptografi Pasca-Kuantum

- Standar utama NIST (ML-KEM, ML-DSA, SLH-DSA) sudah final sejak 2024, FN-DSA (FIPS 206) sedang dikembangkan, dan HQC dipilih sebagai KEM cadangan dengan draf standar diperkirakan pada 2026 dan versi final pada 2027.
- Migrasi akan berlangsung bertahun-tahun karena menyangkut protokol (TLS, VPN, SSH), sertifikat, perangkat keras, dan perangkat IoT berumur panjang.
- Pendekatan praktis: inventaris kriptografi, crypto agility, mode hibrida, dan prioritas pada data yang harus rahasia sangat lama.
- Gunakan TLS 1.3 pada sistem baru karena menjadi jalur dukungan pasca-kuantum.

### 15.2 Kecerdasan Buatan di Dua Sisi

- Penyerang memakai AI untuk phishing yang meyakinkan, tiruan suara dan video, serta mempercepat pengintaian dan pembuatan kode serangan.
- Pembela memakai AI untuk deteksi anomali, triase peringatan, analisis log, dan otomatisasi respons.
- Sistem AI sendiri menjadi target dan permukaan serangan baru: injeksi prompt, kebocoran data lewat model atau agen, dan penyalahgunaan hak akses oleh agen otonom. Prinsip lama tetap berlaku: beri agen AI identitas sendiri, hak akses minimum, batas jaringan yang jelas, dan pencatatan aktivitas.
- Verifikasi lewat saluran kedua tetap menjadi pertahanan terbaik terhadap penipuan berbasis tiruan suara dan video.

### 15.3 Identitas dan Autentikasi Tahan Phishing

Passkeys dan kunci FIDO2 makin luas. Banyak organisasi bergerak menuju akses tanpa kata sandi untuk karyawan dan pelanggan. Tren penguatan identitas mencakup deteksi ancaman identitas (ITDR), akses just-in-time, dan pengurangan akun berhak tinggi yang permanen.

### 15.4 Zero Trust, SASE, dan Arsitektur Tanpa Perimeter Tunggal

Organisasi terus mengganti VPN luas dengan akses per aplikasi (ZTNA), memadukan keamanan dengan jaringan cabang (SASE), dan menerapkan mikrosegmentasi di data center dan cloud.

### 15.5 Visibilitas di Tengah Enkripsi yang Meningkat

TLS 1.3, QUIC/HTTP3, DNS terenkripsi, dan perkembangan seperti Encrypted Client Hello mengurangi metadata yang terlihat di jaringan. Meningkatkan privasi pengguna, tetapi menantang monitoring tradisional. Hasilnya, deteksi bergeser ke telemetri endpoint, identitas, metadata, dan analitik perilaku, bukan hanya inspeksi payload di jaringan.

### 15.6 Keamanan Rantai Pasok dan Secure by Design

- SBOM, verifikasi tanda tangan, dan pengelolaan dependensi menjadi praktik standar.
- Dorongan menuju bahasa pemrograman yang aman memori dan prinsip secure by design (keamanan bawaan, bukan tambahan) dari pengembang dan vendor.
- Perangkat tepi jaringan makin diawasi karena sering menjadi pintu masuk utama.

### 15.7 Attack Surface Management dan Otomatisasi

Pemantauan permukaan serangan eksternal secara berkelanjutan, remediasi otomatis untuk kesalahan konfigurasi, dan Infrastructure as Code yang dipindai keamanan sebelum diterapkan menjadi praktik umum.

### 15.8 Jaringan Baru: Wi-Fi 7, 5G, dan IPv6

Teknologi baru menghadirkan kecepatan dan kapasitas lebih tinggi, serta fitur keamanan yang lebih baik, tetapi juga permukaan serangan baru, misalnya private 5G untuk industri dan makin banyaknya perangkat terhubung. Penerapan IPv6 yang meluas menuntut kebijakan keamanan yang setara dengan IPv4.

### 15.9 Peta Jalan Belajar untuk Pemula

Contoh jalur 12 bulan:

|Bulan|Fokus|Kegiatan|
|---|---|---|
|1 sampai 2|Dasar jaringan dan Linux|Pelajari TCP/IP, subnetting, DNS, HTTP. Latihan terminal Linux. Bangun lab VM|
|3 sampai 4|Dasar keamanan dan kriptografi|Pelajari CIA, TLS, hash, PKI. Praktik dengan Wireshark dan OpenSSL|
|5 sampai 6|Pertahanan jaringan|Firewall nftables, VLAN, IDS Suricata, hardening SSH|
|7 sampai 8|Deteksi dan log|Pasang Wazuh atau Elastic, kumpulkan log, buat aturan sederhana|
|9 sampai 10|Penilaian kerentanan|Nmap, OpenVAS, OWASP ZAP di lab. Belajar membuat laporan|
|11 sampai 12|Respons insiden dan tata kelola|Simulasi insiden, pelajari NIST CSF dan ISO 27001, ikut kompetisi CTF|

Kebiasaan belajar yang efektif: praktik langsung di lab, mendokumentasikan hasil (blog atau repositori catatan), mengikuti CTF tingkat pemula, membaca laporan insiden publik, dan bergabung dengan komunitas keamanan.

### 15.10 Peran dan Sertifikasi

|Peran|Fokus|
|---|---|
|Network administrator / engineer|Membangun dan merawat jaringan, dengan kesadaran keamanan|
|Network security engineer|Firewall, VPN, segmentasi, IDS/IPS|
|SOC analyst|Memantau dan menganalisis peringatan|
|Incident responder / DFIR|Menangani insiden dan forensik|
|Penetration tester / red team|Menguji pertahanan secara etis|
|Security architect|Merancang arsitektur aman|
|GRC specialist|Tata kelola, risiko, kepatuhan|
|Cloud security engineer|Keamanan lingkungan cloud|

Sertifikasi yang sering dijadikan rujukan (pilih sesuai jalur karier dan anggaran): CompTIA Network+ dan Security+, Cisco CCNA, sertifikasi tingkat menengah seperti CySA+ atau blue team lainnya, tingkat lanjut seperti CISSP, CISM, dan OSCP untuk uji penetrasi. Di Indonesia, skema sertifikasi kompetensi melalui BNSP juga relevan. Sertifikasi bukan pengganti pengalaman praktik, tetapi membantu membuktikan dasar pengetahuan.

### Ringkasan Bab 15

- Tren besar: pasca-kuantum, AI di dua sisi, passkeys, Zero Trust dan SASE, visibilitas di era enkripsi, rantai pasok, dan secure by design.
- Pemula sebaiknya membangun fondasi jaringan dan Linux, lalu berpraktik terus-menerus di lab.

### Latihan Bab 15

1. Mengapa migrasi pasca-kuantum perlu dimulai sebelum komputer kuantum yang kuat benar-benar ada?
2. Bagaimana AI dapat memperkuat penyerang maupun pembela?
3. Apa tantangan yang dibawa enkripsi yang makin luas bagi tim monitoring jaringan?
4. Susun rencana belajar 6 bulan versi Anda sendiri sesuai waktu luang yang Anda miliki.

---

## Bab 16: Lab Praktik Terpandu

Semua lab dilakukan pada mesin virtual dan jaringan milik Anda sendiri. Gunakan mode jaringan host-only atau internal pada hipervisor agar lab terisolasi dari jaringan lain. Alamat IP di bawah hanyalah contoh, sesuaikan dengan lab Anda.

Topologi lab yang disarankan:

```
+-----------------+        Host-only network        +----------------------+
| VM Analis       |  192.168.56.0/24                | VM Server            |
| (Kali/Ubuntu)   |<------------------------------->| (Ubuntu Server)     |
| 192.168.56.10   |                                 | 192.168.56.101       |
+-----------------+                                 +----------------------+
```

### Lab 1: Menangkap dan Membandingkan Lalu Lintas HTTP dan HTTPS

Tujuan: melihat langsung mengapa enkripsi penting.

Langkah:

1. Pada VM Server, jalankan server web sederhana di port 8080 pada folder berisi berkas contoh:
    
    ```bash
    python3 -m http.server 8080
    ```
    
2. Pada VM Analis, jalankan Wireshark (atau tcpdump) pada antarmuka host-only.
3. Dari VM Analis, akses `http://192.168.56.101:8080` memakai browser atau curl.
4. Pada Wireshark, gunakan filter `http` dan lihat permintaan serta isi balasan dalam teks jelas.
5. Lakukan hal serupa ke situs HTTPS publik dan perhatikan bahwa isi aplikasi tidak terbaca. Gunakan filter `tls.handshake.type == 1` untuk melihat ClientHello.

Pertanyaan refleksi: informasi apa yang masih terlihat pada lalu lintas HTTPS (alamat tujuan, ukuran, kemungkinan nama server pada SNI)? Apa implikasinya bagi privasi?

### Lab 2: Pemindaian Port dan Inventaris Layanan

Tujuan: mengenal port terbuka dan layanan pada mesin sendiri.

Langkah (dari VM Analis ke VM Server):

```bash
nmap -sn 192.168.56.0/24
sudo nmap -sS 192.168.56.101
nmap -sV -p 22,80,8080 192.168.56.101
```

Catat setiap port terbuka dan tanyakan: apakah perlu? Siapa yang butuh? Versinya terbaru?

### Lab 3: Menerapkan Firewall Default Deny

Tujuan: membatasi layanan menggunakan nftables.

Langkah (pada VM Server, dengan akses konsol hipervisor sebagai cadangan bila terkunci):

1. Salin aturan dari Bab 7 ke `/etc/nftables.conf` dan sesuaikan subnet manajemen.
2. Terapkan: `sudo nft -f /etc/nftables.conf`.
3. Dari VM Analis, ulangi pemindaian Nmap dari Lab 2.
4. Bandingkan hasil sebelum dan sesudah. Port yang tidak diizinkan seharusnya tampak filtered.
5. Coba akses dari alamat yang tidak berada di subnet manajemen dan amati bahwa SSH ditolak.

Pertanyaan refleksi: apa yang terjadi bila baris `ct state established,related accept` dihapus?

### Lab 4: Membuat Sertifikat dan Menguji TLS

Tujuan: memahami sertifikat dan koneksi TLS.

Langkah (pada VM Server):

```bash
# Membuat sertifikat self-signed untuk lab (jangan dipakai di produksi)
openssl req -x509 -newkey rsa:3072 -nodes -keyout key.pem -out cert.pem -days 30 -subj "/CN=lab.local"

# Menjalankan server uji TLS sederhana di port 4433
openssl s_server -accept 4433 -cert cert.pem -key key.pem -www
```

Dari VM Analis:

```bash
openssl s_client -connect 192.168.56.101:4433 -tls1_3
```

Amati peringatan verifikasi sertifikat (karena self-signed), versi protokol, dan cipher suite yang dipilih. Coba paksa versi lama (misalnya `-tls1_1`) dan catat hasilnya.

Pertanyaan refleksi: mengapa browser memperingatkan pada sertifikat self-signed? Apa yang membuat sertifikat dari CA publik dipercaya?

### Lab 5: Hardening SSH

Tujuan: mengamankan akses administrasi.

Langkah:

1. Pada VM Analis, buat kunci: `ssh-keygen -t ed25519`.
2. Salin ke server: `ssh-copy-id pengguna@192.168.56.101`.
3. Uji login dengan kunci.
4. Pada server, ubah `/etc/ssh/sshd_config`: `PermitRootLogin no`, `PasswordAuthentication no`, `MaxAuthTries 3`.
5. Muat ulang layanan SSH, lalu uji dari sesi baru sebelum menutup sesi lama.
6. Coba login dengan kata sandi dan pastikan ditolak.

Pertanyaan refleksi: apa yang harus dilakukan bila kunci privat Anda hilang atau dicuri?

### Lab 6: Mendeteksi Percobaan Brute Force dengan Suricata

Tujuan: merasakan deteksi berbasis aturan.

Langkah (pada VM Server):

1. Pasang Suricata: `sudo apt install suricata`.
2. Atur `HOME_NET` pada `/etc/suricata/suricata.yaml` agar sesuai subnet lab.
3. Buat berkas aturan lokal dengan isi aturan SSH dari Bab 8, daftarkan pada `rule-files`, lalu uji konfigurasi: `sudo suricata -T -c /etc/suricata/suricata.yaml`.
4. Jalankan Suricata pada antarmuka lab: `sudo suricata -c /etc/suricata/suricata.yaml -i <nama-antarmuka>`.
5. Dari VM Analis, hasilkan banyak koneksi ke port 22 milik VM Server sendiri, misalnya:
    
    ```bash
    for i in $(seq 1 10); do nc -zv 192.168.56.101 22; done
    ```
    
6. Periksa `/var/log/suricata/fast.log` untuk melihat peringatan.

Pertanyaan refleksi: bagaimana membedakan lalu lintas sah yang ramai dengan percobaan brute force agar false positive berkurang?

### Lab 7: Merancang Segmentasi (Kertas atau Simulator)

Tujuan: menerapkan prinsip segmentasi pada rancangan.

Tugas: gunakan Cisco Packet Tracer, GNS3, atau cukup gambar di kertas. Rancang jaringan sebuah kampus kecil dengan zona: mahasiswa, dosen, server akademik, server publik (DMZ), Wi-Fi tamu, dan CCTV. Tentukan subnet, VLAN, dan aturan antar zona. Tuliskan tabel aturan yang menyatakan zona mana boleh mengakses zona mana, pada port apa, dan mengapa.

Contoh tabel awal:

|Sumber|Tujuan|Port|Keputusan|
|---|---|---|---|
|Mahasiswa|Server akademik|443|Izinkan|
|Mahasiswa|Server dosen|Semua|Tolak|
|Tamu|Internet|80, 443, 53|Izinkan|
|Tamu|Zona internal|Semua|Tolak|
|CCTV|Perekam|Port tertentu|Izinkan|
|CCTV|Internet|Semua|Tolak|

### Proyek Akhir

Rancang dan dokumentasikan arsitektur jaringan aman untuk sebuah organisasi fiktif (misalnya sekolah, klinik, atau toko daring). Hasil minimal mencakup:

1. Diagram jaringan dengan zona dan alur lalu lintas.
2. Daftar aset penting dan penilaian risiko sederhana (register risiko).
3. Aturan firewall dan segmentasi utama.
4. Rencana autentikasi (MFA, SSO) dan akses jarak jauh.
5. Rencana logging dan monitoring.
6. Rencana backup dan respons insiden singkat.
7. Catatan kesiapan migrasi kriptografi dan pembaruan perangkat.

---

## Kunci Jawaban Singkat

Jawaban berikut bersifat ringkas sebagai pembanding. Jawaban Anda boleh lebih lengkap.

### Bab 1

1. Confidentiality (contoh serangan: penyadapan kata sandi), integrity (contoh: pengubahan data transaksi di jalur), availability (contoh: DDoS).
2. Ancaman adalah sesuatu yang berpotensi menimbulkan kerugian, kerentanan adalah kelemahan yang dapat dimanfaatkan. Contoh: peretas (ancaman) memanfaatkan perangkat lunak yang belum di-patch (kerentanan).
3. Kerahasiaan terancam. Kontrol: hash kata sandi dengan Argon2id atau bcrypt plus salt, MFA, dan enkripsi.
4. Karena satu firewall dapat gagal atau dilewati. Pertahanan berlapis memastikan lapisan lain tetap melindungi dan membatasi kerusakan.

### Bab 2

1. Lapisan 2 (Data Link). Pertahanan: Dynamic ARP Inspection, segmentasi, dan enkripsi end-to-end.
2. SYN flood mengirim banyak SYN tanpa menyelesaikan jabat tangan sehingga tabel koneksi server penuh dan koneksi sah tidak dapat dilayani.
3. /26 berarti 64 alamat, dikurangi alamat jaringan dan broadcast menjadi 62 host usable.
4. Keduanya sering dieksploitasi untuk brute force, penyebaran ransomware, dan pergerakan lateral. Akses harus lewat VPN atau ZTNA dan dibatasi.

### Bab 3

1. Brute force mencoba banyak kombinasi pada satu akun. Password spraying mencoba satu kata sandi umum pada banyak akun. Credential stuffing memakai pasangan username dan kata sandi dari kebocoran lain.
2. ARP bekerja dalam satu domain broadcast lokal, sehingga penyerang harus berada di segmen jaringan yang sama.
3. Contoh: backup terisolasi dan teruji, segmentasi, patching, MFA, pembatasan hak admin, EDR.
4. Verifikasi lewat saluran kedua yang sudah dikenal (menelepon balik ke nomor resmi), terapkan persetujuan ganda untuk transfer, dan jangan mengandalkan suara semata.

### Bab 4

1. Asimetris aman untuk menyepakati kunci tetapi lambat. Simetris cepat untuk data. Gabungan keduanya memberi keamanan dan kinerja.
2. Forward secrecy berarti kunci sesi bersifat sementara sehingga kebocoran kunci privat server di masa depan tidak membuka lalu lintas lama.
3. MD5 rentan terhadap tabrakan sehingga data berbeda dapat dibuat memiliki hash sama.
4. Data terenkripsi disimpan sekarang dan didekripsi nanti saat komputer kuantum memadai. Langkah awal: inventaris kriptografi dan terapkan crypto agility atau mode hibrida.

### Bab 5

1. SMS OTP rentan SIM swap dan pengalihan pesan, serta dapat dikelabui situs phishing. Passkeys terikat ke domain asli dan tidak memakai rahasia bersama.
2. Salt membuat hash berbeda untuk kata sandi yang sama dan melemahkan serangan tabel pelangi.
3. Supplicant adalah perangkat klien yang meminta akses, authenticator adalah switch atau AP yang menjaga port, dan authentication server (RADIUS) memutuskan autentikasi.
4. Contoh: peran Mahasiswa (lihat nilai sendiri), Dosen (isi nilai mata kuliah yang diampu), Admin akademik (kelola data master).

### Bab 6

1. Contoh: jabat tangan lebih singkat, hanya cipher suite modern, forward secrecy wajib, fitur rawan dihapus.
2. Tidak ada rahasia yang dikirim, tidak dapat ditebak lewat brute force kata sandi, dan kunci privat tidak meninggalkan perangkat pengguna.
3. DNSSEC memverifikasi keaslian dan integritas jawaban DNS, DoH mengenkripsi kueri DNS agar tidak disadap.
4. SPF menyatakan server yang berhak mengirim, DKIM menandatangani email, DMARC menetapkan tindakan jika keduanya gagal dan memberi laporan.

### Bab 7

1. Stateless memeriksa tiap paket tanpa ingatan, stateful melacak status koneksi. Analogi satpam yang mengingat orang yang baru keluar.
2. Membatasi lalu lintas keluar menyulitkan malware menghubungi server C2 dan mengirim data keluar.
3. Mengurangi permukaan serangan: hanya jaringan manajemen yang dapat mencoba SSH.
4. Contoh: VLAN mahasiswa, VLAN dosen/server, VLAN printer. Mahasiswa boleh mencetak, tetapi tidak boleh mengakses server dosen. Default deny antar VLAN.

### Bab 8

1. IPS dapat memblokir lalu lintas sah (false positive) dan mengganggu layanan.
2. False positive adalah alarm palsu, false negative adalah serangan yang tidak terdeteksi. False negative lebih berbahaya.
3. Agar urutan peristiwa dari berbagai perangkat dapat dikorelasikan dengan benar.
4. Karena isi payload tidak dapat dibaca, sehingga deteksi bergantung pada metadata, perilaku, dan telemetri endpoint.

### Bab 9

1. Penyerang atau akun yang dicuri dapat berada di dalam jaringan. Kepercayaan harus berdasarkan verifikasi identitas, perangkat, dan konteks.
2. Contoh: verifikasi eksplisit, least privilege, assume breach.
3. VPN tradisional sering memberi akses ke jaringan luas, ZTNA memberi akses hanya ke aplikasi tertentu.
4. Gateway VPN menghadap internet sehingga menjadi target utama. Kerentanan yang tidak di-patch dapat membuka seluruh jaringan.

### Bab 10

1. Kriptografinya lemah (RC4 dengan IV pendek) sehingga kunci dapat dipulihkan dengan cepat dari lalu lintas yang ditangkap.
2. Evil twin adalah AP palsu bernama sama dengan yang sah. Validasi sertifikat server RADIUS membuat klien menolak AP palsu yang tidak memiliki sertifikat sah.
3. Melindungi frame manajemen (misalnya deauthentication) dari pemalsuan.
4. Contoh: WPA3 atau WPA2-AES, kata sandi kuat, SSID pelanggan terpisah dari kasir, isolasi klien, WPS mati, firmware diperbarui, kredensial admin diganti.

### Bab 11

1. Data, akun dan akses pengguna, konfigurasi keamanan aplikasi, dan MFA.
2. Penyerang dapat mengambil alih akun cloud, membuat sumber daya, mencuri data, dan menimbulkan biaya besar.
3. Menjadi kebijakan default deny untuk semua pod pada namespace, sehingga lalu lintas masuk dan keluar ditolak kecuali diizinkan oleh kebijakan lain.
4. Agar kamera yang rentan tidak dapat menjadi jalan menuju jaringan internal dan lalu lintasnya dapat dibatasi.

### Bab 12

1. Vulnerability assessment menemukan kerentanan secara luas dan otomatis, penetration testing membuktikan dampak melalui simulasi serangan.
2. Karena konteks seperti eksploitasi aktif, paparan ke internet, dan nilai aset memengaruhi urgensi.
3. Ruang lingkup, izin tertulis, jadwal, metode yang diperbolehkan atau dilarang, kontak darurat, dan penanganan data.
4. Port terhalang firewall atau penyaring sehingga pemindai tidak dapat menentukan statusnya.

### Bab 13

1. Containment menghentikan penyebaran insiden, eradication menghapus akar masalahnya.
2. Untuk rekonstruksi kejadian, akuntabilitas, bukti, dan pembelajaran.
3. 3 salinan, 2 media, 1 offsite. Salinan immutable tidak dapat diubah atau dienkripsi oleh penyerang.
4. Kehilangan data maksimal 4 jam terakhir dapat diterima dan layanan harus pulih maksimal dalam 2 jam.

### Bab 14

1. Mitigasi (pasang MFA), transfer (asuransi atau kontrak), hindari (hentikan layanan berisiko), terima (risiko rendah yang disetujui manajemen).
2. Govern, Identify, Protect, Detect, Respond, Recover. Govern adalah yang baru pada versi 2.0.
3. Karena aset yang tidak diketahui tidak dapat dilindungi, di-patch, atau dipantau.
4. Kebijakan adalah arah dan aturan tingkat tinggi, standar adalah persyaratan spesifik, prosedur adalah langkah rinci pelaksanaan.

### Bab 15

1. Karena ancaman harvest now, decrypt later dan karena migrasi memerlukan waktu bertahun-tahun.
2. Penyerang memakai AI untuk phishing dan penipuan yang meyakinkan, pembela memakainya untuk deteksi anomali dan otomatisasi respons.
3. Isi dan sebagian metadata sulit dilihat sehingga deteksi harus beralih ke endpoint, identitas, dan analitik perilaku.
4. Jawaban bebas, mengacu pada peta jalan di subbab 15.9.

---

## Glosarium

|Istilah|Arti|
|---|---|
|AEAD|Mode enkripsi yang sekaligus menjamin kerahasiaan dan integritas|
|AES|Algoritma enkripsi simetris standar|
|Aset|Sesuatu yang bernilai bagi organisasi dan perlu dilindungi|
|Assume breach|Anggapan bahwa pelanggaran bisa terjadi sehingga sistem dirancang membatasi dampaknya|
|Botnet|Jaringan perangkat terinfeksi yang dikendalikan penyerang|
|Brute force|Mencoba banyak kemungkinan kata sandi atau kunci|
|CA (Certificate Authority)|Pihak tepercaya yang menerbitkan sertifikat digital|
|CIA triad|Confidentiality, Integrity, Availability|
|CIDR|Notasi penulisan blok alamat IP (contoh /24)|
|Crypto agility|Kemampuan mengganti algoritma kriptografi tanpa membongkar sistem|
|CVE|Pengenal unik kerentanan yang diketahui publik|
|CVSS|Sistem penilaian tingkat keparahan kerentanan|
|DDoS|Serangan penolakan layanan terdistribusi|
|Default deny|Semua dilarang kecuali yang diizinkan secara eksplisit|
|Defense in depth|Pertahanan berlapis|
|DMZ|Zona terpisah untuk layanan yang dapat diakses dari internet|
|DNSSEC|Ekstensi DNS untuk menandatangani data demi keaslian dan integritas|
|EDR|Endpoint Detection and Response|
|Eksploit|Cara memanfaatkan kerentanan|
|Enkripsi|Mengubah data menjadi bentuk tak terbaca tanpa kunci|
|Firewall|Penyaring lalu lintas berdasarkan aturan|
|Forward secrecy|Sifat yang membuat kebocoran kunci jangka panjang tidak membuka sesi masa lalu|
|Hash|Sidik jari digital satu arah dari data|
|HMAC|Hash berkunci untuk integritas dan keaslian pesan|
|HSTS|Mekanisme agar browser selalu memakai HTTPS|
|IDS/IPS|Sistem deteksi atau pencegahan intrusi|
|IoC|Indicator of Compromise, tanda bahwa sistem telah dikompromikan|
|IPsec|Rangkaian protokol pengamanan lapisan IP|
|Kerentanan|Kelemahan yang dapat dimanfaatkan ancaman|
|Least privilege|Hak akses seminimal yang dibutuhkan|
|MFA|Autentikasi multi-faktor|
|Mikrosegmentasi|Segmentasi granular hingga level beban kerja atau aplikasi|
|MITM|Man-in-the-Middle, penyerang menyisip di antara dua pihak|
|NAT|Penerjemahan alamat jaringan|
|NGFW|Firewall generasi lanjut|
|Passkeys|Pengganti kata sandi berbasis kunci publik (FIDO2/WebAuthn)|
|PKI|Infrastruktur kunci publik|
|Pasca-kuantum (PQC)|Kriptografi yang dirancang tahan terhadap komputer kuantum|
|RADIUS|Protokol AAA untuk akses jaringan|
|Ransomware|Malware yang mengenkripsi data lalu meminta tebusan|
|RBAC|Kontrol akses berbasis peran|
|Risiko|Gabungan kemungkinan dan dampak kerugian|
|RPO / RTO|Batas kehilangan data / batas waktu pemulihan yang dapat diterima|
|SASE|Gabungan jaringan dan keamanan yang disampaikan dari cloud|
|SBOM|Daftar komponen perangkat lunak dalam sebuah aplikasi|
|Segmentasi|Memecah jaringan menjadi zona terpisah|
|SIEM|Sistem pengumpul dan korelasi log keamanan|
|SOC|Pusat operasi keamanan|
|Spoofing|Pemalsuan identitas atau alamat|
|SSH|Protokol akses jarak jauh yang aman|
|SSO|Single Sign-On|
|TLS|Protokol pengaman komunikasi yang mendasari HTTPS|
|VLAN|Pemisahan jaringan logis pada switch|
|VPN|Terowongan terenkripsi melewati jaringan tak tepercaya|
|WAF|Firewall untuk aplikasi web|
|Zero Trust|Pendekatan yang tidak memberi kepercayaan otomatis, selalu memverifikasi|
|ZTNA|Akses jaringan Zero Trust per aplikasi|

---

## Rujukan dan Bacaan Lanjutan

Informasi yang bersifat cepat berubah (status standar kriptografi pasca-kuantum, pedoman TLS) dicek pada sumber resmi pada Oktober 2026. Selalu periksa sumber aslinya untuk versi terbaru.

### Standar dan Pedoman Resmi

- NIST, Post-Quantum Cryptography Standardization: https://csrc.nist.gov/projects/post-quantum-cryptography/post-quantum-cryptography-standardization
- NIST, FIPS 203 (ML-KEM), FIPS 204 (ML-DSA), FIPS 205 (SLH-DSA).
- NIST, Request for Comments on SP 800-52 Rev. 2 (pedoman TLS): https://csrc.nist.gov/news/2026/tls-comment-on-sp-800-52-rev-2
- NIST, SP 1800-37, Addressing Visibility Challenges with TLS 1.3 within the Enterprise: https://csrc.nist.gov/News/2025/addressing-visibility-challenges-tls-1-3
- NIST SP 800-207, Zero Trust Architecture.
- NIST SP 800-63B, Digital Identity Guidelines (Authentication and Lifecycle Management).
- NIST SP 800-61, Computer Security Incident Handling Guide.
- NIST Cybersecurity Framework 2.0.
- IETF RFC 8446 (TLS 1.3) dan RFC 9325 (rekomendasi penggunaan TLS).
- CIS Critical Security Controls dan CIS Benchmarks.
- ISO/IEC 27001 dan ISO/IEC 27002.
- MITRE ATT&CK: https://attack.mitre.org
- OWASP (Open Worldwide Application Security Project): https://owasp.org
- Badan Siber dan Sandi Negara (BSSN): https://www.bssn.go.id

### Buku

- Kurose dan Ross, Computer Networking: A Top-Down Approach.
- William Stallings, Cryptography and Network Security: Principles and Practice.
- William Stallings, Network Security Essentials.
- Richard Bejtlich, The Practice of Network Security Monitoring.
- Chris Sanders, Practical Packet Analysis.
- Bruce Schneier, Secrets and Lies dan Click Here to Kill Everybody (bacaan pengantar yang ringan).

### Platform Latihan

- Platform latihan interaktif seperti TryHackMe, Hack The Box (jalur pemula), dan OverTheWire.
- Simulator jaringan: Cisco Packet Tracer, GNS3.
- Kompetisi Capture The Flag (CTF) tingkat pemula.

---

Akhir buku. Semoga bermanfaat. Teruslah berlatih di lab Anda sendiri, bertanya, dan mendokumentasikan hasil belajar Anda.