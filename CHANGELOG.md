# Changelog

<!--toc:start-->
- [Changelog](#changelog)
  - [[2.0.0] - 2025-11-25](#200-2025-11-25)
    - [✨ Added](#added)
    - [📝 Documentation](#📝-documentation)
    - [🔧 Technical Changes](#🔧-technical-changes)
  - [[1.0.0] - 2025-11-24](#100-2025-11-24)
    - [🎉 Initial Release](#🎉-initial-release)
      - [Features](#features)
      - [Output Colors](#output-colors)
      - [Requirements](#requirements)
  - [[Unreleased]](#unreleased)
    - [🔮 Planned Features](#🔮-planned-features)
    - [🐛 Known Issues](#🐛-known-issues)
  - [Version History Summary](#version-history-summary)
  - [Support](#support)
  - [License](#license)
<!--toc:end-->

All notable changes to YT-DLP Batch Downloader will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.0.0] - 2025-11-25

### ✨ Added

- **Hebrew Subtitle Support**: Automatic download of Hebrew subtitles with auto-translation fallback
  - Uses `--sub-langs "he.*,en.*"` to prioritize Hebrew and English subtitles
  - Automatically downloads auto-generated subtitles when manual ones are unavailable
  - Converts subtitles to SRT format for maximum compatibility
  - Embeds subtitles directly into video files for seamless playback
  
- **Chapter/Section Preservation**: Videos with chapters/sections maintain their structure
  - Uses `--embed-chapters` to preserve chapter information in downloaded videos
  - Chapter markers remain intact for easy navigation
  - SponsorBlock markers included for all segment types

- **Thumbnail/Cover Art Embedding**: Video thumbnails embedded as cover art
  - Uses `--embed-thumbnail` to embed video thumbnail into file
  - Cover art displays in media players like VLC, MPV, and mobile players
  - High-quality thumbnail preserved from original source

- **Metadata Tagging**: Complete metadata tagging like music files
  - Uses `--embed-metadata` and `--add-metadata` for comprehensive tagging
  - Includes title, author, upload date, description, and more
  - Metadata visible in all modern media players
  - Helps organize video libraries effectively

- **Resume & Recovery Support**: Robust download continuation capabilities
  - Uses `--continue` to resume interrupted downloads from last position
  - Uses `--no-overwrites` to prevent accidental file overwriting
  - Automatic retry with `--retries 10` for network failures
  - Fragment-level retry with `--fragment-retries 10` for streaming videos
  - Smart retry delay with `--retry-sleep 5` to avoid hammering servers
  - Perfect for unstable connections or large file downloads
  
- **Enhanced Download Information Display**: Shows all embedded features status
  - Real-time feedback about embedded features
  - Clear indication of available accessibility features
  - Resume-safe status confirmation

### 📝 Documentation

- Added comprehensive `CHANGELOG.md` file
- Added `CONTRIBUTING.md` with contribution guidelines
- Updated README with new features documentation

### 🔧 Technical Changes

- Added `--write-subs` flag for manual subtitle download
- Added `--write-auto-subs` flag for auto-generated subtitle download
- Added `--convert-subs srt` for subtitle format standardization
- Added `--embed-subs` for subtitle embedding into video container
- Added `--embed-chapters` for chapter metadata preservation
- Added `--embed-thumbnail` for cover art embedding
- Added `--embed-metadata` and `--add-metadata` for comprehensive tagging
- Added `--no-overwrites` to prevent accidental file replacement
- Added `--continue` for resuming interrupted downloads
- Added `--retries 10` for automatic network failure recovery
- Added `--fragment-retries 10` for streaming video fragment recovery
- Added `--retry-sleep 5` for smart retry delays
- Added `--sponsorblock-mark all` for segment marking (optional feature)

---

## [1.0.0] - 2025-11-24

### 🎉 Initial Release

#### Features

- Batch downloading of multiple YouTube URLs from text file
- Automatic `yt-dlp` installation detection
- URL validation (http/https format checking)
- Interactive preview of URLs before downloading
- Playlist support with individual video tracking
- Automatic download directory creation
- Success/failure tracking with detailed reporting
- Automatic batch file cleanup (removes successful URLs)
- Colorized terminal output for better readability
- Progress indicators during downloads
- Video description file saving
- Custom download directory support
- Comprehensive error handling
- Retry mechanism for failed downloads

#### Output Colors

- 🟢 Green: Success messages
- 🔴 Red: Errors and failures
- 🟡 Yellow: Warnings and information
- 🔵 Blue: Section headers and metadata

#### Requirements

- Bash shell (Linux/macOS)
- yt-dlp installed via pip
- Internet connection for downloading

---

## [Unreleased]

### 🔮 Planned Features

- Quality selection presets (720p, 1080p, 4K)
- Audio-only download mode
- Custom subtitle language selection via command-line flag
- Download history logging to external file
- Parallel download support for faster batch processing
- Integration with download managers
- Configuration file support for default settings
- Metadata extraction and JSON export
- Bandwidth limiting options
- Download scheduling

### 🐛 Known Issues

None reported yet. Please open an issue on the project repository if you encounter any problems.

---

## Version History Summary

| Version | Date       | Key Features                                      |
|---------|------------|---------------------------------------------------|
| 2.0.0   | 2025-11-25 | Hebrew subtitles, Chapter preservation, Enhanced UI |
| 1.0.0   | 2025-11-24 | Initial release with batch download capabilities  |

---

## Support

For bug reports, feature requests, or questions:

- Open an issue on the GitHub repository
- Check existing issues before creating a new one
- Include your yt-dlp version and OS information

## License

This project is licensed under GPL v3+ - see the LICENSE file for details.
