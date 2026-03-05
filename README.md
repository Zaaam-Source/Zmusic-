# 🎵 Zmusic — Android Music Player

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-brightgreen?style=flat-square&logo=android"/>
  <img src="https://img.shields.io/badge/Language-Kotlin-7c3aed?style=flat-square&logo=kotlin"/>
  <img src="https://img.shields.io/badge/UI-Jetpack%20Compose-38bdf8?style=flat-square&logo=jetpackcompose"/>
  <img src="https://img.shields.io/badge/Architecture-MVVM-f472b6?style=flat-square"/>
  <img src="https://img.shields.io/badge/Min%20SDK-26%20(Android%208.0)-orange?style=flat-square"/>
</p>

<p align="center">
  Aplikasi pemutar musik Android berbasis YouTube streaming — mood detection, Spotify Wrapped, floating bubble player, dan masih banyak lagi.
</p>

---

## ✨ Fitur Utama

### 🎵 Core Playback
- Streaming audio via **NewPipe Extractor** — tanpa API key berbayar
- Background playback dengan **ExoPlayer + MediaSession**
- Queue management: shuffle, repeat (off / one / all), skip prev/next
- **Prefetch** lagu berikutnya (cache 5 menit)
- Retry otomatis 3x dengan exponential backoff saat stream gagal
- Audio focus management (pause saat telepon, duck saat notifikasi)
- WiFi Lock + Wake Lock agar tidak putus saat layar mati

### 🫧 Floating Bubble Player
- Overlay bubble yang bisa di-drag ke mana saja
- Expand jadi mini player dengan seekbar, prev/next, play/pause
- Tetap aktif di atas aplikasi lain

### 💜 Mood System
- 6 mood: `SAD` `ROMANCE` `HAPPY` `CHILL` `ENERGETIC` `HYPE`
- Deteksi otomatis dari judul + nama artis (weighted keyword scoring)
- Deteksi dari riwayat putar (session-based history)
- Smart shuffle berdasarkan kompatibilitas mood

### 📊 Stats & Wrapped
- Rekap ala **Spotify Wrapped** per periode
- Top songs, top artists, total waktu dengar
- Distribusi mood, recently played

### 📥 Download & Offline
- Download lagu ke storage lokal
- Playback otomatis dari file lokal kalau sudah didownload

### 🎛️ Fitur Tambahan
- Audio Visualizer real-time (fallback animasi jika permission ditolak)
- Sleep Timer
- Playback Speed Control
- Share **Now Playing Card** ke WA/IG/dll
- Daily Mix Generator otomatis dari histori user
- Playlist CRUD (buat, edit, hapus, tambah/hapus lagu)
- Riwayat pencarian
- Lirik support

---

## 🏗️ Tech Stack

| Layer | Library |
|---|---|
| UI | Jetpack Compose |
| Architecture | MVVM + Hilt (DI) |
| Audio Engine | ExoPlayer / Media3 |
| YouTube Source | NewPipe Extractor |
| Database | Room (SQLite) |
| Async | Coroutines + Flow |
| Image Loading | Coil |
| Navigation | Navigation Compose |

---

## 📁 Struktur Project

```
app/src/main/kotlin/com/zaaam/Zmusic/
│
├── data/
│   ├── LyricsRepository.kt
│   ├── MilestoneRepository.kt
│   ├── MusicRepository.kt          # Core: search, stream, mood, history
│   ├── NewPipeDownloader.kt
│   ├── SettingsRepository.kt
│   └── local/                      # Room DAO & Database
│       ├── AppDatabase.kt
│       ├── PlayHistoryDao.kt
│       ├── PlaylistDao.kt
│       ├── SearchHistoryDao.kt
│       └── SongDao.kt
│
├── model/                          # Data classes & entities
│
├── service/
│   ├── MusicService.kt             # MediaSessionService + ExoPlayer
│   └── FloatingPlayerService.kt    # Floating bubble overlay
│
├── ui/
│   ├── home/                       # Home screen + ViewModel
│   ├── player/                     # Full player screen (1083 baris)
│   ├── search/                     # Search + history
│   ├── explore/                    # Explore by genre/mood
│   ├── library/                    # Playlist management
│   ├── mood/                       # Mood screen
│   ├── trending/                   # Trending screen
│   ├── recent/                     # Recently played
│   ├── stats/                      # Statistik lengkap
│   ├── wrapped/                    # Spotify Wrapped style
│   ├── settings/
│   ├── about/
│   └── components/                 # Shared UI components
│
└── util/
    ├── AudioDownloadManager.kt
    ├── AudioVisualizerView.kt
    ├── DailyMixGenerator.kt
    ├── NowPlayingCardGenerator.kt
    ├── QueueManager.kt
    └── SleepTimerManager.kt
```

---

## 🚀 Cara Setup

1. **Clone / download** project ini
2. Buka dengan **Android Studio** (versi Hedgehog atau lebih baru)
3. Tunggu Gradle sync selesai
4. **Build & Run** ke emulator atau device fisik (Android 8.0+)

> **Note:** Tidak perlu setup API key apapun. YouTube streaming berjalan via NewPipe Extractor secara gratis.

---

## 📋 Requirements

- Android Studio Hedgehog+
- JDK 17+
- Android SDK 26+ (target SDK 34)
- Koneksi internet untuk streaming

---

## 📱 Permission yang Dibutuhkan

| Permission | Keperluan |
|---|---|
| `INTERNET` | Streaming & search YouTube |
| `FOREGROUND_SERVICE` | Background music playback |
| `WAKE_LOCK` | Cegah CPU sleep saat layar mati |
| `SYSTEM_ALERT_WINDOW` | Floating bubble player |
| `RECORD_AUDIO` | Audio visualizer real-time |

---

## 💰 Source Code

> Source code ini tersedia untuk dibeli. Cocok untuk dijadikan base project aplikasi musik Android kamu sendiri.

**Harga: Rp 99.000** — bayar sekali, bebas dikembangkan.

📩 **Kontak pembelian:** [@azm101222](https://t.me/azm101222) di Telegram

---

## 📄 License

Source code ini dijual untuk penggunaan pribadi & komersial. Tidak untuk didistribusikan ulang secara gratis.

---

<p align="center">Made with 💜 using Kotlin & Jetpack Compose</p>
