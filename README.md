# Dilatasi Puisi

Rumah puisi-puisi Angga Nur Salim. Setiap puisi tinggal di ruangnya sendiri, dan tampilannya (CSS) ikut membawa makna puisi, bukan sekadar hiasan.

Live: https://dilatasi-puisi.vercel.app

## Puisi

| # | Puisi | Bentuk |
|---|---|---|
| 1 | **Angga** | Tanduk rusa tumbuh di antara bait (tunas → tipis → patah → kokoh); huruf menebal baris demi baris |
| 2 | **Ia Merasa Sendiri** | Benteng tanpa pintu: bingkai tertutup yang menggelap; tetes tangis membuka pintu |
| 3 | **Ibu Petarung** | Peta perjalanan: jarak dari tepi = jarak dari sarang; dilema bercabang |
| 4 | **Salah Arti** | Arah yang salah dibaca: baris "paling lurus" miring, hanyut, jatuh ke lubang |
| 5 | **Cinta Sekecil Mikroba** | Warna lawan abu-abu: sindiran makin abu-abu, hanya "penuh warna" yang berwarna |
| 6 | **Sabar Saja Dulu** | Dapur dan meja tulis: kalimat gosong, kantuk, kursor yang belum selesai |
| 7 | **Rahmat Allah Mudah** | Debu yang memuai menjadi gurun saat digulir |
| 8 | **Berandai-andai** | Kuda waktu: kaki dari coretan hitungan 6-3-3, satu kaki terangkat; angan pucat |
| 9 | **Batu yang Lelah** | Kebalikan "Angga": huruf menipis bait demi bait; batu pecah jadi kerikil |
| 10 | **Apa Salah Berharap?** | Kata tergigit, kata terbalik, kolom jawaban yang dibiarkan kosong |
| 11 | **Kejatuhan** | Jawaban untuk puisi sebelumnya: baris luka tersusun melengkung seperti senyum |
| 12 | **Berita Lucu** | Tawa melompat → kutipan berita → kemarahan merah gelap |

## Struktur

Seluruh web ada di `index.html`, tanpa build dan tanpa dependensi (font dari Google Fonts).

Data puisi ada di array `PUISI`. Setiap puisi:

| Field | Isi |
|---|---|
| `slug`, `judul`, `tanggal`, `siap` | identitas; `siap: false` tampil abu-abu di daftar |
| `bait` | array bait → array baris (string) |
| `sela` | opsional: `{ indeksBait: { label, svg } }`, ilustrasi yang muncul **setelah** bait tersebut |
| `catatan` | opsional: satu kalimat kecil di bawah puisi |
| `css` | gaya khusus puisi ini |

Setiap bait, baris, dan kata diberi alamat supaya CSS bisa menyentuh bagian mana pun:

- `data-b` / `--b` = indeks bait
- `data-g` / `--g` = indeks baris di seluruh puisi
- `--l` = indeks baris di dalam bait
- `--k` = indeks kata di dalam baris (kata bisa dipilih dengan `.kata:nth-of-type(n)`)

## Aturan CSS puisi

- Setiap aturan wajib diawali `[data-puisi="slug"]` dan setiap nama `@keyframes` wajib berawalan `slug-`, supaya tidak bocor ke puisi lain. Pemeriksaan otomatis di konsol akan memberi peringatan kalau dilanggar.
- Distorsi dijaga sekitar 40%: terasa, tapi tetap mudah dibaca.
- Gerak wajib mati di `prefers-reduced-motion`; efek berbasis guliran harus tetap bermakna dalam keadaan akhirnya (Safari belum mendukung scroll-driven animation).
- Tidak ada efek pada kata "Allah" atau pada kata ibadah.
- Tombol **Baca polos** melepas semua gaya khusus dan ilustrasi.
