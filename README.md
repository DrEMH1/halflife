# Starbie

Starbie is a tiny pocket digital pet. A little creature wanders around a small OLED screen, and you interact with it by tilting, shaking and pressing two keys. It runs on a custom PCB I designed in KiCad around a Seeed XIAO ESP32-C3.

Built for Hack Club's Half-Life program (Week 1), based on the Starbie example project by SharKingStudios.

![Starbie schematic](images/schematic.png)

*The Starbie schematic in KiCad. Parts connect through shared net names (SDA, SCL, BUTTON_1, BUTTON_2, DHT11_DATA).*

## How it works

- The **XIAO ESP32-C3** is the brain. It runs the firmware and talks to every other part.
- The **0.96" OLED** and the **MPU6050** motion sensor share two I2C wires, SDA and SCL. The ESP32 reads the MPU6050 to detect tilting and shaking, and draws the pet on the OLED.
- The **DHT11** sensor reads temperature and humidity on a single data wire. A **10k resistor (R1)** pulls that data line up to 3.3V.
- Two **Cherry MX switches** are the buttons. Each one connects its pin to ground when pressed, and the firmware reads it with the internal pull-up resistor.
- The pet's joy, energy and fullness are saved in the ESP32's flash memory, so they stay after power-off.

### Controls

| Control | What it does |
| --- | --- |
| Button 1, first press | Opens the radial menu |
| Tilt while the menu is open | Moves the selector ball toward one of four actions |
| Button 1, second press | Chooses the highlighted action |
| Button 2 | Shows or hides the stats screen (joy, energy, fullness, temperature, humidity) |
| Shake | Makes Starbie react |

The four actions are NAP, PLAY, FEED and PET. Each one changes the pet's stats and plays its own little animation.

## Hardware

| Part | Purpose |
| --- | --- |
| Seeed XIAO ESP32-C3 | Microcontroller |
| 0.96" SSD1306 OLED (I2C) | Display |
| MPU6050 module | Tilt and shake sensing |
| DHT11 | Temperature and humidity |
| 10k resistor | Pull-up for the DHT11 data line |
| 2x Cherry MX switches | Buttons |

### Pinout

| Part | XIAO pin | ESP32-C3 GPIO |
| --- | --- | --- |
| OLED SDA and MPU6050 SDA | D4 | GPIO6 |
| OLED SCL and MPU6050 SCL | D5 | GPIO7 |
| DHT11 data | D1 | GPIO3 |
| Button 1 | D2 | GPIO4 |
| Button 2 | D3 | GPIO5 |

## Repository layout

```
Starbie/
  README.md
  images/               Pictures used in this README
  PCB/                  KiCad project (schematic and PCB)
  Gerbers/              Gerber and drill files for manufacturing
  Firmware/
    Starbie/
      Starbie.ino       Arduino sketch
```

## Build it

1. Open `PCB/Starbie.kicad_pro` in KiCad 10 to see or edit the design.
2. Order the board using the files in `Gerbers/`.
3. Solder the parts, then upload the firmware (below).

### Upload the firmware

1. Install the Arduino IDE.
2. In File > Preferences, add this to Additional Boards Manager URLs:
   `https://espressif.github.io/arduino-esp32/package_esp32_index.json`
3. In Tools > Board > Boards Manager, install "esp32 by Espressif Systems".
4. Select the board XIAO_ESP32C3 and the correct port.
5. Install these libraries: Adafruit GFX Library, Adafruit SSD1306, Adafruit MPU6050, DHT sensor library.
6. Open `Firmware/Starbie/Starbie.ino` and click Upload.

## Credits

Starter project and guide by SharKingStudios (Hack Club Half-Life), MIT licensed.
