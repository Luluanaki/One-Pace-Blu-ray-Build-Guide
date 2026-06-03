# One Pace Blu-ray Build Guide
A reproducible physical media project for One Pace, featuring Blu-ray disc artwork, case covers, Avery templates, printing instructions, and archival workflow documentation. Designed to help collectors build their own set. No video files included.


> **Disclaimer:** This project is intended as a personal archival/workflow documentation project. It does not include or distribute copyrighted video files, fan edits, subtitles, or other copyrighted material.

<p align="center">
  <img src="References/Guide Images/CaseFront.jpg" width="33%">
  <img src="References/Guide Images/CaseBack.jpg" width="33%">
  <img src="References/Guide Images/CaseSpine.jpg" width="33%">
</p>
<p align="center">
  <img src="References/Guide Images/Discs.jpg" width="80%">
</p>

---

## Overview

This project documents the full process used to turn a large collection of One Pace video files into a polished physical Blu-ray collection that looks and feels as official as possible.



The general workflow is:

* Step 0: Download and gather source episodes
* Step 1: Name and organize files by arc

* Step 2–6: Skip entirely. After extensive testing, these steps turned out to be unnecessary

* Step 7: Author disc structure
* Step 8: Generate Blu-ray output
* Step 9: Burn to BD-R discs
* Step 10: Print disc labels
* Step 11: Apply disc labels
* Step 12: Print and assemble case artwork
* Step 13: Enjoy One Pace

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


---

# Software Requirements

## Core Tools

* **[TMPGEnc Authoring Works 7](https://tmpgenc.pegasys-inc.com/en/download/taw7.html)**

  * Used for Blu-ray authoring, menu creation, chapter management, and disc structure generation.
  * The 30-day free trial was more than enough time for me to complete the entire project.
    
* **[FFmpeg](https://www.gyan.dev/ffmpeg/builds/)** *(only necessary if there are compatibility issues)*

  * May be needed if TMPGEnc does not accept a particular video file or if you need to convert, inspect, or repair source files.
  * Can also be used for advanced workflows such as audio conversion, remuxing, normalization, and chapter handling.
  * A simple installation guide can be found [here](https://github.com/Luluanaki/One-Pace-Blu-ray-Build-Guide/blob/main/References/FFmpeg/README.md).


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

The repository is approximately **0.99 GB** and contains:

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

Expect the download process to take a while. I originally downloaded one arc at a time over the course of about a week before eventually deciding to support PixelDrain so I could download everything more efficiently.

While not required, I purchased **one month of PixelDrain Premium ($5 USD at the time of writing)**, which significantly increased download speeds and allowed me to download the entire collection at once.

This is entirely optional, but it made downloading the full collection much more convenient.

### Subbed Collection

If you plan to create a subbed version, episodes can be downloaded directly from the official One Pace website:

* [One Pace](https://onepace.net/en)

Whenever multiple versions are available, download the **highest quality version**.

### Dubbed Collection

If you plan to create a dubbed version similar to the one documented in this project, download all available dubbed episodes from One Pace and use Muhn Pace for the remaining content.

The following guide provides download links and recommended viewing order information:

* [One Pace Dub Watch Guide](https://www.reddit.com/r/onepace/comments/1rtpukk/one_pace_dub_watch_guide/)

As with the subbed version, download the **highest quality version available** whenever possible.

### Optional: Dual Audio (Dubbed + Subbed)

Including both English dubbed and Japanese audio tracks is theoretically possible, but requires additional processing to combine the streams before authoring.

After testing the available One Pace releases, I found that the subbed versions use **burned-in subtitles** rather than separate subtitle tracks. As a result, creating a Blu-ray with both audio tracks and optional subtitles is not as straightforward as it may seem.

While dual audio may be possible with additional work, I do not currently recommend it unless separate subtitle files (such as `.ass`, `.ssa`, or `.srt`) can be obtained. My project was authored using English dubbed audio only.



# Step 1: Organize the Source Files

Start by placing each arc into its own folder and giving the files a consistent naming format.

> **Note:** If you are creating a original Japanese audio, English subbed collection and downloading everything from a single source (such as One Pace), you can generally skip the renaming step. The filenames may be messy, but they are usually already sorted correctly. Simply organizing the episodes into arc-specific folders is often sufficient.


Example:

```text
01 - Romance Dawn 01.mkv
01 - Romance Dawn 02.mkv
02 - Orange Town 01.mkv
02 - Orange Town 02.mkv
```

This is primarily for organization and makes it easier to sort files alphabetically throughout the authoring process. It is especially useful when combining content from multiple sources, such as One Pace, Muhn Pace, and other fan edits, which all use different naming conventions.

By default, TMPGEnc will label episodes as **Chapter 1**, **Chapter 2**, **Chapter 3**, etc. The source filenames are not shown in the Blu-ray menus unless you manually customize the menu titles during authoring.

[Here](https://github.com/Luluanaki/One-Pace-Blu-ray-Build-Guide/tree/82cb970d23b4d620714037a5c6df4f174cfb2e79/References/Scripts/Renaming) are a few optional PowerShell scripts that can automatically rename entire arcs into a consistent format. They are especially useful when organizing files from multiple sources with different naming conventions.

---

# A Note About Steps 2–6

Originally, this guide contained several additional steps covering:

* Step 2: File inspection with FFprobe
* Step 3: Resolution and framerate normalization
* Step 4: Audio conversion to AC3
* Step 5: MKV remuxing
* Step 6: Arc stitching and chapter marker generation

I spent a considerable amount of time developing and testing workflows for all of the above. My assumption was that Blu-ray authoring software would require highly standardized source files in order to produce reliable results. This was largely based on my experience with free tools such as MultiAVCHD, which frequently struggled with mixed source files and is no longer actively supported.

After completing the entire project and performing additional testing, I discovered that most of this work was unnecessary.

TMPGEnc Authoring Works handled mixed resolutions, framerates, aspect ratios, codecs, and individual episode files far better than I initially expected. In many cases, the software simply took care of these differences automatically.

As a result, the vast majority of users can safely skip what would have been Steps 2–6 and proceed directly to Step 7.

The scripts, tools, and references related to those steps have been left in this repository for anyone interested in the more advanced workflow, but they should be considered optional rather than required. Unless you encounter a specific issue during authoring, I recommend keeping things simple and letting TMPGEnc do the heavy lifting.

---

# Step 7: Author Disc Structure

<p align="center">
  <img src="Project Files/Disc Authoring/Disc15/Menu Screenshots/00_0.jpg" width="75%">
</p>

<p align="center">
  <img src="Project Files/Disc Authoring/Disc15/Menu Screenshots/00_1.jpg" width="75%">
</p>

<p align="center">
  <img src="Project Files/Disc Authoring/Disc15/Menu Screenshots/01_1.jpg" width="75%">
</p>


This is the satisfying, fun part. You'll be happy to know that most of the hard work has already been done. This repository includes pre-built TMPGEnc Authoring Works 7 projects for all 16 discs, complete with menu layouts, navigation, artwork and music.

Your primary tasks will be:

* Importing the episode files
* Adjusting bitrate to fit the disc
* Updating chapter thumbnails
* Optionally renaming chapters
* Generating the final Blu-ray output

For those who want to create their own menu designs, the included projects should still serve as useful templates.


## Understanding Bitrate

> **Note:** If you're familiar with Blu-ray authoring, seeing a target bitrate of **4 Mbps** may seem absurdly low.
>
> Commercial Blu-rays often use bitrates in the **20–40 Mbps** range, and even many home video encodes target **10 Mbps** or higher.
>
> Fortunately, anime compresses extremely well due to its large areas of flat color, clean line art, relatively low visual complexity, and frequent static scenes. A bitrate that would look terrible on a live-action film can still look surprisingly good on anime.
>
> Another important consideration is the source material itself. Most One Pace releases ultimately originate from web streams, meaning the video has already been compressed before it ever reaches your hard drive.
>
> Authoring a Blu-ray at **30 Mbps** does not magically restore detail that was lost in the source. The final quality can only ever be as good as the source material.
>
> For this project, I found that approximately **4 Mbps** provided a good balance between visual quality and storage efficiency, allowing a surprising amount of content to fit on a single 50 GB disc.
>
> In fact, I ran comparison tests on a one-minute clip from a visually complex episode, encoding it at **16 Mbps**, **8 Mbps**, **4 Mbps**, and **2 Mbps**. Even at **2 Mbps**, I couldn't for the life of me spot any meaningful difference between it and the original One Pace source during normal viewing.
>
> After that I became far less concerned with bitrate than I was at the start of this project.




## Import the Video Files

1. Install **[TMPGEnc Authoring Works 7](https://tmpgenc.pegasys-inc.com/en/download/taw7.html)**.

   * The free trial is sufficient for this project.

2. Open the appropriate project file:

```text
├───Project Files
│   ├───Disc Authoring
│   │   ├───Disc01
│   │   │   ├───Disc01
│   │   │   │   ├───Disc01.taw7
```

> **Note:** Do not delete, move, or rename any of the files or folders included with the project archive, even if they appear unimportant. The `.taw7` project references these files directly, including menu artwork, button graphics, menu music, and other assets. Removing them will cause the project to fail to load or prevent it from being archived correctly.

    
3. Click the **SOURCE** tab.

4. On the left side, you'll see tracks that have already been created for each arc.

 

5. Select the desired track and drag all episodes from that arc into the track.
    * Be sure to delete the placeholder video files from each track during this step

      
6. When prompted, select:

* **Add without Opening Clip Edit Window**
* **Add to Current Track**
* Enable:

```text
Run this selection automatically in the future
```

7. Repeat for all remaining arcs on the disc.

<p align="center">
  <img src="References/Guide Images/TMPGEncSource.png" width="80%">
</p>


---

## Verify Chapter Structure

Each imported episode should appear as a separate chapter entry.

For most releases, each episode should show:

```text
Chapters: 1
```

Check all imported episodes before proceeding.

### If an Episode Contains Multiple Chapters

Some fan edits include embedded chapter markers after the opener. While helpful for normal viewing, they create additional chapter entries that interfere with the clean one-chapter-per-episode structure used by the Blu-ray menus.
 
To remove them:

1. Double-click the episode to Open the **Clip Editing** window.
2. Locate the chapter list on the left.
3. Keep only the chapter at:

```text
00:00:00.00
```
4. Delete all remaining chapters by right clicking and **Delete**.

The goal is to maintain one chapter entry per episode for cleaner chapter selection menus.

<p align="center">
  <img src="References/Guide Images/DeleteChapter.png" width="80%">
</p>
---

## Adjust Bitrate

1. Look at the **Estimated Size** bar near the bottom of the window.

2. Right-click the bar and select the appropriate disc size:

```text
Blu-ray Media 50GB (4)
```

or whichever disc size you intend to use.

3. Go to the **OUTPUT** tab at the top.

4. Ensure:

```text
Target Size: None
```

This prevents TMPGEnc from automatically adjusting the bitrate while you're making manual decisions and allows the estimated size to accurately reflect your current settings.


5. Return to the **SOURCE** tab at the top.

6. For each track:

```text
Settings → Video
```

7. Set:

```text
Bitrate: 4 Mbps
```

for every track.

<p align="center">
  <img src="References/Guide Images/AdjustBitrate.png" width="50%">
</p>

### Fine-Tuning

If the estimated size is significantly below the disc capacity, increase bitrate in small increments:

```text
4.0 Mbps
4.5 Mbps
5.0 Mbps
```

until the project is utilizing most of the available space.

Try to stick to one consistent Bitrate for the entire disc.

I generally try not to go below **4 Mbps**.

> **Note:** TMPGEnc may automatically adjust the bitrate when a **Target Size** is specified, but I am not entirely sure what calculations it performs behind the scenes. For that reason, I prefer to temporarily set **Target Size** to **None** while dialing in my bitrate settings. This allows me to see the estimated disc size without any automatic adjustments being applied.
>
> We will still set the target size to match the disc capacity during the final output stage.

---

## Update Chapter Thumbnails

1. Open the **MENU** tab.

2. Navigate to a chapter menu page.

3. Double-click a chapter thumbnail.

**Important:** Avoid accidentally dragging the thumbnail object itself. If something moves unexpectedly, press:

```text
Ctrl + Z
```

3. In the thumbnail editor:

* Scrub through the timeline
* Find an interesting frame
* Click **Set Thumbnail Position**

4. Click **OK**

Repeat for all chapters.

A good thumbnail makes it much easier to identify episodes at a glance.

> **Note:** Each disc folder includes a **Menu Screenshots** folder showing every menu page from my completed project. If you're unsure what a page is supposed to look like, use these screenshots as a reference to compare your thumbnails, chapter titles, and overall menu layout.

 <p align="center">
  <img src="References/Guide Images/Thumbnails.png" width="80%">
</p>


### Aspect Ratio Note

For some early One Piece episodes with a 4:3 image, the thumbnail boxes have been scaled to **134%** so they fill the available menu space.

This affects only the menu thumbnails and does **not** alter video playback.

Later 16:9 episodes typically use **100%**.

---

## Rename Chapter Titles (Optional)

By default, TMPGEnc names episodes:

```text
Chapter 1
Chapter 2
Chapter 3
```

You may prefer more descriptive names.

For example:

```text
01 - The Dawn of Adventure
02 - They Call Him Straw Hat Luffy
```
One Pace conveniently stores the episode titles in the video metadata, making it easy to reference the official episode names if you choose to customize them.

 <p align="center">
  <img src="References/Guide Images/ClipTitle.png" width="50%">
</p>

To change a title:

1. Double-click the chapter name.
2. Edit the text.
3. Adjust font size or enable **Stretch to Fit** if necessary.

---

## Test the Menu

Before generating output:

1. Open the **SIMULATION** tab.
2. Click **START**.

This allows you to test:

* Menu navigation
* Chapter selection
* Playback behavior
* Remote control actions

The preview quality is lower than the final disc and should not be used to judge video quality.

 <p align="center">
  <img src="References/Guide Images/MenuTest.png" width="80%">
</p>

### Hear the Menu Music
The simulation mode is also a great opportunity to test the menu music and hear how it loops.

 All of the discs use instrumental versions of the corresponding opening themes for their respective sagas. If you would like to change the music, go to the **MENU** tab and double-click the background on any menu page. This will open **Menu Item Edit**. From there, navigate to the **BGM Audio Selection** tab.

 Here you can adjust:

 * Source File
 * Volume
 * Fade-in and fade-out
 * Playback start position
 * Which section of the song is used
 * Loop Behavior

 In general, I configured the title menu to begin at the start of the song, while the remaining menus begin near the start of the chorus. Most of my menu loops are set to **60 seconds** long before repeating.

 To change the menu duration, click **Blu-ray Global Menu Settings** in the upper-left corner, then open the **Motion Menu** tab and adjust:

 ```text
 BGM/Motion Menu Duration
 ```

 Keep in mind that longer motion menus consume additional disc space, although the impact is usually fairly small.

---

## Disc Information (Optional)

To customize the title and thumbnail displayed by your Blu-ray player:

1. Open the **SOURCE** tab.
2. Click **Disc Settings** in the upper-left corner.

You can modify:

* Disc title
* Thumbnail image
* Disc metadata

The **Language** field refers to the disc's metadata and menu language, not the audio language.

 <p align="center">
  <img src="References/Guide Images/DiscTitle.png" width="40%">
</p>

---

## Make It Your Own

The included projects reflect the choices I made for my own collection, but they are by no means the only way to author these discs.

Feel free to customize the menus, artwork, music, fonts, navigation, chapter layouts, or anything else to suit your own preferences. Whether you make a few small adjustments or completely redesign everything from scratch, the goal is to create a collection that you're happy with.

---

# Step 8: Output Authored Folder

> **Note:** This step will take a long time—typically **5–10 hours per disc** in my experience—and that does not include the time required to burn the finished Blu-ray.
>
> TMPGEnc is not simply copying your video files onto the disc. It is decoding every episode, re-encoding the video to Blu-ray-compliant settings, generating menu assets, creating chapter structures, multiplexing audio and video streams, and finally building a Blu-ray-compliant folder structure.
>
> During this process, your CPU will likely be under heavy load for hours. The exact time depends on your processor, storage speed, number of episodes, bitrate settings, and whether hardware acceleration is available.
>
> Fortunately, this step requires very little user interaction. Once everything is configured correctly, it is a good time to walk away, go to work, sleep, or watch some One Piece.

## Configure Output Settings

1. Click the **OUTPUT** tab at the top of TMPGEnc.

2. Under **Output Folder Name**, click **Browse...**

3. Navigate to the output folder for the disc you are authoring:

```text
Disc Authoring
└── Disc01
    └── Output
```

4. Click **Select Folder**.

> **Note:** I have already included an **Output** folder for each disc project. This is where TMPGEnc will generate the **BDMV** and **CERTIFICATE** folders needed for burning the final Blu-ray.

5. Set:

```text
Target Size: Blu-ray Media (50GB) Size
```

6. Leave the following option unchecked:

```text
Burn to DVD/Blu-ray Disc
```

We'll handle the burning process separately in the next step.

7. Set **Post-Output Process** to whatever behavior you prefer.

8. Make sure your computer will not go to sleep during the output or burn process.

   * In the Windows search bar, type **Sleep** and open **Power, sleep, and battery settings**.
   * Under **Screen, sleep, & hibernate timeouts**, set **Sleep** and **Hibernate** to **Never**.

9. Double- and triple-check your settings. Once the output process begins, you'll likely be waiting several hours before discovering any mistakes.

 <p align="center">
  <img src="References/Guide Images/01_Output.png" width="60%">
</p>

10. Click **Start Output** in the bottom left and let TMPGEnc do its thing.

---
# Step 9: Burn the Disc

## Open the Disc Writing Tool

Once output is complete, TMPGEnc will prompt you to open the Disc Writing Tool. Open it.

If you missed the prompt, you can access it manually:

* **START** tab in the top left
* Under **Tools** click **Disc Writing Tool**

## Configure Burn Settings

Before starting the burn:

1. Insert the correct blank Blu-ray disc into your writer.
2. I recommend using a Sharpie to temporarily identify the disc so you don't accidentally mix it up later.
3. Under **Content Folder**, click **Browse** and select the disc's **Output** folder containing the generated **BDMV** and **CERTIFICATE** folders.
4. Verify that the correct Blu-ray drive is selected.
5. Set **Writing Speed** to **2x**.

> **Note:** I strongly recommend avoiding the maximum writing speed. Even at 2x, the burn process typically takes only 1–2 hours. For archival projects like this, I prefer to prioritize reliability and longevity over saving a few minutes.

6. Set the **Disc Label** to match the disc you are authoring. For example:

 ```text
 One Pace 01 - East Blue
 ```

This is the name that will appear on your Blu-ray player's interface when the disc is inserted.

> **Note:** One of my finished discs has the wrong disc number in the label metadata. It's not worth wasting another BD-R to fix, but it does annoy me every time I see it. To be avoided.

* Double- and triple-check all settings before proceeding.
  
 <p align="center">
  <img src="References/Guide Images/02_DiscWriting.png" width="50%">
</p>

* Click **Write to Disc** in the upper-left corner and again let TMPGEnc do its thing.

> **Warning:** Unless you are using a rewritable disc (BD-RE), the burn process is a one-time operation. Once the burn process begins, there are no second chances. If the burn fails, is interrupted, the computer goes to sleep, or the power goes out, the disc is usually destined for the coaster pile.



## Test the Finished Disc

Before applying a label, test the disc in your Blu-ray player (PS5 for me).

Verify:

* Menu navigation
* Chapter selection
* Audio playback
* Video playback

Watch at least a few minutes from several different parts of the disc to make sure everything behaves as expected.

If you encounter visual corruption or playback issues, the cause is usually a bad burn, poor-quality media, or hardware issues rather than the authoring software itself.

> **Important:** Do not apply the disc label until you have confirmed the burn was successful.

## Repeat

Once you are satisfied with the disc, repeat **Steps 7–9** for the remaining discs.

> **Note:** I completed these steps over the course of a couple weeks, usually authoring and burning **1–2 discs per day**.

---

# Step 10: Print Disc Labels

<p align="center">
  <img src="References/Guide Images/Discs.jpg" width="80%">
</p>

The digital work is finally done—it's time to make the project look pretty.

At this point, you will need [**Avery Full-Face Disc Labels**](https://a.co/d/02zhhNVN) and access to a decent printer.

## Review the Included Disc Label Artwork

I've already created disc label artwork that I was happy with. Before making any changes, take a look at the included PDFs:

```text
├───Project Files
│   ├───Disc Labels
│   │   ├───PDF
```

If you're happy with the design, you can proceed directly to the **Test Print** section.

> **Warning:** The included label designs contain episode and chapter ranges based on my own build. Depending on how you organize your discs, these numbers may not match your project, particularly for sagas that span multiple discs.
>
> There is also a very good chance that some of my numbering is incorrect—I'm fairly certain Disc 14 and Disc 15 contain mistakes. Fortunately, these labels are easy to update using the included **.avery** project files.


If you'd like to make changes, I've also included the original Avery project files and source assets used to create the labels.

> **Note:** Some assets are stored in the individual source asset folders, while others are located in the shared assets folder under **Project Files**.

## Editing the Avery Projects

To open one of the included `.avery` project files:

1. Go to the Avery Projects website.
2. Create an account if necessary.
3. Click your profile icon in the upper-right corner and select **Projects**.
4. Click **Upload Project**.
5. Select **Browse to Open a File** and locate the desired `.avery` project file.
6. Make whatever changes you'd like.

## A Note About Avery

The Avery web app is excellent for positioning artwork and generating print-ready label sheets, but it has fairly limited design capabilities.

For that reason, I often created or modified artwork in external software such as **GIMP**, **Paint.NET**, or other image editors, then imported the resulting PNG files into Avery for final layout and printing.

If you plan to make significant design changes, you'll likely find a similar workflow much easier than trying to do everything directly inside Avery.


## Test Print

I strongly recommend performing a test print before using one of your Avery label sheets. If you're creating the full 16-disc collection, there are only a couple of spare labels available, so mistakes can become expensive quickly.

To help with this, I have included an **Alignment Test.pdf** page in the repository.

Print the test page on a regular sheet of paper and hold it against an Avery label sheet with a light source behind it. This makes it easy to verify that the artwork is properly aligned before committing to the actual labels.

### Alignment Notes

In my case, the PDFs generated directly from the Avery website were slightly misaligned when printed:

* Approximately **4 mm too far right**
* Approximately **3 mm too far up**

Because of this, I have included adjusted versions of the PDFs with filenames ending in:

```text
*_adjusted.pdf
```

These worked better with my printer, but your results may vary.

> **Note:** The small watermarks in the upper corners of the PDFs will print, but they are outside the label area and will not affect the finished disc labels.

Once you are satisfied with the alignment, proceed with the final print.

## Final Print

Printing settings vary significantly between printers, drivers, operating systems, and paper types, so there is no universal set of settings that works for everyone.

The most important things are:

* Print at 100% scale
* Verify alignment first
* Use the correct paper type for your labels
* Print at the highest quality setting available

For my own build, I used Google Chrome's print dialog because it exposed more print options than some other applications.

### My Print Settings (Reference Only)

These settings worked well for my printer and Avery labels:

* Load the label sheet according to your printer's paper orientation.
* Borderless Printing: **Off**
* Print on Both Sides: **None**
* Pages per Sheet: **1**
* Print Quality: **Best**
* Paper Size: **Letter**
* Print in Max DPI: **Enabled**

Your exact settings may differ depending on your printer model and paper type.



---

# Step 11: Apply Disc Labels

Disc labels need to be applied as close to perfectly centered as possible.

If a label is significantly off-center, it can theoretically introduce balance issues while the disc is spinning, potentially affecting playback or increasing wear on the drive.

You have several options:

* Purchase the official Avery Label Applicator.
> **Note:** Good luck. Avery doesn't appear to sell the full-face label applicator anymore, and I was unable to find one anywhere during this project.

* 3D print an applicator tool. I created a model designed to replicate the Avery tool:
  * [DIY Disc Label Alignment Tool](https://www.printables.com/model/1735505-diy-disc-label-alignment-tool)
* Create your own jig using the spindle that the blank discs were shipped in.
* Eyeball it and hope for the best.

Regardless of the method you choose, take your time.

> **Warning:** Once the adhesive makes contact with the disc, there is very little opportunity for adjustment. Attempting to reposition the label usually damages it.

When applying the label:

* Apply even pressure across the entire surface.
* Work outward from the center.
* Remove any air bubbles.
* Ensure the label is fully adhered around the outer edge.

A smooth, bubble-free application is just as important as proper alignment.

Once the label has been applied, allow it to settle for a short period before placing the disc into a drive.


---

# Step 12: Blu-ray Case Covers

<p align="center">
  <img src="References/Guide Images/CaseFront.jpg" width="33%">
  <img src="References/Guide Images/CaseBack.jpg" width="33%">
  <img src="References/Guide Images/CaseSpine.jpg" width="33%">
</p>

It's time to finish the project with some cover art.

## Included Cover Artwork

I've included PDF versions of the cover art I used for my own collection:

```text
├───Project Files
│   ├───Case Covers
│   │   ├───PDF
```

If you're happy with the design, simply print the PDFs and skip ahead to the printing section.

## Customizing the Covers

If you'd like to make changes—or if you're using individual Blu-ray cases instead of an 8-disc case—I have also included the original project files and source assets:

```text
├───Project Files
│   ├───Case Covers
│   │   ├───Canva Files
│   │   ├───Paintdotnet
│   │   └───Source Assets
```

The Canva template used for the covers can be found [**here**](https://canva.link/kysxnthcchak6o9)

> **Note:** If you are using individual Blu-ray cases, you will likely need to adjust the spine width to match your case dimensions.
>
> ```text
> [Back Cover] [Spine] [Front Cover]
> ```

## My Case Layout

For reference, I split the collection into two 8-disc cases:

```text
Case 1:
The Grand Line Era
East Blue to Fishman Island
Discs 1–8

Case 2:
The New World Era
Punk Hazard to Egghead
Discs 9–16
```

## Printing

Glossy paper around **120 GSM** is a good target. It is thin enough to fit inside a Blu-ray sleeve while looking noticeably nicer than standard printer paper.

If you only need one or two covers, it may be easier to use a local print shop such as Office Depot, Staples, or FedEx Office rather than purchasing an entire pack of specialty paper.

> **Note:** The 8-disc case covers are slightly too large to fit comfortably on standard Letter paper without borderless printing. My printer only allows borderless printing when using photo paper, which is what I ended up using.

## Trimming and Fitting

Before printing the final version, perform a few test prints and make any necessary adjustments.

Once you're happy with the alignment:

* Trim the cover carefully.
* Use a straight edge and hobby knife, razor blade, or paper cutter for the cleanest results.
* Insert the finished cover into the Blu-ray sleeve and verify the fit before making additional copies.

## Finished!

Congratulations! You now have a very official-looking physical collection of One Pace.


---

# Step 13: Enjoy!

Congratulations! You have successfully spent an unreasonable amount of time creating a custom Blu-ray collection for a fan edit of a 1000+ episode anime.

There is now only one remaining step:

**Watch One Pace.**

Good luck. Share your project on r/OnePace so I can see it!

---


This README serves as a reference guide for the full process and as documentation for anyone attempting a similar personal archival project.
