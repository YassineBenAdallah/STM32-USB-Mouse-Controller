<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🔥 STM32 Accelerometer-Based Mouse HID 🔥</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 20px;
        }
        h1, h2 {
            color: #333;
        }
        code {
            background-color: #f4f4f4;
            padding: 2px 4px;
            border-radius: 4px;
        }
    </style>
</head>
<body>
    <h1>🔥 STM32 Accelerometer-Based Mouse HID 🔥</h1>
    <h2>Overview</h2>
    <p>This project implements a Human Interface Device (HID) using an STM32F4 microcontroller. The onboard accelerometer is used to simulate mouse movements, and a GPIO button serves as a mouse click input.</p>

    <h2>Features</h2>
    <ul>
        <li>Simulates mouse movements based on accelerometer readings.</li>
        <li>Provides left-click functionality through a GPIO button.</li>
        <li>Includes calibration for the accelerometer to ensure accurate mouse behavior.</li>
        <li>USB communication using the HID protocol.</li>
    </ul>

    <h2>Hardware Requirements</h2>
    <ul>
        <li>STM32F4 Discovery Board</li>
        <li>Onboard MEMS Accelerometer</li>
        <li>USB connection to the PC</li>
        <li>Push-button (connected to GPIO PA0)</li>
        <li>LED (optional, connected to GPIOD Pin 13)</li>
    </ul>

    <h2>Software Requirements</h2>
    <ul>
        <li>STM32CubeMX</li>
        <li>STM32 HAL Library</li>
        <li>USB Device Middleware (HID)</li>
    </ul>

    <h2>Code Description</h2>
    <p>The main program initializes the accelerometer, GPIOs, SPI, and USB. Calibration is performed to define the range of accelerometer values. During the main loop, the program:</p>
    <ol>
        <li>Reads accelerometer data.</li>
        <li>Calculates mouse movements based on the calibrated values.</li>
        <li>Sends mouse movement data over USB to the PC.</li>
        <li>Handles button press events for left-click functionality.</li>
    </ol>

    <h2>Calibration</h2>
    <p>The <code>ACCELRO_Calibrate</code> function collects accelerometer readings over 5 seconds to determine the minimum and maximum values for both X and Y axes. These values are used to normalize accelerometer input for mouse movement.</p>

    <h2>Mouse HID Structure</h2>
    <p>The <code>mouseHID</code> structure contains the following fields:</p>
    <ul>
        <li><code>button</code>: Mouse button state (0: no click, 1: left-click).</li>
        <li><code>mouse_x</code>: X-axis movement.</li>
        <li><code>mouse_y</code>: Y-axis movement.</li>
        <li><code>wheel</code>: Scroll wheel (not used in this project).</li>
    </ul>

    <h2>Interrupts</h2>
    <p>GPIO interrupt is configured for the button on <code>PA0</code>. When pressed, the callback function sets a flag to simulate a mouse click.</p>

    <h2>USB Communication</h2>
    <p>The USB HID reports are sent using the <code>USBD_HID_SendReport</code> function. Each report contains the button state and mouse movement data.</p>

    <h2>References</h2>
    <ul>
        <li>STM32F4 HAL Documentation</li>
        <li>USB HID Specification</li>
        <li>STM32CubeMX Configuration Guide</li>
    </ul>

    <h2>License</h2>
    <p>This project is licensed under the terms found in the LICENSE file provided with the software. If no LICENSE file is included, the project is provided AS-IS.</p>
</body>
</html>
