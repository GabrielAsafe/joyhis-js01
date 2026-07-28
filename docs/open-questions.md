# Open Questions and Future Work

## Exact display revision

- Is the board officially V2, V4 or another OEM revision?
- Which V4 listing is electrically compatible with Vicont AQC03L?

## U1

- Exact marking and manufacturer.
- Pinout.
- Output voltage.
- Enable and feedback pins.

## Rails

- True 3.3 V test point.
- Presence of a 5 V intermediate rail.
- Whether rails are always-on or switched.
- Whether the accidental short opened a trace/via.

## UART

- Idle/high voltage.
- Baud rate and framing.
- Startup/keep-alive packets.
- Throttle, mode, light and speed fields.

## Next measurements

1. U1 input voltage.
2. Both sides of 4R7 relative to GND.
3. U1 output resistance to GND.
4. D1 out-of-circuit diode test.
5. GN16401 VDD.
6. CH592F supply and reset.
7. Scope capture of U1 switch node.
8. UART capture from a working dashboard.
