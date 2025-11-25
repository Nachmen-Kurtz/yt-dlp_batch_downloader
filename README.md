# 📥 YT-DLP Batch Downloader v2.0

<!--toc:start-->
- [📥 YT-DLP Batch Downloader v2.0](#📥-yt-dlp-batch-downloader-v20)
  - [✨ What's New in v2.0](#what-s-new-in-v20)
  - [🎬 Quick Start](#🎬-quick-start)
    - [Installation](#installation)
    - [Basic Usage](#basic-usage)
  - [📖 Table of Contents](#📖-table-of-contents)
  - [🌟 Features Overview](#🌟-features-overview)
    - [🎯 Core Download Features](#🎯-core-download-features)
    - [🎨 Media Enhancement](#🎨-media-enhancement)
    - [🌍 Accessibility](#🌍-accessibility)
    - [💻 User Experience](#💻-user-experience)
  - [🔍 Detailed Features](#🔍-detailed-features)
    - [1. 🔄 Resume & Recovery System](#1-🔄-resume-recovery-system)
    - [2. 🛡️ Overwrite Protection](#2-🛡️-overwrite-protection)
    - [3. 🖼️ Thumbnail Embedding](#3-🖼️-thumbnail-embedding)
    - [4. 📋 Metadata Tagging](#4-📋-metadata-tagging)
    - [5. 🇮🇱 Hebrew Subtitle System](#5-🇮🇱-hebrew-subtitle-system)
    - [6. 📑 Chapter Preservation](#6-📑-chapter-preservation)
  - [📚 Usage Examples](#📚-usage-examples)
    - [Example 1: Simple Video Download](#example-1-simple-video-download)
    - [Example 2: Educational Playlist](#example-2-educational-playlist)
    - [Example 3: Mixed Batch with Recovery](#example-3-mixed-batch-with-recovery)
    - [Example 4: Large Batch Overnight](#example-4-large-batch-overnight)
  - [🔧 Requirements](#🔧-requirements)
    - [Required](#required)
    - [Optional (Recommended)](#optional-recommended)
    - [Check Your System](#check-your-system)
  - [📦 Installation Guide](#📦-installation-guide)
    - [Method 1: Quick Install (Recommended)](#method-1-quick-install-recommended)
    - [Method 2: Clone Repository](#method-2-clone-repository)
    - [Method 3: System-Wide Installation](#method-3-system-wide-installation)
  - [⚙️ How It Works](#️-how-it-works)
    - [Workflow Diagram](#workflow-diagram)
    - [Behind the Scenes: yt-dlp Command](#behind-the-scenes-yt-dlp-command)
  - [📋 Batch File Format](#📋-batch-file-format)
    - [Basic Format](#basic-format)
    - [Rules](#rules)
    - [Mixed Batch Example](#mixed-batch-example)
    - [Tips](#tips)
  - [🚀 Advanced Usage](#🚀-advanced-usage)
    - [Custom Output Directory Structure](#custom-output-directory-structure)
    - [Run in Background](#run-in-background)
    - [Batch File Management](#batch-file-management)
    - [Update yt-dlp Regularly](#update-yt-dlp-regularly)
  - [🐛 Troubleshooting](#🐛-troubleshooting)
    - [Common Issues](#common-issues)
      - [1. "yt-dlp: command not found"](#1-yt-dlp-command-not-found)
      - [2. "Permission denied" when running script](#2-permission-denied-when-running-script)
      - [3. Downloads failing with "HTTP Error 403"](#3-downloads-failing-with-http-error-403)
      - [4. No Hebrew subtitles appearing](#4-no-hebrew-subtitles-appearing)
      - [5. Thumbnails not showing in file manager](#5-thumbnails-not-showing-in-file-manager)
      - [6. "Video unavailable" errors](#6-video-unavailable-errors)
    - [Debug Mode](#debug-mode)
    - [Getting Help](#getting-help)
  - [📊 Performance](#📊-performance)
    - [Speed Expectations](#speed-expectations)
    - [Disk Space](#disk-space)
    - [Resource Usage](#resource-usage)
  - [🤝 Contributing](#🤝-contributing)
  - [📄 License](#📄-license)
  - [🙏 Acknowledgments](#🙏-acknowledgments)
  - [📞 Support & Contact](#📞-support-contact)
  - [🗺️ Roadmap](#🗺️-roadmap)
    - [Planned Features (v2.1+)](#planned-features-v21)
  - [⭐ Star This Project](#star-this-project)
  - [📸 Screenshots](#📸-screenshots)
    - [Terminal Output](#terminal-output)
<!--toc:end-->

> **A professional-grade, feature-rich batch downloader for YouTube videos using yt-dlp**

[![License: GPL v3+](https://img.shields.io/badge/License-GPLv3+-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Bash](https://img.shields.io/badge/bash-5.0+-green.svg)](https://www.gnu.org/software/bash/)
[![yt-dlp](https://img.shields.io/badge/yt--dlp-latest-red.svg)](https://github.com/yt-dlp/yt-dlp)

---

## ✨ What's New in v2.0

🎯 **Resume Support** - Never restart downloads from scratch  
🛡️ **Overwrite Protection** - Safe to re-run on same batch  
🌐 **Network Resilience** - 10x retry with smart delays  
🖼️ **Thumbnail Embedding** - Beautiful cover art like music files  
📋 **Metadata Tagging** - Full info (title, author, date, description)  
🇮🇱 **Hebrew Subtitles** - Auto-download with translation fallback  
📑 **Chapter Preservation** - Navigate videos by sections  

---

## 🎬 Quick Start

### Installation

```bash
# 1. Install yt-dlp
pip install yt-dlp

# 2. Download the script
wget https://your-repo/yt-dlp_downloader.sh
# or
curl -O https://your-repo/yt-dlp_downloader.sh

# 3. Make executable
chmod +x yt-dlp_downloader.sh
```

### Basic Usage

```bash
# Create a text file with video URLs (one per line)
cat > urls.txt << EOF
https://youtube.com/watch?v=VIDEO_ID_1
https://youtube.com/watch?v=VIDEO_ID_2
https://youtube.com/playlist?list=PLAYLIST_ID
EOF

# Run the downloader
./yt-dlp_downloader.sh urls.txt

# Or specify custom download directory
./yt-dlp_downloader.sh urls.txt /path/to/Videos/
```

That's it! 🚀

---

## 📖 Table of Contents

- [Features Overview](#-features-overview)
- [Detailed Features](#-detailed-features)
- [Usage Examples](#-usage-examples)
- [Requirements](#-requirements)
- [Installation Guide](#-installation-guide)
- [How It Works](#-how-it-works)
- [Output Format](#-output-format)
- [Batch File Format](#-batch-file-format)
- [Advanced Usage](#-advanced-usage)
- [Troubleshooting](#-troubleshooting)
- [Performance](#-performance)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌟 Features Overview

### 🎯 Core Download Features

| Feature | Description | Benefit |
|---------|-------------|---------|
| **Batch Processing** | Process multiple URLs from text file | Download entire playlists/courses at once |
| **Resume Support** | Continue interrupted downloads | Save bandwidth on connection drops |
| **Overwrite Protection** | Never replace existing files | Safe to re-run, protects your downloads |
| **Smart Retry System** | 10 retries with 5s delays | Handles network hiccups automatically |
| **Fragment Recovery** | Retry individual stream fragments | Reliable for HLS/DASH videos |
| **Playlist Support** | Tracks each video individually | Clear progress for large playlists |
| **Auto Cleanup** | Removes successful URLs from batch | Easy retry of only failed downloads |

### 🎨 Media Enhancement

| Feature | Description | Result |
|---------|-------------|--------|
| **Thumbnail Embedding** | Video thumbnail as cover art | Beautiful file icons, player previews |
| **Metadata Tagging** | Title, author, date, description | Organize like music library |
| **Chapter Preservation** | Section markers from YouTube | Navigate long videos easily |
| **SponsorBlock Marking** | Mark sponsor/filler segments | Optional skip segments |

### 🌍 Accessibility

| Feature | Description | Languages |
|---------|-------------|-----------|
| **Hebrew Subtitles** | Auto-download with translation | Hebrew (manual/auto/translated) |
| **Multi-language Support** | Fallback subtitle chain | Hebrew → English → Auto-generated |
| **Subtitle Embedding** | Built into video file | Works on all devices |
| **Format Conversion** | Universal SRT format | Maximum compatibility |

### 💻 User Experience

| Feature | Description | Value |
|---------|-------------|-------|
| **Colorized Output** | Pretty terminal colors | Easy to read status |
| **Progress Tracking** | Real-time download progress | Know exactly where you are |
| **URL Preview** | See URLs before downloading | Verify batch before starting |
| **Detailed Summary** | Complete success/failure report | Full download accountability |
| **Status Indicators** | Visual success/failure marks | Quick status recognition |

---

## 🔍 Detailed Features

### 1. 🔄 Resume & Recovery System

**The Problem:** You're downloading a 2GB video at 80% complete when your internet drops. Traditional downloaders restart from 0%.

**The Solution:**

```bash
Download: video.mp4.part (0% → 80%) [Connection Lost]
Resume:   video.mp4.part (80% → 100%) [Success!]
```

**Three-Layer Protection:**

1. **Download Resume** (`--continue`)
   - Picks up from exact byte position
   - No wasted bandwidth
   - Works for any size file

2. **Connection Retry** (`--retries 10`)
   - Retries entire download up to 10 times
   - Handles DNS, timeout, server errors
   - Eventually succeeds on intermittent issues

3. **Fragment Retry** (`--fragment-retries 10`)
   - For streaming videos (HLS/DASH)
   - Retries only the failed 2-10 second fragment
   - Much faster than full retry

4. **Smart Delays** (`--retry-sleep 5`)
   - Waits 5 seconds between retries
   - Prevents server hammering
   - Increases success rate

**Real-World Benefit:**
> "I downloaded a 6-hour lecture series overnight on spotty hotel WiFi. Had 8 connection drops but all videos completed by morning thanks to auto-retry!" - Happy User

### 2. 🛡️ Overwrite Protection

**The Problem:** You accidentally run the script twice on the same batch file and all your carefully curated downloads get replaced with fresh downloads (losing any edits, metadata, or partial progress).

**The Solution:**

```bash
# First run
./script.sh urls.txt          # Downloads everything

# Second run (accidental)
./script.sh urls.txt          # Skips all existing files ✓
```

**Behavior:**

- ✅ Complete file exists → Skip entirely
- ✅ Partial file exists (`.part`) → Resume from position
- ✅ File doesn't exist → Download normally

### 3. 🖼️ Thumbnail Embedding

**Before:** Generic video icons  
**After:** Beautiful cover art showing video preview

**Where You'll See It:**

- 📁 File Manager: Thumbnail preview on icon
- 🎵 Media Players: Cover art like music albums
- 📱 Mobile Devices: Video gallery thumbnails
- 📺 Media Servers: Plex/Jellyfin artwork

**Technical:**

- Downloads highest quality thumbnail available
- Embeds into video container (MP4/MKV)
- ~100-200 KB file size increase
- No quality loss to video

### 4. 📋 Metadata Tagging

**Like ID3 Tags for Music, But for Videos:**

```
📄 video.mp4
├── Title: "Advanced Python Tutorial - Part 1"
├── Author: "Tech Education Channel"
├── Date: "2024-11-20"
├── Description: "Learn advanced Python concepts..."
├── URL: "https://youtube.com/watch?v=..."
├── Duration: "45:32"
└── Genre: "Education"
```

**View Metadata:**

```bash
# Linux/macOS
ffprobe video.mp4
mediainfo video.mp4
exiftool video.mp4

# Windows
Right-click → Properties → Details tab
```

**Benefits:**

- 🔍 Search videos by author/date in media players
- 📚 Organize video library like music collection
- 🏷️ Remember video source years later
- 🎯 Professional media management

### 5. 🇮🇱 Hebrew Subtitle System

**Smart Priority Chain:**

```
1st Attempt: Manual Hebrew subtitles (creator-provided) ⭐ Best
     ↓ Not available?
2nd Attempt: Auto-generated Hebrew (YouTube speech recognition)
     ↓ Not available?
3rd Attempt: English → Hebrew auto-translation
     ↓ Not available?
4th Attempt: Any Hebrew variant (he-IL, he-auto, etc.)
```

**Features:**

- ✅ Embedded in video file (no separate .srt needed)
- ✅ Toggle on/off in any media player
- ✅ SRT format (universal compatibility)
- ✅ Works on mobile devices
- ✅ Multiple subtitle tracks supported (MKV)

**Practical Example:**

```
Hebrew Tutorial Video:
├── Video Track: Main content
├── Audio Track: Hebrew speech
└── Subtitle Tracks:
    ├── Hebrew (manual) ✓ Active by default
    └── English (auto-translated)
```

### 6. 📑 Chapter Preservation

**What Are Chapters?**

Think of them as bookmarks in a video:

```
0:00 - Introduction
3:15 - Setup and Installation  
8:45 - Basic Concepts
15:30 - Advanced Techniques
22:10 - Real-World Examples
28:00 - Conclusion
```

**Chapter Sources:**

1. **Creator Chapters**: Set by uploader in description
2. **Auto-Generated**: YouTube's AI analysis
3. **SponsorBlock**: Community-marked segments

**Use Chapters:**

- **VLC**: Playback → Chapter → Select chapter
- **MPV**: Press `j` (previous) / `k` (next chapter)
- **Mobile Players**: Chapter list in controls
- **Smart TVs**: Chapter navigation in UI

**Perfect For:**

- 🎓 Educational videos (jump to specific topics)
- 🎬 Long-form content (skip to sections)
- 🎙️ Podcasts (find specific guests/topics)
- 📺 Tutorials (repeat specific steps)

---

## 📚 Usage Examples

### Example 1: Simple Video Download

```bash
# Create batch file
echo "https://youtube.com/watch?v=dQw4w9WgXcQ" > video.txt

# Download
./yt-dlp_downloader.sh video.txt

# Result: Video with all features enabled
```

### Example 2: Educational Playlist

```bash
# Playlist batch file
cat > course.txt << EOF
https://youtube.com/playlist?list=PLu9XJgzPl0123456789
EOF

# Download to specific folder
./yt-dlp_downloader.sh course.txt ~/Videos/Python_Course/

# Result: All videos with Hebrew subs, chapters, metadata
```

### Example 3: Mixed Batch with Recovery

```bash
# Create mixed batch
cat > mixed.txt << EOF
https://youtube.com/watch?v=VIDEO1
https://youtube.com/watch?v=VIDEO2
https://youtube.com/playlist?list=PLAYLIST1
https://youtube.com/watch?v=VIDEO3
EOF

# Start download (connection drops at VIDEO2)
./yt-dlp_downloader.sh mixed.txt

# Script auto-retries, VIDEO2 resumes
# If VIDEO2 still fails, it stays in mixed.txt
# VIDEO1 is removed (successful)
# VIDEO3 and PLAYLIST1 continue

# Re-run to retry only failures
./yt-dlp_downloader.sh mixed.txt
```

### Example 4: Large Batch Overnight

```bash
# 50 video batch file
cat > overnight.txt << EOF
https://youtube.com/watch?v=VID1
https://youtube.com/watch?v=VID2
... (48 more lines)
EOF

# Start download and leave running
nohup ./yt-dlp_downloader.sh overnight.txt ~/Videos/ &

# Check progress anytime
tail -f nohup.out

# Next morning: All completed or failed URLs remain for retry
```

---

## 🔧 Requirements

### Required

- **Operating System**: Linux, macOS, or WSL/Git Bash on Windows
- **Bash**: Version 5.0 or higher
- **yt-dlp**: Latest version (`pip install yt-dlp`)
- **Python**: 3.7+ (for yt-dlp)
- **Internet**: Active connection

### Optional (Recommended)

- **ffmpeg**: For advanced encoding/embedding (usually auto-installed with yt-dlp)
- **curl/wget**: For downloading script itself

### Check Your System

```bash
# Check Bash version
bash --version

# Check yt-dlp
yt-dlp --version

# Check Python
python3 --version

# Check ffmpeg (optional but recommended)
ffmpeg -version
```

---

## 📦 Installation Guide

### Method 1: Quick Install (Recommended)

```bash
# Download script
curl -O https://raw.githubusercontent.com/yt-dlp-batch-downloader/yt-dlp_downloader.sh

# Make executable
chmod +x yt-dlp_downloader.sh

# Install yt-dlp
pip install yt-dlp

# Done! Run it
./yt-dlp_downloader.sh
```

### Method 2: Clone Repository

```bash
# Clone repo
git clone https://github.com/yt-dlp-batch-downloader/yt-dlp-batch-downloader.git
cd yt-dlp-batch-downloader

# Make executable
chmod +x yt-dlp_downloader.sh

# Install dependencies
pip install yt-dlp

# Run
./yt-dlp_downloader.sh urls.txt
```

### Method 3: System-Wide Installation

```bash
# Download and install to /usr/local/bin
sudo curl -o /usr/local/bin/yt-batch https://raw.githubusercontent.com/yt-dlp-batch-downloader/yt-dlp_downloader.sh
sudo chmod +x /usr/local/bin/yt-batch

# Now run from anywhere
yt-batch urls.txt
```

---

## ⚙️ How It Works

### Workflow Diagram

```
┌─────────────────────────────────────────────────────┐
│ 1. Read Batch File (urls.txt)                      │
│    - Count URLs                                     │
│    - Validate format (http/https)                  │
│    - Show preview                                   │
└─────────────────────────────────────────────────────┘
                        ↓
┌─────────────────────────────────────────────────────┐
│ 2. Process Each URL                                 │
│    - Check if file exists (--no-overwrites)        │
│    - Check for .part file (--continue)             │
│    - Download with all features                     │
│    - Handle errors with retries                     │
└─────────────────────────────────────────────────────┘
                        ↓
┌─────────────────────────────────────────────────────┐
│ 3. Post-Processing Per Video                       │
│    - Embed subtitles                                │
│    - Embed thumbnail                                │
│    - Embed metadata                                 │
│    - Embed chapters                                 │
│    - Track success/failure                          │
└─────────────────────────────────────────────────────┘
                        ↓
┌─────────────────────────────────────────────────────┐
│ 4. Update Batch File                                │
│    - Remove successful URLs                         │
│    - Keep failed URLs for retry                     │
│    - Clear file if all successful                   │
└─────────────────────────────────────────────────────┘
                        ↓
┌─────────────────────────────────────────────────────┐
│ 5. Display Summary Report                           │
│    - Total processed                                │
│    - Success count with titles                      │
│    - Failure list with URLs                         │
│    - Download locations                             │
└─────────────────────────────────────────────────────┘
```

### Behind the Scenes: yt-dlp Command

```bash
yt-dlp \
  --no-playlist \                    # Single video mode (not whole playlist)
  --output "%(title)s.%(ext)s" \     # Filename: Video_Title.mp4
  --no-mtime \                       # Don't preserve upload date as file mod time
  --progress \                       # Show download progress bar
  --write-description \              # Save video description to .description file
  --write-subs \                     # Download manual subtitles
  --write-auto-subs \                # Download auto-generated subtitles
  --sub-langs "he.*,en.*" \          # Hebrew & English subtitles
  --convert-subs srt \               # Convert to SRT format
  --embed-subs \                     # Embed into video file
  --embed-chapters \                 # Embed chapter markers
  --embed-thumbnail \                # Embed thumbnail as cover art
  --embed-metadata \                 # Embed JSON metadata
  --add-metadata \                   # Add human-readable tags
  --sponsorblock-mark all \          # Mark SponsorBlock segments
  --no-overwrites \                  # Don't replace existing files
  --continue \                       # Resume interrupted downloads
  --retries 10 \                     # Retry failed downloads 10 times
  --fragment-retries 10 \            # Retry stream fragments 10 times
  --retry-sleep 5 \                  # Wait 5 seconds between retries
  "VIDEO_URL"                        # The video URL
```

---

## 📋 Batch File Format

### Basic Format

```
https://youtube.com/watch?v=VIDEO_ID_1
https://youtube.com/watch?v=VIDEO_ID_2
https://youtube.com/watch?v=VIDEO_ID_3
```

### Rules

✅ **Valid:**

- One URL per line
- Must start with `http://` or `https://`
- Empty lines are ignored
- Supports YouTube videos and playlists
- Supports other yt-dlp compatible sites

❌ **Invalid:**

- URLs without protocol: `youtube.com/watch?v=...` ❌
- Multiple URLs per line ❌
- Comments or annotations (will be treated as invalid URLs) ❌

### Mixed Batch Example

```
# ✅ This works:
https://youtube.com/watch?v=singleVideo1
https://youtube.com/playlist?list=playlistID
https://youtube.com/watch?v=singleVideo2

https://youtube.com/watch?v=singleVideo3

# Note: Empty lines above are fine
```

### Tips

- **Organize by topic**: Create separate batch files per course/topic
- **Use descriptive names**: `python_course.txt`, `music_theory.txt`
- **Keep originals**: Backup batch files before running (they get modified)
- **Test small first**: Try 2-3 URLs before large batches

---

## 🚀 Advanced Usage

### Custom Output Directory Structure

```bash
# Organize by date
./yt-dlp_downloader.sh urls.txt ~/Videos/$(date +%Y-%m-%d)/

# Organize by category
./yt-dlp_downloader.sh python.txt ~/Videos/Tutorials/Python/
./yt-dlp_downloader.sh music.txt ~/Videos/Entertainment/Music/
```

### Run in Background

```bash
# Using nohup (output to nohup.out)
nohup ./yt-dlp_downloader.sh large_batch.txt ~/Videos/ &

# Using screen (detachable session)
screen -S downloads
./yt-dlp_downloader.sh large_batch.txt ~/Videos/
# Press Ctrl+A then D to detach
# Reattach with: screen -r downloads

# Using tmux (modern alternative)
tmux new -s downloads
./yt-dlp_downloader.sh large_batch.txt ~/Videos/
# Press Ctrl+B then D to detach
# Reattach with: tmux attach -t downloads
```

### Batch File Management

```bash
# Split large batch into smaller chunks
split -l 10 huge_batch.txt batch_part_

# Results in: batch_part_aa, batch_part_ab, etc.
# Process each separately:
for file in batch_part_*; do
  ./yt-dlp_downloader.sh "$file" ~/Videos/
done

# Merge failed URLs from multiple runs
cat batch1.txt batch2.txt batch3.txt > failures_combined.txt
./yt-dlp_downloader.sh failures_combined.txt ~/Videos/
```

### Update yt-dlp Regularly

```bash
# YouTube changes frequently, keep yt-dlp updated
pip install --upgrade yt-dlp

# Check version
yt-dlp --version
```

---

## 🐛 Troubleshooting

### Common Issues

#### 1. "yt-dlp: command not found"

**Solution:**

```bash
# Install yt-dlp
pip install yt-dlp

# Or with pip3
pip3 install yt-dlp

# Add to PATH if needed
export PATH="$HOME/.local/bin:$PATH"
```

#### 2. "Permission denied" when running script

**Solution:**

```bash
chmod +x yt-dlp_downloader.sh
```

#### 3. Downloads failing with "HTTP Error 403"

**Cause:** YouTube blocking or rate-limiting

**Solution:**

```bash
# Update yt-dlp (fixes most YouTube blocks)
pip install --upgrade yt-dlp

# Wait a few minutes and retry
# The script's 5-second retry delay helps with this
```

#### 4. No Hebrew subtitles appearing

**Possible causes:**

- Video doesn't have Hebrew subtitles (not even auto-generated)
- Media player doesn't show embedded subtitles

**Solution:**

```bash
# Check if subtitles were downloaded
ffprobe video.mp4 | grep Subtitle

# Enable subtitles in media player:
# VLC: Subtitle → Sub Track → Hebrew
# MPV: Press 'j' to cycle subtitle tracks
```

#### 5. Thumbnails not showing in file manager

**Solution:**

```bash
# Refresh thumbnail cache
# GNOME/Ubuntu:
rm -rf ~/.cache/thumbnails/

# KDE/Plasma:
rm -rf ~/.cache/thumbnails/

# Then refresh file manager (F5)
```

#### 6. "Video unavailable" errors

**Possible causes:**

- Video was deleted/privated
- Region restrictions
- Age restrictions
- URL is incorrect

**Solution:**

```bash
# Test URL manually
yt-dlp --simulate "URL"

# Check if video exists in browser
# Remove failed URL from batch file
```

### Debug Mode

```bash
# Run with verbose output for debugging
yt-dlp --verbose "URL" 2>&1 | tee debug.log

# Check what yt-dlp sees
yt-dlp --dump-json "URL" | jq
```

### Getting Help

1. **Check yt-dlp documentation**: `yt-dlp --help`
2. **Search existing issues**: [yt-dlp GitHub Issues](https://github.com/yt-dlp/yt-dlp/issues)
3. **Update everything**: `pip install --upgrade yt-dlp`
4. **Open an issue**: Provide batch file (without private URLs) and error output

---

## 📊 Performance

### Speed Expectations

| Video Length | File Size | Download Time (10 Mbps) | With Retries |
|--------------|-----------|-------------------------|--------------|
| 5 minutes    | ~50 MB    | ~40 seconds            | +5-10s       |
| 30 minutes   | ~300 MB   | ~4 minutes             | +10-20s      |
| 1 hour       | ~600 MB   | ~8 minutes             | +20-30s      |
| 2 hours      | ~1.2 GB   | ~16 minutes            | +30-60s      |

*Processing overhead (subtitles, metadata, thumbnails) adds <5 seconds per video*

### Disk Space

**Per video:**

- Video: 500 MB (average 1080p, 1 hour)
- Thumbnail: ~150 KB
- Subtitles: ~30 KB (embedded)
- Metadata: ~10 KB (embedded)
- Description: ~5 KB (separate .description file)
- **Total: ~500.2 MB**

**For 100 videos:** ~50 GB + 500 MB overhead

### Resource Usage

- **CPU**: Low (5-10% during download, brief spikes for embedding)
- **RAM**: ~100-200 MB per download
- **Network**: Uses available bandwidth (yt-dlp auto-throttles)
- **Disk I/O**: Moderate during download, brief spikes for embedding

---

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for:

- Code of conduct
- How to contribute
- Development setup
- Testing guidelines
- Pull request process
- Coding style

**Quick Contributions:**

- 🐛 Report bugs
- ✨ Suggest features
- 📚 Improve documentation
- 🧪 Test on different platforms
- 🌍 Translate to other languages

---

## 📄 License

This project is licensed under the **GNU General Public License v3.0 or later** (GPL-3.0-or-later).

**What this means:**

- ✅ Free to use for any purpose
- ✅ Free to modify and distribute
- ✅ Must share modifications under same license
- ✅ Must include copyright and license notices
- ❌ No warranty provided

See [LICENSE](LICENSE) file for full text.

---

## 🙏 Acknowledgments

- **[yt-dlp](https://github.com/yt-dlp/yt-dlp)**: The powerful engine behind this script
- **Contributors**: Everyone who has helped improve this project
- **Community**: For feedback, bug reports, and feature suggestions

---

## 📞 Support & Contact

- **Issues**: [GitHub Issues](https://github.com/YOUR_REPO/issues)
- **Discussions**: [GitHub Discussions](https://github.com/YOUR_REPO/discussions)
- **Documentation**: [Full documentation](https://github.com/YOUR_REPO/wiki)

---

## 🗺️ Roadmap

### Planned Features (v2.1+)

- [ ] Quality selection (720p, 1080p, 4K presets)
- [ ] Audio-only download mode
- [ ] Parallel downloads (multiple videos at once)
- [ ] Configuration file support
- [ ] Download history/log file
- [ ] Progress bar for entire batch
- [ ] Estimated time remaining
- [ ] Bandwidth limiting option
- [ ] Email notification on completion
- [ ] Web interface for batch management

See [CHANGELOG.md](CHANGELOG.md) for version history.

---

## ⭐ Star This Project

If you find this useful, please star the repository! It helps others discover the project.

---

## 📸 Screenshots

### Terminal Output

```
========================================
   YT-DLP Batch Downloader v2.0
========================================

Batch file: educational_videos.txt
Download location: ~/Videos/Courses/
Total URLs found: 5
Features: Hebrew subs, Chapters, Thumbnails, Metadata, Resume support

Preview of records:
  [1] https://youtube.com/watch?v=abc123
  [2] https://youtube.com/watch?v=def456
  [3] https://youtube.com/playlist?list=xyz789
  ...

Press Enter to start downloading...

[14:32:10] Processing [1/5]: https://youtube.com/watch?v=abc123
[download] 100% of 523.45MiB in 00:04:32

✓ Success: Introduction to Python Programming
  Subtitles: Hebrew + Auto-translated (embedded)
  Chapters: Preserved in video
  Thumbnail: Embedded as cover art
  Metadata: Title, author, date tagged

========================================
          Download Summary
========================================

Total URLs: 5
Successfully downloaded items: 12
Failed URLs: 0

Successfully Downloaded:
  ✓ Introduction to Python Programming
    Location: ~/Videos/Courses/
    Features: Hebrew subs, Chapters, Thumbnail, Metadata, Resume-safe
  
  ✓ Python Data Structures
    Location: ~/Videos/Courses/
    Features: Hebrew subs, Chapters, Thumbnail, Metadata, Resume-safe

========================================
Enjoy watching and fruitful learning!
========================================
```

---

<div align="center">

**Made with ❤️ for the learning community**

[⬆ Back to Top](#-yt-dlp-batch-downloader-v20)

</div>
