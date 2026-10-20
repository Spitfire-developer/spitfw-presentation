# Installation Guide

## Requirements
- A FrSky radio running **ETHOS** (tested on 26.1.2 or newer).
- A microSD card.
- The SpitFW release files (downloaded from GitHub Releases).

## Step 1: Copy Files to the SD Card
1. Insert your SD card into your PC.
2. Locate the `/scripts/` folder on your SD card.
3. Extract the SpitFW zip file. You will see a folder named `SpitFW`.
4. Copy the entire `SpitFW` folder into `/scripts/`. 

Your folder structure should look exactly like this:

```text
/scripts/SpitFW/
  ├── data/       (where your settings are saved)
  ├── gfx/        (menu icons)
  ├── PNG/        (instrument images)
  └── main.luac   (the compiled main widget file)
```

## Step 2: Add the Widget to your Radio
1. Safely eject the SD card from your PC and insert it into your radio.
2. Turn on the radio.
3. Go to **Model > Display** (or the screen where you want the widget).
4. Select a widget slot and choose **SpitFW** from the list.
5. The widget will start with a default empty layout.

## Step 3: First Configuration
1. Tap the widget to open the configuration menu.
2. At the top of the screen, you will see **"Window: name required"**.
3. Give this window a unique name (e.g., `1`, `motore`, `volo`). 
4. Press the **Back** arrow.

*[IMAGE: Screenshot of the ROOT configuration page, showing the Window name field at the top]*
