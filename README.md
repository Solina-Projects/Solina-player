<p align="center">
  <img src="assets/solina_player_icon.svg" alt="Solina Player icon" width="160" height="160"/>
</p>

<p align="center">
  <a href="https://github.com/Solina-Projects/Solina-player/releases/latest">
    <img src="https://img.shields.io/github/v/release/Solina-Projects/Solina-player?include_prereleases&logo=github&style=for-the-badge&label=Latest%20Release" alt="Latest release">
  </a>
  <img src="https://img.shields.io/badge/Android-12%2B-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android 12+">
  <img src="https://img.shields.io/badge/License-GPLv3-blue?style=for-the-badge" alt="GPLv3 license">
</p>

<p align="center">
  <img src="assets/screenshot1.jpeg" alt="Solina Player now playing screen" width="205"/>
  <img src="assets/screenshot2.jpeg" alt="Solina Player video folders" width="205"/>
  <img src="assets/screenshot3.jpeg" alt="Solina Player library folders" width="205"/>
</p>

<p align="center">
  <img src="assets/screenshot4.jpeg" alt="Solina Player home screen" width="205"/>
  <img src="assets/screenshot5.jpeg" alt="Solina Player recent videos and Your Mix" width="205"/>
  <img src="assets/screenshot6.jpeg" alt="Solina Player video player in landscape" width="205"/>
</p>

# Solina Player

Solina Player is an Android music player maintained by **Solina**.

## Fork attribution

Solina Player is a fork of [PixelPlayerOSS](https://github.com/PixelPlayerHQ/PixelPlayerOSS),
an Android music player maintained by [Theo Vilardo (@lostf1sh)](https://github.com/lostf1sh).
This fork is based on PixelPlayerOSS commit
`122a48f7b55bbc84242f266ec370e7e7f3b986e9` (2026-11-15, `main`).

The original code is copyright its authors and licensed under the
**GNU General Public License v3.0 or later (GPL-3.0-or-later)**.
This fork stays under the same license — see [LICENSE](LICENSE).
Changes in this fork: rebranded to Solina Player (`app.solina.player`),
Android 12 (API 31) minimum, and arm64-v8a builds only.

## Music + Video

The player plays both music and video, kept separate — never mixed.
Home offers two entry cards (Music / Video), separate audio and video
file counts, a recently-added music row and a recently-added videos row.
Video uses its own ExoPlayer/Media3 player with its own library
(MediaStore.Video), library screen and player screen (seek, speed,
fullscreen, subtitle tracks when the file carries them), in the same
Material 3 Expressive style as the music player. Home sections — new
and existing — can be shown, hidden and reordered from
Settings → Customise Home. The video section has its own bottom bar
(Home / Search / Folders): Home always returns to the main Home page,
video Search lists all videos and searches within them, and Folders
groups videos by folder with sort and Play-all actions, a settings
dialog (view mode / layout / sort), search, and a floating Resume
button that continues the last partially-watched video. While a video
plays, the floating bottom bar is hidden and an extra control bar —
opened with an animated arrow — offers aspect / rotation, speed,
screenshot, audio settings, sleep mode, night light and background
playback. Video formats are what ExoPlayer plus the
bundled FFmpeg decoders support (common containers such as MP4, MKV,
WebM, MOV, AVI, 3GP and FLV); the music player behaviour is unchanged.

## What's new in v1.1.0

- **Video selection:** long-press any video in the library, search or
  folders to select it, then play, add to playlist, share, rename, view
  details or delete — the same selection system the music library
  already had. Folders themselves are not selectable; rename and
  details need exactly one video selected. Delete and rename ask for
  the system MediaStore consent first.
- **Swapped video swipes:** swiping up/down on the left side of the
  video player now changes volume, on the right side brightness. The
  indicator bars stay where they were (volume on the right,
  brightness on the left).
- **Seek stays quiet:** seeking in the video player no longer pops the
  control bars up — only the seek preview shows.
- **Home second tap:** tapping a recently-added song a second time
  opens the full music player; tapping a recently-added video plays it
  inside its card first, and a second tap opens it fullscreen from the
  same position.

## What It Is

Solina Player is an Android music player. It focuses on local playback, self-hosted music libraries, expressive Material 3 UI, and user-controlled online lookups.

The app works offline by default. Optional online services are disabled until you enable them in setup or settings.

Package name: `app.solina.player`

## Why This Exists

Solina Player keeps the player FOSS-oriented and removes integrations that are not part of that direction.

Removed integrations include Telegram, NetEase, QQ Music, Google Drive, Gemini, Cast, Wear OS, Play Store billing, Firebase, Crashlytics, and Google Play Services runtime dependencies.

Cloud playback is limited to self-hosted sources: Navidrome/Subsonic and Jellyfin.

## Features

| Area | Highlights |
| --- | --- |
| Playback | Media3 playback engine, FFmpeg support, gapless playback, crossfade, custom transitions, queue controls, shuffle, repeat, sleep timer, external file playback |
| Library | Local scanning for MP3, FLAC, AAC, OGG, WAV, M4A, albums, artists, genres, folders, favorites, playlists, stats, metadata editing |
| Self-hosted | Navidrome/Subsonic and Jellyfin login, sync, streaming, artwork, and app-private offline downloads |
| Lyrics | Embedded lyrics, local `.lrc` files, lyrics import/editing, optional LRCLIB lookup |
| Artwork | Local artwork, album-art palette extraction, optional Deezer artist image lookup |
| Metadata | On-demand MusicBrainz matching for recording, release, and artist identifiers |
| UI | Jetpack Compose, Material 3, dynamic color, light/dark themes, Glance widgets, animated player surfaces |
| Backup | Preferences, playlists, favorites, lyrics, stats, and app state backup/restore |

## Online Services

Solina Player separates offline playback from network lookups.

| Service | Purpose | Default |
| --- | --- | --- |
| Navidrome/Subsonic | Self-hosted library sync, streaming, and offline downloads | User login required |
| Jellyfin | Self-hosted library sync, streaming, and offline downloads | User login required |
| MusicBrainz | On-demand metadata matching and identifier enrichment | Only when requested |
| LRCLIB | Search online lyrics when local or embedded lyrics are missing | Off |
| Deezer | Fetch missing artist artwork and cache it locally | Off |

LRCLIB and Deezer can be enabled during first-run setup or later from `Settings > Music Management > Optional online services`. MusicBrainz searches run only when you choose the lookup action for a track.

## Requirements

| Requirement | Version |
| --- | --- |
| Android | 12 or newer, API 31+ |
| JDK | 21 |
| Android SDK | compile/target 37 |

This fork builds **arm64-v8a only** (64-bit ARM devices, Android 12+).

## Build From Source

Clone the repository:

```sh
git clone https://github.com/Solina-Projects/Solina-player.git
cd Solina-player
```

Build the debug APK:

```sh
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :app:assembleDebug
```

Build one universal debug APK for local installation:

```sh
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :app:assembleDebug -Psolina.enableAbiSplits=false
```

Build a universal unsigned release APK:

```sh
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :app:assembleRelease -Psolina.enableAbiSplits=false -Psolina.disableReleaseSigning=true
```

Run unit tests:

```sh
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :app:testDebugUnitTest
```

Generate the baseline profile with a connected device or emulator:

```sh
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :baselineprofile:generateBaselineProfile
```

## Download

GitHub releases are available at:

```text
https://github.com/Solina-Projects/Solina-player/releases
```

Obtainium app id:

```text
app.solina.player
```

This fork is not published on F-Droid.

### Alpha builds

Automatic alpha publishing is currently disabled: merges into `main` no longer publish a pre-release. Stable releases are published manually on the [releases page](https://github.com/Solina-Projects/Solina-player/releases) — install only those.

## Project Structure

```text
app/src/main/java/app/solina/player/
- data/             Room, repositories, preferences, services, workers
- di/               Hilt modules and qualifiers
- presentation/     Compose screens, components, navigation, ViewModels
- ui/               Theme and Glance widgets
- utils/            Shared utilities

baselineprofile/      Macrobenchmark and baseline profile generation
```

## Tech Stack

| Area | Technology |
| --- | --- |
| Language | Kotlin |
| UI | Jetpack Compose |
| Design | Material 3 |
| Playback | AndroidX Media3, ExoPlayer, FFmpeg |
| Database | Room |
| Dependency Injection | Hilt |
| Preferences | DataStore |
| Background Work | WorkManager |
| Networking | Retrofit, OkHttp |
| Images | Coil |
| Metadata | TagLib |

## Contributing

Contributions are welcome. Open an issue or pull request with a focused change and include test/build results when possible.

Useful local checks:

```sh
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :app:compileDebugKotlin
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :app:lintDebug
JAVA_HOME=/usr/lib/jvm/java-21-openjdk ./gradlew :app:testDebugUnitTest
```

Release process: [docs/RELEASE.md](docs/RELEASE.md)
