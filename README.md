# DIY Minecraft Compass

A physical replica of the Minecraft compass built with an Arduino Uno, an 8×8 WS2812B NeoPixel matrix, and a GY-271 (HMC5883L) compass module. The compass needle animates across 24 directional frames (15° increments) with the current heading displayed on an I2C LCD screen.

Inspired by [this build](https://www.instagram.com/p/DWOpbKKod3j/), and [this one](https://www.youtube.com/watch?v=OetinqewrzU&t=5s)

---

## End Goal

The finished build will have two modes:

- **True North** — functions as a real compass, the needle tracks magnetic north in real time using the GY-271 module
- **GPS Finder** — bind the compass to a saved GPS coordinate (e.g. your home location) and the needle will always point toward it, just like the Minecraft compass points to your spawn

---

## Current State

> ⚠️ **Work in progress** — the simulation is complete and working. Currently waiting on hardware components to arrive for physical build and testing. The rotary encoder is a temporary stand-in for the compass module during development.

At the moment the project simulates direction using a rotary encoder — turning clockwise or counterclockwise rotates the needle manually. Once the GY-271 module arrives this will be replaced with real heading data.

---

## How it works

- **8×8 NeoPixel matrix** displays the compass needle as a pixel art sprite, with 24 hand-drawn frames covering a full 360° rotation (15° per frame)
- **I2C LCD (16×2)** shows the current direction name and degree value
- **GY-271 compass module** *(end goal)* drives the needle from real magnetic heading data
- Needle colours follow the Minecraft palette — red tip, white tail, dark red shading, grey body

---

## Hardware

| Component | Details |
|---|---|
| Arduino Uno | Main microcontroller |
| WS2812B 8×8 NeoPixel Matrix | Compass display |
| GY-271 (HMC5883L) | Compass module — *awaiting delivery* |
| KY-040 Rotary Encoder | Temporary direction input during development |
| I2C LCD 16×2 | Heading readout |
| 3D printed enclosure | Minecraft compass shell — *pending* |

---

## Wiring

| NeoPixel Pin | Arduino |
|---|---|
| VCC | 5V |
| GND | GND |
| DIN | Pin 6 |

| LCD Pin | Arduino |
|---|---|
| VCC | 5V |
| GND | GND |
| SDA | A4 |
| SCL | A5 |

| Encoder Pin | Arduino |
|---|---|
| CLK | Pin 2 |
| DT | Pin 3 |
| GND | GND |

| GY-271 Pin | Arduino |
|---|---|
| VCC | 3.3V |
| GND | GND |
| SDA | A4 |
| SCL | A5 |

---

## Software

Built with [PlatformIO](https://platformio.org/) in VS Code. Simulated using [Wokwi for VS Code](https://wokwi.com/).

**Libraries:**
- `adafruit/Adafruit NeoPixel`
- `marcoschwartz/LiquidCrystal_I2C`
- `adafruit/Adafruit HMC5883 Unified` *(to be added)*

---

## Project Status

### Done
- [x] 24-frame compass needle animation (15° increments)
- [x] Rotary encoder input with clockwise/counterclockwise detection
- [x] LCD heading display
- [x] Full Wokwi simulation working

### Up next
- [ ] Physical hardware assembly and testing
- [ ] Swap rotary encoder for GY-271 compass module
- [ ] Implement True North mode — live magnetic heading
- [ ] Implement GPS Finder mode — needle points toward a saved coordinate
- [ ] Mode switching (button or long press to toggle between modes)
- [ ] 3D printed Minecraft compass enclosure
- [ ] Pixel mask / matte diffuser panel for authentic screen effect

---

## Pixel Art Tool

During development I built a small browser-based 8×8 pixel editor that outputs Arduino-ready array code directly, used to hand-draw all 24 compass frames. Ask me if you want it.

---

## License

MIT
