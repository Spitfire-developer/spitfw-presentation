# Installation Guide

## Requirements
- A FrSky radio running **ETHOS** (tested on 26.1.2 or newer).
- A microSD card.
- The SpitFW release files (downloaded from GitHub Releases).

## Step 1: Copy Files to the SD Card
1. Insert your SD card into your PC.
2. Locate the `/scripts/` folder on your SD card.
3. Extract the SpitFW zip file. You should see a folder named `SpitFW`.
4. Copy the entire `SpitFW` folder into `/scripts/`. 

Your folder structure should look exactly like this:
```text
/scripts/SpitFW/
  ├── data/       (where your settings are saved)
  ├── gfx/        (menu icons)
  ├── lib/        (shared libraries)
  ├── modules/    (the instruments)
  ├── PNG/        (instrument images)
  └── main.lua    (the main widget file)

(If you are using the compiled .luac version, you will have main.luac instead of main.lua).
