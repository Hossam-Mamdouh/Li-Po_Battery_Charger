PowerCore 3V3

USB-C 1S Li-Po Power Management & 3.3 V Supply PCB

PowerCore 3V3 is a compact power-management board for a single-cell
Li-Po battery. It combines USB-C input, Li-Po charging, system
power-path management, battery protection, and a regulated 3.3 V output.

Features

USB-C 5 V power input

1S Li-Po battery support

MCP73871 charger with system power-path management

DW01A + FS8205A battery protection

TPS63802 buck-boost regulator

Regulated 3.3 V output

Designed for up to 500 mA system load

Approximately 500 mA maximum programmed charge current

USB input PTC protection

Charge/status indication LEDs

Power Architecture

USB-C 5 V
    |
    v
Input Protection
    |
    v
MCP73871 Charger + Power Path
    |                    |
    v                    v
1S Li-Po               VSYS
    |                    |
    v                    v
DW01A + FS8205A      TPS63802
Battery Protection   Buck-Boost
                         |
                         v
                       3.3 V
                         |
                         v
                    System Load

Main Components

Reference   Component      Function

U2          MCP73871       Li-Po charger and power-path controller
U3          DW01A          Battery protection controller
Q1          FS8205A        Dual N-channel MOSFET protection switch
U4          TPS63802       Buck-boost regulator
F1          1.5 A PTC      USB input over-current protection
J1          USB-C          5 V power input
Battery     JST-PH 2-pin   1S Li-Po connection

Charger Configuration

Charge Current

PROG1 = 2 kΩ

Programs approximately 500 mA maximum charge current.

The actual charging current is reduced when system load consumes part of
the available input power.

Termination Current

PROG3 = 20 kΩ

Sets approximately 50 mA termination current.

Input Current Mode

SEL = +5V_USB

The charger uses the higher-current adapter mode rather than the 500 mA
USB mode.

Other Settings

CE pulled high → charging enabled

TE# tied to GND → safety timer enabled

THERM uses a fixed 10 kΩ resistor to GND

VPCC tied to +5V_USB

PROG2 pulled high through 10 kΩ

PG# pulled high through 10 kΩ

STAT1 / STAT2 provide status indication

Battery Protection

The protection stage uses a DW01A controller and FS8205A dual MOSFET.

For the selected FUXINSEMI FS8205A:

Pin 1 → S1
Pin 2 → D1/D2
Pin 3 → S2
Pin 4 → G2
Pin 5 → D1/D2
Pin 6 → G1

Pins 2 and 5 are the common drain connection and must be electrically
connected.

External connections:

Q1 S1      → B-
Q1 S2      → GND / P-
Q1 G1      → DW01A OD
Q1 G2      → DW01A OC
Q1 D1/D2   → common drain node

DW01A current sense:

CSI → 1 kΩ → GND / P-

3.3 V Regulation

The TPS63802 maintains a regulated 3.3 V rail from the 1S battery/system
rail.

Intended load: 500 mA

Inductor: 0.47 µH

Input capacitor: 10 µF

Output capacitor: 22 µF

Feedback: 511 kΩ / 91 kΩ

EN: VSYS

MODE: GND

The buck-boost topology allows 3.3 V regulation as battery voltage moves
above and below the output voltage.

USB-C Interface

The USB-C connector is configured as a power input.

CC1 → 5.1 kΩ → GND
CC2 → 5.1 kΩ → GND

Input decoupling and transient protection are included.

Battery Connector

The current schematic uses:

Battery Pin 2 → VBAT (+)
Battery Pin 1 → B- (-)

JST-PH pin numbering does not inherently define battery polarity. Verify
the actual battery cable/mating connector pinout before connection.

Clearly mark + and − on the PCB.

Power Budget

The intended system load is:

3.3 V × 500 mA = 1.65 W

The programmed 500 mA battery charge current is a maximum. Actual charge
current depends on system load, USB supply capability, regulator
efficiency, and charger operating conditions.

PCB Layout Guidelines

Keep TPS63802 input/output capacitors close to the IC.

Keep the 0.47 µH inductor close to the switching pins.

Keep the FB trace away from switching nodes.

Use short, low-impedance high-current paths.

Place USB input protection close to the USB-C connector.

Use appropriate copper width for battery and system power paths.

Provide solid ground copper and thermal areas.

Clearly mark battery polarity.

Design Status

Revision: A
Status: Prototype / Engineering Design

Before manufacturing, verify:

Schematic ERC

PCB DRC

Q1 symbol-to-footprint pin mapping

Battery connector pinout

PTC fuse rating and thermal derating

USB-C input capability

TPS63802 thermal performance

Charger behavior under simultaneous load and charging

Battery protection thresholds

Applications

Embedded systems

IoT devices

Portable electronics

Battery-powered sensors

ESP32-based products

Automation systems

Custom electronics prototypes

Tools

KiCad 10.x

LCSC components where applicable

Author

Hossam Mamdouh
Embedded Systems Engineer

Portfolio: https://hossam-mamdouh.github.io/

License

Choose an appropriate hardware/software license before public release.
