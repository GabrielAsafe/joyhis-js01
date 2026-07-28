# Replacing the Original Controller and Display

This is the most practical route if the dashboard cannot be repaired and no confirmed AQC03L-compatible V4/V2 replacement is available.

## Parts normally reusable

- 36/37 V battery and BMS.
- Front BLDC hub motor.
- Hall sensors.
- Mechanical chassis and brake hardware.

## Required replacement parts

- Universal 36 V BLDC controller.
- Around 350 W rating.
- Current limit compatible with the original 15 A class and battery BMS.
- Hall-sensor support.
- Analog Hall throttle.
- Ignition/key switch or matching display.

Optional: brake cut-off, light output, matching speed display and self-learning wires.

## Selection checklist

1. 36 V nominal system.
2. Correct maximum battery voltage tolerance.
3. Current limit not excessive for battery/BMS/motor.
4. Hall support.
5. Three-phase connector capacity.
6. Analog throttle support.
7. Brake-input polarity.
8. Wheel-size/speed configuration.
9. Physical dimensions and cooling.
10. Waterproof connectors.

## Wiring concept

```text
Battery -> universal controller -> three motor phases
                          |------> five Hall wires
                          |------> analog throttle
                          |------> brake cutoff / lights / display as supported
```

## First power-up

1. Raise the front wheel.
2. Verify battery polarity and add appropriate fuse/current limiting where practical.
3. Connect phases and Halls.
4. Connect throttle with correct +5 V/GND/signal mapping.
5. Power on with throttle at zero.
6. Apply minimal throttle.
7. Stop if the motor chatters, draws excessive current or heats.
8. Confirm direction and use self-learning if provided.
9. Test brakes before riding.

## Phase/Hall mismatch

Colour-to-colour is only a starting point. Wrong combinations can cause rough running and high current. Never continue a chattering test under load.

## Functions that may be lost

- Original Bluetooth/app.
- Original LCD and error codes.
- Original speed modes.
- Original lighting logic.
- Electronic lock.
- Original brake/regeneration behaviour.

A replacement can also increase speed/current, so configure it conservatively and follow local law.
