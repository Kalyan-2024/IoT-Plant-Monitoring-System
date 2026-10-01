# Wiring guide (starter pin map)

Always check the labels and datasheets for your specific modules. Power down before wiring.

| Module pin | ESP32 / connection | Notes |
|---|---|---|
| Soil sensor AO | GPIO 34 | Analog input; ensure output does not exceed ESP32 input limits |
| Soil sensor VCC | Module-rated supply | Check whether your sensor supports 3.3V |
| Soil sensor GND | GND | Common ground for signal reference |
| Rain sensor AO | GPIO 35 | Analog input; ensure output does not exceed ESP32 input limits |
| Rain sensor VCC | Module-rated supply | Check module voltage requirements |
| Rain sensor GND | GND | Common ground for signal reference |
| DHT22 DATA | GPIO 4 | Use a pull-up resistor if your module does not include one |
| DHT22 VCC | 3.3V or module-rated supply | Follow sensor/module specifications |
| DHT22 GND | GND | Common ground |
| Relay IN | GPIO 26 | Verify 3.3V logic compatibility and active level |
| Relay VCC | Relay module-rated supply (often 5V) | Do not assume every relay module is ESP32-compatible |
| Relay GND | GND | Follow module instructions; common reference may be required |
| Pump | Relay contacts and separate pump supply | Never connect the pump directly to an ESP32 pin |
| PIR OUT (optional) | GPIO 27 | Use only if PIR is included |
| LCD SDA (optional) | GPIO 21 | Confirm LCD backpack voltage and I2C logic compatibility |
| LCD SCL (optional) | GPIO 22 | Confirm LCD backpack voltage and I2C logic compatibility |
| LCD VCC/GND | Module-rated supply / GND | Some 5V LCD backpacks pull I2C lines to 5V; use level shifting if needed |

## Important notes
- Do not connect any sensor output that may reach 5V directly to an ESP32 ADC pin.
- Relay and pump wiring depends on the exact hardware. Use a properly rated driver/relay and a suitable external pump supply.
- The pump control logic is only a starter example. Test with the pump disconnected first.
