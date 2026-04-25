# SailOne
2.5m autonomous DIY sailboat built to cross the Atlantic — Pixhawk + Raspberry Pi + ESP32
# SailOne — Autonomous Atlantic Sailboat

An autonomous 2.5m sailboat designed to cross the Atlantic Ocean as part of the Microtransat Challenge.

## Architecture

Pixhawk ArduPilot → navigation and autopilot
ESP32 → motor PID control, wind vane, belt slip detection
Raspberry Pi → sensor logging, web dashboard, satellite comms

## What's in this repo

- `sailboat_dashboard.py` — Pi main script: sensor reading, web dashboard, CSV logging, power management, capsize detection, leak monitoring, simulated Iridium
- `esp32_controller.ino` — ESP32 firmware: wind vane NMEA output, sail/rudder PID, Pixhawk PWM input, watchdog, boot counter
- `FULL_WIRING.txt` — Complete wiring table for the entire system

## Sensors

- GPS, heading, attitude, wind (via Pixhawk MAVLink)
- Sail + wind AS5600 magnetic encoders (via ESP32)
- BMP280 temperature + pressure (I2C)
- PCF8591 4-channel ADC: moisture, light, 2x NTC thermistor (I2C)
- DS18B20 waterproof temperature probes (1-Wire)
- Rudder potentiometer (ESP32 ADC)

## Website

https://sailone.org

## License
