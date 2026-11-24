# Laporan Praktikum Pertemuan 10 — Pemrograman Web 1

Nama  : Muhammad Alvin Abrar
NPM   : 2510010248
Kelas : 3B REG TI BJB

## Percobaan 1 — Navbar Lab

| No | Eksperimen | Pengamatan |
|----|-----------|------------|
| 1 | Class #menuLab dan aria-expanded saat terbuka | Terbuka: class `collapse show`, tombol `aria-expanded="true"`. Tertutup: kembali `collapse` dan `false`. |
| 2 | Hamburger di 1000 px (navbar-expand-lg) | Tidak tampil, menu berderet horizontal karena 1000 px ≥ 992 px. |
| 3 | Perilaku di 800 px | `-md`: menu berderet. `navbar-expand`: selalu berderet, hamburger tidak muncul. Tanpa class expand: selalu terlipat, bahkan di desktop. |
| 4 | data-bs-target salah ketik | Tombol tidak membuka apa pun karena tidak ada elemen ber-id `menu`. Console belum tentu menampilkan galat. |
| 5 | Tanpa JS bundle | Hamburger dan dropdown tidak bereaksi. Tampilan (CSS) tetap ada, perilaku (JS) hilang. |
| 6 | bg-dark tanpa dan dengan data-bs-theme="dark" | Tanpa tema: latar gelap, teks menu gelap, hampir tak terbaca. Dengan tema dark: teks dan ikon hamburger terang. |
| 7 | sticky-top vs fixed-top | `sticky-top`: menempel saat digulir, judul tidak tertutup. `fixed-top`: judul tertutup karena navbar keluar dari aliran dokumen. |

## Percobaan 2 — Buttons & Badges

| No | Eksperimen | Pengamatan |
|----|-----------|------------|
| 1 | Batal–Simpan di 375 px dan 1000 px | 375 px: bertumpuk selebar penuh (`d-grid`). 1000 px: sebaris rata kanan (`d-md-flex justify-content-md-end`). |
| 2 | Elemen nonaktif yang masih bisa difokus | `<button disabled>` dilewati Tab. Link dengan class `disabled` tetapi masih ber-`href` tetap bisa difokus dan diaktifkan dengan Enter. Link tanpa `href` + `aria-disabled="true"` tidak menerima fokus. |
| 3 | Kontras text-bg-warning vs bg-warning | `text-bg-warning`: teks gelap di atas kuning, kontras memenuhi AA. `bg-warning` saja: teks putih bawaan badge, kontras rendah. |
| 4 | Nama tombol Notifikasi | Dengan `visually-hidden`: "Notifikasi 3 notifikasi belum dibaca". Tanpa: "Notifikasi 3". |

## Percobaan 3 — Tipografi

| Class lama | Utilitas pengganti | Tampilan sama? |
|-----------|--------------------|----------------|
| .judul-besar | display-5 text-center | Ya (display sudah bertebal 300) |
| .pembuka | lead text-body-secondary text-center | Ya |
| .label | text-uppercase fw-bold small | Hampir (letter-spacing tidak punya utilitas bawaan) |
| .catatan | small fst-italic | Ya |
| .nim | font-monospace | Ya |

Temuan Lighthouse untuk `<h4>`: Lighthouse melaporkan peringatan "Heading elements are not in a sequentially-descending order" karena heading melompat dari h1 langsung ke h4. Solusinya tetap memakai <h2> dan mengatur ukurannya dengan class h4.

![Sebelum](p3-tipografi/sebelum.png) ![Sesudah](p3-tipografi/sesudah.png)

## Jawaban Pertanyaan Analisis

1. Saat hamburger diklik, JavaScript Bootstrap menambah dan menghapus class `show` pada `#menuLab` dan mengubah `aria-expanded` pada tombol.
2. Tampilan berasal dari CSS, sedangkan interaksi berasal dari JS. Saat tag `<script>` bundle dihapus, CSS tetap termuat sehingga navbar tampil, tetapi tidak ada kode yang mengubah class dan atribut saat diklik.
3. Class `disabled` hanya mengubah tampilan (tampak pudar dan `pointer-events: none`). Link yang masih punya `href` tetap bisa difokus dengan Tab dan diaktifkan dengan Enter, sehingga pengguna keyboard atau pembaca layar bisa menjalankan aksi yang seolah nonaktif.
4. (a) `<h2 class="h5">` menjaga hierarki heading tetap berurutan (h1 → h2), sehingga pembaca layar dan mesin pencari memahami struktur halaman, sedangkan `<h5>` melompati tingkat. (b) Ukuran tampilan tetap bisa diatur lewat class `h5` tanpa mengubah makna struktur.

## Kesimpulan
Dari praktikum ini saya belajar kalau navbar Bootstrap bisa terlipat dan terbuka karena ada JavaScript-nya. Tombol dan badge juga perlu dipilih sesuai fungsinya. Untuk tulisan, kita bisa memakai class Bootstrap tanpa menulis CSS sendiri.
