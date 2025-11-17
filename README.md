# 📥 YT-DLP Batch Downloader

*A robust, interactive batch downloader for videos & playlists using yt-dlp*

---

## 📌 Overview

**YT-DLP Batch Downloader** is a fully interactive Bash utility that automates downloading large lists of YouTube URLs — including single videos, playlists, and mixed batches — using [`yt-dlp`](https://github.com/yt-dlp/yt-dlp).

The script provides:

* Automatic detection of `yt-dlp`
* Preview of URLs before downloading
* Clean validation & error handling
* Separate success/failure tracking
* Auto-cleanup of the batch file (removing successfully downloaded URLs)
* Pretty-printed, colorized terminal output
* Playlist-aware title extraction (each video item is tracked individually)
* Optional custom download directory

This tool is perfect for users who frequently download educational playlists, long video lists, or maintain “to-download” text files.

---

## 📁 Features

### ✔️ URL Validation

The script checks that every line is a valid URL (must begin with `http://` or `https://`).

### ✔️ Playlist Support

If a playlist is given, *each video inside is recognized and listed individually* using `yt-dlp --get-title`.

### ✔️ Automatic Directory Creation

If a download directory is missing, it is created on the fly.

### ✔️ Batch File Sync

After successful downloads:

* Completed URLs are removed from the batch file.
* Failed URLs remain for retry.

### ✔️ Detailed Summary Report

At the end you get:

* Total URLs processed
* Number of successfully downloaded videos
* Number of failures
* Full title + download path for each successful item

### ✔️ Beautiful Colored Output

Terminal output uses ANSI colors for clarity:

* **Green** → Success
* **Red** → Errors
* **Yellow** → Info/warnings
* **Blue** → Section headers

---

## 🧰 Requirements

* **Bash** (Linux or macOS)
* **yt-dlp** installed

  ```bash
  pip install yt-dlp
  ```

---

## 🚀 Usage

### Basic Usage

```bash
./yt-dlp_downloader.sh urls.txt
```

### Specify custom download directory

```bash
./yt-dlp_downloader.sh urls.txt /home/user/Videos/Linux_Playlist
```

### Batch file format

A plain text file where each line contains **one URL**:

```
https://youtube.com/watch?v=abcdef
https://youtube.com/playlist?list=12345
https://youtube.com/watch?v=xyz123
```

Empty lines are ignored.

---

## 📌 Example Session

```
========================================
   YT-DLP Batch Downloader Started
========================================

Batch file: yt-dlp-url
Download location: The_Linux_Utility
Total URLs found: 1

Preview of records:
  [1] https://youtube.com/playlist?list=PLc7...

Press Enter to start downloading...

[13:59:58] Processing [1/1]: https://youtube.com/playlist?...

✓ Success: Downloaded 2 items:
   - Arch Linux ...
   - The Linux Utility ...

========================================
          Download Summary
========================================

Successfully Downloaded:
  ✓ Arch Linux ...
    Location: The_Linux_Utility
  ✓ The Linux Utility ...
    Location: The_Linux_Utility
```

---

## 🔧 Script Arguments

| Argument              | Description                                 | Required |
| --------------------- | ------------------------------------------- | -------- |
| `<batch_file>`        | Path to text file containing URLs           | Yes      |
| `[download_location]` | Target directory; default is current folder | No       |

---

## 🛡 Error Handling

The script catches:

* Invalid URLs
* Missing batch file
* Missing yt-dlp installation
* Download failures

Failed URLs remain in the batch file for retrying.
