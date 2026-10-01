# IoT-Enabled Plant Growth and Environment Monitoring System

## Project overview
This project uses an ESP32 to read soil moisture, temperature, humidity, and rain-sensor values. A relay can control a water pump when the soil appears dry and rain is not detected. An optional 16x2 I2C LCD displays readings.

> This is a starter implementation. Sensor readings and thresholds must be calibrated for the exact modules before practical or unattended use.

## Features
- Reads an analog soil-moisture sensor.
- Reads temperature and humidity using a DHT22.
- Reads an analog rain sensor.
- Optional PIR motion-sensor reading.
- Controls a relay output for a water pump.
- Optional 16x2 I2C LCD.
- Includes a maximum pump-on time and cooldown as basic safeguards.

## Hardware
- ESP32 development board
- Analog soil-moisture sensor
- DHT22 temperature/humidity sensor
- Rain sensor module with analog output
- 5V relay module compatible with ESP32 logic, or an appropriate driver
- Water pump and separate, correctly rated power supply
- Optional PIR sensor
- Optional 16x2 I2C LCD
- Breadboard, jumper wires, and suitable power supplies

## Pin connections
See [`wiring.md`](wiring.md). Confirm each module's pin labels and voltage requirements before connecting.

## Software requirements
Install Arduino IDE and the ESP32 board package. Install these libraries through Library Manager:
- DHT sensor library by Adafruit
- Adafruit Unified Sensor (if requested by the DHT library)
- LiquidCrystal I2C library (a compatible version)

## Upload steps
1. Open `main.ino` in Arduino IDE.
2. Select your ESP32 board and its COM/serial port.
3. Verify the pin assignments and whether your relay is active-LOW or active-HIGH.
4. Upload the sketch.
5. Open Serial Monitor at **115200 baud**.
6. Check sensor readings with the pump disconnected first.
7. Calibrate `SOIL_DRY_THRESHOLD` and `RAIN_WET_THRESHOLD` using your actual sensor readings.
8. Test the relay and pump safely before leaving the system unattended.

## Calibration notes
- Soil sensor readings vary by model, soil type, supply voltage, and sensor placement. Record values in dry and moist soil before choosing a threshold.
- Rain-sensor analog readings can vary by module. Test dry and wet conditions before choosing `RAIN_WET_THRESHOLD`.
- The code assumes higher soil ADC values indicate drier soil and lower rain ADC values indicate wet conditions. Reverse the comparison if your module behaves differently.
- LCD I2C addresses are often `0x27` or `0x3F`. Change the address in `main.ino` if required.

## Safety
- Do not power a pump from an ESP32 GPIO or the board's 3.3V pin.
- Use a separate supply rated for the pump and a relay/driver rated for the pump's voltage and current.
- Ensure grounds and signal connections follow the module manufacturer's instructions.
- Keep water away from exposed electronics.
- Do not leave the pump unattended until the system has been thoroughly tested.

## Suggested future improvements
- Add a Wi-Fi dashboard using Blynk or ThingSpeak.
- Store readings with timestamps.
- Add a circuit diagram and photographs of the completed prototype.
- Add a data-calibration table and test results.

## Project status
Starter source code and documentation. Update this section with your actual prototype results, photos, and any changes you make.
