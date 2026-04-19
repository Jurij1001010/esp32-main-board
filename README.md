# Smart Compass (ESP32 Main Board)

Smart Compass is a GPS-enhanced compass that lets you save locations with one tap.  
Its analog dial then guides you back, always pointing directly toward your chosen destination—simple, intuitive navigation without maps.

<img alt="Smart Compass photo" src="https://github.com/user-attachments/assets/339ed4bb-7324-45f3-a3b5-d58144e8dfaf" />

## Project Overview

This repository contains firmware for an ESP32-based navigation device with:
- live GPS position tracking,
- compass heading sensing,
- a display-driven analog guidance dial,
- one-button destination save and return navigation behavior.

The project is configured as a **PlatformIO** project (Arduino framework).

## Features

- Save the current location as a destination using a hardware button
- Continuously compute heading and relative direction to the saved point
- Display directional guidance on an analog-style dial
- Serial output for GPS status, heading, distance, and diagnostics
- Basic stale-sensor recovery handling for compass reads

## Hardware Requirements

- ESP32 main board
- GPS module (UART/NMEA output)
- Compass/IMU module (I2C magnetometer support)
- Compatible TFT display
- Push button (for save-location action)

> Note: wiring and pin assignments are defined in source constants. Update them to match your hardware before flashing.

## Firmware Build Instructions

This repository includes `platformio.ini`, so the primary build flow is PlatformIO.

1. Install [PlatformIO Core](https://docs.platformio.org/en/latest/core/installation/index.html).
2. From the repository root, build:

```bash
platformio run
```

## Flashing Instructions

1. Connect your ESP32 board over USB.
2. Flash firmware:

```bash
platformio run --target upload
```

3. (Optional) Open serial monitor:

```bash
platformio device monitor
```

If your board/port differs from defaults, configure the environment in `platformio.ini` or pass upload options via CLI.

## Usage

1. Power on the device and wait for GPS data/fix.
2. Press the save button to store the current location.
3. Follow the on-screen analog direction indicator to navigate back toward the saved location.
4. Use serial output to verify GPS status, heading, and distance calculations while debugging.

## Configuration

Common configuration points are in source files under `src/`, including:
- main application behavior and timing constants
- GPS serial and pin configuration
- compass calibration/tuning constants

Adjust these values for your board revision and sensor orientation.

## Troubleshooting

- **No GPS fix**: confirm antenna visibility, module wiring, and UART settings.
- **Compass heading unstable or incorrect**: verify I2C wiring and adjust compass calibration constants.
- **Build/upload issues**: verify PlatformIO installation, selected environment, USB cable, and serial port permissions.
- **Display not updating as expected**: check display driver/library compatibility and wiring.

## Contributing

Contributions are welcome. Please open an issue or submit a pull request with a clear description of your change.

## License

Add your project license information here (for example, MIT, Apache-2.0, or GPL-3.0) and include a `LICENSE` file in the repository root.
