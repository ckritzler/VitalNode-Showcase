# VitalNode

**Real-time BLE telemetry for cycling and fitness livestreams.**

VitalNode is an Android-based telemetry system that reads Bluetooth Low Energy sports sensors and exposes the live data through a local HTTP/WebSocket server. The data can then be used in browser-based overlays for streaming tools such as OBS Studio and PRISM Live Studio.

> 🚧 VitalNode is currently under active development.

---

## What VitalNode does

VitalNode connects to supported BLE sensors and converts raw sensor data into live streaming-ready metrics.

Supported / planned metrics:

* Heart rate
* Cycling power
* Cadence
* Speed

Example output:

```json
{
  "hr": 152,
  "power": 280,
  "cadence": 90,
  "speed": 36.5
}
```

---

## Use case

VitalNode is designed for streamers, cyclists and fitness creators who want to show live biometric and cycling data during a livestream.

The Android device acts as the bridge between:

```text
BLE Sensors → Android App → Local API → Browser Overlay → OBS / PRISM
```

---

## Architecture

```text
+-------------------+
| BLE Sensors       |
| HR / Power / RPM  |
+---------+---------+
          |
          v
+-------------------+
| VitalNode Android |
| BLE + Data State  |
+---------+---------+
          |
   HTTP / WebSocket
          |
          v
+-------------------+
| Browser Overlay   |
+---------+---------+
          |
     +----+----+
     |         |
     v         v
    OBS      PRISM
```

---

## Planned features

* [x] Android project setup
* [x] Private source repository
* [x] Public showcase repository
* [ ] Sensor data model
* [ ] Local data repository
* [ ] Test dashboard with mock values
* [ ] Local HTTP API
* [ ] WebSocket live endpoint
* [ ] Browser overlay
* [ ] Heart rate BLE support
* [ ] Cycling power support
* [ ] Cadence and speed support
* [ ] OBS Studio test
* [ ] PRISM Live Studio test

---

## Tech stack

* Kotlin
* Android
* Jetpack Compose
* Bluetooth Low Energy
* Kotlin Coroutines
* StateFlow
* Ktor Server
* WebSocket
* HTML / CSS / JavaScript

---

## Target streaming tools

VitalNode is designed to work with browser-based sources and web overlays, including:

* OBS Studio
* PRISM Live Studio
* Streamlabs Desktop
* Standard web browsers

---

## Repository structure

The source code is currently developed in a private repository.

This public repository is used as a project showcase and documentation hub.

It will contain:

* Project description
* Roadmap
* Screenshots
* Overlay previews
* Demo videos
* Release notes

---

## Current status

The project is in the initial setup phase.

Next milestone:

> Build the internal data model and a mock dashboard before implementing Bluetooth support.

---

## License

No source code is published in this repository at the moment.
