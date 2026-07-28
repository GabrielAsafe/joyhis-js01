# Inferred Power Tree and Converter Structures

## System power tree

```text
37 V battery
   |
   BMS
   |
Vicont AQC03L
   |-- motor MOSFET bridge -> three phases
   |-- Hall regulator -> approximately 5 V
   `-- dashboard auxiliary supply -> approximately 15 V
```

## Dashboard power tree

```text
Controller +15 V
   |---------------------> OC5219 LED buck -> LEDs/backlight
   |
   `-> U1 + D1 + 4R7 buck -> probable 5 V and/or 3.3 V logic
                                  |-- CH592F
                                  |-- GN16401
                                  `-- UART/logic
```

## Buck converter structure

A non-synchronous buck normally contains:

- Switching IC.
- Catch/freewheel Schottky diode.
- Inductor.
- Input capacitor.
- Output capacitor.
- Feedback divider.

Probable mapping:

| Function | Board part |
|---|---|
| Switching IC | U1 |
| Inductor | 4R7, probably 4.7 µH |
| Catch diode | D1 marked A7 |
| Input/output filtering | Nearby C-designators |
| Feedback | Nearby resistor network, not conclusively mapped |

## Switching node versus output node

One side of the inductor is a PWM switching node; the other is filtered DC. A multimeter may display an average such as 7.56 V on the switching side. Identify the output side by continuity to the output capacitor, then measure that side relative to GND.

## Possible two-stage regulation

Two plausible structures remain:

```text
15 V -> 5 V buck -> 3.3 V LDO
```

or

```text
15 V -> 3.3 V buck
```

The separated “3.3” points and one approximately 5 V observation prevent a final conclusion.

## Power-hold mechanisms considered

- Controller-side latch after SW pulse.
- Dashboard-side transistor/MOSFET latch.
- UART keep-alive requirement.
- Corrosion shifting a high-impedance enable node.
- Broken track/via in hold path.
