# BLDC Motor and Hall Sensors

The front hub is a brushless DC motor containing stator coils, permanent magnets and three Hall sensors.

## Three phases

The controller creates a rotating magnetic field by switching current among three phases. A battery connected directly to two phases creates only a static field, potentially locking the rotor and drawing destructive current.

## Hall sensors

Three Hall outputs encode rotor sector. The controller uses them for startup, commutation, direction and speed. Typical valid patterns cycle through six states; `000` and `111` are normally invalid during rotation.

## Motor tests with controller disconnected

### Phase resistance

Measure yellow-green, green-blue and blue-yellow. Values should be very low and approximately equal. Subtract probe resistance or use a four-wire meter because ordinary meters are inaccurate below one ohm.

### Phase-to-case insulation

Each phase to axle/case should be open or extremely high resistance.

### Generator test

Set the meter to AC voltage, spin the wheel and compare all three phase pairs. Each should generate a similar small AC voltage that rises with speed.

### Phase-short drag test

With the motor disconnected, short two phase wires together and rotate the wheel. It should become noticeably harder to turn. Repeat for all pairs.

### Hall test

After verifying wiring, power the Hall board from a current-limited regulated supply, typically 5 V. Each yellow/green/blue signal should toggle between low and high while rotating the wheel slowly.
