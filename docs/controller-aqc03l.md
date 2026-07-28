# Vicont AQC03L Controller

## Label

```text
Vicont Brushless Motor Controller
Voltage: DC36V
Rated Power: 350W
Undervoltage: 30V
Current Limiting: 15A
Model: AQC03L
```

## Motor wiring

Three thick phase wires:

- Yellow.
- Green.
- Blue.

Five thin Hall wires:

- Red: probable +5 V.
- Black: probable GND.
- Yellow/green/blue: probable Hall A/B/C.

These colour conventions are common but must be verified before connecting a replacement controller.

## Dashboard wiring

```text
Red     +15 V
Black   GND
Yellow  SW
Blue    TX
Green   RX
```

No obvious analog-throttle signal was present in this harness. A common analog Hall throttle would normally expose +5 V, GND and an approximately 0.8–4.2 V signal. The AQC03L instead appears to receive throttle/mode commands digitally.

## Why bridging wires is insufficient

Applying 15 V to SW may wake the controller, but it cannot create the UART messages expected for throttle and mode control. Randomly bridging RX/TX risks damaging the communication interface.

## Controller screening tests

With battery and motor disconnected, compare diode/resistance readings from each phase to battery positive and negative. The three phases should be broadly similar. A near-zero phase-to-rail reading in both directions can indicate a shorted MOSFET.

With the controller safely powered and awake, Hall red-to-black should be in the 5 V class. Each Hall signal should toggle while slowly rotating the wheel.

## Dashboard supply test

Red-to-black on the dashboard harness previously measured around 15 V. If it remains present after the display failure, part of the AQC03L auxiliary supply is still alive.
