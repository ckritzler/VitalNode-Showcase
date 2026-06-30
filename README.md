# VitalNode

**Real-time BLE telemetry for cycling and fitness livestreams.**

VitalNode is an Android-based telemetry system that reads Bluetooth Low Energy sports sensors and prepares live fitness data for browser-based overlays and livestreaming tools such as OBS Studio and PRISM Live Studio.

🚧 **VitalNode is currently under active development.**

---

## What VitalNode does

VitalNode connects to supported BLE fitness sensors and converts raw sensor data into live, streaming-ready metrics.

The Android device acts as a bridge between sports sensors and livestream overlays:

```text
BLE Sensors → Android App → Local API → Browser Overlay → OBS / PRISM
```

---

## Current status

VitalNode currently has a working Android prototype with BLE sensor discovery and live heart rate support.

Implemented so far:

* Android project setup
* Kotlin + Jetpack Compose app structure
* Sensor data model
* Local sensor repository using StateFlow
* BLE permission handling
* Android version-aware BLE permission checks
* Bluetooth and Location readiness checks
* User guidance when Bluetooth or Location is disabled
* BLE scanner
* BLE device classification
* Heart rate sensor detection
* BLE connection manager
* Heart Rate Measurement notifications
* Battery Level reading
* Live dashboard card for connected sensors
* Manual connect / disconnect flow
* Graceful cleanup on disconnect
* Mock data generator kept for later testing

Tested with:

* **Polar H9 Heart Rate Sensor**
* **Android 10 device**
* Bluetooth + Location based BLE scanning

---

## Supported / planned metrics

| Metric        | Status            |
| ------------- | ----------------- |
| Heart rate    | Working prototype |
| Battery level | Working prototype |
| Cycling power | Planned           |
| Cadence       | Planned           |
| Speed         | Planned           |

Example future output:

```json
{
  "hr": 152,
  "battery": 87,
  "power": 280,
  "cadence": 90,
  "speed": 36.5
}
```

---

## Use case

VitalNode is designed for streamers, cyclists, runners and fitness creators who want to show live biometric and training data during a livestream.

Example use cases:

* Heart rate overlay during cycling streams
* Power and cadence overlay for indoor training
* Live fitness metrics in OBS Studio
* Mobile sensor bridge for browser-based streaming overlays
* Future local HTTP/WebSocket telemetry endpoint

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

Current internal Android flow:

```text
Jetpack Compose UI
        ↓
DashboardViewModel
        ↓
SensorRepository
        ↓
BLE Scanner / BLE Connection Manager
        ↓
Bluetooth LE Sensor
```

---

## Android BLE behavior

VitalNode handles Android BLE requirements depending on the Android version.

On Android 11 and older:

* Bluetooth must be enabled
* Location services must be enabled
* Location permission is required for BLE scanning

On Android 12 and newer:

* Bluetooth runtime permissions are required
* Location is not planned to be required for VitalNode BLE scanning

The app currently checks whether Bluetooth and Location are ready before scanning and guides the user when a required system setting is disabled.

---

## Planned features

* [x] Android project setup
* [x] Private source repository
* [x] Public showcase repository
* [x] Sensor data model
* [x] Local data repository
* [x] Test dashboard with mock values
* [x] BLE scanner
* [x] BLE device classification
* [x] Heart rate BLE support
* [x] Battery level reading
* [x] Connect / disconnect flow
* [x] BLE readiness checks
* [ ] Dashboard design v1
* [ ] Local HTTP API
* [ ] WebSocket live endpoint
* [ ] Browser overlay
* [ ] Cycling power support
* [ ] Cadence and speed support
* [ ] OBS Studio test
* [ ] PRISM Live Studio test
* [ ] Public demo screenshots
* [ ] Demo video

---

## Tech stack

* Kotlin
* Android
* Jetpack Compose
* Bluetooth Low Energy
* Kotlin Coroutines
* StateFlow
* MVVM-inspired structure

Planned:

* Ktor Server
* WebSocket
* HTML / CSS / JavaScript browser overlay

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

## Roadmap

### Milestone 1: Android BLE prototype

Status: **In progress**

Goal:

* Discover BLE fitness sensors
* Connect to a heart rate sensor
* Display live heart rate and battery level
* Handle Bluetooth / Location readiness
* Provide a basic dashboard UI

### Milestone 2: Dashboard Design v1

Goal:

* Improve visual layout
* Add sensor status sections
* Add clearer connected / disconnected states
* Improve empty states and user guidance

### Milestone 3: Local telemetry API

Goal:

* Expose live sensor data through a local HTTP endpoint
* Prepare JSON output for browser overlays

### Milestone 4: Live overlay

Goal:

* Build a browser overlay for OBS / PRISM
* Display heart rate and future cycling metrics in real time

---

## License

No source code is published in this repository at the moment.

This repository currently serves as a public showcase and documentation hub for VitalNode.
