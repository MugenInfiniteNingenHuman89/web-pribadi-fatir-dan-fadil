# ⚡ Dokumentasi Teknis & Desain: Cyberpunk / Neo-Brutalism Portfolio — Fadillah Surya Saputra

Dokumentasi ini menjelaskan arsitektur kode, sistem CSS, mesin *Multi-Layer Parallax*, elemen visual, serta pendekatan *tone* dan tema pada portofolio bertema **Cyberpunk / Neo-Brutalism** milik **Fadillah Surya Saputra** (`index.html`), lulusan **SMK Teknik Kendaraan Ringan Otomotif (TKRO)** & Spesialis Diagnostik Kendaraan Modern.

---

## 1. Pendekatan Tone, Tema & Identitas Visual

Portofolio ini memadukan estetika **Cyberpunk High-Tech** dengan struktur tegas **Neo-Brutalism**, dikontekstualisasikan ke dunia **Teknik Otomotif Modern & ECU Diagnostics**:

* **Tone & Persona:** Futuristik, presisi, teknis, dan taktis—merepresentasikan teknisi otomotif modern (`@suryasaputra_auto` / `SURYA.AUTO`) yang menguasai mekanik konvensional maupun pemindaian komputer kendaraan (*OBD-II Scanner*).
* **Palet Warna Neon Kontras Tinggi:**
  * `cyber.black` (`#05050a`) & `cyber.dark` (`#0c0c16`): Latar belakang ruang diagnostik bengkel digital malam yang pekat.
  * `cyber.yellow` (`#fcee0a`): Kuning elektrik khas antarmuka distopia & tanda peringatan bengkel sebagai identitas utama.
  * `cyber.cyan` (`#00f0ff`) & `cyber.pink` (`#ff003c`): Aksen hologram biru sian dan merah neon untuk status telemetri ECU, indikator aktif, serta efek *glitch*.
* **Tipografi Teknis:**
  * **Orbitron (`font-display`):** Font geometris futuristik untuk tajuk utama dan identitas *garage*.
  * **JetBrains Mono (`font-mono`):** Font *monospace* presisi tinggi untuk log diagnostik OBD-II, metrik keahlian, dan spesifikasi alat ukur.
  * **Space Grotesk (`font-sans`):** Font modern yang bersih untuk keterbacaan deskripsi pengalaman PKL dan proyek otomotif.

---

## 2. Struktur Arsitektur File (`index.html`)

1. **`<head>` & Konfigurasi Tailwind:** Memuat Tailwind CSS CDN, Google Fonts (`Orbitron`, `JetBrains Mono`, `Space Grotesk`), serta konfigurasi warna kustom `cyber.*`.
2. **Lapisan Atmosfer & Parallax Latar (`fixed`):**
   * `.crt-overlay`: Garis pindai monitor diagnostik (*CRT Scanlines*) di seluruh layar.
   * `#parallax-grid` & `#parallax-orb-1..3`: Jaring perspektif *cyber-grid* dan pendaran cahaya neon yang merespons *scroll* dan gerakan kursor.
3. **Header Navigasi (`<header>`):** Identitas monogram **FSS** (`SURYA.AUTO`), tautan navigasi 5 bagian (`01.ABOUT`, `02.ARSENAL`, `03.BUILDS`, `04.PKL_LOG`, `05.CONNECT`), serta tombol sakelar **`CRT: ON/OFF`**.
4. **Konten Utama (`<main>`):**
   * **`#hero`:** Judul utama **FADILLAH SURYA SAPUTRA** dengan efek *Glitch*, terminal perintah otomatis (`scan --obd2`, `tuneup --efi-1.5L`), tombol aksi bersudut tajam (*chamfered*), dan kartu ID **MECH_PASS // #TKRO-2077** lengkap dengan ilustrasi vektor mesin piston & gelombang telemetri ECU.
   * **`#about` (01 // Diagnostic Profile):** Profil lulusan SMK TKRO Surakarta serta 4 kartu metrik bengkel (*50+ Unit Servis & Tune-Up*, *100% Akurasi Diagnosa OBD-II*, *6 Bln PKL Bengkel Resmi*, *10+ Proyek Kelistrikan & Mod*).
   * **`#skills` (02 // Automotive Arsenal):** Matriks kompetensi teknis terbagi dalam 3 modul utama: *Engine & Powertrain*, *Electrical & Diagnostics*, serta *Chassis, Brake & Tools*.
   * **`#projects` (03 // Deployed Builds):** Galeri proyek otomotif dengan filter kategori (`ALL_BUILDS`, `ENGINE_TUNEUP`, `ELECTRICAL_ECU`, `CHASSIS_MOD`) dan modal inspeksi spesifikasi teknis.
   * **`#experience` (04 // Service History):** Lini masa pengalaman **Praktik Kerja Lapangan (PKL)** di bengkel resmi/spesialis dan **Tim Teknis LKS Otomotif** di sekolah.
   * **`#contact` (05 // Direct Uplink):** Formulir komunikasi untuk rekrutmen mekanik, kolaborasi bengkel, maupun konsultasi diagnostik.

---

## 3. Rincian Bagian CSS & Fungsinya

| Selector CSS | Kegunaan & Efek Visual |
| :--- | :--- |
| `.crt-overlay` | Membuat garis horizontal tipis berulang (`repeating-linear-gradient`) menyerupai layar monitor diagnostik CRT klasik. |
| `.cyber-grid` | Membentuk pola kisi koordinat latar belakang menggunakan `linear-gradient` horizontal dan vertikal. |
| `.cyber-chamfer` | Menggunakan properti `clip-path: polygon(...)` untuk memotong sudut kotak menjadi diagonal khas antarmuka sci-fi. |
| `.brutal-card` / `.brutal-card-pink` | Kartu bergaya *Neo-Brutalism* dengan garis tepi tebal (`border: 2px`) dan bayangan blok solid tanpa blur (`box-shadow: 6px 6px 0px`). |
| `.glitch-text` | Efek distorsi teks berlapis menggunakan pseudo-elemen `::before` dan `::after` dengan pergeseran warna sian dan merah neon. |
| `.parallax-layer` | Mengaktifkan akselerasi perangkat keras GPU (`will-change: transform`, `translate3d`) agar animasi *parallax* berjalan mulus di 60fps. |

---

## 4. Elemen HTML & Interaktivitas JavaScript

* **Elemen Utama:** Menggunakan ilustrasi vektor SVG piston mesin & gelombang sinyal ECU, kartu *chamfered*, bilah persentase kompetensi otomotif, lini masa pengalaman PKL, dan formulir terminal bergaya CLI.
* **Mesin JavaScript (`<script>`):**
  * **Multi-Layer Parallax & 3D Tilt (`animateCyberParallax`):** Menggerakkan *grid*, cahaya neon, *watermark* latar belakang (`TKRO // OBD-II`, `SURYA SAPUTRA`), serta memberikan efek kemiringan 3D pada kartu ID mekanik berdasarkan posisi *scroll* dan kursor mouse.
  * **Terminal Typewriter (`runTerminalTyping`):** Mengetik perintah simulasi diagnostik bengkel secara otomatis di bagian *Hero*.
  * **Build Filter & Technical Specs Modal (`openBuildModal`):** Menyaring proyek berdasarkan kategori otomotif dan membuka modal pop-up berisi rincian pengerjaan, alat ukur yang digunakan, serta hasil *Quality Control (QC)*.