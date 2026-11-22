# Anisa — Navy Ice

Template undangan pernikahan digital satu halaman (statis, tanpa backend) bertema **navy & putih es**: tirai cover yang terbelah saat dibuka, hero layar penuh, ayat pembuka, bingkai mempelai menyatu/pisah, kisah, kalender + hitung mundur, kartu akad & resepsi, peta + QR lokasi, galeri, amplop digital (DANA), doa restu, dan RSVP ucapan.

Semua nama, tanggal, alamat, nomor, dan foto di dalam repo ini adalah **data contoh fiktif** untuk keperluan demo template — tinggal ganti dengan data kamu sendiri.

## Isi Repo

| File / Folder | Fungsi |
|---|---|
| `index.html` | Halaman undangan (semua isi & logika ada di sini) |
| `owner.html` | Halaman owner untuk membuat link personal per tamu + kirim via WhatsApp |
| `foto/` | Foto cover, couple, avatar mempelai, dan galeri (`g1`–`g9`) |
| `assets/cover.jpg` | Foto latar cover & hero |
| `audio/` | Musik latar undangan |
| `qr-lokasi.png` | QR menuju Google Maps lokasi acara contoh |
| `qr-undangan.png` | QR untuk membagikan undangan (isi contoh — buat ulang dengan URL kamu) |

## Cara Pakai

1. **Deploy dulu** folder ini ke hosting statis apa pun (GitHub Pages, Netlify, Vercel, Cloudflare Pages, atau hosting biasa) — atau buka langsung `index.html` untuk melihat tampilannya.
2. **Ganti data acara** di `index.html` — cari dan ubah teks berikut:
   - Nama mempelai (judul, cover, hero, bagian *The Couple*, penutup, footer) — contoh saat ini: **Alya Maharani & Rangga Aditya**.
   - Nama orang tua di bagian *The Couple*.
   - Tanggal acara: teks tampil (`Sabtu, 18 September 2027`), target hitung mundur `CONFIG.target`, kalender mini (blok `calendar` di script — sesuaikan jumlah hari, hari pertama, dan tanggal yang dilingkari), serta tanggal pada link Google Calendar.
   - Venue & alamat: teks kartu acara, `CONFIG.addr`, query Google Maps pada iframe peta dan semua tombol peta, serta link Google Calendar.
   - Nomor amplop digital (kartu DANA di bagian *Wedding Gift* + nomor pada fungsi tombol "Salin Nomor").
   - Teks kisah cinta di bagian *Kisah Kami*.
3. **Ganti foto** dengan menimpa file di `foto/` dan `assets/cover.jpg` (pertahankan nama filenya agar tidak perlu mengubah kode):
   - `assets/cover.jpg` — latar cover & hero (potret, subjek di tengah).
   - `foto/g9.jpeg` — foto berdua bawaan untuk bingkai menyatu.
   - `foto/ava-alya.jpeg` / `foto/ava-rangga.jpeg` — foto sendiri-sendiri untuk bingkai pisah.
   - `foto/couple.jpg`, `foto/cover.jpeg`, `foto/g1–g9.jpeg` — galeri & pilihan foto alternatif dari halaman owner.
4. **Buat ulang QR** (`qr-lokasi.png` & `qr-undangan.png`) dengan URL lokasi dan alamat undangan kamu sendiri, misalnya lewat layanan pembuat QR gratis, lalu timpa kedua file ini.
5. **Kirim undangan** lewat `owner.html` (lihat bagian berikut).

## Halaman Owner (`owner.html`)

- **Kode akses / PIN default: `admin123`** — ganti dengan mengedit baris `const PIN="admin123";` di `owner.html`. Ingat: PIN ini hanya gerbang tampilan di browser (bukan keamanan server), jadi jangan pakai kata sandi penting.
- Fitur di dalamnya:
  - **Daftar tamu** — satu nama per baris; tambahkan nomor WA setelah tanda `|` (mis. `Bapak Andi & Keluarga | 081234567890`) agar tombol kirim langsung menuju nomor orangnya.
  - **Template pesan WhatsApp** — satu link saja dengan label `Detail undangan:`; placeholder `{nama}`, `{short}` (link undangan), `{link}` (cadangan).
  - **Tata letak foto mempelai** — *Menyatu* (satu bingkai foto berdua) atau *Pisah* (dua bingkai), plus pilihan foto berdua. Pilihan ini ikut terbawa di link tiap tamu lewat parameter `?layout=` & `?foto=`, jadi tampilan yang diterima tamu sesuai pilihan owner.
  - Link tamu dibuat otomatis dari alamat folder tempat file ini di-hosting — tidak ada domain yang dikunci di dalam kode.

## RSVP & Ucapan — Mode Demo Lokal

Secara bawaan template ini berjalan dalam **mode demo**: `CONFIG.scriptURL` di `index.html` kosong, sehingga ucapan tamu **tersimpan lokal di browser masing-masing tamu** (localStorage) dan tidak terkumpul ke satu tempat. Ucapan contoh tampil dari `CONFIG.demoWishes`.

Kalau ingin ucapan terkumpul betulan, isi `CONFIG.scriptURL` dengan URL Web App Google Apps Script milikmu sendiri (endpoint yang menerima POST JSON `{name, status, message}` dan membalas GET dengan array JSON ucapan) — form akan otomatis beralih memakai endpoint itu.

## Catatan Lain

- Musik latar memakai file di `audio/`; ganti filenya untuk mengganti lagu (perhatikan hak cipta lagu pilihanmu).
- Undangan mendukung nama tamu personal lewat parameter `?to=Nama+Tamu` pada link.
- Tidak ada pelacakan, tidak ada panggilan ke server pihak ketiga selain font Google, peta Google, dan (opsional) endpoint RSVP milikmu sendiri.

## Kredit

Design by **N'Zey** — Instagram [instagram.com/iamkizakixd](https://instagram.com/iamkizakixd) · Telegram [t.me/kizakixd](https://t.me/kizakixd)

Foto contoh pada template ini adalah foto stok pasangan model dari fotografer, dipakai sebagai placeholder — ganti dengan foto kamu sendiri sebelum undangan disebar.
