Smart-Irrigation-System

Smart Irrigation System (Cisco Packet Tracer)

Applied Industrial IoT mini-project — Smart irrigation that monitors soil moisture and triggers watering automatically. Includes Packet Tracer build steps, MCU code, and demo guide.

Aim
Design and simulate a smart irrigation system that minimizes water usage by monitoring soil moisture and automatically controlling a pump/solenoid valve in Cisco Packet Tracer (CPT)**.

Problem Statement
Conventional irrigation often overwaters fields, wasting water and energy. Create a CPT-based IoT solution that:
- Continuously senses soil moisture
- Starts irrigation when moisture drops below a threshold
- Stops irrigation when optimal moisture is reached
- Logs/visualizes readings and actions via MQTT/IoT Cloud (Packet Tracer IoT Server / Home Gateway)
- Provides an easy demo (screen recording) and a clear repo for evaluation.

Scope of the Solution
- Simulation-first in Cisco Packet Tracer (no physical hardware required).
- Local IoT network using Home Gateway (or IoT Server) for device registration and optional MQTT telemetry.
- Single irrigation zone (extendable to multiple zones).
- Basic threshold control with hysteresis; easily extendable to scheduling, weather data, or multi-sensor fusion.
- Optional real-world extension using Arduino/ESP boards (not required for this submission).

Required Components
Software / IDE
- Cisco Packet Tracer 8.x (IoT supported)
- (Optional) TinkerCad/Fritzing for alternative visual circuits
- (Optional) Arduino IDE (if you also prototype on real hardware)
- Any screen recorder (for demo video)

Cisco Packet Tracer IoT Devices
- Home Gateway (or Server-PT with IoT services)
- Microcontroller-PT (Generic MCU)
- Soil Moisture Sensor (Analog)
- Relay (or Transistor + Relay module) — to switch load
- Water Pump / Solenoid Valve (Actuator; can use **Water Sprinkler** device)
- Power (DC supply as needed)
- Switch/Router/Wireless (if using IP/MQTT)
- PC (for registration and dashboard access)

### Optional Physical Hardware (for future work)
- Arduino UNO/Nano or ESP8266/ESP32
- Soil moisture probe (analog)
- 5V relay module
- 12V pump + power supply

## Simulated Circuit (Packet Tracer)
- **A0** (MCU) ← Soil Moisture Sensor **Analog OUT**
- **D2** (MCU) → Relay **IN**
- Relay **COM/NO** → **Pump/Sprinkler** (actuator power line)
- MCU registered to **Home Gateway** via IoT wireless or wired network
- Optional: MQTT topic `farm/zone1/moisture` and `farm/zone1/valve`

A detailed **build walkthrough** is in [`docs/packet-tracer-build.md`](docs/packet-tracer-build.md).
Connection mapping is in [`sim/connection_table.csv`](sim/connection_table.csv).

## How It Works
1. MCU reads **analog moisture** on A0 (0–1023).
2. If moisture **< DRY threshold**, it **energizes relay** to start the pump.
3. Once moisture **> WET threshold**, it **de-energizes relay** to stop watering.
4. Periodically **publishes** readings/events to MQTT (optional).

## Repo Structure
```
smart-irrigation-pt/
├─ docs/
│  ├─ packet-tracer-build.md
│  ├─ demo-script.md
│  └─ architecture.md
├─ src/
│  └─ mcu/
│     └─ irrigation.js
├─ sim/
│  └─ connection_table.csv
├─ media/
│  └─ (place your screenshots / demo video here)
└─ README.md
```

## Quick Start (Simulation)
1. Open Cisco Packet Tracer.
2. Build the circuit following `docs/packet-tracer-build.md` (or replicate from your instructor-provided template).
3. In the MCU's **Programming** tab, create a JavaScript project and paste `src/mcu/irrigation.js`.
4. **Run** the script. Adjust thresholds to suit the sensor scale you observe.
5. (Optional) Configure **Home Gateway / IoT Server** and verify MQTT logs.

## Demo Video / Screenshots
- Follow `docs/demo-script.md` to record a **2–3 minute** screen-capture demo.
- Save the video in `media/` and push to GitHub (or upload to a platform and link).


