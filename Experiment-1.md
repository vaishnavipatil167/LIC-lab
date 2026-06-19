EXPERIMENT – 1
Design and Analysis of PMOS Common Source Amplifier using LTspice
====================================================================

AIM:
To design and analyze a PMOS Common Source (CS) amplifier in 180nm 
technology using LTspice and perform DC, AC and Transient analysis 
under given power constraints.


THEORY
====================================================================

A Common Source amplifier is a single-stage MOSFET amplifier where:

• Input is applied at Gate terminal
• Output is taken from Drain terminal
• Source is connected to VDD (for PMOS configuration)

In PMOS CS amplifier:

When input voltage decreases →
VSG increases →
Drain current ID increases →
Voltage drop across RD increases →
Output voltage decreases

Hence output is inverted (180° phase shift).

------------------------------------------------------------
CONDITION FOR SATURATION REGION
------------------------------------------------------------

VSD ≥ VSG − |VT|

Where:

VSD = Source to Drain voltage

VSG = Source to Gate voltage

VT  = Threshold voltage

------------------------------------------------------------
DRAIN CURRENT EQUATION (Saturation)
------------------------------------------------------------

ID = (μp Cox / 2) (W/L) (VOV)^2

Where:

μp   = Hole mobility

Cox  = Oxide capacitance

W    = Width

L    = Length

VOV  = Overdrive voltage = (VSG − |VT|)

------------------------------------------------------------
SMALL SIGNAL GAIN
------------------------------------------------------------

Av = − gm RD

Where:
gm = 2ID / VOV

Negative sign indicates 180° phase shift.

GIVEN PARAMETERS
====================================================================

Technology = 180 nm

VDD = 1.8 V

Power Constraint P ≤ 1 mW

Load Capacitance CL = 10 pF

Channel Length L = 180 nm

Threshold Voltage VT = −0.3906 V

DESIGN CALCULATIONS
====================================================================

STEP 1: Assume Drain Current

Choose:
ID = 200 µA

STEP 2: Check Power Constraint

P = VDD × ID

  = 1.8 × 200µA
  
  = 0.36 mW

0.36 mW < 1 mW  → Condition Satisfied ✔

------------------------------------------------------------
STEP 3: Choose Output Voltage for Maximum Swing
------------------------------------------------------------

For symmetrical swing:

Vout = VDD / 2

Vout = 1.8 / 2

Vout = 0.9 V

------------------------------------------------------------
STEP 4: Calculate Drain Resistor RD
------------------------------------------------------------

Vout = VDD − ID RD

0.9 = 1.8 − (200µA × RD)

RD = 1.8 / (2 × 200µA)

RD = 4500 Ω

RD ≈ 4.5 kΩ

------------------------------------------------------------
STEP 5: Calculate Overdrive Voltage
------------------------------------------------------------

VOV = VSG − |VT|

Assume:
VSD = 0.9 V

VOV = 0.9 − 0.3906

VOV = 0.5094 V

------------------------------------------------------------
STEP 6: Calculate Transconductance
------------------------------------------------------------

gm = 2ID / VOV

gm = (2 × 200µA) / 0.5094

gm ≈ 0.000785 S

gm ≈ 0.785 mS

------------------------------------------------------------
STEP 7: Theoretical Voltage Gain
------------------------------------------------------------

Av = gm RD

Av = 0.000785 × 4500

Av ≈ 3.53

Gain in dB:

Av(dB) = 20 log10(3.53)

Av(dB) ≈ 10.96 dB

------------------------------------------------------------
STEP 8: Transistor Width Calculation
------------------------------------------------------------

Using current equation:

ID = (μp Cox / 2) (W/L) (VOV)^2

From calculation:

Initial W ≈ 2.8476 µm

From simulation adjustment:

Final Width W ≈ 4.3996 µm

This gives ID ≈ 200 µA

CIRCUIT DIAGRAM 
====================================================================
<img width="988" height="570" alt="Screenshot 2026-02-23 183056" src="https://github.com/user-attachments/assets/3c9a7e71-2ced-4dee-aa22-2ea1aab429df" />


DC ANALYSIS
====================================================================

DC operating point (.op) results:

<img width="1913" height="979" alt="Screenshot 2026-02-22 220343" src="https://github.com/user-attachments/assets/d05eec0e-f996-485b-b905-776d9080e7fb" />


Drain Current ID ≈ 200 µA

Output Voltage Vout ≈ 0.9 V

Transistor operating in Saturation Region ✔

Condition Verified:

VSD ≥ VOV

0.9 ≥ 0.5094  ✔

<img width="1919" height="1001" alt="Screenshot 2026-02-22 220602" src="https://github.com/user-attachments/assets/9a3b8354-2ce1-461e-8973-c78b255feb5a" />


TRANSIENT ANALYSIS
====================================================================

Input Signal:
SINE(0.9 10m 1k)

Measured Values:

Vin (peak-to-peak)  = 0.02012 V

Vout (peak-to-peak) = 0.05869 V

Practical Gain:

Av = Vout / Vin

Av = 0.05869 / 0.02012

Av ≈ 2.9169

Gain in dB:

Av(dB) = 20 log10(2.9169)

Av(dB) ≈ 9.29 dB

Output waveform shows 180° phase shift.

<img width="1919" height="972" alt="Screenshot 2026-02-22 220646" src="https://github.com/user-attachments/assets/1b988cf6-0775-4091-b027-d1b1cc47bf23" />


## COMPARISON TABLE: THEORETICAL vs PRACTICAL RESULTS

| Parameter       | Theoretical | Practical |
|-----------------|------------|-----------|
| Drain Current   | 200 µA     | ≈ 200 µA  |
| Output Voltage  | 0.9 V      | ≈ 0.9 V   |
| Voltage Gain    | 3.53       | 2.91      |
| Gain (dB)       | 10.96 dB   | 9.29 dB   |
| Phase Shift     | 180°       | 180°      |


AC ANALYSIS
====================================================================

AC analysis determines frequency response.

<img width="1919" height="984" alt="Screenshot 2026-02-22 221210" src="https://github.com/user-attachments/assets/7a841d95-0278-4f89-ad16-40c89d32b8ea" />


Midband Gain ≈ 10.96 dB (Theoretical)

3 dB Cutoff Frequency:
<img width="1766" height="822" alt="Screenshot 2026-02-22 221332" src="https://github.com/user-attachments/assets/8409dea6-df14-4b13-957c-ae38abfde393" />


Upper Cutoff Frequency fH ≈ 18.46 GHz

Lower Cutoff Frequency fL ≈ 0 Hz

Bandwidth:

BW = fH − fL

BW ≈ 18.46 GHz






Difference is due to:

• Channel length modulation

• Parasitic capacitances

• Model non-idealities


RESULT
====================================================================

The PMOS Common Source amplifier was successfully designed 
under power constraint P ≤ 1 mW.

DC analysis confirmed proper saturation operation.
Transient analysis verified amplification and phase inversion.
AC analysis confirmed high bandwidth performance.

The practical gain closely matches theoretical gain, 
validating the design calculations.


CONCLUSION
====================================================================

A PMOS Common Source amplifier was designed and analyzed 
in 180nm CMOS technology using LTspice.

All required conditions were satisfied:

✔ Power constraint

✔ Saturation region operation

✔ Required gain

✔ Proper biasing

The experiment successfully demonstrates voltage amplification 
with controlled power consumption and high frequency response.




