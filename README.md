# Panduan Mulai di make.fun — dari Daftar sampai Klaim USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/rujakcungur/panduan-make-fun/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/rujakcungur/panduan-make-fun/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun adalah platform tempat kamu dan agen coding AI milikmu membangun software untuk bounty berhadiah uang. Setiap bounty punya tugas yang jelas, deadline, dan hadiah USDC yang sudah dikunci di escrow on-chain di Solana — jadi hadiahnya benar-benar ada sebelum kamu mulai bekerja. Kamu membangun entry bersama agen AI-mu (Claude Code, Codex, Cursor, Copilot, Gemini CLI, dan lain-lain), mengirim repo GitHub publik atau source bundle beserta transkrip sesi agenmu, lalu entry-mu melewati pemeriksaan otomatis, dinilai, dan kalau masuk peringkat atas, kamu bisa klaim USDC langsung ke wallet Solana-mu.

> **Mulai dari sini:** daftar lewat link referral ini — [https://make.fun/r/7r7xnqjd](https://make.fun/r/7r7xnqjd) (kode referral: `7r7xnqjd`). Gratis, dan pendaftaranmu tercatat sebagai dukungan untuk panduan ini.

## Ringkasan cepat

Untuk yang ingin langsung jalan, alurnya sesederhana ini:

1. Daftar gratis di make.fun, tautkan GitHub + wallet Solana.
2. Pilih bounty gratis di board, unduh kit-nya, baca `RULES.txt`.
3. Login CLI kit ke akunmu, lalu bangun entry di sesi agen baru.
4. Bundle transkrip, jalankan `check`, lalu submit sebelum deadline.
5. Pantau status; kalau menang, klaim USDC ke wallet Solana-mu.

Penjelasan lengkap tiap langkah ada di bawah.

## Yang kamu butuhkan

Sebelum mulai, siapkan empat hal ini:

- **Agen coding AI** — misalnya Claude Code, Codex, Cursor, GitHub Copilot, atau Gemini CLI. Agen inilah yang akan membantumu menulis kode entry.
- **Akun GitHub** — dipakai untuk login, menautkan profil, dan menerbitkan repo entry-mu.
- **Node.js 22** — dibutuhkan untuk menjalankan CLI dari kit bounty.
- **Wallet Solana** — tempat hadiah USDC dikirim saat kamu menang. Kalau belum punya, buat dulu wallet yang mendukung jaringan Solana; menautkannya bisa dilakukan kapan saja sebelum kamu perlu mengklaim hadiah, tapi paling praktis sejak awal.

Tidak perlu modal uang: banyak bounty yang gratis untuk diikuti (cara membedakannya ada di Langkah 2 dan bagian tips). Yang benar-benar wajib sejak awal hanyalah agen AI, akun GitHub, dan Node.js 22.

## Langkah 1 — Daftar akun make.fun

Buka [make.fun](https://make.fun) dan daftar secara gratis. Kamu bisa masuk dengan GitHub, Google, Apple, Discord, atau wallet Solana. Setelah akun jadi, lengkapi profilmu:

1. Tautkan akun **GitHub** — dibutuhkan karena entry dikirim sebagai repo GitHub (atau dikaitkan dengannya).
2. Tautkan **wallet Solana** — ke sinilah hadiah USDC akan diklaim nanti.

Kedua tautan ini cukup dilakukan sekali di halaman profil.

## Langkah 2 — Pilih bounty di board

Buka papan bounty di make.fun dan perhatikan empat hal pada setiap bounty sebelum memutuskan:

- **Hadiah** — berapa USDC dan untuk berapa peringkat teratas.
- **Aturan** — tugasnya apa dan deliverable-nya apa.
- **Deadline** — kapan entry terakhir diterima.
- **Biaya masuk** — apakah gratis atau ada entry fee. Informasi ini tercantum jelas di halaman bounty; kalau kolom biayanya nol/kosong, bounty itu gratis. Kalau mau mulai tanpa biaya sama sekali, pilih yang gratis.

Pilih bounty yang tugasnya masuk akal untuk diselesaikan sebelum deadline-nya. Untuk percobaan pertama, bounty dengan tugas kecil dan deadline longgar jauh lebih ramah daripada bounty besar yang mepet.

## Langkah 3 — Unduh kit bounty

Setiap bounty menyediakan kit berisi aturan lengkap dan CLI. Unduh dan ekstrak dengan perintah ini (ganti `<slug>` dengan slug bounty pilihanmu):

```bash
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
```

Di dalam kit:

- `RULES.txt` — aturan lengkap bounty. **Baca file ini sampai habis sebelum mulai membangun.**
- `cli/makefun.mjs` — CLI yang dipakai untuk login, bundle, check, dan submit. CLI ini berjalan di Node 22.

## Langkah 4 — Hubungkan CLI ke akunmu

Dari dalam folder kit, jalankan login sekali saja:

```bash
node cli/makefun.mjs login
```

Ikuti petunjuknya sampai CLI terhubung ke akun make.fun milikmu. Langkah ini hanya perlu dilakukan satu kali; setelah itu CLI mengingat koneksinya.

## Langkah 5 — Bangun entry-mu

Ini bagian terpenting, jadi perhatikan urutannya:

1. Buat repo baru untuk entry-mu.
2. Mulai **sesi agen yang benar-benar baru setelah bounty-nya dibuka**. Transkrip sesi inilah yang nanti dikirim sebagai bukti proses pembangunan, jadi jangan memakai sesi lama dari sebelum bounty dibuka.
3. Bangun entry-mu bersama agenmu sesuai `RULES.txt`.
4. Commit hasil kerjamu secara berkala. Commit awal yang cepat membuat riwayat repo-mu jelas dan memudahkan kalau kamu perlu mengulang dari titik yang aman.
5. Sertakan lisensi open source yang disetujui OSI — **MIT** adalah pilihan paling sederhana — di repo-mu.

## Langkah 6 — Bundle, check, submit

Setelah entry jadi, bungkus transkrip sesimu:

```bash
node cli/makefun.mjs bundle
```

Lalu jalankan pemeriksaan pra-submit untuk memastikan tidak ada syarat yang kurang:

```bash
node cli/makefun.mjs check
```

Kalau check lolos, kirim entry-mu lewat perintah submit dari CLI kit (opsi persisnya mengikuti `RULES.txt` bounty tersebut). Simpan output submit dan **ID submission** yang kamu terima di tempat yang aman — ID itu yang kamu pakai untuk melacak status entry-mu, dan tanpanya kamu akan kesulitan membuktikan entry mana yang milikmu.

## Langkah 7 — Pantau status dan klaim hadiah

Setelah submit, pantau status entry-mu lewat CLI atau halaman bounty:

- Kalau ada check yang **ditolak**, perbaiki penyebabnya lalu submit ulang **sebelum deadline**. Entry terakhir yang masuk adalah yang dihitung, jadi jangan takut memperbaiki.
- Saat hasil diumumkan, peringkat atas bisa **klaim hadiah USDC** dari profil — hadiah dikirim ke wallet Solana yang sudah kamu tautkan.

## Tips supaya entry tidak ditolak

- **Mulai sesi agen setelah bounty dibuka.** Sesi yang dimulai sebelum bounty dibuka bisa membuat transkrip tidak memenuhi syarat.
- **Baca `RULES.txt` sampai selesai.** Sebagian besar penolakan terjadi karena syarat kecil yang terlewat, bukan karena kualitas entry.
- **Selalu jalankan `check` sebelum submit.** Pemeriksaan ini menangkap masalah yang sama dengan yang akan diperiksa sistem.
- **Bedakan bounty gratis dan berbayar.** Ada bounty tanpa biaya masuk sama sekali, ada juga yang memungut entry fee. Kalau targetmu nol biaya, lewati yang berfee.
- **Jangan menunggu deadline.** Submit lebih awal memberi waktu untuk memperbaiki kalau ada check yang gagal.
- **Simpan ID submission dan output submit.** Keduanya adalah bukti penerimaan entry-mu; tangkapan layar atau file log sederhana sudah cukup.
- **Satu sesi, satu pembangunan.** Kerjakan entry dalam sesi agen yang sama dari awal sampai submit supaya transkripnya utuh dan mudah dibundel.

## Dapat USDC dari link referral kamu sendiri

Setiap akun make.fun punya link referral pribadi berbentuk `https://make.fun/r/<kode>`. Bagikan link itu ke teman atau komunitasmu: setiap pendaftaran yang masuk lewat link-mu bisa menghasilkan reward USDC untukmu setelah ditinjau. Yang dihitung hanya akun baru yang nyata dan aktif — jadi bagikan ke orang yang memang tertarik mencoba, bukan sekadar mengejar jumlah klik.

Kamu bisa menemukan link referral-mu di profil setelah mendaftar.

## FAQ

**Apakah ikut bounty di make.fun berbayar?**
Pendaftaran akun gratis. Sebagian bounty gratis untuk diikuti, sebagian memungut entry fee kecil. Selalu cek keterangan bounty-nya sebelum mulai; kalau mau benar-benar tanpa biaya, pilih yang gratis.

**Apakah hadiahnya benar-benar ada?**
Ya. Hadiah setiap bounty dikunci di escrow on-chain open-source di Solana oleh EZO Labs sebelum kompetisi berjalan, dan bisa diverifikasi siapa pun. Pemenang mengklaim USDC ke wallet Solana mereka sendiri.

**Apakah saya harus bisa coding?**
Tidak harus jago. Entry dibangun bersama agen coding AI — tugasmu mengarahkan, memeriksa hasil, dan memastikan syarat bounty terpenuhi. Semakin baik kamu mengarahkan agenmu, semakin bagus entry-nya.

**Agen AI apa saja yang bisa dipakai?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, dan agen lain yang didukung kit. Yang penting sesi agenmu terekam sebagai transkrip yang bisa dibundel oleh CLI.

**Untuk apa transkrip sesi dikirim?**
Transkrip membuktikan bahwa entry memang dibangun dalam sesi agen yang sah selama bounty berjalan. Sistem memeriksanya secara otomatis bersama repo atau source bundle-mu.

**Kapan hadiah bisa diklaim?**
Setelah hasil bounty diumumkan (diposting), peringkat yang berhak bisa mengklaim USDC dari halaman profil ke wallet Solana yang tertaut.

## Siap mulai?

Daftar sekarang lewat link ini: [https://make.fun/r/7r7xnqjd](https://make.fun/r/7r7xnqjd) — kode referral `7r7xnqjd`. Selamat membangun, dan semoga entry pertamamu langsung naik peringkat!
