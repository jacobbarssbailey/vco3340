# VCO3340
This project provides tested plans for a 6HP Eurorack-format CEM3340 [CoolAudio 3340] VCO synthesizer module. The 3340 VCO chip provides excellent .


### Inputs
- V/OCT: Exponential (1V per octave) pitch input
- Lin FM: Linear frequency modulation
- Sync: Hard sync oscillator to external signal. Requires audio-rate signal at approx. ±5V.
- Width: Set duty cycle of pulse output from 0-100% with ±2.5V signal. Normally 0V, i.e square wave] output


### Outputs
All oscillator outputs (Sine, Triangle, Sawtooth, and Pulse) range from ±5V. The pulse input width is controlled by the Width input, and by default is a 50% duty cycle, i.e. Square wave.


## BOM 

Qty | Value            | Device                  | Package             | Parts                                                |
--- | ---------------- | ----------------------- | ------------------- | ---------------------------------------------------- |
2   | 10KΩ             | Pot (Alpha 9mm)         | 6mm                 | COURSE, FINE                                         |
8   | 3.5mm Jacks      |                         | Thonkiconn          | LINFM, PULSE, SAW, SIN, SYNC, TRI, V/OCT, WIDTH      |
4   | M06              | 2.54mm header           | Pin                 | CTRL, KNOB, OUT, POWER                               |
4   | M06              | 2.54mm header           | Socket              | CTRL, KNOB, OUT, POWER                               |
1   | M08X2            | 2.54mm header           | Pin                 | EXPANSION                                            |
3   |                  | 2.54mm                  | Jumper              |                                                      |
1   | M05x2            | 2.54mm header           | Shrouded            | POWER                                                |
--- | ---------------- | ----------------------- | ------------------- | ---------------------------------------------------- |
2   | 100Ω             | Resistor                | 0805                | R1, R22                                              |
1   | 390Ω             | Resistor                | 0805                | R36                                                  |
2   | 470Ω             | Resistor                | 0805                | R9, R19                                              |
1   | 1KΩ              | Resistor                | 0805                | R32                                                  |
2   | 2.2KΩ            | Resistor                | 0805                | R34, R40                                             |
2   | 3.6KΩ            | Resistor                | 0805                | R23, R25                                             |
1   | 5.6KΩ            | Resistor                | 0805                | R2, R21                                              |
8   | 10KΩ             | Resistor                | 0805                | R5, R10, R27, R35, R38, R39, R41, R42                |
1   | 24KΩ             | Resistor                | 0805                | R20                                                  |
1   | 47KΩ             | Resistor                | 0805                | R3                                                   |
2   | 80KΩ             | Resistor                | 0805                | R28, R29                                             |
5   | 100KΩ            | Resistor                | 0805                | R4, R15, R16, R24, R30                               |
4   | 200KΩ            | Resistor                | 0805                | R14, R18, R26, R31                                   |
1   | 150KΩ            | Resistor                | 0805                | R6                                                   |
3   | 1MΩ              | Resistor                | 0805                | R7, R11, R13                                         |
1   | 1.5MΩ            | Resistor                | 0805                | R8                                                   |
--- | ---------------- | ----------------------- | ------------------- | ---------------------------------------------------- |
2   | 1.0nF            | Capacitor               | 0805                | C1, C2                                               |
1   | 1.25nF           | Capacitor (CG0)         | 0805                | C6                                                   |
2   | 10nF             | Capacitor               | 0805                | C4, C5                                               |
11  | 100nF            | Capacitor               | 0805                | C3, C10, C11, C12, C13, C14, C15, C18, C19, C21, C22 |
2   | 1µF              | Capacitor               | 0805                | C8, C9                                               |
4   | 47µF             | Capacitor (Pol)         | PANASONIC_C         | C16, C17, C20, C23                                   |
--- | ---------------- | ----------------------- | ------------------- | ---------------------------------------------------- |
1   | 10KΩ             | Trimpot                 | 2.54mm Multiturn    | SCALE                                                |
1   | 20KΩ             | Trimpot                 | 2.54mm Multiturn    | HIGHFREQ                                             |
1   | 50KΩ             | Trimpot                 | 2.54mm Multiturn    | SYMMETRY                                             |
1   | 100KΩ            | Trimpot                 | 2.54mm Multiturn    | DRIVE                                                |
--- | ---------------- | ----------------------- | ------------------- | ---------------------------------------------------- |
2   |                  | DIODE                   | SOD-123             | D4, D5                                               |
3   |                  | DIODE                   | SOD-323             | D1, D2, D3                                           |
2   | 3904             | Transistor (NPN)        | SOT23               | Q1, Q2                                               |
1   |                  | LM79L05A                | SOT89               | U1                                                   |
1   |                  | MC78L05A                | SOT89               | U2                                                   |
1   | TL071            | OPAMP-SINGLE            | SO08                | IC1                                                  |
1   |                  | V3340/CEM3340           | SO16                | IC2                                                  |
1   |                  | LM397                   | SOT23-5             | IC3                                                  |
2   | TL072            | OPAMP-DUAL              | SO08                | IC4, IC5                                             |
--- | ---------------- | ----------------------- | ------------------- | ---------------------------------------------------- |


## Notes on assembly:
1. The rear expansion header is not optional; the V/Oct, Pulse Width, and Soft Sync inputs *must* be connected to ground for proper operation
1. Non-shrounded headers may be used for the Power connector, but this makes it easier to invert the cable polarity, with potentially unpleasant results.


## First time setup
The four trim potentiometers must be set up before use. The following procedure is recommended:
1. Confirm that the V/Oct, Pulse Width, and Soft Sync inputs on the expansion header are connected to the neighboring ground pin (with jumpers)
1. Turn HIGHFREQ all the way down. The middle pin should be shorted to ground.
1. Adjust SCALE until V/Oct input tracks at 1V per octave from 40-60Hz to ≅2Khz. This step is the most difficult, but its critical for tuning. If available, compare against a reference VCO with good tracking. Alternative methods include measuring the pulse output with a frequency counter, or measuring with an external tuner.
1. Adjust HIGHFREQ up until higher frequencies track equally well.
1. Measure the SINE output. Adjust DRIVE and SYMMETRY until the output sounds like a Sine Wave. Using an Oscilloscope may make this easiest, but its not critical and your ears are an equally good reference.

## Expansion header

While the module is an excellent standalone module, the rear expansion header may be used to add additional controls or further manipulate outputs.

It can provide power rails to a sister module, but the ±5V rails should be limited to <50mA.

The external V/Oct pin duplicates the front-panel input. The Width input sets the default pulse width. The Soft Sync input is ready to use as is, and expects ±5V audio rate signals as input.

All output waveforms are provided for additional waveshaping.
