# Pertemuan 3 — Analisis Desain Responsif

**Sub-CPMK-1.3 · Asesmen Desain Responsif**

---

## 📋 Deskripsi

Asesmen ini mengevaluasi kemampuan mahasiswa dalam **menganalisis dan memperbaiki masalah desain responsif** pada halaman web nyata. Mahasiswa akan mengidentifikasi isu layout, elemen yang tumpang tindih, dan navigasi yang tidak intuitif, lalu mengimplementasikan solusi menggunakan teknik CSS modern.

---

## 🗂️ Struktur Proyek

```
.
├── index.html          ← Halaman BERMASALAH (tugas analisis mahasiswa)
├── css/
│   └── style.css       ← CSS bermasalah (tanpa media query, unit fixed px)
├── solution/
│   ├── index.html      ← Halaman SOLUSI (referensi setelah pengerjaan)
│   └── css/
│       └── style.css   ← CSS solusi (media query, flexbox, grid, unit relatif)
└── README.md
```

---

## 🎯 Tujuan Pembelajaran

Setelah menyelesaikan asesmen ini, mahasiswa mampu:

1. **Mengidentifikasi** masalah desain responsif menggunakan DevTools browser.
2. **Menerapkan** `meta viewport` yang benar untuk halaman mobile.
3. **Menggunakan** unit fleksibel (`%`, `rem`, `em`, `vw`, `clamp()`) sebagai pengganti `px` tetap.
4. **Membangun** navigasi responsif dengan hamburger menu menggunakan HTML, CSS, dan JavaScript.
5. **Mengimplementasikan** layout adaptif dengan **CSS Flexbox** dan **CSS Grid**.
6. **Menulis** media queries untuk breakpoint mobile (≤480px), tablet (≤768px), dan desktop.
7. **Membuat** gambar responsif dengan `width: 100%; height: auto`.

---

## ❌ Masalah yang Ada di `index.html` + `css/style.css`

| # | Masalah | Lokasi |
|---|---------|--------|
| 1 | `<meta viewport>` tidak ada | `index.html` `<head>` |
| 2 | Atribut `lang` tidak ada pada `<html>` | `index.html` |
| 3 | Lebar container tetap `1200px` (bukan `max-width`) | `css/style.css` `.container` |
| 4 | Navbar `width: 1200px` overflow di mobile | `css/style.css` `.navbar` |
| 5 | Tidak ada tombol hamburger untuk mobile | `index.html`, `css/style.css` |
| 6 | Font-size menggunakan `px` tetap (bukan `rem`/`clamp()`) | `css/style.css` |
| 7 | Gambar `width: 500px; height: 350px` — tidak responsif | `css/style.css` `.about-image img` |
| 8 | Layout About menggunakan `float` dan lebar `px` tetap | `css/style.css` `.about-grid` |
| 9 | Kartu layanan `width: 360px` tetap — meluap di mobile | `css/style.css` `.service-card` |
| 10 | Grid tim menggunakan `flex` tanpa `flex-wrap` | `css/style.css` `.team-grid` |
| 11 | Form kontak `width: 600px` — meluap di layar kecil | `css/style.css` `.contact-form` |
| 12 | Label form tidak diasosiasikan dengan input (`for`/`id`) | `index.html` |
| 13 | Footer tanpa `flex-wrap` — kolom tidak turun ke baris baru | `css/style.css` `.footer-grid` |
| 14 | Badge posisi absolut menimpa konten di mobile | `css/style.css` `.badge` |
| 15 | Tombol tidak punya ukuran minimum untuk touch target | `css/style.css` `.btn-primary` |
| 16 | **Tidak ada satu pun media query** di seluruh file | `css/style.css` |

---

## ✅ Teknik yang Diimplementasikan di `solution/`

### Meta & HTML
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- Atribut `lang="id"` dan `alt` deskriptif pada gambar

### Unit Fleksibel
- `max-width` + `width: 100%` untuk container dan form
- `rem` / `em` untuk font-size dan spacing
- `clamp(min, preferred, max)` untuk heading yang skala otomatis

### Layout
- **Flexbox** dengan `flex-wrap: wrap` untuk About dan Footer
- **CSS Grid** dengan `repeat(auto-fit, minmax(..., 1fr))` untuk Layanan dan Tim
- `aspect-ratio` untuk gambar avatar tim

### Gambar Responsif
```css
img {
  width: 100%;
  height: auto;
}
```

### Navigasi Mobile
- Tombol hamburger dengan animasi 3-garis → silang
- ARIA: `aria-label`, `aria-expanded`, `aria-controls`
- Menu tertutup otomatis saat tautan diklik

### Media Queries
```css
/* Tablet */
@media (max-width: 768px) { ... }

/* Mobile */
@media (max-width: 480px) { ... }

/* Print */
@media print { ... }
```

---

## 📝 Tugas Mahasiswa

1. Buka `index.html` di browser dan aktifkan **Device Toolbar** (F12 → Ctrl+Shift+M).
2. Simulasikan berbagai ukuran layar: **Mobile (375px)**, **Tablet (768px)**, **Desktop (1280px)**.
3. Catat semua masalah responsivitas yang Anda temukan dalam laporan analisis.
4. Perbaiki `index.html` dan `css/style.css` tanpa melihat folder `solution/` terlebih dahulu.
5. Bandingkan hasil perbaikan Anda dengan `solution/index.html` setelah selesai.

---

## 🔧 Cara Menjalankan

Cukup buka file HTML langsung di browser — tidak diperlukan server:

```bash
# Buka halaman bermasalah
open index.html

# Buka halaman solusi
open solution/index.html
```

Atau gunakan ekstensi **Live Server** di VS Code untuk hot-reload.

---

## 📚 Referensi

- [MDN — Responsive Design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)
- [MDN — Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)
- [MDN — CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout)
- [MDN — Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout)
- [web.dev — Responsive Images](https://web.dev/articles/responsive-images)

