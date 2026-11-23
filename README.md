# Dilatasi Puisi

Rumah puisi-puisi Angga Nur Salim. Setiap puisi tinggal di ruangnya sendiri, dan tampilannya (CSS) ikut membawa makna puisi, bukan sekadar hiasan.

## Puisi

- **Angga**: tanduk rusa yang tumbuh, patah, lalu kokoh di antara bait
- **Ia Merasa Sendiri**: benteng tanpa pintu; tangis yang membuka pintu
- **Ibu Petarung**: puisi sebagai peta perjalanan keluar dan pulang ke sarang

## Struktur

Seluruh web ada di `index.html`, tanpa build.

- Data puisi ada di array `PUISI`: `bait` (bait → baris), `sela` (ilustrasi setelah bait), `css` (gaya khusus).
- Setiap baris dan kata diberi alamat (`data-g`, `--g`, `--k`, ...) supaya CSS bisa menyentuh bagian mana pun.
- CSS tiap puisi wajib diawali `[data-puisi="slug"]` dan nama `@keyframes` berawalan slug, agar tidak bocor ke puisi lain.
- Tombol **Baca polos** melepas semua gaya khusus.
