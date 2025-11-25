# Feature Documentation

<!--toc:start-->
- [Feature Documentation](#feature-documentation)
  - [📥 Download Features](#📥-download-features)
    - [1. Resume Support (`--continue`)](#1-resume-support-continue)
    - [2. No Overwrites (`--no-overwrites`)](#2-no-overwrites-no-overwrites)
    - [3. Network Retry System](#3-network-retry-system)
      - [3.1 Connection Retries (`--retries 10`)](#31-connection-retries-retries-10)
      - [3.2 Fragment Retries (`--fragment-retries 10`)](#32-fragment-retries-fragment-retries-10)
      - [3.3 Retry Sleep (`--retry-sleep 5`)](#33-retry-sleep-retry-sleep-5)
  - [🎨 Media Enhancement Features](#🎨-media-enhancement-features)
    - [4. Thumbnail Embedding (`--embed-thumbnail`)](#4-thumbnail-embedding-embed-thumbnail)
    - [5. Metadata Tagging (`--embed-metadata` + `--add-metadata`)](#5-metadata-tagging-embed-metadata-add-metadata)
  - [📝 Accessibility Features](#📝-accessibility-features)
    - [6. Hebrew Subtitle System](#6-hebrew-subtitle-system)
      - [Tier 1: Manual Hebrew Subtitles (`--write-subs`)](#tier-1-manual-hebrew-subtitles-write-subs)
      - [Tier 2: Auto-generated Hebrew (`--write-auto-subs`)](#tier-2-auto-generated-hebrew-write-auto-subs)
      - [Tier 3: Auto-translated (`--sub-langs "he.*,en.*"`)](#tier-3-auto-translated-sub-langs-heen)
    - [7. Chapter Preservation (`--embed-chapters`)](#7-chapter-preservation-embed-chapters)
  - [🔄 How Features Work Together](#🔄-how-features-work-together)
    - [Scenario 1: Large Video Download Over Unstable Connection](#scenario-1-large-video-download-over-unstable-connection)
    - [Scenario 2: Organizing Video Library](#scenario-2-organizing-video-library)
    - [Scenario 3: Educational Playlist Download](#scenario-3-educational-playlist-download)
  - [🎯 Best Practices](#🎯-best-practices)
    - [For Reliable Downloads:](#for-reliable-downloads)
    - [For Library Organization:](#for-library-organization)
    - [For Large Batches:](#for-large-batches)
  - [❓ FAQ](#faq)
  - [🔧 Troubleshooting](#🔧-troubleshooting)
  - [📊 Performance Impact](#📊-performance-impact)
<!--toc:end-->

Comprehensive explanation of all YT-DLP Batch Downloader features and their implementation.

---

## 📥 Download Features

### 1. Resume Support (`--continue`)

**What it does:**
Resumes interrupted downloads from where they stopped instead of starting over.

**How it works:**

- yt-dlp saves partial download progress in `.part` files
- When restarted, it checks for existing `.part` files
- Continues downloading from the last completed byte
- Automatically renames to final filename when complete

**Use cases:**

- Network connection drops mid-download
- System shutdown or crash during download
- Large files (multi-GB videos)
- Unstable internet connections

**Example scenario:**

```
Download starts: video.mp4.part (0% → 45%)
Connection lost at 45%
Restart script: video.mp4.part (45% → 100%)
Complete: video.mp4
```

---

### 2. No Overwrites (`--no-overwrites`)

**What it does:**
Prevents accidentally overwriting existing downloaded files.

**How it works:**

- Before downloading, checks if file already exists
- If exists, skips download completely
- Preserves your existing files
- Prevents data loss from re-running script

**Use cases:**

- Re-running script on same batch file
- Protecting already downloaded content
- Avoiding duplicate downloads
- Saving bandwidth and time

**Example scenario:**

```
First run: Downloads video.mp4 successfully
Second run: Sees video.mp4 exists → Skips download
Result: Original file preserved, no wasted bandwidth
```

**Note:** Combines with `--continue` for smart behavior:

- Partial file exists → Resume
- Complete file exists → Skip entirely

---

### 3. Network Retry System

Three-layer retry mechanism for maximum reliability:

#### 3.1 Connection Retries (`--retries 10`)

**What it does:**
Retries entire download operation up to 10 times on network failure.

**Handles:**

- DNS resolution failures
- Connection timeouts
- Server unavailable (503, 504)
- Network unreachable errors

#### 3.2 Fragment Retries (`--fragment-retries 10`)

**What it does:**
Retries individual video fragments for streaming protocols (HLS, DASH).

**How streaming works:**
Modern videos are split into small fragments (2-10 seconds each). If one fragment fails, only that fragment is retried, not the entire video.

**Handles:**

- Fragment download timeouts
- Corrupted fragment data
- CDN temporary failures
- Streaming protocol errors

#### 3.3 Retry Sleep (`--retry-sleep 5`)

**What it does:**
Waits 5 seconds between retry attempts.

**Why it matters:**

- Prevents hammering overwhelmed servers
- Allows temporary network issues to resolve
- Reduces chance of being rate-limited or blocked
- Respects server resources

**Progressive behavior:**

```
Attempt 1: Immediate
Attempt 2: 5s delay
Attempt 3: 5s delay
... up to 10 attempts
```

---

## 🎨 Media Enhancement Features

### 4. Thumbnail Embedding (`--embed-thumbnail`)

**What it does:**
Embeds the video thumbnail as cover art in the video file.

**Visual result:**

```
Before: [?] video.mp4
After:  [📷] video.mp4 (shows video thumbnail)
```

**Where it appears:**

- Video file icons in file managers
- Media player interfaces (VLC, MPV, QuickTime)
- Mobile device video galleries
- TV/streaming device libraries
- Plex/Jellyfin media servers

**Technical details:**

- Thumbnail downloaded separately first
- Embedded into video container metadata
- Supported formats: MP4, MKV, WebM
- No impact on video quality or playback

**File manager comparison:**

```
Without thumbnail:    With thumbnail:
┌──────────────┐     ┌──────────────┐
│              │     │   [Image]    │
│   video.mp4  │     │   video.mp4  │
│   1.2 GB     │     │   1.2 GB     │
└──────────────┘     └──────────────┘
```

---

### 5. Metadata Tagging (`--embed-metadata` + `--add-metadata`)

**What it does:**
Embeds comprehensive metadata into video files, similar to ID3 tags in music files.

**Metadata included:**

- **Title**: Video title
- **Author/Artist**: Channel name
- **Date**: Upload date
- **Description**: Video description
- **Comment**: Additional info
- **URL**: Original video URL
- **Duration**: Video length
- **Genre**: Category (if available)
- **Album**: Playlist name (if applicable)

**Dual-flag approach:**

**`--embed-metadata`:**

- Embeds JSON metadata from yt-dlp
- Includes technical details
- Raw format preservation

**`--add-metadata`:**

- Writes human-readable tags
- Compatible with media players
- Standard tag formats (ID3, Vorbis, etc.)

**Viewing metadata:**

**Linux/macOS:**

```bash
# Using ffprobe
ffprobe video.mp4

# Using mediainfo
mediainfo video.mp4

# Using exiftool
exiftool video.mp4
```

**Windows:**

- Right-click file → Properties → Details tab
- Use MediaInfo GUI

**Media players:**
Most players (VLC, MPV, Kodi) display this info in their info panels.

**Benefits:**

- Organize video library like music collection
- Search by author/date in media players
- Remember video source years later
- Professional media library management

---

## 📝 Accessibility Features

### 6. Hebrew Subtitle System

Multi-tier subtitle acquisition strategy:

#### Tier 1: Manual Hebrew Subtitles (`--write-subs`)

- Professional, human-created subtitles
- Highest quality and accuracy
- Often provided by content creator
- Preferred when available

#### Tier 2: Auto-generated Hebrew (`--write-auto-subs`)

- YouTube's automatic speech recognition
- Generated from Hebrew audio
- Good accuracy for clear speech
- Fallback if manual subs unavailable

#### Tier 3: Auto-translated (`--sub-langs "he.*,en.*"`)

- Starts with English manual/auto subs
- Auto-translates to Hebrew
- Works when no Hebrew audio/subs exist
- Better than nothing for non-Hebrew content

**Language priority:**

```
1. he (Manual Hebrew) ✓ Best
2. he-auto (Auto-generated Hebrew) ↓
3. en → he (Auto-translated from English) ↓
4. he.* (Any Hebrew variant) ↓ Last resort
```

**Subtitle conversion (`--convert-subs srt`):**

- Converts all formats to SRT
- Universal compatibility
- Plain text format
- Easy to edit if needed

**Subtitle embedding (`--embed-subs`):**

- Subtitles built into video file
- No separate .srt file needed
- Works on all devices
- Can be toggled on/off in player

**Supported formats:**

- MP4: Soft subtitles (togglable)
- MKV: Multiple subtitle tracks
- WebM: Embedded subtitles

---

### 7. Chapter Preservation (`--embed-chapters`)

**What it does:**
Preserves video chapter markers in downloaded files.

**What are chapters?**
Chapters are like bookmarks in a video:

```
0:00 - Introduction
2:15 - Topic 1
8:30 - Topic 2
15:45 - Conclusion
```

**Chapter sources:**

1. **YouTube chapters**: Set by creator in description
2. **Auto-generated**: From video analysis
3. **SponsorBlock**: Community-marked segments

**Chapter usage:**

**In media players:**

- VLC: Playback → Chapter menu
- MPV: Keyboard shortcuts to jump chapters
- QuickTime: Chapter dropdown
- Mobile players: Chapter list in controls

**Practical benefits:**

```
Educational video:
- Skip to specific lecture section
- Review particular topic quickly
- Create study notes with timestamps

Tutorial:
- Jump directly to relevant step
- Replay specific technique
- Follow along at your pace

Podcast/Interview:
- Skip to interesting guest
- Navigate by topic
- Find referenced timestamp
```

**SponsorBlock integration (`--sponsorblock-mark all`):**
Marks these segments (doesn't skip automatically):

- Sponsor segments
- Self-promotion
- Interaction reminders
- Non-music sections
- Filler content

---

## 🔄 How Features Work Together

### Scenario 1: Large Video Download Over Unstable Connection

```
1. Start download: video.mp4.part (0%)
2. Connection drops at 35%
3. --continue resumes from 35%
4. Another drop at 70%
5. --fragment-retries saves specific fragments
6. --retry-sleep prevents hammering
7. --retries ensures eventual success
8. Download completes: video.mp4
9. --no-overwrites protects it from re-runs
```

### Scenario 2: Organizing Video Library

```
1. Download completes
2. --embed-thumbnail → Thumbnail shows in file manager
3. --embed-metadata → Title, author, date tagged
4. --embed-chapters → Video has navigation markers
5. --embed-subs → Hebrew subtitles built-in
6. Result: Professional media library entry
```

### Scenario 3: Educational Playlist Download

```
1. Batch file with 50 lecture videos
2. First 30 download successfully
3. Network fails
4. Restart script:
   - --no-overwrites skips first 30
   - --continue resumes partial #31
   - Continues with #32-50
5. All videos have:
   - Hebrew subtitles for accessibility
   - Chapters for navigation
   - Metadata for organization
   - Thumbnails for recognition
```

---

## 🎯 Best Practices

### For Reliable Downloads

1. Use ethernet over WiFi when possible
2. Let retry mechanisms work (don't cancel too quickly)
3. Keep script running during retries
4. Check batch file after completion for any remaining failures

### For Library Organization

1. Use consistent download directory structure
2. Let metadata embedding complete
3. Verify thumbnails appear before moving files
4. Check subtitle languages with media player

### For Large Batches

1. Test with 2-3 videos first
2. Run during off-peak hours for better speeds
3. Monitor first few downloads for issues
4. Keep batch file as backup until verified

---

## ❓ FAQ

**Q: What if video already exists but partially downloaded?**
A: `--continue` resumes the `.part` file. `--no-overwrites` only checks complete files.

**Q: Will retries slow down my downloads?**
A: Only on failures. Successful downloads aren't affected. The 5s delay only happens between failed attempts.

**Q: Do embedded thumbnails increase file size?**
A: Minimally (~50-200 KB for typical HD thumbnail). Negligible compared to video size.

**Q: Can I see subtitles on mobile devices?**
A: Yes! Embedded subtitles work on iOS, Android, and most media player apps.

**Q: What if Hebrew subtitles don't exist?**
A: Script tries auto-generated Hebrew, then English with auto-translation as fallback.

**Q: Do chapters work in all media players?**
A: Most modern players support them (VLC, MPV, QuickTime, mobile apps). Very old players may not.

---

## 🔧 Troubleshooting

**Issue: Downloads keep failing**

- Check internet connection
- Verify yt-dlp is updated: `pip install --upgrade yt-dlp`
- Try single video first to isolate issue
- Check if video is region-restricted

**Issue: Subtitles not appearing**

- Verify media player supports embedded subtitles
- Check subtitle track in player settings
- Some videos may not have Hebrew available
- Try enabling subtitles in player controls

**Issue: Thumbnails not showing**

- Refresh file manager view
- Thumbnail generation takes a moment
- Some file managers need thumbnail cache rebuild
- Verify with media player instead

**Issue: Chapters not working**

- Not all videos have chapters
- Try viewing in VLC or MPV
- Check "Playback → Chapters" menu
- Original video may not have chapter markers

---

## 📊 Performance Impact

| Feature | File Size Impact | Download Time Impact | Quality Impact |
|---------|-----------------|---------------------|----------------|
| Subtitles | +10-50 KB | +1-2 seconds | None |
| Thumbnail | +50-200 KB | +1 second | None |
| Metadata | +5-10 KB | <1 second | None |
| Chapters | +1-5 KB | <1 second | None |
| Resume | None | Saves time on failures | None |

**Total overhead:** <500 KB and <5 seconds per video
**Benefit:** Immeasurable improvement in usability

---

This documentation covers all the new features in detail. Each feature has been designed to work together for the most robust and user-friendly downloading experience possible! 🚀
