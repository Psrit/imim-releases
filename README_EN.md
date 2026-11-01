<div align="center">

# imim

**Fix timestamps. Preserve memories.**

Images, Metadata & Memories

macOS 26+ · Apple Silicon · Chinese / English

[中文](README.md) · [Downloads](https://github.com/Psrit/imim-releases/releases) · [Issues](https://github.com/Psrit/imim-releases/issues)

</div>

Photos from an old phone, a trip across time zones, or a forgotten hard drive can end up in the wrong place in your library. imim helps repair their capture dates, time zones, and locations. It can also import matching photos and videos from other devices as Apple Live Photos.

This Mac app is still in early development. Photo processing happens on your Mac; photos are not uploaded to a server. Try a few copies before making a large batch of changes.

## Features

- **Browse your photos**: Switch between Apple Photos and a local folder. Double-click a photo to see its image and metadata.
- **Repair dates and locations**: Change the capture date, time zone, or coordinates. Pick a location on the map. Location editing currently supports JPEG.
- **Work in batches**: Create a repair session, analyze and group photos by capture time, then edit them together or individually before importing.
- **Import Live Photos**: Match same-name stills with MOV / MP4 videos. Pairing metadata is added to staged copies, leaving source files untouched.
- **Back up and restore**: Files are backed up before writing. Restore one photo or a whole session. Repaired library photos are imported as new assets.

## Get started

Requires **macOS 26 or later**. The current release workflow targets **Apple Silicon**; a validated Intel build is not available. The interface supports Chinese and English.

Release archives will be available on [GitHub Releases](https://github.com/Psrit/imim-releases/releases). When a build is available, download its ZIP, extract it, and drag `imim.app` into Applications. 

Builds currently use an ad-hoc signature and have no Apple Developer ID signature or notarization. macOS may block a downloaded copy on first launch. If you trust its source, follow the system prompt in System Settings → Privacy & Security → Open Anyway.

Choose your Photos library or a local folder. Library access requires permission; importing repaired copies requires Full Access.

**One photo**: Double-click it, adjust the date, time zone, or location, then save. Folder files can be overwritten, saved elsewhere, or imported into Photos. Library photos are imported as repaired copies; you decide whether to delete the originals after a successful import.

**A batch**: Select photos and click the toolbar wand to create a session. Analyze, edit, and import from the batch repair page. Sessions retain staged files and backups so you can resume or restore them.

**Live Photo import**: Put matching files such as `IMG_0001.jpg` and `IMG_0001.mp4` in one folder, then review them in Import Live Photos. This handles separate still/video pairs, rather than arbitrary vendor-specific embedded motion-photo files. When missing pairing metadata needs to be added, the still must be JPEG.

## Supported formats

Preview support does not imply that every metadata field is writable. RAW decoding also depends on macOS support for the camera format.

| Format | Capture date and time zone | Location |
| --- | --- | --- |
| JPEG | Editable; missing fields can be added | Editable or addable; protected vendor metadata may prevent writing |
| HEIC / HEIF, PNG | Editable; missing fields can be added | Read only |
| TIFF, Sony RAW (ARW / SR2) | Existing writable fields only | Read only |
| WebP, GIF, BMP | Read only | Read only |

Date edits aim to preserve image data. Adding EXIF fields can change metadata layout, and writing JPEG locations may require the system imaging framework to rewrite the file. Unsupported or unsafe writes produce an error.

Live Photo import adds pairing metadata and may remux the video container. General video capture-date editing, cloud-library comparison, and duplicate detection are not implemented.

## Your photos and backups

Library originals are never edited in place. After a repaired copy is imported, deleting the original requires confirmation and moves it to Recently Deleted in Photos. Applying changes to an original folder file does write to disk, after saving a backup.

Sessions and folder backups are stored in:

```text
~/Library/Application Support/com.xiaojx.imim/
├── sessions/
└── folder-backups/
```

Session backups provide a cumulative restore point, rather than a separate history for every edit. Deleting a session also deletes its staged photos and backups. Keep an independent backup of important photos.

Photo processing is local. Maps may use system map services, and retrieving library originals stored in iCloud may require a connection. Software update checks and downloads also use the network.

## Updates

Use Check for Updates… in the app menu, or enable automatic checks in Settings. Automatic checks are off by default. Sparkle verifies update archives using EdDSA signatures.

Installers and update feeds are hosted in a separate public distribution repository. The app source repository remains private. Older copies without an updater need a manual installation first. Sparkle signatures do not replace Apple signing or notarization.

## Feedback

[Open an issue](https://github.com/Psrit/imim-releases/issues) with your macOS version, imim version, photo format, and steps to reproduce. State whether the source is Photos or a folder. If a sample is needed, use one without private information.

## About this repository

This repository contains imim installers, update feeds, and user documentation. Application source code is not included.
