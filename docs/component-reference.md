# PCB Reference Designators and Component Testing

| Prefix | Component | Common function |
|---|---|---|
| R | Resistor | Current limiting, dividers, pull-up/down, feedback, sensing |
| C | Capacitor | Filtering, decoupling, timing, energy storage |
| D | Diode | Rectification, flyback, reverse protection, ESD |
| Q | Transistor/MOSFET | Switching, latching, amplification |
| U | Integrated circuit | MCU, regulator, driver, logic |
| L | Inductor | Switching-converter energy storage and filtering |
| X/Y | Crystal/resonator | Clock source |
| SW | Switch | User/electronic switch |
| J/CN/CON | Connector | Cable interface |
| TP | Test point | Measurement access |
| F | Fuse | Overcurrent protection |
| FB | Ferrite bead | High-frequency noise filtering |
| LED | LED | Indicator/backlight |
| BZ | Buzzer | Audible indicator |
| JP | Jumper | Configuration/trace bridge |
| RV/VR | Variable resistor | Adjustment |
| NTC | Thermistor | Temperature/inrush sensing |
| TVS | Transient suppressor | Surge protection |

## Resistors

Measure unpowered. In-circuit parallel paths can make the reading lower than the marked value. One end may need lifting. Measuring one terminal to GND measures the entire node-to-ground network, not necessarily that resistor.

`R390` typically represents 0.390 Ω, suitable as a current shunt.

## Capacitors

In resistance mode, a capacitor often reads low initially and then rises as the meter charges it. This is normal. A persistent near-zero value can indicate a shorted capacitor or a short elsewhere on the rail. Accurate capacitance generally requires lifting one terminal; ESR requires an ESR meter.

## Diodes

In diode mode, ordinary silicon often reads about 0.5–0.8 V forward and Schottky about 0.15–0.45 V. Reverse should normally be open. In-circuit readings can be altered by parallel paths.

## Inductors

`4R7` commonly means 4.7 µH. DC resistance should be low, but a low ohmic reading does not prove correct inductance under load.

## MOSFETs

Check drain-source for shorts, then gate-source and gate-drain. A body diode normally appears in one drain-source direction. Near-zero both directions can indicate failure.

## Integrated circuits

Do not attempt to “measure the resistance of an IC” as a complete test. Verify supply, enable, reset, clock, input/output activity, temperature and rail shorts.

## Crystals

A crystal cannot be validated with resistance mode. Use an oscilloscope with a low-capacitance probe or a frequency measurement method.
