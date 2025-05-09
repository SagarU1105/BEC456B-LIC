

## Theory of Current Mirror Circuits

A **current mirror** is a fundamental analog circuit configuration designed to replicate a reference current with high precision across one or more output branches, maintaining consistency despite variations in load resistance or supply voltage. In MOSFET-based implementations, PMOS transistors typically form the mirroring structure, while an NMOS transistor often serves as a current source or sink.

### Operating Principle

The current mirror operates as follows:

1. A reference current, \( I_{\text{ref}} \), flows through the input PMOS transistor (M2), establishing a specific drain-source voltage.
2. A second PMOS transistor (M3), configured with an identical gate-source voltage as M2, mirrors the reference current, resulting in an output current \( I_{\text{out}} \approx I_{\text{ref}} \).
3. An NMOS transistor (M1) functions as a current sink, providing a stable current path to ensure proper circuit operation.
4. The output current can be scaled by adjusting the width-to-length (\( W/L \)) ratio of the transistors, enabling precise control over the current mirror ratio.

### Advantages

- Accurate replication of the reference current across multiple outputs.
- Effective for biasing analog circuits, such as amplifiers.
- Minimal component count compared to resistor-based biasing methods.
- Supports multiple current outputs from a single reference source.
- Exhibits high output resistance, approximating an ideal current source.

### Key Properties

- **Stability**: Delivers a stable output current in steady-state conditions.
- **Accuracy**: Dependent on precise matching of transistor parameters (e.g., size and layout).
- **Compliance Voltage**: Requires a minimum output voltage to maintain proper operation.
- **Scalability**: Output current can be adjusted via the \( W/L \) ratio of transistors.
- **Applications**: Widely used in analog circuits, including differential amplifiers and operational amplifiers.
- **Current Gain**: Achievable by varying the sizing ratios of input and output transistors.

### Classification by MOSFET Type

#### NMOS Current Mirror
- **Transistor Type**: Utilizes N-channel MOSFETs.
- **Characteristics**: Offers faster operation due to higher electron mobility, making it suitable for high-speed applications.

---

This formalized description provides a clear and precise overview of current mirror circuits. If further details, mathematical derivations, or circuit diagrams are required, please specify.


PMOS current Mirror Circuit

Uses: P-channel MOSFET
![image](https://github.com/user-attachments/assets/c7246035-9fec-4406-a907-941262e191a4)


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

![image](https://github.com/user-attachments/assets/78ee0995-5d03-4a5e-ac0e-9dceafe0d6a1)

Explanation of Circuit Components:
- Bias Voltages (V2 and V3) = 0.95V: Establish an appropriate operating point to ensure proper transistor functionality.
- Power Supply (VDD = 1.8V): Provides necessary voltage levels for the MOSFETs.
- Output Node (Vout1): The output voltage is measured from this terminal.
- PMOS (M2, M3) and NMOS (M1): The PMOS transistors implement the current mirror, while NMOS acts as a current sink.
- Current Source (I_ref): Ensures a stable reference current for mirroring.

- DC Analysis (For Mirror Ratio 1:1)
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

mA

![image](https://github.com/user-attachments/assets/8741fd30-70bf-4748-8c33-adb97b2d52e0)

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

![image](https://github.com/user-attachments/assets/37a3fa9a-e599-4b75-97b4-72c56e9ad8d1)

![image](https://github.com/user-attachments/assets/5fa2a822-f4e1-45d2-bc1e-ec26415a8e73)

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


![image](https://github.com/user-attachments/assets/88bd975f-08e6-4fd6-99ce-c1cbe11f4592)

![image](https://github.com/user-attachments/assets/b655d2f5-04ed-432d-a1d2-a67402fdc651)Inference:
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
Ensuring the MOSFETs operate in the saturation region while matching expected results.

![image](https://github.com/user-attachments/assets/51703784-699e-4d26-9d14-bf77b3e7979f)

![image](https://github.com/user-attachments/assets/4c6e1f6c-7b2c-43d7-8777-d87269aa94e2)

![image](https://github.com/user-attachments/assets/ee2e833d-3a17-44b6-b1d1-7fef2dc93de8)

![image](https://github.com/user-attachments/assets/d6a1f61a-1a0d-4a4b-88f1-ecf3fc037ff4)
**Inference Analysis**

The amplifier demonstrates suitability for high-frequency operation, attributed to its achieved high bandwidth. The observed gain discrepancy may arise from an underestimated drain resistance or variations in transconductance. Employing a differential configuration enhances common-mode rejection and bolsters noise immunity. The frequency response indicates that the amplifier is well-suited for effective signal amplification in radio frequency (RF) and high-frequency analog circuits.


