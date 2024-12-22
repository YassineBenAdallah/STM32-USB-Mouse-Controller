# 🔥 STM32 Accelerometer-Based Mouse HID 🔥

## Overview
This project implements a Human Interface Device (HID) using an STM32F4 microcontroller. The onboard accelerometer is used to simulate mouse movements, and a GPIO button serves as a mouse click input.

## Features
- Simulates mouse movements based on accelerometer readings.
- Provides left-click functionality through a GPIO button.
- Includes calibration for the accelerometer to ensure accurate mouse behavior.
- USB communication using the HID protocol.

## Hardware Requirements
- STM32F4 Discovery Board
- Onboard MEMS Accelerometer
- USB connection to the PC
- Push-button (connected to GPIO PA0)
- LED (optional, connected to GPIOD Pin 13)

## Software Requirements
- STM32CubeMX
- STM32 HAL Library
- USB Device Middleware (HID)

## Code Description
The main program initializes the accelerometer, GPIOs, SPI, and USB. Calibration is performed to define the range of accelerometer values. During the main loop, the program:
1. Reads accelerometer data.
2. Calculates mouse movements based on the calibrated values.
3. Sends mouse movement data over USB to the PC.
4. Handles button press events for left-click functionality.

## Calibration
The `ACCELRO_Calibrate` function collects accelerometer readings over 5 seconds to determine the minimum and maximum values for both X and Y axes. These values are used to normalize accelerometer input for mouse movement.

## Mouse HID Structure
The `mouseHID` structure contains the following fields:
- `button`: Mouse button state (0: no click, 1: left-click).
- `mouse_x`: X-axis movement.
- `mouse_y`: Y-axis movement.
- `wheel`: Scroll wheel (not used in this project).

## Interrupts
GPIO interrupt is configured for the button on `PA0`. When pressed, the callback function sets a flag to simulate a mouse click.

## USB Communication
The USB HID reports are sent using the `USBD_HID_SendReport` function. Each report contains the button state and mouse movement data.

## References
- STM32F4 HAL Documentation
- USB HID Specification
- STM32CubeMX Configuration Guide

## License
This project is licensed under the terms found in the LICENSE file provided with the software. If no LICENSE file is included, the project is provided AS-IS.
