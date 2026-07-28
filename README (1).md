# Joyhis JS01 / AOVOPRO / Vicont Reverse Engineering

Technical repair and reverse-engineering notes for a Joyhis JS01 electric scooter using a Vicont AQC03L controller and an AOVOPRO-family dashboard.

> This is an independent work-in-progress, not an official service manual. Every statement is marked implicitly by context as **confirmed**, **reported**, **inferred**, or **unresolved**. Do not treat hypotheses as manufacturer specifications.

## Safety

A 36/37 V lithium battery can deliver enough current to destroy probes, tracks and wiring or cause fire. Raise the driven wheel, disconnect the charger, use insulated probes, remove jewellery and never use current mode directly across a voltage source. Do not bypass the battery BMS.

## Confirmed hardware

| Item | Identification |
|---|---|
| Scooter | Joyhis JS01 |
| Battery label | 37 V nominal, 5.2 Ah |
| Vehicle label | 290 W rated, approximately 350 W maximum |
| Controller | Vicont AQC03L |
| Controller rating | DC 36 V, 350 W, 15 A current limit, 30 V undervoltage |
| Motor | Front-wheel BLDC hub motor with Hall sensors |
| Dashboard family | AOVOPRO-style dashboard |
| Closest replacement comparison | V4 was visually closest |
| Earlier working identification | “AOVOPRO Display V2”; not manufacturer-confirmed |
| Main MCU | CH592F |
| Display driver | GN16401 / GN1640 family |
| LED driver | OC5219 |
| Suspected logic regulator | U1, marking resembling `GB13L` or `GBI3L` |

## Main findings

The dashboard connector was mapped as:

```text
Red     +15 V
Black   GND
Yellow  SW
Blue    TX
Green   RX
```

The motor has three thick phase wires and five thin Hall-sensor wires. No ordinary three-wire analog throttle input was identified on the handlebar harness. The original controller therefore appears to rely on UART communication from the dashboard.

The original fault was: the scooter worked only while the power button was held. LCD, lights, throttle and motor operation were available during the hold. Releasing the button switched everything off. After a later accidental probe short near a capacitor, the dashboard became completely dead.

## Documentation map

- [System overview](docs/system-overview.md)
- [Complete fault timeline](docs/fault-history.md)
- [Display variants and V2/V4 discussion](docs/display-variants.md)
- [Dashboard PCB analysis](docs/display-board.md)
- [Vicont AQC03L controller](docs/controller-aqc03l.md)
- [Inferred power tree](docs/architecture/power-tree.md)
- [BLDC motor and Hall system](docs/architecture/bldc-system.md)
- [PCB component reference](docs/component-reference.md)
- [Multimeter tutorial](docs/multimeter-guide.md)
- [Confirmed measurements](docs/measurements/confirmed-values.md)
- [Raw measurement notes](docs/measurements/raw-log.md)
- [Original display repair workflow](docs/repair/original-display.md)
- [Water-damage procedure](docs/repair/water-damage.md)
- [Controller replacement](docs/replacement/controller-replacement.md)
- [UART emulation](docs/replacement/uart-emulation.md)
- [Open questions](docs/open-questions.md)

## Supplied PDF

Store the supplied GN16401/GN1640-family PDF as:

```text
datasheets/DOC043011339.pdf
```

It is referenced throughout this repository.
