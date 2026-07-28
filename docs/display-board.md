# Dashboard PCB Detailed Analysis

## Functional regions

### Digital/display region

Observed:

- U2: CH592F Bluetooth-capable MCU.
- GN16401 display driver.
- 32 MHz crystal.
- PCB antenna.
- LCD/LED connections.

Probable responsibilities:

- Button logic.
- UART protocol.
- Mode and throttle processing.
- Bluetooth/app communication.
- LCD command generation.

### LED power region

Observed:

- U4: OC5219.
- Inductor `470`.
- Schottky diode `SE`.
- Current-sense resistor `R390`.

The arrangement is consistent with a constant-current buck converter for LEDs/backlighting. `R390` commonly denotes approximately 0.390 Ω, appropriate for current sensing.

### Logic power region

Observed:

- U1, marking resembling `GB13L`/`GBI3L`.
- Inductor `4R7`.
- D1 marked `A7`.
- Nearby input/output capacitors and resistors.

Probable topology:

```text
15 V input -> U1 switch -> 4R7 inductor -> output capacitor -> 3.3/5 V logic
                   |
                  D1 freewheel/catch path
```

Exact output voltage and U1 identity remain unresolved.

## CH592F

Likely main processor functions:

- Read the button and other controls.
- Exchange UART frames with the AQC03L.
- Drive GN16401 data/clock/control signals.
- Manage Bluetooth.
- Store configuration.

Useful tests are supply voltage, reset state, 32 MHz oscillation and UART activity. Resistance measurements across MCU pins cannot prove MCU health.

## GN16401 / GN1640 family

Use `datasheets/DOC043011339.pdf` as the repository reference. During the investigation, pin 17 was identified as VDD and pin 6 as GND. The part is an LCD/LED driver supplied from a low-voltage rail, not the controller's power latch.

Diagnostic sequence:

1. Confirm VDD.
2. Confirm GND continuity.
3. Check data/clock activity with a scope or logic analyser.
4. Separate a blank LCD fault from a completely unpowered board.

## OC5219 section

U4 was initially suspected to be the logic regulator. Reading its marking corrected that hypothesis. Its surrounding inductor, Schottky diode and low-value shunt identify it much more plausibly as an LED current regulator.

## U1 section

U1 is the leading suspect for the logic supply because its surrounding topology matches a buck converter. If it receives 15 V but produces no stable output after the accidental short, check D1, output short, enable/feedback network and U1 itself.

## Connector pinout

| Wire | Signal | Role |
|---|---|---|
| Red | +15 V | Controller supply to display |
| Black | GND | Common reference |
| Yellow | SW | Button/wake signal |
| Blue | TX | Serial line |
| Green | RX | Serial line |

TX/RX labels may be from either the local or remote perspective; verify activity before connecting a UART adapter.

## Power-button interpretation

Measured SW behaviour:

```text
released: 0 V
pressed:  15 V
```

This can wake the controller or dashboard, but the original ability to drive while held suggests the system also requires a latch or ongoing UART state after release.
