# Display Board

## Identified ICs

- CH592F BLE MCU
- GN16401 LCD Driver
- OC5219 LED driver
- Unknown U1 (suspected buck regulator)

## Confirmed observations

- Water damage history.
- Corrosion found.
- Display originally remained ON only while holding power button.
- After accidental probe short, display stopped powering.

## Measurements

15V present.
SW:
- 0V idle
- 15V pressed

RX ≈5.7V
TX ≈3.9V

## Functional blocks

MCU -> LCD Driver

15V -> U1 Buck -> Logic Rail

15V -> OC5219 -> LCD backlight

GN16401 documentation:
See DOC043011339.pdf
