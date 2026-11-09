# VeyrionHUD (Paper 1.21.1)

HUD kanan-atas "Veyrion Roleplay": logo V, judul gradasi putih->abu gelap, tanggal+jam WIB,
jumlah online, RAS (dibaca dari AwakeningCutscene), uang. Semua ikon hitam.

## Cara pasang
1. Build plugin: `mvn package` -> `target/VeyrionHUD-1.0.0.jar` (Java 21, butuh internet buat narik paper-api).
2. Taruh di `plugins/` bareng `AwakeningCutscene-1_0_0.jar` (+ ProtocolLib, wajib buat jar itu). Vault opsional (uang).
3. Upload `VeyrionHUD-ResourcePack.zip` ke hosting direct-link, isi `resource-pack.url` + `sha1` di config.yml
   (atau pakai `resource-pack=` di server.properties). Client WAJIB pakai pack ini.
4. `/veyrionhud reload`

## Ras
Plugin mantau cutscene `/awakening <beast|dragon|elf|human> <player>`. Kalau cutscene selesai
sampai akhir, ras player disimpan (`plugins/VeyrionHUD/races.yml`) dan tampil di HUD.
Daftar ras diambil langsung dari jar (tidak ada tambahan). Manual: `/veyrionhud setrace <player> <ras|none>`.

## Kenapa pas di semua GUI Scale
Teks dikirim lewat bossbar dengan lebar total 0 -> mulai tepat di tengah layar, lalu shader
(`rendertype_text.vsh`, marker warna #4E5Cxx) menggeser ke tepi kanan + offset baris. Semua satuan GUI pixel.

## Edit
- Posisi/jarak: `config.yml` (layout.*)
- Warna teks (sekarang putih): `rendertype_text.vsh` (baris "HUD text colour")
- Logo V jadi hitam: `LOGO_BLACK=1 python3 tools/gen_assets.py`
- Ikon/logo/judul: `python3 tools/gen_assets.py` (atau ganti PNG di resourcepack/assets/veyrion/textures/font)
