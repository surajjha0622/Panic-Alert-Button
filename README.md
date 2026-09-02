# LoRa Panic Alert System — Build Log

> **This is a photo and hardware-notes archive, not a working codebase.**
> No firmware is included. Pin/wiring info below was transcribed from
> source files that existed during development but aren't published here,
> and hasn't been independently re-verified with continuity testing.
> Treat everything in this repo as unverified personal notes — not
> instructions, not a kit, not something to deploy as-is.

A long-range wireless panic-button / alert system, built as a hobby
project: battery-powered button posts, LoRa relays, and an ESP32 base
station with an OLED display and a WiFi config portal for naming nodes.

![Deployed pair, showing a received alert](docs/images/deployed-pair-received-alert.jpg)

More photos: [`docs/gallery.md`](docs/gallery.md)
Demo video: [`docs/videos/demo.mp4`](docs/videos/demo.mp4)

## What's here

- [`docs/gallery.md`](docs/gallery.md) — build photos
- [`docs/videos/demo.mp4`](docs/videos/demo.mp4) — demo video
- [`docs/wiring.md`](docs/wiring.md) — pinout notes by node role
  (Transmitter/Post, Relay, Central)

## Hardware

| Part | Notes |
|---|---|
| Arduino Nano (ATmega328) | Transmitter, Relay |
| ESP32 dev board | Central |
| RFM95W (SX1276) LoRa module | 915 MHz, one per node |
| 0.96" SSD1306 OLED (I2C, 128x64) | Central only |
| Piezo / sharp buzzer | all nodes |
| Momentary push button | Transmitter |
| Status LED | Relay, Transmitter |
| 2xAA/3xAAA battery holder | per node |
| Whip antenna (SMA) | per node |

## License

MIT — see [LICENSE](LICENSE).
