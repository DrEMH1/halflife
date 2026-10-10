# Starbie

A tiny motion-controlled digital pet on a custom PCB, built for Hack Club's Half-Life program (Week 1).

## Hardware

| Part | Purpose |
| --- | --- |
| Seeed XIAO ESP32-C3 | Microcontroller |
| SSD1306 OLED (I2C) | Shows the pet |
| MPU6050 | Motion sensor (tilt and shake) |
| DHT11 | Temperature and humidity sensor |
| 2 push buttons | Menu and stats |

## Pinout

| Part | XIAO pin | ESP32-C3 GPIO |
| --- | --- | --- |
| OLED SDA and MPU6050 SDA | D4 | GPIO6 |
| OLED SCL and MPU6050 SCL | D5 | GPIO7 |
| DHT11 data | D1 | GPIO3 |
| Button 1 | D2 | GPIO4 |
| Button 2 | D3 | GPIO5 |

The OLED and the MPU6050 share the same I2C wires (SDA and SCL). Power parts from 3.3V and connect all grounds to GND.

## Repository layout

```
Starbie/
  README.md
  .gitignore
  PCB/                  KiCad project (schematic now, PCB layout next)
  Gerbers/              Gerber and drill files for manufacturing
  Firmware/
    Starbie/
      Starbie.ino       Arduino sketch
```

## Firmware

1. Install the Arduino IDE.
2. In File > Preferences, add this to Additional Boards Manager URLs:
   `https://espressif.github.io/arduino-esp32/package_esp32_index.json`
3. In Tools > Board > Boards Manager, install "esp32 by Espressif Systems".
4. Select the board XIAO_ESP32C3 and the correct port.
5. Install these libraries: Adafruit GFX Library, Adafruit SSD1306, Adafruit MPU6050, DHT sensor library.
6. Open `Firmware/Starbie/Starbie.ino` and click Upload.

## Controls

| Control | Action |
| --- | --- |
| Button 1, first press | Open the radial menu |
| Tilt while the menu is open | Move the selector |
| Button 1, second press | Choose the highlighted action |
| Button 2 | Show or hide the stats screen |
| Shake | Shake reaction |

## Credits

Starter project and guide by SharKingStudios (Hack Club Half-Life).
