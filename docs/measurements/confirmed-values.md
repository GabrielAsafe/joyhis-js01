# Confirmed and Reported Measurements

| Point | Condition | Reading | Meaning/limitation |
|---|---|---:|---|
| 15V-GND | Original operation | ~15 V | Dashboard supply present |
| SW-GND | Released | ~0 V | Idle |
| SW-GND | Pressed | ~15 V | Asserted |
| RX-GND | Operating | ~5.7 V average | Digital line; scope required |
| TX-GND | Operating | ~3.9 V average | Digital line; scope required |
| Upper “3.3”-GND | Unpowered resistance | ~1.1 kΩ | In-circuit network value |
| One “3.3” point | Later powered test | 0 V | Identity unresolved |
| Another node | Later powered test | ~5 V | Possible rail, unconfirmed |
| One side of 4R7 | Powered | ~7.56 V | Possibly PWM average |
| 15V-GND | After failure, 200 kΩ range | display ~170 | roughly 170 kΩ; no hard short |
| SW-GND | After failure, 200 kΩ range | decreased toward zero | capacitor/network behaviour |

Two “3.3” markings were not continuous and must not be assumed to be the same rail.
