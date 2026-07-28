# Reverse Engineering Log

Chronology

1. Display only powered while button held.
2. Button confirmed working.
3. Water ingress confirmed.
4. Corrosion observed.
5. GN16401 identified from datasheet.
6. U4 identified as OC5219 LED buck driver.
7. U1 became primary suspect for logic supply.
8. Controller identified as Vicont AQC03L.
9. Handlebar wiring mapped:
   - 15V
   - GND
   - SW
   - TX
   - RX
10. Motor wiring mapped:
   - 3 phase
   - 5 Hall

Future work

- Dump UART packets.
- Identify U1.
- Reverse engineer startup protocol.
- Create ESP32 replacement display.
