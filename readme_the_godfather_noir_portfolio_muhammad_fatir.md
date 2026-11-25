# 🎩 Dokumentasi Teknis & Desain: The Godfather Noir Portfolio — Muhammad Fatir

Dokumentasi ini membedah secara lengkap arsitektur kode, sistem CSS, mesin *Multi-Layer Parallax*, elemen visual, serta pendekatan *tone* dan tema pada portofolio bertema **Monochrome Noir / The Godfather** milik **Muhammad Fatir** (`index.html`).

---

## 1. Pendekatan Tone, Tema & Identitas Visual
Portofolio ini mengadaptasi atmosfer film kriminal klasik era 1970-an (*Film Noir* & *The Godfather*) ke dalam wujud **Arsip Rahasia Kepolisian / Berkas Inteligensi**:
- **Tone & Persona:** Tenang, berwibawa, misterius, dan taktis (*"The Architect of Digital Syndicates"*). Setiap istilah teknis dibungkus dalam metafora organisasi *La Famiglia* dan kode etik *Omertà* (kerahasiaan & integritas kode).
- **Palet Warna Monokrom Kontras Tinggi:**
  - `noir.pitch` (`#080808`) & `noir.deep` (`#111111`): Dominasi hitam pekat menciptakan ruang bayangan dramatis (*chiaroscuro*).
  - `noir.ivory` (`#e8e4d9`) & `noir.paper` (`#d6d0c0`): Putih gading pudar menyerupai kertas arsip tua dan kemeja tuksedo klasik.
  - `noir.blood` (`#7a0a0a`): Aksen tunggal merah darah gelap untuk stempel *CONFIDENTIAL*, cap lilin (*wax seal*), dan mawar saku (*boutonnière*).
- **Tipografi Tiga Lapis:**
  - **Cinzel (`font-godfather`):** Font *serif* klasik berkarakter tajam untuk judul utama dan nama **MUHAMMAD FATIR**.
  - **Playfair Display (`font-editorial`):** Font bergaya tajuk surat kabar vintage untuk kutipan (*blockquote*) dan sub-judul dramatis.
  - **Courier Prime (`font-typewriter`):** Font mesin tik khas dokumen investigasi, laporan kasus, dan formulir telegram.

---

## 2. Struktur Arsitektur File (`index.html`)
Seluruh aplikasi dibangun dalam satu file HTML mandiri (*Single-File Architecture*) agar ringan, cepat dimuat, dan bebas masalah *dependency*:

1. **`<head>` & Konfigurasi Desain:**
   - Memuat **Tailwind CSS CDN** beserta objek `tailwind.config` kustom untuk warna `noir.*` dan keluarga font.
   - Memuat Google Fonts (`Cinzel`, `Playfair Display`, `Courier Prime`).
   - Blok `<style>` internal untuk efek atmosferik khusus yang tidak tersedia secara bawaan di Tailwind.
2. **Lapisan Latar Belakang Atmosferik (`fixed`):**
   - `#film-grain`: Tekstur bintik seluloid film klasik di atas seluruh layar (`z-index: 9998`, `pointer-events: none`).
   - `#parallax-blinds` & `.noir-smoke`: Bayangan tirai *venetian blinds* diagonal dan kabut asap monokrom yang bergerak dinamis.
3. **Header Navigasi Arsip (`<header>`):**
   - Logo monogram **MF** lengkap dengan garis benang dalang (*puppet strings*), navigasi 4 bab (*I. The Don*, *II. The Syndicate*, *III. Operations*, *IV. Consigliere*), serta tombol sakelar **`NOIR FX: ON/OFF`**.
4. **Konten Utama (`<main>`):**
   - **`#hero`:** Layar pembuka dengan garis *puppet strings*, kutipan ikonik, teks mesin tik otomatis, dan kartu **Mugshot Dossier** interaktif dengan siluet topi Fedora.
   - **`#don` (Section I):** Lembar dokumen kertas perkamen (*Parchment Sheet*) berisi profil intelijen Muhammad Fatir dan 3 pilar prinsip kerja (*Loyalty to Clean Code*, *Silent Execution*, *Ironclad Security*).
   - **`#syndicate` (Section II):** Hierarki kemampuan teknis yang dibagi menjadi tiga tingkatan komando: *The Consigliere* (Arsitektur & AI), *The Caporegimes* (Full-Stack Web), dan *The Enforcers* (IoT & Keamanan).
   - **`#operations` (Section III):** Ruang barang bukti (*Evidence Room*) berisi 4 studi kasus (*Exhibit A–D*) dengan filter kategori dan modal inspeksi berkas.
   - **`#consigliere` (Section IV):** Formulir pengiriman **Telegram Rahasia** lengkap dengan generator nomor referensi dan stempel konfirmasi *DISPATCHED*.
5. **Modal Dossier (`#dossier-modal`) & Mesin JavaScript (`<script>`):**
   - Pop-up kertas arsip untuk membaca detail teknis setiap proyek tanpa mengganggu halaman utama.

---

## 3. Rincian Bagian CSS & Fungsinya
Berikut adalah *class* dan aturan CSS kustom di dalam `<style>` beserta peran masing-masing:

| Selector CSS | Kegunaan & Efek Visual |
| :--- | :--- |
| `.film-grain` | Menciptakan tekstur bintik film klasik menggunakan `radial-gradient` berulang dengan `opacity: 0.065` dan `pointer-events: none` agar tidak menghalangi klik pengguna. |
| `.venetian-blinds` | Menggunakan `repeating-linear-gradient(-24deg, ...)` untuk membentuk bayangan garis cahaya khas jendela kantor detektif film noir. |
| `.noir-fx-off` | Kelas utilitas untuk mematikan efek *film grain* dan *venetian blinds* saat tombol `NOIR FX: OFF` ditekan. |
| `.dossier-card` | Kartu berkas gelap dengan gradasi halus `#121212` ke `#0b0b0b`, garis tepi `#2e2e2e`, dan bayangan dalam (*inset shadow*) yang menyala lembut saat di-hover. |
| `.parchment-sheet` | Mensimulasikan kertas arsip fisik berwarna gading (`#e8e4d9`) dengan tekstur titik halus dan teks gelap (`#111111`) untuk kontras maksimal. |
| `.stamp-confidential` | Membuat stempel tinta merah miring (`transform: rotate(-6deg)`) dengan garis tepi ganda menyerupai cap resmi dokumen rahasia. |
| `.wax-seal` | Membentuk cap lilin merah 3D melingkar menggunakan `radial-gradient` dan berlapis `box-shadow` dalam/luar. |
| `.newspaper-rule` | Garis pemisah antar bagian bertema surat kabar klasik (kombinasi `border-top: 2px` dan `border-bottom: 1px`). |
| `.parallax-layer` | Mengaktifkan akselerasi perangkat keras GPU (`will-change: transform` dan `translate3d`) agar animasi *parallax* berjalan mulus di 60fps. |
| `@keyframes smokeDrift` | Menggerakkan gumpalan asap monokrom latar belakang secara perlahan dengan siklus 14 detik. |

---

## 4. Elemen HTML & Grafis SVG yang Dipakai
- **Custom Inline SVG:**
  - *Puppet-Strings Bar:* Garis kontrol dalang ikonik khas poster *The Godfather* yang diletakkan tepat di atas nama **MUHAMMAD FATIR** dan ikon navigasi.
  - *Noir Reticle / Crosshair:* Bidikan garis putus-putus melingkar dengan titik pusat merah gelap di latar belakang *Hero*.
  - *Noir Fedora Silhouette Portrait:* Ilustrasi vektor siluet pria bertopi Fedora, jas tuksedo, dasi kupu-kupu, mawar merah di kerah jas, dan garis pengukur tinggi badan ala foto tahanan (*police mugshot*).
- **Elemen Semantik HTML5:** Menggunakan `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<blockquote>`, dan `<footer>` untuk keterbacaan struktur dokumen yang rapi.

---

## 5. Kegunaan Kode JavaScript (`<script>`)
Seluruh interaktivitas ditulis menggunakan **Vanilla JavaScript** tanpa library eksternal:
1. **Multi-Layer Parallax Engine (`animateNoirParallax`):**
   - Menggunakan `requestAnimationFrame` dan interpolasi halus (*linear interpolation / lerp* dengan faktor `0.06`) untuk menggabungkan posisi `window.scrollY` dan koordinat kursor (`mousemove`).
   - Menggerakkan elemen ber atribut `data-parallax-speed` dan `data-mouse-factor` pada kecepatan berbeda (lapisan belakang, tengah, dan depan).
   - Memberikan efek kemiringan 3D (*3D Perspective Tilt*) pada kartu `#hero-dossier-card` saat kursor bergerak di layar desktop.
2. **Typewriter Archive Effect (`runTypewriter`):** Mengetik dan menghapus kutipan filosofi kode secara bergantian di bawah kutipan utama.
3. **Noir FX Controller:** Mengatur nyala/mati lapisan *film grain* dan *venetian blinds* demi kenyamanan mata pengguna.
4. **Evidence Filter System:** Menyaring kartu studi kasus (`ALL`, `WEB`, `IOT`, `AI`) berdasarkan atribut `data-category`.
5. **Telegram Dispatch & Clipboard:** Memvalidasi formulir, membangkitkan kode referensi unik (`WIRE-1972-XXXX`), menampilkan stempel *DISPATCHED*, serta menyalin alamat komunikasi ke *clipboard*.
6. **Dossier Modal Controller (`openDossierModal`):** Mengisi dan menampilkan pop-up rincian teknis proyek secara dinamis.