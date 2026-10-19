# Troubleshooting

Here are the most common issues and how to solve them.

### "Var VTOGn does NOT exist"
**Problem**: Inside MULTI-TOGGLE, you see a message saying the variable does not exist.
**Solution**: You need to create the variable manually on your radio. 
1. Go to your radio's **Model > Var** menu.
2. Create a new variable with the exact name shown in the widget (e.g., `VTOG1` or `VTOG1_MOTORE`).

### "The instrument is not visible on the screen"
**Problem**: You activated an instrument, but you don't see it.
**Solution**: 
1. Check the X/Y position. Make sure the coordinates are within your screen boundaries (e.g., X: 0-800, Y: 0-480).
2. Ensure the instrument is actually enabled (the switch is ON).

### "The widget is slow or lags"
**Problem**: The radio feels sluggish when moving between screens.
**Solution**: SpitFW releases bitmaps when a window is hidden to save RAM. However, having too many heavy instruments active on a single window can strain the system. Try to disable unused instruments.

### "The language doesn't change"
**Problem**: You selected English, but the widget is still in Italian.
**Solution**: The language is saved in a global file (`spitfw_global.ini`). Ensure your SD card is not write-protected and that the `/scripts/SpitFW/data/` folder exists.

### "The web simulator doesn't load"
**Problem**: The browser link gets stuck on the loading screen.
**Solution**: The ETHOS web simulator is a service managed by FrSky and can occasionally experience downtime. If it doesn't load on your PC, try from your smartphone. If the issue persists, use the desktop version of ETHOS Suite.
