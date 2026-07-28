# System Overview

## Electrical architecture

```text
37 V lithium battery
        |
       BMS
        |
Vicont AQC03L controller
   |          |             |
3 phases   Hall interface   Dashboard interface
   |          |             |
BLDC motor  rotor position  +15 V / GND / SW / UART
```

The controller switches battery energy into three motor phases. The Hall sensors report rotor position. The dashboard is not merely a screen: it handles the button, user interface, Bluetooth, display drive and digital communication with the controller.

## Battery and controller voltage naming

The scooter battery is labelled 37 V and the controller 36 V. These are compatible nominal descriptions for a common ten-series lithium-ion system. Nominal voltage is not maximum charged voltage.

## Likely startup sequence

1. The battery/BMS powers the controller.
2. The controller supplies approximately 15 V to the dashboard.
3. Pressing the button raises SW from approximately 0 V to 15 V.
4. Dashboard low-voltage rails start.
5. The CH592F boots and exchanges UART data with the controller.
6. A latch or firmware keep-alive maintains operation after release.
7. The dashboard transmits mode and throttle-related commands.

Steps 5–7 are inferred from the connector and behaviour; UART frames have not yet been captured.

## Why the first fault was informative

Because the motor, lights, LCD and throttle all worked while the button was held, the battery, main controller power stage, motor phases, Hall system and much of the dashboard were functional at that time. The initial fault was therefore a failure to maintain the powered state, not a completely failed motor system.
