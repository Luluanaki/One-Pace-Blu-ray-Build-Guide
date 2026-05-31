# Installing FFmpeg on Windows

FFmpeg is used throughout this guide for inspecting, converting, and processing video files. 

## 1. Download FFmpeg

Download the latest Windows build from:

https://www.gyan.dev/ffmpeg/builds/

I recommend downloading the **Essentials Build** ZIP file.

## 2. Extract FFmpeg

Extract the ZIP file to a permanent location such as:

```text
C:\FFmpeg
```

After extraction, the folder structure should look similar to:

```text
C:\FFmpeg
└── bin
    ├── ffmpeg.exe
    ├── ffprobe.exe
    └── ffplay.exe
```

## 3. Add FFmpeg to Your System PATH

1. Press **Windows Key**
2. Search for **Environment Variables**
3. Open **Edit the system environment variables**
4. Click **Environment Variables**
5. Under **System Variables**, select **Path**
6. Click **Edit**
7. Click **New**
8. Add:

```text
C:\FFmpeg\bin
```

9. Click **OK** on all windows to save.

## 4. Verify Installation

Open a new PowerShell window and run:

```powershell
ffmpeg -version
```

You should see version information printed to the console.

You can also verify FFprobe:

```powershell
ffprobe -version
```

If both commands work, FFmpeg has been installed successfully.

## Troubleshooting

If PowerShell reports:

```text
ffmpeg : The term 'ffmpeg' is not recognized...
```

then:

1. Verify that `ffmpeg.exe` exists inside your `bin` folder.
2. Verify that the correct `bin` folder was added to PATH.
3. Close and reopen PowerShell after making PATH changes.
4. Restart Windows if the issue persists.
