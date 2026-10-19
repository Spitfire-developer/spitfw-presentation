# Frequently Asked Questions (FAQ)

**Can I use SpitFW on models other than the Spitfire?**
Yes! While it was born as a Spitfire cockpit, the modular design allows you to use it on any model. You can use the MULTI-TOGGLE for an electric glider, or the AFG for a turbine jet. You can enable only the instruments you need.

**Do I need a radio with a touch screen?**
No. Most instruments can be fully controlled using physical switches. However, the touch screen enhances the experience, especially for the TOUCH and MULTI-TOGGLE modules.

**Can I create my own instruments or modify the code?**
The version distributed on GitHub is compiled into a single monolithic file (`main.luac`) to optimize performance and protect the architecture. 
While the project is built on a highly modular framework, the public release does not include the separate `.lua` module files. 
If you are a developer and you are interested in creating custom instruments, modifying the source code, or collaborating on the project, **please contact me directly** (via GitHub or the repository issues). I am happy to discuss providing access to the modular source code for specific development needs.

**Why are there so many files and folders?**
SpitFW uses a modular architecture to keep memory usage as low as possible. Each instrument is loaded lazily and its bitmaps are released when not visible, ensuring the radio's RAM is not overwhelmed.

**How do I update SpitFW to a new version?**
Simply overwrite the files in the `/scripts/SpitFW/` folder with the new release files. Your configurations inside the `data/` folder will be preserved, as long as the internal format of the files hasn't changed (always check the release notes).

**Can I customize the graphics (PNG files) of the instruments?**
Yes, you can! The visual graphics for the instruments (backgrounds and needles) can be replaced with your own custom designs (e.g., to change colors, or to use metric units). 

However, this is an advanced operation and requires **maximum attention** to three rules:
1. **Same Filenames**: Your custom images must have the exact same filename as the originals (e.g., `spit_mags_onoff.png`).
2. **Same Canvas Dimensions**: The new images must have exactly the same pixel width and height as the original ones.
3. **Pivot Points**: You must ensure that the rotation center (pivot) of the needle remains exactly in the same position as the original. If the pivot is off by even a few pixels, the needle will rotate incorrectly.

*Note: Some instruments (like MULTI-TOGGLE and STALL) are drawn entirely with vector graphics (code) and do not use PNG files. Customizing PNGs is not a trivial task, but it is definitely possible for those who want to create a truly unique cockpit.*
