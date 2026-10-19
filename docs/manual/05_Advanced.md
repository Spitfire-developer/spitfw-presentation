# Advanced Features

SpitFW includes some powerful features that go beyond simple display.

## AFG: Telemetry and Multiple Batteries
If your model uses a telemetry sensor to calculate the remaining battery capacity (like the "Consumptie" sensor), you can use AFG in Telemetry mode.
- **Telemetry Source**: Select the sensor that provides the cumulative consumption.
- **Capacity & Reserve**: Enter the total capacity of your battery and the percentage at which you want the warning LED to trigger.
- **Multiple Batteries**: If you use different batteries (e.g., 4500mAh, 5000mAh, 5200mAh), you can configure a 3-position switch. AFG will automatically use the correct capacity and reserve threshold based on the switch position.
*For a full guide on AFG, read the [AFG Configuration Guide](../AFG-Configuration.md).*

## MULTI-TOGGLE: Global vs Local Variables
MULTI-TOGGLE can output its state to a variable (`VTOGn`). You can choose how this variable is shared across different windows:
- **Global**: The toggle uses the main variable (e.g., `VTOG1`). If you activate Toggle 1 in Window 1 and Window 2, they will mirror each other perfectly. Use this for things like Fuel Gauges or common switches.
- **Local (This window only)**: The toggle uses a specific variable for that window (e.g., `VTOG1_MOTORE`). This allows you to have two independent Toggle 1s in different windows. Use this for things like flaps on a glider (one window) and a custom switch (another window).

## Running in the Background
Some modules are designed to keep running even when their window is hidden:
- **TOUCH**: Continues to monitor the physical switches and update variables (VMAGS, VNAV, VFLAPS) so your mixers keep working.
- **AFG**: Continues to calculate fuel consumption in the background, ensuring you don't lose track of time.
- **ASI & STALL**: Keep processing speed data to ensure the stall warning is always ready.
- **MULTI-TOGGLE**: Continues to read the physical switches and update its variables.
