# Experiment – 2  
## A.Design of CS Amplifier using 180nm Technology with PMOS Active Load  

---

## Aim  

To design a Common Source (CS) Amplifier using 180nm CMOS technology with PMOS active load and verify the performance using DC, Transient and AC analysis.

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

Av = (2.672 × 10⁻³ × 14.97 × 10³)  
      ---------------------------------
      (1 + 2.672 × 10⁻³ × 598.8)

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

# Conclusion

A CS amplifier using 180nm technology with PMOS active load was successfully designed.  

• Biasing conditions satisfied  
• Both MOSFETs operated in saturation  
• Operating point achieved near mid supply  
• Practical gain slightly lower than theoretical due to channel length modulation and parasitic effects  

The design satisfies given power and load capacitance specifications.

----
