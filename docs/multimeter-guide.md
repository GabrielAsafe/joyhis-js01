# Detailed Multimeter Tutorial

## Lead placement

For voltage, resistance, continuity and diode mode:

- Black lead: COM.
- Red lead: V/Ω.

For current, the red lead moves to mA or A. Leaving it in the current jack and probing across a voltage source creates a near-short and is a common cause of board damage.

## Voltage

Voltage is measured in parallel.

1. Select DC voltage.
2. Choose a range above the expected value.
3. Connect black probe to known GND.
4. Touch red probe to the test point.
5. Expose only 1–2 mm of probe tip near SMD parts.

Examples:

- Battery: choose a range safely above full-charge voltage.
- Dashboard input: approximately 15 V.
- Logic rail: likely 3.3 or 5 V.
- Hall supply: typically 5 V.

A multimeter averages PWM and UART. It cannot show baud rate, packets or ripple. The 7.56 V at 4R7 and RX/TX averages must be checked with an oscilloscope/logic analyser.

## Resistance

Power must be off.

1. Disconnect the battery.
2. Wait for capacitors to discharge.
3. Touch probes together and note lead resistance.
4. Measure across the component or from a node to GND.
5. Record polarity and whether the reading changes.

A direct component measurement is still affected by everything connected in parallel. A node-to-GND measurement is useful for finding shorts but is not the resistor's value unless the topology proves it.

## Capacitors in resistance mode

The meter supplies a small test current and charges the capacitor:

```text
lower reading -> rising reading -> high/open reading
```

Changing or falling values can result from parallel resistors, semiconductor junctions, charge redistribution or autoranging.

## Diode mode

Power off. Measure both polarities. Record exact readings. For D1, a decisive test may require lifting one terminal because the buck circuit provides parallel paths.

## Current

Current is measured in series:

```text
source -> meter -> load -> return
```

Never put the meter in current mode across the battery or capacitor. For scooter battery current, use a DC clamp meter or a suitable shunt and proper equipment. For PCB diagnosis, a current-limited bench supply is safer.

## Continuity

Use unpowered for tracing connectors, ground planes, inductors, fuses, vias and broken tracks. A beep does not prove a semiconductor is good.

## Measuring U1 buck converter

### Power off

- 15 V input to GND resistance.
- Output side of 4R7 to GND resistance.
- D1 diode readings both ways.
- 4R7 continuity.
- Feedback resistors.
- Visual inspection for cracked capacitors and burned tracks.

### Powered, preferably current-limited

- U1 input voltage.
- U1 enable if identified.
- Output after 4R7.
- Temperature of U1/D1.
- Switch-node waveform with scope.
- Output ripple at capacitor.

## Safer probing

- Attach the ground clip before power-up.
- Use probe-tip insulation.
- Solder temporary test wires to tiny nodes.
- Do not hold two sharp probes over adjacent IC pins.
- Measure capacitor positive relative to a fixed GND clip instead of touching both capacitor terminals.

## Measurement log format

```text
Date/time:
Board state:
Battery/supply voltage:
Meter model:
Mode and range:
Black-probe reference:
Red-probe point:
Reading:
Stable or changing:
Probe polarity:
Notes/photo filename:
```
