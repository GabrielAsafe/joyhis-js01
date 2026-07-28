# Replacing the Dashboard by UART Emulation

A more advanced option is retaining the AQC03L and emulating the dashboard with an ESP32/Arduino-class device.

## Unknown protocol properties

- Logic voltage.
- Baud rate.
- Packet length.
- Checksums.
- Startup/keep-alive packets.
- Throttle encoding.
- Mode/light commands.
- TX/RX naming perspective.

## Capture workflow

A working original or compatible display is required.

1. Connect logic-analyser GND only after confirming common ground.
2. Measure idle voltage and analyser tolerance.
3. Capture both directions without transmitting.
4. Record power-on, short press, long press, zero throttle, multiple throttle positions, mode changes, lights and wheel movement.
5. Export raw captures.
6. Test common baud rates.
7. Identify repeating frames and changing bytes.
8. Determine checksum and keep-alive timing.

Measured RX/TX averages of about 5.7 V and 3.9 V are not safe evidence for direct 3.3 V MCU connection. Use proper level shifting/protection.

## Safe emulator requirements

- Throttle-zero startup interlock.
- Packet timeout.
- Watchdog.
- Brake override.
- Rate limiting.
- Invalid-frame rejection.

SW alone is unlikely to produce movement because a static wire cannot replace the digital throttle protocol.
