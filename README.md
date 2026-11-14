# Virtual Office Live — data

Data LIVE untuk dashboard Virtual Office Live (versi standalone, dibuka lewat link).
Diperbarui otomatis tiap 2 menit oleh `sync-data.py` (read-only: hanya membaca
saldo on-chain BSC + file log/state lokal, tidak mengubah logika bot apa pun).

## File

- `status.json` — status tiap agen (BURU, PASAR, TUGAS, KODE, orkestrator metawo):
  `status` ("bekerja" bila ada aktivitas tercatat <= 10 menit lalu, selain itu
  "idle"), balance, volume, remaining target, script version, last event ts.
  Mission Board metric utama: `mission_board.total_cuan_u` (saldo U on-chain).
- `events.json` — max 100 event terakhir, `{"id", "ts" (ISO +07:00), "agent",
  "type", "data"}`. Event hanya dari kejadian nyata yang tercatat (run cron,
  sweep floor, dsb.); bila tidak ada kejadian, array kosong.

## Aturan angka

- `null` = tidak bisa dibaca saat sync (bukan nol, bukan karangan).
- Saldo BNB / U / IAO / BAGENT dibaca on-chain via RPC publik BSC.
- URL mentah: `https://raw.githubusercontent.com/metawo14/virtual-office-live-data/main/status.json`
  dan `.../events.json` (raw.githubusercontent bisa cache beberapa menit).
