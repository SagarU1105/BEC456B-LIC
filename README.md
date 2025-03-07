# BEC456B-LIC
Lab component of linear integrated circuit
Differential Amplifier

Overview
Two fully matched MOSFETs with equal source resistances and matching or common inputs make up the MOS differential pair, a sort of amplifier setup. The difference between the MOSFETs' two drain source voltages (VD) will be the output voltage.

Although BJTs can also be used to make the differential pair, MOSFETs will be the main focus of this investigation. The differential amplifier, or diff-amp, is the fundamental component of any op-amp. Therefore, any further comprehension of the op-amp requires a grasp of this circuit.
Amplifier with Differentiation
The diff-amp's basic setup consists of identically matched transistors Q1 and Q2, as well as a common-mode input voltage VCM. The current passing through each transistor is half that of the current source, I, as can be seen in the figure: ID1 = ID2 = I/2.

In order to guarantee amplification, the current source is there to provide a steady, continuous current that keeps the transistors saturated and at their optimal working point. Additionally, it guarantees that the same current passes through both MOSFETs, which is essential because we require a perfect match. This circuit will be simulated later, however first, rather than using a current source, 
![image](https://github.com/user-attachments/assets/cedae2c3-5388-4ad4-8ca7-9f071e52ddd9)

Design and analyse the differential amplifier for the following specifications:

VDD = 1.8 V, P ≤ 2.2 mW, ViCM = 0.95 V, VOCM = 1.1 V, Vp = 0.4 V.

Perform DC analysis, transient analysis, frequency response, extract parameters.



This is the circuit we will have to design, and calculate the values of RSS, RD1, RD2.
![image](https://github.com/user-attachments/assets/ba5675e4-87ef-49ca-9b6c-15d6cdd35715)


Given: VDD = 3.3 V, P ≤ 3 mW, ViCM = 1.72 V, VOCM = 1.81 V, Vp = 0.7 V.

P = 2.2 mW = VDD x ISS = 3.3mW x ISS

ISS = 3 mW / 3.3 V = .909 mA - (1)

ID1 = ID2 = ISS/2 = 0.4545 mA – (2)

RD = (VDD - VOCM)/ID1 = (3.3 – 1.81) V / (0.45 x 10-3) A = 3.27 kΩ - (3)

RSS = Vp / ISS = 0.7 V / 0.909mA  = 770.077 Ω - (4)

From our analysis, we have now calculated the values –

RD1 = R D2 = 3.27 kΩ

RSS = 770.077 Ω

Components Required

DC voltage supply, AC voltage supply, N-channel MOSFETs, resistors

Parameters of MOSFET: 
![image](https://github.com/user-attachments/assets/d24ad006-7a1d-42f6-b9fd-3f0bd661848c)

Since we know the VDS, VGS values, we can calculate whether the MOSFETs are operating in saturation or not. This is crucial, because if the MOSFETs begin to operate in triode, the output gets clipped, which is not what we need.

The condition for saturation is that VDS < VOV, i.e., VDS < VGS - Vth, where Vth is the threshold voltage of the MOSFET, which is obtained from the TSMC 180 nm process technology .lib file. This can be included in the simulation, by adding the SPICE directive, .lib tsmc018.lib.

We can calculate if the MOSFET is operating in saturation, by using the relation VGD < Vth, which is the simplification of the saturation region condition.

VGD = (1.72 – 1.81) V = -0.9 V


For the MOSFETs, we have used W = 2.4956 µm, L = 180 nm.

From this, we can see VGD is negative, while Vth is greater than zero, satisfying our condition for saturation. Therefore, we can safely say the MOSFET is in saturation, and can act as an amplifier.

While we have determined that the MOSFET is in saturation, we need to an ensure an ideal Q-point, to make sure that the waveform does not appear distorted or get clipped off.

For the diff-amp circuit, since the transistors, RD, RSS, supply voltage VDD, will be perfectly matched, any analysis on one half of the diff-amp, can be said to be equal to the analysis on the other. This is also known as the differential half circuit, and makes analysis easier.
![image](https://github.com/user-attachments/assets/738fde17-55a6-4e85-a58c-a74379588e53)

This figure is the results from our DC operating point analysis. As we can see that VD1 = VD2 = 1.81 V, which is matching with our necessary requirements. ID1 = ID2 = .45 mA, ISS = .909 mA which also matches with our requirements. , which also agrees with our analysis.

Next, we can calculate the power and verify whether or not we are within our power budget.

P = VDD. Iss = 1.8 V x .45 mA = .81 mW, which satisfies our power budget.

To perform transient analysis, we will supply an input ac sinusoidal signal, of Vpeak = 50 mV, frequency = 1 kHz, DC offset = 0.95 V. Since we know that the differential amplifier rejects common mode signals, we need to give an ac input to only one of the signals, while keeping the other ac input equal to 0. This will give us an ideal gain, while giving ac input to both MOSFETs will give us very little gain, if any gain at all.

To perform this analysis, we need to configure the voltage source V2, for the MOSFET M1, by setting a sine wave, with DC offset = 0.95 V (Q-point VGS voltage), Amplitude = 50 mV, Frequency = 1 kHz.

For transient analysis, set the stop time equal to 5 ms, and then compare the output and input voltages.
![image](https://github.com/user-attachments/assets/0319342a-7f0c-4e48-a5f9-e63b92229c8a)

From this figure, we can see that there is a 180° phase shift, which is why the output, VD1 represented by the green curve, is inverted compared to the input, VGS, which is represented by the blue curve.

Now, we can calculate the V/V gain, and use it to calculate the dB gain, and verify it with AC small signal analysis.

Av = Vout/Vin = (1.96 – 1.65) / (1.77-1.67)  = 3.1 V/V

∴ Av = 5.5 V/V

Calculating the dB gain, by using the formula, A’v = 20log10(Av), we get,

A’v = 20log(3.1) = 9.82 dB

AC Analysis

Next, we can perform AC analysis and calculate the midband gain, as well as the 3 dB bandwidth for the differential amplifier circuit.

To perform the AC analysis, once again supply ac signal to only of the differential amplifiers, keeping the other ac input equal to 0. Set AC amplitude equal to 1 V, and run the simulation.
![image](https://github.com/user-attachments/assets/6839d362-396f-452f-80d1-68e7639f72a1)
Next, we move onto another variation of the differential amplifier. The only change we will be making is using a current source instead of the RSS resistor, at the bottom of the circuit. There are quite a few advantages of this configuration, such as increasing the common mode rejection ratio, making the amplifier more immune to noise and fluctuations.

Another advantage is that the current source provides a constant current tail current, preventing variations in transistor operating points due to fluctuations in power supply, or temperature change, maintaining the stability of the circuit.

To build this circuit, we will use a current source of value ID1 + ID2 = I = 1.222 mA. We can then perform DC, AC, transient analysis, observe our readings and compare it to the circuit with RSS.

Since we have already completed our analysis and calculated RD values, we need not do it again, instead we can check if the output voltages are the same, and vary any parameters accordingly.
![image](https://github.com/user-attachments/assets/cd1dfc2d-5adc-429c-a4e0-4347da113f0f)
![image](https://github.com/user-attachments/assets/9bc05fb6-fae8-4d2b-890c-46013c74e284)
From here we can see that VD1 = VD2 = 1.1 V, Vp = 0.400116 V, ID1 = ID2 = 0.45 mA, ISS = .909 mA, which are closely matching with the values from our analysis.

From our previous analysis, we have verified that our MOSFETs are operating in saturation, and are at a Q-point which will provide us ideal amplification.

Next, we can calculate the power and verify that it falls within our required budget, i.e., 3 mW.
![image](https://github.com/user-attachments/assets/94c30f5e-3676-4ca5-8b43-bca253e3be8e)
gain for current source= 1.96-1.65/1.77-1.66=2.8=20log10(2.8)=8.94
Av=8.94

AC Analysis

For the DC supply for M1, set the AC amplitude for small signal analysis equal to 1 V, keeping the other MOSFET as ac ground. Set the type of sweep as decade, number of points per decade to 20, start frequency 0.1 Hz, end frequency as 1 THz.
![image](https://github.com/user-attachments/assets/77134e43-c78b-47c5-ad01-6c2e844d6ab3)

circuit with MOSFET as current source

![image](https://github.com/user-attachments/assets/53eb056c-783d-4faa-98e1-c696e5c43b5f)
![image](https://github.com/user-attachments/assets/86bbfd88-acdf-4cc1-8794-4710ce20a109)
From the figure, we can see that the VG for the M3 is 1.80 V, which will give us I of .909 mA, VD3 of around 0.694 V, which is not exactly the Vp we need but is close.

Transient analysis for Fig. 14, with stop time = 5 ms

We can calculate the V/V gain by dividing Vout/Vin. Also, the output voltage curve (green) appears inverted compared to the input voltage curve (blue) due to a 180° phase shift.

Av = Vout/Vin = 3.4 V/V

Converting this to dB, we get A’v = 20log10(Av) = 20log10(3.4) = 10.69dB

AC Analysis

For the DC supply for M1, set the AC amplitude for small signal analysis equal to 1 V, keeping the other MOSFET as ac ground. Set the type of sweep as decade, number of points per decade to 20, start frequency 0.1 Hz, end frequency as 1 THz.

![image](https://github.com/user-attachments/assets/42718a3e-feab-4ddb-b411-368abd591680)
As we can see, we get a midband gain of around 9.8 dB, which is close to the calculated value. We can also the 3 dB bandwidth at around 2.142 GHz. From the figure, we can see that the curve is not the standard frequency response we are used to seeing. This may be due to the effects of the NMOS behaving as a current source, which could explain why a current source is used since it provides stability, and prevents noise and fluctuation.

Inference

After performing this experiment, we learnt how the differential amplifier operates, and how to build it in LTSpice. We see how the differential amplifier rejects common mode signals, but amplifies differential mode signals, making it the ideal building block for the operational amplifier or the op-amp.

We also observed the three different configurations for the differential amplifier, i.e., with resistance RSS, current source ISS, the NMOS biased as a current source operating in saturation region.

The highest gain we observed was in the NMOS configuration, which provided a dB gain of 10.69 dB, compared to the other two configurations. However, the frequency response for this configuration seems very unstable, with constant fluctuations before the midband (possibly due to the effects of the NMOS).

The advantage of the current source configuration is that we obtained almost exact parameters that we had calculated for. It also provides a more stable current ISS, since there won’t be any fluctuations due to temperature, or any other reason. Lastly the RSS configuration also seems reliable, but with increase in temperature and tolerance errors, we may not get exact value of resistance we calculated, which may decrease or increase our current values, causing issue in power budget.

Overall, the differential amplifier is a very useful configuration, since it measures the difference between the two drain voltages, thereby preventing the effects of any noise. Another point to note is that the differential amplifiers require two exactly matched N-channel MOSFETs, making it easier to implement the circuit in LTSpice, using the 180 nm TSMC .lib technology file.















