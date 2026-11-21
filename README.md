d1_superpowers — Enterprise FiveM Modular Superpowers Systemd1_superpowers adalah framework kekuatan super dan kemampuan khusus berbasis Lua 5.4 untuk server FiveM (QBCore, QBox, ESX Legacy, dan Standalone). Didesain dengan standar performa industri ($0.00\text{ ms}$ idle resmon), arsitektur modular terisolasi (plugin-style), serta perlindungan penuh terhadap exploit (server-authoritative).🌟 Fitur UtamaZero-Idle Resmon ($0.00\text{ ms}$): Tidak ada per-frame loop global saat tidak ada power yang aktif. Thread aktif hanya berjalan selama durasi skill dan langsung di-cleanup.Arsitektur Modular (RegisterPower): Setiap kemampuan ditempatkan di file independen (powers/<id>.lua). Menambah atau menonaktifkan skill dapat dilakukan tanpa menyentuh file inti.Beragam Mode Aktivasi:Skill Hotbar (Slot 1–4): Di-bind ke tombol FiveM bawaan (RegisterKeyMapping) untuk eksekusi cepat saat RP.Usable Inventory Items: Penggunaan item langsung dari tas (ox_inventory, qb-inventory, qs-inventory).Radial Menu (ox_lib / qb-radialmenu): Navigasi visual untuk memilih dan mengaktifkan kemampuan.Command & Menu: /powers (UI manajemen player) dan /usepower <id>.3 Mode Integrasi Item per Skill:none: Tanpa item (mengandalkan Admin DB Grant, Job, Gang, atau ACE).passive: Skill hanya tersedia jika item tertentu ada di dalam inventory. Jika item dibuang/dirampok, skill otomatis terkunci.consumable: Skill terpicu saat item digunakan, dan 1 buah item akan terpakai (consumed).Hierarki Izin Berlapis (Server-Authoritative):Direct Admin Grant (Database player_superpowers / Config.AdminWhitelist)Job & Grade RequirementsGang & Grade RequirementsPassive / Consumable Inventory ItemsACE Permission NodesMastery Leveling Engine (Level 1–5): Pemakaian skill sah menambah XP untuk meningkatkan level Mastery, mengurangi cooldown & konsumsi energi, serta memperluas jangkauan/efek skill.Panel & Automation Admin: Menu GUI /powersadmin (ox_lib), command console/Tebex, sistem preset paket skill, serta audit log ke Discord Webhook.📁 Struktur Folder Proyekd1_superpowers/
├── fxmanifest.lua
├── config.lua
├── README.md
├── docs/
│   ├── admin_guide.md
│   └── developer_guide.md
├── sql/
│   └── schema.sql
├── bridge/
│   ├── client.lua
│   └── server.lua
├── shared/
│   ├── registry.lua
│   └── config_powers.lua
├── server/
│   ├── main.lua
│   ├── database.lua
│   ├── permissions.lua
│   ├── admin_menu.lua
│   └── inventory_bridge.lua
├── client/
│   ├── main.lua
│   ├── keybinds.lua
│   ├── energy_hud.lua
│   ├── particle_sync.lua
│   ├── radial_menu.lua
│   └── admin_gui.lua
└── powers/
    ├── flight.lua
    ├── super_speed.lua
    ├── telekinesis.lua
    └── [30_powers_lainnya].lua
🚀 Panduan Instalasi CepatUnduh/Cloning Repository: Letakkan folder d1_superpowers ke dalam direktori resources/[scripts]/ server Anda.Import Database: Jalankan file SQL sql/schema.sql pada database MySQL server Anda via oxmysql / HeidiSQL / phpMyAdmin.Atur Dependency: Pastikan resource pendukung berikut berjalan sebelum d1_superpowers:ensure oxmysql
ensure ox_lib
# Framework (qb-core / qbx_core / es_extended)
ensure d1_superpowers
Konfigurasi Hak Admin: Tambahkan izin ACE pada server.cfg Anda untuk administrator:add_ace group.admin command.powersadmin allow
📄 Dokumentasi Terkait📗 Panduan Admin & Tebex Integrasi: Penggunaan GUI /powersadmin, syntax command console, integrasi Tebex webhook, dan manajemen preset.📘 Panduan Developer & API: Standar pembuatan modul power baru dengan RegisterPower, pengelolaan resmon, dan teknik cleanup.
