# Display Variants: V2, V4 and Compatibility

AOVOPRO-family dashboards are sold under inconsistent V1/V2/V3/V4 names. During this investigation the board was initially called **AOVOPRO Display V2**, while the user later reported that **V4 was the closest visual match** among replacement boards.

Recommended wording for public documentation:

> AOVOPRO-family dashboard PCB. Earlier tentative identification: V2. Closest visually compared replacement: V4. Exact revision and electrical compatibility remain unconfirmed.

## Why appearance is insufficient

Boards can share housing, LCD, button position and connector shell while using different:

- Connector pin order.
- Supply voltage.
- UART baud rate.
- Packet format/checksum.
- Controller firmware.
- Bluetooth MCU.
- Throttle encoding.

Before connecting a replacement, verify +15 V, GND, SW, TX and RX pin positions with a meter. A wrong +15 V/GND mapping can destroy the replacement immediately.

## Known investigated-board hardware

- CH592F BLE MCU.
- GN16401/GN1640-family display driver.
- OC5219 LED driver.
- Unknown U1 buck regulator.
- 32 MHz crystal.
- PCB antenna.
