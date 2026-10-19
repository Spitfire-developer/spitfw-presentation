# Instruments Overview

SpitFW includes over 17 different modules (15 instruments + 2 add-ons). Here is a detailed description of each.

## Engine Instruments

### GEAR (Landing Gear)
Displays the landing gear status. It shows a green indication when the gear is down, and a red indication when it is up. During the transition phase, the light blinks.
- **Configuration**: Requires a 2-position physical switch. It has an "Invert" option if the switch works in the opposite direction.
*[IMAGE: Screenshot of GEAR instrument]*

### NAV (Navigation Lights)
Displays the navigation lights status (OFF, MID, ON).
- **Configuration**: Requires a 3-position physical switch. It has an "Invert" option.
- **Touch Control**: By activating the TOUCH add-on, you can also command the navigation lights directly with your finger. Just like MAGS, you can configure safety hold times for each of the three touch zones.
*[IMAGE: Screenshot of NAV instrument]*

### FLAP
Displays the flap position (UP, MID, DOWN).
- **Configuration**: Requires a 3-position physical switch. It has an "Invert" option.
- **Touch Control**: By activating the TOUCH add-on, you can operate the flaps directly with your finger. You can set custom hold times for the touch zones to prevent accidental activation.
*[IMAGE: Screenshot of FLAP instrument]*

### MAGS (Magnetos)
Displays the state of the magnetos (OFF-OFF, ON-OFF, ON-ON).
- **Configuration**: Requires a 3-position physical switch. It has an "Invert commands" option.
- **Touch Control & Safety**: By activating the TOUCH add-on, you can command the magnetos directly with your finger, recreating the authentic cockpit experience. To prevent accidental engine shutdown from an unexpected screen touch, MAGS is designed with a **safety hold** feature. You must press and hold the screen until the yellow progress rectangle fills completely. Furthermore, if a physical switch (like your main ignition switch) is also configured, it acts as a master override, providing a second level of safety.
- **Customizable Timings**: All three switches (MAGS, NAV, FLAP) have 3 touch zones with configurable hold times. Setting the time to `0` makes the touch immediate, while a value like `30` (3.0 seconds) is highly recommended for safety, giving you time to abort an accidental touch.
*[IMAGE: Screenshot of MAGS instrument]*

### AFG (Analog Fuel Gauge)
Calculates and displays the remaining fuel.
- **Configuration**: It has two distinct modes:
  - **Estimate**: Calculates fuel based on throttle position, tank capacity, and consumption rates. Requires a throttle source.
  - **Telemetry**: Reads a cumulative telemetry sensor (e.g., mAh consumed) and uses a configured capacity and reserve percentage. Can also handle multiple battery capacities using a 3-position switch.
*[IMAGE: Screenshot of AFG instrument]*

### RPM (Tachometer)
Displays engine RPM. 
- **Configuration**: Select the RPM telemetry source. You can set a test value for calibration and adjust the scale.
*[IMAGE: Screenshot of RPM instrument]*

### TRIM
Displays the trim position. This is an exact reproduction of the Spitfire's trim indicator, which shows the nose position (up or down) based on the arrow's indication.
- **Configuration**: Select the trim source. You can set a test value and calibrate the full scale.
*[IMAGE: Screenshot of TRIM instrument]*

### VOLT (Voltmeter)
Displays the receiver battery voltage.
- **Configuration**: Select the voltage source (e.g., RxBt). You can set an alarm threshold (which triggers a red LED) and adjust the LED position.
*[IMAGE: Screenshot of VOLT instrument]*

## Flight Instruments

### ASI (Airspeed Indicator)
Displays airspeed. A yellow dot appears below 150 knots as a visual warning.
- **Configuration**: Select the speed sensor. You can set a test value for calibration.
*[IMAGE: Screenshot of ASI instrument]*

### ALT (Altimeter)
Displays altitude with three concentric needles (100, 1000, 10000).
- **Configuration**: Select the altitude source. You can choose the scale multiplier (x1, x10, x100) to match your sensor.
*[IMAGE: Screenshot of ALT instrument]*

### VSI (Vertical Speed Indicator)
Displays the climb or descent rate.
- **Configuration**: Select the variometer source.
*[IMAGE: Screenshot of VSI instrument]*

### AH6A (Artificial Horizon)
Displays roll and pitch.
- **Configuration**: Select the Roll and Pitch sources. You can enable a "Tap to reset" feature or use a physical switch to calibrate the horizon in flight.
*[IMAGE: Screenshot of AH6A instrument]*

### TS (Turn & Slip)
Shows the turn rate and slip (the vertical arrow in the middle).
- **Configuration**: Select the two telemetry sources (Slip and Turn). You can set test values.
*[IMAGE: Screenshot of TS instrument]*

### GYRO (Compass)
Displays the heading. It calculates the direction using GPS coordinates (trigonometry).
- **Configuration**: Select a GPS source. You can enable a static test mode and set a test heading.
*[IMAGE: Screenshot of GYRO instrument]*

### STALL
A red warning marker that overlays the ASI (Airspeed Indicator). It flashes and beeps when the speed approaches the stall threshold. 
- **Configuration**: Requires ASI to be active. You can set the stall speed, alarm duration, the offset for safety, and the position/size of the LED.
*[IMAGE: Screenshot of STALL overlay on ASI]*

## Add-ons & Extra Tools

### TOUCH (Touch Control)
Adds virtual touch zones to MAGS, NAV, and FLAP. This allows you to control these instruments by tapping the screen, in addition to using a physical switch.
- **Configuration**: You can assign a physical switch as the primary input. You can also set "Hold times" (e.g., hold for 1 second to trigger) for the high, center, and low zones. It supports 2 or 3 positions.
*[IMAGE: Screenshot of TOUCH configuration page]*

### MULTI-TOGGLE
A customizable panel with up to 8 virtual switches (toggles) drawn on the screen.
- **Configuration**: Each toggle can be 2 or 3 positions. You can assign a physical switch, set the name, and choose whether the output variable (`VTOGn`) is global or local to that specific window. It supports a fully automatic layout or custom X/Y positioning.
*[IMAGE: Screenshot of MULTI-TOGGLE panel with several toggles]*
