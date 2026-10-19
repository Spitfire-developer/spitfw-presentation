# Multiple Instances (Windows)

One of the most powerful features of SpitFW is the ability to run **multiple instances** of the widget on the same model. 

## Why use Multiple Instances?
You might want one screen for engine management (MAGS, FLAP, AFG) and another screen for flight instruments (ASI, ALT, AH6A). 
Instead of cramming everything onto one screen, you create two separate windows.

## The Golden Rule: Unique Labels
Every time you add a SpitFW widget to your screen, you **must** give it a unique name in the configuration.
- Window 1: Label = `1` (or `Motore`)
- Window 2: Label = `2` (or `Volo`)
- Window 3: Label = `3` (or `Multi`)

If you use the same name for two windows, they will share the same settings and will overwrite each other's data! 

## Example Setup
Here is how a typical Spitfire pilot might set up their radio:

### Window 1: "Engine" (Label: `1`)
- **Instruments**: MAGS, TOUCH MAGS, FLAP, GEAR, AFG, RPM.
- **Purpose**: Monitor engine parameters and mechanical systems.

### Window 2: "Flight" (Label: `2`)
- **Instruments**: ASI, ALT, AH6A, VSI, GYRO.
- **Purpose**: Monitor flight dynamics.

### Window 3: "Custom" (Label: `Multi`)
- **Instruments**: MULTI-TOGGLE only.
- **Purpose**: Use the entire screen for virtual switches (e.g., for an electric model or glider).

[IMAGE: A diagram or screenshot showing the Widget selection menu with multiple SpitFW instances]

## How to switch between windows
Once configured, you can switch between windows using the normal ETHOS navigation (swiping between screens or assigning them to logical switches, just like any other widget).
