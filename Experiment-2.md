# Experiment – 2  
## A.Design of CS Amplifier using 180nm Technology with PMOS Active Load  

---

## Aim  

To design a Common Source (CS) Amplifier using 180nm CMOS technology with PMOS active load and verify the performance using DC, Transient and AC analysis.

---

##  Theory

### 1. Common Source (CS) Amplifier

A **Common Source (CS) amplifier** is a basic MOSFET amplifier configuration in which:

- The **input** is applied at the **Gate**
- The **output** is taken from the **Drain**
- The **Source** terminal is common (usually connected to ground)

### * Characteristics:

- High voltage gain  
- 180° phase shift between input and output  
- Moderate input impedance  
- High output impedance  

The CS amplifier is one of the most fundamental and widely used configurations in analog circuit design.

---

###  2. Why PMOS Active Load?

Instead of using a physical resistor at the drain terminal, a **PMOS transistor** is used as an **active load**.

### * Advantages:

- Saves chip area (very important in 180nm IC design)
- Provides high output resistance
- Gives higher voltage gain
- Better compatibility with CMOS fabrication process
- Improves integration in VLSI design

Using an active load significantly enhances amplifier performance compared to a simple resistive load.

---

## Given Specifications  

VDD = 1.5 V  
P ≤ 0.5 mW  
CL = 1 pF  
L = 180 nm  

Technology parameters are taken from **tsmc018.lib**

From library:

VTHn = 0.366 V  
|VTHp| ≈ 0.39 V  
tox = 4.1 × 10⁻⁹ m  
εox = 3.9 × 8.854 × 10⁻¹² F/m  
μn = 115.689 cm²/V·s  
μp = 273.80 cm²/V·s  

---

# Step-1: Calculation of NMOS Parameters

### 1) Assume Overdrive Voltage

Vov = 0.25 V  

We know,

Vov = VGS − VTH  

Therefore,

VGS = Vov + VTH  
VGS = 0.25 + 0.366  
VGS = 0.61 V  

---

### 2) Calculation of Vout (Bias Point)

For maximum symmetrical swing,

Vout ≈ (VDD / 2) + VRS  

= (1.5 / 2) + 0.2  
= 0.75 + 0.2  
= 0.95 V  

---

### 3) Drain Current from Power Specification

P = V × I  

0.5 mW = 1.5 × ID  

ID = 0.5 × 10⁻³ / 1.5  

ID = 0.334 mA  

---

### 4) Source Resistor Calculation

VRS = ID × RS  

0.2 = 0.334 mA × RS  

RS = 0.2 / (0.334 × 10⁻³)  

RS = 598.8 Ω  

---

### 5) Gate Voltage of NMOS

VG = VGS + VRS  

VG = 0.61 + 0.2  

VG = 0.81 V  

---

### 6) Saturation Condition Check

Condition:

VDS ≥ Vov  

VDS ≈ VDD/2  

0.75 ≥ 0.25 ✔  

Hence NMOS operates in saturation.

---

# Step-2: PMOS Calculations

For PMOS,

Vov = VSG − |VTHp|  

0.25 = VSG − 0.39  

VSG = 0.64 V  

Now,

VSG = VS − VG  

0.64 = VDD − VG  

VG = 1.5 − 0.64  

VG = 0.86 V  

---

# Step-3: Width Calculation

Drain current equation:

ID = (1/2) μ Cox (W/L) (Vov)²  

Where,

Cox = εox / tox  

Cox = (3.9 × 8.854 × 10⁻¹²) / (4.1 × 10⁻⁹)

Using this equation:

### NMOS

Wn ≈ 8.364 μm  

After tuning in DC:

Wn = 4.832 × 10⁻⁵ m  

---

### PMOS

Wp ≈ 1.977 × 10⁻⁵ m  

After tuning in DC:

Wp = 6.286 × 10⁻⁵ m  

---
# CIRCUIT DIAGRAM :
<img width="998" height="807" alt="image" src="https://github.com/user-attachments/assets/df606019-12c9-45c5-84d8-007dff441fd2" />


# Step-4: DC (Operating Point) Analysis
 # Before tuning :
<img width="1918" height="855" alt="image" src="https://github.com/user-attachments/assets/25836271-72bf-42e8-96b9-2bce30452a7c" />

# After width tuning:
<img width="1897" height="833" alt="Screenshot 2026-02-25 143555" src="https://github.com/user-attachments/assets/4ac58195-649d-4f9e-b020-9cc0a24ac927" />


PMOS:
W = 6.286 × 10⁻⁵ m  
ID = −0.335 mA  

NMOS:
W = 4.832 × 10⁻⁵ m  
ID = 0.335 mA  

Vout = 0.94 V  

✔ Bias point achieved near mid supply.

---

# Step-5: Transient Analysis

Stop time = 5 ms  
  # INPUT WAVEFORM 
  <img width="1919" height="880" alt="Screenshot 2026-02-25 143810" src="https://github.com/user-attachments/assets/4139c739-2446-432a-8100-b947cba222d6" />
 
  # OUTPUT WAVEFORM 
  <img width="1919" height="877" alt="Screenshot 2026-02-25 143905" src="https://github.com/user-attachments/assets/cee36ebe-948c-4395-982e-3f5622de3943" />

Measured gain from waveform:

Gain = ΔVout / ΔVin  

= (1.0873 − 0.84293) / (0.81999 − 0.800)

Gain ≈ 9.723  

Gain in dB:

Av(dB) = 20 log (9.723)

Av ≈ 19.75 dB  

---
Taking Vin(p-p) = 20 × 10⁻³ v

Gain = ΔVout / Vin (p-p)

=  (1.0873 − 0.84293) /  20 × 10⁻³ 

Gain ≈ 12.2185

Av(dB) = 20 log (12.2185)

Av ≈ 21.75 dB  




# Step-6: Theoretical Gain Calculation

Small signal gain:

Av = − gm (ro1 || ro2) / (1 + gm RS)

---

### 1) Transconductance

gm = 2ID / Vov  

gm = 2 × (0.334 × 10⁻³) / 0.25  

gm = 2.672 × 10⁻³ S  

---

### 2) Output Resistance

ro = 1 / (λ ID)

Given:

λ = 0.1 V⁻¹  

ro = 1 / (0.1 × 0.334 × 10⁻³)

ro = 29.94 kΩ  

ro1 || ro2 = 14.97 kΩ  

---

### 3) Theoretical Gain

Av = (2.672 × 10⁻³ × 14.97 × 10³)  / (1 + 2.672 × 10⁻³ × 598.8)

Av = 15.38  

Av(dB) = 20 log(15.38)

Av = 23.74 dB  

---

# Step-7: AC Analysis
<img width="1919" height="858" alt="Screenshot 2026-02-25 144120" src="https://github.com/user-attachments/assets/df8db847-cfac-40a3-a41f-812f8bd6072b" />



gain = 19.75 - 3dB 

gain = 16.75 dB

BW = fH − fL

fL = 0 

BW = fH = 219.542 MHz 


---

# Final Results

| Parameter | Theoretical | Practical |
|-----------|------------|-----------|
| ID | 0.334 mA | 0.335 mA |
| Vout | 0.95 V | 0.94 V |
| Gain | 15.38 | 9.723 |
| Gain (dB) | 23.74 dB | 19.75 dB |

---
#  Inference

The PMOS Common Source amplifier was successfully designed and simulated.

- The transistor operates in saturation region.
- Gain obtained practically is slightly less than theoretical due to:
  - Channel length modulation
  - Parasitic capacitances
  - Non-ideal effects
- Phase shift of 180° confirms inverting amplifier behavior.
- AC and transient analysis results match closely with theoretical values.

Hence, the experiment is verified successfully
---


 
# B.Design of 3-Transistor Common Source Amplifier Using 180nm Technology  

---

## Aim  

To design and analyze a **Common Source amplifier using PMOS active load and NMOS current source bias** in 180nm technology and verify the performance using:

- DC Operating Point Analysis  
- Transient Analysis  
- AC Analysis  

---

## Theory  

### 1. Circuit Description  

This circuit consists of three MOSFETs:

- **M1** → NMOS (Common Source transistor)  
- **M2** → PMOS (Active load)  
- **M3** → NMOS (Current source transistor)  

The output is taken at the drain of M1.

This topology is called:

> **Current Source Loaded Common Source Amplifier**

It provides higher gain and better bias stability compared to resistor-loaded CS amplifier.

---

### 2. Why Active Load and Current Source?

Using PMOS as active load:

- Saves chip area  
- Provides high output resistance  
- Improves gain  

Using NMOS current source:

- Maintains constant drain current  
- Improves bias stability  
- Enhances small signal gain  

---

## Given Specifications  

VDD = 1.5 V  
P ≤ 0.5 mW  
L = 180 nm  
Vov = 0.25 V  

Technology Parameters:

VTHn = 0.366 V  
|VTHp| = 0.39 V  

μn = 273.80 × 10⁻⁴  
μp = 115.689 × 10⁻⁴  

tox = 4.1 × 10⁻⁹ m  

εox = 3.9 × 8.854 × 10⁻¹²  

---

# Step-1: Oxide Capacitance Calculation  

Cox = εox / tox  

Cox = (3.9 × 8.854 × 10⁻¹²) / (4.1 × 10⁻⁹)  

Cox = 8.422 × 10⁻³ F/m²  

---

# Step-2: Drain Current from Power Constraint  

P = VDD × ID  

0.5 × 10⁻³ = 1.5 × ID  

ID = 0.334 mA  

---

# Step-3: M1 (NMOS) Calculations  

Assume:

Vov = 0.25 V  

Vov = VGS − VTH  

VGS1 = 0.25 + 0.366  

VGS1 = 0.616 V  

---

### Output Bias Point  

For symmetrical swing:

Vout = VDD / 2  

Vout = 1.5 / 2  

Vout = 0.75 V  

---

### Assume Source Voltage  

Vs = 0.3 V  

VGS1 = VG1 − Vs  

VG1 = VGS1 + Vs  

VG1 = 0.616 + 0.3  

VG1 = 0.916 V  

---

### Saturation Condition Check  

VDS1 = Vout − Vs  

VDS1 = 0.75 − 0.3  

VDS1 = 0.45 V  

Condition:

VDS ≥ Vov  

0.45 ≥ 0.25 ✔  

M1 operates in saturation.

---

# Step-4: M3 (NMOS Current Source)  

For M3:

VGS3 = Vov + VTH  

VGS3 = 0.25 + 0.366  

VGS3 = 0.616 V  

Since source of M3 is grounded:

VG3 = 0.616 V  

---

# Step-5: Width Calculation  

Drain current equation:

ID = (1/2) μ Cox (W/L) (Vov)²  

---

### NMOS (M1 & M3)

ID = 1/2 × 273.80×10⁻⁴ ×  (3.9 × 8.854 × 10⁻¹²) / (4.1 × 10⁻⁹) × (W/180×10⁻⁹) × (0.25)²  

Solving:

Wn ≈ 8.34 µm  

After DC tuning:

Wn ≈ 25.77µm  

---

### PMOS (M2)

ID = 1/2 × 115.689×10⁻⁴ × (3.9 × 8.854 × 10⁻¹²) / (4.1 × 10⁻⁹) × (W/180×10⁻⁹)  × (0.25)²  

Wp ≈ 19.77 µm  

After DC tuning:

Wp ≈ 59.90 µm  

---
# Circuit Diagram:
![WhatsApp Image 2026-03-01 at 8 45 55 PM](https://github.com/user-attachments/assets/579a1da2-12b3-4dbb-83e5-004041dcd375)


# Step-6: DC Analysis 
Before width tuning :
![WhatsApp Image 2026-03-01 at 6 05 24 PM](https://github.com/user-attachments/assets/7937de16-4bd6-4171-9559-246eda3b59d2)


After width tuning:
![WhatsApp Image 2026-03-01 at 6 05 24 PM](https://github.com/user-attachments/assets/c11fb17b-82cf-451f-bb46-d48c32405624)


ID ≈ 0.333 mA  

Vout ≈ 0.753695 V  

✔ Bias point achieved near mid-supply.

---

# Step-7: Transient Analysis 
![WhatsApp Image 2026-03-01 at 6 38 40 PM](https://github.com/user-attachments/assets/6687d1ad-52a6-4de4-a6f9-58513fa29c1d)

Measured Gain from waveform:

Taking Vin(p-p) = 20 × 10⁻³ v

Gain = ΔVout / Vin (p-p)

=  783.28m-724.04m /  20 × 10⁻³ 

Gain = 2.962

Av(dB) = 20 log (2.962)

Av = 9.431 dB  


---

# Step-8: Theoretical Gain  

Small signal gain:

Av = gm (ro1 || ro2) / (1 + gm ro3)

---

### Transconductance  

gm = 2ID / Vov  

gm = 2 × 0.334×10⁻³ / 0.25  

gm = 2.672 × 10⁻³ S  

---

### Output Resistance  

For NMOS:

λ = 0.1  

ro1 = ro3 = 1 / (λ ID)  

ro1 = 29.94 kΩ  

For PMOS:

λ = 0.12  

ro2 = 24.95 kΩ  

ro1 || ro2 ≈ 13.609 kΩ  

---

### Final Theoretical Gain  

Av = 0.4489 V/V  

Av(dB) ≈ 6.957 dB  

---

# Step-9: AC Analysis  
![WhatsApp Image 2026-03-01 at 6 52 29 PM](https://github.com/user-attachments/assets/4da22aa8-952c-4bf1-95e5-bf5af3b85aac)


gain = 9.55- 3dB 

gain = 6.55 dB

BW = fH − fL

fL = 0 

BW = fH = 167.91 MHz 



---

# Final Results  

| Parameter | Theoretical | Practical |
|------------|-------------|------------|
| ID | 0.334 mA | 0.333 mA |
| Vout | 0.75 V | 0.753 V |
| Gain (V/V) | 0.4489 | 2.962 |
| Gain (dB) | 6.957 dB | 9.431 dB |

---

# Inference  

The 3-transistor Common Source amplifier using PMOS active load and NMOS current source bias was successfully designed and simulated in 180nm technology.

- All MOSFETs operate in saturation region.  
- Bias point achieved near VDD/2.  
- Practical gain is lower due to channel length modulation and parasitic effects.  
- The circuit behaves as an inverting amplifier.

---



