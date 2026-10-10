# Starbie PCB (KiCad)

Contents:

- `Starbie.kicad_pro` and `Starbie.kicad_sch`: the project and the finished schematic.
- `libs/`: the Week 1 care package libraries (XIAO symbol and Imported Parts footprints).
- `sym-lib-table` and `fp-lib-table`: let KiCad find the libraries from inside this folder.

Not done yet: the PCB layout (`Starbie.kicad_pcb`). Open the project, open the PCB Editor, and run "Update PCB from Schematic" to start the layout.

Parts and footprints:

| Ref | Part | Footprint |
| --- | --- | --- |
| U2 | XIAO ESP32-C3 | Imported Parts:XIAO-ESP32-C3-SMD |
| J1 | OLED (Conn_01x04_Pin) | Imported Parts:Display_128x64_096_I2C |
| J2 | MPU6050 (Conn_01x08_Pin) | Connector_PinHeader_2.54mm:PinHeader_1x08_P2.54mm_Vertical |
| U1 | DHT11 | Sensor:Aosong_DHT11_5.5x12.0_P2.54mm |
| R1 | 10k pull-up on DHT11 data | Resistor_THT:R_Axial_DIN0204_L3.6mm_D1.6mm_P7.62mm_Horizontal |
| SW1, SW2 | SW_Push (Cherry MX) | Button_Switch_Keyboard:SW_Cherry_MX_1.00u_PCB |

Nets: SDA = XIAO D4, SCL = XIAO D5, DHT11_DATA = D1, BUTTON_1 = D2, BUTTON_2 = D3.
