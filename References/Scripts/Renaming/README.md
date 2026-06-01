# PowerShell Renaming Scripts

These scripts are optional, but useful if you want to quickly rename entire arcs into a consistent format before importing them into TMPGEnc.

Recommended naming format:

```text
01 - Romance Dawn 01.mp4
01 - Romance Dawn 02.mp4
02 - Orange Town 01.mp4
02 - Orange Town 02.mp4
```

---

## Rename One Pace Files

This script is designed for standard One Pace filenames such as:

```text
[One Pace][1] Romance Dawn 01 [1080p][En Dub][44DFDE68].mp4
[One Pace][3-5] Romance Dawn 03 [1080p][En Dub][D326C4B7].mp4
```

```powershell
# Rename-OnePaceArc.ps1
# Run this script inside the folder containing the arc files.

# Change these values for the arc you are renaming.
$ArcNumber = "01"
$ArcName = "Romance Dawn"

# Preview changes first. Set to $false when ready to actually rename.
$PreviewOnly = $true

Get-ChildItem -File | Where-Object {
    $_.Extension -match "\.(mp4|mkv)$"
} | ForEach-Object {

    # Matches filenames like:
    # [One Pace][1] Romance Dawn 01 [1080p][En Dub][HASH].mp4
    # [One Pace][3-5] Romance Dawn 03 [1080p][En Dub][HASH].mp4
    if ($_.BaseName -match "\[One Pace\]\[[^\]]+\].*?(\d{2})\s*\[") {

        $EpisodeNumber = $matches[1]
        $NewName = "$ArcNumber - $ArcName $EpisodeNumber$($_.Extension)"

        if ($PreviewOnly) {
            Write-Host "PREVIEW: $($_.Name) -> $NewName"
        }
        else {
            Rename-Item -LiteralPath $_.FullName -NewName $NewName
        }
    }
    else {
        Write-Host "SKIPPED: $($_.Name)"
    }
}
```

When the preview looks correct, change:

```powershell
$PreviewOnly = $true
```

to:

```powershell
$PreviewOnly = $false
```

and run the script again.

---

## Rename Muhn Pace / Other Fan Edit Files

Muhn Pace and other fan edits may use different naming formats, so this script is more manual. It simply renames files in alphabetical order.

Use this when the files are already sorted in the correct episode order.

```powershell
# Rename-ArcByOrder.ps1
# Run this script inside the folder containing the arc files.

# Change these values for the arc you are renaming.
$ArcNumber = "01"
$ArcName = "Romance Dawn"

# Starting episode number.
$StartNumber = 1

# Preview changes first. Set to $false when ready to actually rename.
$PreviewOnly = $true

$Files = Get-ChildItem -File | Where-Object {
    $_.Extension -match "\.(mp4|mkv)$"
} | Sort-Object Name

$Counter = $StartNumber

foreach ($File in $Files) {
    $EpisodeNumber = "{0:D2}" -f $Counter
    $NewName = "$ArcNumber - $ArcName $EpisodeNumber$($File.Extension)"

    if ($PreviewOnly) {
        Write-Host "PREVIEW: $($File.Name) -> $NewName"
    }
    else {
        Rename-Item -LiteralPath $File.FullName -NewName $NewName
    }

    $Counter++
}
```

This script is useful when filenames are inconsistent but the files are already in the correct order.
