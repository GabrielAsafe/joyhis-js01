# Fault History and Investigation Timeline

## 1. Original symptom

The scooter powered only while the dashboard button was physically held. During the hold:

- LCD operated.
- Lights operated.
- Throttle operated.
- Motor drove normally.

Releasing the button immediately shut the system down. A sufficiently long hold still produced the normal long-press shutdown action.

## 2. Environmental history

The scooter had previously fallen into water. Corrosion was visible on connector pins. This made ionic leakage, damaged vias, connector resistance and corroded high-impedance control paths credible causes.

## 3. Button verification

The physical switch was tested and considered operational. Attention moved from the button mechanism to power-hold logic, MCU startup, low-voltage regulation, UART keep-alive and corrosion.

## 4. Connector measurements

| Signal | Reported reading |
|---|---:|
| 15V | approximately 15 V continuously |
| SW, released | approximately 0 V |
| SW, pressed | approximately 15 V |
| RX | approximately 5.7 V average |
| TX | approximately 3.9 V average |

RX/TX were measured with a multimeter, so these are averages of active digital lines, not proven logic-high voltages.

## 5. Logic-rail observations

Two points associated with a “3.3” marking were not electrically connected. One later measured 0 V while another node measured about 5 V. Therefore, the silkscreen could not be treated as proof of one shared 3.3 V rail.

The upper “3.3” point measured about 1.1 kΩ to GND in-circuit.

## 6. Identification corrections

Early analysis mistakenly referred to Q1 and U3 in locations where those designators were not present. Closer photographs showed visible designators including U1, U2, U4 and Q2/Q3/Q4. These mistakes are retained here to prevent future readers from repeating them.

## 7. GN16401 conclusion

The supplied PDF showed the GN16401/GN1640-family part to be a display driver with a low-voltage VDD, including pin 17 as VDD and pin 6 as GND. It is not a 15 V power-latch controller and cannot by itself maintain scooter power.

## 8. U4 identification

U4 was photographed with marking `OC5219` and a second line `2446`. It sits with an inductor marked `470`, a Schottky diode marked `SE` and current shunt `R390`. This is consistent with a constant-current LED buck stage, not the main logic supply.

## 9. U1 hypothesis

U1 sits beside an inductor marked `4R7`, diode D1 marked `A7` and nearby capacitors. This strongly resembles a non-synchronous buck converter producing the dashboard logic rail. Its marking looked similar to `GB13L` or `GBI3L`, but the exact part remains unknown.

## 10. Switching-node measurement

One accessible side of 4R7 measured approximately 7.56 V. That can be the average of a PWM switching waveform and must not be interpreted as a regulated 7.56 V output. The output side should be identified by continuity to the output capacitor and measured relative to GND.

## 11. Accidental short and new fault

While probing a capacitor, the board stopped working completely. Possible damage paths include:

- Shorting a switch node to GND.
- Applying 15 V to a logic rail.
- Damaging U1.
- Damaging D1.
- Cracking/shorting a ceramic capacitor.
- Burning a track or via.
- Damaging downstream ICs.

## 12. Post-failure resistance readings

With the meter on 200 kΩ:

- 15 V to GND displayed approximately 170, interpreted as roughly 170 kΩ; this did not indicate a hard short.
- SW to GND decreased toward zero; this can result from capacitance, semiconductor paths or autoranging and was not diagnostic by itself.
