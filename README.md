A bit-perfect desktop music player for Windows. Plinth 0.13.2 makes ReplayGain tag writing crash-safe, fixes Hindi and other scripts showing as empty boxes, corrects some misleading text and adds the LICENSE file to the installer.

Features :

### Playback and output
- WASAPI Exclusive: bit-perfect. With nothing switched on, samples are only bit-shifted into the DAC's container (16, 24, 24-in-32 or 32 bit), never altered.
- WASAPI Shared: audio goes through the Windows mixer.
- ASIO: installed-driver discovery and direct selection. ASIO never silently falls back to another output.
- Playback never switches output mode behind your back. If a device or format is refused, Plinth stops and says why.
- Formats: FLAC, WAV, AIFF, ALAC and AAC (m4a), MP3, Ogg Vorbis, Opus, APE, WavPack, WMA/ASF (through Windows Media Foundation), and DSF/DFF including DST-compressed DFF.
- Gapless playback whenever the next track can use the same live stream, across sample-rate changes too. When an output reopen is needed, Plinth reports that transition instead of calling it gapless. Gapless On/Off switch in the player bar.
- Song transitions (off by default): Crossfade (equal-power) and AutoMix (silence trimming, beat-aware overlap, pitch-preserving tempo matching when track tempos are compatible, smooth fade otherwise). Overlap length and fallback duration are set in Settings. Native DSD, unknown durations, resampling and mismatched formats use a normal handoff.
- Repeat (off, all, one) and previous/next. CUE sheets: external .cue files and embedded FLAC CUESHEET tracks, with per-track queue entries and file-relative seeking.
- Per-device output and DSP profiles, remembered for each DAC.
- Buffer size setting for slow disks and network drives.
- First-play volume check: Plinth waits for your confirmation and shows any positive ReplayGain or EQ boost. It cannot read or lower your DAC or amplifier's hardware volume.

### DSD
- Native DSD to the DAC as DoP (bit-exact payload, markers and idle pattern), for DSD64 up to DSD512.
- Automatic conversion to 176.4 or 192 kHz PCM when the DAC refuses DoP or DSP is on.
- ID3 tags inside DSF/DFF files are read.

### Sound processing (all bypassed when off)
- Upsampling to 2x, 4x, 8x or the maximum the DAC accepts, within the same rate family (Kaiser-sinc polyphase).
- Crossfeed for headphones.
- Room correction by partitioned FFT convolution, from a WAV or FLAC impulse response (REW, Dirac and similar).
- Parametric equaliser with draggable graph, exact value entry, peak and shelf bands, and AutoEq / REW import. Preamp.
- Optional software volume, TPDF dither and a clipping counter.
- Processing order: crossfeed, room correction, upsampling, EQ and volume, dither.
- Signal path panel (click the quality chip or press S): Source, Processing and Output stages with the format between them, a status colour for each, and a verdict bar. Labels include Bit-perfect, Native DSD, DSP active, Reduced and Windows mixer.

### ReplayGain
- Reads track and album gain and peak tags. Playback use is off by default, with track or album mode and an optional clipping check.
- Scanner finds files missing tags, analyses loudness and writes standard track gain and peak tags, with an option to overwrite existing tags. Tags are written on a temporary copy first (new in 0.13.2).
- ReplayGain column with measured, missing, unsupported and error states. WMA/ASF tags are not read or written.

### Library
- Folder scan with tags, cover art and CUE support. Albums, Artists, Tracks, Queue, Playlists and search.
- Debounced automatic rescans of watched folders. Missing files are skipped and reported.
- Tile and list layouts for every page, remembered between sessions. Sortable track columns, with Genre and Date added in the sort menu.
- Format-coloured labels and explicit resolution, such as FLAC 24-bit 96 kHz.
- Artist tiles with cached artist photos and local album art as fallback.

### Playlists
- Create from the Playlists page, from the Queue (Save as playlist), from an album, or from any track's right-click menu. Mosaic covers.
- Play, shuffle, add to queue, rename, duplicate, delete (with confirmation), reorder and remove tracks.
- Import and export standard M3U8. Playlists store file paths, are saved atomically and survive rescans.

### Now Playing
- Compact header with artwork, title, resolution, codec and file details, and an immersive full view with artwork-tinted backdrop and every tag Plinth has.
- Optional visualizer driven by the audio that is playing (spectrum, loudness, bass beats), plus a full-screen visualizer. It reads a copy of the samples and never changes what reaches the DAC. It is off during native DSD.

### Online info (off by default)
- Artist pages: photo, biography, origin, genres, links and a discography with the albums you own marked. Album pages: description, label, catalogue number, release date, genres, links and credits per album and track. Cover art for albums with none.
- Sources: MusicBrainz, Wikipedia and Wikidata, and the Cover Art Archive. Only artist and album names are sent. Results are cached locally and nothing in your files is changed.
- Fetch for your whole library in the background, with pause and resume. Optional contact address in the User-Agent.

### Sources: Telegram and Discover
- Telegram: sign in with your own account and your own API ID and hash. Search channels or paste an @username, then browse their audio files. Channel profile pictures, per-channel song search with suggestions, multi-select, Download selected, Download all, Remove all downloads, Remove download, chosen download folder. Sign out and forget deletes the login and credentials.
- Discover: open music from the Internet Archive with no account (Live Music Archive, netlabels, community audio or everything). Each item shows its uploader's licence, with covers, search, multi-select and downloads.
- Downloads are exact: only the track you choose is fetched. Files are written as .part and renamed when complete. Cached files play through the normal bit-perfect player. Cache limit (4 GB by default) trims least recently played files and never touches queue or playlist items.
- Plinth does not suggest, index or rank channels, and does not check licences. You are responsible for playing only what you have the right to use.

### Application updates
- Settings > Application updates shows the installed and latest version and the release notes. Automatic checks (daily or weekly, switchable), then Download, then Install and restart.
- Stable releases only. HTTPS only. The installer's size and SHA-256 are verified against the published checksum before it can run. Nothing downloads or installs without a click.

### Interface
- Dark and Light themes (Ctrl+T). Outfit, Montserrat and JetBrains Mono are embedded, so the app looks the same on every PC. System fonts are used only for glyphs the bundled fonts lack: Japanese, Chinese, Korean, symbols, and now Indic scripts.
- Eased hover and focus, slim overlay scrollbars, a sidebar that scrolls on short windows, and per-page layouts.
- Support options in the sidebar: Buy Me a Coffee, and a UPI QR code for supporters in India.

### Keyboard shortcuts (press ? or F1 for the full list)
- Space: play/pause. Left/Right seek 5 s (Shift: 30 s). Ctrl+Left/Right previous/next. R repeat. Ctrl+Up/Down software volume.
- / or Ctrl+K search. Ctrl+1 to 8 jump to a page. Ctrl+N new playlist. Ctrl+, Settings. Ctrl+E Now Playing. Page Up/Down scroll. S signal path. Esc closes the open panel.
- Now Playing: F full screen, V visualizer, M full-screen visualizer.

### Privacy
Plinth has no analytics or telemetry. It contacts only the services you use: api.github.com and github.com for update checks and downloads, archive.org for Discover, Telegram directly from your PC, and MusicBrainz, Wikipedia/Wikidata and the Cover Art Archive when Online info is on. Your library, playlists and settings stay in %APPDATA%\Plinth.

### Known limitations
- No streaming-service integration, remote control or multi-room.
- Kernel Streaming output is not offered (removed in 0.13.0). The player uses WASAPI Shared, WASAPI Exclusive and ASIO.
- ReplayGain tags cannot be written for WMA/ASF. Room-correction convolution supports mono and stereo only.
- APE decoding is mono and stereo; DST-compressed DFF supports up to 6 channels; floating-point WavPack is not supported.
- A file cannot be played while it is still downloading, and downloaded remote tracks cannot yet be added to playlists.
- Arabic and Hebrew text is shown unshaped.
