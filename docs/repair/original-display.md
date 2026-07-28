# Original Dashboard Repair Procedure

The current board has two layers of fault history: the original failure to remain on after button release, and the later complete no-power failure after an accidental short.

## Step 1 — disconnect and inspect

Disconnect battery and dashboard. Inspect both sides under magnification, especially U1, D1, 4R7, nearby capacitors, connector pins, vias and any location touched by the probe. Look for cracked ceramic capacitors, lifted pads, discolouration, solder splashes and corrosion.

## Step 2 — clean water damage

Use high-purity isopropyl alcohol and a soft ESD-safe brush. Replace badly plated connector terminals rather than merely polishing them. Dry fully before testing.

## Step 3 — identify the U1 output side

With power off, use continuity to determine:

- One side of 4R7 connected to U1/D1: switching side.
- Other side connected to output capacitors/logic: output side.

Mark the output side in a photo.

## Step 4 — unpowered checks

1. 15 V to GND resistance.
2. U1 output to GND resistance in both probe polarities.
3. D1 diode mode both directions.
4. 4R7 continuity.
5. Input connector continuity to U1.
6. Output rail continuity to CH592F/GN16401 supply pins where known.
7. Check for an opened trace or via caused by the short.

The reported 170 kΩ input resistance suggests no hard 15 V input short, but does not prove U1 is healthy.

## Step 5 — current-limited 15 V test

Preferred: isolated bench supply at 15 V with a conservative current limit.

1. Disconnect the dashboard from the scooter.
2. Verify polarity twice.
3. Start with low current limit.
4. Apply power.
5. Observe current and heating.
6. Measure U1 input.
7. Measure output side of 4R7.
8. Measure GN16401 VDD and CH592F supply.

Stop immediately if current jumps, a component heats quickly or voltage collapses.

## Step 6 — interpret results

### U1 has no input

Trace connector, fuse-like parts, diode/protection path and damaged vias.

### U1 has input but no output

Check output short, D1, enable, feedback divider and U1.

### Correct output but no MCU activity

Check reset, 32 MHz crystal, corrosion and MCU damage.

### MCU active but LCD blank

Check GN16401 supply and serial control signals.

### Logic restored but still only on while held

Capture SW and UART during press/release. Find whether the keep-alive failure occurs before or after UART stops. Inspect any Q2/Q3/Q4 transistor network associated with enable/hold, but identify connections before assigning function.

## Likely post-short failure candidates

1. U1 buck regulator.
2. D1 Schottky diode.
3. Cracked/shorted output capacitor.
4. Burned track or via.
5. Downstream CH592F/GN16401 if overvoltage reached the logic rail.

This is a diagnostic priority list, not a confirmed failure list.
