# 🎵 Zmusic

**Aplikasi streaming musik open-source untuk Android** — memutar jutaan lagu dari YouTube tanpa iklan, tanpa akun, dan sepenuhnya gratis.

Dibangun dengan Kotlin, Jetpack Compose, dan Material 3. Menggunakan [NewPipeExtractor](https://github.com/TeamNewPipe/NewPipeExtractor) sebagai backend untuk mengakses konten YouTube secara publik.

> Made with ♪ in Indonesia

---

## Fitur

**Streaming & Pemutar**
- Streaming musik langsung dari YouTube tanpa iklan
- Pemutar lengkap dengan kontrol play/pause, next, previous, seek ±10 detik
- Mini player bar yang tetap tampil saat navigasi antar halaman
- Antrian lagu (queue) dengan mode shuffle
- Kontrol kecepatan pemutaran
- Download lagu untuk didengarkan offline

**Pencarian & Penemuan**
- Pencarian lagu via YouTube Music
- Halaman Home dengan konten trending dan rekomendasi
- Halaman Explore untuk jelajahi musik berdasarkan genre
- Halaman Trending — lagu-lagu yang sedang populer di YouTube Indonesia
- Infinite scroll — konten terus dimuat saat scroll ke bawah

**Mood & Personalisasi**
- 6 mode mood: 😊 Happy, 😢 Sad, ⚡ Energetic, 😌 Chill, ❤️ Romance, 🔥 Hype
- Deteksi mood otomatis berdasarkan judul dan artis lagu
- Rekomendasi lagu sesuai mood yang dipilih

**Lirik**
- Lirik otomatis dari LRCLIB (synced dan plain text)
- Synced lyrics — lirik berjalan mengikuti waktu lagu
- Terjemahan lirik ke Bahasa Indonesia via MyMemory API

**Koleksi & Statistik**
- Buat dan kelola playlist tanpa batas
- Riwayat lagu yang pernah diputar
- Statistik: total play, total durasi, top lagu, top artis, distribusi mood
- Long press lagu untuk tambahkan ke playlist

**Desain**
- UI Material 3 dengan tema gelap dan terang (mengikuti sistem)
- Desain glassmorphism pada kartu dan navigasi
- Floating pill bottom navigation
- Edge-to-edge display
- Lokalisasi Bahasa Indonesia

---

## Tech Stack

| Komponen | Library |
|----------|---------|
| Bahasa | Kotlin |
| UI Framework | Jetpack Compose + Material 3 |
| Arsitektur | MVVM + Hilt (Dependency Injection) |
| Database | Room |
| Media Player | Media3 / ExoPlayer |
| Ekstraksi YouTube | NewPipeExtractor v0.26.0 |
| HTTP Client | OkHttp 4.12.0 |
| Image Loader | Coil Compose |
| Async | Kotlin Coroutines + Flow |
| Build | Gradle KTS + KSP |

---

## Persyaratan

- Android 8.0+ (API 26 — Android Oreo) hingga Android 15
- Koneksi internet untuk streaming (kecuali lagu yang sudah didownload)

---

## Struktur Project

```
app/src/main/kotlin/com/zaaam/Zmusic/
├── ZmusicApp.kt                  # Application class + NewPipe init
├── data/
│   ├── MusicRepository.kt        # Logika utama: search, stream, trending, mood
│   ├── LyricsRepository.kt       # Fetch lirik dari LRCLIB + terjemahan
│   ├── NewPipeDownloader.kt      # OkHttp bridge untuk NewPipeExtractor
│   └── local/
│       ├── AppDatabase.kt         # Room database (v3)
│       ├── SongDao.kt
│       ├── PlaylistDao.kt
│       └── PlayHistoryDao.kt
├── di/
│   └── AppModule.kt              # Hilt dependency injection module
├── model/
│   ├── Song.kt
│   ├── Playlist.kt
│   ├── Mood.kt                   # 6 enum mood + query pencarian
│   ├── Lyrics.kt
│   ├── PlayHistory.kt
│   └── entity/                   # Room entities + query result classes
├── service/
│   └── MusicService.kt           # MediaSessionService + foreground player
├── util/
│   ├── QueueManager.kt           # Manajemen antrian lagu + shuffle
│   ├── AudioDownloadManager.kt   # Download manager dengan progress tracking
│   └── Extensions.kt             # Format durasi (mm:ss, jam menit)
└── ui/
    ├── MainActivity.kt           # Entry point + navigasi + floating nav bar
    ├── theme/ZmusicTheme.kt      # Warna, tipografi, glass tokens
    ├── home/                     # HomeScreen + ViewModel (discovery, infinite scroll)
    ├── search/                   # SearchScreen + ViewModel
    ├── player/                   # PlayerScreen + ViewModel (lyrics, download, speed)
    ├── library/                  # LibraryScreen, PlaylistDetail + ViewModel
    ├── trending/                 # TrendingScreen + ViewModel
    ├── explore/                  # ExploreScreen + ViewModel (genre-based)
    ├── mood/                     # MoodScreen + ViewModel
    ├── stats/                    # StatsScreen + ViewModel
    ├── recent/                   # RecentlyPlayedScreen + ViewModel
    ├── about/                    # AboutScreen + DevScreen
    └── components/               # MiniPlayerBar, SongItem, AlbumArt, GlassCard
```

---

## Disclaimer

Zmusic adalah aplikasi pemutar musik open-source yang bersifat independen dan **TIDAK** berafiliasi, didukung, disponsori, atau disetujui oleh YouTube™, Google LLC, Spotify™, Spotify AB, atau entitas lain manapun.

Semua merek dagang, nama layanan, dan logo yang disebutkan adalah milik dari pemiliknya masing-masing.

Aplikasi ini menggunakan NewPipeExtractor sebagai library pihak ketiga untuk mengakses konten yang tersedia secara publik. Pengembang tidak bertanggung jawab atas penggunaan yang melanggar ketentuan layanan pihak ketiga.

**Aplikasi ini GRATIS dan tidak diperjualbelikan dalam bentuk apapun.** Jika kamu mendapatkan aplikasi ini dengan membayar, kamu telah ditipu.

---

## Kontak & Dukungan

- **Telegram:** [@azm101222](https://t.me/azm101222) — Bug report & saran
- **Saluran WhatsApp:** [Zmusic Updates](https://whatsapp.com/channel/0029Vb7ZuEK3QxRtvlO89u0u)
- **Donasi:** [Saweria](https://saweria.co/Zsmm) — Dukung pengembangan Zmusic ❤

---

## Lisensi

```
Copyright © 2025 Zaaam

Zmusic dilisensikan di bawah GNU General Public License v3.0.
Lihat file LICENSE untuk detail lengkap.
```

### Library Pihak Ketiga

| Library | Lisensi |
|---------|---------|
| NewPipeExtractor | GPL-3.0 |
| ExoPlayer (Media3) | Apache-2.0 |
| Jetpack Compose | Apache-2.0 |
| Hilt (Dagger) | Apache-2.0 |
| Room Database | Apache-2.0 |
| OkHttp | Apache-2.0 |
| Coil | Apache-2.0 |
| Kotlin Coroutines | Apache-2.0 |
