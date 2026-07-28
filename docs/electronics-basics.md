# Electronics Basics

## Voltage
Measure in parallel.
Black probe on GND.
Red probe on test point.

## Resistance
Power OFF.
Measure across the component.
In-circuit values may differ because of parallel paths.

## Current
Move the meter lead to the current input.
Open the circuit and place the meter in series.
Never measure current by touching both probes across a voltage source.

## Diode Mode
Forward bias:
- Silicon: ~0.55-0.75V
- Schottky: ~0.15-0.40V

Reverse should be open.

## Capacitors
An increasing resistance reading is normal because the multimeter charges the capacitor.

## Inductors
Normally measure very low resistance.

## MOSFETs
Check drain-source shorts first.

## DC/DC Buck Converter
Typical blocks:
Input -> IC -> Inductor -> Output Capacitor

Observed on the display:
U1 + 4R7 + D1 appears to form the logic buck converter.

## LED Buck Driver
Observed:
OC5219 + 470 inductor + Schottky diode + R390 current shunt.

## UART
TX = transmit
RX = receive
GND common reference.
