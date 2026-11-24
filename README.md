ESP32 DevKit V1 Expansion Board
A through-hole expansion board designed around a removable 30-pin ESP32 DevKit V1 module. The project is intended to make selected ESP32 power, GPIO and I²C connections easier to access during prototyping.
Project status: Schematic, BOM and Gerber files are documented in this repository. Physical fabrication, assembly, electrical testing and fit verification have not been claimed.

Project overview
- Controller module: 30-pin ESP32 DevKit V1 (removable module)
- EDA software: EasyEDA Standard
- PCB style: Through-hole expansion board
- External input connector: 2-pin, 5.00 mm terminal block
- I²C connector: 4-pin header
- Power selection: 2-pin jumper
- Protection components: MF-R110 resettable fuse and 1N5819 Schottky diode
Intended features
- Two 1×15 female headers for the ESP32 DevKit V1
- Breakout access to the ESP32 pins exposed by the module
- 4-pin I²C connector: 3V3, GND, GPIO21 (SDA) and GPIO22 (SCL)
- External power input connector
- Resettable fuse and series Schottky diode in the external positive supply path
- 100 µF and 100 nF supply capacitors
- Power indicator LED
- GPIO indicator LED
- Jumper intended to select whether protected external power is connected to ESP32 VIN
Main components
Reference	Part / value	Footprint or package	Qty
C4	100 µF capacitor	CAP-D6.3×F2.5	1
C5	100 nF capacitor	RAD-0.1	1
D2	1N5819 Schottky diode	DO-41	1
F1	MF-R110 resettable fuse	Through-hole, 5.08 mm pitch	1
J1, J2	1×15 female headers, 2.54 mm	HDR-F-2.54_1X15	2
J3	1×4 male header, 2.54 mm	HDR-M-2.54_1X4	1
J4	2-pin power terminal block, 5.00 mm	CONN-TH_2P-P5.00	1
JP1	1×2 male jumper header, 2.54 mm	HDR-M-2.54_1X2	1
LED1, LED3	Red 3 mm LEDs	LED-TH_BD3.0_RED	2
R1, R2	1 kΩ resistors	R_AXIAL-0.3	2


See BOM.csv for the exported bill of materials.
I²C connector pinout
J3 pin	Signal	ESP32 connection
1	3V3	3V3
2	GND	GND
3	SDA	GPIO21
4	SCL	GPIO22


Confirm the pin numbering and connector orientation against the schematic and the physical board before connecting peripherals.
External power notes
The intended external supply path is:

J4 (+) → F1 → D2 (1N5819) → protected positive rail

J4 (−) → GND

The 1N5819 is a series reverse-polarity protection diode. Its forward voltage drop means the protected rail will be below the input voltage. Use a regulated supply and verify the voltage at the ESP32 VIN pin under load before operation.

JP1 is intended to connect the protected positive rail to ESP32 VIN when fitted. Do not assume this jumper isolates USB power on every ESP32 DevKit V1 clone. Before using external power and USB at the same time, inspect the exact DevKit power-path schematic or measure/verify its circuit. Keep the external supply disconnected during USB programming unless the power arrangement has been independently verified.

Never apply 5 V to the ESP32 3V3 pin or directly to GPIO pins. GPIO signals are 3.3 V logic.
Repository files
Suggested repository structure:
ESP32-DevKit-V1-Expansion-Board/
├── README.md
├── Schematic/
│   └── Schematic_ESP32-DevKit-V1-Expansion-Board.pdf
├── BOM/
│   └── BOM.csv
└── Gerber/
    └── Gerber_ESP32-DevKit-V1-Expansion-Board.zip
The PDF schematic, CSV BOM and Gerber ZIP supplied with this project should be uploaded to the corresponding folders. Rename the files to the simpler names shown above, or edit the paths in this README to match the actual filenames.
PCB dimensions
The supplied board-outline Gerber describes an approximate board size of 68.71 mm × 42.29 mm. This is derived from the Gerber outline coordinates; verify the dimensions in your PCB editor and against the physical ESP32 module before ordering boards.
Verification checklist before fabrication
- [ ] Confirm J1/J2 row spacing against the exact 30-pin ESP32 DevKit V1.
- [ ] Confirm female-header footprint, pin pitch, orientation and mating height.
- [ ] Confirm all connector pin numbers and net connections against the schematic.
- [ ] Verify D2 polarity and the 1N5819 DO-41 footprint.
- [ ] Verify MF-R110 lead spacing and footprint.
- [ ] Verify electrolytic capacitor polarity and lead spacing.
- [ ] Check LED polarity and resistor connections.
- [ ] Confirm JP1 connects protected power to VIN as intended and does not create an unintended USB backfeed path.
- [ ] Run schematic ERC and PCB DRC; resolve all genuine errors.
- [ ] Inspect Gerber layers and drill files in a Gerber viewer.
- [ ] Perform physical fit checks and electrical tests after fabrication.
Learning outcomes
This project documents practice in schematic capture, through-hole component selection, connector pinout planning, power-input protection, BOM export and Gerber generation using EasyEDA Standard.
Author
Add your name, GitHub profile and contact details here.
