# SailOne — Autonomous Atlantic Sailboat

A 2.5m autonomous sailboat designed to cross the Atlantic Ocean, powered entirely by wind and solar energy. Built as an open-source project in Setúbal, Portugal.
----
<img width="602" height="595" alt="image" src="https://github.com/user-attachments/assets/29908790-4d65-4c96-90cc-235c0b86c5bb" />

[![Website](https://img.shields.io/badge/website-sailone.org-blue)](https://sailone.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Partner](https://img.shields.io/badge/partner-Prusa%20Research-orange)](https://prusament.com)

---

## Architecture

```
Pixhawk ArduPilot  →  navigation, autopilot, GPS, attitude
ESP32              →  motor PID control, wind vane, dual encoder slip detection
Raspberry Pi       →  sensor logging, web dashboard, satellite comms (Iridium)
```

---

## Repository Structure

```
SailOne/
├── pi_code/
│   ├── sailboat_dashboard.py     — Flask dashboard, MAVLink, CSV logging, power management
│   └── watchdog.py               — TPL5110 hardware watchdog kicker
├── esp32_code/
│   ├── esp32_controller_v6.ino   — Full controller: dual AS5600 encoders, PID, slip detection
│   ├── esp32_test_v3.ino         — Test sketch: TCA9548A + 3x AS5600 + FlySky
│   └── rudder_test_v2.ino        — Rudder-only test with magnet status check
├── simulation/
│   └── rudder_simulator.py       — Python PID simulator: 10 ocean conditions
├── docs/
│   └── SAILONE_Specifications.pdf
└── README.md
```

---

## Electronics Stack

| Component | Role |
|-----------|------|
| Pixhawk (ArduPilot Rover/Boat) | Autopilot, GPS, heading, attitude |
| Raspberry Pi Zero 2W | Dashboard, logging, Iridium comms |
| ESP32 | Motor PID, wind vane, encoder reading |
| TCA9548A I2C multiplexer | 5x AS5600 encoders on one bus |
| AS5600 magnetic encoders (x5) | Wind, sail shaft, sail motor, rudder shaft, rudder motor |
| BTS7960 H-bridge (x2) | Sail and rudder motor drivers |
| 5840-31ZY worm gear motor | Sail control |
| JGY-370 worm gear motor | Rudder control |
| BMP280 | Temperature + pressure |
| PCF8591 ADC | Moisture, light, NTC thermistors |
| DS18B20 | Waterproof temperature probes |
| RockBLOCK 9603 (planned) | Iridium satellite comms |

---

## Power System

| Component | Spec |
|-----------|------|
| Battery | 4S LiFePO4 12.8V 30Ah |
| Solar | 20W panel + MPPT controller |
| Daily consumption | ~23 Wh/day |
| Solar production | ~75 Wh/day |
| Battery autonomy (no sun) | 13 days |

---

## Project Status

- ✅ Electronics bench-tested and operational
- ✅ GPS lock confirmed, all sensors reading
- ✅ First autonomous sailing tests on 1.5m test vessel
- ✅ Dual encoder belt slip detection working
-  Hull design and mold production — in progress
-  Hull construction and motor assembly — summer 2026
-  Full water testing and sea trials — autumn 2026
-  Madeira crossing attempt (~970km) — autumn 2026
-  Atlantic crossing attempt — 2027

---

## Partners

- **[Prusa Research](https://prusament.com)** — filament and 3D printing equipment

---

## Website

[sailone.org](https://sailone.org) — full build log, specifications, and live tracking

## License

MIT — all code and designs are open-source. Build your own.
