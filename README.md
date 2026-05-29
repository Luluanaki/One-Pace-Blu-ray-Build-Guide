# One Pace Blu-ray Build Guide
A reproducible physical media project for One Pace, featuring Blu-ray disc artwork, case covers, Avery templates, printing instructions, and archival workflow documentation. Designed to help collectors build their own set. No video files included.


> **Disclaimer:** This project is intended as a personal archival/workflow documentation project. It does not include or distribute copyrighted video files, fan edits, subtitles, or other copyrighted material.

---

## Overview

This project documents the full process used to turn a large collection of One Piece arc-based video files into a polished physical Blu-ray collection.

The general workflow is:

1. Download / gather source episodes
2. Organize files by arc
3. Inspect video/audio properties
4. Normalize inconsistent files
5. Stitch episodes by arc or disc section
6. Add chapters where useful
7. Author Blu-ray discs with menus
8. Burn to BD-R discs
9. Design and print disc labels
10. Apply labels with an alignment tool
11. Design Blu-ray case covers
12. Print, trim, and assemble the final cases

---

# Hardware Requirements

## Required

* Windows PC
* External or internal Blu-ray writer
* BD-R or BD-R DL discs
* USB storage / large internal drive
* Printer or access to a print shop
* Blu-ray cases
* Disc label applicator or printed alignment tool

## Recommended

* At least 1 TB of free storage
* SSD storage for active encoding/authoring work
* Dedicated folder structure for source, normalized, stitched, and authored files
* Blu-ray player or software player for testing
* Paper cutter or sharp hobby knife for cover trimming

---

# Software Requirements

## Core Tools

* **FFmpeg**

  * Used for video conversion, normalization, stitching, audio conversion, and chapter handling.

* **FFprobe**

  * Used to inspect codec, resolution, framerate, pixel format, audio format, and file consistency.

* **PowerShell**

  * Used for batch renaming, scanning folders, running FFmpeg commands, and automating checks.

* **TMPGEnc Authoring Works**

  * Used for Blu-ray menu creation, disc structure creation, and authoring.

## Optional Tools

* **MediaInfo**

  * Helpful for visually checking video/audio metadata.

* **MKVToolNix**

  * Useful for inspecting, remuxing, and editing MKV files.

* **Canva / Photoshop / GIMP / Affinity Designer**

  * Used for Blu-ray cover and disc label artwork.

* **Nero / ImgBurn / other disc tools**

  * Optional depending on your burning workflow.

---

# Things You May Need to Buy

## Disc Burning

* Blu-ray writer
* BD-R 25 GB discs
* BD-R DL 50 GB discs
* Spare test discs

## Labeling

* Avery full-face disc labels
* Small-hole disc labels, not large-hole CD-style labels
* Glossy or semi-gloss label sheets
* Disc label alignment tool
* Optional: custom 3D printed alignment tool
* 0.8 x 8 x 20 mm spring, if using the custom printed tool

## Packaging

* Multi-disc Blu-ray cases
* Glossy cover paper
* Access to high-quality color printing
* Paper trimmer or craft knife
* Cutting mat
* Ruler

---

# Recommended Folder Structure

```text
One Piece Archive/
│
├── Source/
│   ├── 01 - Romance Dawn/
│   ├── 02 - Orange Town/
│   └── ...
│
├── Normalized/
│   ├── 01 - Romance Dawn/
│   ├── 02 - Orange Town/
│   └── ...
│
├── Stitched/
│   ├── Disc 01/
│   ├── Disc 02/
│   └── ...
│
├── Authored Blu-ray/
│   ├── Disc 01/
│   ├── Disc 02/
│   └── ...
│
├── Labels/
│
├── Covers/
│
└── Scripts/
```

---

# Step 1: Organize the Source Files

Start by placing each arc into its own folder.

Use a consistent naming format:

```text
01 - Romance Dawn 01.mkv
01 - Romance Dawn 02.mkv
02 - Orange Town 01.mkv
02 - Orange Town 02.mkv
```

A consistent naming format makes batch scripting, stitching, menu creation, and troubleshooting much easier later.

---

# Step 2: Inspect the Files

Before stitching or authoring anything, check each arc for consistency.

Important things to inspect:

* Resolution
* Framerate
* Video codec
* Pixel format
* Audio codec
* Audio sample rate
* Number of audio channels

Example FFprobe command:

```powershell
Get-ChildItem *.mkv | ForEach-Object {
    Write-Host "==== $($_.Name) ===="
    ffprobe -v error -select_streams v:0 `
        -show_entries stream=codec_name,profile,width,height,pix_fmt,level,r_frame_rate `
        -of default=noprint_wrappers=1 "$($_.FullName)"

    ffprobe -v error -select_streams a:0 `
        -show_entries stream=codec_name,sample_rate,channels `
        -of default=noprint_wrappers=1 "$($_.FullName)"
}
```

The goal is to catch mismatches before they cause problems during stitching or Blu-ray authoring.

---

# Step 3: Normalize Problem Files

Some arcs may contain mixed resolutions, mixed framerates, or different audio formats.

Common examples:

* One file is 1080p while the rest are 720p
* Some files are 24 fps while others are 23.976 fps
* Audio differs between AAC and AC3
* One short special episode does not match the rest of the arc

When possible, normalize the odd file to match the majority of the arc.

Example: downscaling one 1080p file to 720p:

```powershell
ffmpeg -i "input.mkv" `
-vf "scale=1280:720" `
-c:v libx264 -crf 18 -preset slow `
-c:a ac3 -b:a 192k `
"output_720p.mkv"
```

For Blu-ray compatibility, AC3 audio is often safer than AAC.

---

# Step 4: Decide Disc Groupings

Plan the disc layout before authoring.

For this project, the collection was split into two major Blu-ray cases:

```text
Case 1:
Discs 1–8
East Blue through Fishman Island

Case 2:
Discs 9–16
Punk Hazard through Egghead
```

The goal is to keep arcs grouped naturally and avoid awkward splits where possible.

Sometimes a disc may contain multiple smaller arcs. Other times, a large arc may need its own disc.

---

# Step 5: Stitch Episodes

Some Blu-ray authoring software behaves better when episodes are stitched into larger arc files or disc sections.

Use FFmpeg’s concat demuxer.

Create a text file like this:

```text
file '01 - Romance Dawn 01.mkv'
file '01 - Romance Dawn 02.mkv'
file '01 - Romance Dawn 03.mkv'
```

Then run:

```powershell
ffmpeg -f concat -safe 0 -i filelist.txt -c copy "Romance Dawn Stitched.mkv"
```

If `-c copy` fails, the files are not truly compatible and need to be normalized first.

---

# Step 6: Add Chapters

Chapters are useful when multiple episodes are stitched into one file.

They allow you to jump between episodes from the Blu-ray chapter menu.

Chapters can be added with FFmpeg metadata or through authoring software, depending on your workflow.

A basic chapter metadata file looks like:

```text
;FFMETADATA1

[CHAPTER]
TIMEBASE=1/1000
START=0
END=1200000
title=Episode 01

[CHAPTER]
TIMEBASE=1/1000
START=1200000
END=2400000
title=Episode 02
```

Then mux it:

```powershell
ffmpeg -i "input.mkv" -i chapters.txt -map_metadata 1 -codec copy "output_with_chapters.mkv"
```

---

# Step 7: Author the Blu-ray

Import the final stitched files into TMPGEnc Authoring Works or another Blu-ray authoring program.

Recommended settings:

* Blu-ray Video project
* Use top menus when possible
* Create track menus / chapter menus
* Use arc names as titles
* Use episode names or numbers as chapters
* Avoid unnecessary re-encoding when possible

Watch disc size carefully. A 50 GB Blu-ray does not provide a full 50 GiB of usable space. In many authoring programs, the usable size is closer to about 44.7 GiB.

---

# Step 8: Manage Bitrate and Disc Size

If the authored project is too large, the authoring software may lower bitrate to make it fit.

This is not always bad, but the more compression you apply, the more quality you risk losing.

General guidance:

* Higher bitrate = better quality, larger file
* Lower bitrate = more content, lower quality
* 5 Mbps can fit a lot of DVD-ish quality content
* 12–16 Mbps looks better but fills discs much faster
* Long arcs may need their own disc

If a disc is only slightly oversized, reducing bitrate may be acceptable. If it is massively oversized, split the content across discs instead.

---

# Step 9: Burn the Disc

After authoring, burn the Blu-ray structure to a BD-R or BD-R DL disc.

Recommended practice:

* Use a slower burn speed for reliability
* Verify the disc after burning
* Test the disc in a Blu-ray player or software player
* Check menus, chapters, audio, and playback order

Do not label the disc until you know the burn works.

---

# Step 10: Design Disc Labels

Disc labels can make the final set look much more professional.

Use full-face small-hole Blu-ray/DVD labels, such as Avery-style labels.

https://www.avery.com/myaccount/projects

Important notes:

* Use small-hole labels if you want full-face coverage
* Avoid large-hole CD labels unless that is your intended design
* Make sure the label template matches the exact product
* Print a test on plain paper first
* Check alignment before printing on actual label sheets

---

# Step 11: Apply Disc Labels

Disc labels need to be centered carefully.

If a label is badly off-center, it can theoretically cause balance issues when the disc spins.

Recommended process:

1. Peel the label from the backing sheet.
2. Place the label adhesive-side up in the alignment tool.
3. Place the disc reading-side up.
4. Add a protective plastic disc if available.
5. Press down evenly using the pusher.
6. Smooth the label from the center outward.
7. Check for bubbles or lifted edges.

Let the label settle before putting the disc into a case.

---

# Step 12: Design Blu-ray Case Covers

For multi-disc Blu-ray cases, design a full wraparound insert:

```text
[Back Cover] [Spine] [Front Cover]
```

Include:

* Series title
* Case number
* Disc numbers
* Arc list
* Episode/chapter range
* Simple artwork
* Optional screenshots or saga labels

Example:

```text
Case 1:
East Blue to Fishman Island
Discs 1–8

Case 2:
Punk Hazard to Egghead
Discs 9–16
```

Glossy paper around 120 gsm is a good target. It is thin enough to fit in a Blu-ray sleeve but nicer than regular printer paper.

For only one or two covers, using Office Depot, Staples, FedEx Office, or another print shop may be easier than buying a large pack of specialty paper.

---

# Step 13: Final Assembly

After every disc is burned, tested, labeled, and placed into the case:

* Confirm disc order
* Confirm labels match disc numbers
* Confirm the case cover matches the disc range
* Check that all discs lock securely into the case
* Store the project files and scripts somewhere safe

Recommended backup files:

* Final stitched MKVs
* Authoring project files
* Disc label designs
* Blu-ray cover designs
* Scripts used for renaming, probing, and conversion

---

# Troubleshooting Notes

## The authoring software rejects a stitched file

Usually this means one or more source files do not match.

Check:

* Resolution
* Framerate
* Audio codec
* Audio sample rate
* Pixel format

Normalize the mismatched file and try again.

## The disc is too large

Options:

* Lower the target bitrate
* Split the disc into two discs
* Put one large arc by itself
* Remove extras or special episodes
* Re-author using fewer menu assets

## The menu disappears when there is only one track

Some authoring software may skip the top menu if there is only one title/track.

Possible workaround:

* Add a second small title
* Split the arc into multiple logical tracks
* Check project/menu settings for “always show top menu”
* Use chapter menus if top menus are unavailable

## The video has black bars

Black bars may be part of the actual video image, not just player formatting.

Check the real encoded resolution with FFprobe.

A file can be 1920x1080 while still containing 4:3 content with black bars baked into the image.

## The PS5 does not play data discs properly

The PS5 is not ideal for Blu-ray data-disc playback. Authored Blu-ray Video discs are much more compatible than MKV files burned as raw data.

---

# Useful FFmpeg Commands

## Check Resolution

```powershell
ffprobe -v error -select_streams v:0 `
-show_entries stream=width,height `
-of csv=s=x:p=0 "input.mkv"
```

## Check Framerate

```powershell
ffprobe -v error -select_streams v:0 `
-show_entries stream=r_frame_rate `
-of default=noprint_wrappers=1:nokey=1 "input.mkv"
```

## Convert Audio to AC3

```powershell
ffmpeg -i "input.mkv" `
-c:v copy `
-c:a ac3 -b:a 192k `
"output_ac3.mkv"
```

## Normalize to 1080p H.264 + AC3

```powershell
ffmpeg -i "input.mkv" `
-vf "scale=1920:1080" `
-c:v libx264 -crf 18 -preset slow `
-c:a ac3 -b:a 192k `
"output_1080p_ac3.mkv"
```

## Normalize to 720p H.264 + AC3

```powershell
ffmpeg -i "input.mkv" `
-vf "scale=1280:720" `
-c:v libx264 -crf 18 -preset slow `
-c:a ac3 -b:a 192k `
"output_720p_ac3.mkv"
```

## Stitch Compatible Files

```powershell
ffmpeg -f concat -safe 0 -i filelist.txt -c copy "stitched_output.mkv"
```

---

# Lessons Learned

* Organize everything before you start authoring.
* Normalize files before stitching.
* Do not assume files match just because they look similar.
* Short specials can cause annoying mismatches.
* Blu-ray authoring software is picky.
* 50 GB discs have less usable space than expected.
* Testing before labeling saves wasted labels.
* A clean naming convention makes the entire process easier.
* Physical presentation takes almost as much planning as the video workflow.

---

# Project Status

The full collection has been organized, burned to Blu-ray, labeled, and packaged into two multi-disc Blu-ray cases.

Final layout:

```text
Case 1:
Discs 1–8
East Blue through Fishman Island

Case 2:
Discs 9–16
Punk Hazard through Egghead
```

This README serves as a reference guide for the full process and as documentation for anyone attempting a similar personal archival project.
