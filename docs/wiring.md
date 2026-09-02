# Wiring

Two different boards are in play: the Central node runs on an **ESP32**;
Transmitter and Relay run on **Arduino Nano**. Pins below were read out of
firmware source that isn't included in this repo (see the top-level
README) — they are **not independently verified by continuity testing**,
just transcribed. Treat as a starting reference to check against your own
board before relying on it.

## Central (ESP32)

| RFM95W pin | ESP32 pin |
|---|---|
| NSS / CS | GPIO 5 |
| RST | GPIO 14 |
| DIO0 | GPIO 26 |
| 3.3V | 3V3 |
| GND | GND |

| Peripheral | ESP32 pin |
|---|---|
| Buzzer + | GPIO 27 |
| LED + | GPIO 12 |
| OLED SCL | GPIO 22 |
| OLED SDA | GPIO 21 |

OLED is I2C, SSD1306 128x64, address `0x3C`.

On boot, Central starts a WiFi access point (`GhOsT-pRoToCoL`, password
`12345678`) serving a captive-portal config page for naming Post/Relay
nodes — connect to it and it should redirect to the config page
automatically.

## Transmitter / Post (Arduino Nano)

| RFM95W pin | Nano pin |
|---|---|
| NSS / CS | D10 |
| RST | D9 |
| DIO0 | D2 |
| SCK | D13 |
| MISO | D12 |
| MOSI | D11 |
| 3.3V | 3V3 |
| GND | GND |

| Peripheral | Nano pin |
|---|---|
| Button | D7 (other leg to GND, `INPUT_PULLUP`) |
| LED/buzzer | D6 |

## Relay (Arduino Nano)

RFM95W wiring identical to Transmitter above.

| Peripheral | Nano pin |
|---|---|
| Buzzer | D7 |
| LED | D6 |

## Notes from the build

- RFM95W needs 3.3V — don't feed it 5V directly; confirm your breakout
  board has a regulator if powering from a 5V rail.
- Antennas are externally mounted SMA whips, hot-glued for strain relief.
- Multiple enclosures share the same internal layout: Nano/ESP32 stacked
  under the RFM95W module, battery holder glued to the base.
