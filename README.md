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

### **Windows PC**

* TMPGEnc Authoring Works 7 is Windows-only, so a Windows PC is required for the authoring portion of this guide.

### [**External**](https://www.microcenter.com/product/690617/verbatim-ultra-hd-4k-usb-32-gen-1-blu-ray-writer) **or Internal Blu-ray Writer**

* Any Blu-ray writer that supports **BD-R** and **BD-R DL** media should work.
* USB 3.0 is recommended but not required.
* Burn speed is not particularly important since this guide recommends writing discs at **2x speed** for reliability rather than maximum speed.

### [**BD-R / BD-R DL Discs**](https://a.co/d/0aujSNa2)

* 50 GB BD-R DL discs are recommended for this project in order to maximize content per disc.
* Depending on your preferred disc layout and bitrate settings, standard 25 GB BD-R discs may also be usable for some content.

### **Blu-ray Cases**

* [Individual Cases](https://a.co/d/0coLu6g3)
* [8-Disc Cases](https://a.co/d/0g0iiGoA)

*This repository includes artwork for 8-disc cases. However, Canva templates and source files are provided if you would like to create artwork for individual cases or other case formats.*

### **Printer or Access to a Print Shop**

* Required for printing disc labels and case artwork.
* Local print shops such as Office Depot, Staples, or FedEx Office can be a convenient option if you only need a few copies.

### [**Avery Full-Face Disc Labels**](https://a.co/d/02zhhNVN)

* Either **Glossy** or **Matte** labels work well.
* Make sure to purchase the **Full-Face** version or it won't properly fit the BD-R discs.




## Recommended

* **At least 400 GB of free storage**

  * *The complete One Pace collection occupied approximately 254.42 GB immediately after download. Additional space will be needed for processing and authoring.*

* **Blu-ray player or software player for testing**

  * *A PS5 was used for testing throughout this project.*

* **Paper cutter or sharp hobby knife**

  * *Useful for trimming printed case artwork.*

* **Label Applicator Tool**

  * Buy one or [3D print one](https://www.printables.com/model/1735505-diy-disc-label-alignment-tool) if you have the means.
  * *Make sure it is designed for full-face labels.*
  * Or just eyeball it and hope for the best.


---

# Software Requirements

## Core Tools

* **[FFmpeg](https://www.gyan.dev/ffmpeg/builds/)**

  * Used for video inspection, conversion, normalization, audio conversion, and chapter handling.
  * A simple installation guide can be found [here](https://github.com/Luluanaki/One-Pace-Blu-ray-Build-Guide/blob/main/References/FFmpeg/README.md).

* **[TMPGEnc Authoring Works 7](https://tmpgenc.pegasys-inc.com/en/download/taw7.html)**

  * Used for Blu-ray authoring, menu creation, chapter management, and disc structure generation.
  * The 30-day free trial was more than enough time for me to complete the entire project.

---

# Recommended Folder Structure

```text
├───DISC 01
│   ├───01 - Romance Dawn
│   ├───02 - Orange Town
│   ├───03 - Syrup Village
│   ├───04 - Gaimon
│   ├───05 - Baratie
│   ├───06 - Arlong Park
│   ├───07 - Side Stories
│   └───08 - Loguetown
├───DISC 02
│   ├───09 - Reverse Mountain
│   ├───10 - Whisky Peak
│   ├───11 - Little Garden
│   ├───12 - Drum Island
│   └───13 - Alabasta
├───DISC 03
│   ├───14 - Jaya
│   └───15 - Skypiea
├───DISC 04
│   ├───16 - Long Ring Long Land
│   └───17 - Water Seven
├───DISC 05
│   ├───18 - Enies Lobby
│   └───19 - Post Enies Lobby
├───DISC 06
│   ├───20 - Thriller Bark
│   └───21 - Sabaody Archipelago
├───DISC 07
│   ├───22 - Amazon Lily
│   ├───23 - Impel Down
│   ├───24 - Adventures of the Straw Hats
│   ├───25 - Marineford
│   └───26 - Post War
├───DISC 08
│   ├───27 - Return to Sabaody
│   └───28 - Fishman Island
├───DISC 09
│   ├───29 - Punk Hazard
│   └───30 - Dressrosa - Part 01
├───DISC 10
│   └───30 - Dressrosa - Part 02
├───DISC 11
│   ├───31 - Zou
│   └───32 - Whole Cake Island - Part 01
├───DISC 12
│   ├───32 - Whole Cake Island - Part 02
│   └───33 - Reverie
├───DISC 13
│   ├───34 - Wano Act 1
│   └───35 - Wano Act 2
├───DISC 14
│   ├───36 - Wano Act 3 - Part 01
│   └───36 - Wano Act 3 - Part 02
├───DISC 15
│   └───36 - Wano Act 3 - Part 03
└───DISC 16
    └───37 - Egghead
```

---
# Step 0: Download This Repository and One Pace

Before beginning, download both this repository and the One Pace episodes that will be used for authoring.

## Download This Repository

Download this repository by clicking **Code → Download ZIP** on the GitHub page.

The repository is approximately **0.92 GB** and contains:

* Disc authoring project files
* Disc label artwork
* Blu-ray case artwork
* Avery label templates

---

## Download One Pace

### Storage Requirements

Before downloading, make sure you have enough free storage available.

In my case, the complete One Pace collection occupied approximately **254.42 GB** immediately after downloading and before any processing, normalization, or authoring work was performed. Additional temporary space will be necessary as well.

### Download Speeds

Many files are hosted through PixelDrain. While not required, I chose to purchase **one month of PixelDrain Premium ($5 USD at the time of writing)** to speed up the download process significantly.

This is entirely optional, but it made downloading the full collection much more convenient.

### Subbed Collection

If you plan to create a subtitled version, episodes can be downloaded directly from the official One Pace website:

* [One Pace](https://onepace.net/en)

Whenever multiple versions are available, download the **highest quality version**.

### Dubbed Collection

If you plan to create a dubbed version similar to the one documented in this project, download all available dubbed episodes from One Pace and use Muhn Pace for the remaining content.

The following guide provides download links and recommended viewing order information:

* [One Pace Dub Watch Guide](https://www.reddit.com/r/onepace/comments/1rtpukk/one_pace_dub_watch_guide/)

As with the subtitled version, download the **highest quality version available** whenever possible.


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
