# BEC456B-LIC
Lab component of linear integrated circuit
Experiment 3: Current Mirror Circuit
Theory
Function of a Current Mirror Circuit
A current mirror is an essential analog circuit block primarily used for precise current replication. The circuit ensures that the output current remains proportional to a reference current despite variations in voltage conditions or load resistance. In MOSFET-based implementations, PMOS transistors form the current mirror, while an NMOS transistor typically acts as a current source or sink.

Working Principle
- The reference current (I_ref) flows through the input PMOS transistor (M2), establishing a corresponding voltage across its drain-source terminals.
- The second PMOS transistor (M3) mirrors this current due to its identical gate-source voltage, thereby ensuring that I_out ≈ I_ref.
- The NMOS transistor (M1) serves as a current sink, providing a stable current path to maintain circuit operation.
- By adjusting the width-to-length (W/L) ratio of the transistors, the current mirror ratio can be modified to control the output current precisely.
Advantages of Current Mirrors
Provides accurate copying of a reference current to one or more output branches.
Useful for biasing analog circuits like amplifiers.
Requires fewer components compared to resistor-based biasing.
Allows multiple current outputs from a single reference source.
Offers high output resistance, acting like an ideal current source.
Properties of Current Mirrors
Maintains stable output current once steady-state is reached.
Accuracy depends on how well the transistors are matched in terms of size and layout.
Requires a minimum voltage (compliance voltage) at the output to function correctly.
Output current can be scaled by adjusting the W/L ratio of the transistors.
Commonly used in many analog circuit blocks like differential amplifiers and op-amps.
Can provide current gain when using different sizing ratios for input and output transistors.
Classification based on type of moseft used in current mirror circits
NMOS Currnet Mirror Circuir

Uses: N-channel MOSFET

Faster operation due to high electron mobility. image

PMOS current Mirror Circuit

Uses: P-channel MOSFET
image

Significance in Amplifier Circuits
In amplifier design, current mirrors are widely employed as active loads to improve gain and stability. Unlike resistive loads, current mirrors offer higher output resistance, leading to greater voltage gain and better linearity.

Part A: Design and Analysis of Current Mirror as Active Load in an Amplifier Circuit
Aim:
To design and analyze a current mirror circuit functioning as an active load in an amplifier circuit.

Given Specifications:

Power Supply (VDD) = 1.8V
Power Consumption (P) ≤ 1mW
Gain (Av) > -10V/V
Analysis to be Performed:
DC Analysis
Transient Analysis
AC Analysis
Extraction of required parameters
Components Required:
NMOS and PMOS Transistors
Resistors
Current Source
Voltage Supply
Connecting Wires
Circuit Diagram
Screenshot 2025-04-03 234826

Explanation of Circuit Components:
- Bias Voltages (V2 and V3) = 0.95V: Establish an appropriate operating point to ensure proper transistor functionality.
- Power Supply (VDD = 1.8V): Provides necessary voltage levels for the MOSFETs.
- Output Node (Vout1): The output voltage is measured from this terminal.
- PMOS (M2, M3) and NMOS (M1): The PMOS transistors implement the current mirror, while NMOS acts as a current sink.
- Current Source (I_ref): Ensures a stable reference current for mirroring.
DC Analysis (For Mirror Ratio 1:1)
Calculation of Reference Current:
I
t
=
P
V
D
D
=
1
m
W
1.8
V
=
0.555
m
A
I
r
e
f
=
I
t
2
=
0.2778
m
A
Screenshot 2025-04-03 234851

For W/L values:

M1: 3.3um / 180nm
M2: 3.3um / 180nm
M3: 3.3um / 180nm
Vin = 0.816V
Analysis by Varying L while Maintaining the Ratio
| L (nm) | W (um) | Id (M1) | Id (M2) | Id (M3) |
|--------|--------|----------------|----------------|----------------|
| 180    | 3.3    | 0.0002778 A    | 0.0002773 A    | 0.0002773 A    |
| 500    | 9.165  | 0.0002778 A    | 0.0002848 A    | 0.0002848 A    |
| 1000   | 18.33  | 0.0002778 A    | 0.0002803 A    | 0.0002803 A    |
Transient Analysis
Obtained gain = 10.3737V/V
Screenshot 2025-04-03 235357

AC Analysis and Frequency Response
Expected gain = 20 dB
Obtained gain = 22.860 dB

Screenshot 2025-04-03 235849

DC Analysis (For Mirror Ratio 1:2)
I
r
e
f
=
I
t
3
=
0.185
m
A
W/L values:

M1: 2.9um / 180nm
M2: 5.8um / 180nm
M3: 5.8um / 180nm
Transient Analysis and AC Response
Obtained gain: 12.1326V/V

Obtained gain (dB): 24.306 dB

Screenshot 2025-04-04 002616 Screenshot 2025-04-04 002719

Inference:
The current mirror accurately reproduces the reference current with minimal deviations.
Altering the W/L ratio proportionally maintains a nearly constant drain current, demonstrating the robustness of the mirror circuit.
Gain measurements slightly exceed theoretical predictions, likely due to parasitic effects or transistor mismatches.
Increasing the mirror ratio improves gain but reduces bandwidth.
Results align well with theoretical expectations, verifying the circuit's reliability.
Part B: Differential Amplifier Design
Aim:
To design and analyze a differential amplifier using the same design specifications as in Part A.

1. Designing the Circuit
The circuit consists of six MOSFETs with different (W/L) ratios, and is to be ensured that all transistors remain in the saturation region during the analysis. The given (W/L) ratios for each transistor are:

M1: 10um / 180nm
M2: 10um / 180nm
M3: 100μm / 180nm
M4: 50μm / 180nm
M5: 105.12μm / 180nm
M6: 105.12μm / 180nm
DC Analysis and Biasing
Ensuring the MOSFETs operate in the saturation region while matching expected results. Screenshot 2025-04-04 004350

Screenshot 2025-04-04 004456

Transient Analysis:
image

AC Analysis and Frequency Response:
image

Gain=34.12db
3db Bandwidth=389.79Mhz

Inference:
The amplifier will work on high operating frequency due to obtained high bandwidth
The gain discrepancy may stem from underestimated drain resistance or deviations in transconductance.
The differential configuration provides excellent common-mode rejection and improved noise immunity.
The obtained frequency response suggests that the amplifier is effective for signal amplification in RF and high-frequency analog circuits.
